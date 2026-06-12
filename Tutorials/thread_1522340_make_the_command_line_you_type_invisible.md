---
title: "make the command line you type invisible"
date: 2010-07-02
forum: Tutorials
---

### Post by sulekha on 2010-07-02
To hide the user input to be displayed on screen, use the terminal line setting command** stty -echo**, whatever the user enters after this command will not be displayed in the screen. to make the input characters get displayed on the screen use **stty echo**

---

### Post by light50 on 2010-07-09
Thank-you, do you know nay examples of where this command is used?

---

### Post by muhammed irshad on 2010-07-10
can you please explain how it works???

---

### Post by Tony Flury on 2010-07-10
stty - is a command that sets the various options on the terminal.

the -echo option turns off the "echo" option - with echo off the keys you pressed are processed but not echoed on to the screen

for more information : 

enter : 
```

$ man stty

```
at the terminal

---

### Post by Tony Flury on 2010-07-10
> **light50 said:**
> Thank-you, do you know nay examples of where this command is used?

This exact command is not used directly in this case - but the sudo program uses the "echo" attribute when it prompts for your password - to ensure that you can type your password without the characters being seen on the screen.

---

### Post by muhammed irshad on 2013-04-30
Thanks a lot for the explanation

---

