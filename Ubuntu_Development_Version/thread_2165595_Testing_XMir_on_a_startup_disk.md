---
title: "Testing XMir on a startup disk"
date: 2013-08-05
forum: Ubuntu Development Version
---

### Post by WebDrake on 2013-08-05
Is it possible to test XMir on a startup disk, and if so how?

I've generated a startup disk from the latest daily iso's but so far as I can tell it's running regular X.  I'm guessing this is because XMir has not yet landed as default in 13.10 ... ?  So, I guess it will be necessary to install XMir via the PPA.  The question is whether this is a sane/wise thing to do.

I suppose as an alternative I could try the Xubuntu-on-XMir iso, but I'm a Unity user by habit ... :-)

Bottom line is, I don't have a spare machine to try things out on and I'd really like to give XMir-based Ubuntu a proper spin well in advance of the 13.10 release, so any advice on how to do this is welcome.  I have heard that VirtualBox doesn't really play nice in this respect, otherwise I'd try that as a solution.

Lastly, is there a known ETA for XMir being enabled by default in the daily iso's?  From chatter on the Xubuntu mailing list it looks like it should be arriving in the 13.10 archives in the next days.

Thanks an advance for any advice or information! :-)

---

### Post by grahammechanical on 2013-08-05
I have been running saucy salamander on xmir with Ubuntu, Kubuntu, Xubuntu, Ubuntu Studio & Lubuntu since the first week of July. I followed the instructions here.

[http://www.olli-ries.com/running-mir/](http://www.olli-ries.com/running-mir/)

I have not found anything to worry about. The bug where we saw two cursors has been fixed since a couple of days ago. There are still a couple of issues but otherwise you would not notice any difference. I am posting this from Ubuntu+xmir. All applications work as they should. We do not get ETAs in the development branch. Only the release date. If we have enabled the proposed repository then we may get some code a few days earlier than without the proposed repository being enabled. If nothing breaks then the code comes in through the normal channels or is removed.

I only have one machine. I have several partitions that I use for testing. I also have Precise and Raring that I can use if things break drastically.

Regards.

---

### Post by terry_gardener on 2013-08-05
i would like to test xmir/mir but when i installed using the olli-ries guide and rebooted. it didn't boot, all i got was a black screen with cursor thats it, and nothing worked.

---

### Post by WebDrake on 2013-08-05
@graham: Thanks for the info and reassurances, but nevertheless the goal here is to test Ubuntu + XMir *before* installing it :-)  Regarding ETAs, I'm not asking for a firm deadline -- I understand how the development release operates, as for the past 2-3 releases I've tended to install after Alpha 1 or 2 stage.  I'm just curious if there is a rough estimate of when XMir will become the default option, as that's the point that I'd really like to start testing things.

---

### Post by ajgreeny on 2013-08-05
To try Xubuntu 13.10 with xmir and mir see:-
[http://www.webupd8.org/2013/08/xubuntu-1310-xmir-iso-available-for.html](http://www.webupd8.org/2013/08/xubuntu-1310-xmir-iso-available-for.html)
[http://vanir.unit193.tk/mir/](http://vanir.unit193.tk/mir/)

---

### Post by WebDrake on 2013-08-20
Just thought I'd update here -- once Mir landed in the universe repositories, I found it easy to download a daily image and set up a startup disk, boot into that, add universe to the software sources and then follow the installation instructions here: [http://unity.ubuntu.com/mir/installing_prebuilt_on_pc.html](http://unity.ubuntu.com/mir/installing_prebuilt_on_pc.html)

One restart later and Unity was running very nicely on XMir with only the anticipated issues (e.g. multi-monitor setup only supports mirrored displays).  So I'll add my voice to those saying that Canonical has done very nice work here. :-)

I'm running a ThinkPad T420 with Intel graphics, just for reference.

---

