---
title: "ubuntu 6.06 +esx3.5 sd errors"
date: 2009-07-30
forum: Server Platforms
---

### Post by jwilke on 2009-07-30
Hi people,

I am running a Zimbra mailserver in a VM (esx 3.5) on ubuntu 6.06 and I think I am running into the problem described here :

[http://www.novell.com/support/search.do?cmd=displayKC&docType=kc&externalId=7000715&sliceId=1&docTypeID=DT_TID_1_1&dialogID=45588563&stateId=0%200%2075165918](http://www.novell.com/support/search.do?cmd=displayKC&docType=kc&externalId=7000715&sliceId=1&docTypeID=DT_TID_1_1&dialogID=45588563&stateId=0%200%2075165918)

one of my virtual scsi disks that holds a mail store occasionally reports :

Jul 30 00:53:23 zimbra kernel: [59450619.090000] sd 0:0:1:0: SCSI error: return code = 0x20008
Jul 30 00:53:23 zimbra kernel: [59450619.090000] end_request: I/O error, dev sdb, sector 79291311

and the filesystem gets remounted ro 

This typically always happens late at night while running incremental or full backups.

I haven't been able to find anything in vmware logs indicating that there is a problem with my SAN hardware, so I my guess is that this is caused by the bug mentioned above.

Can someone confirm that this problem is still present in ubuntu 6.06, or if it was fixed, which kernel version I should be using ?

also found this reference

[http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commitdiff;h=ad8c31bb69d60c0c6bc6431bccdf67e5a96c0d31;hp=b364fd5081b02fa8a966a29eea2da628913fd4b8which](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commitdiff;h=ad8c31bb69d60c0c6bc6431bccdf67e5a96c0d31;hp=b364fd5081b02fa8a966a29eea2da628913fd4b8which)


Thanks in advance !

Jeroen

---

### Post by Musashi-san on 2009-09-10
Same problem here with ubuntu 6.06 used as SVN server + ESX 3.5

have you found any solution ?

Thanks in advance.

---

