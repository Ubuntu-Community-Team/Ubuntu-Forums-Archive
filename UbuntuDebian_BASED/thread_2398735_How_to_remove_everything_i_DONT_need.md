---
title: "How to remove everything i DONT need?"
date: 2018-08-16
forum: Ubuntu/Debian BASED
---

### Post by warmango on 2018-08-16
So im trying to remove all the software that isnt nessecary for the desktop interface to run, i am running Knoppix 8.2 DVD 64bit from a Live Frugal install on USB.  Any ideas? below is a list of all my installed software that came with it.  [https://paste.ubuntu.com/p/GBhmN2YzZQ/](https://paste.ubuntu.com/p/GBhmN2YzZQ/)

---

### Post by QIII on 2018-08-16
Hello!

It would be difficult to say how Knoppix' packages are set up and what dependencies might be involved.  That's probably something the Knoppix developers would be familiar with.  You might try the [Knoppix forum]("http://www.knoppix.net/forum/").

If you get no help on the forum, you may try contacting Klaus or his colleagues [here]("http://knopper.net/kontakt/").  Don't worry that it's in German.  Aside from the request that you first try to get an answer on their forum, there's nothing really important there unless you are seeking commercial support, which will cost you 60 Euro.  Asking your question in English will likely be fine.

That said, what is among the list of things you don't need to run the desktop is somewhat dependent on what *you* need from the desktop.  There are rarely definitive lists of "what you can remove" for any distro.

Cheers!

---

### Post by warmango on 2018-08-16
I tried the forums, but i was unable to make ANY FREAKING POST in ANY SUBFORUM on the page... yeah... i think i will just contact them directly, Thanks!

---

### Post by yancek on 2018-08-18
A Live install of Knoppix as with any other Linux, is a read-only system and not modifiable as is.  It doesn't matter if it is a 'frugal' install on a hard drive or if it is on a DVD or flash drive.  You would probably need to do this before you install by loop mounting it or use squashfs tools which is not a simple process..  It would probably be easier to do a full install which will enable you to more easily remove software you don't want/need.  If you read the Knoppix documentation, you will see that it was originally created to be used as a Live CD/DVD, is based on Debian and uses packages from different versions/releases of Debian and if you start modifying them, you will likely run into incompatibility problems.  The link below at the knoppix site discusses the problems with this.

[http://knoppix.net/wiki/Full_HD_install_-_warning](http://knoppix.net/wiki/Full_HD_install_-_warning)

Knoppix was designed for very specific reasons and I'm not sure what your end goal is.  You may be better off using some other minimal OS which has only the software tools you want.  Some Linux distributions allow you to select individual software packages during the install.  Slackware is one that I am aware of but I expect selecting individual package would probably take a full day to install and then you would need to remaster it with tools such as mkisofs, genisoimage or xorisso.

---

