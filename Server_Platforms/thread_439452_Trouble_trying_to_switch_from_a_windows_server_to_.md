---
title: "Trouble trying to switch from a windows server to Ubuntu server"
date: 2007-05-10
forum: Server Platforms
---

### Post by Pro_D on 2007-05-10
I have a windows 2000 server right now.  I am trying to get several things going on a linux server so that I can replace it, things like dhcp and dns (right now).

Coming from setting up a windows 2000 network with a few clicks I didn't know much about dns (ok on most of the other stuff eventualy) but I know a lot more than I did 3 days ago!

My test environment is ubuntu 6.06 server with 2 nics, eth 0 which will be the internet nic (down the road), and eth 1 which is the lan nic (internal network class c address).  On the lan nic is a hub and also on that hub is a windows 2000 computer.  I have the 2000 computer on a workgroup named workgroup.

Pluging that windows 2000 machine into the windows network gets me an IP address and a name that can be used to ping that machine from any other machine on that network.

If I plug that windows 2000 machine into the ubuntu sever network it gets an IP address but pinging it from the server gets me a nice unknown host message using either the short name (ex pete) or the full dns name (ex pete.linux.bogus).  Also dig gives me a servfail status trying the computers name.

I have configured the dhcp server to update the dns server (found a nice howto) yet I can't seem to get the windows computer pingable by name.  I don't know if I am missing something or just have a bad configuration...  All the diagnostic checks (I know how to do on linux) show I have the dns server setup properly and the software (nslookup) seem to indicate that ubuntu server is setup right from the windows 2000 machine as well.  I also don't see anything odd in daemon.log.

The howto I most recently used to get dhcp to update dns was [this one](http://ubuntuforums.org/showthread.php?t=267974).  I changed things where appropriate (IP addresses, domain names, server name, only one server).

Any ideas? Other info usefull?

---

### Post by craigp84 on 2007-05-11
> I am trying to get several things going on a linux server so that I can replace it, things like dhcp and dns (right now).

Good stuff - i hope it works out for you. It's easier in the long run, just fairly different from the windoze way.

> Coming from setting up a windows 2000 network with a few clicks I didn't know much about dns (ok on most of the other stuff eventualy) but I know a lot more than I did 3 days ago!

Funny you should mention that, there was a wee debate on this the other day. Glad to hear you're learning! I hope it continues to be interesting.

I just want to clarify something here. Can you ping the windows workstation name from the windows workstation but can't ping the windows workstation name from the linux server?

If i've read you right, then it should just be a case of updating /etc/resolv.conf on the server to something like:

```

search your.domain.here
nameserver 127.0.0.1
```

The search line ensures that when you try to ping "fred" that "fred.your.domain.here" is also tried. The nameserver line just tells your linux server to use itself for DNS resolution.

If that's not the issue, have another shot at explaining the issue for me.

Hope this helps,

Craig

---

### Post by Pro_D on 2007-05-11
Success!  Windows 2k machine gets and IP address that it can ping with full DNS name and the ubuntu server can ping the win2k machine!

The problem was several fold.

A> I forgot about resolv.conf. It get's reset each time the ubuntu server talks to the windows dhcp server and sets the nameserver entry to ask the windows server ONLY.

B> I was either blind or didn't restart the services in my final attempt that day and didn't notice an error message in the daemon log that dhcpd couldn't open the rndc.key, Though I could have sworn I used the chown (chown root:dhcpd rndc.key) line in the walkthrough to make the key accessible by dhcpd.

C> I missed a line (after all those rechecks?!) in my named configuration telling it to include the rndc.key

D> After all that was fixed apparently I had permissions wrong on the zones directory and so bind wasn't allowed to create/update the entry that dhcp instructed it to.

Lesson: Sometimes it's handy to reboot a computer, makes it easier to look at things fresh.

All in all an error in configuration files AND I missed something.  Now to go figure more stuff out :) .

Question: If I have more trouble figuring out this server should I post to this thread or start a new one?  I anticipate more issues with dns/dhcp but I am going to take a stab at them first.

---

### Post by craigp84 on 2007-05-11
Post a fresh one. This one's reached it's conclusion!

-c

---

