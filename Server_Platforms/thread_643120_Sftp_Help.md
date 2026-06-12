---
title: "Sftp Help"
date: 2007-12-17
forum: Server Platforms
---

### Post by macmichael01 on 2007-12-17
Hello,
I would like to be able to sftp but can't seem to get it to work with a client. I am trying to use cyber duck for mac which has an sftp option. I noticed that I CAN login via the command line through sftp no problem. any clue as to what is going wrong?

---

### Post by cdenley on 2007-12-17
Can you ping your server? I had a similar problem with a windows client over the internet, and I believe it was because my router was blocking pings.

---

### Post by macmichael01 on 2007-12-17
I checked my router and I did not have WAN Ping Response enabled, so I enable. I guess I am not really sure why this would make a difference if this is enabled. Here is the error that I am still getting when I try to connect via CyberDuck. 

I/O Error: Connection failed.
sftp://me@somedomain.com:22
Invalid Perm Structure '-----BEGIN...' missing

I hope this is not an obvious error that I am over looking.

---

### Post by macmichael01 on 2007-12-17
opps solved my own problem. I was using the wrong key file. Thanks for your help

---

