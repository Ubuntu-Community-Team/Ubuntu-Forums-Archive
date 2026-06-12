---
title: "Editors of choice and the people who use them"
date: 2008-06-26
forum: The Cafe
---

### Post by johnhdsi on 2008-06-26
I have a question in regards to programming and editors. I am trying to learn programming basics on my own from what I can find on the internet. What's the opinion on editors?


I have installed the ones I read about.

Emacs
vim
nano
Idle
Gedit

Which is best for learning?

Can anyone also point me to a good source for learning how to write code? I would greatly appreciate it.


Thanks,
John

---

### Post by cdtech on 2008-06-26
What language do you want to learn?

---

### Post by LaRoza on 2008-06-26
> **johnhdsi said:**
> I have a question in regards to programming and editors. I am trying to learn programming basics on my own from what I can find on the internet. What's the opinion on editors?

Can anyone also point me to a good source for learning how to write code? I would greatly appreciate it.


Check out the Programming Talk forum and its stickies. [http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)

Ubuntu comes with Gedit and Gedit has a lot of plugins in the repos and is a natural starting editor (in fact, I still use it) 

[http://ubuntuforums.org/showthread.php?t=839955](http://ubuntuforums.org/showthread.php?t=839955)

---

### Post by RiceMonster on 2008-06-26
Nano is good CLI editor for begginers, though I highly reccomend you learn vim, as it's highly efficient. However, there's a few lines you have to comment out in the vimrc in Ubuntu because the default vim on Ubuntu SUCKS. I think it's something like "set compatible" and then there's another one that makes the text bold and easier on the eyes. I don't remeber right now, and I'm not using Ubuntu right now, so I can't tell you.

---

### Post by LaRoza on 2008-06-26
> **RiceMonster said:**
> Nano is good CLI editor for begginers, though I highly reccomend you learn vim, as it's highly efficient. However, there's a few lines you have to comment out in the vimrc in Ubuntu because the default vim on Ubuntu SUCKS. I think it's something like "set compatible" and then there's another one that makes the text bold and easier on the eyes. I don't remeber right now, and I'm not using Ubuntu right now, so I can't tell you.

The default vim in Ubuntu is "vim-tiny".

Run:

```

sudo aptitude install vim

```

To get the full experience.

---

### Post by MONODA on 2008-06-26
You should also enable syntax highlighting in .vimrc but I am not sure how to do that, arch does it by default :D

---

### Post by erginemr on 2008-06-26
You can't go wrong with **Geany**, which has extra functionalities like syntax highlighting, building, compiling and running programs, be it c, c++, python, etc.
[http://geany.uvena.de/](http://geany.uvena.de/)

If you are asking for a genral advice on which programming language to learn, I can safely suggest **Python**:
[http://ubuntuforums.org/showpost.php?p=4891924&postcount=4](http://ubuntuforums.org/showpost.php?p=4891924&postcount=4)

---

### Post by erginemr on 2008-06-26
> **MONODA said:**
> You should also enable syntax highlighting in .vimrc but I am not sure how to do that, arch does it by default :D

For highligthing and enabling other options in vim:
[http://ubuntuforums.org/showpost.php?p=4576155&postcount=2](http://ubuntuforums.org/showpost.php?p=4576155&postcount=2)

---

### Post by mini_g on 2008-06-26
I'd also check out Kate.  I'm not sure as to how it fairs in non-webpage code, but it has a different "tweak" on the interface than Gedit.

---

### Post by LaRoza on 2008-06-26
> **MONODA said:**
> You should also enable syntax highlighting in .vimrc but I am not sure how to do that, arch does it by default :D

With vim-tiny, you can't have syntax highlighting. Installing "vim" will get you that by default.

> **erginemr said:**
> You can't go wrong with **Geany**, which has extra functionalities like syntax highlighting, building, compiling and running programs, be it c, c++, python, etc.
[http://geany.uvena.de/](http://geany.uvena.de/)


That has nothing that Vim doesn't have or Gedit ;)

---

### Post by erginemr on 2008-06-26
> **LaRoza said:**
> ...
That has nothing that Vim doesn't have or Gedit ;)

No, it has. Geany has specific tools to ease program editing and testing (such as commands for compiling and building, and an embedded console window), which neither standard vim, nor gedit has.

---

### Post by Barrucadu on 2008-06-26
I like Emacs, which has syntax highlighting, a terminal, games, web browser, web server, it has everything!
You could even run Vim inside Emacs if you really wanted to.

---

### Post by -grubby on 2008-06-26
> **mini_g said:**
> I'd also check out Kate.  I'm not sure as to how it fairs in non-webpage code, but it has a different "tweak" on the interface than Gedit.

Kate seems to handle Python code well

---

### Post by shifty2 on 2008-06-26
I would highly reccommend either emacs or vim.

Both have steep learning curves, especially vim which is totally different to anything you will have used before, but its well worth persisting with them. I don't think anyone other than extreme devotees will argue that emacs is "quicker" at writing code - ultimately why you will choose the editor. However, the advantage of emacs is its extensibility; I can write emails, go on IRC, commit changes to a project, make emacs behave like vim, do pretty much anything (even watch films) without leaving the editor.

I use emacs because of this extensibility, but only after M-x viper-mode ;)

EDIT:
Barrucadu got there first

---

