---
title: "Newb: Please help with initial server setup (Bootable raid5)"
date: 2009-05-30
forum: Server Platforms
---

### Post by Smartin on 2009-05-30
Hi,

(Sorry this got a bit long...)

I consider myself a complete newb at anything to do with Linux (although I have managed to persuade one server to serve four sites, including a Wordpress install and a Drupal instal), I'm a Mac refuge.

I have bought a cheap server, an HP ML115 G5, and have deliberately bitten off more than I can chew so I can learn as I go. 

Unfortunately I have fallen badly at the first hurdle, although I did manage to get the server out of the box Ok ;-)
[B]
This is my ideal scenario:[/B]
I have taken the original drive out of the server and have fitted three 500GB drives in its place. I really want to create a *bootable* raid 5 setup and work entirely from that.

Having knocked myself out against this for several days now, I'm beginning to get the message that it's not possible to boot from (or even install on to) a raid 5 array.

Can anyone confirm this?

If it is possible to do, *please* could you point me to a simple step by step howto? I simply can't find anything *specifically* to do with a bootable raid 5 array.

**This is my second choice scenario:**
Assuming the above is impossible, I could fit the original 160GB drive back in the box. I could then install Ubuntu 8.04 LTS on there and all data on a raid 5 array created from the three 500GB drives.

How would I partition the 16ogb drive so that  everything other than the OS goes on to the raid array? The idea being that all really valuable data goes safely on the raid array and the replaceable OS goes on the single drive. I take on board the importance of backups etc...

Would the mount point for the Raid array be /var? Is 'var' where all data goes?

Please give me some pointers (and speak to me like I'm three years old please :-)?

The server has 1gb RAM at the moment but I intend to add 3GB to that. I guess this is important for the partitioning scheme...?

Thanks guys :-)

Simon

---

### Post by MJWitter on 2009-05-30
As far as i know the problem you are having is that the boot data needs to be seperate from the raid 5 array.  What might work in your situation is to create a 200mb partition, mirrored on each of the drives(raid 1) for /boot and use the rest of the drive space as raid 5 array. I had this set up for a little while..

As to what partitions to use for the install, here is a guide on the [linux filesystem]("http://www.freeos.com/articles/3102/").

I don't know of any guides on the subject, but if you need help along the way, just post here and I'm sure that either I or someone else will be able to help out!

---

### Post by Smartin on 2009-05-30
> **MJWitter said:**
> As far as i know the problem you are having is that the boot data needs to be seperate from the raid 5 array.  What might work in your situation is to create a 200mb partition, mirrored on each of the drives(raid 1) for /boot and use the rest of the drive space as raid 5 array. I had this set up for a little while..

As to what partitions to use for the install, here is a guide on the [linux filesystem]("http://www.freeos.com/articles/3102/").

I don't know of any guides on the subject, but if you need help along the way, just post here and I'm sure that either I or someone else will be able to help out!

MJ,

Thanks for your help :-)

What you say seems like a good idea.

Can I mirror the OS partition across all three drives in your example above?

Wouldn't it be easier to use the 160GB drive as the boot drive and store all the data on the raid array. Then keep the 160 GB well backed up on an external USB drive for instance?

Just need a bit of a kick-start... :-)

Edit: Skimming through the page you liked to makes me wonder what the *minimum* is I would have to put on the boot/160GB drive to create a bootable system and what else could be stored more safely on the raid array...?

Anyone?

Simon

---

### Post by MJWitter on 2009-05-30
Yes, you can mirror across all three drives.  
If you prefer to use the 160Gb disk, then you can do that and just have the web data, such as the /var partition, stored on the raid array.

Unfortunately my knowledge of web servers is extremely limited and as such don't want to give advise which may be incorrect in terms of the best partitioning layout.

---

### Post by Smartin on 2009-05-30
> **MJWitter said:**
> Yes, you can mirror across all three drives.  
If you prefer to use the 160Gb disk, then you can do that and just have the web data, such as the /var partition, stored on the raid array.

Unfortunately my knowledge of web servers is extremely limited and as such don't want to give advise which may be incorrect in terms of the best partitioning layout.

MJ,

With me being a newb it sounds simpler to just keep a minimal install on the 160GB and the rest on the raid array. Yes?

Any idea how *little* I could place on the 160?

Simon

---

