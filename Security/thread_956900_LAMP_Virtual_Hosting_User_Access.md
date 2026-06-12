---
title: "LAMP Virtual Hosting User Access"
date: 2008-10-23
forum: Security
---

### Post by craigp on 2008-10-23
So i decided to use proftpd for FTP access and i am using mysql to control it all.

Example for what i am refering to is here:
[http://www.howtoforge.com/proftpd_mysql_virtual_hosting](http://www.howtoforge.com/proftpd_mysql_virtual_hosting)
or
[http://www.nerdgirl.dk/proftpd/installation.php](http://www.nerdgirl.dk/proftpd/installation.php)

I have it all working but i am wondering how i should do the user accounts. Should i have it so that when they all access the files they are all under one group called www and then have all of the folders owned by the same user and group

or alternatively

create a different user and group for every site that i host? If i go with the latter i could end up with a lot of users on the computer because i could have a couple hundred sites on the server. 

It would be less maintenance if i had them all as the same users and groups but would that be a lot less secure? any other problems?

Cheers

---

### Post by Dr Small on 2008-10-23
The problem with having one user and group is that it can potentially create security problems. Like say, userA writes a script to put on his site, and the script runs on the server and rewrites userB's homepage. If all files are owned by the group "www" (and userB has bad permissions on his files (664, for example)), userA could easily change userB's files.

On the other hand, if there are seperate user/groups for each login, then the file ownership would be userA:userA and userB:userB. Unless userB's file is owned by group userA, userA can't alter his files.

Personally, I don't see why you couldn't just use accounts. I have seen some servers run hundreds of sites all from the same server, so it shouldn't be a big deal.

---

### Post by craigp on 2008-10-24
So i have been using different users and groups for each different virtual site. However, what do i do to have write access to all of them? Do i login as root? If so how can i do that because i tried setting that up and it isnt working..

---

