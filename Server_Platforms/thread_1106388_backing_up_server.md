---
title: "backing up server"
date: 2009-03-25
forum: Server Platforms
---

### Post by I_M_smbody on 2009-03-25
What is the best kind of recovery preparation  for a ubuntu server?
I do back ups of the system and have copies of the smb.conf, fstab, password and group file but I'm not sure I have every contingency covered. 

So my question is how do experienced admins handle system back up and recovery when you want to be sure you can recover and get up and running quickly? 

from bare metal on the same server?

onto a new server systems? (in case of fire or meteor) 

Part of the problem is I'm working on SOP's for the company so I need to cover every possible scenario as simple as possible but in detail. My usual seat of the pants methods aren't going to work. 

My standard MO has been to just do a fresh install since I have 12 users and a fairly simple set up then just restore the data to the necessary partitions but I need something  someone else can do if I get hit by a fast moving bus while carrying the fileserver. 

Thanks

I'M somebody

---

### Post by HermanAB on 2009-03-25
My production systems are all virtual machines and the data is not kept on the VM, but rather on a separate NFS mounted disk drive - a NAS in other words.  I save the VMs on DVDs and backup the data to USB disk drives using rsync.

Cheers,

Herman

---

### Post by I_M_smbody on 2009-03-26
I like the sound of using a virtual machine to store the server I was thinking of that I like the Idea that I can run the machine on any architecture. Is it possible to convert an existing server to  a vm.

what are you using for the virtual server software? vmware? do know of a tutorial that covers the set up I was checking through your site and I couldn't find one.]
Thanks

IMsmbody

---

### Post by hyper_ch on 2009-03-27
setting up a machine does not take much time if you have:

- copy of all data
- copy of all config
- list of isntalled packages.

I use for that rsync to backup my server to different server. In case server gets hacked or something, I can through an webcontrol of my server provider do a complete re-install of the server (takes about 15min to put debian in default state on there) and then just mirror data backup and install according packages again.

---

### Post by I_M_smbody on 2009-04-07
I have records of the set up and I have copies of the fstab, the password and group files
and smb.conf file. what other file would you suggest I copy it make the restore quick?

Thanks 

IM Smbody

---

### Post by hyper_ch on 2009-04-07
generally the /home partition, the /etc one.. additionallöy maybe /var/www and a backup of databases (e.g. mysql).

---

