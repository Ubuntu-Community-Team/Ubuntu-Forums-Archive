---
title: "How do I find out whether I'm using 32bit or 64bit"
date: 2010-04-06
forum: The Cafe
---

### Post by kyreks4 on 2010-04-06
Hi, my name is Kevin, and I am having a heck of a time... I recently just switched to Ubuntu 9.10, within the last few months. I love it, but I have NO idea whether or not I am running 64 or 32 bit... please help 

I typed in the command that was listed a little higher in the page, but it told me i had i686 and I'm not sure what that means... :( :confused:

---

### Post by NightwishFan on 2010-04-06
Hi Kevin, welcome to Ubuntu forums. This means you are running 32-bit Ubuntu.

---

### Post by chris200x9 on 2010-04-06
> **kyreks4 said:**
> Hi, my name is Kevin, and I am having a heck of a time... I recently just switched to Ubuntu 9.10, within the last few months. I love it, but I have NO idea whether or not I am running 64 or 32 bit... please help 

I typed in the command that was listed a little higher in the page, but it told me i had i686 and I'm not sure what that means... :( :confused:

lol?

---

### Post by earthpigg on 2010-04-06
just to clarify, you can be running 32 bit ubuntu on a 64 bit processor.

a 64 bit cpu can run 32 bit code, but a 32 bit cpu cannot run 64 bit code.

possible combinations:

i_86 cpu running 32 bit ubuntu
_64 cpu running 32 bit ubuntu
_64 cpu running 64 bit ubuntu

if you have an _64 cpu, and ONLY use open source software, you should be running 64 bit ubuntu.

if you have an _64 cpu, and only run a FEW closed source things (flash, ubuntu-restricted-extras), then the best option is up for debate, but most will agree that 64 bit ubuntu is best.

if you have an i_86 cpu, you must be running 32 bit ubuntu.


to find CPU:

```
sudo lshw | grep "width: 64 bits"
```
if anything comes back, you are running a 64 bit cpu (_64)

to find Ubuntu:

```
uname -a
```
if you see "AMD64" or "x86_64" anywhere, you have a 64 bit operating system installed.

---

### Post by FuturePilot on 2010-04-06
> **NightwishFan said:**
> Hi Kevin, welcome to Ubuntu forums. This means you are running 32-bit Ubuntu.

This thread is 3 years old :-|

---

### Post by NightwishFan on 2010-04-06
I did not see that. I am not the one who bumped it. ;/

---

### Post by cariboo on 2010-04-07
> **FuturePilot said:**
> This thread is 3 years old :-|

It's fixed now :). This is a brand new thread.

---

### Post by kyreks4 on 2010-04-17
thanks so much... sometimes this stuff is a bit hard to understand...

i am going to go 64 bit... well i (kind of) already have i am using Zorin OS 2.0 64 bit, which seems to run a bit smoother... and am upgrading to Lucid via clean install (i did something with the x mouse cursors from gnome-look and it said if you do it... I can't directly upgrade
from 9.10 because of the removal of a certain package/package dependancies

anywho, thanks a bunch... I will get the 64 bit version for Lucid when I get the oppourtunity, and a copy of 32 bit (just in case i need to run it on an older computer)

btw isn't Zorin just a "remixed" version of Ubuntu? do things work the same??? it's a bit confusing....  does it deserve* any* place here??? it still uses the same repos...:confused: 

thanks a bunch I have almost completely gone OSS the only reason I would touch Window$ anymore is because (a) my school only uses Windows, of course

and (b) the games.... but hopefully we will have a big breakthrough with Wine...

so long and thanks for all the Ubuntu! & the kind welcome feeling i get from the AWESOMEREST COMMUNITY IN THE WORLD! :)

---

### Post by cariboo on 2010-04-17
> btw isn't Zorin just a "remixed" version of Ubuntu? do things work the same??? it's a bit confusing.... does it deserve any place here??? it still uses the same repos..

I had to look it up, but yes it is. 

Linux is Linux, under the fancy graphics all distro's work the same. The only real difference is package management. RedHat/OPENSuse and others use rpm to manage packages, where as Debian/Ubuntu uses dpkg and packages with a .deb extension. There are several other distributions that use different schemes to manage package, but it would take more time to list them all than I'm willing to do right now. :)

---

### Post by Genius314 on 2010-04-17
Just a rule of thumb: Generally, unless you actively seek out 64-bit, you're probably running 32-bit*.
The world isn't *quite* ready to switch over yet, there's still some kinks to work out, so 64-bit operating systems and programs are often put out of the way, where they're hard to get to by accident.

*This isn't necessarily true for buying a full PC, though. If you bought a PC and aren't sure what OS is pre-installed: If you have 4 gigs or more of RAM, you've probably got 64-bit. If you've got 3 or less, you've probably got 32-bit.

---

### Post by cariboo on 2010-04-17
It's getting pretty hard to buy a 32-bit processor, the only one I have is an atom n270 in my netbook. Even the atom 320 in my media center pc is 64-bit and hyper-threaded.

---

