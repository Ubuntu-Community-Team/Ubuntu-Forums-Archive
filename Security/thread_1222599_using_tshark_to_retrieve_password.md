---
title: "using tshark to retrieve password?"
date: 2009-07-25
forum: Security
---

### Post by SlugSlug on 2009-07-25
I set up a last.fm account a while back for exaile.
Now I want to log in to it, but it seems I must have used some random password and a 10min mail account.

My username (what i want to keep) and password are stored in Exaile so I was wondering if there was a way to use tshark to retrieve it as Exile communicates?

I've tried Exaile config and its encrypted

---

### Post by grayn0de on 2009-07-26
I am guessing you mean having Exaile communicate with Last.fm's site via SSL and all that.

In that case, try using ettercap (for packet sniffing) and sslstrip.py (a python script that strips ssl encapsulation off of traffic on your designated network interface. You can find a video demonstrating sslstrip on the Pauldotcom Security Weekly website, here: [http://pauldotcom.com/2009/05/cool-penetration-tests-and-use.html](http://pauldotcom.com/2009/05/cool-penetration-tests-and-use.html)

Also, you'll find sslstrip here: [http://www.thoughtcrime.org/software/sslstrip/](http://www.thoughtcrime.org/software/sslstrip/)

Ettercap can be installed via apt-get. Learn to use it via the man pages: 'man ettercap'.

---

