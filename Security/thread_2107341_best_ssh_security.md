---
title: "best ssh security"
date: 2013-01-21
forum: Security
---

### Post by wlraider70 on 2013-01-21
I've been using pubkeys for ssh security. 

The other day i was setting up a new server and I used Google authentication, the one with the 6 digit changing code. I also still have the password enabled. 

So whats best

pubkeys or authenticator or authenticator and password?

---

### Post by MadsRC on 2013-01-22
Oh my, I didn't know you could use the Authenticator with other services than GMail.
I use it for my Google Account and I'm extremely happy with it.

However, I'm a little skeptical about it though. I know the authenticator i Open Source, but since I haven't reviewed the code or read about anyone that have, I'd have to do a little more research before I decide upon that.

I guess it's up to how much you trust Google ;)

Keys are still my preferred way of doing secure logins. One key for every machine I use, with a strong password, plus a special key I keep on me, encrypted and with a extra strong passphrase for emergency access. If any keys are lost, simply remove the key from authorized_keys...

Only problem is though, that ssh-copy-id  host@network is problematic if logins are keys only, since I haven't found a way to make the ssh-copy-id connection using an existing key...

---

### Post by wlraider70 on 2013-01-22
This is the guide I used 

[http://www.howtogeek.com/121650/how-to-secure-ssh-with-google-authenticators-two-factor-authentication/](http://www.howtogeek.com/121650/how-to-secure-ssh-with-google-authenticators-two-factor-authentication/)

All the crypto is done on your server.

---

### Post by CharlesA on 2013-01-22
> **wlraider70 said:**
> This is the guide I used 

[http://www.howtogeek.com/121650/how-to-secure-ssh-with-google-authenticators-two-factor-authentication/](http://www.howtogeek.com/121650/how-to-secure-ssh-with-google-authenticators-two-factor-authentication/)

All the crypto is done on your server.
Wow. Thanks for the link.

---

### Post by donniezazen on 2013-01-26
> **wlraider70 said:**
> This is the guide I used 

[http://www.howtogeek.com/121650/how-to-secure-ssh-with-google-authenticators-two-factor-authentication/](http://www.howtogeek.com/121650/how-to-secure-ssh-with-google-authenticators-two-factor-authentication/)

All the crypto is done on your server.

Thanks setting it up now.

---

### Post by mazato on 2013-02-19
guys, I used the link that wlraider70 posted, but i can get through the passwords. everything sets up fine though.

---

### Post by wlraider70 on 2013-02-19
What version of Ubuntu are you using?
Are you saying you can't get the regular user password to work out the Google code won't work?

---

