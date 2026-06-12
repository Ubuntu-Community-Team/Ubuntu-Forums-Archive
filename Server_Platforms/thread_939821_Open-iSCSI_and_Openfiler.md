---
title: "Open-iSCSI and Openfiler"
date: 2008-10-06
forum: Server Platforms
---

### Post by Cadmus on 2008-10-06
Hello all, I'm trying to build a simple iSCSI system with a target made in Openfiler,  and Ubuntu 8.04 as an initiator. Both are virtual machines so I can try things and roll them back. Here's what I've managed so far.

[LIST]
[*]Installed Openfiler
[*]Created a partition on the target
[*]Made that partition an iSCSI target
[*]Created a network ACL so only my initiator can access the target
[/LIST]

And I've hit a bit of a brick wall, I've been googling on it for a couple of hours now and I can't seem to find a way forward. I know I have to use iscsiadm to discover the target, and then log in to it so I can use it on the initiator as a drive.

I've tried following a couple of guides that just tell you to do
```
iscsiadmin -m discovery -t st -p 192.168.0.2
```
and if you follow that with
```
iscsiadmin -m node
```

It will give you the list, but that just return 'no targets found'. Would I be right in guessing I did something wrong at the discovery stage? Can someone help me with settings I may have wrong on my target?

---

### Post by Cadmus on 2008-10-07
I don't like bumping, but I'm just stumped.

---

### Post by kiklhorn on 2008-10-13
I'm start testing iSCSI today (openfiler as target and MS iscsi initiator on Windows and open-iscsi on Ubuntu)

You may try this:
```
iscsiadm -m discovery -t sendtargets -p myiscsiportalIP
iscsiadm -m node -p myiscsiportalIP -T iqn.mytargetfullpathDiscoveredInPreviousCommand -l
fdisk -l
```
You can see full tutorial at [http://www.mjohnsullivan.com/node/66](http://www.mjohnsullivan.com/node/66)

I don't know how to make permanent connection yet(after restart service iSCSI discs disapears)
maybe any config file somewhere in /etc/iscsi/ or any iscsiadm option

---

### Post by Cadmus on 2008-10-14
Ah, thanks, I'm not getting anything at the discovery stage, so I'll check how Openfiler does authentication.

---

### Post by fuelrod on 2009-04-14
Im not sure how to do this in general but you can do it on a connection by connection basis.

Just edit the file /etc/iscsi/nodes/{TARGET}/{IP/HOSTNAME},{PORT},{ID}/default and change node.startup to automatic

---

