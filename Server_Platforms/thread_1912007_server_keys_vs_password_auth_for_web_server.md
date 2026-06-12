---
title: "server keys vs password auth for web server"
date: 2012-01-19
forum: Server Platforms
---

### Post by jonny.milano on 2012-01-19
Hi, I'm a front-end developer that just setup a new Ubuntu web server (LAMP). Some googling lead me to a few discussions on server keys (public/private pair). Now, in the past I've just used SFTP. But some programs for writing code that I use are starting to support (in a kinda clunky way) server keys. I've never had a security issue in the past and not being a server guy, I don't know the level of importance here. My web apps are simple and I never house super important stuff on a my web servers. I'm not trying to be a troll here, but what is your take on this? Is it worth the extra hassle of trying to find ways of easily editing code with server keys in place? I installed fail2ban.

---

### Post by Buntumatic on 2012-01-19
You do not mention SSH. Is that what you are talking about? If yes, then key based authentication is definitely way more secure. However, when abiding general UNIX rule 'default denied' and granting only necessary permissions plus using cracklib to deny weak passwords - password based authentication can be secure enough.

---

### Post by jonny.milano on 2012-01-19
Oh yes, sorry, should have mentioned SSH. I thought that sFTP was only that. Sorry. Yes, also when talking keys, I'm talking SSH. 

Thank you for your input on the matter, I've got SSH Keys installed but am pulling my hair out on a mac environment trying to get my IDE's to authenticate correctly. I may just go back to password based auth.

---

### Post by CharlesA on 2012-01-20
As long as you have a strong password 15-20 characters (or more), you should be fine. I use a passphraseless key when I run scripts, but that might be a security risk unless the lock it down.

---

### Post by jonny.milano on 2012-01-20
Thanks to you both! I will put to rest my paranoia. I have found it much easier to update code and move files via sftp now rather than with ssh key pairs.

---

