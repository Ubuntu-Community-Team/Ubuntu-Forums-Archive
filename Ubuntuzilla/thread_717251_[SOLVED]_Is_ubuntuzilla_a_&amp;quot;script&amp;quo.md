---
title: "[SOLVED] Is ubuntuzilla a &amp;quot;script&amp;quot;?"
date: 2008-03-06
forum: Ubuntuzilla
---

### Post by Mark_in_Hollywood on 2008-03-06
I installed ubuntuzilla today from Sourceforge using:

ubuntuzilla-4.4.5-0ubuntu1-i386.deb

the package dowloaded and the "Install" radio button was ready. I closed Firefox, clicked install and watched the software installer work. A few seconds later it was gone and everything was A-OK.

Later upon restarting my Gutsy, running FF causes it to lock, and slow and a box pops up on screen saying a script is running and do I want to cancel it. I try to click yes, but the computer is now almost frozen.

So I go back to the uninstall instructions and do:

mark@Lexington-19:~$ sudo apt-get remove --purge ubuntuzilla
[sudo] password for mark:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ubuntuzilla

This isn't fair. I can't even know if 'zilla installed or is now lost. What's worse I don't know what is harming the FF browser.

---

### Post by nanotube on 2008-03-06
hm, weird... 
what's your output of
```
dpkg -L ubuntuzilla
```
and
```
apt-cache show ubuntuzilla
```

the "script is running" bit is likely due to some javascript that's running in firefox, rather than to anything running on your system.

what extensions do you have installed? does the same thing keep happening if you try starting with a new fresh profile (run "firefox -P" and create a new clean profile - you can always go back again to your old one, so don't worry).

---

### Post by Mark_in_Hollywood on 2008-03-06
> **nanotube said:**
> hm, weird... 
what's your output of
```
dpkg -L ubuntuzilla
```
and
```
apt-cache show ubuntuzilla
```

the "script is running" bit is likely due to some javascript that's running in firefox, rather than to anything running on your system.

what extensions do you have installed? does the same thing keep happening if you try starting with a new fresh profile (run "firefox -P" and create a new clean profile - you can always go back again to your old one, so don't worry).

mark@Lexington-19:~$ dpkg -L ubuntuzilla
Package `ubuntuzilla' is not installed.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
mark@Lexington-19:~$ apt-cache show ubuntuzilla
W: Unable to locate package ubuntuzilla
E: No packages found
mark@Lexington-19:~$ 

Extension:
Ad Block Plus
Google Desktop for Firefox
Google Toolbar for Firefox
PDF Download
Tor button
Ubufox
User Agent Switcher

I'm lost about the Firefox -p

is that from a terminal? I usually mouse click the FF icon in my panel

---

### Post by nanotube on 2008-03-07
ah so it appears you did uninstall ubuntuzilla

by the way... you say you installed the ubuntuzilla package - but did you use ubuntuzilla to actually install the official mozilla build of firefox (by running from terminal
```
ubuntuzilla -a install -p firefox
```
?

just to double check here, since you didn't specifically mention doing this.

about firefox -p - yea, start it from a terminal
you could also just "move" your old profile out of the way (it's in .mozilla folder in your home dir) and a new one will automatically start. 

see if that makes it behave, and then at least you would have narrowed it down to a profile problem.

---

