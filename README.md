# EX.-NO-1D-IMPLEMENTATION OF VIGENERE CIPHER
## AIM:
  To implement the Vigenere Cipher substitution technique using C program.
## ALGORITHM:
  STEP-1: Arrange the alphabets in row and column of a 26*26 matrix.
  STEP-2: Circulate the alphabets in each row to position left such that the first letter is attached to last.
  STEP-3: Repeat this process for all 26 rows and construct the final key matrix.
  STEP-4: The keyword and the plain text is read from the user.
  STEP-5: The characters in the keyword are repeated sequentially so as to match with that of the plain text.
  STEP-6: Pick the first letter of the plain text and that of the keyword as the row  indices and column indices respectively.
  STEP-7: The junction character where these two meet forms the cipher character.
  STEP-8: Repeat the above steps to generate the entire cipher text.
## PROGRAM:
```
  #include <stdio.h>
    #include <string.h>
    #include <ctype.h>
    #define MAX 100
    void generateVigenereMatrix(char matrix[26][26]) {
    char alphabet = 'A';
    for (int i = 0; i < 26; i++) {
        for (int j = 0; j < 26; j++) {
            matrix[i][j] = alphabet;
            alphabet++;
            if (alphabet > 'Z') alphabet = 'A';
        }
    }
    }
    void encrypt(char plaintext[], char keyword[], char ciphertext[]) {
    char vigenereMatrix[26][26];
    generateVigenereMatrix(vigenereMatrix);

    int lenPlaintext = strlen(plaintext);
    int lenKeyword = strlen(keyword);

    for (int i = 0, j = 0; i < lenPlaintext; i++) {
        if (isalpha(plaintext[i])) {
            int row = toupper(plaintext[i]) - 'A';
            int col = toupper(keyword[j]) - 'A';
            ciphertext[i] = vigenereMatrix[row][col];
            j = (j + 1) % lenKeyword;
        } else {
            ciphertext[i] = plaintext[i];  
        }
    }
    ciphertext[lenPlaintext] = '\0';  
    }
    int main() {
    char plaintext[MAX], keyword[MAX], ciphertext[MAX];
    printf("Enter the plaintext: ");
    fgets(plaintext, MAX, stdin);
    plaintext[strcspn(plaintext, "\n")] = '\0';  
    printf("Enter the keyword: ");
    fgets(keyword, MAX, stdin);
    keyword[strcspn(keyword, "\n")] = '\0';  
    for (int i = 0; keyword[i]; i++) {
        keyword[i] = toupper(keyword[i]);
    }
    for (int i = 0; plaintext[i]; i++) {
        plaintext[i] = toupper(plaintext[i]);
    }
    encrypt(plaintext, keyword, ciphertext);
    printf("Ciphertext: %s\n", ciphertext);
    return 0;
    }
```
## OUTPUT:
![image](https://github.com/user-attachments/assets/42f51491-c2b5-4e43-9a71-c3605d68aa06)
## RESULT:
  Thus the Vigenere Cipher substitution technique had been implemented successfully.
