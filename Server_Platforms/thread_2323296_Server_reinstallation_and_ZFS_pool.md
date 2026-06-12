---
title: "Server reinstallation and ZFS pool"
date: 2016-05-04
forum: Server Platforms
---

### Post by joebell on 2016-05-04
I have had an Ubuntu Server 14.04.4 LTS running with one ZFS pool used for data storage and shares populated via Samba. Due to number of reasons a new installation will have to be done on the system, but I do not want to loose the data on the present ZFS storage pool. After the new installation is finished, I would like to re-attach the existing ZFS storage pool from the old system to the new system. Everything will be performed on the same box, just the operating system will be renewed from the scratch. It would be great if someone among you can provide help and/or instructions how to proceed, as I am quite new to Ubuntu and afraid I can lose the data after the new system is on and running. Unfortunately, there is no option to move the data to another storage temporarily, then create completely new ZFS pool on the new installation and move the data from temporary storage backwards.

---

### Post by howefield on 2016-05-04
Thread moved to the "*Server Platforms*" forum.

---

### Post by darkod on 2016-05-04
I haven't done anything similar (only quick tests in vbox with small pools), but in theory the steps are:
1. Export the zfs pool(s)
2. Reinstall the OS on the OS disk (I assume it's on a separate disk)
3. Import the pools and re-create the samba shares
4. If you have local users defined for the shares you will have to re-create them too of course

One question: How urgent it is to do the installation right away? I am asking because it might be best to use the latest 16.04 LTS that just came out, but I usually don't start using the new releases until the first .1 which should come out sometime in August.

---

### Post by joebell on 2016-05-05
Hi Darko,

Nice to have your instructions on how to preserve existing ZFS pools when going to reinstall Ubuntu Server 14.04.4 LTS 64bit operating system from the scratch. In my first post I was intending to ask the same question as yours about the new release of Ubuntu Server 16.04. Time is no limit, hence I will definitely give a try to this new operating system. Moreover, my idea is to make that new installation a Domain Controller using Samba4. I do hope that everything will go smoothly. Allow for some time, and I will let you know the results.

---

### Post by joebell on 2016-05-08
Darko,

Many thanks for your advice. Everything was working like a charm.:D

---

### Post by joebell on 2016-05-13
Darko,

I promised to let you know my experience building the new Ubuntu Server 16.04 LTS. Besides ZFS storage migration from the old system (Ubuntu Server 14.04.4 LTS) I decided to configure the box to act as a DNS, DHCP and Samba 4 Domain Controller providing shares for Windows users. The ZFS transfer worked excellent. Then I tried to manage installation of BIND9 with DHCP with dynamic updates on two separate boxes to achieve BIND+DHCP failover. Again, everything turned out well. Finally I installed Samba 4 and wished to make the server a Domain Controller and a File Server for Windows workstation. This procedure I had made many times in the past on the previous Ubuntu Server releases. I have had no difficulties at all until I started with Ubuntu Server 16.04 LTS and Samba 4.3.9 for Ubuntu. Not to be rude, I just wish to express my disappointment here. Installation was OK. Domain provision looked great. I can even join Windows workstations to the domain. No problem. Active Directory can be managed directly from Windows workstation, either. Everything seemed to be accomplished without any hassles. All essential testing was good, too. Finally, this hit me hard. There is no chance to connect to the shares even if I am trying it as a Domain Admin. I can see them all, but no connection to none of them including netlogon and sysvol. I issued this command on the domain controller - smbclient //localhost/netlogon -UAdministrator -c 'ls' - and have got this error: NT_STATUS_OBJECT_NAME_NOT_FOUND listing \*. Till now I have not found any solution for this. What I know is I am not alone who has similar experience. Unfortunately, everything I tried to avoid this problem failed. Now I am fed up and wish to go back to the "old good" Ubuntu Server 14.04.4 LTS x64.

If you knew someone by chance who would be able to help, I can give the new system a once more try. If not, there is no other way but to throw away Ubuntu Server 16.04 and start the installation of Ubuntu Server14.04.4 LTS from the very beginning.

---

### Post by darkod on 2016-05-13
I think you are too fast in writing off 16.04. Can it be a permissions issue? Something already existing on the pools or something that needs to be configured again after the OS reinstall?

16.04 is rather new but during development there is a lot of testing like for all LTS versions. It might be a bug that no one caught during testing, or it might be just something that can be easily solved.

---

### Post by joebell on 2016-05-14
Darko,

It is nice to hear from you. I have tried everything I have known from the past. Another post have been submitted asking someone on this Forum for help who might have had similar troubles like me - see this link [http://ubuntuforums.org/showthread.php?t=2324439](http://ubuntuforums.org/showthread.php?t=2324439). It means I am not going to reinstall the system immediately. Another temporary solution can be applied to users foe a short time. That's why i can wait a little bit to get an answer either by searching Internet and/or receiving reaction to my post herein. Here is another link (in Russian) - [http://forum.ubuntu.ru/index.php?topic=273123.15](http://forum.ubuntu.ru/index.php?topic=273123.15). They are discussing the same behavior as I am facing. I am not sure if you can read/understand it, but in the last post on that page the man is giving his opinion in Russian that can be translated as "It seems that Samba will take a long time to become a real AD DC... ".

Although I do not agree with him totally (he must be a Windows guy), my experience with Samba 4.3.9-Ubuntu on Ubuntu Server 16.04 LTS is the same like his one.

Well, I will be trying to solve that issue within some period of time, but finally and for sure a point will be achieved at which I will have to make my final decision. I will be keeping you informed.

Best Regards!

---

