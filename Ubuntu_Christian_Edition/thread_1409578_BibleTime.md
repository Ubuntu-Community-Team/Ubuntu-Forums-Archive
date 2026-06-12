---
title: "BibleTime"
date: 2010-02-17
forum: Ubuntu Christian Edition
---

### Post by rsaavedra74 on 2010-02-17
Hello friends,

I just installed Bible Time with hopes of doing my Bible Studies electronically and couldn't find the NIV or how to add it in the books are of the software. If anyone knows how to, can you be so kind and share it with me?

Thanks,
Raf

---

### Post by mavrick13927 on 2010-02-17
Raf,

NIV is not a freely distributable Bible edition.  You would need to buy it regardless of OS or Bible study tool used.  

Bibletime is "using the Sword programming library to work with Bible texts, commentaries, dictionaries and books provided by the Crosswire Bible Society."

Looking at the FAQ on crosswire web page is the official answer below along with suggesting other free comparable versions (ESV and NET)

[http://www.crosswire.org/index.jsp?section=FAQ#Do_you_or_will_you_have_NIV.2FNASB.2FNLT.2FMessage.2FNKJV.2Fother_translation.3F](http://www.crosswire.org/index.jsp?section=FAQ#Do_you_or_will_you_have_NIV.2FNASB.2FNLT.2FMessage.2FNKJV.2Fother_translation.3F)

I hope that helps.  God bless.

---

### Post by rsaavedra74 on 2010-03-21
> **mavrick13927 said:**
> Raf,

NIV is not a freely distributable Bible edition.  You would need to buy it regardless of OS or Bible study tool used.  

Bibletime is "using the Sword programming library to work with Bible texts, commentaries, dictionaries and books provided by the Crosswire Bible Society."

Looking at the FAQ on crosswire web page is the official answer below along with suggesting other free comparable versions (ESV and NET)

[http://www.crosswire.org/index.jsp?section=FAQ#Do_you_or_will_you_have_NIV.2FNASB.2FNLT.2FMessage.2FNKJV.2Fother_translation.3F](http://www.crosswire.org/index.jsp?section=FAQ#Do_you_or_will_you_have_NIV.2FNASB.2FNLT.2FMessage.2FNKJV.2Fother_translation.3F)

I hope that helps.  God bless.Thanks a lot for your help!!!

Friends I encountered this error when I tried to install any bible or book  into BT 2.0: "The destination directory is not writable or does not exist. Installation will fail unless this has first been fixed." 
I'm new to Linux  and have no idea how to tinker much with it yet... I tried to google the error but unfortunately nothing comes to light... :( Can anyone point me in the right direction?

Thanks and God Bless!!!
Raf

---

### Post by frad70 on 2010-03-27
Go to Settings / Bookshelf Manager and change Install Folder path from something that looks like /etc/.sword to /home/your_name/.sword where your_name is probably rsavedra or robert or whatever you have chosen as your login 

Greetings from London!

Rad
[www.frad70.webs.com](www.frad70.webs.com)

---

### Post by Deer Hunter on 2010-04-09
I realize that this won't be a direct answer to your actual problem, but give this a thought:

If you're using Ubuntu 9.10 CE (just checking because you can use BibleTime on standard Ubuntu as well), try out a free program called e-Sword.  Some kind people on this sub-forum have made it possible to install the latest version of this great program, along with any and all add-ons, just like you would use it in Windows.  Many commentaries and Bible versions are available for free download from [www.e-sword.net;](www.e-sword.net;) although I'll be up-front with you and say that there are some commentaries and Bible versions too that you have to purchase a security key in order to install them (NIV is $29.99 as I type this).

Anyway, like I said this may not be exactly what you're looking for, but I like the program, and if you're interested it's definitely worth checking out.  Best wishes as you study God's Word!

Davis

---

### Post by Subito Piano on 2011-01-22
There's been a lot of arguments as to which Bible program is best, and like others i've had my personal preference - BUT when a friend pointed me to [www.theword.net]("http://www.theword.net") i found something that truly was superior.  You may not like it, i understand, but it has far more tools -- perhaps more geared to a Bible teacher than the layman.  It works very well under wine with different distro's, and it's worth checking out.  :-)

---

### Post by ubuntu27 on 2011-01-22
You might be interested in using another Bible program called [Bible Analyzer]("http://bibleanalyzer.com/"), for more information on how to install it, [go to this thread]("http://ubuntuforums.org/showthread.php?t=1625790").

Good luck!

---

### Post by Subito Piano on 2011-01-22
Sounds interesting -- but i have AMD 64-bit architecture and there is only an i386 deb....

---

### Post by marl30 on 2011-01-23
> **Subito Piano said:**
> Sounds interesting -- but i have AMD 64-bit architecture and there is only an i386 deb....
Use the PPA on the first page of the thread the guy above shared. That's what I used to install it. I'm also running 64 bit.

---

### Post by Subito Piano on 2011-01-23
Yeah i did that, trying apt-get, but it didn't work.  I posted my terminal output at [that thread]("http://ubuntuforums.org/showthread.php?t=1625790&page=2").  (I don't want to turn this into a duplicate thread, maybe i should have just posted my problems either here or there instead of both threads - sorry!)

