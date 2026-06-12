---
title: "Samba &amp; Mac client"
date: 2011-04-07
forum: Server Platforms
---

### Post by ckfoxtrot on 2011-04-07
Hi all,

A few days ago I installed Ubuntu Server 10.10 on an old pc of mine.

I have installed samba on the server and it appears that I have it configured properly and running fine.

There are two users set up on my server and I have them added to samba with passwords established.  I have the first user (user1) logged in on the system.

When I connect to the server from my MacBook Pro, I can connect fine with user1's username and password.

However, if I try to connect using user2's username (which is the same as my username on my MBP) and password, I fail to establish a connection, Mac OS telling me that I provided an invalid username and/or password.

I have double checked the username and password for user2 on my server and everything appears to be correct.

If anyone has any ideas on what the problem might be I would appreciate hearing them.

ck

---

### Post by bab1 on 2011-04-07
> **ckfoxtrot said:**
> Hi all,

A few days ago I installed Ubuntu Server 10.10 on an old pc of mine.

I have installed samba on the server and it appears that I have it configured properly and running fine.

There are two users set up on my server and I have them added to samba with passwords established.  I have the first user (user1) logged in on the system.

When I connect to the server from my MacBook Pro, I can connect fine with user1's username and password.

However, if I try to connect using user2's username (which is the same as my username on my MBP) and password, I fail to establish a connection, Mac OS telling me that I provided an invalid username and/or password.

I have double checked the username and password for user2 on my server and everything appears to be correct.

If anyone has any ideas on what the problem might be I would appreciate hearing them.

ck

All users need to have a Linux (Ubuntu) account as well as a Samba account.  This can be a system account (no login).  Another way is to allow all user access via a guest account.

---

### Post by ckfoxtrot on 2011-04-07
> **bab1 said:**
> All users need to have a Linux (Ubuntu) account as well as a Samba account.  This can be a system account (no login).  Another way is to allow all user access via a guest account.

Hi bab1,

Both user1 and user2 have linux and samba accounts on my server, but I can only connect with user1 from my MBP for some reason.

---

### Post by bab1 on 2011-04-07
> **ckfoxtrot said:**
> Hi bab1,

Both user1 and user2 have linux and samba accounts on my server, but I can only connect with user1 from my MBP for some reason.

My first inclination is to add a third user (user3) and see it that user works.

---

### Post by Morbius1 on 2011-04-08
Did you originally set user2's samba password to match user2's login password on the server itself? Or did you want them to be different?

---

### Post by ckfoxtrot on 2011-04-08
Hi guys,

I added another user like bab1 suggested and it indeed allowed me to connect with that user.

So being, I ran smbpasswd -x user2 and for user3, -a user2, and now it works!

The system and samba pws were set the same for both of those users, which, seeing as it now works, I guess was not the problem (though setting them as the same might not be the best idea...?)

Thanks for the help!

ck

---

