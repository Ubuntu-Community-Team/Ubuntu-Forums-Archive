---
title: "DHCP, Samba, Firewall, Proxy Help"
date: 2007-10-19
forum: Server Platforms
---

### Post by WIGGMPk on 2007-10-19
Here Goes,

Im currently at work so config details (if needed) will have to wait till later. But generally this is what I "WANT" to do. Im just not too sure if it can be done this way.

I have an Ubuntu Gutsy Gibbon Server amd64(acctually its Gutsy Gibbon amd64 desktop w/ LAMP, DHCP, Samba, Firestarter, CalmAV). The server has 2 NIC's.. eth0 & eth2

eth0 is connected directly to the internet via cable modem
eth2 is connected  directly to a wireless router on the "internet" port (DHCP disabled)

I would like my computer to act as a DHCP server, and have set eth2 an IP address of 192.168.100.0 and gives ranges of xxx.xxx.xxx.100 - .200 and broadcasts on xxx.xxx.xxx.201. The DHCP server is (as far as I can tell) configured correctly.

Firestarter fails to load automatically on boot. (I believe it needs root/sudo to start) I am not too sure how to change this so it does NOT fail on boot. Also, after manually starting Firestarter.. Its status moves to disabled.

The wireless router. It is a Linksys Wireless Router + Speedbooster, yadda yadda yadda.. DHCP is disabled. Is it possible to make this wireless router act exactly as a WIRELESS HUB or WIRELESS BRIDGE. Mainly because my laptop is wireless and rather then throwing a HUB on the server and being limited on distance because of being tethered to the HUB. Both server and laptop (after disabling DHCP) cannot connect to the configuration page of the router now.

So basically, I need to know weither or not its possible to make a wireless router into a wireless hub.

Anyone able to throw some reference links or good walkthroughs for configuring a server to act as DHCP/Proxy would also be appreciate



Sorry if this is incoherent babble.

---

### Post by dmizer on 2007-10-19
1) you're better off using your router as your dhcp server and firewall instead of trying to configure ubuntu to do the same.

2) once you've configured firestarter, your firewall is working even if the firestarter gui is not functioning.  or in otherwords ... when you boot, your firewall is working even though the firestarter gui did not start.

3) if firestarter is configured correctly, it can do everything you want your server to do (firewall, nat, dhcp server).

4) if you want to configure your router as a hub, you'll have to look at the documentation for your router.

is there a specific reason why you want to use ubuntu as your router instead of your router as your router?  there's probably a much easier solution than reconfiguring your entire network.

---

### Post by WIGGMPk on 2007-10-20
The main reason for wanting to setup a Linux DCHP, Samba, Domain Server is for the experience really.

Using my router as my router and taking the 'easier' route of doing things may work fine and get finished faster. But I wont really be getting anything usefull out of it.

I was hired as a PC specialist with my current employer. My job is mainly pretty much fixing/troubleshooting computers & peripherals for a large distribution center. Lately, as we approach the 4th Quater and IT staff is pretty low (corporate wide) I have been asked to troubleshoot network issues.

Our company uses a similar setup as what im trying to accomplish at home, but obiously on a much large scale with a lot more expensive gadets (wlan access points). So all in all, im just trying to get myself familar with the way things work so that I can potential become a better asset to my company..

If that makes sence

---

### Post by dmizer on 2007-10-20
learning is one thing, but keep in mind ... your company probably has separate servers for each of those tasks.  and most certainly their router is not hosting their samba network shares.

for samba, see the first link in my sig.

for nat and dhcp, ditch firestarter and check this link: [https://help.ubuntu.com/community/InternetConnectionSharing?](https://help.ubuntu.com/community/InternetConnectionSharing?)

here's some reading for domain name hosting:
[https://help.ubuntu.com/community/BIND9ServerHowto?](https://help.ubuntu.com/community/BIND9ServerHowto?)

don't have anything handy for you on a proxy server as i've never installed one.  but that should give you enough to keep you busy for a bit ...

ps.
i asked why you wanted to do this so i could tailor my response accordingly.  obviously, there is way more than one way to skin this cat.

---

### Post by WIGGMPk on 2007-10-29
Thanks mate

I apologize for the time it took for me to reply as work has had me plenty busy.

I really appreciate the informational resources you provided. Much appreciated

---

