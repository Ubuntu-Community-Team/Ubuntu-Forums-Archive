---
title: "Protecting Ubuntu for demonstration purposes"
date: 2005-07-29
forum: Server Platforms
---

### Post by watje on 2005-07-29
Hi,

Next month we're placing a computer with Ubuntu in the local library.
It's for demonstration purposes only.
The computer must be protected against vandalism.

This is my idea (correct me if I'm wrong or if you have other suggestions):

chown -R root:root /; chmod -R 600 /;
chmod -R 555 /bin /usr/bin /usr/local/bin;

The computer must promt for a password when someone's trying to shut it down.
I don't exectly know how to do this so please help me with this.

Does someone know other things to make the computer more 'safe'?
Thank you in advance!

---

### Post by Sam on 2005-07-29
[UbuntuGuide - Security](http://ubuntuguide.org/#security) should be a good start.

---

