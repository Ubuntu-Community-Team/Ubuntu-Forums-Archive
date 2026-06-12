---
title: "Ubuntu Server PDC &amp; Mythtv in one Box"
date: 2012-08-12
forum: Server Platforms
---

### Post by grunge09 on 2012-08-12
Can I have Ubuntu Server PDC & Mythtv (backend & frontend) in one Box

I have the 2 separate pc's to do this, but I would like to be able to combine them both in one computer.  

Basically my Mythtv install and data on the Ubuntu Server, and still be able to access data off file server all on same PC.  

mythTv Box 

AMD Quad Core 3.2GHz
2 GB Ram
2 TB Drive (about 50% full) (I just used DD clone drive and gparted to resize new drive)
Haupauge HVR-2250 TV Card
DVD ROM
2 3200 rpm case fans to keep temps down

Ubuntu 12.04 server box

AMD 3200+ CPU
4 GB RAM
2 x 2tb drives (RAID 1 via MADM)
Samba as PDC
CDR & DVD ROM Drives

I could use the existing Mythbox and all the 2 tb drives in a RAID 5 (plus a few more 2tb drives) with Ubuntu Server and MLADM.  Then install Xserver GIU,a, then isntall MythTV & Samba.  

My problem is this, IF a 2tb drive fails Other than a notification, I do not think I know ever know which one actually failed.  

I looked at a Drobo box, they have convenient lights when one fails.  Is there something similar, or something I can install in the case like those 3 bay data hot swap enclosres that fit into 2 5.25" drive bays?

Anyone got any ideas?

---

### Post by TheFu on 2012-08-12
You can monitor SMART data, but SMART tends to be nearly worthless.

You can monitor the software RAID. It will tell you exactly which device/partition isn't available.  There are many different ways to do this. **cat /proc/mdstat** is an easy way. You can easily write a script that runs every few minutes looking for a pattern ... perhaps "[4/4] [UUUU]"?

Logwatch will tell you about big things every day if you like.

Monitoring and alarming is a way of life when you run servers.

I can't see any reason why running those two major functions won't work on a single box. Whether is it a good idea or not is a completely different question that only you can answer for your specific situation.

Are you looking for some piece of hardware with green/red lights?  I don't think that exists for software RAID setups.  Getting those lights is why hardware RAID devices cost $20K. ;)

---

### Post by grunge09 on 2012-08-13
Are you looking for some piece of hardware with green/red lights?  I don't think that exists for software RAID setups.  Getting those lights is why hardware RAID devices cost $20K. 

I have a 26 Bay 4u Rackmount Raid NAS by supoer Micro, but its loud, heavy, and generates a lot of heat.  Did not want to use that.  That's why I was thinking of marrying it all in one box.  Or by using something like a Drobo where I could put like 5 2tb drives in raid 5.

---

### Post by TheFu on 2012-08-13
A drobo is pretty costly unless you have more money than time.  

I still don't really understand what you want.  It sounds like you want some LEDs that reflect the current status of the /proc/mdstat file, right?

Inside the mdstat there is a pattern "[4/4] [UUUU]".  That means all 4 drives in the array are working as expected.  So what you need is a physical device that displays all possible combinations of the pattern.  It has been years since I've seen what a failed slice looks like, but we can just look for a non "U" in those 4 places.

Now we need some sort of device to display that.  I'd think a USB LED controller or even a little scrolling LED message board would be easy to control. Actually, you only need a single LED, since any reported error could be enough to make it light up. Then you could look at the mdstat file yourself and take the necessary corrective steps.  Am I making sense?
 I would be surprised if a USB-LED controller was more than $10.  While you are at it, why not have the error condition send your smartphone an email or SMS with the error condition?

Am I understanding what you seek correctly?

---

