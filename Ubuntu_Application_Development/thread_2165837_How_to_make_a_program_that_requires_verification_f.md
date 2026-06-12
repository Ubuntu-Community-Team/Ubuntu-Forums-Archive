---
title: "How to make a program that requires verification from both parties?"
date: 2013-08-06
forum: Ubuntu Application Development
---

### Post by Bresser on 2013-08-06
Hello, I want to make a program with C++. So here is the story, I owe my mother for a car she bought me. I want a program that where we set the amount on the program. I input what I paid and she has to somehow verify that I did pay before it takes the amount off. That way she cannot say i didnt pay because she verified that I paid it. Is this possible? if so how?

---

### Post by TheFu on 2013-08-06
I wouldn't write this in C++ - I'd leverage GPG and PKI certs, then just use email to send gpg-signed agreements back and forth.  Read up on gpg signing, so you understand why it works.

For stuff like this, where both parties trust each other, why not just create a spreadsheet with the interest calculations built in and another row with the payments made?  Look up **amortization** to understand more.  If you make monthly payments, there shouldn't be more than 36 lines - after all, who would have a car payment for more than 36 months? That's sorta the line that says - any more money and you really shouldn't buy this.

---

