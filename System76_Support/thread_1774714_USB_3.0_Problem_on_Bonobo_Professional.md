---
title: "USB 3.0 Problem on Bonobo Professional"
date: 2011-06-03
forum: System76 Support
---

### Post by sbly585 on 2011-06-03
All,

I just purchased a new Bonobo Professional last week and I'm having a USB 3.0 problem. I have purchased an Iomega 1.5 TB eGo USB 3.0 portable drive. I have removed the CD partition using an iomega utility. I am able to formato the drive ONLY on a Windows machine. All attempts to partition and format it under Linux have failed with an error message stating that the last cylinder is larger than the actual number of cylinders.

Nevertheless, I can format it with Windows on a different machine with NTFS. I can then connect the drive to the Bonobo using USB 2.0 and the drive works just fine as NTFS formatted. When I connect it to one of the USB 3.0 ports and go into the Ubunto Disk Utility the drive is recognized but no partition is present.

Do you guys think this is a drive problem (like Iomega not supporting the USB 3.0 standard properly), a problem with the machine's USB 3.0 ports, or something software related?

Thanks!

---

### Post by isantop on 2011-06-06
Can you format the drive in Ubuntu if you use a format other than NTFS?

---

### Post by sbly585 on 2011-06-07
Unfortunately, no. All attempts to partition and format the drive under Ubuntu with any format type result in the same error message as stated above. The only way to format this drive seems to be under Windows with NTFS. I'm starting to think that Iomega has designed the firmware in such a way that it will only work on Windows! I am planning to purchase a generic USB 3.0 drive enclosure to see what happens.

---

### Post by isantop on 2011-06-08
I have seen a few issues with Iomega drives in the past, so that is an (unfortunate) possibility. Let me know what you find out with the external enclosure.

---