### Post by MJWitter on 2009-05-30
The least you can install on the 160Gb drive is the /boot partition, which is about 200mb usually(alot of which won't be used)..  

Would you be happy to try something first, because I would hate for you to waste a 160Gb drive for 200MB of usage if not necessary..

This will install the whole thing on the 3 500GB drives, and not use raid for the boot at all.

Go thorugh the setup  and when you get to the partitioning stage, create a 200MB partition on each of the drives.  At use as, make the one ext3 and /boot partition. Make sure it says boot flag on(or something like that) for that one partition.  The other two can be left as don't use.

Now, create the raid 5 array on the rest of the disk, partitioning it how you want.

That should be able to boot, and have the extra partitions available so that you can mirror the boot partition in the future if you so wish.

---

### Post by Smartin on 2009-05-31
> **MJWitter said:**
> The least you can install on the 160Gb drive is the /boot partition, which is about 200mb usually(alot of which won't be used)..  

Would you be happy to try something first, because I would hate for you to waste a 160Gb drive for 200MB of usage if not necessary..

This will install the whole thing on the 3 500GB drives, and not use raid for the boot at all.

Go thorugh the setup  and when you get to the partitioning stage, create a 200MB partition on each of the drives.  At use as, make the one ext3 and /boot partition. Make sure it says boot flag on(or something like that) for that one partition.  The other two can be left as don't use.

Now, create the raid 5 array on the rest of the disk, partitioning it how you want.

That should be able to boot, and have the extra partitions available so that you can mirror the boot partition in the future if you so wish.

MJ,

Thanks again...

I always get asked about a swap partition, saying that if I don't allocate one things won't run efficiently. Where should the swap partition go and how big should it be if I have 4 or 8 GB ram?

Will all the other mount points need to be specifically allocated or will the installer do that automagically?

Do I have to allocate a certain amount of space to each of the other mount points? If so, how much to each?

Simon

---

### Post by MJWitter on 2009-05-31
With so much ram it is unlikely you will use swap, but perhaps allocate 4-8 GB just in case. The swap partition can go on the end of the raid 5 array.

You can allocate the rest of the array to root (/) as one partition and then everything will be kept there(/,/home,/var etc), or you can decide what to allocate to each section in a seperate partition.  

Maybe have a quick read on LVM and logical partitions before you continue. Normally, one can only have 3 primary partitions per disc, but LVM and logical partitions enable more.  

Is this server going to get lots of traffic? Be used by many people on the internet?  If so, perhaps you should do some  more research into web server setups.  If not, then it might be fine to just have 1 /boot partiton, 1 / (root) partition and 1 SWAP partition.

---

### Post by Smartin on 2009-05-31
> **MJWitter said:**
> With so much ram it is unlikely you will use swap, but perhaps allocate 4-8 GB just in case. The swap partition can go on the end of the raid 5 array.

You can allocate the rest of the array to root (/) as one partition and then everything will be kept there(/,/home,/var etc), or you can decide what to allocate to each section in a seperate partition.  

Maybe have a quick read on LVM and logical partitions before you continue. Normally, one can only have 3 primary partitions per disc, but LVM and logical partitions enable more.  

Is this server going to get lots of traffic? Be used by many people on the internet?  If so, perhaps you should do some  more research into web server setups.  If not, then it might be fine to just have 1 /boot partiton, 1 / (root) partition and 1 SWAP partition.

MJ,

I'm going to have a go at this tomorrow for sure. We are having 'Cape Town' weather here in the Uk so we are trying to make the most of it... :-)

The server will have low traffic only but I want to learn about all sorts of things so it will be multi-purpose, file server, mail etc etc.

Simon

---

### Post by Smartin on 2009-05-31
> **MJWitter said:**
> With so much ram it is unlikely you will use swap, but perhaps allocate 4-8 GB just in case. The swap partition can go on the end of the raid 5 array.

You can allocate the rest of the array to root (/) as one partition and then everything will be kept there(/,/home,/var etc), or you can decide what to allocate to each section in a seperate partition.  

Maybe have a quick read on LVM and logical partitions before you continue. Normally, one can only have 3 primary partitions per disc, but LVM and logical partitions enable more.  

Is this server going to get lots of traffic? Be used by many people on the internet?  If so, perhaps you should do some  more research into web server setups.  If not, then it might be fine to just have 1 /boot partiton, 1 / (root) partition and 1 SWAP partition.

MJ,

I couldn't keep away of course...

I got it working! :-)

I decided to use the 160gb disk to boot from so I just put a 300mb boot partition and a 10gb swap on it. I then created the raid array using the three 500gb disks and allocated the '/' mount point to it and crashed on with the installation.

I figured this was the easiest way and made the most of the raid array.

It seemed to work :-)

