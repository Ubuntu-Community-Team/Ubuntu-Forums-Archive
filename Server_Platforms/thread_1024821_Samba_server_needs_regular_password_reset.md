---
title: "Samba server needs regular password reset"
date: 2008-12-29
forum: Server Platforms
---

### Post by coaltown on 2008-12-29
Hey, I'm having a strange problem with my samba server. Once I set the password on one of my samba users, samba operates fine for a while, allowing people to connect and use the files without a problem. But after a while, I start getting reports that people can't connect anymore. This happens roughly once a day. I have found that while restarting samba does nothing to fix the problem, resetting the password for that samba user again does fix the problem. Any ideas?

---

### Post by Iowan on 2008-12-29
The /etc/samba/smb.conf file has an authentication section dealing with syncing smb passwords with Unix passwords.  How is yours set?

---

### Post by coaltown on 2008-12-30
Unix password sync is set to false, but its commented out:

;   unix password sync = false

BTW, I forgot to mention, this all happened after I upgraded from Ubuntu 7.04 to 8.04. In 7.04 it worked fine, and I'm using the exact same config file and the drives are mounted to the exact same paths. My unix users are exactly the same with the same passwords and the same UID's as before. The only two things that are different are the version of ubuntu and probably the version of Samba

---

### Post by coaltown on 2009-01-12
Hey everybody. Still here. I swear to god, I'll switch to windows. (Just kidding). Bump

---

### Post by pdtpatrick on 2009-01-12
Hmm maybe you might have to set unix password sync to true and uncomment it? That way it uses your local authentication to authenticate the users against the users of your local box. Saves you time rather than having a user on the computer and then adding the same user to samba with the same password.

---

