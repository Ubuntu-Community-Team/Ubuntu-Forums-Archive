---
title: "ruler software? measure distance between two points on screen"
date: 2009-10-04
forum: The Cafe
---

### Post by mainstreetexile on 2009-10-04
Hi, does anyone know of any ruler software that would allow you to click two points on the screen and give you the measurement between those points in pixels (or whatever other unit)?

The only thing I've found is KRuler (and its gnome equivalent), which is alright but very basic and only allows you to measure straight horizontal or vertical distances.

---

### Post by Sean Moran on 2009-10-04
I understand why my ScreenRuler (of the KDE equiv if you run that) wouldn't work, but don't have any answers other than add X^2 to Y^2 and square root it for the diagonal measurement
:KS

---

### Post by mainstreetexile on 2009-10-04
Hi Sean, thanks for the reply, I guess you're right and I could go pythagorean on it :)

Even that would be easier if there were a ruler program that showed measurements for both axes on the window at the same time or it might be easier if there was a way to rotate the measurement window.  I guess there isn't any existing app that'll let me click one point, click a second point and get a measurement between them though.

---

### Post by doorknob60 on 2009-10-04
I was bored, so I made one (I used some code from other people, but combined it all into one hackish but working solution).

[http://doorknob60.is-a-geek.org/files/screenruler-0.1.tar.gz](http://doorknob60.is-a-geek.org/files/screenruler-0.1.tar.gz)

Extract that, keep the two files in the same folder, and run the sh file. Requires gcc (compiler) and zenity (Gnome dialog displayer thingy). Give it a try :) Seems to work fine for me, but I need some testers.

---

### Post by Sean Moran on 2009-10-04
> **doorknob60 said:**
> I was bored, so I made one (I used some code from other people, but combined it all into one hackish but working solution).

[http://doorknob60.is-a-geek.org/files/ruler.tar.gz](http://doorknob60.is-a-geek.org/files/ruler.tar.gz)

Extract that, keep the two files in the same folder, and run the sh file. Requires gcc (compiler) and zenity (Gnome dialog displayer thingy). Give it a try :) Seems to work fine for me, but I need some testers.
Brilliant work.

After I pressed ENTER twice I got 'Change is  Pixels' with no value but probably because I'm testing Karmic. :KS

---

### Post by doorknob60 on 2009-10-04
Do you get any terminal output? Also, do you have gcc installed and working, and both files in the same directory. Again, I made it about 10 minutes ago and have only tested it on my Arch box, so it's sure to have problems, and with feedback I can hopefully fix them :D gcc is included in the build-essential meta-package [Clicky]("apt:build-essential") Also can someone make sure my math is right, I'm tired so I'm honestly not sure if I got it right, but I think it is :P

EDIT: Funny, when I don't run it in the terminal, I also get the "Change is pixels" thing, run it from the terminal and it should work. Odd, don't know why it would do that...

EDIT2: Or maybe you're getting (standard_in) 1: parse error, happens in certain parts of the screen (corners?), meh I'll see what I can do about that one :P

---

### Post by mainstreetexile on 2009-10-04
man, thats awesome! i was having the same problem as sean but only for coordinates on the far left side of the screen. it looks like there's a problem with the way you're splitting up the value with the 'cut' command in your script though since the coordinates from getcurpos aren't zero padded.

i changed the relevant lines in ruler.sh from this:

```

X1=`./getcurpos | cut -c1-4`
Y1=`./getcurpos | cut -c5-10`

```

