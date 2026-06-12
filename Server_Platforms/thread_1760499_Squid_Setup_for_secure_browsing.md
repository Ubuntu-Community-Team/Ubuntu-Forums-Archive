---
title: "Squid Setup for secure browsing"
date: 2011-05-17
forum: Server Platforms
---

### Post by PrestonD on 2011-05-17
Hi all, long time 'lurker' first time poster!

I would like to use my Ubuntu server machine as a proxy so I can browse a little more securely/privately while I am traveling.  I connect to a lot of open Wi-FI networks.

I have Squid setup on an old laptop running Ubuntu Server 10.10 at home, and the main machine I will be using to connect to the proxy is a computer running Windows Vista.

I am able to connect and use the Ubuntu Server machine as a proxy while traveling with the squid config file modified with http access set to 'allow all'.  

Obviously this isn't the ideal setting.  After lots of reading and Googling I can't figure out how to allow only my Vista laptop to use the proxy.  I'm a little lost with the ACL settings required.  

Any help would be greatly appreciated!

Preston

---

### Post by PrestonD on 2011-05-18
Follow up...

Am I on the right track with Squid?  Or would it be better to use PuTTY and openSSH as described here:

[http://www.techrepublic.com/blog/security/use-putty-as-a-secure-proxy-on-windows/421](http://www.techrepublic.com/blog/security/use-putty-as-a-secure-proxy-on-windows/421)

---

### Post by PrestonD on 2011-06-11
bump :(

---

### Post by Lars Noodén on 2011-06-11
You can do that without Squid.  

If you just want to surf via proxy, then you can do something similar faster and easier with SSH.  Do this by connecting to your home machine with the -D option from your traveling machine. Then on your traveling machine, connect to the port specified by -D but on your local host.

e.g.

```

ssh -D 5012 server.example.com

```

Then on the the local machine, specify for Firefox to connect to the SOCKS proxy at 127.0.0.1 port 5012.

---

### Post by moonpup on 2011-06-11
+1 for that setup! I tunnel all my browsing over ssh through my home server in that manner. In fact, I take it one step further and configure Firefox to do DNS lookups on the remote side of the tunnel to further hide where I browse to when using other networks.

---

### Post by PrestonD on 2011-06-13
Thanks for the replies.  The more I read about squid, I was beginning to think that it was not exactly what I wanted.  Thanks for the affirmation.


I was able to set up the tunnel and browse as described here:  [http://www.techrepublic.com/blog/security/use-putty-as-a-secure-proxy-on-windows/421](http://www.techrepublic.com/blog/security/use-putty-as-a-secure-proxy-on-windows/421)


Lars, you lost me a little bit with the -D option.   I see that it means to 'bind the address : port', but not really sure what that does for my connection.

I have been using PuTTY on my traveling machine (Windows Vista).  How do I (or can I) specify that option?  

Moonpup, good stuff about the remote DNS lookups, I'll have to change that one in Firefox.

Having a blast with my server and the command line.  I've played with Ubuntu (Desktop) a lot, but this is my first venture into the command line only world.   Kind of rewarding :D!

---

### Post by Lars Noodén on 2011-06-13
> **PrestonD said:**
> Lars, you lost me a little bit with the -D option.   I see that it means to 'bind the address : port', but not really sure what that does for my connection.

I have been using PuTTY on my traveling machine (Windows Vista).  How do I (or can I) specify that option? !

You can do a [SOCKS proxy on PuTTy](http://www.virtualroadside.com/blog/index.php/2007/04/12/dynamic-socks-proxy-using-putty/).

I was (am) expecting Ubuntu on the desktop since it's so much easier to work with.  The -D option means that you are creating a SOCKS proxy that can be accessed on the local machine.

---

### Post by PrestonD on 2011-06-17
Got it working, thanks for the advice!

---

