---
title: "[SOLVED] Hello and thanks for the welcome!"
date: 2008-10-14
forum: Testimonials &amp; Experiences
---

### Post by Linuxidiot on 2008-10-14
I told myself if i ever got my hands on a computer i would run linux.Ive spent about 10 hours yesterday researching and download and burning(day off work:)) Im very excited and have found this OS ubuntu...Im very pleased but im so new to this new world and some things i have a hard time with.My current endevours are my graphics card driver setup which is a Nvidia geforce 9500gt and the beloved game World of warcraft installation, i read the easy instructions but when i attempt to CD to the wow folder and run the wine.exe i believe it is, i get a no file or directory message:( Also im a great copy and paster!:) but i want to learn what it is im doing, why that specific code command...and im excited about learning how to code, im not a rich man so i have to teach myself... is there a freeware program i can get to teach me some of these things...i dont want to be an idiot all my days:) Anyway thanks for the welcome and i look forward to being a productive member of the community!

A quick update: thanks to crazy and some other forum links ive been reading i have finally corrected my driver problem, the link below was very helpfull and browsing through some of the options on Ubuntu i have found there is a driver in the synaptic package manager for nvidia, Im not sure if this works but its there....now onto my WOW problem:)

---

### Post by Rocket2DMn on 2008-10-14
Moved to Ubuntu Testimonials & Experiences - welcome!  We're glad you're enjoying yourself, the community is here to help!

---

### Post by crazyness003 on 2008-10-14
Hello, and welcome. Its very obvious you want to dive off the deep end here, and thats completely cool; but please, if possible, organize your questions a little better. Give details, and whats you've tried so far.
Lets start off with which version of Ubuntu you have. Is it 7.10 or 8.04? Is it 32bit or 64bit?
Here, run this command in your terminal
```
uname -a
```Whats this does is give you **-a**ll of info concerning your system. I have no idea what it means, but it works.
and
```
 cat /etc/issue
```

This is mine
```
Linux xxxx 2.6.27-6-generic #1 SMP Tue Oct 7 04:15:23 UTC 2008 x86_64 GNU/Linux

``````
Ubuntu intrepid (development branch) \n \l

```It tells you that you're running Linux (duh i guess), your machine name (i conceal mine for *paranoid* reasons), my kernel build number (very important info about your system), some date info, and my architecture (in my case the x86 architecture in 64 bits) and that i have Ubuntu Intrepid Ibex (which is version 8..10...its still beta)

Okay, one down.

TWO: Your graphics card is very new, in fact so new i know nothing about it (no surprise). But if I had to guess, its probably supported by the cutting-edge nvidia drivers. An easy way to get these, rather than wait for them to be updated in the repositories (something windows dosnt have, but is freaking awesome), is to download Envy. Do this by opening Synaptic Package Manager (enter root password when prompted. Remeber this requures root privileges, so what you do after you do this can and will impact your system in a good or bad way, so be careful), and searching for [FONT=Courier New]envy[/FONT]. Click on the icon to the left of it, select mark for instalation and hit apply. 
or
Type this into the terminal
```
sudo apt-get install envyng-gtk
```Enter your root password when prompted (remeber be careful after doing this)
Then it will ask you to install envyng-core and possibly fglrx-modaliases.
type "y" (no quotes) and hit return (enter)
And watch the fireworks (metaphorically speaking).
After you get this program, open it (its in your Applications -> System Tools menu)
And select nvidia, thenn let it automatically deted the drivers needed.
This might fix that problem.

btw: sudo means super user do, basically "super user" is just that super. It allows you to temporarly log in as the root administrator of the machine. This helps as a security measure (do not compare to the UAC that vista sports, that thing is useless).

Unfortunately thats all i can really help with. Good luck

---

### Post by weirdtalk on 2008-10-14
Welcome to the world of Linux

> **Linuxidiot said:**
>  when i attempt to CD to the wow folder and run the wine.exe i believe it is, i get a no file or directory message

I think thats because the command is wine not wine.exe  
So I would type: 
wine install.exe
or
wine setup.exe
or whatever the program is.

if you still get an error it's because you need to install wine.
either use synapic or type
sudo apt-get install wine

and try it again

> **Linuxidiot said:**
> 
 but i want to learn what it is im doing, why that specific code command...and im excited about learning how to code, im not a rich man so i have to teach myself... is there a freeware program i can get to teach me some of these things...

not too many programs. but tons of websites that are free, as well as these forums.

I've give two console tips. First is you can complete folder/file/command names by pressing tab.
Second the command man is a manual so for example man cd lists the ins and outs of the change directory command.

Hope that helps

---

### Post by scouser73 on 2008-10-14
Hi and welcome to the forum, you'll find lots of very helpful people here, I hope you enjoy it.

> .. is there a freeware program i can get to teach me some of these things..

Here is a site that will be of use to you, it's e-books, I can't think of an actual program. [http://www.ubuntugeek.com/free-ubuntu-linux-e-books.html]("http://www.ubuntugeek.com/free-ubuntu-linux-e-books.html")

---

