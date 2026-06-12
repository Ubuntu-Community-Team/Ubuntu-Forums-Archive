---
title: "Ubuntuzilla causing broken packages"
date: 2010-10-25
forum: Ubuntuzilla
---

### Post by griztown on 2010-10-25
Somehow, after installing ubuntuzilla, my packages for Firefox got broken when trying to upgrade.  Now I get the following message and I can't figure out how to get around it.

E: /var/cache/apt/archives/firefox_3.6.11+build3+nobinonly-0ubuntu0.10.04.1_i386.deb: trying to overwrite '/usr/bin/firefox', which is also in package firefox-mozilla-build 0

Any suggestions?

---

### Post by lovinglinux on 2010-10-25
Removed

---

### Post by griztown on 2010-10-25
I ran that but it didn't seem to work. I still get the same error message.

---

### Post by lovinglinux on 2010-10-26
> **griztown said:**
> I ran that but it didn't seem to work. I still get the same error message.

Try

```
sudo apt-get purge firefox-mozilla-build
sudo apt-get purge firefox
```

Then install which one you want, with:

```
sudo apt-get install firefox
```

or

```
sudo apt-get install firefox-mozilla-build
```

---

### Post by griztown on 2010-10-26
Thanks for the help.  When I run the first I get this error:


You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  firefox-branding: Depends: firefox (= 3.6.11+build3+nobinonly-0ubuntu0.10.04.1)
  firefox-gnome-support: Depends: firefox (= 3.6.11+build3+nobinonly-0ubuntu0.10.04.1)
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

I then tried 'apt-get -f install' which threw this error:

dpkg: error processing /var/cache/apt/archives/firefox_3.6.11+build3+nobinonly-0ubuntu0.10.04.1_i386.deb (--unpack):
 trying to overwrite '/usr/bin/firefox', which is also in package firefox-mozilla-build 0:3.6.11-0ubuntu1
Errors were encountered while processing:
 /var/cache/apt/archives/firefox_3.6.11+build3+nobinonly-0ubuntu0.10.04.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by lovinglinux on 2010-10-26
> **griztown said:**
> Thanks for the help.  When I run the first I get this error:


You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  firefox-branding: Depends: firefox (= 3.6.11+build3+nobinonly-0ubuntu0.10.04.1)
  firefox-gnome-support: Depends: firefox (= 3.6.11+build3+nobinonly-0ubuntu0.10.04.1)
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

I then tried 'apt-get -f install' which threw this error:

dpkg: error processing /var/cache/apt/archives/firefox_3.6.11+build3+nobinonly-0ubuntu0.10.04.1_i386.deb (--unpack):
 trying to overwrite '/usr/bin/firefox', which is also in package firefox-mozilla-build 0:3.6.11-0ubuntu1
Errors were encountered while processing:
 /var/cache/apt/archives/firefox_3.6.11+build3+nobinonly-0ubuntu0.10.04.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Try 

```
sudo apt-get purge firefox-mozilla-build
```

---

### Post by DooM55 on 2010-10-26
try

```


sudo apt-get purge firefox

sudo apt-get install firefox

sudo apt-get update


```:popcorn:

---

### Post by griztown on 2010-10-26
I appreciate all of your help.  None of these solutions have worked.  

I keep getting an error that there are packages with unmet dependencies, namely firefox.  But if I try installing firefox it tells me I can't install firefox cause I'd overwrite another firefox in firefox-mozilla-build.  I can't purge firefox-mozilla-build cause I have unmet dependencies.  A classic Catch-22!  Is there some nuclear bomb method I can try here?

---

