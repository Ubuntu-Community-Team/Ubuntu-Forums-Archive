---
title: "Shared lib error"
date: 2007-05-03
forum: Ubuntuzilla
---

### Post by HughJass on 2007-05-03
Trying to install Firefox on Feisty (AMD 64) using the script. I downloaded and installed the 32bit libraries recommended. 

I get this error message when trying to start Fx

 
sandy@sandy-desktop:~$ firefox
/opt/firefox/firefox-bin: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory
sandy@sandy-desktop:~$

---

### Post by nanotube on 2007-05-03
hi
it appears that you are missing libgtk. so just run the following command to install it from the repositories:
```
sudo aptitude install libgtk2.0-0
```
that should fix the problem for you.

it is surprising you don't already have it installed, i thought it came by default with ubuntu. are you by any chance running kubuntu?

---

### Post by HughJass on 2007-05-03
Did that but the error message is identical to that posted above when I try to launch Firefox.
Maybe I should use the remove script to get back tto what I had?

---

### Post by nanotube on 2007-05-03
hi,
yea, you certainly can do the 'remove' and go back to the repos version... but first, maybe let's try to figure this out. i, for one, am curious as to what's going on. :)

could you please run
```
locate libgtk-x11-2.0.so.0
```
and post the output?

we will get to the bottom of this - if you are willing to investigate, at least. :)

---

### Post by HughJass on 2007-05-03
Well I am willing too. 
All programs are now taking 10-15 secs to open and KPPP won't work at all.
I am working with an old computer to connect with here.

Here is the output...


sandy@sandy-desktop:~$ locate libgtk-x11-2.0.so.0
/usr/lib/libgtk-x11-2.0.so.0.1000.11
/usr/lib/libgtk-x11-2.0.so.0
sandy@sandy-desktop:~$

---

### Post by nanotube on 2007-05-03
hmm, well, try this:
```
sudo aptitude reinstall ia32-libs-gtk
```

(courtesy of [http://ubuntuforums.org/archive/index.php/t-90106.html](http://ubuntuforums.org/archive/index.php/t-90106.html))

---

### Post by HughJass on 2007-05-03
It was'nt installed.

It is now and Firefox does load.

I am still having problems but will wait and try and get a better handle on them for you before I re-post.

Thanks,
Sandy

---

### Post by nanotube on 2007-05-03
> **HughJass said:**
> It was'nt installed.

It is now and Firefox does load.

I am still having problems but will wait and try and get a better handle on them for you before I re-post.

Thanks,
Sandy

ah, cool. i will add this package to the faq on our site, then.

sure, feel free to post with any other problems, i'll be glad to try to help. :)

EDIT: oh, it already was on the site in [ instructions for 64bit users]("http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla#.5BThunderbird.2C_Firefox.5D_What_you_need_to_run_Firefox_and_Thunderbird_on_64-bit_system"). :)

---

### Post by HughJass on 2007-05-04
Yes, but I did install all the recommended files except the ncurses one which it said it couldn't find.

It was after this that the rest of the system went haywire. It is pretty well unusable I'm afraid.

My uneducated guess is that lots of files are in the wrong place.

After rebooting this morning I found that none of the programs would load properly not just Firefox.

I will try uninstalling these lib32 files and see if I get the system back.

---

### Post by nanotube on 2007-05-04
hmm, well please report back.
all those packages are in the official repositories, so they /shouldn't/ cause problems, but i guess everything is possible. :)

---

