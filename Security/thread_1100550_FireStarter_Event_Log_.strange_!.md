---
title: "FireStarter Event Log .strange !"
date: 2009-03-19
forum: Security
---

### Post by Na$$im on 2009-03-19
Hi there,
i started using Amsn  ,and then i disconnected and close it ... after closing amsn , the "msnp" Service on port 1863 stayed on active connection list ! is it normal ?!
after that  i have 2 "DCOM-scm" blocked connection log on port 135  .what the hell is that ?!

thanks

---

### Post by lovinglinux on 2009-03-19
Firestarter is not the best tool for monitoring connections. 

As far as I remember, there is some sort of bug in netfilter that creates this kind of false report. If you use for example the application IPTState to monitor connections, it will also show this kind of error after closing the application that was connected to the network. It does not happen all the time and not with all connections, just a few. 

I'm not an expert, but I think it works like this:

Every connection has a TTL (time to live).

> Time to live (sometimes abbreviated TTL) is a limit on the period of time or number of iterations or transmissions in computer and computer network technology that a unit of data (e.g. a packet) can experience before it should be discarded.

When the application start a connection it has a TTL of 119 hours and change. If you close the application, all connections should be terminated, but sometimes they don't, so the TLL will continue it's countdown to zero, when it will be closed.

This doesn't mean you are actually exchanging data with the remote machine, but if that machine sends new packages to yours, they will probably go trough the firewall, because the connection is considered established.

So if you are really worried about this, you should first check if there is actually data being transmitted. You can do this with iftop. You can also terminate the connection manually using IPTState, which I think is a better tool for connection monitoring than Firestarter.

To install them:

```
sudo apt-get install iftop iptstate
```

Additionally, there are several reports about Firestarter bugs that allow a remote machine to take control of your system. Since Firestarter needs root access to run, this is a big security issue. If you really want to use Firestarter, you should configure it and then close it. The firewall will continue to work after closing it, because Firestarter is just a firewall manager, not the firewall itself. This means Firestarter just create the firewall rules for iptables, which is actually the firewall.

Another option would be to use ufw (gufw for gui), which is the current default firewall manager for iptables. It is very simple to use, just like Firestarter, but lack the monitoring stuff.

About "DCOM-scm" [http://www.grc.com/port_135.htm](http://www.grc.com/port_135.htm)

Since they are blocked, there is nothing to worry about. 

Firestarter also scares people with this kind of thing because the user thinks they are being hacked by some weird application. But what happens is that Firestarter connection type is based on port number, not on application. Since "DCOM-scm" is the most common application to use port 135, then Firestarter says it is "DCOM-scm", but that's not necessarily true. For instance, if I configure my torrent application to accept incoming connections on port 135 (not a good idea), then all torrent connections will be considered "DCOM-scm" by Firestarter. But they aren't.

---

### Post by Na$$im on 2009-03-20
Thanks alot , Very helpful explanation ! I heard about TTL before ,but never thought that it can be so frequent ...i'm gonna to take look at IpsState and see what it can do ...

Cheers

---

