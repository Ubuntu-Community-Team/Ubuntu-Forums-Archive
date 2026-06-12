---
title: "One user can log onto samba, but the other cannot"
date: 2012-07-11
forum: Server Platforms
---

### Post by Neezer on 2012-07-11
Hello,

I recently installed ubuntu server 12.04 onto a computer at home. I installed it with user1 as the admin user. I then created a user2 for my wife and a password to go along with it. I set up a samba share and can see it from the macbook air. I can login with user1 and the associated password, but I cannot login with user2 and her password.

When I try user2 and the password, I get an error message: "You entered an invalid username or password. Please try again."

I know that I typed in the username and password correctly, so I'm not sure why I'm getting this error.

I also have webmin installed as a way for me to administer things. Any help here would be much appreciated.

---

### Post by volkswagner on 2012-07-11
Did you add the second user both as a system user and SAMBA user?

Please post your smb.conf

---

### Post by Neezer on 2012-07-12
Sorry about the delay here. I got some help on the IRC channel. I ended up having to reinstall samba because I kept getting errors when I tried to add my wife as a samba user. after I reinstalled it worked just fine.

Thanks

---

### Post by sherrycd on 2012-07-12
> **Neezer said:**
> Hello,

I recently installed ubuntu server 12.04 onto a computer at home. I installed it with user1 as the admin user. I then created a user2 for my wife and a password to go along with it. I set up a samba share and can see it from the macbook air. I can login with user1 and the associated password, but I cannot login with user2 and her password.

When I try user2 and the password, I get an error message: "You entered an invalid username or password. Please try again."

I know that I typed in the username and password correctly, so I'm not sure why I'm getting this error.

I also have webmin installed as a way for me to administer things. Any help here would be much appreciated.
But I can't edit the profile

---

