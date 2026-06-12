---
title: "How exposed am I?"
date: 2008-02-07
forum: Server Platforms
---

### Post by mwacky on 2008-02-07
I am not a Linux expert by any means and am actually happy I've been able to setup what I have, so I'm asking for advise, pointers, links to help answer this question: How exposed am I? vunerable to hackers, etc?

Here's the setup;

Common cable modem/service. 

Belkin Wireless Router, WPA secured.  Setup to only allow traffic to port 80 and 21, which is connected via DynDNS so i can get in to web and ftp server from outside world.

Ubuntu Desktop (latest updates, wireless connection) has samba, vnc, ssh, webmin, web, and ftp (port 21 public above) ports open via Firestarter Firewall.  The there are only two ftp accounts with secure passwords and non-common usernames.  Never seen anything unidentifable in the transfers logs, but I'm constantly being hit by people trying to crack the password with scripts, so I'm hoping noone has ever gotten in.  This happens to the servers at work too, but it really stress my old Ubuntu Desktop when someones actively hits ftip, my log files grow huge.

XP Pro Desktop: (latest updates, wired) allows web traffic (port 80 public above), has fairly secure passwords.  Also open to rdc, file sharing, ftp on the internal network.  Nothing weird in the http log.

Laptop that has samba, vnc open when it's on.

I think that I'm secured, the router only allows to the two ports, but is this naive to assume?  Lots of internal services etc.open for me to mess with and I doubt anyone is getting into the wireless network around me.  So I really think only real threat is the two open ports in my router.

Apologize for the lengthiness of this post, so thanks for reading it and double thanks for any advice.

---

### Post by faulkes on 2008-02-07
You may wish to install denyhosts or fail2ban on the ftp server, what they do is basicly monitor for repeated failed logins, after a configurable limit, the place a ban either in iptables or in /etc/hosts.deny which prevents those addresses from connecting again.

iirc you can install denyhosts via

```

sudo apt-get install denyhosts

```

The configuration file lives in /etc/

Faulkes

---

### Post by Maxtorm on 2008-02-07
Another thing to consider would be removing FTP altogether and replacing it with SCP. FTP passes usernames and passwords in plain text, so anyone between you and your server could sniff that information with relative ease. Conversely, SCP connections are encrypted.

---

### Post by faulkes on 2008-02-08
And denyhosts is configurable as well to support sftp / scp.

There you go, a nicely wrapped up solution.

Faulkes

---

