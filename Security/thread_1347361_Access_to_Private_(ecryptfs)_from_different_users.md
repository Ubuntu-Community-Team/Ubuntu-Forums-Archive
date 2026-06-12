---
title: "Access to Private (ecryptfs) from different users"
date: 2009-12-06
forum: Security
---

### Post by broseman on 2009-12-06
Hi community,

I have a Private directory since Ubuntu Intrepid (created via the alternate installer) and now would like to have access to it from different users, i.e. I have a few ubuntu installations on the same PC and would like to get access to the Private directory from every installation. 

```
ecyptfs-mount-private
```

does not seem to have any options which could help me.

Thanks in advance

broseman

---

### Post by broseman on 2009-12-11
I found a solution by editing /etc/fstab and mounting my existing Private directory via PAM on login.
You will quickly find a few howtos explaining the procedure.
One thing I noticed: most howtos are talking about putting the final mount command into the bash_profile.
But this is only necessary for console-based login. 
What worked for me was instead putting the command into "main menu" < "session" < "start programms"

Thanks for listening.

broseman

---

