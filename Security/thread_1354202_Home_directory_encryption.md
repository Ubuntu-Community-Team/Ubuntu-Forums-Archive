---
title: "Home directory encryption"
date: 2009-12-13
forum: Security
---

### Post by User3k on 2009-12-13
I noticed that Xubuntu does not, or maybe I missed it, encrypt the home directory when installed? If I didn't miss that during the install, is there a reason why Xubuntu doesn't do this?

I would like to encrypt my whole /home/user directory. I am not really sure how to do this so it would be set up like it was when I had Ubuntu 9.10 installed. Any ideas/pointers?

---

### Post by bodhi.zazen on 2009-12-13
I believe you missed that option when you installed.

Here is a screen shot (from Ubuntu, but I believe it is the same with xubuntu)

[http://www.ubuntugeek.com/encrypted-home-now-offerred-at-installation.html](http://www.ubuntugeek.com/encrypted-home-now-offerred-at-installation.html)

---

### Post by User3k on 2009-12-13
> **bodhi.zazen said:**
> I believe you missed that option when you installed.

Here is a screen shot (from Ubuntu, but I believe it is the same with xubuntu)

[http://www.ubuntugeek.com/encrypted-home-now-offerred-at-installation.html](http://www.ubuntugeek.com/encrypted-home-now-offerred-at-installation.html)


Yeah I think I did to. It didn't make sense that Xubuntu didn't have it, but I wanted to make sure it wasn't an XFCE issue and that is why it was left out.

Is there anyway to fix this now? I never encrypted my home directory before, want to give it a try and see how it goes for future use.

---

### Post by Agent ME on 2009-12-13
You'll need the [ecryptfs-utils](apt:ecryptfs-utils) package for this.

To add an encrypted "Private" folder to your user account, the command "ecryptfs-setup-private" will set this up.

To create a new user that is encrypted (instead of just having an encrypted Private folder, the whole /home/*username*/ directory is encrypted; this is what the option in the installer does), the command "sudo adduser --encrypt-home *username*" will do.

---

### Post by User3k on 2009-12-13
Great. Thanks.

---

