---
title: "allocate space for each user"
date: 2010-10-01
forum: Server Platforms
---

### Post by hemi519 on 2010-10-01
Hi All,

Iam new to the server side. and i want to know, if it is possible if i can have sub-users in my server and can i allocate a limited amount of space only. For example i am the  root of server and now i can add another user with name john and he should be able to use only of 2GB out of my total hard-disk. Is this possible? or is there any other way to do this. Plz help me out if anyone knows this solution

---

### Post by abix_adam_pl on 2010-10-01
The solusion for this is QUOTA ( [http://www.ubuntugeek.com/how-to-setup-disk-quotas-in-ubuntu.html](http://www.ubuntugeek.com/how-to-setup-disk-quotas-in-ubuntu.html) )
Also you may intrest in limits ([http://manpages.ubuntu.com/manpages/lucid/man5/limits.conf.5.html](http://manpages.ubuntu.com/manpages/lucid/man5/limits.conf.5.html))

Best regards,
Adam

---

### Post by hemi519 on 2010-10-04
thanks for that suggestion, But when iam trying to install the quota 


apt-get install quota quotatool 

iam getting this  error 


E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by hemi519 on 2010-10-04
the problem is solved iam able to install it

---

### Post by hemi519 on 2010-10-06
Iam in middle of adding users and allocating space for them, I am having a doubt here, i created a user with name John, now iam able to see John in my /home/ folder and also at the login screen. Am i in correct way. Is this wht happens when every new user is created. If it is wrong way help me out

---

