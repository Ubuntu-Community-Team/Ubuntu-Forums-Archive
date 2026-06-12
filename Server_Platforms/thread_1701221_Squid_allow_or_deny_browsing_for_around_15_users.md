---
title: "Squid allow or deny browsing for around 15 users"
date: 2011-03-06
forum: Server Platforms
---

### Post by Demented ZA on 2011-03-06
I have searched the internet and I found A LOT of information regarding squid, but its either very simplistic (e.g caching server) or extremely advanced and daunting, using words like accelerator and reverse proxying that scare me. 

I can't find anything for my needs, although I have once before and forgot to bookmark it. I would like to get an understanding of squid, and I'm prepared to not just copy and paste.

I'm running a mail server and a two interface firewall system. I want to extend it by using squid to:

[LIST=1]
[*]Cache web content to speed things up and
[*]Block or Allow users to browse depedning on authentication for Users (staff) and IPs  for Managers (Managers should be unrestricted, and don't want to be bothered with Username/Passowrd nags).
[/LIST]
I have read a guide before that allows me to do the above, and it explained it fairly well, but kept it simple. I thought I bookmarked it, but i guess I didn't :-(

I have already set up squid to do direct proxying for my local network (10.10.10.0/24) as per the [Ubuntu community guide]("https://help.ubuntu.com/community/Squid"). But I now need to setup ACLs.

Thank you in advance.

---

### Post by Demented ZA on 2011-03-06
In short, all I want is for a user to enter his username and password in order to browse.

As for managers, I can just set up firewall rules, so managers do not have to go through the proxy server. There are two managers.

---