### Post by nanotube on 2010-10-27
what's your output if you try to ```
sudo apt-get remove firefox-mozilla-build
```
and also what's your output for ```
dpkg-divert --list
```

---

### Post by griztown on 2010-10-27
> **nanotube said:**
> what's your output if you try to ```
sudo apt-get remove firefox-mozilla-build
```
Here's what I get:
```
The following packages have unmet dependencies:
  firefox-branding: Depends: firefox (= 3.6.11+build3+nobinonly-0ubuntu0.10.04.1)
  firefox-gnome-support: Depends: firefox (= 3.6.11+build3+nobinonly-0ubuntu0.10.04.1)
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```
> and also what's your output for ```
dpkg-divert --list
```
This is the output:
```
diversion of /bin/sh to /bin/sh.distrib by dash
diversion of /usr/share/man/man1/sh.1.gz to /usr/share/man/man1/sh.distrib.1.gz by dash
local diversion of /usr/bin/mozilla-firefox to /usr/bin/mozilla-firefox.ubuntu
diversion of /usr/share/vim/vim72/doc/help.txt to /usr/share/vim/vim72/doc/help.txt.vim-tiny by vim-runtime
diversion of /usr/share/vim/vim72/doc/tags to /usr/share/vim/vim72/doc/tags.vim-tiny by vim-runtime
diversion of /usr/share/dict/words to /usr/share/dict/words.pre-dictionaries-common by dictionaries-common
diversion of /usr/share/dbus-1/services/org.freedesktop.Notifications.service to /usr/share/dbus-1/services/org.freedesktop.Notifications.service.notify-osd by notify-osd
diversion of /usr/lib/gnupg/gpgkeys_curl to /usr/lib/gnupg/gpgkeys_curl.non_curl by gnupg-curl
diversion of /usr/lib/gnupg/gpgkeys_hkp to /usr/lib/gnupg/gpgkeys_hkp.non_curl by gnupg-curl
diversion of /usr/share/gnome-games/pixmaps/slot.svg to /usr/share/gnome-games/pixmaps/slot.svg.unbranded by branding-ubuntu
diversion of /usr/share/gnome-games/pixmaps/baize.png to /usr/share/gnome-games/pixmaps/baize.png.unbranded by branding-ubuntu
diversion of /usr/share/gnome-games/mahjongg/pixmaps/postmodern.svg to /usr/share/gnome-games/mahjongg/pixmaps/postmodern.svg.unbranded by branding-ubuntu
diversion of /usr/share/gnome-games/gnometris/pixmaps/gnometris.svg to /usr/share/gnome-games/gnometris/pixmaps/gnometris.svg.unbranded by branding-ubuntu
diversion of /usr/share/gnome-games-common/cards/gnomangelo_bitmap.svg to /usr/share/gnome-games-common/cards/gnomangelo_bitmap.svg.unbranded by branding-ubuntu
diversion of /var/lib/gdm/.gconf.defaults/%gconf-tree.xml to /var/lib/gdm/.gconf.defaults/%gconf-tree.xml.ubuntu by xubuntu-gdm-theme
```

---

### Post by nanotube on 2010-10-28
hmm, maybe try removing packages firefox-branding and firefox-gnome-support ?

btw, curious, how did this happen? did you use the ubuntuzilla.py install script at all, or were you always on the repository?

---

### Post by griztown on 2010-10-28
> **nanotube said:**
> hmm, maybe try removing packages firefox-branding and firefox-gnome-support ?

btw, curious, how did this happen? did you use the ubuntuzilla.py install script at all, or were you always on the repository?

So it recommends I run 'apt-get -f install' which I do and then I get this message

```
dpkg: error processing /var/cache/apt/archives/firefox_3.6.11+build3+nobinonly-0ubuntu0.10.04.1_i386.deb (--unpack):
 trying to overwrite '/usr/bin/firefox', which is also in package firefox-mozilla-build 0:3.6.11-0ubuntu1
Errors were encountered while processing:
 /var/cache/apt/archives/firefox_3.6.11+build3+nobinonly-0ubuntu0.10.04.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

When I try installing firefox-branding or firefox-gnome-support I get the unmet dependencies error.

