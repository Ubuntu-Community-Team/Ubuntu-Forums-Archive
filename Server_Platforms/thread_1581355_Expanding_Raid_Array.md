---
title: "Expanding Raid Array?"
date: 2010-09-24
forum: Server Platforms
---

### Post by janascii on 2010-09-24
I'm planning out my new server and was wanting to know if it were possible to add/expand a raid array.  I was planning on eventually getting a raid 5 setup across a few drives, but would rather not buy several 2tb hard drives at once.  Is it possible to make an independent partition into a raid 1 and then into a raid 5 as I add more drives?  I know its possible to expand a raid 5/6 once it is running, but I've not seen any documentation on the other portion.  Thanks for any insight.

---

### Post by CharlesA on 2010-09-24
I'm not sure if it's possible to do what you are suggesting using RAID. You can do something like RAID-0 then throw that into a RAID5 array, but that uses more disks and is more cumbersome then just doing a regular RAID5 or RAID6.

When I did my RAID array, I just bought 3 2TB drives and threw them in a RAID5. That would probably be the best way to go about it.

I do know that HW RAID cards from 3Ware and Adaptec allow you to expand the array as needed.

Just as a reference, I'm using 3 of these [drives]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822145298") with this [controller card]("http://www.newegg.com/Product/Product.aspx?Item=N82E16816115053").

---

### Post by n1unqn on 2010-09-24
Agree, if you want an expandable raid then RAID 5 is the way to go.

Hard RAID is much better, you can get motherboards with it built in, also use RAID spec hard drives (I use Western Digital RE) they are designed for 24x7 on use. [http://www.wdc.com/en/products/Products.asp?DriveID=732](http://www.wdc.com/en/products/Products.asp?DriveID=732)

If you use RAID 5 you should also have Battery Backup or UPS as there are stories of RAID 5's messing up in power cuts.

---

### Post by janascii on 2010-09-25
The plan is to have an intel atom server board and run through software raid.  It'll just be a fileserver for the house mostly and will act as the backup partition for our other machines in the house.  

I've looked around some more and found this...
[URL="http://scott.wallace.sh/2007/04/14/converting-raid1-to-raid5-with-no-data-loss/"]http://scott.wallace.sh/2007/04/14/converting-raid1-to-raid5-with-no-data-loss/
[/URL]

Basically he started with a raid 1 array and ran out of space, so he redefined the array with level 5, but only 2 members.  Functionally it would still be a raid1 array, but would be using the raid5 algorithm... which could be expanded while maintaining data.  I'd assume that technique would still work.

---

### Post by ian dobson on 2010-09-25
Hi,

I have a mdadm RAID5 array, it started as a 3x2Tb array. About 2 months I added a 4th drive to the array, then grew the array to include the new drive then expanded the file system to use the extra space.

The whole process took about 14hours. Just make sure you have a good backup before you start.

Regards
Ian Dobson

---

