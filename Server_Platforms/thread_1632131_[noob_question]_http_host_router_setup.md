---
title: "[noob question] http host router setup"
date: 2010-11-27
forum: Server Platforms
---

### Post by slwx on 2010-11-27
Hi,
I've been trying to set up a small website, to test. I've done this with apache2, 
At home I'm using a linksys wrt54g router, 4 computers are connected to it. When I go on another computer besides mine and surf to [http://192.168.1.101](http://192.168.1.101) (my ip), I get my website.

But how do i surf to my website from an external PC, further than my router (router ip adress ... .250.252)
I've been messing arround with my routers configurations, comming to the following conclusion:

when i enable DMZ host, and enter 192.168.1.101 I can surf to my website entering [http://.](http://.).. .250.252, **but only from my own computer**. not from computers beyond my router..

I also disabled the following in the router:
* blocking anonymous internet request
* filter multicast
* filter internet NAT redirection
* filter IDENT (port113)

                                                       Any ideas ?
Thanks, 
Mathi

---

### Post by windependence on 2010-11-27
Look up "port forwarding". There are tons of articles on the web for this. You need to forward port 80 from your router to your server.
 
-Tim

---

### Post by volkswagner on 2010-11-27
You also need to verify your isp does not block port 80, or you may need to host on am alternate port.  Check canyouseeme.org from inside your LAN.

---

### Post by slwx on 2010-11-28
Hi, thanks for replys.
I've been trying to forward port 80 to my computer, but I can't seem to log on to my router .. should I do this using ssh connection? 
Or maybe I just can't do it using this specific router (linksys WRT54G)?
Thanks, Mathi

---

### Post by volkswagner on 2010-11-28
You need to search documents specific to your router.

Typical Linksys routers have web interface at [http://192.168.1.1](http://192.168.1.1)

You will need to enter that address on a LAN connected web browser.  If you never setup username and password, you will need the default which is typically admin admin.  or no username and password admin.

Disclaimer:  This is basic stuff.. if you are unaware of such, you should do more research on security.  Since you will be opening your LAN for attack after punching holes in your firewall, you should have a greater knowledge about what you are doing.  This is a friendly warning and not a flame!

---

### Post by James78 on 2010-11-28
> **volkswagner said:**
> Disclaimer:  This is basic stuff.. if you are unaware of such, you should do more research on security.  Since you will be opening your LAN for attack after punching holes in your firewall, you should have a greater knowledge about what you are doing.  This is a friendly warning and not a flame!
Definitely. Check out Fail2ban for help on banning hack attempts.

For [SSH]("https://help.ubuntu.com/community/SSH/OpenSSH/Configuring"), turn of root logins, [passworded logins]("https://help.ubuntu.com/community/SSH/OpenSSH/Configuring#Disable%20Password%20Authentication"), and use [keyed authentication]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys"). You can also [change the port number]("https://help.ubuntu.com/community/SSH/OpenSSH/Configuring#Listen%20on%20a%20Non-Standard%20Port") if you wish, but I just keep mine the same.

For FTP, well, there's Fail2ban for that.

For Bind, same, Fail2ban, but make sure you have a [secure configuration]("http://www.cymru.com/Documents/secure-bind-template.html"), also, you should enable DNSSEC.

For [Apache]("http://ubuntuforums.org/showthread.php?t=1600727"), use modsecurity (it says to use rules from SVN in thread, you don't need to do this anymore, just use the latest version), modevasive.

For Fail2ban, check [this]("http://ubuntuforums.org/showthread.php?t=1600727") out.

For Postfix, check out [this]("http://ubuntuforums.org/showthread.php?t=1600727") thread.

For securing your kernel as much as possible, same [thread]("http://ubuntuforums.org/showthread.php?t=1600727") again.

Oh, and for portforwarding, you can use [this site]("http://portforward.com") for tutorials.

---

