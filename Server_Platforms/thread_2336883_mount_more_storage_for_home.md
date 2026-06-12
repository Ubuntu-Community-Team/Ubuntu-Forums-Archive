---
title: "mount more storage for /home"
date: 2016-09-12
forum: Server Platforms
---

### Post by Vegan on 2016-09-12
eventually a LAMP box may run out room, not likely with 10TB disks but not every rig has a bank of them to work with

tar -cvpzf backup.tar.gz /home

so now that I have a backup, I wanted to say mount /dev/sdc to /home so that users could have a few EB to work with

obviously I need to maintain permissions and owner etc

---

### Post by TheFu on 2016-09-12
What is the question?  I can't figure it out from the post above. Something to do with storage, but I can't tell what exactly.

---

### Post by Vegan on 2016-09-12
with azure you can get more storage as needed and mount it on your virtual machine, so I figuring why not bolt on an extra EB or 3

sudo lshw -class disk
sudo fdisk /dev/sdc
sudo mkfs -t ext4 /dev/sdc
once the storage is partitioned and formatted it&#8217;s ready for use. so first we need a place to mount the disk under
sudo mkdir /home
sudo mount -t ext4 /dev/sdc /home

etc

---

### Post by TheFu on 2016-09-12
I'm still not seeing any question. However, 
* If you add very large storage, ext4 isn't the best choice.
* Should use something like LVM to get snapshots and flexibility it provides  It is nice to be able to extend file systems without taking the disks offline.
* How much does an EB cost? Chances are you'd want to split that up across lots of servers to gain added redundancy across multiple levels.

BTW, normally, it is good to post the command used AND the output causing issues with a question. That way people trying to help get facts, not interpretations.

Question?

---

### Post by Vegan on 2016-09-12
The VM I have now comes with 30GB for the system and 20GB for the user, enough for now, but I am always looking at what else can I do to milk the LAMP box for more ideas

---

### Post by TheFu on 2016-09-12
Mom always said not to put all our eggs in 1 basket. Sound advice. Don't put all your services/storage on 1 server, especially if it is on the internet.

---

### Post by Vegan on 2016-09-13
Wordpress automatically date stamps every backup it makes
so I have the ability to make snapshots

this one capability i believe all packaged solutions should feature

---

### Post by TheFu on 2016-09-13
> **Vegan said:**
> Wordpress automatically date stamps every backup it makes
so I have the ability to make snapshots

this one capability i believe all packaged solutions should feature

Wordpress?  That's what you are talking about?  You won't get it to handle EB worth of data.  You won't be using those trivial tar snapshot scripts to backup EB worth of data either.  EB .... you mean Exabyte, correct?    [http://highscalability.com/blog/2012/9/11/how-big-is-a-petabyte-exabyte-zettabyte-or-a-yottabyte.html](http://highscalability.com/blog/2012/9/11/how-big-is-a-petabyte-exabyte-zettabyte-or-a-yottabyte.html)
Heck, I'd not use their tar snapshot scripts for anything over a trivial blog website.

There is no one-size-fits-all backup solution. There are always multiple considerations.  What works for a tiny WP blog isn't sufficient for other types of web apps or where large data is involved.  If you cannot physically move the data over the wire during the allowed backup window, what then?  What happens if it takes more than 24 hours to move all the changed data, but you still want daily backups?  Systems like this do exist.

---

### Post by Vegan on 2016-09-13
Azure has enough resources to make the disks for my VM fault tolerant, so I am not worried about a dead hard disk

I was considering a another table for my vegan site to handle the USDA database that I could use to calculate some nutrition information from

not sure if i could get it working with WP or not, need to use PHP to query the database etc

---

### Post by TheFu on 2016-09-14
Azure is nothing special. Over time, I expect it will be great, but I don't want to be an early adopter there. Most Linux VPS provide redundancy, if you like. The level of redundancy is up to you. Whether local storage redundancy is more important than geographical redundancy is a question only you can answer.  I gotta ask - how much is MSFT paying you to post here about Azure?

The USDA DB isn't that big. Have you seen  [NUT ]("http://nut.sourceforge.net/") that has it?  [https://ndb.nal.usda.gov/](https://ndb.nal.usda.gov/) for any lurkers.

---

### Post by Vegan on 2016-09-15
besides a nutrient database i was even considering using the entire UPC database which is also not all that big

then when somebody searches by UPC they can find information, from a vegan's point of view

Even the UN now recognizes that meat is poison

---

