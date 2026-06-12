---
title: "User accounts/adding user to group"
date: 2008-09-13
forum: Security
---

### Post by chris.davies on 2008-09-13
I have my server setup from fast hosts something they call matrix linux. Each domain has an owner (an account which is created on the Ubuntu system) and each domain is within a group.

I wanted to make it so my existing user account can edit files, so thought i'ld add my username to the group that owns the newly created domain files. I followed the tutorials on : [http://articles.techrepublic.com.com/5100-22_11-5349294.html](http://articles.techrepublic.com.com/5100-22_11-5349294.html)

and was asked for a password, I tried both my password for my existing account and the root password with no luck.

How do i go about adding my user account to a group in Ubuntu?

>C

---

### Post by boblemur on 2008-09-14
```
man adduser
```

will show u the full details however, but for example if u want to add user to group and type

```
adduser user group
```


ohh and u will need sudo obviously...

hope this helps

---

