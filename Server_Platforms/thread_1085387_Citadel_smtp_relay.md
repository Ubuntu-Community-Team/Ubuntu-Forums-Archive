---
title: "Citadel smtp relay"
date: 2009-03-03
forum: Server Platforms
---

### Post by peterroots on 2009-03-03
I have just installed Citadel on a Kubuntu8.04 machine and it seems to be working ok once I got the hang of it.
Our organisation has email addresses set up on a server remote from us and owned by our parent organization that owns and manages this and our domain name.
We have a fixed IP for out network but it is not linked to our domain and can not be so when I try to use citadel to send mail the receiving mail servers reject it as it is not coming from a valid server.
From what I have read I need to relay smpt - I can not use smart hosts in citadel as our parent oranisations mail system (which I would like to relay through) requires CRAM-MD5 authorization, or so it says when I telnet in.
I installed esmtp (as suggested in the citadel docs) but can't figure out how to a) tell citadel to send its external mail though it or b) how to make esmtp use cram-md5.
I have looked at postfix but so many posts suggest it could take months to figure out I don't fancy getting bogged down with this.
This is my first time trying to mess with mail servers and I have been thoroughly confused, so far, with what I have read.
I am assuming I can collect mail into citadel on an account by account basis by setting them to pickup it up with pop3, though my fist attempt failed I expect it is just something silly I did so it is back to tinkering on that.
Any hints on how to to the rely, or where to look for understandable pointers would be much appreciated.
Thanks

---

