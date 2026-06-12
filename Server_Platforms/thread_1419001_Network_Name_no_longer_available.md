---
title: "Network Name no longer available"
date: 2010-03-01
forum: Server Platforms
---

### Post by dhillis on 2010-03-01
For those of you who have been following.  I now have the server at the school up and running.  Myself as well as one other teacher have no problem finding the server, connecting to it, and even transferring data to and from. 

I however have one other teacher that get an error when trying to connect.

Says that the server name is no longer available.  

What should I be looking at to fix this?

---

### Post by ICEB3AR on 2010-03-01
Maybe a bit more Information - for those who have not been following your posts yet - are appropriate ;)

---

### Post by dhillis on 2010-03-01
like?...lol...not trying to be rude but what other information do you need?  I am a complete noob and have taken about 2 weeks (during breaks at work) to get this running.....


here is my smb.conf file.

---

### Post by BobVila on 2010-03-01
> **dhillis said:**
> like?...lol...not trying to be rude but what other information do you need?  I am a complete noob and have taken about 2 weeks (during breaks at work) to get this running.....


here is my smb.conf file.

Also not trying to be rude, but taking the ten seconds to describe your setup might be helpful.

For example...
Are you trying to hit this server by fqdn or ip?
Where's your DHCP server? 
Is there a DNS entry for the box?
Which user is having trouble?
Anything special about his/her setup?
Can he ping the server?
Can he ssh to it?
Is there anything strange in /var/log/auth.log?

Some of the answers to these questions might turn out to be irrelevant, but you'll find that the more background you can provide, the faster we'll turn around a good answer for you.

---

### Post by Iowan on 2010-03-01
> **dhillis said:**
> like?...lol...not trying to be rude but what other information do you need? A link to the previous thread(s) might be helpful - although I found it [here]("http://ubuntuforums.org/showthread.php?t=1411283")...
Does the server have a static address or is it DHCP? I'm still a bit confused about how Winbind comes into play - but thought I'd ask if the server has it installed.

---

