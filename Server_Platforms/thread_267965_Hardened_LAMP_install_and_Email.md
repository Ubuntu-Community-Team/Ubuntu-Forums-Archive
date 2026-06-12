---
title: "Hardened LAMP install and Email"
date: 2006-09-29
forum: Server Platforms
---

### Post by wvrent on 2006-09-29
I've been hardening a LAMP stack install on 6.06 LTS using the following [guide]("http://www.freesoftwaremagazine.com/articles/hardening_linux?page=0%2C0")  with pretty good success so far.  However the Fcheck script the use is intend to email the system admin in the event of a file change.  Thats when I discovered that the LAMP install doesn't have a mail package.  I could always install Postfix, but is that overkill?  I never want to recieve mail from this server, I just want to send out.

Without adding unnessesary complexity to the stack, what are my best options?

---

### Post by yellowtip on 2006-10-02
It's a good question!  I toowould like to know the best way to setup a simple/secure smtp server on my LAMP server.

Anybody?

---

### Post by sonic2000gr on 2006-10-02
I would suggest you install postfix. I am using it for quite a few months now with zero problems.

For an installation walkthrough I suggest you read [this excellent guide]("http://www.howtoforge.org/perfect_setup_debian_sarge"). Postfix install starts on page 4.

(Actually the steps involved are for Debian 3.1 but very little will be different if at all)

---

