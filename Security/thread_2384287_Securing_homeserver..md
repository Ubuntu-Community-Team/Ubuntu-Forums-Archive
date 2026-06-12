---
title: "Securing homeserver."
date: 2018-02-05
forum: Security
---

### Post by rizeeu on 2018-02-05
When NextCloud 13 is comming out with the end-to-end crypt i'm going to put my homeserver/desktop online

Any submitted gudies/pointers will be greatly appreciated specially since its my first linux-server setup and in a security-freak when it comes to personal-data.

It will be used for NC13, Plex Media Server and general using from the desktop GUI(thinking Mate),i have read so many guides my head is about to explode, i cant really find a 'kinda-new' one tho, maybe the old ones still work fine.

---

### Post by TheFu on 2018-02-05
If you care about security, use a full VPN, self-hosts, for access to plex and nextcloud systems that you run.  OpenVPN is an option, but if you want a higher level of security, check out LibreSwan which is based on IPSec.

I use opevnvpn (256-AES) because the clients on android work pretty well, providing LAN access for my android devices as I travel.

I think letting the entire world have access to plex or nextcloud just so I can access it easily is asking too much.

---

### Post by rizeeu on 2018-02-05
Agree, i only want nextcloud open for 3-4 users and plex for 5-6, only problem i have is getting started with everything, setting up the nextcloud & plex itself ain't no problem, just the OpenVPN/redirect/fail2ban/ufw or general network settings that isnt my strongsuite in
any OS.

---

### Post by TheFu on 2018-02-05
I allow openvpn and ssh inbound. Both use keys, never passwords.

fail2ban is easy for ssh.  Install it. By default, it protects ssh on 22/tcp.  Let the router deal with port translation for some non-default port, say 63022/tcp --> 22/tcp for ssh.

You can use ssh as a SOCKS proxy to your home network for all internal webaccess.  I know this works for plex and for the nextcloud webapp.  The hard part is that Android and SOCKS proxies ... I have no idea how to use make that happen.  

But Android does openvpn nicely. The way I do it is with 2 subnets on my LAN.  172.22.22.0/24 for real computers and 172.21.22.0/24 for VPN clients. That made the routing between VPN clients and my internal LAN systems easier.  At least is seems easier to me.

We all have weak areas in our knowledge. It is common.  I don't know much about Desktop methods and only deal with firewall stuff when necessary.

I find ssh to be possible of almost everything I need, but is means traveling with a real computer, not just a tablet.  Tried traveling with a tablet - didn't turn out well at all.

[https://ubuntuforums.org/showthread.php?t=2349509](https://ubuntuforums.org/showthread.php?t=2349509) has my SOCKS proxy script. Hope that helps.

---

### Post by rizeeu on 2018-02-05
I remeber reading something about Proxyuser(or Droid/Root) this however required root on everyphone/device, sure my devices will always be rooted but the other users will not. But u setup (2G/3G/4G/WIFI) and decide which will use the VPN connection, however this is long time ago so i cant really be sure that works anymore.

Well, then maybe i will just VPN the nextcloud, because i will need it on remote tablets for the kids. 

But then back to start again, right now i just wanna setup the plex and harden/secure the server as much as possible(for a normal user atleast) and i have no idea in which end to begin

---

### Post by TheFu on 2018-02-05
I don't allow plex from the internet and block outbound plex to many plex.xyz locations (/etc/hosts) because I don't like their spying.  Since we can't see the code, all security has to occur outside the plex machine.  Plex doesn't need outbound internet access except for the specific channels you want to watch and for the DB to be updated via scrapers (theTVdb, etc).  You can block all others.

[https://lifehacker.com/5817447/how-to-block-unwanted-ads-in-all-applications-and-speed-up-web-browsing-with-the-hosts-file](https://lifehacker.com/5817447/how-to-block-unwanted-ads-in-all-applications-and-speed-up-web-browsing-with-the-hosts-file) might be helpful.

---

### Post by rizeeu on 2018-02-06
Ah, havnt even noticed that Plex had started doing that, well whhich plex.xyz are u blocking?

---

### Post by TheFu on 2018-02-06
> **rizeeu said:**
> Ah, havnt even noticed that Plex had started doing that, well whhich plex.xyz are u blocking?

I've never had a plex account and it is unlikely you live in the same part of the world as me, so what I need to block probably isn't the same as what others need.  Just setup the firewall to LOG all outbound requests and keep track of where they go, so you don't miss any.

If you use a self-hosted VPN, no plex account is needed.

---

