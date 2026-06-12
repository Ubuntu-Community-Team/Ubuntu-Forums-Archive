---
title: "Mozilla Firefox security problem"
date: 2009-05-13
forum: Security
---

### Post by michael91 on 2009-05-13
I've recently changed my OS to Linux Mint (a variant of 8.10, iirc). A few minutes ago, I tried using Firefox, and before actually opening, an Alert box came up saying 

"Could not initialize the application's security component. The most likely cause is problems with files in your application's profile directory. Please check that this directory has no read/write restrictions and your hard disk is not full or close to full. It is recommended that you exit the application and fix the problem. If you continue to use this session, you might see incorrect application behaviour when accessing security features."

The computer is shared, so I don't know if the second user did something to cause this. Also, I only noticed this while typing this message, when I type, red lines even appear under words that are spelled correctly (i.e. most of this message). Other correctly spelled words (such as Firefox and Alert) aren't underlined.

How do I go about fixing these problems?

---

### Post by pro003 on 2009-05-13
like it says, check your .mozilla folder in home dir press ctrl+h if it's probably hidden

open nautiusa in terminal, type;

```
gksu nautilus
```

enter your passwd

browse to home dir ctrl+h and look for **.mozilla** folder

right click it and set read/write permission.

hope you solve the problem.

---

### Post by michael91 on 2009-05-13
Unfortunately, no. It didn't work.

---

### Post by pro003 on 2009-05-13
Ok. This should work:

in terminal:

# sudo apt-get remove --purge firefox

# sudo rm -rf .mozilla

      Then install firefox again:

# sudo apt-get update
# sudo apt-get install firefox
# sudo apt-get install -f

---

