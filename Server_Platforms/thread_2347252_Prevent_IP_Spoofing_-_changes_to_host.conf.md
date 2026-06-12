---
title: "Prevent IP Spoofing - changes to host.conf"
date: 2016-12-22
forum: Server Platforms
---

### Post by bearlake on 2016-12-22
Hi good folks,

Reading on the Internet about the above subject and can't get a clear answer or does it matter?

Every read me is one way or the other.

What's the difference?



file: host.conf

order bind,hosts
nospoof on

or

order hosts,bind
nospoof on


Thanks

---

### Post by TheFu on 2016-12-23
nsswitch.conf replaced the hosts.conf almost 30 years ago.  I have **never** ever seen the hosts.conf file used anywhere in my career. Not once.  

bind probably refers to DNS.  hosts probably refers to /etc/hosts.  The order determines which is checked first. Normally, hosts would be first. No idea what no-spoof means in this context. I'd check the manpage.
```
       nospoof
              Valid values are on and off.  If set to on, the resolv+  library
              will  attempt  to prevent hostname spoofing to enhance the secu&#8208;
              rity of rlogin and rsh.  It works as follows: after performing a
              host  address lookup, resolv+ will perform a hostname lookup for
              that address.  If the two hostnames do not match, the query will
              fail.  The default value is off.

```
The references to rsh/rlogin should be enough to set the time for this file. ssh replaced rsh around 1994-ish. manpages are a wonderful thing.

I have doubts that the code has been maintained. I don't know anything, so I'm probably wrong. That has never stopped me from posting here before. ;)

---

### Post by bearlake on 2016-12-23
Hi TheFu and many thanks.

This is where I found what info I could on the Nospoof on and so on.

In the write up it's number 7 and 8.

Found a total of 3 guides that mention the same but the order is different.

[HTML]https://www.thefanclub.co.za/how-to/how-secure-ubuntu-1604-lts-server-part-1-basics[/HTML]

---

### Post by TheFu on 2016-12-24
Not a bad guide. A little old-school stuff and some new stuff.  Much of it has the current defaults for the OS, so no changes are needed. Having a list of settings without explanation isn't all that useful.  What happens when the way to accomplish those things is removed or changed?

If you want more, get Bob Toxen's book. He's big on using the firewall to slow down the bad guys.

[http://blog.jdpfu.com/2016/10/04/lamp-server-security](http://blog.jdpfu.com/2016/10/04/lamp-server-security) has my take.  For example, I don't run apache for the world and lock down access to any services for anyone who doesn't specifically need access.  I use a reverse proxy that does to filtering to block unreasonable requests from "bad guys."

I'd disable IPv6 unless you are positive you need it. If not, is it just another attack vector that most people aren't prepared to handle. Teredo tunnels can be really bad for LAN security.

---

### Post by bearlake on 2016-12-24
> **TheFu said:**
> Not a bad guide. A little old-school stuff and some new stuff.  Much of it has the current defaults for the OS, so no changes are needed. Having a list of settings without explanation isn't all that useful.  What happens when the way to accomplish those things is removed or changed?

If you want more, get Bob Toxen's book. He's big on using the firewall to slow down the bad guys.

[http://blog.jdpfu.com/2016/10/04/lamp-server-security](http://blog.jdpfu.com/2016/10/04/lamp-server-security) has my take.  For example, I don't run apache for the world and lock down access to any services for anyone who doesn't specifically need access.  I use a reverse proxy that does to filtering to block unreasonable requests from "bad guys."

I'd disable IPv6 unless you are positive you need it. If not, is it just another attack vector that most people aren't prepared to handle. Teredo tunnels can be really bad for LAN security.

Many thanks again.

I bookmarked Bob Toxen's book and will spend time with it.

IPv6 was the first thing disabled on setup.

Using a very high port for SSH which hasn't seen any attacks yet but from myself.
Fail2ban caught all my attacks so far and emailed me with the bans info.

Added a VPN to the server and client.

Guess this thread can be closed and marked as solved.

---

