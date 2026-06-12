---
title: "Microsoft Access database on Samba can't be opened by multiple users at once."
date: 2014-03-27
forum: Server Platforms
---

### Post by lepukowsky on 2014-03-27
I think I have backed myself into a corner. I offered to help a small family business by setting up a Samba file server. Everything works great except for their Microsoft Access database. On windows the .mdb file can be opened simultaneously by multiple users across the network, but when the .mdb file is on the samba server it locks.

Anyone out there ever setup a working MS Access DB on samba? I'm looking for a config file that "just works". I feel stupid because I didn't foresee this as a problem. I found a link to an O'Reily doc that was really intense and talked about all the different types of Linux locking, but I'd prefer not to have to learn and test all of that if someone out there can confirm that this is or is not possible.

I know there are a million Samba posts already, but searching this specific topic on the forums was not promising for me. Any help would be greatly appreciated. Thanks!!

---

### Post by TheFu on 2014-03-27
File locking is complex.
If you need a multiuser DB, then use a multi-user DB. Using MS-Access for anything but a single user is asking for corruption - just sayin'.  I've seen it over and over.

---

### Post by lepukowsky on 2014-03-27
Yeahhhh it's just it went from "working" to "not-working" with the switch to Linux in their eyes, which is a shame. I understand it wasn't a perfect system before, but they only have 3 employees so if 2 users had the same customer profile open at the same time they would just be like "yo, I'm editing that....get out!". The fact that Microsoft allows the .mdb's to be shared over networks and opened simultaneously means it essentially IS a multiuser DB... at least on their platform.

I am actually a Jr LAMP programmer by trade, but I'm not trying to redesign their db from scratch, migrate the data,  and be on the hook for maintenance when all I was originally supposed to do was set up a file server.

Is there really no conceivable Samba configuration that would allow this .mdb file to behave the same way it does on Windows?

---

### Post by oldfred on 2014-03-27
While I am sure Samba is part of the issue and I do not know anything about that.

Have you split Access into front end & back end data base, so only Access data is on server not Access queries, forms & reports.

Long retired now, but when working I would always split Access if more than one user or lots of data. But that was in a Windows shop.
Also when more than a few users or lots of data it worked to make backend MS SQL server. Have not tried many db's with Access but used btrieve, and SQL server. Had to install ODBC drivers which even with Windows was not always easy. But ODBC should then work with any db like PostgresSQL or MySQL.

---

### Post by TheFu on 2014-03-27
> **lepukowsky said:**
> 
Is there really no conceivable Samba configuration that would allow this .mdb file to behave the same way it does on Windows?

Don't know. There seem to be a few file-locking specific settings. I wouldn't trust my data with them, but perhaps someone else would? Guess that is up to you.  **man smb.conf** explains.

Or just load up a minimal Windows into a virtualmachine.

---

### Post by jfolsom2 on 2014-03-27
Found this: [http://www.oregontechsupport.com/samba/](http://www.oregontechsupport.com/samba/)

Scroll down to or search for "oplocks".

Maybe it will be useful, as it talks specifically about MS Access databases on Samba shares.

---

### Post by lepukowsky on 2014-03-27
Nice. That's the warmest lead yet. I've seen stuff about oplocks but nothing specific to ms access that would help me understand as a real world example. I will check this out when I get home. Still holding out that someone can confirm or flat deny this possibility though!

---

### Post by munzerelli on 2014-03-30
> **lepukowsky said:**
> I think I have backed myself into a corner. I offered to help a small family business by setting up a Samba file server. Everything works great except for their Microsoft Access database. On windows the .mdb file can be opened simultaneously by multiple users across the network, but when the .mdb file is on the samba server it locks.

Anyone out there ever setup a working MS Access DB on samba? I'm looking for a config file that "just works". I feel stupid because I didn't foresee this as a problem. I found a link to an O'Reily doc that was really intense and talked about all the different types of Linux locking, but I'd prefer not to have to learn and test all of that if someone out there can confirm that this is or is not possible.

I know there are a million Samba posts already, but searching this specific topic on the forums was not promising for me. Any help would be greatly appreciated. Thanks!!

im basiclly in the exact same position as you. 12.04LTS samba, file access is working great, but the issue i did not for see is the *.accdb locking issues. the db is for a small reality group of 7 users, i can get users access, but when they enter a new prospect on one user saves aby other user can not save until the first user closes out the db. i dont want to say we have to go to a windows server. i dont have the knoledge to convert this database to anything else. i have trued with oplocks enabled and disabled. i feel stuck and could use some help also. is there even a solution out there?

---

### Post by SeijiSensei on 2014-03-30
I found this posting on the Samba lists:
[https://lists.samba.org/archive/samba-ntdom/2000-July/013519.html](https://lists.samba.org/archive/samba-ntdom/2000-July/013519.html)

---

