---
title: "Cannot add password to smbpasswd"
date: 2009-09-12
forum: Server Platforms
---

### Post by okos on 2009-09-12
Hello,
After looking for a while and not finding a resolution, I finally decided to break down and post my issue.

I cannot add a password to my user name for samba. I found other people with the same issue but have not found a resolution.

```
dp@dp-laptop:/etc/samba$ sudo smbpasswd -a dp
[sudo] password for dp: 
Sorry, try again.
[sudo] password for dp: 
Sorry, try again.
[sudo] password for dp: 
Sorry, try again.
sudo: 3 incorrect password attempts

```

Samba seems a bit buggy. Any help would be much.

ps. I hope I posted this in the correct forum. Samba is a server but smbpasswd is a security issue. If the administrator chooses to move this post to the correct place, fine with me.

Thanks

---

### Post by Romey-Rome on 2009-09-12
That's sudo asking for YOUR password, not smbpasswd rejecting a new accoun password.

---

### Post by swerdna on 2009-09-12
Sorry -- bad advice -- removed

---

### Post by okos on 2009-09-13
> **Romey-Rome said:**
> That's sudo asking for YOUR password, not smbpasswd rejecting a new accoun password.

I'm sorry I'm not understanding what you are you suggesting to do.
I tried using swpasswd as a user but it has to be done by root.

What do you suggest?

---

### Post by okos on 2009-09-13
Thanks for the help.

I figured it out.
> dp@dp-laptop:~$ sudo su
[sudo] password for dp: <enter user password>
root@dp-laptop:/home/dp#
root@dp-laptop:/home/dp# smbpasswd dp
New SMB password:
Retype new SMB password:
root@dp-laptop:/home/dp# 


---

