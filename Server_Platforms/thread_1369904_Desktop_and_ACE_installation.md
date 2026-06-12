---
title: "Desktop and ACE installation"
date: 2010-01-01
forum: Server Platforms
---

### Post by dukla on 2010-01-01
Hi I am using server edition of Ubuntu for my server and i have two questions ...

First i want to install whole machine through desktop environment so i want to install ubuntu-desktop but after i want to remove so how can i do so completely remove it after?

And second i am trying to install ACE [http://download.dre.vanderbilt.edu/previous_versions/ACE-5.7.5.zip](http://download.dre.vanderbilt.edu/previous_versions/ACE-5.7.5.zip) from this and i need some advices.

How to even configure? When i do basic procedures like mkdir build cd build ../configure is says bad interpreter and after i fix this it says something about config.dab or something like that. Can anybody help me here? Thx

---

### Post by bruno9779 on 2010-01-01
I tried downloading that, and I have found an html in the uncompressed folder with compiling instructions.

Thing is, they aren't very easy ones at that.

May I ask, what does this program do?

---

### Post by dukla on 2010-01-01
I will if you also help me with the desktop problem... How can i remove desktop when i install it on ubuntu server or should i just install desktop ubuntu? because i need it only for install all things and after behave like server with minimum processes ... because i hate command line after install ubuntu server when i cannot see for example if my apatche is working etc ...

---

### Post by dukla on 2010-01-01
Here is my message when i try to configure it: bash: ../configure: /bin/sh^M: bad interpreter: No such file or directory

But the file is there here is message when i try to execute non existing file:
bash: ./configure: No such file or directory

---

### Post by bruno9779 on 2010-01-01
You can install and remove the package ubuntu desktop quite safely. I have never done it, but there are a few post on this forum about that, and the OPs didn't seem to have any relevan issue.

to play it extra safe you could use aptitude instead of apt-get as it is supposed to handle romoval of dependencies better

---

### Post by dukla on 2010-01-01
> **dukla said:**
> Here is my message when i try to configure it: bash: ../configure: /bin/sh^M: bad interpreter: No such file or directory

But the file is there here is message when i try to execute non existing file:
bash: ./configure: No such file or directory
So i did 
aptitude install tofrodos
dos2unix configure

And now i have this message:
configure: error: cannot run /bin/bash ../aux_config/config.sub

---

### Post by dukla on 2010-01-01
Anybody have any idea? Ahh i see its 2 AM :-)

---

### Post by dukla on 2010-01-02
I tried erything nobody can help me here - google, local support nobody knows the solution if any...

Maybe i should swich the distro from ubuntu to another ...

---

### Post by bruno9779 on 2010-01-02
It appears to be an issue with your code, not with your build environment. As it is, apparently there are several syntax mistakes that prevent running it

What is this code supposed to do? and where you have got it from? (not the download link, the download page)

---

### Post by noway2 on 2010-01-03
I have successfully added the gnome desktop on multiple occasions to a server addition.  I would suggest using that.  If I recall, there are TWO things that you will want to 'apt-get install', but I don't remember which they are.  I do know that the subject has been beaten to death in this forum, so a search should quickly reveal the process.

---

