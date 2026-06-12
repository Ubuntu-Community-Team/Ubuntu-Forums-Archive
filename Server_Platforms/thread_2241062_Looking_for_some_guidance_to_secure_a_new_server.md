---
title: "Looking for some guidance to secure a new server"
date: 2014-08-23
forum: Server Platforms
---

### Post by Yves_Dawson on 2014-08-23
Hi,

I'm setting up a new server that will be accessible from the outside and I'm really a newbie when it comes to securing it against attacks and hackers.

I've heard about ConfigServer Firewall (CSF) but on their website Ubuntu 14 is not listed as Supported and tested.

I've also looked at a Metasploit tutorial ([http://backtracktutorials.com/metasploit-tutorial/](http://backtracktutorials.com/metasploit-tutorial/)) but not tested it yet.

The server will have web, mail (with virtual domains), DNS and MySql services.

Right now I'm some kind of lost about securing all this.

So I'd like some advises about the path to follow. And I'd like to know if installing CFS on Ubuntu 14 is safe and if the Metasploit tutorial I linked will let me really test if my server is secure.

Thanks

---

### Post by sandyd on 2014-08-25
> **Yves_Dawson said:**
> Hi,

I'm setting up a new server that will be accessible from the outside and I'm really a newbie when it comes to securing it against attacks and hackers.

I've heard about ConfigServer Firewall (CSF) but on their website Ubuntu 14 is not listed as Supported and tested.

I've also looked at a Metasploit tutorial ([http://backtracktutorials.com/metasploit-tutorial/](http://backtracktutorials.com/metasploit-tutorial/)) but not tested it yet.

The server will have web, mail (with virtual domains), DNS and MySql services.

Right now I'm some kind of lost about securing all this.

So I'd like some advises about the path to follow. And I'd like to know if installing CFS on Ubuntu 14 is safe and if the Metasploit tutorial I linked will let me really test if my server is secure.

Thanks
CSF works fine on 14.04 - I have it running on a few servers.

Note that we do not support cracking/hacking/etc on these forums.

---

### Post by Yves_Dawson on 2014-08-25
> **sandyd said:**
> CSF works fine on 14.04 - I have it running on a few servers.

Note that we do not support cracking/hacking/etc on these forums.


Thanks for your reply, glad to hear that CFS works on 14.04.

And I guess that by saying that you don't support cracking/hacking you're talking about testing my server security...

So maybe a link to a good tutorial on securing my Ubuntu server or advises on anything that CFS won't cover regarding protection (if there's anything!) could be a good counter part.

---

### Post by cj13579 on 2014-08-26
Suggest you also look at putting denyhosts on there. Its available in the repos.

---

