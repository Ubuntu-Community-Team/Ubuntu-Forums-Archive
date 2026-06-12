---
title: "Can not connect to Server Outside of LAN"
date: 2010-03-02
forum: Server Platforms
---

### Post by dvalverde on 2010-03-02
To start I just want to say I am pretty new to both Servers in general, and Linux.  I have used them both for a few years but in no way am I an expert.

Yesterday I had my server up and running perfectly for both Local and External.

Today while at work I tried to show a customer my website and it would NOT connect.  I checked my phone where I had a ssh terminal to try and connect.  Still no connection.  I have added a lot of server applications to my server ranging from PHPBB, Webmail, Webhosting, Game Servers, and Samba.  Like I said all of these connected and worked Externally yesterday.  Today I can only connect locally.

Here is what I have:

OS: Ubuntu Server 9.10
Router: SMCD3GN
   *I have configured portforwarding to allow both ports: 22 UDP/TCP, and 80 UDP/TCP
Applications Installed: SSH-server, Apache2, php5, phpbb, Samba, mediawiki, clamav, ubuntu-desktop.

*Note* I have ajusted iptables and ufw to allow ports 22 and 80

I know to use my IP address for my external and NOT to use my local.

Is there something I may have missed or will I need to reinstall my server and start fresh.

---

### Post by Kiwi76 on 2010-03-03
There's two possibilities.

If your external IP address is dynamic, you may need to use DynDNS or something similar.

Also, check and make sure the server itself is using a static IP address. If it's using DHCP, the router may assign it a new IP address every so often.

In any case, it sounds like the internal or external IP address changed and it broke the connection/setup. I would guess it's one of those two if it worked before but not now.

---

### Post by dvalverde on 2010-03-03
> **Kiwi76 said:**
> There's two possibilities.

If your external IP address is dynamic, you may need to use DynDNS or something similar.

Also, check and make sure the server itself is using a static IP address. If it's using DHCP, the router may assign it a new IP address every so often.

In any case, it sounds like the internal or external IP address changed and it broke the connection/setup. I would guess it's one of those two if it worked before but not now.

I actually thought that one my self.  Coming to realize my ip is still the same for external as well as my LAN IP.  The truth is it makes no since to me what so ever.  Thanks for the effort though I am starting to think I need to reinstall the OS and start from scratch.  Is it possible that the X11 Desktop environment (when I added ubuntu-desktop) there could have been  something that may of blocked it?  Originally I was strictly doing it in Xterm and it worked.  it wasn't till I added the desktop environment this happened.

---

### Post by Iowan on 2010-03-03
You've checked your [IP]("http://www.whatismyip.com/") from the server to verify it hasn't changed? (or do you have fixed IP from your ISP?)

---

