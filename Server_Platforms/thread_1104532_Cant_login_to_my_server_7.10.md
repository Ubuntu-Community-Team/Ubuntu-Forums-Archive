---
title: "Cant login to my server 7.10"
date: 2009-03-23
forum: Server Platforms
---

### Post by cbielich on 2009-03-23
OS: Ubuntu 7.10

Here is the story, very strange. I run a web server and its been running fine for months, almost a year. Today when I came in I noticed one of my backup scripts which uses ftp to pull down files to backup was error'ing out with an incorrect username and/or password. So I tried to SSH into the box to check it out using putty.exe and just like the first time you ssh you have to gen a new key and approve it, it asked me that like I have never ssh'd into the box before. To clarify I have already done that many times. Then I try my user account and it acts like I have the wrong password or incorrect account name. So I think maybe its a ssh thing I go to the box itself....same thing. No accounts work (ie. root, username) I never log in using root anyways but the regular account I use is no longer working so I cant get in my box. I am downloading a new copy of 7.10 and seeing if I can repair it that way. Any ideas what happened?

C

---

### Post by Bachstelze on 2009-03-23
You got hacked, probably.

---

### Post by cbielich on 2009-03-23
Thats what I was thinking..


Well I downloaded a copy of 7.10 (because I lost my last copy) got in recovery mode. Reassigned passwords to my accounts and that's it. I'm back in. Very weird. I checked the history and found no suspicious commands typed so maybe I have a ghost in the server room.

---

### Post by Iowan on 2009-03-24
Not that 7.10 isn't a fine distro (I still run it on this desktop), but why didn't you take the opportunity to upgrade to LTS (8.04)?

---

