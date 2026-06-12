---
title: "Need some help figuring out my RAID configuration"
date: 2010-07-30
forum: Server Platforms
---

### Post by Magnesium on 2010-07-30
Hi folks, lots of questions here but I really appreciate any help,

I've inherited a Dell PowerEdge 600SC server. It's got a 15,000 RPM SCSI drive that I want to install Ubuntu on, and 4 250GB SATA drives connected to a Promise FastTrak S150 SX4 SATA/RAID card, that I want to set up in RAID 5 for storage.

[Here's a link to the card's user manual]("http://firstweb.promise.com/upload/Support/Manual/FastTrak%20S150%20SX4%20SX4000%20UM%20v3.8.pdf").

OK, so when I boot with this card I can set up the array to use all drives in RAID 5. It says the array is active. Then when I look at it in Linux I see 4 separate drives. :confused: Is this a FakeRAID controller? The fact that I'm seeing separate drives, and that there are driver downloads on Promise's website, would imply that it is FakeRAID, right? But the user manual says that the card has a built-in XOR accelerator, which would imply real RAID! :S (Plus the card is huge and has it's own DIMM stick.)

Any opinions?

And assuming that it's FakeRAID, I am slightly confused as to the best way to set it up. As I understand it I can use LVM or dmraid for the purpose...which is better? And will one use the hardware on the card better? Final question....there are drivers for download on the Promise website, but they're for Red Hat and SUSE only. Should I try to use those drivers? Or are Ubuntu's built-in ones going to be enough?

Thanks for any help you can give me. Even general comments about RAID and Linux will help, because I am a little foggy on the whole situation.

Mg

---

### Post by cj.surrusco on 2010-07-30
If it is being recognized as seperate disks in Ubuntu, then it is not set up correctly, or is in fact, fakeraid. True hardware RAID is completely transparent to any operating system. So, it might mean that you have something between true and fake raid. Maybe it just fakeraid with some kind of hardware to accelerate it... not completely sure.

But if it is fakeraid, I would recommend not using it and instead using [Linux software RAID]("https://help.ubuntu.com/community/Installation/SoftwareRAID"). I mean you could try setting up the fakeraid, but since some drivers aren't made for Linux, it may be difficult. I wasn't able to set up fakeraid at all, myself. Maybe that's just me though. 

Software RAID isn't that much different from fakeraid, there is some info on it in the link I attached.

---

### Post by Magnesium on 2010-07-30
Ah, thank you for that link! I didn't realize there were 3 types...I guess mentally I had always clumped (Fully) Software RAID together with FakeRAID, but it looks like there is in fact a little difference.

So to make Fully Software RAID, one would use LVM? Or dmraid? Or are they the same? Also, if I use Sofware RAID, would it take advantage of my controller card at all? (That special XOR processor). See, there are drivers for this controller for Linux written by the manufacturer...but they are for RHEL and SUSE.

Maybe the most important question is, am I making too big of a deal out of trying to use my card? This is going to act as a LAMP/LDAP/FTP server...not a whole lot of processor activity going on, leaving plenty for any calculations needed for RAID. What's the real-world performance difference between a FakeRAID and Software RAID setup?

Thanks again for helping.

---

### Post by cj.surrusco on 2010-07-31
> **Magnesium said:**
> Ah, thank you for that link! I didn't realize there were 3 types...I guess mentally I had always clumped (Fully) Software RAID together with FakeRAID, but it looks like there is in fact a little difference.

So to make Fully Software RAID, one would use LVM? Or dmraid? Or are they the same? Also, if I use Sofware RAID, would it take advantage of my controller card at all? (That special XOR processor). See, there are drivers for this controller for Linux written by the manufacturer...but they are for RHEL and SUSE.

Maybe the most important question is, am I making too big of a deal out of trying to use my card? This is going to act as a LAMP/LDAP/FTP server...not a whole lot of processor activity going on, leaving plenty for any calculations needed for RAID. What's the real-world performance difference between a FakeRAID and Software RAID setup?

Thanks again for helping.

You would actually want to use [mdadm]("http://www.linuxmanpages.com/man8/mdadm.8.php"). It will manage the software RAID for you. 

AS far as not using the card, I wouldn't totally worry about it. You may have *slightly* better performance with it (if you are able to get it configured), but for the most part it would be about equal to software RAID. Also, since you will have that extra processing power, there will be even less of a difference. 

I too, did the same thing, I paid extra for a motherboard with fakeraid, and ended up using software RAID. Did you pay a lot for that card? I would feel bad about wasting that money, but it least it is being used as a sata controller if you do decide to use software RAID ;)

---

### Post by Magnesium on 2010-07-31
Thanks for the correction...mdadm sounds like my new best friend. (Is the fact it is a palindrome important, I wonder? :P )

