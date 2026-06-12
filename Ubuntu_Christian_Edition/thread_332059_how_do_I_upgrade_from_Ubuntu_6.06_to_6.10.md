---
title: "how do I upgrade from Ubuntu 6.06 to 6.10 ?"
date: 2007-01-05
forum: Ubuntu Christian Edition
---

### Post by Scott A on 2007-01-05
how do I upgrade from Ubuntu 6.06 to 6.10 ?  Are there step by step instructions? I am new to ubuntu. 

I want to be able to have automatix, wine and run windows programs on Ubuntu CE

Thanks, 
Scott A    jasa711 at yahoo dot com

---

### Post by stalker145 on 2007-01-05
> **Scott A said:**
> how do I upgrade from Ubuntu 6.06 to 6.10 ?  Are there step by step instructions? I am new to ubuntu. 

1. Check out [this thread]("http://ubuntuforums.org/showthread.php?t=286599"). It gives detailed instructions:D 

> **Scott A said:**
> I want to be able to have automatix, wine and run windows programs on Ubuntu CE

2. [This web site]("http://www.getautomatix.com/") should be able to help you on this one. Make sure you get Automatix2 since it's newer, cooler, and is meant for Edgy (6.10)

3. Have fun

---

### Post by doobit on 2007-01-05
The best way is to create your /home on it's own partition. Then you can reinstall the whole OS without losing your settings. The upgrade procedure doesn't always work very well.

---

### Post by Scott A on 2007-01-05
I went to the link, but they seem to have some kind of code to type in. 
"$ gksu "update-manager -c""  
 Where do you type in the code?

I am REALLY new to ubuntu, and know very little. 

Also, for creating my "/home " on its own partition, I just don't have a clue what that is. What does that mean?

Sorry that I don't know the basics.

---

### Post by doobit on 2007-01-05
Why do you want to upgrade? 6.06 has 3 years of support and works pretty good. and you can use Automatix and install Wine with 6.06

---

### Post by mysticrider92 on 2007-01-05
> **Scott A said:**
> I went to the link, but they seem to have some kind of code to type in. 
"$ gksu "update-manager -c""  
 Where do you type in the code?

I am REALLY new to ubuntu, and know very little. 

Also, for creating my "/home " on its own partition, I just don't have a clue what that is. What does that mean?

Sorry that I don't know the basics.

For the code, open a terminal and type it there (without the quotes or the $ sign). Creating a new partition usually requires a cd (burning the [gparted live cd]("http://gparted.sourceforge.net/livecd.php") to a CD-RW is a good choice). Repartitioning a hard drive can be dangerous, so I wouldn't recommend trying it before making a backup.

---

