# EX. NO: 1(A) : IMPLEMENTATION OF CAESAR CIPHER

## AIM:
To implement the simple substitution technique named Caesar cipher using C language.

## ALGORITHM:

STEP-1: Read the plain text from the user.

STEP-2: Read the key value from the user.

STEP-3: If the key is positive then encrypt the text by adding the key with each character in the plain text.

STEP-4: Else subtract the key from the plain text.

STEP-5: Display the cipher text obtained above.

## PROGRAM:

```c
#include <stdio.h>
#include <string.h>
#include <ctype.h>

int main() {
    char text[1000];
    int key, i;
    
    printf("Enter the plain text: ");
    fgets(text, sizeof(text), stdin);
    text[strcspn(text, "\n")] = '\0'; // Remove trailing newline
    
    printf("Enter the key value: ");
    scanf("%d", &key);
    
    for(i = 0; text[i] != '\0'; i++) {
        // For uppercase letters
        if(isupper(text[i])) {
            if(key > 0)
                text[i] = ((text[i] - 'A' + key) % 26) + 'A';
            else
                text[i] = ((text[i] - 'A' + (key % 26) + 26) % 26) + 'A';
        }
        // For lowercase letters
        else if(islower(text[i])) {
            if(key > 0)
                text[i] = ((text[i] - 'a' + key) % 26) + 'a';
            else
                text[i] = ((text[i] - 'a' + (key % 26) + 26) % 26) + 'a';
        }
        // Non-alphabetic characters remain unchanged
    }
    
    printf("Cipher text: %s\n", text);
    
    return 0;
}
```

## OUTPUT:

```
Enter the plain text: HELLO WORLD
Enter the key value: 3
Cipher text: KHOOR ZRUOG
```

```
Enter the plain text: KHOOR ZRUOG
Enter the key value: -3
Cipher text: HELLO WORLD
```

## RESULT :
Thus the implementation of Caesar cipher had been executed successfully.
