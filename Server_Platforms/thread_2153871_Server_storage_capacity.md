---
title: "Server storage capacity"
date: 2013-06-12
forum: Server Platforms
---

### Post by batmanrob on 2013-06-12
Hello I have 1 ubuntu server (10.04 lucid) where I installed ISPCONFIG3. Let's call it server**[COLOR=Orange] A[/COLOR]**

That server  "A"  has 20TB storage capacity that I got by a combination of RAID contoller and onboard ports.
The problem is that server "A" is running out of storage space. And I can't add external usb hard drives or additional hard drives.

I'm thinking of building another server "B"  with 20TB storage capacity.
Now the problem is how to configure server A to use the new 20TB space  available on server "B",  so I can have a total storage size of 40TB ?
I have users using server "A" and I don't want them to be affected by  the storage limitation issue since they are uploading files daily into  serve A.

Can I have somebody help me here ?

---

### Post by Bashing-om on 2013-06-12
[COLOR=#000000]batmanrob;
A consideration; How long until this additional 20T of storage is also consumed ?
Why not schedule the down time and convert to LVM (Logical Volume Management) ? Then is no problem at all in the future to add additional storage -on the fly-.

Else; one is looking at formatting, mounting, deciding on what "data" the new storage is to hold, copying, reconfiguring to point to the new partitions, testing, then removing the original data on the original storage. Only you can know what "data" moved would be the least intrusive to your users. Only you can know what reconfiguration will be needed to do this.
[/COLOR][INDENT=2][COLOR=#000000]
we can help in generalities..the specifics are on you

simply said, but is a huge task

[/COLOR][/INDENT]

---

### Post by ian dobson on 2013-06-12
Hi,

If you could add a Network Card to Server A then maybe try using a NAS with iSCSI, The storage space is mounted on Server A but it's actually attached to the Server through a Network rather than SATA/SAS.

Regards
Ian Dobson

---

### Post by papibe on 2013-06-13
> **ian dobson said:**
> ... add a Network Card to Server A then maybe try using a NAS with iSCSI,
+1

Create a [SAN]("http://en.wikipedia.org/wiki/Storage_area_network"), so server A can access B using a "private network connection".

If your users are uploading directly to the server, or using a samba share, you may also use NFS to mount B directories on A.

Note that either [iSCSI]("https://help.ubuntu.com/12.04/serverguide/iscsi-initiator.html") or [NFS]("https://help.ubuntu.com/12.04/serverguide/network-file-system.html") would be like having another partition, so it would give you access to the whole space but in 2 separate 20TB partitions. In order to agglomerate all space into one pool, take a look at  Bashing-om's suggestion (LVM).

Regards.

---

### Post by rubylaser on 2013-06-13
Another idea that would keep everything on server "A".  Do you have any PCIe ports left on the on board that you could use an external SFF-8088 cable to a SAS expander in a separate JBOD disk array in another chassis?  Then you could pool the existing storage with the new storage with something like mhddfs or AUFS to present a volume of 40TB total.

---

### Post by Bashing-om on 2013-06-13
[COLOR=#000000]@ rubylaser I do not see you very often ... your skill with servers and extended partitions continue to astound me !

Back in my formative association with the forum I saw a lot of you ... then nothing for a long while...then on occasion; 
It is always great to see you "pop up".
[/COLOR][INDENT=2][COLOR=#000000]
just my thought

[/COLOR][/INDENT]

---

### Post by grunge09 on 2013-06-13
Have you thought about a 16 bay, 20 bay or 24 bay rack mount server RAID case?  You can find used ones on ebay built out and ready to use, or buy a new case and build it yourself.  

that would solve your storage problem.  I have 2 at home now.  one is 15 bay with full of 250 gb drives, and a 24 bay box with 6 x 2tb drives and adding drives as needed. 

for example:

4U Server Case 20 HotSwap Drive Bays New Norco RPC-4020 $359.99 on ebay.

---

### Post by rubylaser on 2013-06-13
> **Bashing-om said:**
> [COLOR=#000000]@ rubylaser I do not see you very often ... your skill with servers and extended partitions continue to astound me !

Back in my formative association with the forum I saw a lot of you ... then nothing for a long while...then on occasion; 
It is always great to see you "pop up".
[/COLOR][INDENT=2][COLOR=#000000]
just my thought

[/COLOR][/INDENT]

Thanks for the vote of confidence :)  I used have a a lot more free time on my hands.  Lately, life and work have had me very busy, so I find very little time to get onto the forums.  I do need to make an effort to lurk around here more.

---

### Post by batmanrob on 2013-06-16
Hello Rubylaser, I tried to materialized your advice by the attached picture. So the SFF-8088 cable will link the two servers.. From there I can use mhddfs as explained in this post (  [http://romanrm.ru/en/mhddfs](http://romanrm.ru/en/mhddfs) )...
Another  solution I come across is Glusterfs for high availability storage.. But I'm not quite sure if Glusterfs will automatically increase the storage capacity of server A by adding the storage space available in server B. That way if server A is full, Glusterfs will send the load to the server with available space...

---

### Post by batmanrob on 2013-06-16
Hello Papibe, thanks for your reply

---

### Post by rubylaser on 2013-06-16
> **batmanrob said:**
> Hello Rubylaser, I tried to materialized your advice by the attached picture. So the SFF-8088 cable will link the two servers.. From there I can use mhddfs as explained in this post (  [http://romanrm.ru/en/mhddfs](http://romanrm.ru/en/mhddfs) )...
Another  solution I come across is Glusterfs for high availability storage.. But I'm not quite sure if Glusterfs will automatically increase the storage capacity of server A by adding the storage space available in server B. That way if server A is full, Glusterfs will send the load to the server with available space...

Yes, this is what I was talking about.  This would allow you to expand your storage by pooling it.  AUFS provides the same concept and runs in kernel space, so it is faster than the FUSE based mhddfs.  Ceph or Gluster will likely be a bit of overkill at this point :)

---

