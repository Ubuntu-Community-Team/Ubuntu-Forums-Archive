---
title: "Which do you prefer for SSH logins: password, or key-based authentication?"
date: 2005-12-11
forum: Server Platforms
---

### Post by J.C. Denton on 2005-12-11
Where I work, we have a great deal of UNIX systems that we manage.  Most of them share a "common" root password that's propogated across the network.  When it comes time to change critical passwords (i.e. root/toor, etc.) the password is changed on the master, and people continue with password based authentication.

I'm kind of torn on this.  I really like the idea of key-based authentication.  That way if someone's workstation was comprised, revoke the authorized key, the world is safe (again).  With password-based authentication, the password is compromised, and *everyone* has to learn a new password.

So what does the Ubuntu Forums community think? Password, or key-based authentications? 

If you like key-based authentications, what would you recommend for "converting" password users? Is there any way to ease the pain of the initial setup?

---

