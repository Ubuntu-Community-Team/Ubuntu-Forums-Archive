---
title: "Merging disks"
date: 2018-12-22
forum: Ubuntu Cloud and Juju
---

### Post by albertocastillo2001 on 2018-12-22
Hello

I have a baremetal server on Scaleway that has 2 disks running Ubuntu 16.04 LTS
One is a 50 GB one that comes with the server, and an additional one that must be mounted which is 250 GB

I have several users under /home and I have to create more users that will run specific processes to each user. Unfortunately I am running out space in the 50 GB one and would like to merge the 250 GB one in there without loosing any information.
If you have also another choice that would be doable I would appreciate it as well.

Thanks

---

### Post by vidtek on 2018-12-22
> **albertocastillo2001 said:**
> Hello

I have a baremetal server on Scaleway that has 2 disks running Ubuntu 16.04 LTS
One is a 50 GB one that comes with the server, and an additional one that must be mounted which is 250 GB

I have several users under /home and I have to create more users that will run specific processes to each user. Unfortunately I am running out space in the 50 GB one and would like to merge the 250 GB one in there without loosing any information.
If you have also another choice that would be doable I would appreciate it as well.

Thanks

Buy a couple of terabyte discs, they are so cheap these days it is just not worth stuffing about.  Use qt5-fsarchiver to back up the partitions as they are at present.

qt5-fsarchiver will clone to larger or smaller partitions with no data loss.  Alternately use dd or rsync to back them up, but qt5-fsarchiver and it's cli version fsarchiver is easier and can do different sizes with less hassle.
Tony

---

### Post by albertocastillo2001 on 2018-12-22
Hi vidtek

Thanks for your answer.
Unfortunately that's not an option, as it's a baremetal server from Scaleway. I can add 50 GB disks by one euro each, but can't buy the size I want. This is why I have to scale them and use as I asked for.

The machne comes with a 50 GB disk
A 250 GB disk that you can mount
And then you can add 50 GB disks by paying one extra euro per disk.

Thanks

---

### Post by vidtek on 2018-12-23
> **albertocastillo2001 said:**
> Hi vidtek

Thanks for your answer.
Unfortunately that's not an option, as it's a baremetal server from Scaleway. I can add 50 GB disks by one euro each, but can't buy the size I want. This is why I have to scale them and use as I asked for.

The machne comes with a 50 GB disk
A 250 GB disk that you can mount
And then you can add 50 GB disks by paying one extra euro per disk.

Thanks

Sorry didn't realize it was a cloud situation, should read the question more carefully, never heard of scaleway, and just assumed it was a standard setup.  You should still be able to utilise fsarchiver to achieve your aims though.
Tony.

---

### Post by albertocastillo2001 on 2018-12-23
Hi

FSArchiver seems to be a backup utility. I don't want to use this.
What I need to do is mounting the 250 GB disk and then "bridge" the 2 disks together so I can use all available space.

As I mentioned earlier, users have their documents under /home/USERNAME and I can't move that. Any idea to "merge" them somehow?

Thanks

---

### Post by vidtek on 2018-12-24
> **albertocastillo2001 said:**
> Hi

FSArchiver seems to be a backup utility. I don't want to use this.
What I need to do is mounting the 250 GB disk and then "bridge" the 2 disks together so I can use all available space.

As I mentioned earlier, users have their documents under /home/USERNAME and I can't move that. Any idea to "merge" them somehow?

Thanks

With fsarchiver you can move partitions around, clone to smaller or larger than the original.
There are many tutorials here on the different ways to move home folders.  In your situation I would keep the 50gb for just the operating system and the other for home and data folders.
Tony.

---

### Post by albertocastillo2001 on 2018-12-24
I actually would like to use both disks as they will hold a large amount of data, this is why I would like to merge them in some way similar to a RAID 0 setup but without the need to rebuild the volumes or the array (as there's no array) and can't actually stop the processes that are running for these users.
Btw, happy holidays and thanks for your help!

---

