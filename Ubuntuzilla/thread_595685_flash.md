---
title: "flash"
date: 2007-10-29
forum: Ubuntuzilla
---

### Post by cybergalvez on 2007-10-29
Installed flash, works with the official ubuntu firefox, but not ubuntuzilla installed version.  How can I fix this?
Jose

---

### Post by aysiu on 2007-10-29
It probably depends on how you installed Flash. How did you install it?

---

### Post by cybergalvez on 2007-10-29
> **aysiu said:**
> It probably depends on how you installed Flash. How did you install it?

I think it was from the apt-get (sorry I don't remember all that well I installed a bunch of stuff yesturday, including realplayer and java)
Jose

---

### Post by aysiu on 2007-10-29
> **cybergalvez said:**
> I think it was from the apt-get (sorry I don't remember all that well I installed a bunch of stuff yesturday, including realplayer and java)
Jose
Hm. That's weird. It would have made sense if you'd installed Flash by visiting a Flash website and following the *Install Missing Plugins* prompts.

Can you close Firefox, paste these commands into the terminal, and then open Firefox again and see if Flash works? ```
sudo apt-get update
sudo apt-get install flashplugin-nonfree
sudo mv /opt/firefox/plugins /opt/firefox/plugins.old
sudo ln -s /usr/lib/firefox/plugins /opt/firefox/plugins
```

---

### Post by nanotube on 2007-10-29
or actually, even before you do that, see what's in your
```
ls -al /opt/firefox/plugins
```

(if you follow aysiu's instructions before this, then just use
```
ls -al /opt/firefox/plugins.old
```

that /should/ contain the flash plugin...
unless gutsy puts flash somewhere else? 

could you also post output of
```
sudo dpkg -L flashplugin-nonfree
```
just to see where the files go?

---

### Post by cybergalvez on 2007-10-29
I'm pretty sure the flash plugin is there, I looked last night and saw it last night.  The odd thing is when I goto a page with flash I basically get a blank spot where the flash should load not no error message, if I uninstall ubuntuzilla then flash works, with it installed flash does not work.  I've also had some general problems installed plugins bascally if I install a plugin it's not usable until I go through a round of uninstall and reinstall of firefox
Jose

---

### Post by nanotube on 2007-10-29
> **cybergalvez said:**
> I'm pretty sure the flash plugin is there, I looked last night and saw it last night.  

well, the major question is, /where/ did you look? :) 

hm, could be something new with gutsy. hey aysiu, do you happen to be running gutsy or have a livecd handy - could you see if you can reproduce this? if you don't have gutsy handy, then i guess i'll have to burn a livecd and test myself. :)

---

### Post by aysiu on 2007-10-29
I upgraded to Gutsy on two computers and had no Flash issues. Of course, I'm using the Ubuntu builds, not the Mozilla ones, so it's possible they may have switched up locations. I'll check and get back to you on it.

---

### Post by aysiu on 2007-10-29
Okay: ```
**sudo dpkg -L flashplugin-nonfree**
/.
/usr
/usr/lib
/usr/lib/xulrunner
/usr/lib/xulrunner/plugins
/usr/lib/mozilla
/usr/lib/mozilla/plugins
/usr/lib/iceape
/usr/lib/iceape/plugins
/usr/lib/iceweasel
/usr/lib/iceweasel/plugins
/usr/lib/firefox
/usr/lib/firefox/plugins
/usr/lib/midbrowser
/usr/lib/midbrowser/plugins
/usr/lib/flashplugin-nonfree
/usr/share
/usr/share/doc
/usr/share/doc/flashplugin-nonfree
/usr/share/doc/flashplugin-nonfree/copyright
/usr/share/doc/flashplugin-nonfree/changelog.gz
/usr/share/lintian
/usr/share/lintian/overrides
/usr/share/lintian/overrides/flashplugin-nonfree
/var
/var/lib
/var/lib/flashplugin-nonfree
/var/cache
/var/cache/flashplugin-nonfree
```

---

### Post by nanotube on 2007-10-29
hey thanks
but unfortunately, that doesn't tell me much, because the package is just a shell that downloads and installs the adobe plugin from the macromedia site. 

so cybergalvez, could you please post output of the following commands:
```
ls -ald /opt/firefox/plugins
```
```
ls -al /opt/firefox/plugins
```

first one should show that the dir is a link to /usr/lib/firefox/plugins, and the second will list the contents of the dir, which should show "firefox-flashplugin.so" in there somewhere.

(or aysiu, if you care to test by installing ubuntuzilla... :) )

