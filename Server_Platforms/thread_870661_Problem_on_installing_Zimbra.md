---
title: "Problem on installing Zimbra"
date: 2008-07-26
forum: Server Platforms
---

### Post by satimis on 2008-07-26
Hi folks,


Ubuntu 8.04 server amd64
zcs-5.0.8_GA_2462.UBUNTU6_64.20080709205157.tgz


Zimbra package is retained and decompressed on /usr/src/


On running;
# ./install.sh```

....

Checking for prerequisites...
    NPTL...FOUND
    sudo...FOUND sudo-1.6.9p10-1ubuntu3
    libidn11...FOUND libidn11-1.1-1
    fetchmail...FOUND fetchmail-6.3.8-10ubuntu1
    libgmp3...MISSING
    libxml2...FOUND libxml2-2.6.31.dfsg-2ubuntu1
    libstdc++6...FOUND libstdc++6-4.2.3-2ubuntu7
    openssl...FOUND openssl-0.9.8g-4ubuntu3.3
    libltdl3...FOUND libltdl3-1.5.26-1ubuntu1
Prerequisite check complete.
Checking for standard system perl...

###ERROR###

One or more prerequisite packages are missing.
Please install them before running this installer.

Installation cancelled.

```

Installation failed.  But I can't libgmp3 on Ubuntu repo.


On googling I found following thread;
Xen Debian Etch libgmp3...MISSING libxml2...MISSING
[http://www.zimbra.com/forums/installation/10445-xen-debian-etch-libgmp3-missing-libxml2-missing.html](http://www.zimbra.com/forums/installation/10445-xen-debian-etch-libgmp3-missing-libxml2-missing.html)


There advises me referring to "debian etch"


On #10 of
[http://www.zimbra.com/forums/installation/6443-debian-etch-4-0-install.html](http://www.zimbra.com/forums/installation/6443-debian-etch-4-0-install.html)

It seems not very relevant.


Please help.  TIA


B.R.
satimis

---

### Post by songshu on 2008-07-26
could it be libgmp3c2???

not sure but you could give it a try, nevertheless i have installed zimbra on debian etch and it does install and work problem free as it should, so if you can't get it to work you might want to give that a try..

---

### Post by satimis on 2008-07-26
> **songshu said:**
> could it be libgmp3c2???
Hi songshu,

No, libgmp3c2 already installed.

> 
not sure but you could give it a try, nevertheless i have installed zimbra on debian etch and it does install and work problem free as it should, so if you can't get it to work you might want to give that a try..
I got an information on Zimbra forum.  Version 8.04 is NOT supported.  I'm advised going back to 6.06, the out-dated version.  Strange?


satimis

---

### Post by songshu on 2008-07-26
> **satimis said:**
> Hi songshu,

the out-dated version.  Strange?


satimis

not entirely strange though, Hardy is fairly new with a short development period and zimbra is quite a big integrated beast, if i'm not mistaking, the reason zimbra is such a huge package is because it installs its own modified versions of postfix, mysql etc...

this also means that the versions of installed software for dapper are the same as for hardy, thus making the dapper zimbra version not outdated and dapper will also be supported for another 3 years.

besides dapper is a lot more bug free by now compared to hardy, so i reckon that its actually a wise decision to go with the "outdated" version.

---

### Post by satimis on 2008-07-26
> **songshu said:**
> not entirely strange though, Hardy is fairly new with a short development period and zimbra is quite a big integrated beast, if i'm not mistaking, the reason zimbra is such a huge package is because it installs its own modified versions of postfix, mysql etc...
Hi songshu,


Thanks for your advice.


I already have an Ubuntu 6.06 LAMP server amd64 box here.  As curiosity I expect testing a newer version.  Anyway I'll go back to 6.06 version to install Zimbra.  It is only a test.  After testing I may continue installing CRM on this box.


One side question if Zimbra having postfix, mysql, etc modified. would there be any problem on running them.  Debian modifies postfix and mysql as well users have to get documents on Debian running them.  Their official documents are not 100% workable.  I learnt a bitter lesson before.


Others noted with thanks.


B.R.
satimis

---

### Post by songshu on 2008-07-26
> **satimis said:**
> 

One side question if Zimbra having postfix, mysql, etc modified. would there be any problem on running them.  Debian modifies postfix and mysql as well users have to get documents on Debian running them.  Their official documents are not 100% workable.  I learnt a bitter lesson before.


Others noted with thanks.


B.R.
satimis

good question, zimbra install everything in /opt/zimbra so it is installed in a different place
like
/opt/zimbra/postfix/sbin/postfix
instead of 
/usr/sbin/postfix

not sure what the problems will be running different versions simultaneously but i think it would be better to install things like zimbra on a dedicated box anyway.

Just a suggestion:
Just like you i like to play around with new things and have different servers running. You might want to look for running virtual machines if you don't want to buy a huge load of hardware.

As an example i keep notes of my debian etch install [http://songshu.org/doku/doku.php](http://songshu.org/doku/doku.php) where each service is running in a Vserver, it takes me two minutes to install a new and clean playing ground for experimentation and can delete the virtual servers if its not to my liking without disturbing any of my other set ups.

---

### Post by satimis on 2008-07-26
Hi songshu,


> 
Just a suggestion:
Just like you i like to play around with new things and have different servers running. You might want to look for running virtual machines if you don't want to buy a huge load of hardware.

As an example i keep notes of my debian etch install [http://songshu.org/doku/doku.php](http://songshu.org/doku/doku.php) where each service is running in a Vserver, it takes me two minutes to install a new and clean playing ground for experimentation and can delete the virtual servers if its not to my liking without disturbing any of my other set ups.
Good suggestion.


I have a virtual box (VMware box) running for somtimes, with Ubuntu 7.04 as host and CentOS 5 as guest.  I'm running a mail server on host which needs port 25 and 80 because of SquirrelMail.  I have only one public IP.  I failed to backport 80 to the host.  Therefore it would be a problem for me running server on the guest, CentOS 5.  I just leave the box there.  All servers here are headless.  I need a workstation to remote configure them.  Formerly I had an idea building a workstation as host and then installing server on top as guest.  Later I found a solution running LiveCD on a server which is not in use temporarily to configure another server.  Actually what I need on the workstation is an editor, ssh and a GUI brower for browsing Internet for technical documents and help.  While running LiveCD I save documents on an external enclosure with an old HD of 40G installed.


I have an empty box here ready for installing new OS.  What will be your suggestion installing vserver on it?  Which OS would you recommend?  TIA


Others noted with thanks.

B.R.
satimis

---

### Post by songshu on 2008-07-26
recommendations are always personal.

Have tried vmware in the past but it is fairly heavy on resources and i have to allocate resources like RAM and disk space in advance which i don't like.
Others do see an advantage in allocating resources tough, and it also gives you the opportunity to run different OS ,bsd,linux,windows.

Personally i went for Vserver for the following reasons.

diskspace and RAM is used unallocated: 
i have 8GB RAM in my box and if one of the servers needs more then i figured in advance it will just grab what it needs.

speed:
Vserver is more an advanced chroot environment then full virtualisation, in vmware each run there own kernel but in Vserver the kernel is shared between the host and the virtual servers so there is no to very little overhead. this means there is no performance difference when you run something on a dedicated box or in a vserver.

and i don't need to run anything else then linux, i basically use debian etch only, but you could run different templates of .deb and .rpm based distros in Vserver next to each other. No windows or BSD tough.

There are other options as well like Xen, virtuozo and KVM (each has its own advantage/disadvantage) but i use debian and the Vserver kernel is in the repos and its similar to the Jail idea that i was used to in FreeBSD so it suited me well.

I have no complains about the stability, i use it in a production environment and it has never failed me.

As always the choice is yours.

---

### Post by satimis on 2008-07-26
I'm considering installing a basic OS as host on the box without doing any job.  On its top I'll install a virtual server either vserver or KVM (kernel virtualizaion).  All servers will run on guest OS.  I heard KVM sometimes without time testing it.


Regarding RAM, I only have 4G RAM, max, on the servers.  Neither I'm prepared to upgrade it nor there is spare slot to take up addtional RAM.  They are dualchannel RAM, DDR2 800.  The boxes are at least 2~3 years old.  I'm waiting AMD Barcelon CPU on the market to build new box of qaud core CPU and DDR3 RAM.


Regarding HD partitioning I haven't figured out how to do it.  The size of HD is 160G.  The host will take 5~6G capacity max, without any job asigned other than running the virtural server, vserver or KVM.  The remaining capacity of the HD will be shared amongst 3 servers.  Now my questions are;


If host OS takes 6G
guest-1 OS takes 50G
guest-1 OS takes 50G
guest-3 OS takes 50G
balance 4G as spare


1)
how to partition the HD

LV1 6G
LV2 50G
LV3 50G
LV4 50G
???


2)
Can I futher partition each of them as
/boot
/
/var
/home

how to make them?  Partition all of them first before installation of OS started?  If YES there are many partitions;

LV1
LV2
LV3
etc.
....
LV16


3)
I'm prepared to install /boot of host OS on a primary partition.  Then there will be 17 partitions altogether.


4)
Can /home be shared amongst servers (guests)?  Or can /home be shared on all guests and host?


Hoping that you can shed me some light before start.  


TIA


B.R.
satimis

---

### Post by songshu on 2008-07-26
> **satimis said:**
> I'm considering installing a basic OS as host on the box without doing any job.  On its top I'll install a virtual server either vserver or KVM (kernel virtualizaion).  All servers will run on guest OS.  I heard KVM sometimes without time testing it.

i don't know about KVM other then that its supposed to be the first choice in Hardy, you might want to try/investigate.

keep the host clean indeed, i have some software running on the host for my UPS and NTPD + postfix to send mails in case of trouble, but thats about it.

> 
Regarding RAM, I only have 4G RAM, max, on the servers.  Neither I'm prepared to upgrade it nor there is spare slot to intake addtional RAM.  They are dualchannel RAM, DDR2 800.  The boxes are at least 2~3 years old.  I'm waiting AMD Barcelon CPU on the market to build new box of qaud core CPU and DDR3 RAM.


4G RAM is plenty and should be enough to host several dozen servers, don't know about KVM but Vservers share there resources when it comes to RAM, if you run MySQL in 2 servers its not 1 + 1 when it comes to RAM usage.

> 
Regarding HD partitioning I haven't figured out how to do it.  The size of HD is 160G.  The host will take 5~6G capacity max, without any job asigned other than running the virtural server, vserver or KVM.  The remaining capacity of the HD will be shared by 3 servers.  Now my questions are;


If host OS takes 6G
guest-1 OS takes 50G
guest-1 OS takes 50G
guest-3 OS takes 50G
balance 4G as spare


1)
how to partition the HD

LV1 6G
LV2 50G
LV3 50G
LV4 50G
???


you could, but i don't go through the trouble

> 
2)
Can I futher partition each of them as
/boot
/
/var
/home

yes, you can do this within the template options before you make them, but i don't go through the trouble

> 
how to make them?  Partition all of them first before installation of OS started?  If YES there are many partitions;

LV1
LV2
LV3
etc.
....
LV16

something like this below, you can specify everything in the default template or specify it on the command line when making them, as example below this vserver would be installed in /VSERVERS which is a separate partition on my box.

newvserver --vsroot /VSERVERS --hostname ldap --domain cipar.net --ip 192.168.1.5/24 --dist etch --mirror [http://192.168.1.12:3142/debian.apt-get.eu/debian](http://192.168.1.12:3142/debian.apt-get.eu/debian) --interface dummy0

> 
3)
I'm prepared to install /boot of host OS on a primary partition.  Then there will be 17 partitions altogether.


i do this to, but only because i use RAID10 so i made a separate /boot with RAID1, otherwise i would not go through the trouble

> 
4)
Can /home be shared amongst servers (guests)?  Or can /home be shared on all guests and host?


i think you could, if you would mount it over the network it would most certainly possible, otherwise i'm not sure so you might want to check.


I'm a simple guy and therefore like to keep things simple, this always leads to less complication and easier restoring in case of emergencies, so my partitioning is simply like this

/boot 100 MB (only separate because of RAID10) 
/ 10 GB      (10GB is plenty for root, you could do with a lot less)
/SWAP 1GB    ( i never use it actually)
/VSERVERS 989.2 GB (one big partition where all the Vservers are placed)

then i also have another set of disks where i store my backups under
/BACKUP

---

### Post by windependence on 2008-07-26
You guys may be interested to know that VMware is releasing it's ESXi server FREE on Monday, the 28th. There is no host OS for this, it runs on the bare metal and is only 32 MB. If you think VMware server is too heavy, then you should try this. This is the same commercial product people have been paying for. VMware is trying to keep their business from Micro$oft and Sun by giving away their hypervisor. Great news!

-Tim

---

### Post by songshu on 2008-07-26
> **windependence said:**
> You guys may be interested to know that VMware is releasing it's ESXi server FREE on Monday, the 28th. There is no host OS for this, it runs on the bare metal and is only 32 MB. If you think VMware server is too heavy, then you should try this. This is the same commercial product people have been paying for. VMware is trying to keep their business from Micro$oft and Sun by giving away their hypervisor. Great news!

-Tim

well....not really.

as always there is a catch, don't get me wrong, VMWare is a great product, but not just because of its hypervisor, especially the management frame work is what still separates it from Xen and there is a reason my mother warned me never to accept free candy ;)

"start quote from http://blog.scottlowe.org/2008/07/25/my-take-on-free-esxi/"
"
you have to remember that VMware is only releasing ESXi for free. They’re not releasing VirtualCenter for free. You’ll still need VirtualCenter and VI3 Enterprise licenses in order to do stuff like VMotion, Storage VMotion, VMware DRS, VMware HA, VMware DPM
"end quote"

---

### Post by windependence on 2008-07-26
....And you don't need most of that for a small enterprise, or if you are going to use a home grown monitoring system. 

I can clone VMs with all that jazz, and moving machines live (Vmotion) is really cool but do I need it? No. I am rather excited that competition is forcing them to do this. 

Xen would be great if the damn CD would work during an install. Also, since Citrix owns them now, look for them to go the way of VMware soon. Anything that is really desirable in this space is gonna be paid for at first until it becomes ubiquitous and then they will just start charging for support again (which is good because I don't need it since I AM the support).

-Tim

---

