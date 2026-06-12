---
title: "Computers and Mathmatics"
date: 2008-08-21
forum: The Cafe
---

### Post by jamescox84 on 2008-08-21
Hi Everyone,
I remember from my Computational Systems lessons at College, some interesting things about how computer perform arithmetic. How once you have addition working, you get subtraction, multiplication and division for free. The logic was.

You have adding implemented in hardware: (Full-Adder I suppose)

To subtract:
Add a negative number. (Makes sense when using 2-compliment)

To multiply:
Add multiple times. (Seems simple)

To divide:
Multiply by a fraction. (I understand the mathematical basis for this)

But here is my question if multiplication was implemented via iteration. You can't have 0.5 iterations, can you? How does the computer divide? I love the elegance of the theory, but how could division be implemented like this?

---

### Post by Joeb454 on 2008-08-21
Would you not multiply 1 iteration by 0.5?

---

### Post by jamescox84 on 2008-08-21
> **Joeb454 said:**
> Would you not multiply 1 iteration by 0.5?

This seem's like an answer but I don't understand.

For example: how would this roll out?

3.25 * 21.5

---

### Post by jespdj on 2008-08-21
Floating point numbers, such as 3.25 and 21.5, are usually stored in [IEEE 754](http://en.wikipedia.org/wiki/IEEE_754-1985) format inside the computer. The hardware knows how to deal with numbers in that format.

---

### Post by Nepherte on 2008-08-21
[QUOTE=jamescox84]To multiply:
Add multiple times. (Seems simple)[/QUOTE]
There's a shortcut for multiplying if you multiply with a power of 2. You can then simply shift the binary number to the left. So multiply with 2^n, you shift the number to the left with n positions.

---

### Post by Kvark on 2008-08-21
This is how I think computers do it since they only have the digits 0 and 1 but no decimal point:
[LIST=1]
[*]Use scientific notation: 0.065 * 0.0018 = 6.5*10^-2 * 1.8*10^-3
[*]Multiply the coefficients as whole numbers: 65 * 18 = 1170 so the resulting coefficient is 1.17.
[*]Add the exponents together: -2 + -3 + 1 = -4
[*]Compare the signs, both numbers are positive so the result is positive.
[*]The result: 1.17*10^-4
[/LIST]
The one thing I don't understand is that if you preserve the decimal point in step 2 you'll see the result should be 11.7 so to compensate for moving the decimal point to 1.17 you must add +1 to the exponent in step 3. Since the computer has no decimal point in step 2 how does it know if it should add +1 the exponent to compensate for moving the decimal point or not?

---

### Post by Nepherte on 2008-08-21
> **Kvark said:**
> This is how I think computers do it since they only have the digits 0 and 1 but no decimal point:
[LIST=1]
[*]Use scientific notation: 0.065 * 0.0018 = 6.5*10^-2 * 1.8*10^-3
[*]Multiply the coefficients as whole numbers: 65 * 18 = 1170 so the resulting coefficient is 1.17.
[*]Add the exponents together: -2 + -3 + 1 = -4
[*]Compare the signs, both numbers are positive so the result is positive.
[*]The result: 1.17*10^-4
[/LIST]


That is pretty much how it works. They use a normalized scientific notation. Then they transform the number with the lowest exponent so that it is written in function of the highest exponent. Then do a normal multiplication of the numbers and they add the exponent. Afterwards they normalize the number again, because the result isn't necessarily normalized.

---

### Post by jamescox84 on 2008-08-22
Thanks for the responses. I understand what you are saying, the computer uses floating point numbers, and has a special algorithm for multiplication/division with floating point numbers. So does this mean that no modern processor uses repeated addition for multiplication? Or is this what is used at step 2? Also to divide two whole numbers, must they be converted to floating point numbers then processed? I'm I right in thinking it is fundamentally wrong to used the multiplication algorithm I originally posted to divide to whole numbers?

Sorry loads of questions there, just this is something that really interests me.

---

### Post by jespdj on 2008-08-22
Some interesting links for you:

Start with [Adder (electronics)](http://en.wikipedia.org/wiki/Adder_(electronics)), and have a look at [Adder-subtracter](http://en.wikipedia.org/wiki/Adder-subtracter) (a digital logic circuit which can add as well as subtract).

See also [Arithmetic logic unit](http://en.wikipedia.org/wiki/Arithmetic_logic_unit).

Multiplication is not generally done by repeated adding, that would be much too inefficient, especially if you're multiplying two large numbers together. There are smarter ways to do it. It can be done just like the way you would do it on paper, by computing partial products and adding them together. See: [Multiplication ALU](http://en.wikipedia.org/wiki/Multiplication_ALU) and [Booth's multiplication algorithm](http://en.wikipedia.org/wiki/Booth%27s_multiplication_algorithm).

---

