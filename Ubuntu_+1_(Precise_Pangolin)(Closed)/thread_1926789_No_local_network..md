---
title: "No local network."
date: 2012-02-16
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Gregory Lee on 2012-02-16
I can't get in touch with either of two devices on my local network, both routers that I need to configure using my web browser.  It seems to me to be an odd situation, since I'm using the local network to get to the internet with no problem.  I've used both wifi and ethernet cable successfully.  I had no difficulty in browsing to my router with my previous Linux system, nor with my wife's MS Windows Vista computer.  When I try it now from Ubuntu 12.04, the browser just tries for 2-3 minutes to connect, then times out.

Maybe there's a system setting of some sort I need to make to contact lan devices?

---

### Post by cariboo on 2012-02-16
I just tried accessing my router, using both Firefox and Chromium, and get the warning screen, about the certificate being invalid, using https. then both browsers crash. Is this what you are seeing?

---

### Post by effenberg0x0 on 2012-02-16
> **Gregory Lee said:**
> I can't get in touch with either of two devices on my local network, both routers that I need to configure using my web browser.  It seems to me to be an odd situation, since I'm using the local network to get to the internet with no problem.  I've used both wifi and ethernet cable successfully.  I had no difficulty in browsing to my router with my previous Linux system, nor with my wife's MS Windows Vista computer.  When I try it now from Ubuntu 12.04, the browser just tries for 2-3 minutes to connect, then times out.

Maybe there's a system setting of some sort I need to make to contact lan devices?

About the network appliances:

[LIST]
[*]Do they have fixed IPs (as in "are you pointing your browser to the right place")?
[*]Can you ping them via gnome-terminal?
[/LIST]
 ```
ping xxx.xxx.xxx.xxx

```
[LIST]
[*]Are they currently set to allow any MAC address to access them?
[*]Do they require http_**s**_://xxx.xxx.xxx.xxx?
[*]Are they set to port 80? or another port like [http://xxx.xxx.xxx.xxx:8081](http://xxx.xxx.xxx.xxx:8081)
[*]Is there more than one DHCP server in this network?
[*]Are you in the same LAN segment as them?
[*]And if not, are they set to allow access to their management page from outside their LAN segment?
[*]Are you running ufw or another firewall?
[*]Are they under another firewall-enabled node?
[*]If you connect your PC to them via an Ethernet cable, can you ping and access their management interface?
[*]You may also set a fixed IP address in the devices subnet and try to access them again.
[*]Some devices allow you to adjust and check settings via telnet:
[/LIST]
```
telnet xxx.xxx.xxx.xxx
```[B]
EDIT:[/B] The guys at the [Networking]("http://ubuntuforums.org/forumdisplay.php?f=336") area of UbuntuForums can offer you good help.

**EDIT2:** Since you mentioned two routers, my guess will be that both have their dhcp servers enabled in different LANs. Let's say 192.168.1.x and 10.0.0.x. And both are set to not allow access to their management interfaces from outside their LAN (which is pretty much a default for most routers).

Regards,
Effenberg

---

### Post by Gregory Lee on 2012-02-16
> **cariboo907 said:**
> I just tried accessing my router, using both Firefox and Chromium, and get the warning screen, about the certificate being invalid, using https. then both browsers crash. Is this what you are seeing?
No, I see an attempt to connect which times out.  Or, rather I saw that.  I may have solved my problem.  The Firefox Edit > Preferences > Advanced > Network > Connection Settings > Configure Proxies was set to Use system proxy settings.  I changed it to No proxy, and now I can browse to my one router.

The other router doesn't work yet, but it's a brand new device that I probably just don't know enough about setting up.

---

### Post by Gregory Lee on 2012-02-16
> **effenberg0x0 said:**
> About the network appliances:

[LIST]
[*]Do they have fixed IPs (as in "are you pointing your browser to the right place")?
[*]Can you ping them via gnome-terminal?
[/LIST]
 
That's a lot of questions, and several of them I followed up on, which helped me zero in on the problem, which I'm thinking now, for one of the routers, had to do with proxy settings.  I don't know yet what's going on with the other one, but apparently it's a different problem.

I can ping the "good" router, and also telnet to it.  So I started thinking it was a problem with the browser.  I don't know what the "system proxy settings" are, but I think there may be a system bug there.

Thanks for your help.  I don't think the problem with the other router has anything to do with Ubuntu, so I won't go into that here.  I may go over to the Networking area, as you suggest.

---

