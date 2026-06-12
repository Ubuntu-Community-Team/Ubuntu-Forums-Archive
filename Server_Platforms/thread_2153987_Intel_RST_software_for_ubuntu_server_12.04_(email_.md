---
title: "Intel RST software for ubuntu server 12.04? (email notifications?)"
date: 2013-06-13
forum: Server Platforms
---

### Post by kevinxsalerno on 2013-06-13
Hi. I am running an ubuntu 12.04 server.

I have a raid 1 array for my OS drives, and a raid 5 array for my storage drives. 

I used the built into the motherboard intel utility to create my raid. I installed ubuntu on my motherboard/bios controlled raid and mounted my storage drive just fine.

My question is now, how can I install some sort of software within my ubuntu OS to know if/when a drive fails and how can I get it to email/text me? This server is in a closet with no screen, I can't just reboot it every now and then to look at the bios post.

---

### Post by kevinxsalerno on 2013-06-17
Over 100 views and 0 replies.... I'm guessing nobody knows the answer

---

### Post by SeijiSensei on 2013-06-18
If you are using hardware RAID, which it sounds like you are, then you would need to use an Intel-specific utility to manage notifications.  From the operating system's point of view, the RAID array appears as a single device.  It has no way to tell that there is an array there.

---

