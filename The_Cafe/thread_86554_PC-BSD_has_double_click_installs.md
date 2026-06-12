---
title: "PC-BSD has double click installs"
date: 2005-11-05
forum: The Cafe
---

### Post by BWF89 on 2005-11-05
PC-BSD the BSD created to make BSD easy to use as a desktop OS has a thing where all you have to do to install a program is unzip it and double click the install file to install it! It's called a PBI file.

[http://www.pcbsd.org/?p=pmscreens](http://www.pcbsd.org/?p=pmscreens)

---

### Post by kairu0 on 2005-11-05
They're doing wonder for BSD: Double-click install sounds very easy to do.

Would I want this feature in Ubuntu? Yes! :)

---

### Post by dabear on 2005-11-05
[QUOTE=kairu0]
Would I want this feature in Ubuntu? Yes! :)[/QUOTE]
We kinda already have. Take a look at gdebi, debins or my [very own dadebstaller](http://ubuntuforums.org/showthread.php?t=84314)

---

### Post by BWF89 on 2005-11-05
Only problem is that packages have to be specially ported to the PBI format. And by looking at their double click install directory ([http://www.pbidir.com/](http://www.pbidir.com/)) theres not awhole lot there.

---

### Post by xequence on 2005-11-05
It looks very promising ;) In fact, ill probably download it tomorow and try it...

---

### Post by -Rick- on 2005-11-05
Nice...my new project is aiming to get something like that on various linuxes/unixes with various frontends.

---

### Post by 23meg on 2005-11-05
[Klik]("http://klik.atekon.de/") is doing something similar for linux.

---

### Post by kairu0 on 2005-11-05
[QUOTE=xequence]It looks very promising ;) In fact, ill probably download it tomorow and try it...[/QUOTE]

I think PC-BSD is really at the "try it" stage right now. Once they get to 1.0 it'll probably be more interesting.

---

### Post by xequence on 2005-11-05
[QUOTE=kairu0]I think PC-BSD is really at the "try it" stage right now. Once they get to 1.0 it'll probably be more interesting.[/QUOTE]

Do you mean its unstable? Or is it stable, but not much functionality?

I have been looking at BSD for awhile and none seem to come with a desktop environment and an easy installer. (As far as I know, they dont really have much documentation on it to say "___BSD doesent come with a GUI")

---

### Post by Lambert on 2005-11-05
I'm not 100% sure on this, but I believe they accomplish this by deviating from the shared libraries. So each pbi installs the app in it's own stand alond directory. I've seen many posts on this learning linux where it's said to be a weakness of windows and security.

---

### Post by kairu0 on 2005-11-05
[QUOTE=xequence]Do you mean its unstable? Or is it stable, but not much functionality?

I have been looking at BSD for awhile and none seem to come with a desktop environment and an easy installer. (As far as I know, they dont really have much documentation on it to say "___BSD doesent come with a GUI")[/QUOTE]

Disclaimer: I've never used PC-BSD :) I HAVE used FreeBSD.

PC-BSD is still at major number 0.8 which means that it hasn't reach its first milestone. They're still defining the basics of what PC-BSD is going to be like at this point.

I can't say much about stability or functionality as I haven't used it.

I really hope they pull this off though, because it's about time there was a friendly BSD.

---

### Post by TravisNewman on 2005-11-06
[QUOTE=xequence]Do you mean its unstable? Or is it stable, but not much functionality?

I have been looking at BSD for awhile and none seem to come with a desktop environment and an easy installer. (As far as I know, they dont really have much documentation on it to say "___BSD doesent come with a GUI")[/QUOTE]
er? Installing the last version of freeBSD (5.3? don't remember) took about 15 minutes, and it has a pretty simple installer (if you can install slackware, you can install it), and when I was done, I had a full featured Gnome desktop and could switch to KDE if I wanted.

---

### Post by kairu0 on 2005-11-06
[QUOTE=panickedthumb]er? Installing the last version of freeBSD (5.3? don't remember) took about 15 minutes, and it has a pretty simple installer (if you can install slackware, you can install it), and when I was done, I had a full featured Gnome desktop and could switch to KDE if I wanted.[/QUOTE]

15 minutes? I wonder how the new 6.0 performs.

---

### Post by jsgotangco on 2005-11-06
Very nice. I have WPA working out of the box in my laptop.

---

### Post by xequence on 2005-11-06
[QUOTE=panickedthumb]er? Installing the last version of freeBSD (5.3? don't remember) took about 15 minutes, and it has a pretty simple installer (if you can install slackware, you can install it), and when I was done, I had a full featured Gnome desktop and could switch to KDE if I wanted.[/QUOTE]

Oh, ok, my mistake ;)

---

### Post by kairu0 on 2005-11-10
Distrowatch announced that PC-BSD 1.0RC1 is now out. Apparently, the PC-BSD team has up'd the whole system to FreeBSD 6.0. I've got to wipe off a partition and try this.

---

### Post by etc on 2005-11-10
[QUOTE=kairu0]Distrowatch announced that PC-BSD 1.0RC1 is now out. Apparently, the PC-BSD team has up'd the whole system to FreeBSD 6.0. I've got to wipe off a partition and try this.[/QUOTE]
Downloading as we speak, this is going to be interesting.

---

### Post by etc on 2005-11-11
I just installed PC-BSD and I'm impressed.
Sadly I didn't get to try out the double click installs because it didnt detect my wireless card.
But, it took about 15 minutes to install and thats amazing, it takes ubuntu about 45 minutes to an hour and windows  ~1.5 to 2 hours.

---

### Post by kairu0 on 2005-11-17
[QUOTE=etc]I just installed PC-BSD and I'm impressed.
Sadly I didn't get to try out the double click installs because it didnt detect my wireless card.
But, it took about 15 minutes to install and thats amazing, it takes ubuntu about 45 minutes to an hour and windows  ~1.5 to 2 hours.[/QUOTE]

What impressed you aside from the installation time?

---

### Post by xequence on 2005-11-17
[QUOTE=etc]I just installed PC-BSD and I'm impressed.
Sadly I didn't get to try out the double click installs because it didnt detect my wireless card.
But, it took about 15 minutes to install and thats amazing, it takes ubuntu about 45 minutes to an hour and windows  ~1.5 to 2 hours.[/QUOTE]

Only 15 minutes? Wow, how many MB/GB is the default install?

Ubuntu takes me 45 minutes and windows takes 25 minutes.

---

