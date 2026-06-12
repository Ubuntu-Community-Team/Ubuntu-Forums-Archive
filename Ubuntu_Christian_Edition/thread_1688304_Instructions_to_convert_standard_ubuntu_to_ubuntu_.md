---
title: "Instructions to convert standard ubuntu to ubuntu ce from the website didn't work"
date: 2011-02-15
forum: Ubuntu Christian Edition
---

### Post by tumelo on 2011-02-15
I used the 64-bit command, but my friend tried the 32-bit command and that didn't work for him either. He has ubuntu 9.10 and I have ubuntu 10.10. This is what I get when I try it:

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 ubuntu-ce : Depends: opensong but it is not installable
             Depends: xiphos but it is not going to be installed
             Depends: wine-christian-repos but it is not going to be installed
E: Broken packages

---

### Post by jonathonblake on 2011-02-15
> **tumelo said:**
> 
The following packages have unmet dependencies:


I do not know what the issue with Xiphos is. :(
It _should_ be installable.  However, I ended up adding the CrossWire PPA, so I could get the most recent version.  

The rest of the programs depend upon an older version of Wine. You'll have to manually install it.  

jonathon

---

### Post by david_kt on 2011-02-15
Have you tried to follow below instruction:

[http://ubuntuforums.org/showthread.php?t=1492885](http://ubuntuforums.org/showthread.php?t=1492885)

DK

---

### Post by tumelo on 2011-02-16
> **david_kt said:**
> Have you tried to follow below instruction:

[http://ubuntuforums.org/showthread.php?t=1492885](http://ubuntuforums.org/showthread.php?t=1492885)

DK

Thanks dave. that didn't work for my ubuntu 10.10, but it worked for my Mint 10. Strange.

---

