---
title: "iSCSI Connecting to a Windows server"
date: 2011-02-07
forum: Server Platforms
---

### Post by CheezItMan on 2011-02-07
I'm trying to setup a new Ubuntu Server via terminal to host a variety of websites.  I need quite a bit of space, so our Windows System admin set me up with an iSCSI connection to a drive array, however I'm a little unsure how to translate that and get the is open-iscsi service connecting to it.

The settings he sent me include: 

DNS Domain Name
two IP Addresses for it

A Name for the service: pd2_video
An IQN:  

He enabled CHAP with a username and password.

Where do I need to look to see documentation on how to connect to this service?

I have tried following:  [http://www.qnap.com/pro_features_iSCSI_Ubuntu.asp](http://www.qnap.com/pro_features_iSCSI_Ubuntu.asp)

However I get:

iscsiadm: connection to discovery address x.x.x.x failed

I just can't see why.

---

### Post by CheezItMan on 2011-02-07
Solved - My windows administrator hadn't setup the allowed IP Addresses correctly.

---