I don't remember exactly how I got here but I know I was using the repositories.  I think I uninstalled something in an attempt to upgrade firefox to 3.6.

---

### Post by nanotube on 2010-10-28
try running the following:

```
sudo dpkg-divert --package firefox-mozilla-build --add --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
```

then run ```
sudo apt-get -f install
``` again. this may resolve the conflict.

---

### Post by griztown on 2010-10-28
> **nanotube said:**
> try running the following:

```
sudo dpkg-divert --package firefox-mozilla-build --add --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
```

then run ```
sudo apt-get -f install
``` again. this may resolve the conflict.

It was going along marvelously ... then it failed.  Here's what it said:

```
Installing new version of config file /etc/apparmor.d/usr.bin.firefox ...
Installing new version of config file /etc/apport/blacklist.d/firefox ...
update-alternatives: error: alternative path /usr/bin/firefox doesn't exist.
dpkg: error processing firefox (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of firefox-gnome-support:
 firefox-gnome-support depends on firefox (= 3.6.12+build1+nobinonly-0ubuntu0.10.04.1); however:
  Package firefox is not configured yet.
dpkg: error processing firefox-gnome-support (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 firefox
 firefox-gnome-support
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by nanotube on 2010-10-29
does file /usr/bin/firefox exist for you?

---

### Post by griztown on 2010-10-29
> **nanotube said:**
> does file /usr/bin/firefox exist for you?

No

```
$ ls /usr/bin/firefox
ls: cannot access /usr/bin/firefox: No such file or directory

```

---

### Post by nanotube on 2010-10-29
ah, i guess one of the posts above has instructed you to remove it heh.
well... two questions then... how about /usr/bin/firefox.ubuntu , can you ls -l that one?

and also... recreate the /usr/bin/firefox linking to the mozilla build, with this command:
```
sudo ln -s /opt/firefox/firefox /usr/bin/firefox
```

---

### Post by blainep0 on 2010-10-29
I am having the same problem. After reading through here I have ran both remove and purge on firefox and firefox-mozilla-build but some how my Firefox link still works (launches 3.6.11) and when I try to install the newest mozilla buildI get:

[I]Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  firefox-mozilla-build
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/11.4MB of archives.
After this operation, 0B of additional disk space will be used.
Selecting previously deselected package firefox-mozilla-build.
(Reading database ... 250721 files and directories currently installed.)
Unpacking firefox-mozilla-build (from .../firefox-mozilla-build_3.6.12-0ubuntu1_i386.deb) ...
dpkg-divert: `diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu by firefox-mozilla-build' clashes with `local diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu'
dpkg: error processing /var/cache/apt/archives/firefox-mozilla-build_3.6.12-0ubuntu1_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 2
dpkg-divert: mismatch on package
  when removing `diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu by firefox-mozilla-build'
  found `local diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu'
dpkg: error while cleaning up:
 subprocess new post-removal script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/firefox-mozilla-build_3.6.12-0ubuntu1_i386.deb
localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB
localepurge: Disk space freed in /usr/share/doc/kde/HTML: 0 KiB

Total disk space freed by localepurge: 0 KiB

E: Sub-process /usr/bin/dpkg returned an error code (1)
[/I]
Since I saw it asked earlier, I was at one point using the old ubuntuzilla.py but swapped once it was possible. I haven't had any issues up until this though.

Sorry, forgot to mention that this is a 10.04 machine, originally installed 8.04 and has gotten each upgrade as its became available, but LTS locked it after upgrading to 10.04. I have another more recent install of 8.04 on a dinosaur machine that is having no problem with Ubuntuzilla.

---

