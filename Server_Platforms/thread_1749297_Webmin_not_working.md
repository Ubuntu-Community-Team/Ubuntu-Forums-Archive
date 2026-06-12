---
title: "Webmin not working"
date: 2011-05-04
forum: Server Platforms
---

### Post by Ghost_Mazal on 2011-05-04
Lo all ,

I have just done a fresh install of server 11.04 32bit.
I installed webmin. I can hit webmin , but it doesn't take my login. I tried with both my users but it refuses to log me in as if my username or password is wrong.

Any ideas ?

Thanx

---

### Post by collisionystm on 2011-05-04
> **Ghost_Mazal said:**
> Lo all ,

I have just done a fresh install of server 11.04 32bit.
I installed webmin. I can hit webmin , but it doesn't take my login. I tried with both my users but it refuses to log me in as if my username or password is wrong.

Any ideas ?

Thanx


I believe I am correct when I say, you can only login to Webmin as root. At-least, that was the case with me.

To do this you must enable the root account.

I suggest you look on google for how-to's for this. Unforunately it is against policy here to enable the root account.

---

### Post by Ghost_Mazal on 2011-05-05
This wasn't the case before. On both 10.10 and 10.04 any sudo user could log in. I did get it fixed though. I found that now you have to manually go and specify that setting in "Webmin users" setting. There is a setting for "Allow all sudo users". I guess it is a new version of webmin and the previous ones already had that option set. Now you have to go enable root (like you said) and then go and specify that setting in webmin manually. Which is all good , but now my root account is enabled and I didn't really want that.

---

### Post by kochecc2 on 2011-06-10
I had the same problem and I fixed it by adding my username to the file ```
/etc/webmin/miniserv.users
```

Just add another line like the one that is in there but replace root with your username.

I did need to ```
sudo service webmin restart
``` after making this change.

---

### Post by Nessus81 on 2011-07-12
Thanx Kochecc2 for the tip. i can login to webmin now.
There is only problem i only can see the system information after i applied your fix. I added the line  [username]: x : 0 (without the spaces) Does anyone have an idea what i did wrong?

---

### Post by Nessus81 on 2011-07-12
> **Nessus81 said:**
> Thanx Kochecc2 for the tip. i can login to webmin now.
There is only problem i only can see the system information after i applied your fix. I added the line  [username]: x : 0 (without the spaces) Does anyone have an idea what i did wrong?

Solved the problem i needed to modify [FONT=Calibri]/etc/webmin/webmin.acl with an extr line like:
[username]: acl
and login to webmin and give me al the rights I needed in the webmin users
[/FONT]

---