---

### Post by ubuntu27 on 2011-01-23
You can install 32bit program on 64 bit Linux.

To install 32-bit deb to 64 bit Ubuntu/Debian Linux:

1) Open the terminal
2) navegate to where the deb is (use "cd" command)
3) type ```
sudo dpkg -i --force-architecture NAME-of-deb.deb
```


That should be it.

More info can be [found here]("http://www.unixtutorial.org/2008/03/install-32-bit-deb-packages-on-64-bit/") or [here]("http://microwavebiscuit.wordpress.com/2007/02/23/how-to-get-32-bit-packages-installed-in-64-bit-ubuntu/"), or even [here as well]("http://askubuntu.com/questions/7863/is-it-ok-to-force-install-an-32-bit-debian-package-on-amd64")

---

### Post by Subito Piano on 2011-01-23
I forced it -- made sure i had  python-wxgtk2.8 (>= 2.8.8.1) and  python-wxgtk2.8 (>= 2.8.8.1) 
BUT i still get

************ Starting Bible Analyzer *************
Traceback (most recent call last):
  File "/usr/share/bibleanalyzer/analyzer3.py", line 6, in <module>
    import wx, re, wx.html, sys, os, cStringIO
  File "/usr/lib/python2.6/dist-packages/wx-2.8-gtk2-unicode/wx/__init__.py", line 45, in <module>
    from wx._core import *
  File "/usr/lib/python2.6/dist-packages/wx-2.8-gtk2-unicode/wx/_core.py", line 4, in <module>
    import _core_
ImportError: /usr/lib/python2.6/dist-packages/wx-2.8-gtk2-unicode/wx/_core_.so: symbol _ZN21wxMemoryFSHandlerBase19AddFileWithMimeTypeERK8wxStringPKvmS2_, version WXU_2.8 not defined in file libwx_baseu-2.8.so.0 with link time reference

Honestly --- thanks for everyone's help but it's not worth it, Between BibleTime and theWord i've got plenty of resources.  I use this only for my personal study and for teaching HS Bible; i don't use it enough to warrant further efforts.  Thanks for the help.

---

### Post by warroomcbw on 2011-01-30
> **ubuntu27 said:**
> You might be interested in using another Bible program called [Bible Analyzer]("http://bibleanalyzer.com/"), for more information on how to install it, [go to this thread]("http://ubuntuforums.org/showthread.php?t=1625790").

Good luck!

Bible Analyzer is easy to install under WINE using the windows exe install files. I've been an e-sword user for years and I love it...I had them both installed in ubuntu.  It goes much better with Davids' GUI's and patches(way better than the old ways).  Recently I did take interest in Bible Analyzer and really like it, but I'm not done yet with the testing of it.  It installs easy using the above mentioned method.  I must admit though, I will never give up on E-sword.  It's been too good of a friend.
Happy Hunting.
cbw

---

### Post by Shabakthanai on 2011-03-28
Distributor ID:	LinuxMint 
Description:	Linux Mint 10 KDE 4.6.0
Release:	10 
Codename:	julia 
Motherboad:  ASUS M3N-HT Deluxe Mempipe
Processor:  AMD Phenom 9600 Black Box QuadCore 2300mhz
4gb AXIOM ECC DDR2 SDRAM 667mhz
DVDRW 16x SATA
Western Digital 1tb SATA HDD
Maxtor 500gb SATA HDD

I just installed Bibletime 2.5 in KDE Mint 10 64bit after a recent upgrade from 32bit to 64bit.

**Highlight**nolonger appears as an option.  Is this a change in the 64bit version or am I missing where to change the configuration?  TIA

If not, how do I highlight a portion of scripture.

---

### Post by jonathonblake on 2011-04-04
> **Shabakthanai said:**
> 
I just installed Bibletime 2.5 in KDE Mint 10 64bit after a recent upgrade from 32bit to 64bit.

Try using the current version of BibleTime.

> **Highlight**nolonger appears as an option. 

Can you post a screenshot of what you are referring to here?

jonathon

---