### Post by RJARRRPCGP on 2010-10-29
Looks like the FS could be corrupted. Sorry. :( 

The problem may just be a file-locking issue. (like Microsoft!)

---

### Post by lovinglinux on 2010-10-29
> **nanotube said:**
> ah, i guess one of the posts above has instructed you to remove it heh.
well... two questions then... how about /usr/bin/firefox.ubuntu , can you ls -l that one?

and also... recreate the /usr/bin/firefox linking to the mozilla build, with this command:
```
sudo ln -s /opt/firefox/firefox /usr/bin/firefox
```

I guess it was my suggestion. I have already removed the code, but I don't know why it didn't work, since the command was supposed to replace it with the diverted version.

Perhaps the user should remove all info about firefox and firefox-mozilla-build from dpkg, then install again.

---

### Post by blainep0 on 2010-10-30
Perhaps a stupid question, but would it be safe to assume my issue is my own fault? Like I mentioned earlier, the troubled machine has had the ubuntuzilla.py installer at one point but the fresher install has never had it.

When I did the fresh install, I simply Googled Ubuntuzilla and found the new apt repo, and when I was finished there I went to the other machine and just removed the .py and added the repo.

Until tonight I'd never seen the plainly wrote out instructions -- "Current users of ubuntuzilla should run "ubuntuzilla.py -a remove -p  yourpackage" before installing these packages, to undo the local  diversion of /usr/bin/(package) links."

So in theory (had I not been an idiot and just decided to reformat and install a fresh 10.10 before reading a little deeper) could I have just reinstalled ubuntuzilla.py, then correctly remove it to fix the issue I was having, since it looks like there were some some dpk-divert errors in my log?

---

### Post by nanotube on 2010-10-30
> **blainep0 said:**
> Perhaps a stupid question, but would it be safe to assume my issue is my own fault? Like I mentioned earlier, the troubled machine has had the ubuntuzilla.py installer at one point but the fresher install has never had it.

When I did the fresh install, I simply Googled Ubuntuzilla and found the new apt repo, and when I was finished there I went to the other machine and just removed the .py and added the repo.

Until tonight I'd never seen the plainly wrote out instructions -- "Current users of ubuntuzilla should run "ubuntuzilla.py -a remove -p  yourpackage" before installing these packages, to undo the local  diversion of /usr/bin/(package) links."

So in theory (had I not been an idiot and just decided to reformat and install a fresh 10.10 before reading a little deeper) could I have just reinstalled ubuntuzilla.py, then correctly remove it to fix the issue I was having, since it looks like there were some some dpk-divert errors in my log?

yes, it your case, it seems that all you'd have had to do was to remove the local dpkg diversion for /usr/bin/firefox, and then you'd have been ok....

---

### Post by nanotube on 2010-10-30
> **lovinglinux said:**
> I guess it was my suggestion. I have already removed the code, but I don't know why it didn't work, since the command was supposed to replace it with the diverted version.

Perhaps the user should remove all info about firefox and firefox-mozilla-build from dpkg, then install again.

hey, yea dunno what exactly happened there... but then again i also am not sure what exactly caused this user's problem, since he says he hasn't used the .py script... and to date, everyone with this problem has gotten them for failure to run ubuntizilla.py remove script as the instructions suggest...

---

### Post by griztown on 2010-10-31
> **nanotube said:**
> ah, i guess one of the posts above has instructed you to remove it heh.
well... two questions then... how about /usr/bin/firefox.ubuntu , can you ls -l that one?

and also... recreate the /usr/bin/firefox linking to the mozilla build, with this command:
```
sudo ln -s /opt/firefox/firefox /usr/bin/firefox
```

Hi everybody, sorry for the delay.  Thanks for all the help by the way.

I ran ls -l on /usr/bin/firefox.ubuntu and this is what I have:
```
$ ls -l /usr/bin/firefox.ubuntu
lrwxrwxrwx 1 root root 32 2010-10-28 22:50 /usr/bin/firefox.ubuntu -> ../lib/firefox-3.6.12/firefox.sh

```

I created the link and tried to run ```
sudo apt-get -f install
``` but it failed again with this error:```
dpkg: error processing firefox (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of firefox-gnome-support:
 firefox-gnome-support depends on firefox (= 3.6.12+build1+nobinonly-0ubuntu0.10.04.1); however:
  Package firefox is not configured yet.
dpkg: error processing firefox-gnome-support (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 firefox
 firefox-gnome-support
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by nanotube on 2010-11-01
first, just to make sure, i want to see if your link is looking right, try ```
ls -al /usr/bin/firefox
```

second, the error seems to suggest that firefox (the ubuntu repos version) is not properly installed... so maybe try "sudo apt-get install firefox" ?

---

### Post by griztown on 2010-11-10
> **nanotube said:**
> first, just to make sure, i want to see if your link is looking right, try ```
ls -al /usr/bin/firefox
```

second, the error seems to suggest that firefox (the ubuntu repos version) is not properly installed... so maybe try "sudo apt-get install firefox" ?

Sorry for the delay, I was out of town for about a week and a half.

Here are the results of the ls command:
```
$ ls -al /usr/bin/firefox
lrwxrwxrwx 1 root root 20 2010-10-31 22:03 /usr/bin/firefox -> /opt/firefox/firefox
```

After running sudo apt-get install firefox I got this error:

```
Setting up firefox (3.6.12+build1+nobinonly-0ubuntu0.10.04.1) ...
update-alternatives: error: alternative path /usr/bin/firefox doesn't exist.
dpkg: error processing firefox (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of firefox-gnome-support:
 firefox-gnome-support depends on firefox (= 3.6.12+build1+nobinonly-0ubuntu0.10.04.1); however:
  Package firefox is not configured yet.
dpkg: error processing firefox-gnome-support (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 firefox
 firefox-gnome-support
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

So somehow I need to configure firefox?

---

### Post by griztown on 2010-11-15
So is this a lost cause?  How can I get back to no broken packages?  Is there some nuclear option?

---

### Post by nanotube on 2010-11-16
> **griztown said:**
> So is this a lost cause?  How can I get back to no broken packages?  Is there some nuclear option?

let's undivert the /usr/bin/firefox symlink:
```
sudo dpkg-divert --package firefox-mozilla-build --remove --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
```

now, check to see where /usr/bin/firefox points you:
```
ls -al /usr/bin/firefox
```
you should see this:
```
lrwxrwxrwx 1 root root 32 2010-10-28 22:50 /usr/bin/firefox -> ../lib/firefox-3.6.12/firefox.sh
```

If that is indeed the case, try running
```
sudo apt-get install firefox
```
and hopefully that'll go through this time. :)

---

### Post by griztown on 2010-11-16
> **nanotube said:**
> let's undivert the /usr/bin/firefox symlink:
```
sudo dpkg-divert --package firefox-mozilla-build --remove --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
```



Arrrgggh!  I can't perform the first command:

```
Removing `diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu by firefox-mozilla-build'
dpkg-divert: rename involves overwriting `/usr/bin/firefox' with
  different file `/usr/bin/firefox.ubuntu', not allowed
```

---

### Post by nanotube on 2010-11-17
ok, so before you do that, then, do 
```
sudo rm -rf /usr/bin/firefox
```

from there, follow the steps

---

### Post by griztown on 2010-11-17
> **nanotube said:**
> ok, so before you do that, then, do 
```
sudo rm -rf /usr/bin/firefox
```

from there, follow the steps

Alright!  This worked.  Now I can use firefox.  But when I try and run my update manager, it fails on firefox with this error.

```
E: /var/cache/apt/archives/firefox-mozilla-build_3.6.12-0ubuntu1_i386.deb: trying to overwrite '/usr/bin/firefox', which is also in package firefox 0
```

So do I need to uninstall this firefox package before running the upgrade?  I'm wondering if I did something similar that got me into this mess in the first place.

Thanks!

---

### Post by nanotube on 2010-11-18
try ```
sudo apt-get remove firefox-mozilla-build
```

---

### Post by griztown on 2010-11-30
Thanks Nanotube!  That worked and now I have no more broken packages.  So what would be the proper way to install firefox so I don't screw things up?

---

### Post by nanotube on 2010-12-02
great! finally we did it. :)

as far as installing the mozilla builds... first, make sure you don't have any ubuntu-mozilla-daily or other "third-party" ppas dealing with firefox enabled... then you can just install firefox-mozilla-build. now that your diversion problems are solved, things should 'just work'. :)

---

### Post by griztown on 2010-12-02
> **nanotube said:**
> great! finally we did it. :)

as far as installing the mozilla builds... first, make sure you don't have any ubuntu-mozilla-daily or other "third-party" ppas dealing with firefox enabled... then you can just install firefox-mozilla-build. now that your diversion problems are solved, things should 'just work'. :)

Yep!  Thanks again Nanotube!

---

### Post by nanotube on 2010-12-03
> **griztown said:**
> Yep!  Thanks again Nanotube!

you're welcome, enjoy your firefox! :)

---

### Post by witeshark17 on 2011-03-04
> **nanotube said:**
> let's undivert the /usr/bin/firefox symlink:
```
sudo dpkg-divert --package firefox-mozilla-build --remove --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
```

now, check to see where /usr/bin/firefox points you:
```
ls -al /usr/bin/firefox
```
you should see this:
```
lrwxrwxrwx 1 root root 32 2010-10-28 22:50 /usr/bin/firefox -> ../lib/firefox-3.6.12/firefox.sh
```

If that is indeed the case, try running
```
sudo apt-get install firefox
```
and hopefully that'll go through this time. :) At this point I get this:

ls -al /usr/bin/firefoxls: cannot access /usr/bin/firefox: No such file or directory

and

sudo apt-get remove firefox-mozilla-buildReading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package firefox-mozilla-build

Can PPA purge help?

[http://www.webupd8.org/2010/08/ppa-purge-added-to-official-ubuntu-1010.html](http://www.webupd8.org/2010/08/ppa-purge-added-to-official-ubuntu-1010.html)

---

### Post by Karlchen on 2011-03-07
Hello, whiteshark17.

The error message which you receive >  Unable to locate package firefox-mozilla-build seems to suggest that you have already uninstalled Firefox-Mozilla-Build succesfully. Or [you have never installed the Firefox-Mozilla-Build from the Ubuntuzilla repository]("http://ubuntuforums.org/showpost.php?p=10514329&postcount=6") at all, but from some other location. In the latter case you might want to uninstall that package first.

Why do you insist on performing the uninstallation on the commandline, although it seems to be unclear which commandline is the appropriate one? Why don't you use the Synaptic GUI, select the Installed Applications part and search for Firefox? Synaptic will only present what has been installed. All you need to do then is selecting Firefox for removal and apply.

Anyway, afterwards you should be fine going ahead and installing the original Ubuntu Firefox version.
```
sudo apt-get update
sudo apt-get install firefox
```Kind regards,
Karl

---

### Post by witeshark17 on 2011-03-07
> **Karlchen said:**
> Hello, whiteshark17.

The error message which you receive  seems to suggest that you have already uninstalled Firefox-Mozilla-Build succesfully. Or [you have never installed the Firefox-Mozilla-Build from the Ubuntuzilla repository]("http://ubuntuforums.org/showpost.php?p=10514329&postcount=6") at all, but from some other location. In the latter case you might want to uninstall that package first.

Why do you insist on performing the uninstallation on the commandline, although it seems to be unclear which commandline is the appropriate one? Why don't you use the Synaptic GUI, select the Installed Applications part and search for Firefox? Synaptic will only present what has been installed. All you need to do then is selecting Firefox for removal and apply.

Anyway, afterwards you should be fine going ahead and installing the original Ubuntu Firefox version.
```
sudo apt-get update
sudo apt-get install firefox
```Kind regards,
Karl Thanks for the reply!

---

