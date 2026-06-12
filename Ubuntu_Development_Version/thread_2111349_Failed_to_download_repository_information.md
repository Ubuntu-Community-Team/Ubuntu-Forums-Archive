---
title: "Failed to download repository information"
date: 2013-02-01
forum: Ubuntu Development Version
---

### Post by Chelidze on 2013-02-01
So I did an upgrade to ubuntu 13.04 from 12.10 and now I am getting an error like this.



This is not my first time I got an error like this every time I do upgrades I get this problem and I do a clean reinstall after every upgrade 

 Can some one help me with this problem, I am quite new to this 

Thank you in advanced

---

### Post by cariboo on 2013-02-01
The upgrade process disables ppa's on purpose, it's up to you to re-enable them after the upgrade is finished.

The reasoning behind this is so that no unsupported packages are pulled in while the upgrade is in process, once it's finished, you can add what you want.

Another thing you will have to do is make sure that all the ppa's you have listed actually have Raring versions, as there are some that don't update to the next version until after it is released.

---

### Post by Chelidze on 2013-02-02
> **cariboo907 said:**
> The upgrade process disables ppa's on purpose, it's up to you to re-enable them after the upgrade is finished.

The reasoning behind this is so that no unsupported packages are pulled in while the upgrade is in process, once it's finished, you can add what you want.

Another thing you will have to do is make sure that all the ppa's you have listed actually have Raring versions, as there are some that don't update to the next version until after it is released.

So for example "Grub Customizer" is giving me an error because it does not supports 13.04 for now and after/if they will push out a 13.04 release update will not return with an error ??

---

### Post by grahammechanical on 2013-02-02
> and after/if they will push out a 13.04 release update will not return with an error ??

Not necessarily. PPA = Personal Package Archive. It is the responsibility of the application's maintainer to make sure that a Raring Ringtail repository is available for that package. I have no doubt that Daniel Ritchter will do this.

Regards.

---

### Post by Chelidze on 2013-02-02
> **grahammechanical said:**
> Not necessarily. PPA = Personal Package Archive. It is the responsibility of the application's maintainer to make sure that a Raring Ringtail repository is available for that package. I have no doubt that Daniel Ritchter will do this.

Regards.

Thank you for the information one more question if you do not mind every time I've did an upgrade software source shows every ppa twice is there a way to automatically fix this I've deleted duplicates manually ?? any easy way to remove duplicates from software source ??

---

### Post by cariboo on 2013-02-02
So are you getting 4 entries for each ppa? Usually you just get a line for the binary, and a line for the source, this is done automagically when you use apt-add-repositories, or add them via software sources.

**Additional information**: For each ppa you add you should have the following two lines:

```
deb http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu quantal main
# deb-src http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu raring main
```

note the second line I have commented out, where it says deb-src, this allows you to download the source package, and complie it yourself if you want.

---

### Post by Chelidze on 2013-02-03
> **cariboo907 said:**
> So are you getting 4 entries for each ppa? Usually you just get a line for the binary, and a line for the source, this is done automagically when you use apt-add-repositories, or add them via software sources.

**Additional information**: For each ppa you add you should have the following two lines:

```
deb http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu quantal main
# deb-src http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu raring main
```

note the second line I have commented out, where it says deb-src, this allows you to download the source package, and complie it yourself if you want.

 every time i did an upgrade on ubuntu I am getting duplicates for every entree  for example 
```
deb http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu quantal main
# deb-src http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu raring main 
deb http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu quantal main
# deb-src http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu raring main
``` 
it would look like this

---

### Post by ibjsb4 on 2013-02-03
> every time i did an upgrade on ubuntu I am getting duplicates for every entreeThats the way /sources.list.d stores it.  If thats what your looking at, nothing wrong there.

```
cat /etc/apt/sources.list.d/*
```

---

### Post by Chelidze on 2013-02-03
> **ibjsb4 said:**
> Thats the way /sources.list.d stores it.  If thats what your looking at, nothing wrong there.

```
cat /etc/apt/sources.list.d/*
```

So when I manually deleted duplicate from software source no harm was done :) 
```
cat /etc/apt/sources.list.d/*
```
what does this commend do ??

---

### Post by ibjsb4 on 2013-02-03
> **Chelidze said:**
> So when I manually deleted duplicate from software source no harm was done :) 
```
cat /etc/apt/sources.list.d/*
```what does this commend do ??

That will just give you a print out of everything in sources.list.d

---

### Post by Chelidze on 2013-02-03
> **ibjsb4 said:**
> That will just give you a print out of everything in sources.list.d

I have a question I attached ppa list txt document can you tell me if this list is ok or it has some issues

---

### Post by ibjsb4 on 2013-02-03
> **Chelidze said:**
> I have a question I attached ppa list txt document can you tell me if this list is ok or it has some issues

Well, thats a mess.

You will find that your raring ppa's don't work because they do not yet exist and probably will not exist until 13o4 final release comes out.  If it was me, I just remove the entire thing and not concern myself with ppa's until the 13o4 final release comes out.

Rename the /sources.list.d folder to something like /sources.list.d.old and create a new /sources.list.d folder (empty).

An easy GUI way to do this is open a terminal and enter:
```

gksudo nautilus
```And navigate to the folder and make the changes.

---

### Post by Chelidze on 2013-02-03
> **ibjsb4 said:**
> Well, thats a mess.

You will find that your raring ppa's don't work because they do not yet exist and probably will not exist until 13o4 final release comes out.  If it was me, I just remove the entire thing and not concern myself with ppa's until the 13o4 final release comes out.

Rename the /sources.list.d folder to something like /sources.list.d.old and create a new /sources.list.d folder (empty).

An easy GUI way to do this is open a terminal and enter:
```

gksudo nautilus
```And navigate to the folder and make the changes.


 Thank you (ibjsb4, cariboo907) for the replies I believe you've gave me the information i've needed so thank you

---

