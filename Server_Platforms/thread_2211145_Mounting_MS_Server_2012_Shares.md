---
title: "Mounting MS Server 2012 Shares"
date: 2014-03-14
forum: Server Platforms
---

### Post by whaase on 2014-03-14
I know this has been asked a lot of times and I have googled and tried just about every combination I can find to mount a windows share, but I can't get it to work properly.

We have a MS Server 2012 at work with shares. One share is shared to everyone, no restrictions. 

I have a Ubuntu server that I'm trying to mount that share. I can get it to mount, but I can not write to it no matter what I try as a user, I have to be root for it to work. 

I tried creating the same user and password on both machines and got the same result. 

The directory i am mounting to on the ubuntu server was giving a chmod 777. Didn't help

I've tried editing the fstab with all combinations I could find. Same Result

I tried webmin, same result.

Anyone?

---

### Post by nerdtron on 2014-03-15
> I have a Ubuntu server that I'm trying to mount that share. I can get it  to mount, but I can not write to it no matter what I try as a user, I  have to be root for it to work.

What command have you used to mount the share?
After you have mounted it can you post the output of the command "mount"

---

