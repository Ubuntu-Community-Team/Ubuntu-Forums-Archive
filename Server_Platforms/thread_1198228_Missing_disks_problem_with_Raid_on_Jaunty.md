---
title: "Missing disks problem with Raid on Jaunty"
date: 2009-06-27
forum: Server Platforms
---

### Post by IanCoubrough on 2009-06-27
Hi,
I joined the community to try and solve a problem with setting up RAID on Jaunty, in the event, email server issues prevented me logging on until after I had already found the solution. So, I will post a brief description of the problem and the solution I found in case this helps anyone else.
 
I wanted to set up RAID10 and RAID1 arrays on a new Jaunty server install, this was to be done on six 750GB Western Digital disks that had previously been on another machine under hardware raid. I first tried to set up a RAID10 array with Jaunty booting off a separate disk, using mdadm I created the array with a live CD, the installation went fine except that the partitioner said it had detected disks that might be part of a raid array and did I want to enable RAID, I found it strange that if I answered yes to this then the partitioner subsequently saw 5 disks, and if I answered no, it saw 6. I pressed ahead and installed anyway. On reboot I got grub error 15, which I assumed was the installer seeing the disks in a different order to grub. Finally I managed an install by physically removing the raid disks and installing on a single disk. then I connected the raid disks up and rebooted. md0 did not start, and would not assemble. On closer inspection I found a device /dev/md-d0, and when I stopped this, I could assemble and start /dev/md0 with six disks.
 
I tried using /etc/rc.local to stop /dev/md-d0 and start md0 to no avail, the commands would only work after the system had loaded and I had logged in. At this point I started to suspect the previous history of the disks, and ran the utility from Western Digital to a) check all the disks and b) write zeros to the entire disk. This exercise made no difference at all. I also tried creating a RAID1 array as well and installing on to that - the partitioner correctly showed /dev/md0 and /dev/md1 as available and allowed me to install on the /dev/md0 RAID1 array, however grub would not boot the system complaining that it could not find '/'.
 
Eventually I came across this post [http://diehealthy.org/linux/dmraids-metadata-mdadm](http://diehealthy.org/linux/dmraids-metadata-mdadm), sure enough, dmraid -r showed up an NVidia raid config on one of the disks, how that survived the zeroing of all data I have no idea, in fact the Nvidia config was a leftover from a couple of years previously, I had first installed these disks under NVidia raid on a Vista install, subsequently moving them to an Adaptec hardware controller when Vista frequently failed to boot.
 
The problem was solved with dmraid -r -E to remove the offending metadata After which I installed Jaunty on a RAID1 partition with no problems. So, if the Jaunty installer asks if you want to enable RAID because it has found disk(s) with RAID info on them, don't think that it is referring to mdadm created RAID partitions. If you are not using motherboard (fakeraid), then get rid of the old metadata first.

---

