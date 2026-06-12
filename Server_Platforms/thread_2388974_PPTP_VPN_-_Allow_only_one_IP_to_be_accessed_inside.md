---
title: "PPTP VPN - Allow only one IP to be accessed inside the network"
date: 2018-04-09
forum: Server Platforms
---

### Post by putz182 on 2018-04-09
Hi, I think my problem is simple but I have no idea how to solve it without iptables.

I have a network behind a NAT with a lot of hardwares such as GPIOs, dataloggers and so on.
This is also a physical place with multiuser access.

For security reasons, I'm closing physical access and all users must log virtually through VPN.
I'm going to use default PPTP with chap-secrets since it is easy and fast to configure (server and client).

The problem is:
User: door
pass: key
IP which door can access: door@192.168.1.201:8523

How do I deny access to any other IP inside the network for the user "door"? For exemple, after "door" log in, if he tries to reach 192.168.1.200 it must deny!

---

### Post by TheFu on 2018-04-10
If you care at all about security, do not use PPTP. It has been hacked since 2005 and since 2012, tools have been available to hack it in real-time.

Stick with ssh, IPSec or openvpn - all using keys, never passwords.
With openvpn, you can setup different routes based on the authenticated userid.

---

### Post by putz182 on 2018-04-10
Nice! Thank you! Which one do you suggest? Keep in mind that clients are low level users (Windows).

I've used OpenVPN in the past but found that is a private service which needs annually payment.
EDIT: Since it is open source, maybe I can generate my certificates, right?

SSH can be a good alternative since users and tunnel can be easily configured. However, without bin/bash it will not work correct? Is there a way to create a SSH tunnel without allowing a live shell for the user. I have a lot of windows users which only want to click something.
Never tested IPSec.

Which I can allow only one IP access?

---

### Post by TheFu on 2018-04-10
openvpn is F/LOSS.  You can do everything yourself on your systems.  I do for remote access to my home, but there are times when a paid VPN is better too.

I don't use Windows with a VPN. For me, I don't see the point when the OS will constantly report to home (and I don't mean my home). I do use openvpn from Linux and Android clients.

Yes, ssh can allow only 1 program to be run. That's how it works for github.  But it isn't a VPN because only TCP traffic can be tunneled.  OTOH, if the IP you want to access is running a TCP service (like HTTP), then it is by far the easiest to setup for desktops, but not so easy for smartphones.

IPSec is the most secure.  I've only deployed it in corporate environments with 2FA and only on desktops/laptops.  IPSec is part of the IPv6 standard, so if you are deploying that too ... it is definitely worth checking out.

---

