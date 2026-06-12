---
title: "How to partition a web server"
date: 2012-12-30
forum: Server Platforms
---

### Post by fernandoch on 2012-12-30
How would you go about partitioning a web server? I have 500 GB.

Would you create an lvm? Yes or no?

Thank you.

---

### Post by chadk5utc on 2012-12-30
I googled this also use it
LVM is suitable for:
    Managing large hard disk farms by letting you add disks, replace disks, copy and share contents from one disk to another without disrupting service (hot swapping).
    On small systems (like a desktop at home), instead of having to estimate at installation time how big a partition might need to be in the future, LVM allows you to resize your disk partitions easily as needed.
    Making backups by taking "snapshots".

---

### Post by cariboo on 2012-12-31
On my home file/media/web server, I set up / to be 20GiB, /home at 100GiB on a 120GiB hard drive. for data I have:

[LIST]
[*]2 X 500Gib
[*]2 X 400gib
[*]1 X 1TiB
[/LIST]

I gave / 20GiB, as thats all I figured I needed for mysql and mediawiki, /home is for family members to store personal files.

---

### Post by HomelandSecurity on 2012-12-31
> **fernandoch said:**
> How would you go about partitioning a web server? I have 500 GB.

Would you create an lvm? Yes or no?

Thank you.
is this for home, small business or med scale company.
500gb is not really a lot for a lvm , depending of course from the hardw. that you have.
i'd put "home", "var" end "etc" outside the "/" partition. to make backup, log-tmp files cleanup, reconfig easier . it's easier to create an image of a server when the etc folder is not present, even when the server is live. And also it makes it much easier to upgrade the hhds , You can easiel add more swap memory if you can handle more RAM and so on.

---

### Post by fdrake on 2012-12-31
> **HomelandSecurity said:**
> is this for home, small business or med scale company.
500gb is not really a lot for a lvm , depending of course from the hardw. that you have.
i'd put "home", "var" end "etc" outside the "/" partition. to make backup, log-tmp files cleanup, reconfig easier . it's easier to create an image of a server when the etc folder is not present, even when the server is live. And also it makes it much easier to upgrade the hhds , You can easiel add more swap memory if you can handle more RAM and so on.
+1 (I agree with myself)

---

### Post by spynappels on 2012-12-31
I'd definitely recommend going for LVM, it makes everything much easier down the line.

I'd create a 100MB boot partition and put all the remaining space into a volume group.
I'd then create a 20GB root logical volume, a 50GB /var volume and then a further logical volume to mount as /var/www and make it as large as you think you will need. Any unused space would become a last LV for /home.

---

### Post by darkod on 2012-12-31
> **spynappels said:**
> I'd definitely recommend going for LVM, it makes everything much easier down the line.

I'd create a 100MB boot partition and put all the remaining space into a volume group.
I'd then create a 20GB root logical volume, a 50GB /var volume and then a further logical volume to mount as /var/www and make it as large as you think you will need. Any unused space would become a last LV for /home.

Wouldn't it be much better to start the LVs with as small size as possible (depending what you need for the start), and then grow them as needed from the unused VG space?

If I'm not mistaken, you can grow the LV and the filesystem online, but you can shrink only the LV online. You need to shrink the filesystem offline. Which means you need to shut down to shrink because shrinking the LV without the filesystem first is pointless and dangerous.

Isn't the point of LVM to start small and grow as needed, instead of assigning the whole VG to LVs right away at the start? Later if you want to reassign part of the space to another LV it's more difficult (but not impossible).

---

### Post by spynappels on 2012-12-31
> **darkod said:**
> Wouldn't it be much better to start the LVs with as small size as possible (depending what you need for the start), and then grow them as needed from the unused VG space?

If I'm not mistaken, you can grow the LV and the filesystem online, but you can shrink only the LV online. You need to shrink the filesystem offline. Which means you need to shut down to shrink because shrinking the LV without the filesystem first is pointless and dangerous.

Isn't the point of LVM to start small and grow as needed, instead of assigning the whole VG to LVs right away at the start? Later if you want to reassign part of the space to another LV it's more difficult (but not impossible).

That's a good point, I was thinking in terms of the disk size now being fully available and the VG being extended by the addition of further PVs when required, which was why I said to create the /var/www LV as large as was required, with the option of growing when the VG was enlarged by adding extra PVs (HDDs).

The OP would need to host an extremely large number of websites with large databases for the disk to fill, and /home does tend to fill up rather more quickly.

But yes, you could (should) probably start small and grow as required.

---

### Post by fernandoch on 2013-01-01
Thank you guys.

And why not / 498 GB and swap 2 GB?

---

### Post by volkswagner on 2013-01-01
> **fernandoch said:**
> Thank you guys.

And why not / 498 GB and swap 2 GB?

One simple reason yet compelling enough is if you have a run away log file you could fill up your root partition.

If you / partition fills up, your system will become unstable and likely unresponsive to most commands.

A second compelling reason for creating separate partitions is for upgrades or re-installations.  If you have your data on separate partitions from /, you can reinstall without overwriting/formatting your user data.

You may think with ~500gigs it may take a long time before a run away log file fills the drive, I'd say time is relative :)

I'm sure you could install as you mention and likely have no issues.

If this project is for learning server admin, then I'd say go for lvm with small partitions for key mount points.  If this is just to get the server up as quick as possible then by all means partition like you mention, / and /swap.

[URL="http://unix.stackexchange.com/questions/685/why-put-things-other-than-home-to-a-separate-partition"]
Here are some responses[/URL] to your question.

---

### Post by fernandoch on 2013-01-01
Thank you, very clear.

---

### Post by Vegan on 2013-01-01
I use Linux in a virtual machine and i find its not very resource hungry even with a database driven web site.

The LAMP stack works fine with the defaults using 512 MB of RAM and a dynamically expanding hard disk. I use 2040 MB which is the standard for a MBR based VM.

Ubuntu is quick and easy with practical defaults.

---

### Post by LHammonds on 2013-01-02
I also recommend using LVM and as others have stated, start out with the smallest size necessary for your partitions and leave room to grow.  Separating the partitions increases security and stability of your system.

You can even setup your server to automatically grow partitions as needed on-the-fly and backups can be made while the servers is running.  No downtime required for resizing or backing up.

I have documented how I setup my servers in my signature.  A large section covers partitioning design.

LHammonds

---

