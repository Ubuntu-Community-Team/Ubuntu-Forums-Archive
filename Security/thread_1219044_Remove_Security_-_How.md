---
title: "Remove Security - How?"
date: 2009-07-21
forum: Security
---

### Post by Quarkrad on 2009-07-21
Apologies if this has come up before - I'm running 9.04 (clean install - no upgrade).  From what I have read - there is a bug re security updates with 9.04; my update manager keeps giving me the message:

**Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/Release](http://security.ubuntu.com/ubuntu/dists/jaunty-security/Release)  Unable to find expected entry  multivers/source/Sources in Meta-index file (malformed Release file?)**

Is there something I can remove to stop this happening?

---

### Post by bodhi.zazen on 2009-07-21
You do not want to remove that, you want to correct the error.

Here are the sources from jaunty, you do not need the deb-src unless you compire from source.

Edit with :

```
gksu gedit /etc/apt/sources.list
```

```
deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security universe
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse
```

---

### Post by Quarkrad on 2009-07-21
Fantastic - all working OK.  Thank you very much for your help - appreciated.  :)

---

