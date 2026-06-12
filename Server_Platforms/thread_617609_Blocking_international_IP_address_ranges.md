---
title: "Blocking international IP address ranges"
date: 2007-11-19
forum: Server Platforms
---

### Post by fmriguy on 2007-11-19
Hi all,

I run a very basic server that only offers up ssh/sftp connectivity.  My only port forwarded through my router is port 22.  However, I've been noticing a lot of authentication failures coming from IP's in China, Japan, etc. and given that I don't have any users there, I'm assuming these must be unfriendly types trying to gain access to my server.

Is there a way to simply block access to the server from all IP's outside of North America.  Of course this is kind of a kludge since smart folks could just use a proxy, but it would at least limit a bit of the traffic.  Also, other alternative ideas are welcome.

I'm somewhat new to linux, so I think I might need to use iptables, but not sure what steps to take?  Any help would be much appreciated.

Thanks!

For reference, I'm running Feisty Fawn...

---

### Post by Mithrilhall on 2007-11-19
I would suggest trying: fail2ban

[http://www.fail2ban.org/wiki/index.php/Main_Page](http://www.fail2ban.org/wiki/index.php/Main_Page)

It should be in the repositories.

```

sudo apt-get install fail2ban

```

That should install it and get it running for you.

---

### Post by MJN on 2007-11-19
Indeed, chasing IP allocations based on supposed geographic location is the wrong way to go. Besides which there are more than enough compromised machines in the US that you may as well cater for with the same solution.

Denyhosts is an alternative to fail2ban, however having usedboth extensively I prefer the latter. Search the archives also for means of achieving a similar effect with iptables (mainly using triggered rate limiting).

Start with fail2ban for an immediate out-of-the-box solution then look at alternatives if you're still interested.

Mathew

---

### Post by fmriguy on 2007-11-19
Thanks for the quick responses.  Turns out I already had fail2ban installed but didn't realize it!  I went into the configuration and changed the max retry to 3 rather than the default value of 6.  Hopefully that will kill the connections more quickly.  Thanks!

---

