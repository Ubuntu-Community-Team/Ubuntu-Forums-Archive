---
title: "Wine is hiding somewhere"
date: 2010-06-11
forum: Wine
---

### Post by ubuntoooooo on 2010-06-11
I have a couple problems, mostly what I want is to get rid of wherever wine is hiding in this install of lucid. That would be the initial problem.
I've done 'sudo apt-get remove/purge wine' and it says it isn't there. I've erased the .wine folder and the .PlayOnLinux folder that I'm sure was part of the whole mess.
Now I've exhausted some time searching out a cure, but my wordings were probably never correct.

Secondly, or a kind of compromise, if I could get help with making a script to run through PlayOnLinux where I can launch Steam with the alsa-oss work around for some games.

While I would prefer the second option, I'd like to know for future reference the answer to the first as well. 
Any insight is appreciated, I feel so basic asking such a simple question.

---

### Post by cogadh on 2010-06-11
If you've already run those commands and deleted the .wine and .PlayOnLinux directories, then Wine is gone. What makes you think it is still there?

---

### Post by ubuntoooooo on 2010-06-11
I guess when I try to install wine from a .tar of version 1.1.43 via the './tools/wineninstall' way of compiling, it states there is a wine version still present.

```
Wine Installer v1.0

Warning !! wine binary (still) found, which may indicate
a (conflicting) previous installation.
You might want to abort and uninstall Wine first.
(If you previously tried to install from source manually, 
run 'make uninstall' from the wine root directory)

```

The reason for building from 1.1.43 is because that is the version I desire for the program that uses the alsa-oss work around.

[edit]: I would go ahead and just install it anyways, but the reason I think it really is still there is because of a persistent error in Steam. The error is not present on PlayOnLinux with the same features, which, if possible I would prefer a way to use the alsa-oss work around via PlayOnLinux.
Perhaps I should be posting over there for that.

---

### Post by cogadh on 2010-06-11
Did you ever install Wine from source before? If so, just follow what the error message says to get rid of it. You definitely do not have any of the prepackaged versions from the repositories after running those previous uninstall commands, so an old source install would seem to me to be the only way it might still be hanging around.

---

### Post by ubuntoooooo on 2010-06-11
I probably should have included that I did 'make uninstall' after I got that message. There was nothing that that did, I guess I can just attempt to run 'winecfg' and it'll build itself back up so I can get the exact error message.

```
------desktop:~/.wine$ make uninstall
make: *** No rule to make target `uninstall'.  Stop.

```

So yeah, that's already been done. But you are right, sort've I did install from source. But I tried to delete the /.wine folder and /.playonlinux first because I got that first error about wine being there off the bat.

Yeah sorry, I should have included that.

---

### Post by cogadh on 2010-06-11
That doesn't look like the right directory to run the "make uninstall" in. You need to do that in the directory that contains the Wine source code, not Wine's "fake Windows" directory.

---

### Post by ubuntoooooo on 2010-06-11
I'm sorry but can you elaborate on that a little? I tried to do it from the folder where I did the initial install from ~/Desktop/wine-1.1.43 and it gives me the same message as just before:

"make: ***no rule to make target uninstall...~" etc

EDIT
> i-desktop:~/Desktop/wine-1.1.43$ sudo dpkg -r wine
[sudo] password for i: 
dpkg: warning: ignoring request to remove wine which isn't installed.
i-desktop:~/Desktop/wine-1.1.43$ 


went through the readme again to apply the same to the "source folder"(still not sure if) and I just thought I'd say this to in case I was in the right place.

---

### Post by cogadh on 2010-06-11
I'm not sure if I can really elaborate more. Whatever directory you have the source code for your previous Wine install in is the directory you need to run the "make uninstall" in; it will be the same directory you ran the compile commands in. I'm assuming that wine-1.1.43 is the only source version you have ever tried to install, so if that directory is the one that you currently have the source code in, it should work. If you have installed any other source versions of Wine in the past, then you need to run the "make uninstall" in their respective source directories.

---

### Post by ubuntoooooo on 2010-06-11
This is the right idea I think, I guess I need to try to back track if I've ever installed an earlier wine?
I wish I could post on PlayOnLinux but I'm having incredible difficulty getting an account with their current system of signing up for the forums.

Thanks,
but on the off chance I didn't install any others from source? I've checked synaptic and the little GUI add/remove thing.

I just can't remember if I've installed from source at all. It would be infinitely easier if I could just get my PlayOnLinux to use alsa-oss. But I dunno, I'll let you know if I get this solved.

---

### Post by ubuntoooooo on 2010-06-11
I fixed it, I had to go into the /root/ folder and just search out all the Wine entries. Now I'm compiling again so far, without any errors.

This should also hopefully absolve me of that blasted bin/vgui2 message when I boot up Steam.

---

