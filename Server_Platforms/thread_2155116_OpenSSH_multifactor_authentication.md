---
title: "OpenSSH multifactor authentication"
date: 2013-06-17
forum: Server Platforms
---

### Post by Blazr on 2013-06-17
Hi,

I have OpenSSH 6.2 installed and I'm trying to get public key + google auth both required for ssh login. I heard that 6.2 supports AuthenticationMethods which makes this possible, but whenever I add AuthenticationMethods to my sshd_config file, sshd refuses to run

This is the line I've been adding to /etc/ssh/sshd_config:

AuthenticationMethods publickey,keyboard-interactive

The sshd will close shortly after starting once I add this. Any idea why? any help on this would be greatly appreciated.

---

### Post by linuxtechguy on 2013-06-18
What error do you see in the logs?

---

### Post by wlraider70 on 2013-06-21
Try this article.

[http://www.howtogeek.com/121650/how-to-secure-ssh-with-google-authenticators-two-factor-authentication/](http://www.howtogeek.com/121650/how-to-secure-ssh-with-google-authenticators-two-factor-authentication/)

---

### Post by 3L33T on 2013-06-21
Niiiiice!!!  I didnt know about this until now.

Gotta love this forum! ;)

---

### Post by Blazr on 2013-06-21
Thanks for the links guys, but I think I didn't explain myself properly.

I have Google Authenticator working on SSH, the problem is it only works when you login via password, when you use a public key it overrides Google authenticator. I have read that OpenSSH 6.2 has a new option in the config, AuthenticationMethods, to fix this (I will post a link later), but I am unable to get it to work.

I will also post the logs later but last time I didn't see anything interesting in there that could help.

---

### Post by Lars Noodén on 2013-06-22
How are you doing the configuration, in /etc/pam.d/ somewhere or in /etc/ssh/sshd_confg?

---

### Post by einar2 on 2013-10-06
I have written a blog post about setting three-factor authentication up here: [http://herehttp://turquoiseliquorice.wordpress.com/2013/10/05/three-factor-authentication-with-openssh-google-authenticator-and-password/](http://herehttp://turquoiseliquorice.wordpress.com/2013/10/05/three-factor-authentication-with-openssh-google-authenticator-and-password/)

It seems that your PAM module is not correctly configured.

Try change:

AuthenticationMethods publickey,keyboard-interactive

to:

AuthenticationMethods publickey,password

and see if that works as expected. That will confirm the issue is with PAM.

Which guide have you followed to set up Google Authenticator?

---

