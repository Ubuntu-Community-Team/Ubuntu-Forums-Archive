---
title: "installing google chrome 26 in raring"
date: 2013-04-05
forum: Ubuntu Development Version
---

### Post by ptn107 on 2013-04-05
I just ran into this problem on a newly installed test machine for raring.  Be on the lookout.  The latest google chrome requires libudev0 to be installed, but it is not longer available in raring.  We have libudev1 in raring now.

To install [_google chrome 26.0.1410.43-r189671_]("https://www.google.com/intl/en/chrome/browser/") you will need to also install the following two files for your architecture, until the dependecies are modified.

_for 64-bit:_
libudev0: [_download_]("http://mirror.pnl.gov/ubuntu//pool/main/u/udev/libudev0_175-0ubuntu13_amd64.deb")
libxss1: [_download_]("http://mirror.pnl.gov/ubuntu//pool/main/libx/libxss/libxss1_1.2.2-1_amd64.deb")

Put the two files in the same folder as google-chrome-stable_current_amd64.deb.  Run
```
sudo dpkg -i *.deb
```

or

_for 32-bit:_
libudev0: [_download_]("http://mirror.pnl.gov/ubuntu//pool/main/u/udev/libudev0_175-0ubuntu13_i386.deb")
libxss1: [_download_]("http://mirror.pnl.gov/ubuntu//pool/main/libx/libxss/libxss1_1.2.2-1_i386.deb")

Put the two files in the same folder as google-chrome-stable_current_i386.deb.  Run
```
sudo dpkg -i *.deb
```

---

### Post by pfeiffep on 2013-04-05
I found it easier to install Chromium

---

### Post by slickymaster on 2013-04-05
> **ptn107 said:**
> I just ran into this problem on a newly installed test machine for raring.  Be on the lookout.  The latest google chrome requires libudev0 to be installed, but it is not longer available in raring.  We have libudev1 in raring now.

To install [_google chrome 26.0.1410.43-r189671_]("https://www.google.com/intl/en/chrome/browser/") you will need to also install the following two files for your architecture, until the dependecies are modified.

_for 64-bit:_
libudev0: [_download_]("http://mirror.pnl.gov/ubuntu//pool/main/u/udev/libudev0_175-0ubuntu13_amd64.deb")
libxss1: [_download_]("http://mirror.pnl.gov/ubuntu//pool/main/libx/libxss/libxss1_1.2.2-1_amd64.deb")

Put the two files in the same folder as google-chrome-stable_current_amd64.deb.  Run
```
sudo dpkg -i *.deb
```

or

_for 32-bit:_
libudev0: [_download_]("http://mirror.pnl.gov/ubuntu//pool/main/u/udev/libudev0_175-0ubuntu13_i386.deb")
libxss1: [_download_]("http://mirror.pnl.gov/ubuntu//pool/main/libx/libxss/libxss1_1.2.2-1_i386.deb")

Put the two files in the same folder as google-chrome-stable_current_i386.deb.  Run
```
sudo dpkg -i *.deb
```

That's strange, I'm on a 3.8.0-15-generic box, with Chrome 26.0.1410.43 (Official Build 189671) just installed without having to do none of those steps.

---

### Post by ptn107 on 2013-04-05
I have another machine that has been running raring for quite some time.  It has libudev0 and libudev1 installed.  Apparently the problem only arises in fresh installations made after 3/26/13.

---

### Post by slickymaster on 2013-04-05
> **ptn107 said:**
> I have another machine that has been running raring for quite some time.  It has libudev0 and libdev1 installed.  Apparently the problem only arises in fresh installations made after 3/26/13.

That's even stranger
```
slickymaster@PaPir:~$ uname -rv
3.8.0-15-generic #25-Ubuntu SMP Wed Mar 27 19:21:15 UTC 2013
```

---

### Post by roly33 on 2013-04-06
I had to do a clean re-install the other day & I'm now unable to Install Chrome as I keep getting a dependency error.

[ATTACH=CONFIG]241004[/ATTACH]

I never got this error when I originally installed, and was able to install Chrome.

I'm fully upto date, & I'm stumped as to how I was able to Install Chrome originally, but now get a dependancy error.

Roland

---

### Post by vasa1 on 2013-04-06
Something related maybe here: [http://ubuntuforums.org/showthread.php?t=2132483](http://ubuntuforums.org/showthread.php?t=2132483)

---

### Post by craig10x on 2013-04-06
I was just checking out live session of the beta and i see the same problem....who needs to fix that dependency problem...would that be on the ubuntu end or the chrome end?
And i was wondering if it had been reported to the appropriate place?

---

### Post by craig10x on 2013-04-06
just curious, but why do you need the screensaver file? 
wouldn't just the libudev0 file do it?  

i am running the 13.04 development which i installed 2 months ago, so of course, i don't have the problem with Chrome...but just out of curiousity, i am running the live session of 13.04 beta at the moment and the problem is there of course...

it didn't work when i used the terminal...instead i had ubuntu software center install the two dependency files first, then when i tried to install the Chrome deb file in the software center, it installed without a hitch...

Who is going to have to fix this?  Is it on the ubuntu side or chrome side?  and has it been reported to the appropriate place?  (just wondering)...

---

### Post by cariboo on 2013-04-06
merged two similar threads.

---

### Post by clanmackay on 2013-04-13
I ran into the same problem and this fixed it for me.  Thank you.

---

### Post by craig10x on 2013-04-15
There is an article here about it:
[http://www.webupd8.org/2013/04/fix-google-chrome-cant-be-installed-in.html#disqus_thread](http://www.webupd8.org/2013/04/fix-google-chrome-cant-be-installed-in.html#disqus_thread)

Apparently, google will have to fix this one, so that we would be able to install Chrome again without having to add the dependency...for now, it's only way to do it on new installs...

---

### Post by Gavin77 on 2013-04-15
I got Chrome installed using this thread but it seems to have a problem displaying Korean text, it's all squashed together.  For example on [www.naver.com](www.naver.com) 

The same version of Chrome running on Quantal doesn't have any problems.

---

### Post by Frogs Hair on 2013-04-15
Though I can't read Korean I see the same compressed text on the site posted. The site looks fine in Firefox.

---

### Post by petersicparker on 2013-04-27
works just great!!!! thanks :D

---

