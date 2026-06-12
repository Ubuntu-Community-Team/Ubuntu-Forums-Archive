---
title: "Diskless cluster - nfs-common boot problem"
date: 2011-04-27
forum: Server Platforms
---

### Post by simonglewis on 2011-04-27
Hello,

This is my first post on these forums.  I have found them to be an invaluable source of knowledge for most of my linux based problems - so thank you for that!

I am currently attempting to build a small diskless cluster with ubuntu - following the guidelines at:
[www.calvin.edu/~adams/research/]("http://www.calvin.edu/%7Eadams/research/")**microwulf**/sys/**microwulf**_notes.pdf

I have the cluster up and running, but there is a problem with the nfs.  The cluster nodes can see their own file system, but cannot mount any other folders (that have been shared in the /etc/exports file on the head node)
The command:
sudo mount 192.168.2.1:/home /home 

gives an error message:
mount: wrong fs type, bad option, bad superblock on 192.168.2.1:/home
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I can solve this problem bt installing either nfs-common or nfs-client on the node.

However, as soon as nfs-common is installed on the node, it hangs during the restart, just after the following:
Begin: Running /scripts/local-bottom ...
Done.
Done.
Begin: Running /scripts/init-bottom ...
Done.


Then nothing happens.
I can only get it to reboot by chroot into the file system and apt-get remove --purge nfs-common.

I am still quite inexperienced with linux, so am not sure exactly what the problem is.  Is there a way to disable nfs-common activating at that point in the boot sequence?  What is the best way to troubleshoot this problem?
There is nothing written to the logs at this point in the boot.


Thanks for looking, and any help will be greatly appreciated.

Simon

---

### Post by simonglewis on 2011-04-27
I forgot to add - I am using Ubuntu 10.04 LTS.

I have tried various fixes, including using ext3 and ext4 filesystem on the head node

I have tried deleting various files that nfs-common adds to the system

Let me know if you need any other info.
Thanks,  Simon

---

### Post by Usa_Tony_Cuba on 2011-04-27
> **simonglewis said:**
> 
sudo mount 192.168.2.1:/home /home 

Are you sure that is the correct Internal IP..?
Look to my like that is Your Gateway (router IP).. have you tried   192.168.0.100 , 192.168.2.100  ...?

You might want to check the configuration of your router ..? to know which is the reserved IP witch are of the machine you are trying to set

---

### Post by simonglewis on 2011-04-27
Thanks for the reply.

Yes - I am pretty sure this IP address is correct.  I am mounting the master home directory from the node.  The master ethernet port is set to 192.168.2.1.

This mount command works fine after i have installed nfs-common.  The problem occurs when I try and re-boot the node - it hangs.

---

### Post by d1ngd0 on 2011-05-04
I have the same problem. If you have figured it out please tell me, otherwise I will tell you if I figure it out.

---

### Post by sirlark on 2011-05-26
Hi, I'm having the same problem too. We had a working diskless cluster with lucid. When we applied updates within lucid (of which nfs-common was one update) the nodes no longer booted, with the same problem as above. We have since tried the following

Created a new chroot filesystem using debootstrap for lucid (this worked fine)
Applied updates to this system (it broke)

Created a new chroot filesystem using deboostrap and natty and immediately updated (broke)

I'm currently in the process of trying natty without updates. Our idea is to get natty without updates booting diskless then pinning nfs-common to ensure it doesn't get updated. Assuming natty's un-updated nfs-common doesn't already exhibit the problem.

Otherwise, we'll have to drop back to lucid.

I haven't found a bug report for this anywhere, and until I read this post today, I wasn't sure in which package the problem lay. Initially I thought the problem was in the initrd image. I think this deserves a bug report?

---

### Post by sirlark on 2011-05-26
quick update, natty sans updates didn't work. I went back to my original lucid chroot, and purged nfs-common and its dependencies. I then removed lucid-updates from my apt/sources.list, and reinstalled nfs-common. My nodes now boot again.

Clearly the problem is with nfs-common or one of its dependencies.

---

