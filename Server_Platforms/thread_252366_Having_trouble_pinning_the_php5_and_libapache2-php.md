---
title: "Having trouble pinning the php5 and libapache2-php5 packages.."
date: 2006-09-06
forum: Server Platforms
---

### Post by JLTB on 2006-09-06
Hi,

I've had to pin down a few packages before in Debian, and once before on Ubuntu Breezy .. so I think i'm following the steps right .. but for some reason everytime I try to dist-upgrade my server it want's to upgrade the packages I've pinned down (to older versions).

My system is a DELL PowerEdge 2850 running the 2.6.15-26-amd64-xeon kernel with Ubuntu 6.06 Server installed.  All packages are up to date, except for everything relating to PHP5 which I have to keep at 5.0.x (the app we're running needs that version ... sux i know).

Here's my /etc/apt/preferences file..

```

Package: php5
Pin: version 5.0.5-2ubuntu1
Pin-Priority: 2001
Package: php5-cli
Pin: version 5.0.5-2ubuntu1
Pin-Priority: 1001
Package: php5-common
Pin: version 5.0.5-2ubuntu1
Pin-Priority: 1001
Package: php5-cgi
Pin: version 5.0.5-2ubuntu1
Pin-Priority: 1001
Package: php5-dev
Pin: version 5.0.5-2ubuntu1
Pin-Priority: 1001
Package: php5-mysql
Pin: version 5.0.5-2ubuntu1
Pin-Priority: 1001
Package: php-pear
Pin: version 5.0.5-2ubuntu1
Pin-Priority: 1001
Package: libapache2-mod-php5
Pin: version 5.0.5-2ubuntu1
Pin-Priority: 1001
Package: php5-gd
Pin: version 5.0.5-2ubuntu1
Pin-Priority: 1001
Package: php5-mhash
Pin: version 5.0.5-2ubuntu1
Pin-Priority: 1001
Package: php5-curl
Pin: version 5.0.5-2ubuntu1
Pin-Priority: 1001
<there are no empty line breaks at the end of the file...>

```

My /etc/apt/apt.conf file looks like this...

```

APT::Authentication::TrustCDROM "true";
Acquire::http::Proxy "false";
APT::Default-Release "dapper";
<there are no empty line breaks at the end of the file...>

```

I have tried everything with and without the ```
APT::Default-Release "dapper";
``` line to no effect.

Anybody have any ideas?  Do i need to pin a few more or less packages?  Any experience with this problem?

Thanks in advance for any help you can provide!!

James Andres - [www.projectopus.com](www.projectopus.com)

---

### Post by JLTB on 2006-09-07
Anybody? Anybody? Buhler? Buhler?

Seriously though, the issue is still plaguing me and I don't have a good way to update my system until these packages are pinned (safely update that is...).

Help :-)

---

### Post by techbri on 2006-09-27
JLTB, You mentioned that you have Ubuntu 6.06 running on a PE2850. What did you have to do to get the raid controller configured? I have a PE2850 with a Perc 4/DC split backplane on it. I have a raid 1 for the OS and and raid 5 for the data volume. I would like to put Ubuntu on it and then VMware Server but I see some issues dating back to 2005 where problems have been reported with the perc controllers and Ubuntu. Is this no longer the case? I appreciate any assistance you can provide. Thanks!

---

### Post by JLTB on 2006-09-27
Hey techbri,

This is getting kinda offtopic, but i'll try to answer two things (what happend with my problem, for the curious, and your raid question)

[LIST=1]
[*]First, on the original topic of the thread.  I actually didn't solve this problem but found a way to get the "normal" version of PHP5 (5.1.2) running correctly for me.  So the pinning issue is yet unresolved.
[*]With regard to the PERC controller, I actually didn't know there were any issues installing Ubuntu using this RAID controller.  I just stuck the disk in and ignorantly installed the system.  Everything went smoothly--for me at least!
[/LIST]


One hic-up I did encounter was that the RAID controller needs to be turned on in the BIOS before it will activate correctly.

This happend to me after I sent my box into Dell for service, they replaced the backplace + RAID controller (after the service system wouldn't boot).  Once I figured out that the controller wasn't set to "RAID" mode in the bios I figured I'd turn it on.  However, when you try switching it to RAID the controller will scream "I'm going to turn these disks into a RAID volume. If you do this ALL your data will LOST FOR SURE!" (well something like that).

I had my stuff backed up, so I hit yes.

After the process was complete I expected my disks to be wiped as the message said, instead I found that everything was still intact!  This was because my disks were already a RAID setup, from before the servicing.

So, although I wouldn't bet money against it, it appears that you can flip the RAID switch on and off in the BIOS without any destructive effects to your volumes.  I'm not crazy enough to try this with important data though.....

Oh yea, one last tip.  The lm_sensors system reads every sensor under the sun EXCEPT the sesors on Dell servers :-(.  So as far as I can tell you need to run  Red Hat if you want to know your system temp, fan speeds, or the state of your hard disks.

---

### Post by techbri on 2006-09-27
Thanks for your response. Sorry to take things off topic. I think I  will give it a whirl.

---

### Post by techbri on 2006-09-27
One last question....do you have the perc 4/DC, 4e or another controller. Mine is reported as the 4/DC and I just want to make sure it will work. Thanks again!

---

### Post by JLTB on 2006-09-28
The 4e AFAIK.

---

