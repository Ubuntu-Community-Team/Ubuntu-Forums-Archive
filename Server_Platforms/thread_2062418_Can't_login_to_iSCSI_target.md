---
title: "Can't login to iSCSI target"
date: 2012-09-24
forum: Server Platforms
---

### Post by zee on 2012-09-24
Hi.
  To speed-up transfers between a iSCSI target (Synology DS1511+) and a workstation (HP Z800) I purchased an Intel ethernet card. The NAS and computer are directly connected.

  The problem is that now I can't login to the NAS anymore. I used this [guide]("http://www.howtoforge.com/using-iscsi-on-ubuntu-10.04-initiator-and-target") in the past to configure the iSCSI initiator.

  Step 1: iscsiadm -m discovery -t st -p 192.168.1.2
```
root@erwin:~# iscsiadm -m discovery -t sendtargets -p 192.168.1.2
192.168.1.101:3260,0 iqn.2000-01.com.synology:syn-data
192.168.1.2:3260,0 iqn.2000-01.com.synology:syn-data
```

  Step 2: iscsiadm -m node
```
root@erwin:~# iscsiadm -m node
192.168.1.101:3260,0 iqn.2000-01.com.synology:syn-data
192.168.1.2:3260,0 iqn.2000-01.com.synology:syn-data

```

  Step 3: do the login
```
root@erwin:~# iscsiadm --mode node --targetname iqn.2000-01.com.synology:syn-data --portal 192.168.1.2:3260 --login
Logging in to [iface: iscsi-1, target: iqn.2000-01.com.synology:syn-data, portal: 192.168.1.2,3260]
iscsiadm: Could not login to [iface: iscsi-1, target: iqn.2000-01.com.synology:syn-data, portal: 192.168.1.2,3260]: 
iscsiadm: initiator reported error (19 - encountered non-retryable iSCSI login failure)
```

  What happened? I tried to fix the problem by removing the contents of /etc/iscsi/ifaces/ and /etc/iscsi/nodes/ but it didn't help.
  I have no authentication set on the iSCSI target.

  I'm using Ubuntu 12.04 LTS, 64-bit.

  The solution was to disable: Header Digest and Data Digest on the target.

Thanks for any advice,
zee

---

### Post by JDubois450 on 2013-01-28
Hi,

I'm having the same problem....
Even with the doc from version 12.04
[https://help.ubuntu.com/12.04/serverguide/iscsi-initiator.html](https://help.ubuntu.com/12.04/serverguide/iscsi-initiator.html)

And the NAS is working properly because I already done it from the past with an earlier Ubuntu version.

Without chap credential, it's OK and working fine.
I tried your solution : disable: Header Digest and Data Digest on the target
And nothing changed...   :-(

But I want to use chap and I want to do my login over the console.
I don't want to put user-name and password in the "/etc/iscsi/iscsid.conf"

Any tricks for this?

Thx

---