---

### Post by cybergalvez on 2007-10-30
hey thanks
but unfortunately, that doesn't tell me much, because the package is just a shell that downloads and installs the adobe plugin from the macromedia site. 

so cybergalvez, could you please post output of the following commands:
```
ls -ald /opt/firefox/plugins
```
jc@phoenix:~$ ls -ald /opt/firefox/plugins
lrwxrwxrwx 1 root root 24 2007-10-28 21:31 /opt/firefox/plugins -> /usr/lib/firefox/plugins


```
ls -al /opt/firefox/plugins
```
jc@phoenix:~$ ls -al /opt/firefox/plugins
lrwxrwxrwx 1 root root 24 2007-10-28 21:31 /opt/firefox/plugins -> /usr/lib/firefox/plugins



first one should show that the dir is a link to /usr/lib/firefox/plugins, and the second will list the contents of the dir, which should show "firefox-flashplugin.so" in there somewhere.

(or aysiu, if you care to test by installing ubuntuzilla... :)

---

### Post by nanotube on 2007-10-30
> **cybergalvez said:**
> 
```
ls -ald /opt/firefox/plugins
```
jc@phoenix:~$ ls -ald /opt/firefox/plugins
lrwxrwxrwx 1 root root 24 2007-10-28 21:31 /opt/firefox/plugins -> /usr/lib/firefox/plugins

nice, that's as expected

> 
```
ls -al /opt/firefox/plugins
```
jc@phoenix:~$ ls -al /opt/firefox/plugins
lrwxrwxrwx 1 root root 24 2007-10-28 21:31 /opt/firefox/plugins -> /usr/lib/firefox/plugins


ah sorry, the second command should end with a /:
```
ls -al /opt/firefox/plugins/
```
please give it another go :)

---

### Post by cybergalvez on 2007-10-30
> **nanotube said:**
> nice, that's as expected



ah sorry, the second command should end with a /:
```
ls -al /opt/firefox/plugins/
```
please give it another go :)

Ok I did that and this is what I got:
```
jc@phoenix:~/Downloads/firefox$ ls -al /opt/firefox/plugins/
total 40
drwxr-xr-x 2 root root  4096 2007-10-08 17:25 .
drwxr-xr-x 6 root root  4096 2007-10-28 21:52 ..
lrwxrwxrwx 1 root root    37 2007-10-27 23:05 flashplugin-alternative.so -> /etc/alternatives/firefox-flashplugin
lrwxrwxrwx 1 root root    57 2007-10-28 20:58 gcjwebplugin.so -> /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/gcjwebplugin.so
lrwxrwxrwx 1 root root    39 2007-10-28 20:43 libjavaplugin.so -> /etc/alternatives/firefox-javaplugin.so
-rwxr-xr-x 1 root root 19160 2007-10-08 17:25 libnullplugin.so
lrwxrwxrwx 1 root root    36 2007-10-25 20:51 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 root root    37 2007-10-25 20:51 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 root root    34 2007-10-25 20:51 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root root    35 2007-10-25 20:51 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 root root    36 2007-10-25 20:51 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 root root    37 2007-10-25 20:51 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 root root    42 2007-10-25 20:51 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 root root    43 2007-10-25 20:51 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rw-r--r-- 1 root root 11456 2007-10-22 06:38 libunixprintplugin.so
lrwxrwxrwx 1 root root    34 2007-10-28 15:45 nphelix.so -> /opt/RealPlayer/mozilla/nphelix.so
lrwxrwxrwx 1 root root    35 2007-10-28 15:45 nphelix.xpt -> /opt/RealPlayer/mozilla/nphelix.xpt

```

