---
title: "Raid 1 Help PLEASE"
date: 2008-09-11
forum: Server Platforms
---

### Post by raptorman on 2008-09-11
Hello and thanks for any help.

I am trying to get Linux RAID working using webmin but can&#8217;t seem to get the partitions correct. I am using Ubuntu 8.04 server with 2 identical 100 GIG IDE drives. When I do the initial install I select guided use entire disk. After the install I go into webmin and see the following.
[http://s132.photobucket.com/albums/q12/raptorman33/?action=view&current=1.jpg](http://s132.photobucket.com/albums/q12/raptorman33/?action=view&current=1.jpg)

When selecting IDE Device E I get the following details.
[http://s132.photobucket.com/albums/q12/raptorman33/?action=view&current=2.jpg](http://s132.photobucket.com/albums/q12/raptorman33/?action=view&current=2.jpg)
This drive says Cylinders 12162

Selecting the second dive creating a Linux partition with the same start and end point as the first drive I am only getting 5.75 GIG as shown below.

[http://s132.photobucket.com/albums/q12/raptorman33/?action=view&current=3.jpg](http://s132.photobucket.com/albums/q12/raptorman33/?action=view&current=3.jpg)

 
This drive is showing Cylinders 193821 

I know I can install a GUI and use GPARTED to make these partitions but I am trying really hard to use a CLI and Webmin. I spent over a week trying to just use the CLI then switched to webmin. If I can get the knowledge using webmin then I am going to try again using just the CLI.

Thanks in advance for any help

---

### Post by Krupski on 2008-09-11
> **raptorman said:**
> Hello and thanks for any help.

I am trying to get Linux RAID working using webmin but can&#8217;t seem to get the partitions correct. I am using Ubuntu 8.04 server with 2 identical 100 GIG IDE drives. When I do the initial install I select guided use entire disk. After the install I go into webmin and see the following.
[http://s132.photobucket.com/albums/q12/raptorman33/?action=view&current=1.jpg](http://s132.photobucket.com/albums/q12/raptorman33/?action=view&current=1.jpg)

When selecting IDE Device E I get the following details.
[http://s132.photobucket.com/albums/q12/raptorman33/?action=view&current=2.jpg](http://s132.photobucket.com/albums/q12/raptorman33/?action=view&current=2.jpg)
This drive says Cylinders 12162

Selecting the second dive creating a Linux partition with the same start and end point as the first drive I am only getting 5.75 GIG as shown below.

[http://s132.photobucket.com/albums/q12/raptorman33/?action=view&current=3.jpg](http://s132.photobucket.com/albums/q12/raptorman33/?action=view&current=3.jpg)

 
This drive is showing Cylinders 193821 

I know I can install a GUI and use GPARTED to make these partitions but I am trying really hard to use a CLI and Webmin. I spent over a week trying to just use the CLI then switched to webmin. If I can get the knowledge using webmin then I am going to try again using just the CLI.

Thanks in advance for any help

Is your OS installed on those drives (i.e. on one or more of the partitions)?

(arghh! Nevermind I looked more carefully at your screen shots).

Read THIS: [http://www.howtoforge.com/install-ubuntu-with-software-raid-10](http://www.howtoforge.com/install-ubuntu-with-software-raid-10)

It show how to install Ubuntu onto a RAID 10 setup, but the instructions equally work with RAID 1.

Good luck

---

### Post by raptorman on 2008-09-11
Thank You Krupski

I will give it a try. Is there no way to make a RAID 1 array with the OS already installed? Does this have to be done during the initial install?

Thanks you very much

---

### Post by cariboo on 2008-09-11
Usually you set up your raid array before installing the system.

Jim

---

### Post by Krupski on 2008-09-11
> **raptorman said:**
> Thank You Krupski

I will give it a try. Is there no way to make a RAID 1 array with the OS already installed? Does this have to be done during the initial install?

Thanks you very much

Frankly, I don't know.

I imagine if you had a running system and added another drive to it (with the intent of making a mirror), the RAID driver would begin to sync one drive to the other. But WHICH would be the "source"?

The sync process might write the emptiness of the new drive onto the working old drive...

The best way I can think of to do it is to start clean... make the array with a live CD, then install onto the array.

-- Roger

---

### Post by y@w on 2008-09-11
> **raptorman said:**
> Thank You Krupski

I will give it a try. Is there no way to make a RAID 1 array with the OS already installed? Does this have to be done during the initial install?

Thanks you very much

It's doable, but not exactly easy.. You would have to start with some empty space on the first drive to move a partition to a RAID or shrink a partition somehow and move each of the partitions to RAIDed partitions.. Very messy, I'd just start over.

---

