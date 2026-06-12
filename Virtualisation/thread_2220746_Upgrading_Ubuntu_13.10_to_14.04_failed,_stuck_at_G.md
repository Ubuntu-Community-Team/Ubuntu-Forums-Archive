---
title: "Upgrading Ubuntu 13.10 to 14.04 failed, stuck at GRUB prompt"
date: 2014-04-29
forum: Virtualisation
---

### Post by christiaan-c on 2014-04-29
During the dist-upgrade of my Ubuntu 13.10 server, it got stuck during some part of GRUB.
The bug resulted in: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1311543](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1311543)

After retrying it failed again and I decided to reboot to see if it would fix my system.
Sadly though, I'm stuck at the GRUB rescue prompt and I have no clue what to do there.

After a bit of research I gave the boot-repair disc a try but it seems to fail running the specified commands.
An error in grub-pc.

My boot info script:
[http://paste.ubuntu.com/7358757/](http://paste.ubuntu.com/7358757/)

I run the Ubuntu server in a Xenserver 6.2 VM.

As a GRUB n00b I'm kinda clueless where to start.
Can anyone help me trying to tackle this problem?

---

### Post by ott-fogliata on 2014-05-12
Hi, 
i have same problem; Is there anyone has solved it?

thanks

---

### Post by oldfred on 2014-05-12
@ott-fogliata
I doubt that your problem is exactly like the OP. He had an install inside a virtual system with LVM. If Boot-Repair cannot correctly mount that and reinstall grub I do not know what to do for him.
But you issue should be a lot different. Start a new thread and post a link to BootInfo report from Boot-Repair.

---

### Post by ott-fogliata on 2014-05-14
@oldfred
Hi Oldfred, Excuse me, I think I have the same problem 'cause it all happened during dist-upgrade from 13.10 to 14.04 LTS in a virtualized ubuntu server (Xen Server 6.2)
Hi,
Ot.

---

### Post by oldfred on 2014-05-14
Ok, but I am moving thread to visualization sub-forum where those who know more may see it.

---

