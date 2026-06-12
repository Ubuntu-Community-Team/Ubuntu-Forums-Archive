---
title: "define seperate .bashrc for the terminal plugin"
date: 2008-04-24
forum: Ubuntu System Panel
---

### Post by delfick on 2008-04-24
hello

is it possible for the terminal plugin to use it's own .bashrc file?

cause as you can see in the screenshot, my .bashrc file makes my terminal look nice, but when it's used in the terminal plugin for the usp, then it just takes up way too much room ...

(it also doesn't help that the text is black, and seeing as my desktop background is black and I've set it to use that as a background, we get even more problems :p)

thnx :)

---

### Post by Malac on 2008-04-24
As ever delfick I will put this on my list and get to it as soon as I can. :)
 
I think it can be passed as an option on creation of the terminal but I will have to look into this.
 
I'm currently doing some heavy downloading so everything net based is taking forever, will check the docs later if I can.
 
Have you tried the new tweaks to applications plugin yet?
 
**Edit: Actually delfick can you attach to a post or send me via e-mail **(address in about box of USP credits)** your bashrc file as it looks like I may have to create USP specific and/or ignore normal settings. Cheers.**

---

### Post by Malac on 2008-04-25
Okay delfick done that so ignore previous post.

Can you test the attached and if all works well I'll upload it to the SVN Repository.
You need a file called **.uspbashrc** in your home folder. If it exists it will use that instead of .bashrc if it doesn't it will use .bashrc

Hope this helps

---

### Post by delfick on 2008-04-26
> **Malac said:**
> As ever delfick I will put this on my list and get to it as soon as I can. :)

did I ask that before ?

sorry :)


> **Malac said:**
> Okay delfick done that so ignore previous post.

Can you test the attached and if all works well I'll upload it to the SVN Repository.
You need a file called **.uspbashrc** in your home folder. If it exists it will use that instead of .bashrc if it doesn't it will use .bashrc

Hope this helps

cool, thnx, that works great :)

(also I've attached my .bashrc file anyways :) btw it's not all mine, I copied it from somewhere (unfortunately can't remember where) and slightly modified it))

EDIT : It's a modified version of the one found here [http://ayozone.org/2008/02/25/bash-fancy-prompt-and-improvments/](http://ayozone.org/2008/02/25/bash-fancy-prompt-and-improvments/)

---

### Post by Malac on 2008-04-27
I just meant it's usually you that comes up with ideas but that's cool. :)

I'll upload this to the SVN then everyone can benefit from your idea.:guitar:

EDIT: Okay that's done.
I've uploaded the plugins separately to the Downloads page of the SVN here:
[http://code.google.com/p/ubuntu-system-panel/downloads/list](http://code.google.com/p/ubuntu-system-panel/downloads/list)

Enjoy.

---

### Post by delfick on 2008-04-27
> **Malac said:**
> I just meant it's usually you that comes up with ideas but that's cool. :)

lol :)

> I'll upload this to the SVN then everyone can benefit from your idea.:guitar:

cool :)

> EDIT: Okay that's done.
I've uploaded the plugins separately to the Downloads page of the SVN here:
[http://code.google.com/p/ubuntu-system-panel/downloads/list](http://code.google.com/p/ubuntu-system-panel/downloads/list)

Enjoy.

is it possible to make it so that they're all in their own svn branch, so so that if people have downloaded them, and want to use any future updated versions, all they have to do is svn update to get the new versions? :)

---

### Post by Malac on 2008-04-28
> **delfick said:**
> is it possible to make it so that they're all in their own svn branch, so so that if people have downloaded them, and want to use any future updated versions, all they have to do is svn update to get the new versions? :)
I'll try and get round to that tonight.

---

### Post by delfick on 2008-04-28
> **Malac said:**
> I'll try and get round to that tonight.

awsome :)

---

### Post by Malac on 2008-05-03
> **delfick said:**
> awsome :)Done :) :)

---

### Post by delfick on 2008-05-03
> **Malac said:**
> Done :) :)

:D

---

