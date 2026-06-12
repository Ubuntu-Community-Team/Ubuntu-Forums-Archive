---
title: "x2go - over the Internet"
date: 2016-11-29
forum: Server Platforms
---

### Post by bearlake on 2016-11-29
Hi good folks.

Very new to servers but moving along great so far.

Setup one server for testing locally as a file server using SSH key with no issues.

Set up over again but wanted to try X2GO locally with SSH key but also wanted to add it to the Internet for testing.

All worked great over port 222 using SSH key and not password over the Internet.

So far port 222 is the only open port on my router for testing.

What measures can/should I take to make sure that security around my SSH server is absolutely impermeable?

Thanks

---

### Post by TheFu on 2016-11-29
No such thing as **absolutely impermeable**.  If you need that, turn the machine off, unplug it from the power, network, monitor, keyboard. Don't look at it directly either. ;)

Of course, that isn't really very useful, so some simple steps to provide _*some*_ level of security are probably good enough. Then there are harder steps to provide more security and less convenience.  Lastly there are much harder steps to provide even higher levels of protection that very few people will actually want to deploy.  Only you can decide what is needed.

So .... let's start by describing each of the ways to secure any service and ssh in specifics.

* Only allow access to the port from known remote locations. Block everything by default and allow the specific locations you know are needed.  This is normal firewall practice and should be part of every network architecture.  Do people from Russia or USA or Brazil or China or UK need access to your ssh port? Block them all and only allow the specific IPs you actually visit access.  ufw, iptables or any front-end to the built-in firewall can do this.

* Prevent brute force password attacks. People will attempt logins as many times as you allow.  There are tools to watch these failed attempts and block those IPs using the firewall. After a configured period of time, the firewall opens that port again, so they can try again.  DenyHosts and fail2ban are tools that do this.  fail2ban is what I use, but for a few months, a few years ago, it had a bug and didn't block anyone.

* Use a non-standard port.  222/tcp is a non-standard port, but still below 1024, so it requires root start the process.  A higher port would be slightly better (not sure how much better).  By running on a non-standard port, 99% of all attacks are prevented, but people do scan all the ports below 10,000 all the time and those scans will see the ssh running on 222/tcp.  50,000+ might be a better choice?  I dunno.  I use higher ports.

* Never use passwords. Use 2-4K ssh-keys.  Make those keys have long passphrases to access.  Using 2FA might be smart to unlock the keys too.  That can be as easy as adding a short (8 characters) to a generated HW token, like a yubikey.  The most secure password is one you don't actually know.

* Choose strong ciphers. Block weak ones.

* Never allow remote root access.  There is a setting to prevent ssh from allowing root@ at all.

* Limit the userids that are allowed to ssh in.

* Rate limit connections.

* Use strange userids. If the only userid allowed to ssh in is rwer8434923eew, it is doubtful anyone will guess that.  This is advice I give to people stuck with stupid, short, banking credentials too (8 characters numbers and alphabet).  The userid can usually be 50 characters.  It isn't like we'll ever have to actually type it in.  john, bob, pete, ann, mary, thefu, probably aren't smart userids.  kgewids842327854y would be a better choice, right?  Well, it was until I posted it here.  Never start any userid/password with a capitol and never end them with an 's' or punctuation or 2 digits that look like a month or year.

* Stay patched. From time to time, there are issues with ssh and sshd or some libraries used to build it.

* Have versioned backups of the system.  Versioned, backups, are my #1 security technique.  Keeping 30-120 days of daily backups means never having to say "that file is gone forever." Priceless.
 
* Monitor the log files, so you know if things are having issues.

* Use remote logging, not local.  If someone does get in, they will clean up the log files for all the *bad things* they did. If remote logging is used, they'd have to hack 2 systems.

* Port knocking.  You can look that up.

* Validate that things actually work the way you expect.  Sometimes things we configure don't actually work. That's useless. Test it.

More answers.
* [https://askubuntu.com/questions/2271/how-to-harden-an-ssh-server](https://askubuntu.com/questions/2271/how-to-harden-an-ssh-server)
* [http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures](http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures)
* Generic server security: [http://blog.jdpfu.com/2016/10/04/lamp-server-security](http://blog.jdpfu.com/2016/10/04/lamp-server-security)

---

### Post by bearlake on 2016-11-29
Many Thanks @ TheFu.

Never use passwords - already had that done.

Never allow remote root access - already had that done.

Limit the userids that are allowed to ssh in - need to do that.

The rest I will work on.

Many Thanks again.

---

