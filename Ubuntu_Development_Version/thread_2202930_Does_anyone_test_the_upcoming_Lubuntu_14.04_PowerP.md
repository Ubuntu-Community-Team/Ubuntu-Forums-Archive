---
title: "Does anyone test the upcoming Lubuntu 14.04 PowerPC?"
date: 2014-01-31
forum: Ubuntu Development Version
---

### Post by xeno74 on 2014-01-31
Hi All,

Does anyone test the upcoming Lubuntu 14.04 on a Power Mac? I test Lubuntu 14.04 on my NG Amigas. I've found three issues.

1. ibus-ui-gtk3 crashed with SIGABRT in g_assertion_message() -> [https://bugs.launchpad.net/ubuntu/+source/ibus/+bug/1274897](https://bugs.launchpad.net/ubuntu/+source/ibus/+bug/1274897)
2. midori crashed with SIGSEGV in JSC::LLInt::CLoop::execute() -> [https://bugs.launchpad.net/ubuntu/+source/midori/+bug/1274167](https://bugs.launchpad.net/ubuntu/+source/midori/+bug/1274167)
3. Wrong colors with Mesa 9.2 and Mesa 10.0 on Lubuntu 14.04 PowerPC -> [https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/1275042](https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/1275042)

Find screenshots attached.


Rgds,

Christian

---

### Post by Elfy on 2014-01-31
not often we do this

Copied to U+1

I'll merge them in a month or so

---

### Post by xeno74 on 2014-02-01
> **Elfy said:**
> not often we do this

Copied to U+1

I'll merge them in a month or so

Thanks a lot for your effort! :smile: I'm so glad that a PowerPC port is available for 14.04.

@All

Let's test =d>

We need for a good release a lot of diligent tester. :) That's very important for Lubuntu on the PowerPC platform.

Here are some important (L)Ubuntu PowerPC links:

Lubuntu 14.04 (Trusty Tahr) Daily Build (desktop images): [http://cdimage.ubuntu.com/lubuntu/daily-live/current/](http://cdimage.ubuntu.com/lubuntu/daily-live/current/)
Lubuntu 14.04 (Trusty Tahr) Daily Build (alternate install images): [http://cdimage.ubuntu.com/lubuntu/daily/current/](http://cdimage.ubuntu.com/lubuntu/daily/current/)
Lubuntu install guide for Power Macs: [http://powerpcliberation.blogspot.de/2012/10/lubuntu-install-guide.html](http://powerpcliberation.blogspot.de/2012/10/lubuntu-install-guide.html) 
Lubuntu PPC & Mac testing: [https://wiki.ubuntu.com/Lubuntu/Testing/PPC%26Mac64](https://wiki.ubuntu.com/Lubuntu/Testing/PPC%26Mac64)
Lubuntu/Documentation/FAQ/PPC: [https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/PPC](https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/PPC)
Ubuntu Power Mac FAQ: [https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)
Ubuntu Power Mac known issues: [https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)
(K)(L)Ubuntu( server) downloads for Power Macs and NG Amigas: [https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads) 
Lubuntu install guide for the AmigaOne X1000: [http://amigaworld.net/modules/newbb/viewtopic.php?topic_id=38004&forum=34](http://amigaworld.net/modules/newbb/viewtopic.php?topic_id=38004&forum=34)
Ubuntu install guide for the Sam460ex (Lite): [http://jabirulo.site90.com/sam460ex/](http://jabirulo.site90.com/sam460ex/)
Linux kernel for all Sams: [http://www.supertuxkart-amiga.de/amiga/sam.html#downloads](http://www.supertuxkart-amiga.de/amiga/sam.html#downloads)
Linux kernel for the AmigaOne X1000: [http://www.supertuxkart-amiga.de/amiga/x1000.html](http://www.supertuxkart-amiga.de/amiga/x1000.html)
Ubuntu support forum for all Sams: [http://forum.hyperion-entertainment.biz/viewforum.php?f=52](http://forum.hyperion-entertainment.biz/viewforum.php?f=52)
Ubuntu support forum for the AmigaOne X1000: [http://forum.hyperion-entertainment.biz/viewforum.php?f=35](http://forum.hyperion-entertainment.biz/viewforum.php?f=35)
Lubuntu 13.04 Raring Ringtail Power Mac Preview: [http://ppcluddite.blogspot.de/2013/02/lubuntu-1304-raring-ringtail-preview.html](http://ppcluddite.blogspot.de/2013/02/lubuntu-1304-raring-ringtail-preview.html)

All the best,

Christian

---

