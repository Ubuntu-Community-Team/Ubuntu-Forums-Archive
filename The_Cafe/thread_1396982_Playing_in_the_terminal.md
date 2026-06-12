---
title: "Playing in the terminal"
date: 2010-02-02
forum: The Cafe
---

### Post by teresaejunior on 2010-02-02
:popcorn:

Don't worry, this is safe!
Paste this in your terminal and press enter:

```
clear;PS1='\[\033]0;Just for fun!!!\007\033[1;33m\]I changed your terminal title, what to do now?\[\033[0m\] '

```

---

### Post by Tibuda on 2010-02-02
I thought this was about nethack or other terminal game.

> What to do now?
```
PS1='\t \w$(__git_ps1)\$ '
```

---

### Post by teresaejunior on 2010-02-02
How can I make this the default without the error bash: __git_ps1: command not found

---

### Post by juancarlospaco on 2010-02-02
**sudo apt-get install cmatrix ; cmatrix**

---

### Post by teresaejunior on 2010-02-02
> **juancarlospaco said:**
> **sudo apt-get install cmatrix ; cmatrix**

Cool!

Hey, if I write a sh script using #!/bin/sh, and if use colors in echo, will it be portable?

---

