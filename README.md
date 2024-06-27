# PasswordStrengthTester-Python
Creating a Password Strength Tester with multiple levels of testing using python

# Steps
1. Import Necessary Modules

      import string

This line imports the string module, which provides constants and functions for working with strings.

2. Start an Infinite Loop

while True:
This initiates a loop that will continue until explicitly terminated.
3. Prompt User for Password Input

    password = input(f"choose your password:  ")
This line prompts the user to enter a password and stores it in the password variable.
4. Check Password Complexity

    upper_case = any([1 if c in string.ascii_uppercase else 0 for c in password])
    lower_case = any([1 if c in string.ascii_lowercase else 0 for c in password])
    special = any([1 if c in string.punctuation else 0 for c in password])
    digits = any([1 if c in string.digits else 0 for c in password])

    characters = [upper_case, lower_case, special, digits]
These lines check various aspects of the password:
upper_case: Checks if the password contains uppercase letters.
lower_case: Checks if the password contains lowercase letters.
special: Checks if the password contains special characters.
digits: Checks if the password contains digits.
It creates a list characters to store these checks.
5. Read Common Passwords List

    with open('common.txt', 'r') as f:
        common = f.read().splitlines()
Opens a file named common.txt in read mode and reads its contents into a list common. This list contains common passwords that users should avoid using.
6. Check if Password is Common

    if password in common:
        print("Password was found in a common list. Score: 0 / 7")
        exit()
Checks if the entered password is in the common list. If it is, it prints a message and exits the program.
7. Calculate Password Length Score

    length = len(password)

    score = 0

    if length > 8:
        score += 1
    if length > 12:
        score += 1
    if length > 17:
        score += 1
    if length > 22:
        score += 1

    print(f"Password length is {str(length)}, adding {str(score)} points!")
Calculates a score based on the length of the password:
Adds 1 point if the password length is more than 8 characters.
Adds another point if the length is more than 12 characters.
Adds another point if the length is more than 17 characters.
Adds another point if the length is more than 22 characters.
Prints the length of the password and the corresponding score.
8. Calculate Character Type Score

    if sum(characters) > 1:
        score += 1
    if sum(characters) > 2:
        score += 1
    if sum(characters) > 3:
        score += 1

    print(f"Password has {str(sum(characters))} different character types, adding {str(sum(characters) - 1)} points")
Calculates a score based on the types of characters in the password:
Adds 1 point if the password contains more than 1 type of character.
Adds another point if it contains more than 2 types.
Adds another point if it contains more than 3 types.
Prints the number of different character types and the corresponding score.
9. Determine Password Strength

    if score < 4:
        print(f"The password is very weak! Score: {str(score)} / 7")
    elif score == 4:
        print(f"The password is not bad! Score: {str(score)} / 7")
    elif score > 4 and score < 6:
        print(f"The password is pretty good! Score: {str(score)} / 7")
    elif score > 6:
        print(f"The password is strong! Score: {str(score)} / 7")
Determines the strength of the password based on the calculated score:
Scores less than 4 are considered very weak.
A score of 4 is considered not bad.
Scores greater than 4 and less than 6 are considered pretty good.
Scores greater than 6 are considered strong.
10. Prompt for Another Password or Exit

    cont = input("Want to try another password (yes/N)")

    if cont == "yes":
        continue
    else:
        input("Press any key to exit")
        break
Asks the user if they want to try another password.
If the user enters "yes", the loop continues, prompting for another password.
If the user enters anything else, the program prompts to exit.

# Additional Notes

MAKE SURE you have "common.txt" Contained in the same folder that you have the sourse code runing from or else its not going to work in this instance.
You can use any password file list as long as it is .txt I used this one because it was the first oen I found
