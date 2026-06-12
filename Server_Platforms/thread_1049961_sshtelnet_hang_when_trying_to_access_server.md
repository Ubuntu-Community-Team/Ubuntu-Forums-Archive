---
title: "ssh/telnet hang when trying to access server"
date: 2009-01-25
forum: Server Platforms
---

### Post by itsadok on 2009-01-25
I have several Ubuntu 8.04 servers in a remote location. The servers are heavily loaded, with CPU usage in the upper 90s.

Occasionally (every 4-5 weeks), a server would stop responding when I try to ssh to it. Since I don't have physical access to the servers I have had to ask the remote site support to power cycle the server, which usually means lots of work when it comes back up.

In my despair, I tried installing telnetd on the servers so that I'd have an alternative method of logging in on emergencies. However, this didn't help since telnet hangs in a similar fashion.

Note that the server still works - I have http access and the log files show no noticeable problem.

When I do ssh -vvv I see that the authentication succeeds, and the connection hangs after "Entering interactive session.". When I telnet I get the welcome message, I enter my username and password and then it hangs.

I'm guessing something is happening in .bashrc or .profile, but I haven't touched it other than add a few aliases.

**So:**
1. Anything I can do to access my server right now without a hard reset?
2. Anything I can do to prevent this from happening again?

Right now my best idea is to add a web interface to shut down my processes, so that a hard reset would cause less damage, but I don't love that idea for several reasons.

---

### Post by HermanAB on 2009-01-25
I suspect that as soon as the user bash shell starts, the priority becomes that of a lowly user and so it never gets scheduled.  You may have better luck if you configure SSH to allow root login using keys, since then the priority should remain high. (Or make the user a member of the wheel group.)

You should also consider installing Webmin as an alternative control method.  That is what I do on my servers.

Hope that helps!

Herman

---

### Post by trentscott4 on 2009-01-25
> **HermanAB said:**
> 
You should also consider installing Webmin as an alternative control method.  That is what I do on my servers.


Agreed!

```

  1. From terminal, install the package dependencies with the
following command:

     sudo aptitude install perl libnet-ssleay-perl openssl
libauthen-pam-perl libpam-runtime libio-pty-perl libmd5-perl
  2. Download the latest Webmin package from SourceForge:
     wget http://downloads.sourceforge.net/webadmin/webmin_1.441_all.deb
  3. Install the package:
     sudo dpkg -i webmin_1.441_all.deb
  4. From another machine on your local network, browse to:
     https://your-server-ip:10000
  5. Login using the account created during system installation of your server.

```

---

### Post by itsadok on 2009-01-26
Thanks for your suggestions. I've installed Webmin, and I'm considering allowing a root ssh key. It can also make admin scripting easier, but I don't love the security implications.

---

### Post by trentscott4 on 2009-01-26
I just don't open port 10000 on the router and create a firewall rule (Networking > Firewall) to ALLOW TCP connections on port destination port 10000.

Ideally, it would be cool to have a MAC address filter on the firewall connection...

---

