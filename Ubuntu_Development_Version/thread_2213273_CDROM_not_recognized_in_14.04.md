---
title: "CDROM not recognized in 14.04"
date: 2014-03-25
forum: Ubuntu Development Version
---

### Post by A.O._Stanley on 2014-03-25
I am using 14.04 but I wonder if that makes a difference. If so, please move this over there.

This is an older HP lapttop that until a few days ago was running XP. I put a DVD in the drive, and it played. I tried an audio CD which it seemed to recognize but wouldn't play, but this may be due to other issues.

When I run ```

```sudo apt-get update```

``` I get the following error: 

 "W: Failed to fetch cdrom://Ubuntu 12.04.03 LTS -Precise Pangolin- -Release i386 (20130820.1)/dists/precise/restricted/binary-i386/Packages Please use apt-cdrom to make this DC-ROM recogonized by APT. apt-get update cannot be used to add new CD-ROMs."

If I run ```

```apt-cdrom```

```, nothing changes

If I do a search for additional drivers, I get this message: "A  proprietary driver has private code that Ubuntu developers can't review  or improve."

So I can't update until this is fixed, if it can be fixed.

Thanks

---

### Post by hamishmb on 2014-03-25
Okay, you've got a cdrom included in your sources.list which can sometimes happen. What you need to do to fix this is click on the Unity dash (or other menu system) and open "Software Sources" sometimes also called "Software & Updates". Then what you need to do is go to the "Other Software" tab, and uncheck the option listing a cdrom. Then click apply, and update again and that should fix it. By the way, 14.04 is not a stable version yet, so it may be better to use 13.10 or 12.04 Long Term Support instead.

Hamish

---

### Post by A.O._Stanley on 2014-03-25
Yep, that appears to have been it.

Thanks, Hamish, much appreciated.

---

### Post by deadflowr on 2014-03-25
Sidenote: The ability for Ubuntu to play audio cd's depends on whether or not you have the codec to do so.
```
sudo apt-get install ubuntu-resticted-extras
```
will pull in a good majority of codecs you might need.
Right now 14.04 is still in development, so packages like the one above, might still be getting tweaked...

---

### Post by sandyd on 2014-03-25
Moved to Ubuntu+1

---

### Post by empholmi on 2014-12-27
When I uncheck the CDROM "Installable from CDROM/DVD"
                                         " CDROM with Ubuntu 14.04 Trusty Tahr"
                                          "Offically supported"
                                          "Restriced copyright"
Does that mean I will stop getting OS updates or does that mean that it will stop looking for a CDROM that is inserted locally? I need the OS updates. I am waiting for full inate SSD support. I already edited my OS for that, but still need the offical updates. 
And is that CDROM a CDROM on an update server?

---

### Post by Elfy on 2014-12-27
It will stop looking for a cdrom.

As 14.04 is now long released - I'll close this development thread.

---

