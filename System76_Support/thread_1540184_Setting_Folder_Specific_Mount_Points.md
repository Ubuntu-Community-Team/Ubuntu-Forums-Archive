---
title: "Setting Folder Specific Mount Points"
date: 2010-07-27
forum: System76 Support
---

### Post by tcopeland on 2010-07-27
I'm hoping to buy a System76 Wildebeest in the near future. I chose to have an Intel X25-M SSD factory installed, and I plan on buying a Western Digital Caviar Black 1TB 6 Gb/S HDD as a secondary storage device. Using RAID would be a bad idea, I realize. I want to mount /media/home (all users, if for some reason I set up more than one account) on the HDD and have programs and operating systems on the SSD. So basically, /media/home (once again, ALL home folders in the case of more than one user account) on the Caviar Black, and EVERYTHING else on the SSD. When I say everything else, I mean everything but Windows. Should I choose to install windows for some reason, I'll put it and all of it's respective files on the HDD. I won't need the SSD's speed, as I won't use Windows for much. Only Linux operating systems will be on the SSD. How do I set mount points like this?
Thanks!

---

### Post by isantop on 2010-07-27
Actually, the UNIX mounting system is robust enough to make this extermely simple.

You'll need a compatible filesystem and partition on the HDD. Hook them up to the computer before installing Ubuntu.

Next, run through the Ubuntu installer. When you get the the "Prepare Partitions" step, select "Specify Partitions Manually."

Now, You should see a graphical representation of all of your storage devices. Set up ext4 and swap partitions on the solid state drive (probably /dev/sda). Then, set up an ext4 partition on the hard drive. (Probably /dev/sdb). Next, set the ext4 partition on /dev/sda to have a mount point of /. Set the ext4 partition on the solid state drive to have a mount point of /home. Finally, finish the installation.

When the computer reboots, Ubuntu should mount the SSD at /home transparently, so you will be totally set up.

---

### Post by tcopeland on 2010-07-27
Thanks! I thought it would be as simple as that, but I just wanted to be sure before I buy and set up. Seeing as Ubuntu comes factory installed, could I boot into live and set mount points in GParted w/o having to reinstall?

---

### Post by isantop on 2010-07-28
You could, but it gets a bit complicated. I can help you out, but it would best be handled after you had the system, and over email.

---

### Post by tcopeland on 2010-07-28
Seeing as I don't have the system yet (and I will have to wait until I can afford it), this is not imminent. However, thank you and I'll be sure to contact you for help if [my friend]("http://ubuntuforums.org/member.php?u=133517") doesn't know this way.

---

