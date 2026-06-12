---
title: "Quake 4"
date: 2010-03-25
forum: Wine
---

### Post by bigseb on 2010-03-25
I see on the Wine AppDB that there is a native version available. What does that mean exactly? I was browsing through the discount box shelf at a game store yesterday and there was a copy of Quake 4. Will that install in Ubuntu then and run with a patch (similar to what I had to do with Doom 3)? If so then I'll get it ASAP.

---

### Post by Ferrat on 2010-03-25
> **bigseb said:**
> I see on the Wine AppDB that there is a native version available. What does that mean exactly? I was browsing through the discount box shelf at a game store yesterday and there was a copy of Quake 4. Will that install in Ubuntu then and run with a patch (similar to what I had to do with Doom 3)? If so then I'll get it ASAP.

Yes it's just like with Doom3, you buy the game and then use a linux installer from Id softwares site to run it on Linux.

---

### Post by Brebs on 2010-03-25
I wrote an [installation script for the DVD version](http://forums.fedoraforum.org/showthread.php?t=189064).

Quake4 is native to Linux. Running the Windows version through Wine will not bring any benefit, and will only bring additional hassle.

---

### Post by bigseb on 2010-03-26
> **Ferrat said:**
> Yes it's just like with Doom3, you buy the game and then use a linux installer from Id softwares site to run it on Linux.
  Thanx Ferrat. I will buy it this afternoon!

---

### Post by bigseb on 2010-03-26
> **Brebs said:**
> I wrote an [installation script for the DVD version]("http://forums.fedoraforum.org/showthread.php?t=189064").
 
Quake4 is native to Linux. Running the Windows version through Wine will not bring any benefit, and will only bring additional hassle.
  Thanks brebs

---

### Post by bigseb on 2010-03-27
> **Brebs said:**
> I wrote an [installation script for the DVD version]("http://forums.fedoraforum.org/showthread.php?t=189064").

Quake4 is native to Linux. Running the Windows version through Wine will not bring any benefit, and will only bring additional hassle.


Brebs, I checked out that link. I copied the code in the window and saved as a .txt file in my Documents. When I run 'sudo bash installquake4'  in the terminal it tells me it can't find the file (or something along those lines). 

Please help me out. I'm really stuck here. Thanks.

---

### Post by Toffeeapple on 2010-03-27
Save it as a text file named installquake4, you don't need to be putting the .txt extension, It also needs to be executable..

You also need to put the path to it.. so for example if it's in your documents it would be something like this..

```
/home/YOUR USER NAME/Documents/installquake4
```

Or where ever it is..

```
chmod +x installquake4
```
Will make it executable..

---

### Post by bigseb on 2010-03-27
That script of brebs automatically starts the download of the linux installer. Way cool!

BUT...

its an immense file approx 270 Mb. If I look on the idsoftware ftp server I see there is a previous version of only 78Mb. Will that on not work?

---

### Post by Toffeeapple on 2010-03-27
Yep, the 270 Mb file is the one you need... at least it was for me anyway.

---

### Post by bigseb on 2011-12-01
UPDATE:

I tried this installer in Mint 12 the other day and it wouldn't work. Why is this? I was under the impression that underneath the interface these OS's were all the same?

---

### Post by Brebs on 2011-12-01
Come on - show an error message. Something useful for debugging.

---

### Post by bigseb on 2011-12-01
Will do once I get home. Thanks.

---