Well I'm glad to know that the card wouldn't really help me much...doing full software RAID sounds *sooo* much easier than hacking RHEL or SUSE drivers from 5 years ago to work in Ubuntu Server 10.04  ](*,)  I'll just let my little processor get some XORing practice.......

I was given this server (PowerEdge 600SC) because it wasn't being used anymore. So I didn't pay anything for the box ;) But it isn't mine, I am setting it up for my department at school.

You've been very helpful CJ...2 more questions please? First, nothing is different if I want to add this array after installation, right? I just run the mdadm command once I've got Ubuntu installed on its own drive. (I was going to instal Ubuntu on a 15,000 rpm SCSI drive and use the RAID array for storage.) Second, I know there are many ways, but how do you have your system set up to alert you if a drive fails?

Thanks for your help.

Mg

---

### Post by cj.surrusco on 2010-07-31
You can create the RAID array either during or after the install. I actually prefer to create it during the install. It is easier to do then. Just create the RAID device and choose that it not be mounted (or set the mount point then, if you wish). I think it is pretty easy to figure out once you are there.

As far as alerting me when a drive fails, I honestly have no system. I do have a server that is on all of the time, but there is no RAID, since it was more of a project on an old desktop than an actual server. The software RAID is on my desktop, so I would be notified during boot if it was running in degraded mode (without all drives). 

You can set up e-mail notifications with mdadm by adding "MAILADDR root" (without quotes) to your /etc/mdadm.conf. You would obviously have to have an email address tied to you root account, I'm not sure how to set that up though...

---

### Post by jacekk015 on 2010-07-31
In Ubuntu 10.04 the config file is on /etc/mdadm/mdadm.conf

---

### Post by Magnesium on 2010-07-31
> **cj.surrusco said:**
> You can create the RAID array either during or after the install. I actually prefer to create it during the install. It is easier to do then. Just create the RAID device and choose that it not be mounted (or set the mount point then, if you wish). I think it is pretty easy to figure out once you are there.

As far as alerting me when a drive fails, I honestly have no system. I do have a server that is on all of the time, but there is no RAID, since it was more of a project on an old desktop than an actual server. The software RAID is on my desktop, so I would be notified during boot if it was running in degraded mode (without all drives). 

You can set up e-mail notifications with mdadm by adding "MAILADDR root" (without quotes) to your /etc/mdadm.conf. You would obviously have to have an email address tied to you root account, I'm not sure how to set that up though...

Ah, I didn't realize that I could set up the RAID array without specifying a part of the filesystem to be mounted on it (like /var or /home or something). Since I can't do the install until my new SCSI drive arrives I guess I will just set it up all at install. Should I pick to use LVM or no? Is LVM required to use mdadm?

And it looks like I can say an address directly instead of saying root: [http://www.novell.com/support/search.do?cmd=displayKC&sliceId=SAL_Public&externalId=7001034](http://www.novell.com/support/search.do?cmd=displayKC&sliceId=SAL_Public&externalId=7001034)

> **jacekk015 said:**
> In Ubuntu 10.04 the config file is on /etc/mdadm/mdadm.conf

Thanks for the correction....

---

### Post by Magnesium on 2010-08-02
No opinion on using LVM or not?

---

### Post by jacekk015 on 2010-08-02
Read some about LVM first.

mdadm is a software RAID
LVM - logical volume manager
They aren't needed together.

LVM can be used on top of devices or RAID arrays to connect, and maybe later resize, volumes space. Flexibility, but also more difficult to manage.

For example you have:
One RAID5 500GB, second RAID0 500GB and third RAID1 500GB - total 1,5TB
You can connect all this space with one volume group and then distribute only needed space to logical volume.
You create 100GB logical volume for pictures, mount it, and rest of space remains for future use.

It looks very OK, but believe me - it's not easy. Complexity is always our enemy when disaster happens.
Test it on virtual machine first.

---

### Post by Magnesium on 2010-08-02
> **jacekk015 said:**
> Read some about LVM first.

mdadm is a software RAID
LVM - logical volume manager
They aren't needed together.

LVM can be used on top of devices or RAID arrays to connect, and maybe later resize, volumes space. Flexibility, but also more difficult to manage.

For example you have:
One RAID5 500GB, second RAID0 500GB and third RAID1 500GB - total 1,5TB
You can connect all this space with one volume group and then distribute only needed space to logical volume.
You create 100GB logical volume for pictures, mount it, and rest of space remains for future use.

It looks very OK, but believe me - it's not easy. Complexity is always our enemy when disaster happens.
Test it on virtual machine first.

Thank you so much...I did read about LVM but was always confused....because both LVM and RAID use multiple disks to make 1 volume. Just in very different ways.

Looks like I will use Software RAID 10 and no LVM for the server. Thanks everyone for your help in this, and getting me straightened out! This is why I love Ubuntu.

Mg

---

