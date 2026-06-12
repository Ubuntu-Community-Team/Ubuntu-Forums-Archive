---
title: "tboot setup w/ Ubuntu 12.10 server"
date: 2013-03-01
forum: Security
---

### Post by emmaker on 2013-03-01
I'm trying to setup tboot on a dual E5-2600 server running Ubuntu 12.10 64 bit server and I am pretty lost. To me it looks like the way it currently works has changed and the documentation hasn't caught up yet (or at least what I've looked at).

I got tboot and TrouSerS install on the server. That went ok and from that I get the documents lcptools2.txt and policy_v2.txt for tboot in /usr/share/doc/tboot. They have you create a file called list.data and that is put into your grub.conf file. I can create that file without any issue.

Here's where things start to diverge and I get lost.

First thing is that the system is using a grub.cfg file that was created from the scripts in /etc/grub.d using grub-mkconfig, there is no grub.conf file. There are files in that directory that are added from installing tboot called 20_linux_tboot and 20_linux_xen_tboot which create tboot boot items. I've looked into 20_linux_tboot script and it looks for a SINIT file but i don't see it looking for any form of list or data file to get the keys and other information that is put into the list.data file. So is there any information on how to setup tboot with these new scripts or could someone help out with it?

I've read in one post that tboot doesn't work with an EFI boot and you have to use legacy boot. I've checked my /etc/fstab file and don't see a EFI partition in there so I'm assuming that I'm doing a legacy boot. Any comments on whether or not you have to boot in legacy or not?

Any other ideas and thoughts about setting up and using tboot?

I'm not a Linux system person so I don't know a lot of ins and outs of doing stuff. So if you have any ideas or pointers please keep them simple, thank you.

Thanks in advance.
Jay S.

---

