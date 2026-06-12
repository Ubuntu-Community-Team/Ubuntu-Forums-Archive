---
title: "Dell PERC RAID Controller 3/Si"
date: 2008-09-22
forum: Server Platforms
---

### Post by chainofcommand02 on 2008-09-22
Hello all, I believe this is my first post on the Ubuntu Forums. I've had a little Linux/Ubuntu experience but please treat me like the complete noob that I am.

The question: As I understand it, Ubuntu 8.04 might not/does not support Dell PERC RAID Controller 3/Si, is that correct?

I have a used Dell PE 2450 that I want to make a fairly basic file server for my home network, right now it has the previous owner's Windows Server 2003 installed on it. Before I do anything destructive (DBAN the disks, create a new RAID array, etc) I wanted to get some facts straight. I appreciate everybody's help!

---

### Post by windependence on 2008-09-23
Well it sure didn't like it on my server. Ubuntu would load fine but days later kernel panic until I removed the Perc3 (LSI Megaraid) controller.

-Tim

---

### Post by chainofcommand02 on 2008-09-23
Well that's a bummer. What do you recommend I do then? I would really like to use the hardware RAID. So what other distros should I look at? I've tried a few, and OpenSUSE looks promising, the live CD works very well, but of course actually installing the distro on the server is a different matter altogether.

---

### Post by windependence on 2008-09-24
Well SuSE is fine, and so is CentOS. If you don't need a GUI and you want stability, I would highly recommend FreeBSD. You can get more information at daemonforums.com.

Please ask if you need more info. I'll give you a hand.

-Tim

---

### Post by chainofcommand02 on 2008-09-26
OK well these three options (OpenSUSE, CentOS and FreeBSD) all sound promising, each have their strengths... have you seen any of these three work FOR SURE with my hardware (Dell PE 2450) or so I just have to just jump in blind? It sounds like FreeBSD has a steep learning curve, but so did Ubuntu coming from Windows... Like I said before I don't want to DBAN disks or format anything or do anything destructive until I have a solid plan... But if I have to, I have to. Anyway, it looks like this thread is about to take a hard left out of "Ubuntu" and into... something else. Do we need to move this conversation elsewhere or leave it as-is in the server discussion? Like I said I'm new around here and I need any guidance you can give me. Thank you very much!

---

