---
title: "RAID5 after installing to a single disk - Now I want 3"
date: 2010-06-04
forum: Server Platforms
---

### Post by schworak on 2010-06-04
I may need to just start from scratch but I hope that is not the case. I have been reading and I get conflicting information or at least I get confused about what I am reading (most likely)

I have read a How-To for setting up RAID5 on three disks starting with a clean install from the live CD. So I am sure I can do this and have my system boot up to the RAID just fine.

I have seen a How-To for taking a single data drive and adding two more drives to it to create a three drive RAID5 setup for data. But this one assumed that the OS was on another drive.

So, is there a way to add two more drives to my existing system and convert the OS drive over to a RAID5 configuration? Without losing all the work I have already set up of course.

This is Ubuntu 10.04 by the way.

---

### Post by ian dobson on 2010-06-04
Hi,

You can't boot linux from a RAID5 mdadm array. All you could do is create a small boot parition for / and mirror it over all your drives and create a RAID5 array over the rest of the space.
That's how I've setup my backend server (6 x 2TB wd drives.)

Regards
Ian Dobson

---

### Post by schworak on 2010-06-04
That kind of makes sense and was what I was guessing after re-reading the how-to documents. I guess I didn't quite have it right in my head.

After thinking about it a bit, I think I will set up the 3 drive RAID5 now just for the data, a mirror for the OS and later down the road move the data drives over to another computer to make a simple NAS for cheap.

Thanks!

---

