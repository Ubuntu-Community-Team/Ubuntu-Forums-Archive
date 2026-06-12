---
title: "iSCSI support in Ubuntu"
date: 2006-08-15
forum: Repositories &amp; Backports
---

### Post by Widodh on 2006-08-15
I don't know where to post this, so my best guess is this forum.

I want to sent this message to the repository managers, but i don't know where to contact them.

The "ubuntu-archive" mailinglist is a moderated mailinglist, i did not get approval.

I hope somebody can forward this to the right person.

Comments are always welcome!

> 
Dear Sir/Madam,

Recently I started using Ubuntu Dapper on various AMD64 systems and it has really been a nice experience. The packages are well thought of and there are a lot of packages.

In the past i've used Debian Sarge on all my servers, but since the 64Bit support of Debian is not that great, i've moved on to Ubuntu Dapper.

A few months ago the company at wich i work purchased an EMC Cellera
SAN/NAS, this supports iSCSI and NFS.

NFS is widely supported by Ubuntu, but iSCSI is not although these
options are compiled in the kernels:
CONFIG_SCSI_ISCSI_ATTRS=m
CONFIG_ISCSI_TCP=m

In order to use iSCSI on a Linux system you need some tools, i prefer
Open-iSCSI ([www.open-iscsi.org)](www.open-iscsi.org)).
Currently, EMC only supports RedHat Enterprise and SuSE Linux for iSCSI,
this is because there are tools provided for iSCSI by the vendor.

We have been trying to get professional support from EMC for Ubuntu, but
they refuse this support since the iSCSI tools are not provided by the
Ubuntu team.

I have seen that Ubuntu is working hard to get supported by several
vendors like MySQL, IBM (DB2) and Sun, wouldn't it be great if Ubuntu
would be supported by EMC (the largest storage vendor on the planet) as
an iSCSI OS?

That's why I would like to see the Open-iSCSI tools added to the Ubuntu
archives. When the tools are added to the archives i can contact EMC and
ask them to investigate if they can support Ubuntu.

I have been testing a lot with Open-iSCSI under Ubuntu, and it works
fine, so that wouldn't be an issue.

If needed, I can help testing the tools or help creating the packages.

I hope to get a positive response.

With kind regards,

Wido den Hollander
PCextreme B.V. 


---

### Post by Thomas Uhl on 2006-08-19
Hi!

I am also interested in getting the open-iscsi-tools into ubuntu.
If you need help (build server, reposistoy) let me know.

Yours
  Tom

---

### Post by Widodh on 2006-08-19
I would like to help, but i don't know where to reach the right people for this matter?

Does anyone have any idea where to contact the right people?

---

### Post by Thomas Uhl on 2006-08-19
A good start would be to compile current versions of open-iscsi and provide a ready to install package. Are you aware of debian packaging? I think the open-iscsi package for FC6 wouöd be a good starting point.

Yours
  Tom

---

### Post by Widodh on 2006-08-19
Yes, i know how to make Debian packages, so that won't be a problem.

I'll go compile some versions and try to make some working packages.

---

### Post by UbuWu on 2006-08-19
For getting your packages in the repo's, see: [https://wiki.ubuntu.com/MOTU](https://wiki.ubuntu.com/MOTU)

---

### Post by Widodh on 2006-08-21
Thanks, i will take a look at it!

---

### Post by Widodh on 2006-09-07
To give it a little update, i am currently working on a package.

I have been testing a lot with it, and it seems to work fine.

I will test it some more on various systems.

---

### Post by fnjordy on 2006-09-21
This would also have to update busybox-initramfs/initramfs-tools so you could specify "BOOT=iscsi" in initramfs.conf?

So something like [IBM's iSCSI boot support](http://storagefoo.blogspot.com/2006/09/ibm-bladecenter-iscsi-boot-support.html) replaces the TFTP of the Linux kernel and initial ram disk, and the updated initramfs package mounts iSCSI instead of NFS then the rest of the system continues to start.

---

### Post by Widodh on 2006-10-23
Ok, i have been working on the package for some time (and tested it mostly) and i think it is ready for some extra tests.

You can add:
deb [http://pcx.apt-get.eu/ubuntu](http://pcx.apt-get.eu/ubuntu) dapper unofficial

Now you can install: open-iscsi

Note: This package is only available for amd64 and the 2.6.15 kernel.

After installing you have to configure /etc/initiatorname.iscsi after wich you can start open-iscsi.

Now you can detect and login to targets.

I also made a persistent device naming script under /etc/udev/rules.d/10-persistant_scsi.rules

This script makes sure your devices are named persistent on all hosts you detect it on.

You would have to edit SYSFS{vendor}=="EMC", SYSFS{model}=="Celerra iSCSI and SYMLINK+="emc_%c%n" to your needs.

Make sure you restart udev after making any modifications.

Please give me feedback here or via [email]wido@pcextreme.nl[/email]

---

### Post by jasnix on 2006-10-25
Would it be possible to get an edgy package for this ?

I am new to iSCSI and I would like to set it up for the first time.  Could you please provide me with resources/documentation on how to set it up?


Thanks!!

---

### Post by Widodh on 2006-10-25
Well, not for now, i am staying at Dapper for the moment since this is a LTS.

Make sure you install:
- linux-headers
- linux-source
- patch
- gcc
- make

Then you can download open-iscsi from: [http://www.open-iscsi.org/bits/open-iscsi-1.0-485.tar.gz](http://www.open-iscsi.org/bits/open-iscsi-1.0-485.tar.gz)

After wich it is:
```
tar -xzf open-iscsi-1.0-485.tar.gz
cd open-iscsi-1.0-485
make
make install
```

Then use:
```
iscsiadm -m discovery --type sendtargets --portal <iSCSI host IP>:3260
```

To detect targets.

---

### Post by mavila on 2007-10-29
I installed under Edgy the following (which I would suggest using rather than building from source - unless you have a really good reason otherwise) command

sudo apt-get install open-iscsi

using apt-get will allow you to easily manage upgrades in the future. Im not too sure which repository this came from (universe I think), but my gutsy box is now running "open-iscsi (from .../open-iscsi_2.0.865-1_i386.deb)"

All seems to be working well - although I havent done anything to stress it yet.

Another suggestion, I dont know the size of your EMC installation or what transactions you may have upcoming - one thing you can insist upon with your local SE is what EMC calls a RPQ. They absolutely HATE these things as its a ton of paperwork (i.e. if your a small shop dont expect the SE to do anything - if you have a 7 figure transaction on the table, the salesman will absolutely make the SE do his job). Essentially an RPQ is an exception that is documented by the lab as a supported deviation from the matrix. You might also want to verify that there isnt some level of support for open iSCSI already in there (if they are supporting Red Hat ans SUSE I would dig a bit on what they are driving iSCSI with.

Good luck

---

### Post by Widodh on 2007-10-30
Yes, i have been using iSCSI in Ubuntu since Feisty now, works great!

At the moment we use Gutsy on some servers for Xen 3.1 and Open-iSCSI 2.0

I haven't contacted EMC yet, but i will in the future.

---

