---
title: "XP can't map ..."
date: 2009-05-26
forum: Server Platforms
---

### Post by bujums on 2009-05-26
I have a Ubuntu Server for file sharing.  I was able to get 4 of the XP computers to successfully "map the drive" but one XP computer will not.  I can go through the process and it even sees the server but when I select it to map It does not, the "ok" button fades out and I can't proceed.  I have also tried to goto my network places and add a network place... and basically the same thing happens.  

any ideas?

---

### Post by jonabyte on 2009-05-26
Many ideas, need more info.

How are you doing this, I am assuming samba?

How is samba setup?

Is the security set to user?

Post the smb.conf.

---

### Post by bujums on 2009-05-26
I have set shares  for guest access not user... essentially I have not setup any security... and the system can't find the file smb.conf.  I am just trying to point the XP computer to the server all the other computers see the server just fine. I am only having trouble with one of them.  I don't think is it the Ubuntu server giving trouble I think it is the windows XP computer

---

### Post by HermanAB on 2009-05-26
On XP, do you have a username and password?  XP networking won't work properly if it is configured without a password.

---

