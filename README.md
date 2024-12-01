java c Assignment One: Implementation of Autokey Cipher and Row Transposition Cipher CE235 Assignment One
2024-2025
University of Essex
1. Task of Assignment One
The aim of Assignment One is to write a Python program, which will implement the Autokey cipher and the Row transposition cipher. The introduction of the two ciphers can be found from the lecture notes.
Specifically, this assignment task is expected to do the following:
§ Design (with flowcharts) and develop a Python program with encryption and decryption functions for Autokey
cipher and the Row transposition cipher.
§ For the Row transposition cipher, if the length of the plaintext message (number of letters in message) is not
multiple times of the key length, you can add several letters to the end of the message before encryption, and delete these added letters after decryption to recover the original message.
A sample Python program caesar.py for Caesar cipher is provided for reference. The sample Python program can be run with default demo message and key from the command line in Terminal window like this:
python caesar_ciphyer.py
This reference program caesar_ciphyer.py encrypts a given message and then performs decryption. After the caesar_ciphyer.py program is run, it will display the plaintext, ciphertext, and the decrypted plaintext. If the cipher works correctly, the plain text and decrypted text should be the same.
Your program for these two ciphers should have a name like ak_registrationnumber.py (replace registrationnumber with your own registration number). Your program must run from command line like this (with a registration number 123456) :
python ak_123456.py
The outputs of ak_registrationnumber.py (including the key, plaintext, ciphertext and decrypted text) are required to be
displayed, following the display format given in the reference program caesar_ciphyer.py. 2. How to submit
Submit one python program file to Faser with the following filename (replace registration number by your own one):
ak_registrationnumber.py
Submission deadline is Wednesday, 04/12/2024 (UK time: 23:59); Beijing time: Thursday, 7:59, 05/12/2024.
3. Marking Scheme
There are 12 marks for this assignment (out of 100 marks for the overall module marks).
1) Flowcharts for the Autokey cipher and the Row transposition cipher take 1 mark each. The functions for the Autokey
cipher and the Row transposition cipher take 5 marks and 5 marks, respectively.
2) You will be asked by Professor He or the teaching assistants at NWU to demonstrate your work (including flowcharts
and program) and answer some questions to ensure it is your own work. Marks will be given according to the quality of your work and the demonstration. If you are asked to but you don’t demonstrate your work, no mark will be given to your assignment work.
3) Apart from demonstration of your work to the teaching staff members, it is mandatory for you to submit your program file to Faser (flowcharts are not to be submitted to Faser). You will not get mark for your work on the assignment if your program is not submitted to Faser. If your submission is late, there will penalty on your mark according to the university policy.
4) Extra check of your submitted program may be conducted by Professor He. If any programming or plagiarism problems are found from the check, your marks will be deducted.
4. Plagiarism
You should work individually on this assignment. Anything you submit is assumed to be entirely your own work. The usual Essex policy on plagiarism applies: http://www.essex.ac.uk/plagiarism/.

Appendix A. Sample Python Program for Caesar Cipher
 import sys #------------------------------------------------------------------------------ ### Note: Allow the program to be run from the command line:
## You can simply use the default message and key given in the program # python caesar_cipher.py
## You can also use message and key given in command line in Terminal (not required), ## where, atestmessage is the message (no space!)
# python caesar_cipher.py atestmessage
# the alphabet with all symbols in the set can be encrypted
LETTERS = 'abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ'
def caesar_cipher(message, mode, key):
# stores the encrypted/decrypted form of 代 写CE235、 Python
代做程序编程语言the message ciphertext = ''
# run the encryption/decryption code on each symbol in the message string for symbol in message:
if symbol in LETTERS:
# get the encrypted (or decrypted) index of this symbol in the LETTERS num = LETTERS.find(symbol) # index of the uncoded symbol in LETTERS if mode == 'encrypt':
num = num + key elif mode == 'decrypt': num = num - key
else:
print('Correct operation mode is needed') exit()
# handle the wrap-around if num is larger than the length of LETTERS or less than 0 num = num % len(LETTERS)
# add encrypted/decrypted number's symbol at the end of translated ciphertext = ciphertext + LETTERS[num]
else:
# just add the symbol without encrypting/decrypting if it is not in the set LETTERS ciphertext= ciphertext + symbol
return ciphertext
   def row_cipher(message, mode, key):
# You need to comment out the following statement and complete the function body for your own python program output_text = message
return output_text
 def autokey_cipher(message, mode, key):
# You need to comment out the following statement and complete the function body for your own python program output_text = message
return output_text
if __name__ == '__main__':
# Determine the number of arguments in the command line numArgv = len(sys.argv)
# the default string to be encrypted/decrypted message = 'a secret message.'
# the default key used by the caesar cipher key_caesar = 3
# the default key used by the autokey cipher key_autokey = 'abcde'
 
   # the default key used by the row transpose cipher
key_row = '3214' # note: you can change the key_row with other orders of the columns being read out.
if numArgv == 2:
# get the message from the input given in the command line message = sys.argv[1]
elif numArgv == 3:
# get the message and key for autokey cipher specified the input given in the command line message = sys.argv[1]
key_autokey = sys.argv[2]
elif numArgv == 4:
# get the message and key specified the input given in the command line message = sys.argv[1]
key_autokey = sys.argv[2]
key_row = sys.argv[3]
elif numArgv > 4:
# Instruction on providing message and key from command line
print('+++Please input optional message and keys for autokey and row transpose cipyers with correct format') print('+++python caesar_cipher.py')
print('+++For example: ')
print('+++python caesar_cipher.py testmessage abcd') # here the string "testmessage" is the plaintext,
exit()
# change the mode to encrypt or decrypt
mode = 'encrypt' # set to 'encrypt' or 'decrypt'
ciphertext_caesar = caesar_cipher(message, mode, key_caesar)
mode = 'decrypt'
plaintext_caesar = caesar_cipher(ciphertext_caesar, mode, key_caesar)
# Note: you can use two separate functions for encryption and decryption instead of using one function # for both encryption and decryption with different inputs.
mode = 'encrypt' # set to 'encrypt' or 'decrypt'
ciphertext_autokey = autokey_cipher(message, mode, key_autokey)
mode = 'decrypt'
plaintext_autokey = autokey_cipher(ciphertext_autokey, mode, key_autokey)
mode = 'encrypt' # set to 'encrypt' or 'decrypt' ciphertext_row = row_cipher(message, mode, key_row) mode = 'decrypt'
plaintext_row = row_cipher(ciphertext_row, mode, key_row)
### Note: don't change the following code in your own program for displaying program outputs print('##############################################')
print('Caesar Cipher with key: ', key_caesar) print('##############################################')
print('Plain message: ', message) print('Ciphertext: ', ciphertext_caesar) print('Decrypted text: ', plaintext_caesar)
print(' ') print('##############################################') print('Autokey Cipher with key: ', key_autokey) print('##############################################') print('Plain message: ', message)
print('Ciphertext: ', ciphertext_autokey)
print('Decrypted text: ', plaintext_autokey)
print(' ') print('##############################################') print('Row Transposition Cipher with key: ', key_row) print('##############################################') print('Plain message: ', message)
print('Ciphertext: ', ciphertext_row)
print('Decrypted text: ', plaintext_row)
 
         
加QQ：99515681  WX：codinghelp  Email: 99515681@qq.com