to this (uses a space delimiter instead of a set # of characters):
```

X1=`./getcurpos | cut -d " " -f 1`
Y1=`./getcurpos | cut -d " " -f 2`

```

and the same for the lines for X2 and Y2 and it works great!

here's the updated script (i commented out the gcc/rm lines in my copy after compiling):

```

#!/bin/bash
gcc -Wall -lX11 getcurpos.c -o getcurpos
zenity --info --text="Press enter for first mouse position"
X1=`./getcurpos | cut -d " " -f 1`
Y1=`./getcurpos | cut -d " " -f 2`
zenity --info --text="Press enter for second mouse position"
X2=`./getcurpos | cut -d " " -f 1`
Y2=`./getcurpos | cut -d " " -f 2`
XC=`echo "${X1}-${X2}" | bc | awk ' { if($1>=0) { print $1} else {print $1*-1 }}'`
YC=`echo "${Y1}-${Y2}" | bc | awk ' { if($1>=0) { print $1} else {print $1*-1 }}'`
zenity --info --text="Change is `echo "sqrt(${XC}^2+${YC}^2)" | bc -l` pixels"
rm getcurpos

```

---

### Post by Sean Moran on 2009-10-04
> **doorknob60 said:**
> Do you get any terminal output? Also, do you have gcc installed and working, and both files in the same directory. Again, I made it about 10 minutes ago and have only tested it on my Arch box, so it's sure to have problems, and with feedback I can hopefully fix them :D gcc is included in the build-essential meta-package [Clicky]("apt:build-essential")
I wouldn't have a clue what 'zenity' means either.

It's a stock 9.10 beta downloaded on Oct 1, installed Oct 2, and I've been really choicy about the apt-gets, so no gcc unless it's part of the standard issue.  The script still picked up the ENTER key from the GUI and wrote a nice message, and that's about all I logged in here to learn on this Sunday.  The main thing I thought was totally cool was how quickly you put the solution together beyond Pythagoras.  I'll leave the incidentals to you since it was almost perfect if it isn't already.

---

### Post by doorknob60 on 2009-10-04
Thanks for the changes, but I already made some changes of my own (removed the need for using cut altogether). It seems to work fine now. New link: [http://doorknob60.is-a-geek.org/files/screenruler-0.1.tar.gz](http://doorknob60.is-a-geek.org/files/screenruler-0.1.tar.gz) Actually your version is probably more efficient than mine though :P

Sean might work for you too. gcc I'm not sure if it's included by default, but it's a very standard program, and you'll end up needing it eventually (it's what you use to compile any program). Still doesn't work from double clicking though (only from terminal). Any idea why it wouldn't work that way?

Also, I know it's weird that it compiles and then deletes the programs after each run, but out of simplicity I though it would be easier that way, and since the programs are only a few lines they compile instantly anyways.

---

### Post by mainstreetexile on 2009-10-04
Looks good to me, thanks for whipping that up, it works great and it does exactly what I needed!

As far as not working when double-clicked, it might be because the current working directory is different when its ran from konqueror etc vs running it from the directory itself in your terminal emulator.

If you put this line in ruler.sh somewhere, you'll see what I mean:

```
zenity --info --text="Current directory is `pwd`"
```

For me it defaults to my home directory, so it won't find the `./x` program (I guess unless you extracted those files to your home directory).

---

### Post by Sean Moran on 2009-10-04
> **doorknob60 said:**
> Thanks for the changes, but I already made some changes of my own (removed the need for using cut altogether). It seems to work fine now. New link: [http://doorknob60.is-a-geek.org/files/ruler-0.1.tar.gz](http://doorknob60.is-a-geek.org/files/ruler-0.1.tar.gz)

Sean might work for you too. gcc I'm not sure if it's included by default, but it's a very standard program, and you'll end up needing it eventually (it's what you use to compile any program). Still doesn't work from double clicking though (only from terminal). Any idea why it wouldn't work that way?
I ran it from Nautilus as an 'admin/desktop' user.  Let me try it from gTerm, as is.  BRB.

```

flash@crash-koala:~$ Download/ruler.sh
gcc: getcurpos.c: No such file or directory
Download/ruler.sh: line 4: ./getcurpos: No such file or directory
Download/ruler.sh: line 5: ./getcurpos: No such file or directory
Download/ruler.sh: line 7: ./getcurpos: No such file or directory
Download/ruler.sh: line 8: ./getcurpos: No such file or directory
(standard_in) 2: syntax error
(standard_in) 2: syntax error
(standard_in) 1: syntax error
rm: cannot remove `getcurpos': No such file or directory
flash@crash-koala:~$ 

```This awakened the gTerm.  It might be that gcc is not yet installed***, because I'm concentrating on basics like panel and menu in the context of binary 1s and 0s and left/right-brain sorts of arts and sciences, but it looks like you've put the icing on the cake by now, isn't it?

---o0o----

*** actually I'd guess the contrary, and probably something simple I don't have the mindset hexadecimal to see at first glance right now.

---

### Post by doorknob60 on 2009-10-04
No, gcc looks like it's installed. You just need to cd into the directory where the files are located for it to work (I told you it was hackish :D). I'm making an Arch PKGBUILD for it right now (lol) and maybe if I feel like it I could make a deb? That eliminates the issues (my Arch one doesn't have that problem right now).

EDIT: Oh yeah, I just made a page for it lmao [http://doorknob60.is-a-geek.org/wiki/index.php/Screen_Ruler](http://doorknob60.is-a-geek.org/wiki/index.php/Screen_Ruler)

---

### Post by Viva on 2009-10-04
There is a ruler screenlet

---

