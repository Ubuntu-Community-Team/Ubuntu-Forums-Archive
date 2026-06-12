---
title: "Sun Grid Engine Qmon Crash error?"
date: 2010-03-28
forum: Server Platforms
---

### Post by jxzz on 2010-03-28
Are there any people successfully running SGE in latest Ubuntu desktop 9.10 package? 

I got several old PCs and want to install SGE to do bioinformatics scientific research.   All my Ubuntu machines are updated to latest patches of security/recommended patches of 9.10 version. 

I installed SGE from Synaptic and everything with default configuration. However, qmon can not be loaded. The error message  was reported earlier in the forum but was never got fixed. Here is error after running "sudo qmon" with crash: 

Warning: Cannot convert string "-adobe-helvetica-medium-r-*--14-*-*-*-p-*-*-*" to type FontStruct
Warning: Cannot convert string "-adobe-helvetica-bold-r-*--14-*-*-*-p-*-*-*" to type FontStruct
Warning: Cannot convert string "-adobe-helvetica-medium-r-*--20-*-*-*-p-*-*-*" to type FontStruct
Warning: Cannot convert string "-adobe-helvetica-medium-r-*--12-*-*-*-p-*-*-*" to type FontStruct
Warning: Cannot convert string "-adobe-helvetica-medium-r-*--24-*-*-*-p-*-*-*" to type FontStruct
Warning: Cannot convert string "-adobe-courier-medium-r-*--14-*-*-*-m-*-*-*" to type FontStruct
Warning: Cannot convert string "-adobe-courier-bold-r-*--14-*-*-*-m-*-*-*" to type FontStruct
Warning: Cannot convert string "-adobe-courier-medium-r-*--12-*-*-*-m-*-*-*" to type FontStruct
Warning: Cannot convert string "-adobe-helvetica-medium-r-*--10-*-*-*-p-*-*-*" to type FontStruct
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  45 (X_OpenFont)
  Serial number of failed request:  665
  Current serial number in output stream:  676

I re-installed xfonts-base, xfonts-75dpi, xfonts-100dpi  with no luck.  It appears that Ubuntu does not have above fonts. 

Without qmon, I could not configure SGE to work.  I searched over Google, and the Ubuntu forum with no solution either.

---

### Post by solar sailer on 2011-07-06
jxzz, 
 
Were you able to resolve this issue? I receive an identical error while starting qmon on Natty Server. It appears xfonts-75dpi includes the correct fonts, but X cannot resolve them. The fonts are present in /usr/share/fonts/X11/75dpi.
 
I created an xorg.conf in /etc/X11 as follows:
 
```
 
Section "Files"
 
FontPath "/usr/share/fonts/X11/75dpi"
 
EndSection

``` 
 
This was unsuccessful. Any ideas?
 
Thanks!

---

### Post by solar sailer on 2011-07-06
In the majority of qmon documentation I've seen, qmon is run remotely by forwarding X across ssh.
 
**I was able to start qmon over ssh without errors **
using puTTY and Xming with Xming-fonts installed.  
 
Windows installers are here:
 
[http://www.straightrunning.com/XmingNotes/](http://www.straightrunning.com/XmingNotes/)
 
No luck running qmon locally, but I wouldn't expect GUI to work out-of-the-box on a server distro anyway.

---

### Post by linuxuser42 on 2011-09-07
I guess you miss the packages xfonts-100dpi and xfonts-75dpi, like I did.

---

### Post by toontu on 2011-09-30
Check Section 8.4.1 in this blog: [http://webappl.blogspot.com/2011/05/install-sun-grid-engine-sge-on-ubuntu.html](http://webappl.blogspot.com/2011/05/install-sun-grid-engine-sge-on-ubuntu.html)

It should do you the job nicely. Good luck.

---

