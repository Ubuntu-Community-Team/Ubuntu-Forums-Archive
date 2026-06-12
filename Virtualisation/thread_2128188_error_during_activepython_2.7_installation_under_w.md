---
title: "error during activepython 2.7 installation under wine &lt;SOLVED&gt;"
date: 2013-03-22
forum: Virtualisation
---

### Post by al.adab on 2013-03-22
hello,

Until a couple of days ago I was using Calibre 0.9.24 in combination with ActivePython 2.7.2.5 (Windows MSI X86) and PyCrypto 2.3 (for 32bit Windows and Python 2.7). Both ActivePython & PyCrypto run under Wine 1.5.26. I know of a Linux version of Python, though I can't figure out how to use it for purposes of Calibre ebook-adding/-converting. The Windows version worked all right

Recently I had to completely re-install Xubuntu 12.04. After re-installing Wine, and while installing ActivePython (and then PyCrypto), a window popped up: sorry I don't have the whole error message, it said something like 

*pythonw.exe has encountered a problem and needs to close. We are sorry for the inconvenience.* (if I remember correctly, it also said that this error might be due to some deficiency in Wine).

As I closed the error message window, the installation was completed (or so it seemed, no further error messages were given) and now both AP and PyC appear to be correctly installed in the Main Menu under Wine. The things is that the Calibre ebook conversion no longer works, and I don't really know if this has anything to do with the error message above. 

How can I make sure that ActivePython and PyCrypto work correctly under Wine? Alternatively, how can I make use of their Linux equivalent and "force" Calibre to use them? 

Thanks for your help!

---

### Post by al.adab on 2013-03-22
brief update: Wine>Programs>ActivePython 2.7>Python Package Manager = see error message (same as during installation) on screenshot in attachment. Btw, neither Wine>Programs>ActivePython 2.7>"Idle (Python Gui)" nor >"Python Interactive Shell" respond (if that's relevant at all). 

I've just a) re-installed ActivePython, b) re-installed Xubuntu 12.04 (and consequently Wine, etc), to no avail. The same error message keeps on popping up. I can't find anything relevant under the Wine Application Database...

---

### Post by schragge on 2013-03-22
Do I understand correctly that my suggestion in [thread=2123310]that thread[/thread] didn't work? Or you just want to have the latest version of Calibre? Look, the Calibre in *precise* is currently at version 0.8.38. In order to use the Linux native port of Calibre you either stick with that version or backport the latest version from *raring* youself as there's currently no Calibre PPA for *precise*.

Alternatively, if you upgrade to *quantal*, there is [a PPA]("https://launchpad.net/%7En-muench/+archive/calibre") for *quantal* with latest Calibre packages backported from *raring*.

---

### Post by al.adab on 2013-03-22
had to give up trying the "Then put the plugin into folder where Calibre would see it, install and configure it from inside Calibre" suggestion in your thread. When I did try, I didn't get anywhere, sorry. I had to resort to the Windows version. 

My old laptop won't take *quantal* (for some reason I can't remember). Though can we please go back to my question: I'm not interested in having the latest version of Calibre, in fact I couldn't care less. But ActivePython 2.7 did work under Wine 1.5 and now it doesn't. Wine 1.5 works fine in Xubuntu 12.04, as far as I can see. I've just posted a thread in the Wine forum, hope someone gets back to me from there. Ideas?

---

### Post by al.adab on 2013-03-24
update: i was advised to set an override for msvcr90 in winecfg. Error message is gone. Thanks for your help.

---

