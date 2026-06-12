---
title: "Spore won't play"
date: 2010-01-31
forum: Wine
---

### Post by Jabrouwer on 2010-01-31
I installed Spore through the autorun.exe on the disk, with nothing special.  When it tried to install/update or whatever DirectX, it gave an error, so I cancelled.  Now when I try to run Spore I get the error:

"The game cannot start.
There seems to be a problem with establishing a connection to the internet.  Please shutdown other applications and try again or reboot your computer."

---

### Post by asdfoo on 2010-03-12
> **Jabrouwer said:**
> I installed Spore through the autorun.exe on the disk, with nothing special.  When it tried to install/update or whatever DirectX, it gave an error, so I cancelled.  Now when I try to run Spore I get the error:

"The game cannot start.
There seems to be a problem with establishing a connection to the internet.  Please shutdown other applications and try again or reboot your computer."

Which version of Wine are you using?  I am going to assume 1.0.1.

Install the latest beta 1.1.40 and retry.

---

### Post by Saint Nick on 2010-07-31
I too have a problem with trying to play Spore.  I currently have joined a thread on WineHQ Bugzilla.

[http://bugs.winehq.org/show_bug.cgi?id=23273](http://bugs.winehq.org/show_bug.cgi?id=23273)

Here are my procedures:  

Here is a link to the basic specs of my computer:

[http://support.dell.com/support/edocs/systems/dim4600/en/4600i/sm/specs.htm](http://support.dell.com/support/edocs/systems/dim4600/en/4600i/sm/specs.htm)

But I upgraded to a to a GeForce 7950 GT video card with 512 MB of memory and
256 bit memory inter face (AGP 8x) and upgraded to 2.5 GB of Memory.

Wine version 1.1.42-0ubuntu4

Installation
  mount to /media/dvd
  cd /media/dvd/
  wine ./Autorun.exe

Execution
  Wine Settings: Vista (tried a few others but same flag occurs)
  cd /home/wrodgers/.wine/drive_c/Program Files/Electronic Arts/SPORE/Sporebin
  ,/SporeApp.exe

After that it errors (see attachment)

Any help would be appreciated and if you have questions, I'll try to help as well

---

