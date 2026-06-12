---
title: "[SOLVED] SMILE installed"
date: 2008-08-23
forum: Ubuntu Studio
---

### Post by Creative2 on 2008-08-23
i was reading a post where it said ...SMILE it's hard to install in ubuntu...really

well today i have download  2 rpm([http://rpmlinux.org/rpm](http://rpmlinux.org/rpm)) files and i have converted with alien et voila' i have got it..

[CENTER]**[SIZE="6"]HOW TO[/SIZE] :**[/CENTER]

**NB DON'T MINIMIZE OR RESIZE SMILE WINDOWS OR YOU WILL HAVE SOME PROBLEM.....  _FOR INTEL GRAPHIC CARD USER ONLY _**

[B]
[COLOR="Red"]Edit now 0.7.3[/COLOR][/B] is out you can easly use it just donwload and double click on "smile" file (after you have installed the packages you can see right down here)

1 turn on medibuntu repo see here  [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

2 and of course you have to fix dvd-slideshow&#8230;if you have not already done

```
 sudo apt-get install sox libsox-fmt-all ffmpeg
```
this replace 192 with 192k
```
 sudo sed -i &#8217;s/-ab 192/-ab 192k/g&#8217; /usr/bin/dvd-slideshow 
```

then just install these debian package


i have upload there packages converted :

[http://www.mediafire.com/?n0yxzrdj1tj](http://www.mediafire.com/?n0yxzrdj1tj)
[http://www.mediafire.com/?s2xmtm0ml3m](http://www.mediafire.com/?s2xmtm0ml3m)
[B]
Then open a terminal and type [/B]

```
smile 
```

it will be loaded

---

### Post by Creative2 on 2008-08-26
just updated what i have done to get smile

---

### Post by DWright on 2008-08-27
Any chance of you uploading a deb package for SMILE 0.7.3?

---

### Post by Creative2 on 2008-08-28
i am using 0.7.3 .... just installl 0.7.2 as you can read in this topic then download 0.7.3 unpack it in your home or where you want and then create a laucher linked to smile file and it works :)

---

### Post by hjoakim on 2008-11-15
Is there a deb package for latest version? Can't seem to find it and noob at all other instructions how to install latest version with the help of the terminal. Ubuntu should be user-friendly but I find my self sitting here for 2 hours now finding information on how to solve all problems with installing SMILE on Ubuntu, which obviously is not any help for me :(

I miss the old.exe files for windows with just one click and it was installed hehe :D

I have version 0.7.2 installed.

Grateful for any help!

---

### Post by 4ebees on 2008-11-16
> **Creative2 said:**
> i am using 0.7.3 .... just installl 0.7.2 as you can read in this topic then download 0.7.3 unpack it in your home or where you want and then create a laucher linked to smile file and it works :)

Maaaaaaaaaaaate, Thanks for that. Much appreciated. "Good work" says I...street cred :))

---

### Post by hjoakim on 2008-11-22
After running

sudo sed -i ’s/-ab 192/-ab 192k/g’ /usr/bin/dvd-slideshow

I get

sed: -e expression #1, char 1: unknown command: `&#65533;'

How can I fix this?

---

### Post by #!/bin/bash on 2008-11-30
> **hjoakim said:**
> After running

sudo sed -i &#8217;s/-ab 192/-ab 192k/g&#8217; /usr/bin/dvd-slideshow

I get

sed: -e expression #1, char 1: unknown command: `&#65533;'

How can I fix this?

That s/b
sudo sed -i 's/-ab 192/-ab 192k/g' /usr/bin/dvd-slideshow

NOTE: You should maybe do this also:
sudo sed -i 's/-ab 192/-ab 192k/g' /usr/bin/dvd-menu

---

### Post by #!/bin/bash on 2008-12-07
dvd-slideshow-0.8.2 takes care of alot of bugs.

---

### Post by celticbhoy on 2009-02-11
Get this on .deb install of webkit

---

