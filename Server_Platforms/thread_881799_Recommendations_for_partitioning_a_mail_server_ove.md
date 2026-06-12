---
title: "Recommendations for partitioning a mail server over RAID arrays"
date: 2008-08-06
forum: Server Platforms
---

### Post by Quitch on 2008-08-06
Yes, it's the old favourite, Linux partitions.

Back when I first discovered Linux I spent as much time piddling around with partition setups and various fstab flags as I did actually using the thing, but one thing I never had available to me when setting up a new system was RAID arrays. Now I work with servers and get to do it all again (but this time for real :P), and due to the fact I'm inheriting this system the RAID arrays are already pre-determined, a RAID 1 array of two disks (duh) and a RAID 5 with four disks.

The question I have is how best to split a mail server on such a setup. On Windows I'd put the C partition on the first array and the D partition on the second array, and that'd be that. I don't know what best practice is for Linux in this situation though, should I be putting / on one and /home on another etc.?

Off the top of my head I think sendmail (though another MTA may be used) puts its queue under /var/... and therefore I'd want most of the setup on the first array and then /var on the second. Advice welcome! Big Grin

My gut tells me I should do the following:

RAID1 (72GB):

/boot
/
/swap
/usr

RAID5 (216GB):

/var
/home
/tmp

Unsure whether it's worse the hassle of spinning off /tmp into its own partition.

This is a gateway system processing incoming and outgoing mail, but not holding any mailboxes.

---

### Post by StickyStyle on 2008-08-06
Since it's just a gateway as you say, why bother with gaining the extra disk space with a RAID5 - why use all six disks in one RAID1+0?  You get all the speed, and more redundancy since you already have 6 disks in the machine.

Yeah, /var should have its own partition, perhaps even have the /var/spool on another partition.  /tmp is a good idea to have on its own partition also so some runaway process that writes to /tmp doesn't eat up all your HD.

And if its just a gateway as you say with no users, /home /usr /boot can all just be on the / partition.

---

### Post by Quitch on 2008-08-07
Will the benefits of 1+0 be greater than the mail queue being on a separate controller and array to the rest of the system?

Should /var/spool be split off into its own partition?

---

### Post by StickyStyle on 2008-08-07
Well your first controller (RAID1) is going to be basically idle after boot up, all the activity is going to be taking place on second (RAID5) controller in your configuration - so there really is no net performance gain splitting your setup like that.  In fact you will be taking a hit in performance by using RAID5 as the controller or OS if your doing software RAID has to now calculate disk parity.

There are a few reasons for using separate controllers, like bus bandwidth or I/O contention.  
Hypothetical here...
Say this was a server where users accessed their mail and was the mail gateway (and say you had a few hundred active users), with the users mail store and the spool on the same controller you *may* run into some contention issues as the controller is getting commands to go all over the drives for receiving mail from postfix and the users IMAP or POP procs are pulling in mail.  Here if you put the spool on one and the users mailstore on another you have solved the contention issue.

Really we need a little more info about the utilization of this server, are we talking 10 messages/min or 10,000 messages/min?  What kind of hardware is this machine?

I see people often underestimate what their servers can do and spend too much money on the box, or too much time fussing around with points that in the end will not make much of a difference.

---

