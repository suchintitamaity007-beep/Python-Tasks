import random

words=["python","programming","developer","computer","hangmangame"]
print("_ _ _ !Welcome to the HANGMAN GAME! _ _ _")
while len(words)>0:
    secret_word=random.choice(words)
    words.remove(secret_word)
    guessed_letters=[]
    incorrect_guesses_left=6

    while incorrect_guesses_left>0:
        display_word=""
        for letter in secret_word:
            if letter in guessed_letters:
                display_word+=letter+" "
            else:
                display_word+="_"
        print("\n Word to guess: "+ display_word.strip())
        print(f"Incorrect guesses remaining: {incorrect_guesses_left}")
        if "_" not in display_word:
            print("\n CONGRATULATIONS! YOUR GUESS IS CORRECT! YOU WON!")
            break
        guess=input("Guess a letter: ").lower()
        if len(guess)!=1 or not guess.isalpha():
            print("Please enter a single valid letter.")
            continue
        if guess in guessed_letters:
            print("You already guessed that letter. Please try a different one.")
            continue
        guessed_letters.append(guess)

        if guess in secret_word:
            print(f"GOOD JOB! '{guess}' IS IN THE WORD!")
        else:
            print(f"Sorry, '{guess}' is not in the word.")
            incorrect_guesses_left-=1
    if incorrect_guesses_left==0:
        print("\n Game Over! You ran out of guesses!")
        print(f"The secret word was: {secret_word}")
    if len(words)>0:
        play_again=input("\n Would you like to play another round? (yes/no): ").lower()
        if play_again!="yes":
            print("Thanks for playing!")
            break
        else:
            print("\n Let's play another round!")
            

                
                
        
