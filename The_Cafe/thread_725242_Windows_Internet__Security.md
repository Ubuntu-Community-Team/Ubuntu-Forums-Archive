---
title: "Windows Internet  Security"
date: 2008-03-15
forum: The Cafe
---

### Post by dyous87 on 2008-03-15
Hello everyone. I have a questions regarding some open source internet security programs such as ClamWin AV. I run Windows XP inside of virtual box in order to run some of those annoying windows programs that just don't seem to have a proper linux alternative. At the moment for my antivirus program I am using ClamWin AV and I am running it along side the default Windows Firewall. 

My question to you is: do any open source programs exist that have the features of a professional proprietary internet security suite such as Norton or McAfee? Obviously for the virus scanner we have ClamWin. Does anyone know how this fairs against those proprietary scanners?

Also what can be used for a firewall and is there anyway to have a scanner constantly check in the background for security threats or viruses. (ClamWin only works on demand).

These are the features that McAfee Internet Security Suite offers: [http://us.mcafee.com/root/landingpages/affLandPage.asp?affid=0&lpname=14229&cid=39235](http://us.mcafee.com/root/landingpages/affLandPage.asp?affid=0&lpname=14229&cid=39235). can these features be replicated by any existing open source packages? If so I propose that they somehow be combined into a full internet security suite that can work together efficiently.

---

### Post by freebios on 2008-03-15
clam is competitive with proprietary software because the community submits so many virus/definitions to be included, proprietary companies don't have this kind of community so they lack in this area.  gnome lokkit is a great open source firewall, and if looking for a windows fire wall zone alarm is proprietary but is available at no charge from zone labs.  i prefer free software because you can use it with less restrictions to accomplish the same task, and yes free software is  made by the community is just as good as proprietary software in many cases.  hope this info helps :guitar:

---

### Post by dyous87 on 2008-03-15
Thanks. That's exactly what I figured about ClamWin AV. I was just a bit hesitant because I've been running it inside of my Virtual Box Windows XP for over a year now and I have never ever had ti detect one virus. When I was a windows only user a few years ago I used to use Norton and virii were always detected.

Then again I don't really browse the web on my windows installation much so I am sure that has a lot to do with it.

About Zone Alarm, I do know of this program and have used it before but I would much rather prefer open source applications that are less restrictive and built by the community. If no such Internet Security Suite existed, which i believe is the case, I was hoping to find individual programs that can somehow be bundled together in order to offer these features in an easy to use package.

---

### Post by dyous87 on 2008-04-16
So I have been googling around and trying to find a full effective open source windows security suite and I finally came across IPCop which is a Firewall Linux Distro. 

I was wondering if it would be possible to secure windows by somehow setting this up inside Qemu or VirtualBox in a Windows host. 

I read this tutorial explaining how to set it up within a windows host using windows virtual pc. I tried following the guide but I couldn't get virtual pc running in windows xp and using qemu for me hasn't worked thus far.

Does anyone know if this is possibly with qemu?

---

