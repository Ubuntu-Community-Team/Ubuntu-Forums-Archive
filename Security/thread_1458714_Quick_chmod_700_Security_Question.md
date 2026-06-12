---
title: "Quick chmod 700 Security Question"
date: 2010-04-20
forum: Security
---

### Post by halloween2311 on 2010-04-20
Greetings Everyone.

I'm reviewing my security set up before I install 10.04 and had a quick question regarding using chmod 700 to set up a private subdirectory in my home folder.

Now as I understand it if I create a sub directory with chmod 700 then read-write-execute permissions will only be given to me (the owner).  However I am the only user on this computer so if someone hacks my account then they will have the same access, correct?

So my question is, on a single user only computer is it worthwhile to create a private subdirectory?  Are there other advantages I am missing here?

Thanks for the thoughts as always!

---

### Post by bodhi.zazen on 2010-04-20
> **halloween2311 said:**
> Greetings Everyone.

I'm reviewing my security set up before I install 10.04 and had a quick question regarding using chmod 700 to set up a private subdirectory in my home folder.

Now as I understand it if I create a sub directory with chmod 700 then read-write-execute permissions will only be given to me (the owner).  However I am the only user on this computer so if someone hacks my account then they will have the same access, correct?

That is correct. Physical access == full access to all files, your only protection is to encryption.

> So my question is, on a single user only computer is it worthwhile to create a private subdirectory?  Are there other advantages I am missing here?

Thanks for the thoughts as always!

The answer to that second question is for the most part an opinion, up to you to decide. You might want to look at LUKS and / or encryption of your home directory at installation.

---

### Post by halloween2311 on 2010-04-20
> **bodhi.zazen said:**
> That is correct. Physical access == full access to all files, your only protection is to encryption.



The answer to that second question is for the most part an opinion, up to you to decide. You might want to look at LUKS and / or encryption of your home directory at installation.

Thanks for the reply bodhi.zazen (and for the numerous tutorials of yours. I have used to learn more about securing Ubuntu:) ).

I'm already using full disk encryption via LUKs on the alternate CD, but I'm always looking for new ways to feed my paranoia!  :lolflag:

Thanks!

---

### Post by cdenley on 2010-04-20
You may have the only system user account, but processes often execute as separate users for security. For example, apache runs as www-data. If apache or a web application is exploited to gain local file access outside /var/www, they still won't have access to your private directory (unless they escalate to root privileges).

---

### Post by halloween2311 on 2010-04-21
> **cdenley said:**
> You may have the only system user account, but processes often execute as separate users for security. For example, apache runs as www-data. If apache or a web application is exploited to gain local file access outside /var/www, they still won't have access to your private directory (unless they escalate to root privileges).

Ahhh... I see.  Thank you, I hadn't thought of that.

Is there any downside you can think of to having the private directory?  For example if I have to restore from backups would I still have access to it? Or if I copy them into a new system would doing another chmod 700 on the file allow me to regain access?

Thanks again.

---

### Post by cdenley on 2010-04-21
With physical access, you can always read a file with minimal effort (unless it is encrypted and you don't have the password).

---

### Post by The Cog on 2010-04-21
> **halloween2311 said:**
> Ahhh... I see.  Thank you, I hadn't thought of that.

Is there any downside you can think of to having the private directory?  For example if I have to restore from backups would I still have access to it? Or if I copy them into a new system would doing another chmod 700 on the file allow me to regain access?

Thanks again.

I can't think of a down side, other than it's harder to share data with the other users (that you don't have). In fact, my home directory is chmodded 700.

---

### Post by halloween2311 on 2010-04-21
Thank you everyone for the replies.

I believe this what I will do:
1. I will continue with my full disc encryption
2. I will chmod 700 a subdirectory in my home directory for important files
3. I will use PgP to encrypt those files individually.

Okay, I think my paranoia is sated now!:-)

Thanks again everyone for the replies and feedback!

---

