---
title: "Share Folder Password?"
date: 2006-09-25
forum: Server Platforms
---

### Post by Banagor on 2006-09-25
Hey there,

Very quick question for everyone (I hope this is the correct area to post in):

I'm setting up a really simple Ubuntu share folder for a small office. I don't want everyone to have access on the network, however. How can I make a very simple name/password setup to access the folder over the windows network?

Thanks in advance.

P.S. Yes I installed NFS and Samba.

---

### Post by Iowan on 2006-09-25
The **invalid users=** parameter should keep certain people out of specific shares (or off the server if installed in [global]).

---

### Post by Banagor on 2006-09-25
Cool...

But how can I keep everyone out except for certain users? Also, do I have to make logins/users on the Ubuntu server for access to the share folder for this to work? Basically, I want 6 people to have access to the folder, but not everyone else. I just want those 6 to have logins/passwords (or simply one login/password) for them to have access to the files.

1) Do they each need a login/password? If so, where do I make them? Under users? Groups?

2) How do I keep everyone else out? Just those 6 need access.

Any help appreciated. :)

BTW, I haven't used Linux in years. My last experience with it was KDE 3.0 which was great, but I had no idea how nice Ubuntu looks. Seriously, I'm impressed. It looks, frankly, amazing. I actually burned a copy of it today to put on my machine here at home which I intend to make into another server just for myself. I don't really have much of a reason for that, honestly, except the fact that it just LOOKS so nice. :)

---

### Post by Banagor on 2006-09-27
No other suggestions...?

Did I say something wrong? :)

---

### Post by Iowan on 2006-09-27
> **Banagor said:**
> No other suggestions...?

Did I say something wrong? :)
I had a busy night - After the usual 6:00am - 4:00pm day, I went back to work @8:00pm until 4:00am, napped until 9:00, then back to work again.  

There's a companion parameter called **valid users=** that can be used to limit who has access to a share.  (I suspect it, too, could be used globally.) As you're suggesting, the more efficient/secure method would be to set **security=user** and set up the "chosen few" with usernames/passwords on both Linux and Samba (That'd keep the "undesirables" completely away from shares, etc.)  For a double-dose of security, you could still use **valid users=** with either the usernames, or you could build a group, then give that group access.
I'm gonna use fatigue as the excuse for not remembering the details for adding a user with **adduser** (or is it **useradd**?) and **smbpasswd**

---

