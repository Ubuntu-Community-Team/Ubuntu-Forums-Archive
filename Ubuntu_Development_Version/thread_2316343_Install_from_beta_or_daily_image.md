---
title: "Install from beta or daily image?"
date: 2016-03-07
forum: Ubuntu Development Version
---

### Post by cogset on 2016-03-07
What would be the best way to set up a Xenial installation (or a development version in general)?

I've tried the Xenial beta image and it will boot to a live session but the actual installer didn't load before the live session, whilst the daily build I had tried a few weeks before did have a working installer (or at least that's what it looked like...) although the live session was kind of a rough ride with errors popping here and there: so, in case I'd like to have an alternative Xenial installation (just for testing), where should I start from?

Maybe try the beta disk again and install directly from the live session (skipping the installer), or perhaps download a current daily build?

I'd think that the daily image may be ahead of the beta release, but also potentially have more bugs: however, since the beta image seems to be not entirely reliable either, what do you suggest?

Edit: I'm talking about a "real" installation to disk, I'm not so interested at the moment in trying Xenial in a virtual environment.

---

### Post by sudodus on 2016-03-07
Start from the daily iso file :-)

If it does not work, try again with tomorrow's daily build.

The developing version works most of the time, but remember that your installed system might fail suddenly, so don't use it as your production system, or at least have a backup system based on a released version!

---

### Post by jerrylamos on 2016-03-07
For years I prefer to install from daily image which I update with zsync.
I've 3 partitions here, a 14.04.4 LTS which usually works, and two partitions with Xenial which may be busted for one function or the other.
Since I'm looking for bugs an ordinary user might get, I alternate development level installs every couple weeks.  
Latest post beta daily .iso is somewhat srewed up so I've switched back to the previous Xenial, updated sudo apg-get update sudo apt-get dist-upgrade every day or so.

Not uncommon for Alpha and Beta images to be out of date.  They are just a snapshot in time.

Not hard to install.  I've an exec that does a lot of the setup plus hand installs of Google-Chrome, samba smb.conf, various settings.

Most files are saved onto an Archive accessible to all 3 partitions.

And if I want a bruising I can boot Windows 10.  Ugh.  Slow.  Beaucoup inline code for programs and processes I have never used, don't use, and never will.  I'm conversant at some level with Win 10 to help my wife who maintains a couple web sites with software not available on linux.

---

### Post by grahammechanical on 2016-03-07
> I'd think that the daily image may be ahead of the beta release, but  also potentially have more bugs: however, since the beta image seems to  be not entirely reliable either, what do you suggest?

This near to the release date = less bugs. It really makes no difference as Ubuntu stopped using Alpha & Beta as miles stones some months ago.

There are three ways we can put in an install

1) Let the live session load to the screen with a dialog that offers Try Ubuntu or Install Ubuntu. We click Install Ubuntu.
2) Let the live session load to the screen with a dialog that offers Try Ubuntu or Install Ubuntu. We click Try Ubuntu and at the live session desktop we click the Install Ubuntu icon.
3) At the first purple screen with the icons of a human & a keyboard we press Enter. Then we select a Language and press Enter. At the Underlying screen we get these options.

a) Try Ubuntu without installing
b) Install Ubuntu
c) Check disc for defects
d) Test memory
e) Boot from first hard disk.

All of these ways to start the installer should work. But a couple of years ago I could only get a daily image to run the installer by choosing the third option.

If you are having problems running the live session you may need to use one or more of the F6 options. See Changing the CD's Boot Options. section 6 - F6

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Regards

---

