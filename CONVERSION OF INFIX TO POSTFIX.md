# Exp.No:32  
## CONVERSION OF INFIX TO POSTFIX

---

### AIM  
To write a Python program to convert a given Infix expression to Postfix expression by following the precedence and associative rules. The input expression contains only Division, Subtraction, and Bitwise AND operators. A dictionary is used to set the priority for operators, and a set is used to hold the operators used in the given expression.

---

### ALGORITHM

1. **Start the program.**
2. **Initialize an empty stack** and an empty output string.
3. **Iterate through each character** in the infix expression:
   - If the character is **not an operator**, append it directly to the output string.
   - If the character is an **open parenthesis '('**, push it onto the stack.
   - If the character is a **close parenthesis ')'**, pop from the stack and append to the output until encountering a left parenthesis '('.
   - If the character is an **operator**, handle it based on precedence:
     - While there’s an operator at the top of the stack with higher or equal precedence, pop the stack and append those operators to the output.
     - Push the current operator onto the stack.
4. **Use a priority dictionary** to define operator precedence, ensuring higher precedence operators are placed before lower precedence ones.
5. Once the expression is fully processed, continue popping any remaining operators from the stack and append them to the output.
6. **Return the final postfix expression.**
7. **Print the result.**
8. **End the program.**

---

### PROGRAM

```python
stack = [] 
output = []

# Include only used operators: '/', '-', '&', '(', ')'
Operators = {'/', '-', '&', '(', ')'}

# Set proper precedence (higher number = higher precedence)
Priority = {'&': 1, '-': 2, '/': 2, '(': 0}  # Note: '/' and '-' same precedence

def infixToPostfix(expression):
    for char in expression:
        if char not in Operators:
            output.append(char)
        
        elif char == '(':
            stack.append(char)
            
        elif char == ')':
            while stack and stack[-1] != '(':
                output.append(stack.pop())
            stack.pop()  # Remove '(' from stack
            
        else:
            while stack and Priority[char] <= Priority.get(stack[-1], 0):
                output.append(stack.pop())
            stack.append(char)
        
    while stack:
        output.append(stack.pop())

    return ''.join(output)
    
# Input
expression = input()
print("infix notation: ", expression)
print("postfix notation: ", infixToPostfix(expression))

```

### OUTPUT
<img width="742" height="170" alt="image" src="https://github.com/user-attachments/assets/f4235da6-87ea-4791-bc70-af6b18cc364a" />



### RESULT
Thus the python program for convert a given Infix expression to Postfix expression by following the precedence and associative rules has been implemented and executed successfully.
