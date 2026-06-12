---
title: "raid sata drives not detected during installation"
date: 2012-07-24
forum: Server Platforms
---

### Post by avanindra on 2012-07-24
Hi Folks,

I am trying to install ubuntu server of 12.04 on a system with configuration intel xeon processor and s1200bts motherboard , which has support for raid creation. So I created raid array of two 1 TB drives using intel's server deployment cd.

After that I am trying to install ubuntu server 12.04 , once I reach to partion disk menu during installation , the hard drives present in my system are not shown. Only the following entries are shown:

Configure iSCSI volumes

Undo changes to partitions
Finish partitioning and write changes to disk

If I understand correctly here the partition guiding entries should be shown. What am I doing wrong here?

Can anyone please guide me.


Thanks and many regards

Avanindra Singh

---

### Post by sandyd on 2012-07-24
> **avanindra said:**
> Hi Folks,

I am trying to install ubuntu server of 12.04 on a system with configuration intel xeon processor and s1200bts motherboard , which has support for raid creation. So I created raid array of two 1 TB drives using intel's server deployment cd.

After that I am trying to install ubuntu server 12.04 , once I reach to partion disk menu during installation , the hard drives present in my system are not shown. Only the following entries are shown:

Configure iSCSI volumes

Undo changes to partitions
Finish partitioning and write changes to disk

If I understand correctly here the partition guiding entries should be shown. What am I doing wrong here?

Can anyone please guide me.


Thanks and many regards

Avanindra Singh
what raid controller model is it?

---

### Post by darkod on 2012-07-24
Unless the server has a hardware raid controller, you are probably better using the linux software raid function instead of the board built-in fakeraid.

In that case you don't create the array in advance, you configure the software raid during the manual partitioning.

If there is a hardware controller, you need to investigate if the model is supported by ubuntu server or you need additional drivers.

Also, did you try selecting the Configure iSCSI option to see if that activates the raid array?

---

### Post by a2j on 2012-07-24
> **darkod said:**
> Unless the server has a hardware raid controller, you are probably better using the linux software raid function instead of the board built-in fakeraid.

In that case you don't create the array in advance, you configure the software raid during the manual partitioning.

If there is a hardware controller, you need to investigate if the model is supported by ubuntu server or you need additional drivers.

Also, did you try selecting the Configure iSCSI option to see if that activates the raid array?

And I'll just add that in some cases Linux software raid would be better than hardware raid controller.

---

