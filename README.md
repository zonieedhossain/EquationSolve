# EquationSolve
Problem Solve operator precedence infix post fix  like calculate .

# Basic examples
              infix 1+2*3 to postfix
              (1+(2*3)) -> add parentheses
              (1+(23*)) -> convert multiplication
              (1(23*)+) -> convert addition
              123*+ -> remove parentheses
# Convert infix to postfix
1. we can set parentheses around an operator whenever there is no operator with higher precedence to the left or the right of the operator
2. If we scan from left to right, we can make sure that there is no operator with higher precedence to the left, but we still have to look to the right
3. The order of operands does not change

# For more clear idea
 --> 1+2*3^4/5-6
 --> scan: +,* (operators) and 12 (postfix)
 --> precedence of + is lower than *; thus, scan further:+,*,^ (operators) and 123 (postfix)
 --> precedence of * is lower than ^; thus, scan further: +,*,^,/ (ops.) and 1234 (postfix)
 --> precedence of ^ is higher than /; thus, append ^: +,*,/ (ops.) and1234^ (postfix)
 
 # For visual idea 
 
                   ---> 1+2*3^4/5-6 <---
                  symbol operators postfix
                     1                1
                     +       +        1
                     2       +        12
                     *      +,*       12
                     3      +,*       123
                     ^     +,*,^      123
                     4     +,*,^      1234
                     /    +,*,^,/     1234 
                           +,*,/      1234^ 
                            +,/       1234^*
                     5      +,/       1234^*5
                     
# Algorithm:
   set operator_stack to empty stack
   while (not end of input)
          symbol = next input
          if (symbol is operand)
              add symbol to postfix string
          else
            while (operator_stack not empty and top element has higher precedence than symbol)
                  pop top element and add it to postfix string
            push symbol onto operator_stack
          while (operator_stack not empty)
            pop top element and add it to postfix string
            
# Reference
https://www.academia.edu/9476379/Using_Stacks_Algorithms_for_Infix_Postfix_and_Prefix
