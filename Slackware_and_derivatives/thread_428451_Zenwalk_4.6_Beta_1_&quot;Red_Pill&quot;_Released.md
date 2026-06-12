---
title: "Zenwalk 4.6 Beta 1 &quot;Red Pill&quot; Released"
date: 2007-04-30
forum: Slackware and derivatives
---

### Post by ThinkBuntu on 2007-04-30
Message from Jean-Philippe Guillemin, lead developer of Zenwalk.
> Hi,

The BETA1 version of Zenwalk 4.6 "Red pill" introduces public beta releases of Zenwalk GNU Linux. Main changes in this release are :
- Kernel 2.6.21, with kvm support
- a new toolchain, featuring a new glibc and gcc so that most packages have been rebuilt,
- XFCE 4.4.1 with new plugins, and system notifications (for example, udev now send user notifications about hotplugged devices),
- Firefox 2.0.0.3, Thunderbird 2.0.0.0,
- Many improvements in the base system and admin tools.

You will notice that Zenwalk installer has been simplified a lot, making it one of the simplest setup available in the GNU Linux world.
You will also enjoy faster boot times, resulting from the highly parallelized and optimized init system.

The full changelog is available here : [http://www.zenwalk.org/modules/news/article.php?storyid=45](http://www.zenwalk.org/modules/news/article.php?storyid=45)

Please report any bug or missing feature, so that we can stabilize this release. Note that the kernel will be updated before the final 4.6, in order to get Linus bugfixes.

Have fun

JP

Download points :
USA : [http://distro.ibiblio.org/pub/linux/distributions/zenwalk/people/jp/SNAPSHOT-29042007/zenwalk-4.6.iso](http://distro.ibiblio.org/pub/linux/distributions/zenwalk/people/jp/SNAPSHOT-29042007/zenwalk-4.6.iso)
USA : [ftp://distro.ibiblio.org/pub/linux/distributions/zenwalk/people/jp/SNAPSHOT-29042007/zenwalk-4.6.iso](ftp://distro.ibiblio.org/pub/linux/distributions/zenwalk/people/jp/SNAPSHOT-29042007/zenwalk-4.6.iso)
FRANCE : [ftp://mirror.meleeweb.net/pub/linux/zenwalk/people/jp/SNAPSHOT-29042007/zenwalk-4.6.iso](ftp://mirror.meleeweb.net/pub/linux/zenwalk/people/jp/SNAPSHOT-29042007/zenwalk-4.6.iso)
FRANCE : [http://zenwalk.linuxish.net/people/jp/SNAPSHOT-29042007/zenwalk-4.6.iso](http://zenwalk.linuxish.net/people/jp/SNAPSHOT-29042007/zenwalk-4.6.iso)

---

### Post by DJiNN on 2007-04-30
Do you know if it's possible to do the equivalent of a "dist-upgrade" to bring my 4.4.1 up to the 4.6 beta specs?  I'm not sure how to go about it & don't want to break it as it's working really well at the moment. 

Thanks.....
DJiNN

---

### Post by satanius on 2007-05-01
It is possible, just follow the instructions in this wiki [http://wiki.zenwalk.org/index.php/Snapshot_for_Toolchain](http://wiki.zenwalk.org/index.php/Snapshot_for_Toolchain).

---

