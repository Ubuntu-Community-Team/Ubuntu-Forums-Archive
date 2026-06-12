---
title: "Wine doesn't detect my cdrom drive"
date: 2011-05-30
forum: Wine
---

### Post by dahhn on 2011-05-30
I have the same problem with IGI 2 Covert Strike. Its driving me nuts and when I checked wine/dosdevices it shows that drive e:, e::, f:, f:: are broken because specified path does not exist.

---

### Post by bobwyajnr on 2011-05-30
> **dahhn said:**
> I have the same problem with IGI 2 Covert Strike. Its driving me nuts and when I checked wine/dosdevices it shows that drive e:, e::, f:, f:: are broken because specified path does not exist.

Hi

I would seriously take a chill pill first - before preceeding! In my experience Wine problems could quite easily cause a stroke (probably about in the 57th hour of trouble-shooting).:popcorn:

The *permanent* dosdevices point directly at the DVD-drive block device (e.g. link **d::** points directly at /dev/sr0 on my laptop).

As media is inserted in the physical device it should automagically be dynamically mounted in a *temporary* dosdevice (e.g. link **d:** points directly at the dynamically created folder /media/_DISC LABEL_ on my system).

Try inserting in the game disc. If you don't have auto-mounting enabled (in Gnome) then mount the game disc. Then perhaps you could run:
```
sudo mount
```
that will show you all the mounted filesystems on your system. You should see something like (near the bottom as it a recent mount point):
**/dev/sr0 on /media/CD_ROM type iso9660 ...**

The **winecfg** (command line or Gnome menu) shows you what drives are present, their type and what folder they map to.

Running **wine explorer**  (command line or Gnome menu) is useful for checking the contents of your drives.

It also worth reading the [Wine FAQ]("http://wiki.winehq.org/FAQ") and [User Guide]("http://www.winehq.org/documentation"). These cover how to access your optical media in Wine - going into some detail.

Bob

---

### Post by 3602 on 2011-05-30
In Drives, make a new drive letter and point it to /cdrom. In Advanced Options choose CD-ROM instead of Autodetect.
Also in your Windows program you may need to play with the communications method, if possible...

---

### Post by dahhn on 2011-05-31
Ok I'll try it and see if it helps.

---

### Post by dahhn on 2011-05-31
> **dahhn said:**
> Ok I'll try it and see if it helps.

It worked. Thanks a lot.

---

### Post by ranger12 on 2011-06-20
Hmm, I am running 11.04 and running Wine and am having the same trouble. I tried the method of pointing it to /cdrom and that didn't work. The disk that shows up in nautilus states the path as /media/'whatever'. I tried pointing it to to /media from within winecfg and that didn't work either. I am running the latest wine dev version - 1.3.22. Maybe it is broken in this version. I wonder if I should uninstall it and try the stable version.

---

### Post by ranger12 on 2011-06-20
I can go into winecfg and mount the specific cd that is currently in the drive under the /media folder and that works - I just can't set it up to dynamically mount any cd disc I put in the drive and any given time.

---

### Post by ranger12 on 2011-06-20
Ok the symlink in the ~/.wine/dosdevices/d: directory does point to /media. When I put a cd in the drive and click on the symlink it does show the contents of the cd. I don't know what is going on when I run the game - it just says it cannot find the cd - it doesn't matter what cd I put in either.

---

### Post by bobwyajnr on 2011-06-20
@**ranger12**

There appears to be a regression in Wine 1.3.22. Even with a link D:: pointing at the DVD-rewriter device - mounted DVD/CDs aren't picked up. Also **winecfg** is not creating the D:: link anymore (for fresh Wineprefix's).

Hmmm me feels a regression test coming on! Bet someone's already filed a bug against this one... :popcorn:

Bob

---

### Post by ranger12 on 2011-06-21
Yeah, I was starting to think the same thing. Winecfg seemed like it created the symlink ok but it still does not work which is weird. I can do a direct map to a specific cd with winecfg and that works but it doesn't work with doing a dynamic map to the drive. I think I might uninstall the dev build and install the stable version and see what happens.

---

### Post by ranger12 on 2011-06-21
Well I am stumped. I regressed back to the stable version of 1.2.3 and it is exhibiting the same behaviour.

---

### Post by ranger12 on 2011-06-22
Well this is interesting. I downloaded and installed PlayonLinux and used it to install Star Wars Jedi Knight: Jedi Outcast and it works just fine after that. I guess I will use PlayonLinux to install software - that is as long as it is on PlayonLinux's list. If I do it using winecfg it does not work. I wonder PlayonLinux does differently that makes it work?

---

### Post by bobwyajnr on 2011-06-22
> **ranger12 said:**
> Well this is interesting. I downloaded and installed PlayonLinux and used it to install Star Wars Jedi Knight: Jedi Outcast and it works just fine after that. I guess I will use PlayonLinux to install software - that is as long as it is on PlayonLinux's list. If I do it using winecfg it does not work. I wonder PlayonLinux does differently that makes it work?

Like I said there is a regression in newer (??) Wine versions (I'll look out for it in my current regression tests on Deus Ex 1). POL uses various different versions of Wine+patches (each Windows application/game is then stored in a seperate Wineprefix). If you check, I am sure you will find the reason POL is working is just because it uses an older version of Wine for installing and running the Star Wars game. No magic, smoke or mirrors :)

Bob

---

