---
title: "install multiple versions of firefox in linux"
date: 2012-01-10
forum: Tutorials
---

### Post by COKEDUDE on 2012-01-10
Since apt-get and yum won't let you install multiple versions of firefox I will explain how to here. 

1. Go to this page and decide which version of firefox you want. 
[ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/](ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/)
I used this one. 
[ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/9.0.1/linux-i686/en-US/firefox-9.0.1.tar.bz2](ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/9.0.1/linux-i686/en-US/firefox-9.0.1.tar.bz2)

2. Unzip the archive
```
tar -zxvf firefox-9.0.1.tar.bz2

```-z means filter the archive through gzip
-x extract
-v verbose
-f file name

3. Put firefox in its own directory. 
```
mv firefox firefox-9.0.1

```

4. Make a backup of your profile direcory
```
cp -r /home/bob/.mozilla /home/bob/.mozilla3

```
If you use seamonkey or thunderbird there profile info will also be there. 

4. Create a new profile so you don't corrupt your old profile. 
```
firefox -CreateProfile "firefox-9.0.1 /home/bob/.mozilla/firefox/firefox-9.0.1"

```This is my profile name **firefox-9.0.1** and this is my profile directory **/home/bob/.mozilla/firefox/firefox-9.0.1**

5. Run firefox 9.0.1 from the directory I put it in. 
```
/home/bob/firefox-9.0.1/firefox -no-remote -P firefox-9.0.1

```/home/bob/firefox-9.0.1/firefox is my install directory 
-no-remote allows to use firefox 9.0.1 and my old version of firefox
-P is the profile option
firefox-9.0.1 is the name of my profile

These 2 links go into more depth if you are interested. 
[http://www.libre-software.net/how-to-install-firefox-on-ubuntu-linux-mint](http://www.libre-software.net/how-to-install-firefox-on-ubuntu-linux-mint)
[http://odyniec.net/blog/2010/02/running-multiple-versions-of-firefox-in-ubuntu-9-10/](http://odyniec.net/blog/2010/02/running-multiple-versions-of-firefox-in-ubuntu-9-10/)

Don't do this like one of the links say to do. 
```
firefox -no-remote -CreateProfile firefox-3.6
```
That creates a profile called firefox-3.6 like you would expect but it puts profile in the firefox directory instead of creating its own separate directory. So in this case it would be in **/home/bob/.mozilla/firefox/** instead of **/home/bob/.mozilla/firefox/firefox-3.6** like you would expect.

---

### Post by neu5eeCh on 2012-05-22
I've been using this technique for several iterations of Ubuntu.

Lately, however, I notice that whenever I start any profile that isn't *default*, even when I've specified the profile in the command line (using the -P option), I _still_ get the "Choose User Profile" dialogue window (and _even_ when I've checked off the "Don't Ask at Startup" option). Is this annoyance a bug?

---

