---
title: "Add spare drive to Ubuntu Server"
date: 2009-08-31
forum: Server Platforms
---

### Post by unsoc on 2009-08-31
My current server has Maxtor 40GB ( IDE ) hard drive as the main drive. I have a spare Western Digital 200GB  ( IDE )hard drive that was in a PC that was given to me. 
Since I already have the server setup to my likings I see no reason to redo it. I want to add the 200GB as a spare drive to use the server as a media server. What are the steps needed to add the 200GB drive as a spare?

I also have a 200GB SATA drive. Would there be any advantages in using this drive as the main or spare? 

Thanks to those who reply!

---

### Post by hessiess on 2009-08-31
> **unsoc said:**
> My current server has Maxtor 40GB ( IDE ) hard drive as the main drive. I have a spare Western Digital 200GB  ( IDE )hard drive that was in a PC that was given to me. 
Since I already have the server setup to my likings I see no reason to redo it. I want to add the 200GB as a spare drive to use the server as a media server. What are the steps needed to add the 200GB drive as a spare?

I also have a 200GB SATA drive. Would there be any advantages in using this drive as the main or spare? 

Thanks to those who reply!

SATA is has much more bandwith than IDE and also has smaller cables, which can improve airflow and reduce the internal temperature.

Basically you want to format the drive with ext3, add it to /etc/fstab mounting it in the filesystem, i.e. /srv/ (you can have multiple partitions mounted in different places if you want) and move your data onto the drive.

---

### Post by unsoc on 2009-09-05
I finally got around to adding the drive and setting it up. The net thing I want I'd like to be able to to is access it over the internet.

I read a few guides but it was for adding a domain, and when I typed the address it was looking for spare.com/10.168.1.100/ The IP is my router of course I just changed the number for a little more security. 

Thanks

---

### Post by hessiess on 2009-09-05
To acsess the drive over the net you can use SFTP.

---

### Post by unsoc on 2009-09-05
I'm aware of this, I do it now. It's not a issue for me, but there will be family members who I want to be able to see the site so they can look at the photo gallery, upload photos and so on.

Thanks.

---