Now I need to figure out how to back up the boot partition... ;-)

Thanks for all your help :-)

Simon

---

### Post by Pnuts on 2009-05-31
Simon,

I have a similair setup with 3x320gb drives in a Raid 5 array.

Here is what I did:

At the partition page during the Jaunty Server installation, I choose manual.

I then delete all existing partitions off of my 3 drives (if any) -- [COLOR="Red"]**This destroys any data on the drives**[/COLOR]

On all 3 drives I create these 3 partitions:

100mb - Set to Raid volume (create this first, Primary partition at start of drives)
XX gb - Set to Raid volume (create last, use all remaining space, Primary or logical, doesnt matter)
YY gb - Set to Raid volume (Create 2nd, Logical partition at end of drives

For YY, I did this: (RAM times 2.5 which is usually recommended, and then divided by 3 since i have 3 drives)

YY = (RAM * 2.5) / 3

Once done, choose the configure raid choice at the top.

Create a RAID 1, tell it 3 drives when prompted and 0 spare. Choose the 3 100mb partitions. Probably sda1, sdb1, sdc1.

Create a RAID 0, choose the 3 swap partitions, probably sda5, sdb5, sdc5 if you followed my example above.

create a RAID 5, choose the last 3 partitions that remain.

finish the raid setup and return to the manual partition page. You should see the 3 raid arrays you made at the top of the list. Change the first on to ext3 and /boot. Change the 2nd to use as swap and change teh 3rd to ext3 and /

then finish at the bottom and continue the install. This will setup all data in a raid 5 array on the 3 drives and use them for the /boot and swap data.

Boot is Raid 1 because grub is able to boot a mirrored drive. Swap is raid 0 as it performs better then in raid 5 and there is no need for redundancy on a swap partition.

-Pnuts

---

### Post by MJWitter on 2009-05-31
Glad to see it has all worked out well!

Enjoy the weather, I hope it lasts!

---

### Post by Smartin on 2009-05-31
> **Pnuts said:**
> Simon,

I have a similair setup with 3x320gb drives in a Raid 5 array.

Here is what I did:

At the partition page during the Jaunty Server installation, I choose manual.

I then delete all existing partitions off of my 3 drives (if any) -- [COLOR="Red"]**This destroys any data on the drives**[/COLOR]

On all 3 drives I create these 3 partitions:

100mb - Set to Raid volume (create this first, Primary partition at start of drives)
XX gb - Set to Raid volume (create last, use all remaining space, Primary or logical, doesnt matter)
YY gb - Set to Raid volume (Create 2nd, Logical partition at end of drives

For YY, I did this: (RAM times 2.5 which is usually recommended, and then divided by 3 since i have 3 drives)

YY = (RAM * 2.5) / 3

Once done, choose the configure raid choice at the top.

Create a RAID 1, tell it 3 drives when prompted and 0 spare. Choose the 3 100mb partitions. Probably sda1, sdb1, sdc1.

Create a RAID 0, choose the 3 swap partitions, probably sda5, sdb5, sdc5 if you followed my example above.

create a RAID 5, choose the last 3 partitions that remain.

finish the raid setup and return to the manual partition page. You should see the 3 raid arrays you made at the top of the list. Change the first on to ext3 and /boot. Change the 2nd to use as swap and change teh 3rd to ext3 and /

then finish at the bottom and continue the install. This will setup all data in a raid 5 array on the 3 drives and use them for the /boot and swap data.

Boot is Raid 1 because grub is able to boot a mirrored drive. Swap is raid 0 as it performs better then in raid 5 and there is no need for redundancy on a swap partition.

-Pnuts
Pnuts,

Thanks for chipping in...

I'm a bit further along now :-)

Is the setup I implemented not a sensible one?

Simon

---

### Post by Smartin on 2009-05-31
> **MJWitter said:**
> Glad to see it has all worked out well!

Enjoy the weather, I hope it lasts!

MJ,

I guess I ought to get outside... have spent most of the day in a darkened room :-)

Simon

---

### Post by Pnuts on 2009-05-31
> **Smartin said:**
> Pnuts,

Thanks for chipping in...

I'm a bit further along now :-)

Is the setup I implemented not a sensible one?

Simon

Your set-up is fine. I didn't have a 4th drive. I also broke out the partitions a bit differently then I mentioned above. Seperate /var, /usr, /tmp, /var/log, /home, and 2 larger partitions under /var for other data I wanted on a separate partition.

-Pnuts

---