Jose

---

### Post by nanotube on 2007-10-30
> **cybergalvez said:**
> Ok I did that and this is what I got:
```
jc@phoenix:~/Downloads/firefox$ ls -al /opt/firefox/plugins/
lrwxrwxrwx 1 root root    37 2007-10-27 23:05 flashplugin-alternative.so -> /etc/alternatives/firefox-flashplugin

```


well, that shows that flash plugin is in there, so firefox should be detecting it...

when you launch the ubuntuzilla firefox, and then go to "about:plugins", does flash show up there?

---

### Post by cybergalvez on 2007-10-30
> **nanotube said:**
> well, that shows that flash plugin is in there, so firefox should be detecting it...

when you launch the ubuntuzilla firefox, and then go to "about:plugins", does flash show up there?

yes it shows up, it just does not work
Jose

---

### Post by nanotube on 2007-10-30
hm, that's strange... in that case, i am kind of at a loss...
could it be that it's one of the issues affecting 2.0.0.8?

[http://developer.mozilla.org/devnews/index.php/2007/10/22/firefox-2008-update-to-be-updated/](http://developer.mozilla.org/devnews/index.php/2007/10/22/firefox-2008-update-to-be-updated/)

try using ubuntuzilla to remove 2.0.0.8, install 2.0.0.7 (when it asks whether 2.0.0.8 is right, say no, and enter manually "2.0.0.7"), and see if that solves the problem. 
maybe that would also resolve your other thread ([http://ubuntuforums.org/showthread.php?t=595671](http://ubuntuforums.org/showthread.php?t=595671))

if not... then the other thing to try may be to manually copy the flashplayer.so into /opt/firefox/plugins/

---

### Post by cybergalvez on 2007-11-02
I've been working on this and it gets odder.  I uninstall flash (with apt-get) and then downloaded flash from adobe and followed the instructions on installing it using the nswrapper.  If I run firefox.ubuntu it works fine, if I run firefox the plugin won't load.  In both cases about:plugin shows that the plugin is installed.  Any thoughts about what is going on?
Jose

---

### Post by cybergalvez on 2007-11-02
More info if I run the "ubuntu" firefox npviewer loads when I goto a flash page, if however I load the ubuntuzilla firefox and go to the same page, it does not load.  Is there a config file that needs editing?
Jose

---

### Post by nanotube on 2007-11-05
ah hmm... well, i don't really know what nswrapper is, nor npviewer... are you running the plugins through some kind of wrapper lib? (is it for like 64bit machines or something?)
that could be the cause of these weird problems...

---

### Post by bbrg548 on 2007-11-12
I have fixed this problem on my system. I could not run Flash in the ubuntuzilla firefox, but it would work if I ran "firefox.ubuntu" from the terminal (or changed the launcher to run "firefox.ubuntu").

I'm on a 64 bit system (AMD Turion 64x2). Ubuntu uses "flashplugin-alternatative.so" (probably a 64-bit version) and it looks like ubuntuzilla won't work with that.

I downloaded the .tar.gz package from Adobe's website and extracted it to my desktop, then copied "libflashplayer.so" and "flashplayer.xpt" to my ./.mozilla/plugins/ directory. Problem fixed.

The same trick will work with java. I downloaded the java ".bin" from Sun's website, moved it to /usr/java/ and ran it from a terminal. Then (in the terminal) I changed to my .mozilla/plugins directory and ran:

> ln -s /usr/java/jre1.6.0_03/plugin/i386/ns7/libjavaplugin_oji.so ./libjavaplugin_oji.so


Java now works in my ubuntuzilla build.

I figured this out after finding this page that was linked in another thread:
[http://plugindoc.mozdev.org/faqs/firefox-linux.html#install-where]("http://plugindoc.mozdev.org/faqs/firefox-linux.html#install-where")

-Jake

---

### Post by behanj on 2008-09-25
@bbrg548

Old post now byt -

Thank you for posting your fix

This got Flash working in my Firefox

My spec:
AMD64
Ubuntu Hardy Heron 64
Firefox 3.0.2 from Ubuntuzilla

---

