---
title: "Headless Ubuntu 12.04"
date: 2013-04-19
forum: Server Platforms
---

### Post by brent1975 on 2013-04-19
Hello, I have a 12.04 server running perfectly. I primarily use the server for storage of media and personal apps/docs that I don't want to store on the local computer/laptops. When I first got the server running I had plenty of space for files with out any issue. But over time all my media pictures, music , movies etc has taken up drive space and now I am faced with either deleting some of the content or upgrading the drive. The current drive is a 200 gig. I am wanting to throw in a 2 or 3 tb drive. So here is the question.

I was looking around at different methods of imaging my server and came across clonezilla. If I upgraded my drive and slapped that image on the new drive will that work? Or will there be problems with disk partitions. such as seeing the entire drive? I have spent alot of time getting this server configured to my needs. if it would be better to just install a fresh install that is fine and have no problem doing so. Just wanted to eliminate some of the down time.


Thank you in advance.

-Brent

---

### Post by tgalati4 on 2013-04-19
Generally it is better to do a clean install.  Make notes of your configuration changes.  Make a list of installed packages--there are tutorials on this.  

If you do clone the drive, you will need to use *blkid* to get the UUID of the new drive and make changes to grub and /etc/fstab and probably elsewhere where your old drive's UUID will need to be substituted for the new drive's UUID.  It's technical and you need to know what you are doing, otherwise you will spend a lot of time fixing things.

---

### Post by CharlesA on 2013-04-20
> **tgalati4 said:**
> Generally it is better to do a clean install.  Make notes of your configuration changes.  Make a list of installed packages--there are tutorials on this.  

I would agree with this. The last time I moved my server to new hardware, I reinstalled from scratch and used a script i wrote during the initial testing/deployment to get the configuration and stuff identical to the current server.

> If you do clone the drive, you will need to use *blkid* to get the UUID of the new drive and make changes to grub and /etc/fstab and probably elsewhere where your old drive's UUID will need to be substituted for the new drive's UUID.  It's technical and you need to know what you are doing, otherwise you will spend a lot of time fixing things.

It has been my experience with Clonezilla that it doesn't change the UUID of the partition. Maybe that has changed, but your advice about checking fstab is a good idea too. :)

---

### Post by papibe on 2013-04-20
Hi  brent1975.

I share  tgalati4 and CharlesA's assessments. 

However I want to add my thoughts about a couple of things.

**MBR -> GPT**
If you go with a 3TB disk, you have to rethink your strategy. Since your current drive is 200GB, it probably has a MBR table partition (or MSDOS partition). This kind of partition table supports up to 2GB, so you wouldn't be able to access the remaining 1GB.

In order to take advantage of the whole 3TB you would need to create a GPT partition table.

Then in this case, cloning the whole disk would not look like a good idea. The closest thing would be to clone or copy your partitions separately,  and then paste them into the new disk (already formated with GPT). I haven't done this myself.

**Different approach**
You don't have to get rid of the old one, and install the new one. You can keep both.

Keep your disk where it is, and add the new disk. Then you can format it and mount it wherever you want into your file structure. Move your files around and that's it.

For this to work, your motherboard needs to have to SATA ports available, though.

Let us know how it goes.
Regards.

---

