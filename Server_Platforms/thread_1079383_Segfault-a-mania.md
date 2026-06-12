---
title: "Segfault-a-mania"
date: 2009-02-24
forum: Server Platforms
---

### Post by TedHale on 2009-02-24
Ok, I have two four year old Rackable blades that I'm trying to install Ubuntu 8.04.1 LTS Server 64-bit from a USB CD-ROM. Here is the rough progression of what happens.

1. Install the OS with only openSSH.
2. Install slapd/ldap-utils/migrationtools
3. setup above #2, no problems
4. Install Samba/smbldap-tools/smbclient/samba-doc
5. setup slapd/samba for integration, no problems
6. setup smbldap-tools used to keep both systems insync
7. populate LDAP directory with it's skeletal entries and:

segmentation fault

Once this occurs, samba throws these errors on restart:
* Stopping Samba daemons


Signal 11 (SEGV) caught by ps (procps version 3.2.7).
Please send bug reports to <feedback@lists.sf.net> or <albert@users.sf.net>
start-stop-daemon: warning: failed to kill 4504: No such process


Signal 11 (SEGV) caught by ps (procps version 3.2.7).
Please send bug reports to <feedback@lists.sf.net> or <albert@users.sf.net>
   ...done.
 * Starting Samba daemons
   ...done.
 
and syslog contains this error:

Feb 23 12:35:36 cronus kernel: [  364.658901] smbldap-populat[4635]: segfault at 0 rip 7fca8f0c1d9b rsp 7fff97532be0 error 4

Today, I was curious and tried to upgrade the OS to 8.04.2 and it errored out with this in the syslog:

Feb 24 09:48:53 cronus kernel: [  442.055177] dpkg-preconfigu[4599]: segfault at 0 rip 7fd326cc3d9b rsp 7fff2f135580 error 4
Feb 24 09:49:02 cronus kernel: [  451.437885] frontend[4752]: segfault at 0 rip 7fac1e098d9b rsp 7fff26508890 error 4

And for the hell of it, I tried to run populate three more times to see how the rip and rsp numbers were related:

Feb 24 09:53:02 cronus kernel: [  691.128143] smbldap-populat[4812]: segfault at 0 rip 7f800c13dd9b rsp 7fff145acc70 error 4
Feb 24 09:58:32 cronus kernel: [ 1019.857498] smbldap-populat[4830]: segfault at 0 rip 7f2ae080ad9b rsp 7fffe8c7a330 error 4
Feb 24 10:00:53 cronus kernel: [ 1160.739888] smbldap-populat[4833]: segfault at 0 rip 7ff15fb0bd9b rsp 7fff67f7d630 error 4

My first inclination is that it's a memory problem. Running memtest86+ through 7 passes have produced no errors. Also, this same problem appearing on both servers would be an argument against memory issues.

I'm wondering could there be a kernel driver/version issue perhaps? Can anyone break down what these errors mean on a fundamental level (rip/rsp/error4)?

Any help would be greatly appreciated. Thanks.

T

I have a third machine identical to the above two that after a clean install will segfault with an error6 when running anything that uses Tar.

---

### Post by freerkkalsbeek on 2009-02-24
Have you tried using the 32-bit versions?

I'd only use 64bit if there is very a good reason for it.

Freerk

---

### Post by TedHale on 2009-02-25
I haven't actually. That's been suggested, but to be honest, if it's a kernel issue, I'll change OS's before limiting the full usage of the hardware. Also these are production boxes and require the ability to run packages like Java64-bit server, etc so my hands are tied on that front.

I did find out a few other interesting things. So even after a clean install (again), it occurs now that there is a chance to get the broken tar package (as briefly described above - that throws segfault error 6). After doing a e2fsck on my raid device it found some non-contiguous blocks and after rebooting from that, tar worked.. but then later something else failed. From that it's starting to point towards a harddrive issue. My next plan is to zero out all of my HDs between the three servers (which were setup with RAID1 on install) and do one of them normally with RAID1 as my control, one with just partitions and another using LVM and see if it has something to do with the RAID configuration and this particular hardware setup or lingering HD detritus.

I'll post an update this afternoon.

---

### Post by TedHale on 2009-02-25
Well unfortunately, that didn't work. 

Does anyone have a good resource that can lend some insight as to what the error elements mean???

Segfault at 0  0 what?

rip/rsp ??  

error 4 ?

---

