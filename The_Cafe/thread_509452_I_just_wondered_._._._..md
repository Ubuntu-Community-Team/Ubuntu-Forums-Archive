---
title: "I just wondered . . . ."
date: 2007-07-25
forum: The Cafe
---

### Post by rolnics on 2007-07-25
How come Unix OS were able to recognise the difference between upper and lower case for passwords and stuff like that, long before windoze?? 

Please don't state the obvious one = windoze is crap!

---

### Post by aysiu on 2007-07-25
Windows is not crap.

Windows favors convenience over security.

*nix was never meant to be convenient. And the *nix conventions (even for filenames, not just passwords) differentiate between upper- and lower-case letters.

---

### Post by forrestcupp on 2007-07-25
Some people would rather there not be a distinction between upper and lower case.

---

### Post by Tomosaur on 2007-07-25
In Linux, different case characters are treated as completely different characters. If you create a file called 'myFile.txt', you cannot open it through the terminal by using 'MYFILE.txt' or 'MYfILE.txt', only 'myFile.txt'. Windows does not do this, you can find and open files using different case characters.

Windows' method requires a tiny bit of extra code and thus processing to be able to do this, while Linux favours efficiency and security. That, and capital letters in passwords and such-like can give security benefits which Windows invalidates through its method. There is only one way to type 'hello' on Windows, but on Linux you could type it 'Hello', 'hello', 'hEllo' etc etc, and each style would be treated as unique, thus making it more difficult to crack the password.

---

### Post by prizrak on 2007-07-25
In the ASCII table (and Unicode as well) upper and lower case characters have different code. By default all software is case dependant. For instance if you write a program that would take a password "butilka" it will not take "BUTILKA" unless you put an OR clause in it for instance.

Let user in If pwd == "BUTILKA" or pwd=="butilka". 

Windows developers made a conscious decision to make things easier for the user and coded it in a way that would disregard case (not in passwords though). It was done to make it 
A) Easier to deal with - if you are looking for a file called "Essay", you can just type in "essay" in the search box
B) Less confusion - it's easy enough to confuse "Essay" with "essay" if you happen to have both files in the same directory.

---

### Post by Tundro Walker on 2007-07-26
For home users, I could see convenience winning out.  But in a corporate environment, I'd think Windows would get implemented for tighter password security.  I guess that falls on the IT dept's head, not Microsoft's.  But, you'd think MS would build in a toggle switch in the registry for "ROBUST_PASSWORD_SECURTY = True/False" to enable/disable a *nix-style password system.  Oh well.

---

### Post by prizrak on 2007-07-26
> **Tundro Walker said:**
> For home users, I could see convenience winning out.  But in a corporate environment, I'd think Windows would get implemented for tighter password security.  I guess that falls on the IT dept's head, not Microsoft's.  But, you'd think MS would build in a toggle switch in the registry for "ROBUST_PASSWORD_SECURTY = True/False" to enable/disable a *nix-style password system.  Oh well.

Where did people get the idea that Windows passwords are case insensitive? I know for a fact that Win2K had case sensitive logon passwords. I can't say anything for NT4.5 as I never used it. The 9x line didn't actually have passwords outside of logging into a domain.

---

