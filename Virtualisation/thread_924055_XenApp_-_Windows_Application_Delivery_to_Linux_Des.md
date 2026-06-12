---
title: "XenApp - Windows Application Delivery to Linux Desktop?"
date: 2008-09-19
forum: Virtualisation
---

### Post by JinxAu on 2008-09-19
I have been trying to figure out whether the Citrix XenApp software allows the delivery of Windows Applications to a Linux Desktop... have had no luck with the Citrix website, except for finding that it seems to work on Mac OS X (and apparently the iPhone?).

Thought I would throw the question up here to see if anyone has any information on this, as it would definitely be a huge plus for putting Linux on the Desktop in Enterprise and Education environments... because of this, I am suspecting this feature is not enabled. ;)

Cya round
Jinx

---

### Post by lazyart on 2008-09-19
I would think yes, since XenApp is MetaFrame.

---

### Post by austinjh on 2008-09-21
Citrix has been delivering windows applications to linux desktop for about the last 10 years. As a Citrix consultant I'm fortunate enough to have implemented this solution a number of times in my real world job. Not just educational sector either. I had the pleasure of doing this with a 100 Red Hat linux desktops for a UK based insurance company based in the South East. RH wasn't my first choice, the company had been using it since before year 2000.

---

### Post by austinjh on 2008-09-21
Having thought about, many of the "little black box" thin client terminals run on a linux stack. Check out NeoWare, Wyse and HP thin client devices.

Also check out the Linux based [ThinStation]("http://sourceforge.net/projects/thinstation/") project.

---

### Post by JinxAu on 2008-09-21
My understanding is that Citrix has been doing Terminal Services "on-top-of" Linux based systems for a while now. However, I am wondering about the applications delivered "into-the-desktop-environment".

After checking out the XenApp demo videos, where an Application such as Microsoft Powerpoint is running "as an application" on the demonstration Windows Desktops... got me wondering whether they are doing the same kind of delivery with Linux. 

Terminal Services is a fair solution, but having the applications integrated straight into the Desktop seems to make more sense, as the user can actually use the local desktop (Linux) for it's range of applications and then open Microsoft Office when they need to, using it like any other application on the Linux Desktop.

I know you have Cross-Over Office/Wine solutions, but being able to centrally manage these kinds of applications across platforms makes more sense to me - at least in a fleet/lab environment.

Cya round
Jinx

---

### Post by JinxAu on 2008-10-08
Have been checking out Ubuntu Hardy and KVM and found this handy Help document: [https://help.ubuntu.com/community/SeamlessVirtualization](https://help.ubuntu.com/community/SeamlessVirtualization)

Apparently you can setup rdesktop to provide Seamless Applications via RDP.

Definitely a helpful solution for Linux Desktop migration. :)

Interesting to see whether you can use the local Linux resources such as CDROM, Printers, USB storage, HDD storage etc.

Cya round
Jinx

---

