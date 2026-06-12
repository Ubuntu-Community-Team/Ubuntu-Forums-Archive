---
title: "User quotas, limit?"
date: 2010-10-29
forum: Server Platforms
---

### Post by mYrN on 2010-10-29
Hi. Im trying to limit the diskspace users on the system may consume, and i found quotas (im a total linux noob). But when i try to set it, no matter what i set it to the maximus is 2 GB. Now... i need quite a lot more than that. One user should be able to use 1900 GB and the other 600 GB. How can i fix this? Im using ubuntu server 10.04. Thanks!

---

### Post by psusi on 2010-10-29
Hrm... I have not used quotas since like 1995, but it sounds like there is a 32 bit bug that needs fixed.

Rather than use quotas though, you might try either just manually enforcing it ( hey, I have noticed you are using too much disk space, please delete something ) or giving each user their own volume, both of which should be doable if you only have 2 users.

---

### Post by mYrN on 2010-10-30
Im using 64 bit. The thing is i cant sit and monitor the server all the time, and to have separate volumes isnt doable in my system. I Need a way to set a limit.

---

### Post by psusi on 2010-10-30
> **mYrN said:**
> Im using 64 bit.

Doesn't matter.

> **mYrN said:**
> The thing is i cant sit and monitor the server all the time, and to have separate volumes isnt doable in my system. I Need a way to set a limit.

Would it really be so bad if someone exceeded there limit slightly for a short while?  And why can't you have multiple volumes?

---

### Post by mYrN on 2010-10-30
Yes, since each user Really needs their space. Is there a way to enforce this?

---

### Post by psusi on 2010-10-30
I just tried this on 10.10 and it works fine here.  How exactly did you setup and enable the quotas?

---

### Post by mYrN on 2010-10-30
Can you have more than 2 GB? How exactly did you do that? :)

---

### Post by psusi on 2010-10-31
Yes... I currently am using over 6 gb and when I set my quota to how many blocks I'm using now, I tried to create a new file and got an error: out of quota.  Increased it a few blocks and it worked.

I installed the quota package, then added the quota option to my mount options in /etc/fstab, remounted, and ran quotacheck to build a current quota file, then ran quotaon to enable it.  Then I ran edquota to edit the limit.

---

### Post by mYrN on 2010-10-31
What should i set the limits to to get 1900 GB limit and 600 GB limit then?
If i write 644245094400 bytes (600GB) as the limit, it says: "edquota: Cannot write quota for 1002 on /dev/md3: Numerical result out of range".

---

### Post by psusi on 2010-10-31
Quotas are listed in kb, not bytes.

---

