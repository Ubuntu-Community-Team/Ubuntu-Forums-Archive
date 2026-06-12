---
title: "[Project] run"
date: 2009-01-18
forum: The Cafe
---

### Post by smif1984 on 2009-01-18
Hi all,

this is the official thread of my python project. It is a small utility to launch programs and to open files. It is a powerful substitute for the alt+f2 run dialog built-in into Gnome, which i didn't like very much.

It features tab completion for commands found in PATH and for pathnames and a command history as well. 

I will keep this thread updated with news and release announcements, but you can post to report bugs or to make suggestions.

You can download it from:
[http://www.gtk-apps.org/content/show.php/run?content=96644](http://www.gtk-apps.org/content/show.php/run?content=96644)

Cheers

---

### Post by jespdj on 2009-01-19
A kind of application launcher? Do you know that there are already several of those, for example [GNOME Do](http://do.davebsd.com/)?

---

### Post by smif1984 on 2009-01-19
> **jespdj said:**
> A kind of application launcher? Do you know that there are already several of those, for example [GNOME Do](http://do.davebsd.com/)?

HI, 
yes i know that, i just wanted to write a simple program to launch programs and open files without having to install tons of mono libraries. Moreover it's more a programming exercise than a complete project. Anyway it works quite fine for me, it does the job i want from an application launcher.

Thanks for the suggestions.

Davide

---

### Post by spupy on 2009-01-19
> **smif1984 said:**
> HI, 
yes i know that, i just wanted to write a simple program to launch programs and open files _**without having to install tons of mono libraries**_. Moreover it's more a programming exercise than a complete project. Anyway it works quite fine for me, it does the job i want from an application launcher.

Thanks for the suggestions.

Davide

A++, will run again! :)

Although I have two notes:
- If a pattern is unique, why not auto-complete it to the end? That could save a lot of tabbing.
- If I type "/ho" and press Tab, it gets auto-completed to "/home", which is good, but the cursor doesn't move to the end, which is bad (when I start typing the next folder).

---

### Post by smif1984 on 2009-01-20
Yes, you are not the first one making this point to me. I'll find a solution for this for the next release. Keep it up!

---

### Post by smif1984 on 2009-01-20
> **spupy said:**
> A++, will run again! :)

Although I have two notes:
- If a pattern is unique, why not auto-complete it to the end? That could save a lot of tabbing.
- If I type "/ho" and press Tab, it gets auto-completed to "/home", which is good, but the cursor doesn't move to the end, which is bad (when I start typing the next folder).

I've just finished to implement this feature. Actually is quite useful :)

Cheers

---

### Post by spupy on 2009-01-20
> **smif1984 said:**
> I've just finished to implement this feature. Actually is quite useful :)

Cheers

Please post here when you upload new version. Thanks :)

---

### Post by smif1984 on 2009-01-31
Hi all,
i've released a new version, check it out!!!

---

### Post by spupy on 2009-01-31
> **smif1984 said:**
> Hi all,
i've released a new version, check it out!!!

Great! Autocompletion works so much better.
Although something strange is going on. If I type "/usr/bin/gedit" for example, it makes firefox ask me to save the file. :O Pictures open in firefox as well, which is kinda good. Do you try to open non-executable with the associated program? Because that would be awesome.

---

### Post by smif1984 on 2009-01-31
Hi,
all files are opened with the default application by means of the program xdg-open, installed by default in ubuntu. This works with directories, e.g. /home/ , and  other types of files but the default application depends on your settings. Actually /usr/bin/gedit is a binary file so there shouldn't be any default application: you can see this by running my program in a terminal, and trying to open the binary file. The output is:
```
Error showing url: No application is registered as handling this file

```

Actually you should run "gedit" instead of /usr/bin/gedit, otherwise my program will try to open the file, not to run it.

Cheers

P.S. pictures open with eog in my case...

---

### Post by Hells_Dark on 2009-01-31
I use gmrun..
autocompletion,etc.

---

### Post by spupy on 2009-01-31
> **smif1984 said:**
> Hi,
all files are opened with the default application by means of the program xdg-open, installed by default in ubuntu. This works with directories, e.g. /home/ , and  other types of files but the default application depends on your settings. Actually /usr/bin/gedit is a binary file so there shouldn't be any default application: you can see this by running my program in a terminal, and trying to open the binary file. The output is:
```
Error showing url: No application is registered as handling this file

```

Actually you should run "gedit" instead of /usr/bin/gedit, otherwise my program will try to open the file, not to run it.

Cheers

P.S. pictures open with eog in my case...

Yeah, I'm using Gentoo, so everything is little crazy here. :) It seems the error was on my side.

---

### Post by smif1984 on 2009-02-03
Fixed a bug handling whitespaces in filenames. I've released a new version. :)

---

### Post by smif1984 on 2009-02-03
> **Hells_Dark said:**
> I use gmrun..
autocompletion,etc.

Actually my program is very similar to gmrun with the the difference in how you search through history. I didn't like ctrl+r, so i implemented my own ideas.

---

### Post by sujoy on 2009-02-03
is this on sourceforge, launchpad or any such place? i am always looking for simple apps to get my hands dirty :). not that i am a competent coder, but i'd like to try

---

### Post by smif1984 on 2009-02-03
> **sujoy said:**
> is this on sourceforge, launchpad or any such place? i am always looking for simple apps to get my hands dirty :). not that i am a competent coder, but i'd like to try


you can find it here!

[http://www.gtk-apps.org/content/show.php/run?content=96644](http://www.gtk-apps.org/content/show.php/run?content=96644)


cheers!

---

### Post by sujoy on 2009-02-03
ok, thanks

---

### Post by antistress on 2009-03-23
i will give Run a try since i don't want any mono application running on my system either (by the way people can try jBrout instead of F-Spot it's amazing)

what about making shorcuts more discoverable for new users ?

The GUI could precise them :

run command _ o X
|_________________________________________________|
Insert command xxx matches found
o Run in terminal (ctrl+enter) o Run as root (shift+enter) Cancel Run

---

### Post by Mehall on 2009-03-23
quick comment: gmrun doesn't have mono dependencies, I don't believe. I think it has less dependencies than most any Python app could ever achieve, thoguh i can;t say for sure, not having installed this app, and already ahving python on my system for something else.

---

### Post by sujoy on 2009-03-24
gmrun
```
Depends On     : gtk2  popt 
```
data from pacman :)

---

