---
title: "Retreive MySQL database from drive?"
date: 2006-11-29
forum: Server Platforms
---

### Post by Beernut on 2006-11-29
Well here is my dilemma I had this web server running a wordpress blog and the hard drive died by died I mean a mechanical failure.  I didn't have a recent backup of the database (I know stupid me ](*,) ) After a lot of tinkering and a lot of luck I have been able to mount the drive by booting with a [STD live CD]("http://www.s-t-d.org/").  I figure I have two options but not sure which to try.

**Option #1**
I can see the the database folder in /var/lib/mysql/wordpress but I can't access because it's locked.  If there is a way I can change permissions and copy the folder would I be able to copy it to another server and access it so I can dump the data?  If so I am not really sure how to go about this.

**Option #2**
Try to boot with a Ubuntu server disc in rescue mode and install grub to this drive so that I just boot it and access the database through PhpMyAdmin or the command line and dump the database.  I am a little hesitant to try writing to this disc because I don't know how long it will keep running.

Sorry for the long post but I realize I am walking on egg shells with this drive.  Any help would be greatly appreciated.

---

### Post by elst on 2006-11-29
I beleive that Option 1 should work: if the MySQL service service isn't running then you can just copy the files for your databases and put them on to another Linux installation. I would double-check the MySQL documentation for recommendations first, though!

---

### Post by tturrisi on 2006-11-29
Try copying it first and after copied to a good drive try to access it.

---

### Post by Beernut on 2006-11-30
Thanks for the replies.  I was leaning towards option #1 myself feel better that it doesn't seem to off the mark.  I am not very familiar with the DD command but have been looking some tutorials has anybody used this and copied to a SAMBA share?  I am guessing this would be the best way to do the copy.  Unless there is an easier way by getting ownership.

---

### Post by tturrisi on 2006-12-01
Have a cd burner?

---

### Post by Beernut on 2006-12-02
OK I am ready to throw the drive in the garbarge.  The problem is I can't do anything because the files are locked or a permission issue.  Does anyone know how to get ownership of the files even using Ubuntu rescue mode?

The drive has been running OK however it making some clicking noise which I think is the arm banging against the platter.

---

