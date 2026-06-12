---
title: "failed upgrade to Hardy"
date: 2008-08-13
forum: Server Platforms
---

### Post by rasp1 on 2008-08-13
I was upgrading from Feisty to Hardy via do-release-upgrade, and it got stuck on the generating locales.  I restarted the machine and it seemed to mostly work, but I can't run apt-get because it says that it was interrupted and that I need to dpkg --configure -a.  When I run it it hangs on the locales again, and takes up all available cpu time.  I let it run for a week to see if it was just being slow to no avail.

  I would not like to reinstall, I would like to salvage this if possible.  Can anyone point me in the right direction, I have no idea where to go from here and google hasn't been a friend.

 The ps aux
root		4199	0.0		0.4	3768	2480	pts/0	S+	Aug05	0:00	dpkg		--configure -a
root 	4220	0.0		0.0	1768	488		pts/0	S+	Aug05	0:00	/bin/sh -e	/var/lib/dpkg/info/locales.postinst configur
root		4221	0.0		0.1	1768	528		pts/0	S+	Aug05	0:00	/bin/sh /usr/sbin/locale-gen
root 	4235	0.0		0.0	1768	312		pts/0	S+	Aug05	0:00	/bin/sh /usr/sbin/locale-gen
root		4264	99.9 	10.4 54968	53768	pts/0	R+	Aug05	2576:56	localedef --no-archive --magic=20051014 -i en_US -c -f
root		4265	0.0		0.0	0		0		pts/0	Z+	Aug05	0:00	[gzip] <defunct>

To me it looks like the gzip is messing up, but I don't know.

---

### Post by joebeasley on 2008-08-15
System hangs trying to load the locales. (Boot to recovery mode and run 'dpkg --configure -a'

I also found that the system will not boot with the 2.6.24-20 kernel.  Had to use the previous one.

---

### Post by Tearstone on 2008-08-22
I am having precisely the same issue right now. I did notice it was passing what I thought it the wrong version to the command line, so I attempted to manually run the locales.postinst configure manually but it just sits there. I seems as though it is waiting for something?

---

