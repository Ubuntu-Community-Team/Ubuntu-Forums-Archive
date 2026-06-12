---
title: "Ports blocked, can't use SSH tunneling."
date: 2005-10-27
forum: Server Platforms
---

### Post by ShawnMilo on 2005-10-27
I've been trying to set up squid so I can use my home machine as a proxy server. Then I can ssh from work and get around blocked ports/content.

The problem is that my Ubuntu Server 5.10 box rejects all attempts at port forwarding. I never had this problem with vanilla Debian, but I am stuck here.

I checked for iptables, but I don't see it running in 'ps aux' and I don't see any config file. I did a grep across the entire /var/log directory but don't see any logs reporting that any firewall or other app successfully blocked the port.

I know port 443 works fine, because I have sshd configured to use that port, and I connect just fine, only minus the port forwarding.

I tried Google searching and searching these forums. I've now spent a couple of hours on this and I'm giving up and asking for help.

I've tried ports 3128 and 8888 so far, but to no avail. My ssh client (putty) shows that the attempts to forward are being rejected by my Ubuntu box.

Thanks,
Shawn

---

### Post by cydizen on 2005-10-27
try running 

```
sudo /sbin/iptables -L
```

this will tell you if iptables is blocking anything.

If you are using a default install, then it should not be stoping any traffic.  Are you running squid or anything like that?

Can you telnet to any of those ports?

---

### Post by ShawnMilo on 2005-10-27
Here's what I get when I run that command:

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination        



Yes, I have squid running -- that's what I'm trying to use as a proxy server. Squid appears to be running fine -- I've run it with -d and it never receives a connection.

What next?

Thanks,
Shawn

---

### Post by cydizen on 2005-10-27
squid blocks access by default, you have to add yourself to the squid access list in the .conf.   Also, squid uses port 3128 by default, which (i think) most companies block.

---

### Post by cydizen on 2005-10-27
Sorry, you also have to look for ALLOW / DENY in there to...

---

### Post by ShawnMilo on 2005-10-27
I understand that, and I've dealt with squid and the squid.conf file before. That's not the issue. The problem is that Ubuntu Server is rejecting the port forwarding from my ssh session. Please read my original post.

I also know about blocked ports -- that's why I'm trying to use an ssh tunnel, as specified in the original post.

Milo

---

### Post by cydizen on 2005-10-27
I am just going to throw something random out there... do you have a router coming into your home box?

---

### Post by cydizen on 2005-10-27
Oh hey, sorry about the quick scan of the post. My bad dude. I was at work and  I guess I wasn't totally focused.  Anyway, lets what we can do to get you around your problem.

---

### Post by ShawnMilo on 2005-10-28
Yes, I have a router at home. I used to have static IPs.

However, this is not the problem. Through the router I have opened port 443 to a specific machine, and set sshd to listen at 443 instead of 22. This is working, because I am able to open an ssh connection to the machine.

The router can have nothing to do with my problem because that's the whole point of using an ssh tunnel. For that matter, at work my firewall only allows 80 and 443 to get through, so my home router is a moot point.

The question is: Why is Ubuntu rejecting every attempt by my ssh client to open an ssh tunnel by forwarding a local port to it?

An example from the command line would be:

ssh -L 3128:mymachine.net:3128 mymachine.net

This should work because I'm not using -R, which would potentially conflict with the server if it was a reserved port, the port number is high enough not to be a port protected by the server, and I've done it before with Debian.

I hope this is enough detail. Please feel free to ask any more questions or to make any more suggestions.

Milo

---

### Post by ShawnMilo on 2005-10-28
Note: please also read my post immediately above this one, since there were no new replies before I posted this one.

Further info: When I make the ssh connection, everything is fine. However, when I change my browser to use localhost port 888 as a proxy server, then actually attempt to go to any page, the following two things happen:

1. The browser returns "the document contains no data."

2. My ssh client returns an error line stating that the port forwarding was rejected by the server.

Throughout this, squid shows no signs of receiving the page request. Something in Ubuntu Server 5.10 is blocking the port.

I've tried this with ports 3128 and 8888, and yes I modified the squid.conf to reflect this.

Thanks again,
Milo

---

### Post by ShawnMilo on 2005-11-02
Hi. It's another week, and this thread has fallen down out of site and lost. I'm posting to bring it back up to the attention of you five-cuppers, and to see if anyone knows the solution.

Please check all my posts before replying -- I've made many statements which will answer most of the basic background questions.

If I don't get this resolved soon, I'm going to be forced to just switch back to Debian. That would be a shame, because I'm certain that the solution is incredibly simple, just incredibly non-obvious.

Thanks, all!

Milo

---

### Post by LordHunter317 on 2005-11-02
[QUOTE=ShawnMilo]I've been trying to set up squid so I can use my home machine as a proxy server. Then I can ssh from work and get around blocked ports/content.[/quote]That likely won't work... I'm not sure what you're trying to do, but I don't see how squid is part of the solution.

You just want to use SSH with dynamic port fowarding -- SSH will automatically become a SOCKS5 proxy.  Point whatever applications you want to free through the proxy.

And if you get fired for doing this, don't say you weren't warned.

> I checked for iptables, but I don't see it running in 'ps aux' and I don't see any config file.That's because it has neither.  iptables controls the firewall, which is in the kernel.  Hence, no process to speak of.

> I've tried ports 3128 and 8888 so far, but to no avail. My ssh client (putty) shows that the attempts to forward are being rejected by my Ubuntu box.As somone else mentioned, you likely didn't configure squid to not kick you out.  You're connecting fine, but squid is refusing to proxy for you.

> I understand that, and I've dealt with squid and the squid.conf file before. That's not the issue. The problem is that Ubuntu Server is rejecting the port forwarding from my ssh session. Please read my original post.Well, posting it so it can be verified would be prudent.  Squid doesn't allow connections from localhost by default.  You did allow connections from localhost, right?  Well, if you're using the command you gave, they'll appear from 'mymachine.net' (whatever IP  your box things that is) on the loopback iface.

Posting your squid.conf, the exact error you're recieving, and the configuration change you made on the client would be rather prudent.

---

### Post by Jussi Kukkonen on 2005-11-03
[QUOTE=ShawnMilo]
ssh -L 3128:mymachine.net:3128 mymachine.net

This should work because I'm not using -R, which would potentially conflict with the server if it was a reserved port, the port number is high enough not to be a port protected by the server, and I've done it before with Debian.[/QUOTE]

I've done port forwards (-L and -R) on both Hoary and Breezy, so it's definitely possible.

Just a thought: could it be a name resolution problem? Could you try
```
ssh -L 3128:localhost:3128 mymachine.net 
```
...not that this is very likely.

---

