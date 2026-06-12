---
title: "Virtual Ethernet Failed VMWare Workstation"
date: 2010-10-11
forum: Virtualisation
---

### Post by kevinhobson2000 on 2010-10-11
Hi all,

When i started up my Ubuntu box this morning i get the following:

kev@ubuntu:~$ sudo /etc/init.d/vmware start
Starting VMware services:
   VMware USB Arbitrator                                               done
   Virtual machine monitor                                            failed
   Virtual machine communication interface                             done
   VM communication interface socket family                            done
   Blocking file system                                                done
   Virtual ethernet                                                   failed

I am runniing Ubuntu 10.04 and 7.1.2 build-301548.

I a hve tried a reboot and restarting the services to no avil.

Thanks

Kev

---

### Post by kevinhobson2000 on 2010-10-11
Solved this by opening the virtual network editor and clicking save.

Service starts now,

Very odd.

Cheers

Kev

---

### Post by sepdau on 2012-10-19
> **kevinhobson2000 said:**
> Solved this by opening the virtual network editor and clicking save.

Service starts now,

Very odd.

Cheers

Kev

When open it has a > Network configuration is missing. Ensure that /etc/vmware/networking exists.
How to fix it?

---

### Post by overdrank on 2012-10-19
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

