---
title: "Aliases in wine"
date: 2009-06-17
forum: Wine
---

### Post by wbest on 2009-06-17
For various reasons, I have to call perl in wine like so:
 
C:\public\perl\bin\perl
 
but...I'd rather just call it like so:
 
perl
 
How can I make an alias that runs in wine to do this, like:
 
"perl" = "C:\public\perl\bin\perl
 
Would this be considered an alias?  Or is it really more of an envrinment variable?
I thought environment variables are really made to just be used by programs, so I'm a little unclear on how they work.  So, any advice would be greatly appreciated.

---

### Post by wbest on 2009-06-17
Don't everybody all rush and answer at once!
 
No but seriously, I figured it out myself.
 
I had to set it up as an environment variable like so:
[http://www.winehq.org/docs/wineusr-guide/environment-variables](http://www.winehq.org/docs/wineusr-guide/environment-variables)
 
But I had to create the Environment key in HKEY_CURRENT_USER.
 
Then to call it, like an environment variable in Windows, I had to do %perl%
 
So its all cool now.

---

### Post by NightMKoder on 2009-06-17
You just have to add perl to the path. Same place you were looking, just add C:\public\perl\bin\ after the other entries. [http://wiki.winehq.org/UsefulRegistryKeys](http://wiki.winehq.org/UsefulRegistryKeys) , which says to do it in HKLM.

---

