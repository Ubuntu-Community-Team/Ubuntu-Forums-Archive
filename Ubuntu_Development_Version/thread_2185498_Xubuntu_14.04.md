---
title: "Xubuntu 14.04"
date: 2013-11-02
forum: Ubuntu Development Version
---

### Post by OrangeCrate on 2013-11-02
I'm up and running the 11/2 daily. The install and setup went fine.

```

$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu Trusty Tahr (development branch)
Release:	14.04
Codename:	trusty

```

```

$ uname -a
Linux laptop 3.12.0-1-generic #3-Ubuntu SMP Tue Oct 29 18:41:32 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

```

This cycle should be a breeze. Always busy, but, I'll help when I can...

[http://cdimage.ubuntu.com/xubuntu/daily-live/20131102/](http://cdimage.ubuntu.com/xubuntu/daily-live/20131102/)

Edit:

I see that link died, or is temporarily down. This one seems to be working:

[http://mirrors.fe.up.pt/pub/xubuntu/daily-live/current/](http://mirrors.fe.up.pt/pub/xubuntu/daily-live/current/)

---

### Post by Will_McDade on 2013-11-02
What's it like then? Spill those beans. xD

---

### Post by OrangeCrate on 2013-11-02
^,

Though LTS development releases generally don't suffer from showstopper bugs, there will be plenty of things both odd and strange to keep a person busy until the release date.

If you want to jump into the deep end, go ahead and install in a separate partition, the latest daily from the link I provided above. Keep something that works, for everyday use, in the other partition. The worst that could probably happen to you, is that you'll get confused, or something will bork beyond hope, and you'll have to reinstall a later daily to get up and running again. Frankly, trial and error are how you're going to learn.

If you aren't experienced with dev releases, and are only asking a rhetorical question, or you are unwilling to boot your computer with a rubber mallet occasionally (just kidding), here are some dates of note for this release:

> 
    Alpha 1 - December 19th (for flavours)
    Alpha 2 &#8211; January 23rd (for flavours)
    Beta 1 &#8211; February 27th (for flavours)
    Final Beta &#8211; March 27th
    Release Candidate &#8211; April 10th


[http://www.omgubuntu.co.uk/2013/08/ubuntu-14-04-lts-release-schedule](http://www.omgubuntu.co.uk/2013/08/ubuntu-14-04-lts-release-schedule)

If you don't want to get involved with testing, you'd probably be safe to install sometime after the final beta.

Good luck, and have fun if you decide to join us.

:)

---

### Post by Elfy on 2013-11-04
Looks ok at the moment with Gtk3 indicators working as well :)

[https://wiki.ubuntu.com/Xubuntu/Roadmap/Specifications/Saucy/Gtk3Indicators](https://wiki.ubuntu.com/Xubuntu/Roadmap/Specifications/Saucy/Gtk3Indicators)

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=247551&d=1383554810[/IMG]

---

### Post by OrangeCrate on 2013-11-04
> **Elfy said:**
> Looks ok at the moment with Gtk3 indicators working as well :)

[https://wiki.ubuntu.com/Xubuntu/Roadmap/Specifications/Saucy/Gtk3Indicators](https://wiki.ubuntu.com/Xubuntu/Roadmap/Specifications/Saucy/Gtk3Indicators)

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=247551&d=1383554810[/IMG]

Added the Gtk3 indicators, worked fine, no crashes, all the shown indicators have menus.

I didn't go the route of the commented line, just a straight-up build as indicated.

> # (above you can add --prefix=/usr if you're not afraid of reinstalling your xfce4-panel with "sudo apt-get install xfce4-panel --reinstall")

---

### Post by Elfy on 2013-11-04
Nice - I think in here I've gone for prefix=/usr - the vm has it just for the user I think. 

Should get that in for 14.04.

We had an extra meeting last night if you're interested - [http://ubottu.com/meetingology/logs/xubuntu-devel/2013/xubuntu-devel.2013-11-03-22.39.html](http://ubottu.com/meetingology/logs/xubuntu-devel/2013/xubuntu-devel.2013-11-03-22.39.html)

Last roadmap meeting for this cycle will be on Thursday.

---

### Post by OrangeCrate on 2013-11-04
> **Elfy said:**
> Nice - I think in here I've gone for prefix=/usr - the vm has it just for the user I think. 

Should get that in for 14.04.

We had an extra meeting last night **if you're interested** - [http://ubottu.com/meetingology/logs/xubuntu-devel/2013/xubuntu-devel.2013-11-03-22.39.html](http://ubottu.com/meetingology/logs/xubuntu-devel/2013/xubuntu-devel.2013-11-03-22.39.html)

Last roadmap meeting for this cycle will be on Thursday.

I'm interested, and have bookmarked the link. I'll check for the minutes after your meeting on Thursday.

Thanks.

---

### Post by OrangeCrate on 2013-11-04
Just playing around...

I replaced the "Action Buttons" in the upper right hand corner, with a launcher loaded with the "Log Out" option, and a custom icon from the "Status Icons" collection.

Honestly, at least to me, the Gtk3 setup looks pretty clean just as it is, without any further customization, though I assume you will be able to, once it goes final.

---

### Post by Elfy on 2013-11-05
> **OrangeCrate said:**
> ...
Honestly, at least to me, the Gtk3 setup looks pretty clean just as it is, without any further customization, though I assume you will be able to, once it goes final.

I'd assume the same.

The best place to find out is in #xubuntu-devel

Though I will *endeavour* to keep people abreast of changes for the LTS.

---

### Post by OrangeCrate on 2013-11-05
> **Elfy said:**
> I'd assume the same.

**The best place to find out is in #xubuntu-devel**

Though I will *endeavour* to keep people abreast of changes for the LTS.

Just subscribed to the list, thanks for the tip.

---

### Post by Elfy on 2013-11-05
> **OrangeCrate said:**
> Just subscribed to the list, thanks for the tip.

Mailing list? or IRC channel? 

(though perhaps I should have said mailing list in the first place)

Bit confused :p

---

### Post by OrangeCrate on 2013-11-05
> **Elfy said:**
> Mailing list? or IRC channel? 

(though perhaps I should have said mailing list in the first place)

Bit confused :p

Mailing list.

Edit:

[https://lists.ubuntu.com/mailman/listinfo/xubuntu-devel](https://lists.ubuntu.com/mailman/listinfo/xubuntu-devel)

---

### Post by Elfy on 2013-11-05
Just checking :)

---

