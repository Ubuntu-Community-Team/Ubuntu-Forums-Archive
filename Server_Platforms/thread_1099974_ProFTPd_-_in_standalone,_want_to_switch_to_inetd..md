---
title: "ProFTPd - in standalone, want to switch to inetd."
date: 2009-03-18
forum: Server Platforms
---

### Post by dodle on 2009-03-18
I set up ProFTPd in standalone mode, but now I want to run my machine with no desktop, from the console.  If I switch to the inetd mode it should run at start-up, right?  How can I switch modes?  Do I have to edit /etc/init.d/proftpd?

---

### Post by RealPSL on 2009-03-21
I am not sure I fully understand the reason you want to switch. However switching from standalone to inetd means that it would not run at startup but only when someone attempts to connect to ftp. This relies on a super daemon line inetd or xinetd (preferred) to launch the proftpd process. /etc/init.d/proftpd would not longer come into play.

There us more information [here]("http://proftpd.org/docs/howto/ServerType.html") on how to make the switch and an explanation of how each works. If you have additional problems after reviewing this information make another post and someone will try and help you.

[http://proftpd.org/docs/howto/ServerType.html](http://proftpd.org/docs/howto/ServerType.html)

Sorry I glanced at the link I sent you and realized that you would probably not have xinetd installed by default. You can use synaptic (Menu: System > Administration > Synaptic Package Manager) and search for xinetd. Or from the command line ```
sudo apt-get install xinetd
```

---

### Post by HermanAB on 2009-03-21
Note that unless your machine has extremely little RAM - just a few tens of megabytes, using a super daemon doesn't make sense.  So Xinetd and the like isn't really used anymore.

Cheers,

Herman

---

### Post by dodle on 2009-03-21
Okay, I was confused.  I wanted to run ProFTPd at startup, but I thought that if I started up in text-mode, I had to use inetd.  It seems to run well in GUI mode, so I think I'll just leave it at that.

---

### Post by Dr Small on 2009-03-21
> **dodle said:**
> Okay, I was confused.  I wanted to run ProFTPd at startup, but I thought that if I started up in text-mode, I had to use inetd.  It seems to run well in GUI mode, so I think I'll just leave it at that.
ProFTPd is not a GUI, but a daemon. If you have gProFTPd installed, then yes, that is the GUI for the daemon, but ProFTPd will run without any GUI, as it is a daemon.

---

