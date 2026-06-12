---
title: "Virtual Desktop?"
date: 2008-12-08
forum: Virtualisation
---

### Post by sndnichols on 2008-12-08
I have an asus eeepc. It is pretty good to use for e-amil, web, etc. I would like to set it up to also use the power of my server. At present, I am running 2 vm's using VMware server. I am considering going to esxi, too. The vm's I ma using are for webserver and mythbuntu. I am not sure of the "best" way to implement using the eeepc for a more desktop like use. I looked into LTSP but it seems like I won't be able to use the storage or external cd without some difficulty. I want my daughters to learn to use computers. Logging in with several users on the eeepc kind of slows it down as well. I am thinking of setting up a desktop (ubuntu 8.10) on the server and then accessing it from the eeepc. Does that sound like the "best" way to go? BTW, the eeepc connects to the server wirelessly through an AP on my home network. TIA

PS The server is runnung 8.04 server, it is dual processor quad core, 8G ram, 4TB storage.

---

### Post by Dedoimedo on 2008-12-09
Hello,

How many hard disks do you have? If you allocate virtual machines to several hard disks, you'll improve performance. Pre-allocating hard disk space also helps. I think the simplest solution is "normal" virtualization and then connect to remote host and run virtual machines from there.

Dedoimedo

---

### Post by sndnichols on 2008-12-09
I have (4) 1TB drives. At present, I have (10) partitions on them uusing LVM. The partitions are root, boot, swap, tmp, var, usr, home, media, etc, and opt.  All of the vm's are on the same partition, that is /usr. The vm's have pre-allocated space. Should I move the vm's to seperate partitions?

---

### Post by Dedoimedo on 2008-12-09
It would improve the performance for sure. Even separate hard disks. Single hard disk head per vm, optimal. I'm doing it at home. The difference is very much noticeable when your hard disk single-tasks one os or has to jump between two. Now, three, four, eight hard disks, the more the better.
Dedoimedo

---

### Post by sndnichols on 2008-12-09
WHich partiotions are "most appropriate" for the vm's? I was thinking /usr would make the most sense originally, but I am new to servers and linux. Seems like the webserver could go to /opt and put the desktop vm on /home for my girls. Does that seem like a good way to use the partitions "correctly"

---

### Post by Dedoimedo on 2008-12-09
Why not create a partition called /vm or /data?
Dedoimedo

---

### Post by sndnichols on 2008-12-09
So how would I get another drive? Are you suggesting shrinking the partitions so I can reclaim one of the drives? I am not quite sure what you are telling me.

---

### Post by Dedoimedo on 2008-12-09
Well, you seem knowledgeable enough, I think you can figure what you want. The LVM allows you quite a bit of flexibility. I would leave a single physical disk unused and then mount it for vm use only.
Dedoimedo

---

