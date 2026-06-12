---
title: "Oblivion in Wine"
date: 2010-09-14
forum: Wine
---

### Post by sun_hill on 2010-09-14
Hi.  I recently received the Elder Scrolls IV: Oblivion Game of the Year edition.  I was able to successfully install it in Wine, but when I start the game, I get a great deal of flickering, essentially making the game unplayable.  I'm running 10.04 with Kernel 2.6.32-24 with all the updates (as of 09/14/2010) and I presume the most recent version of Wine.

My hardware is
Lenovo T400

Intel Core 2 Cuo 2.4 Ghz
1.9 G ram
ATI Mobility Radeon HD 3400 Series

Any help is appreciated!

---

### Post by Jazzy_Jeff on 2010-09-14
Have you turned off the Compiz Desktop Effects?

---

### Post by gradinaruvasile on 2010-09-14
It works ok in Wine 1.3.2 for me. A little slow though, but thats because of my integrated 8200 nvidia. But even the water reflections show perfectly.
I installed directx dlls via winetricks to make it play properly.

I use Debian Squeeze, no compiz and disabled compositing.

---

### Post by jpaugh64 on 2010-09-14
Well, this is a really generic reply, but sometimes running a wine  program inside the terminal can generate some useful output. A lot of  times, it will say something like "[can't find this file that I need]"  (paraphrased horribly).

To do this, open a terminal (Applications-->Accessories-->Terminal), and then type

```
user@host:~$ cd "~/.wine/drive_c/"
```This is the fake C: drive  that wine installs programs to. Then, navigate to the folder that you  installed Oblivion in (which is probably in "Program Files") using the  "cd" command like so, for example:

```
$ cd "Program Files/Oblivion"
```Then, type
```
ls *.exe
```to find every Windows program in the directory.

Then type 
```
wine name-of-program.exe
```to run the program in Wine. Look at  the text output on the terminal for any signs of trouble. Wine usually  outputs a lot of stuff--most of which means something to someone  else--so just look for things that are obviously wrong, such as "[can't  do/find this or that]."

NOTE: I haven't used Wine for a while, so my instructions are really bad. I don't remember exactly where Wine s

---

