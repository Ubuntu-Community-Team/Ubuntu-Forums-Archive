---
title: "ssh login failure logging question"
date: 2011-10-07
forum: Security
---

### Post by Cyked on 2011-10-07
Using SSH key Auth. If I login with a non-existent userid ID it logs the ID and IP in authlog. If I do the same with a valid ID and bad PW it logs nothing. Shouldn't it log this???

---

### Post by jramshu on 2011-10-07
Should log it as an authentication failure. 

Best to disable password authentication and set a password for the key itself. JMO

---

### Post by Dangertux on 2011-10-08
It does log it it should say failed authentication for user whoever in auth.log

It may also say failed to provide public key.

---

### Post by Lars Noodén on 2011-10-09
Which version of SSH is it?

---

### Post by azmyth on 2011-10-09
I tried it on my system and I noticed the same thing as you. I suspect it has to do with the level of logging set in the /etc/ssh/sshd_config file.

---

### Post by Dangertux on 2011-10-09
If you need to increase SSH logging you can change the following in /etc/ssh/sshd_config

```

LogLevel INFO

```

to

```

LogLevel VERBOSE

```

other possible values

WARNING - Log only on Warnings
ERROR - Log on errors
DEBUG - Considerably more output than VERBOSE
DEBUG2 - More than DEBUG
DEBUG3 - The most logged , this may slow down your system considerably.

---

### Post by Cyked on 2011-10-11
Weird. I didn't know this posted. I was posting on my phone, got a bunch of DB errors from the site so I didn't think it went through.

I checked after I got home, and what IS happening is if its a failed attempt WITH the actual key it will  only log failures in authlog with bad user IDs.  I assume this is because why would someone else have your key.  I'll check the logging settings out of curiosity under sshd_config.

---

