---
title: "Default user permissions error w/Ubuntu Server"
date: 2010-04-27
forum: Server Platforms
---

### Post by krodrigue on 2010-04-27
I am running Ubuntu Server 9.10

I noticed after a few reboots of the server I get a permissions error after logging in. It seems that root is the owner of everything including the users home dir.

I don't remember having this kind of issue in the past, what do you think?

---

### Post by ajgreeny on 2010-04-27
The real question is "why has ownership changed?".

Try to chown home back to yourself with ```
sudo chown -R user:user /home/user
``` if you have not already done so.

You may have a need also to chmod the home, but it will depend on why things have gone awry.  Try ```
chmod -R 755 /home/user
``` but only once home belongs to you again.

---

### Post by krodrigue on 2010-04-29
That is a great question, I wish I had the answer to it. The only thing I did was change the root passwd and log in as root  but this is the first time I had this happen.

---

### Post by krodrigue on 2010-04-29
Seems like I have the problem solved but now I cant start Firefox, but I can if I do it through the terminal as root.

---

### Post by ajgreeny on 2010-04-29
DO NOT use Firefox as root!!!

That is really asking for potential problems, as Firefox will be able to do anything to your system.

I suggest you make a new user who has admin privileges, as you do at the moment, then move all your personal files etc etc from your old home to the new one, and finally chown all those files to your new ownername.

Something has gone very wrong, but you should not use a workaround that demands root use for something connected to the web.

---

### Post by krodrigue on 2010-04-29
> **ajgreeny said:**
> DO NOT use Firefox as root!!!

That is really asking for potential problems, as Firefox will be able to do anything to your system.

I suggest you make a new user who has admin privileges, as you do at the moment, then move all your personal files etc etc from your old home to the new one, and finally chown all those files to your new ownername.

Something has gone very wrong, but you should not use a workaround that demands root use for something connected to the web.

Ok, I has already got red of the permissions errors before you sent the post but I must not have gotten all of them, I used the commands you posted and its now working, thanks.

---

