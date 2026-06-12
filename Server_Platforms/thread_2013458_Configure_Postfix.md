---
title: "Configure Postfix"
date: 2012-06-30
forum: Server Platforms
---

### Post by computerfox on 2012-06-30
Hello all,

I'm back on this topic again because I realized it's necessary for me to set this up.

Some basics, I use webmin for most of my management.  I opened up ports 110 and 25, even though all I want to do is send mail at least via PHP.  This is vital for a number of my scripts.  In my host file, I have my public IP address as well as my internal address and the loopback.

My goal: to be able to send mail via PHP from hosting.domain.com, which is a public subdomain, not an MX, not sure if that has something to do with it.

Any ideas?  I would like to know the best/simplest way to properly set up Postfix on my server.

---

