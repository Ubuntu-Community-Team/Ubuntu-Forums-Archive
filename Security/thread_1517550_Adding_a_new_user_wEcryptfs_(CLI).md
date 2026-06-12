---
title: "Adding a new user w/Ecryptfs (CLI)"
date: 2010-06-25
forum: Security
---

### Post by Gurtz on 2010-06-25
Hi all,

I feel this is a bit of a dumb question, but I have searched for an answer, and haven't turned up anything yet. I have just installed 10.4 using the minimal install (because I basically want to start from the ground up, rather than installing a lot of software I won't need). At the prompt I provided a user ID and password, and asked the installer to encrypt my home directory. So far so good.

However, after doing the install, I realized I'd prefer to use a different user ID. So, I'd like to add a new user, but also have that user's home encrypted with ecryptfs. But I want to do so at the command line (because I don't have a GUI at this point, and, I'd like to learn the CLI better anyway).

Can someone give me a brief summary of the steps I'll need to take (including, if possible, the steps for deleting the original user ID)?

Thanks so much! Though I'm really new here, I already appreciate how helpful everyone is. It seems like a very cool community.

All the best,
Gurtz

---

### Post by bodhi.zazen on 2010-06-25
```
sudo adduser --encrypt-home new_user_name
```

[http://manpages.ubuntu.com/manpages/lucid/en/man8/adduser.8.html](http://manpages.ubuntu.com/manpages/lucid/en/man8/adduser.8.html)

---

### Post by Gurtz on 2010-06-25
Thank you! I thought it was going to be a lot more complicated than that.

I appreciate the reply.

All the best,
Gurtz

---

### Post by bodhi.zazen on 2010-06-25
You are most welcome =)

---

