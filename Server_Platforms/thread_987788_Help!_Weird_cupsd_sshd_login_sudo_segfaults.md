---
title: "Help! Weird cupsd sshd login sudo segfaults"
date: 2008-11-19
forum: Server Platforms
---

### Post by evolutionx on 2008-11-19
Hi everyone,

I recently installed Ubuntu Server 8.10 and have configured it with LAMP, SSH, CUPS and SAMBA.

Everything has been running fine up until today where I have lost the ability to login to the machine either remotely or at the machine itself even after a reboot.

Before rebooting it I grabbed the output from dmesg via a ssh session that was still open on another machine.  No sudo commands would work and logging in at the machine itself would just redisplay the login prompt.

Trying to open a new ssh session to the machine would prompt you for your details then show that the machine had closed the connection.

Here is the dmesg output.  Has anyone else encountered this?

```
[74541.075306] type=1503 audit(1227149670.372:6): operation="inode_permission" requested_mask="rw::" denied_mask="rw::" fsuid=0 name="/var/lib/samba/group_mapping.ldb" pid=4536 profile="/usr/sbin/cupsd"
[74541.080080] type=1503 audit(1227149670.382:7): operation="inode_permission" requested_mask="rw::" denied_mask="rw::" fsuid=0 name="/var/lib/samba/group_mapping.ldb" pid=4536 profile="/usr/sbin/cupsd"
[74550.926825] type=1503 audit(1227149680.222:8): operation="inode_permission" requested_mask="rw::" denied_mask="rw::" fsuid=0 name="/var/lib/samba/group_mapping.ldb" pid=4536 profile="/usr/sbin/cupsd"
[74550.939972] type=1503 audit(1227149680.232:9): operation="inode_permission" requested_mask="rw::" denied_mask="rw::" fsuid=0 name="/var/lib/samba/group_mapping.ldb" pid=4536 profile="/usr/sbin/cupsd"
[74553.537775] type=1503 audit(1227149682.840:10): operation="inode_permission" requested_mask="x::" denied_mask="x::" fsuid=0 name="/usr/share/samba/panic-action" pid=9854 profile="/usr/sbin/cupsd"
[74553.572975] cupsd[4536]: segfault at 0 ip b7079abb sp bff6c5a0 error 4 in pam_smbpass.so[b701d000+12a000]
[74748.747900] sshd[10231]: segfault at 0 ip b7889abb sp bffe64f0 error 4 in pam_smbpass.so[b782d000+12a000]
[74766.293556] sshd[10317]: segfault at 0 ip b77deabb sp bfc3b150 error 4 in pam_smbpass.so[b7782000+12a000]
[74811.520132] sshd[10361]: segfault at 0 ip b7868abb sp bfec6bd0 error 4 in pam_smbpass.so[b780c000+12a000]
[74828.318587] login[26776]: segfault at 0 ip b7c58abb sp bfe58770 error 4 in pam_smbpass.so[b7bfc000+12a000]
[74847.315675] login[10455]: segfault at 0 ip b7cc8abb sp bfcc6de0 error 4 in pam_smbpass.so[b7c6c000+12a000]
[74864.392785] login[10479]: segfault at 0 ip b7c5eabb sp bfa5eb80 error 4 in pam_smbpass.so[b7c02000+12a000]
[75102.607384] sudo[11095]: segfault at 0 ip b7d72abb sp bf9816d0 error 4 in pam_smbpass.so[b7d16000+12a000]
[75140.509963] sudo[11204]: segfault at 0 ip b7c0fabb sp bfc20170 error 4 in pam_smbpass.so[b7bb3000+12a000]
[75166.670099] sudo[11233]: segfault at 0 ip b7d05abb sp bf815d60 error 4 in pam_smbpass.so[b7ca9000+12a000]
[75203.610623] sudo[11348]: segfault at 0 ip b7d47abb sp bfa567a0 error 4 in pam_smbpass.so[b7ceb000+12a000]
[75298.191437] sudo[11599]: segfault at 0 ip b7dcfabb sp bfde0b40 error 4 in pam_smbpass.so[b7d73000+12a000]
[75309.912374] sudo[11614]: segfault at 0 ip b7c3aabb sp bf84ada0 error 4 in pam_smbpass.so[b7bde000+12a000]
[75315.274615] sudo[11622]: segfault at 0 ip b7db7abb sp bf9c7f30 error 4 in pam_smbpass.so[b7d5b000+12a000]
[75348.251185] sudo[11656]: segfault at 0 ip b7cfcabb sp bfa0cf70 error 4 in pam_smbpass.so[b7ca0000+12a000]

```

The only things that I have changed recently is uncommenting the load printer settings in smb.conf to allow my Windows machines to print to the CUPS server.

Cheers,

---

### Post by igor.zem on 2008-11-22
Hi,

I had the same problem. Mine was solved by applying the actions suggested on

[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/278617](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/278617)

My problem arrised most probably after installing update of libpam-smbpass from 2:3.2.3-1ubuntu3.1 version from 2:3.2.3-1ubuntu3.

Hope the link helps you.

Best regards

Igor

---

### Post by loopyzort on 2009-02-20
hello,
i just encountered the same exact problems, followed the advice on the thread to comment out my 2 pam files and now i can re-connect to the server. however, samba is no longer working and cups still doesn't work (never did get it set up correctly). it seems commenting out those pam files was a workaround to some bigger bug, no? do you have any idea on how to get my 8.10 samba & cups servers up & working and not crashing each other out? the thread link doesn't really have a solution, just a workaround.

thanks

---

### Post by valery_la99 on 2009-05-06
I found that I was experiencing this bug:

[https://lists.ubuntu.com/archives/ubuntu-server-bugs/2008-November/007839.html](https://lists.ubuntu.com/archives/ubuntu-server-bugs/2008-November/007839.html)

So I removed /var/lib/samba/secrets.tdb and problems went away.

---

