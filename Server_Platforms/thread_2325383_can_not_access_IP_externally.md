---
title: "can not access IP externally"
date: 2016-05-21
forum: Server Platforms
---

### Post by ryan209 on 2016-05-21
So this isn't directly ubuntu server related but it is preventing my server from being up.

I recently upgraded my internet and comcast sent me a new xfinity router/modem in one. Model: TG1682G to be exact.

Everything worked fine before switching to this router/modem, I have forwarded the ports for HTTP MYSQL & SSH and open port check tool (canyouseeme) can see the ports.  But when navigating to my IP address nothing loads.  I am dumbfounded at what else I need to do =/ this new router/modem has a lot of settings but I've never known to do anything other than forward the ports.

So for an easier testing environment, I installed xampp on my pc and disabled the modem and windows firewall, but that didnt help either.  I have no idea what to do =(

---

### Post by steeldriver on 2016-05-21
Are you trying to access the external IP from within the LAN? if so, the issue might be that the router does not support NAT loopback

Can you try from outside the LAN (for example, from your phone)?

---

### Post by ryan209 on 2016-05-22
Yup, it loads from outside the LAN (on my phone) but does not on the LAN (if phone is on wifi for example) is there anyway I can enable this?

I found a workaround, but this is not ideal.  Pointing my devices IP to the domain name via the host file but i dont like that solution

---

### Post by papibe on 2016-05-22
Hi ryan209.

I don't believe that router will support NAT loopback.

You are left with a couple of options:
[LIST]
[*]Use the internal IP, or hostname, when you are at home, or
[*]Install and configure a set of tools to make the access as transparent as possible.
[/LIST]
Hope it helps. Let us know if you need more details on the second option.
Regards.

---

### Post by ryan209 on 2016-05-22
im speaking with a comcast person right now, OMG i swear they are retarded -_-

Roomates name on the account

```
[COLOR=#333333][FONT=sans-serif]Hello THOMAS_, Thank you for contacting Comcast Live Chat Support. My name is Dhiman. Please give me one moment to review your information.[/FONT][/COLOR][COLOR=#333333][FONT=sans-serif]
[LIST]
[*]THOMAS
[*]12:19PM
[/LIST]
My Issue: I have just recieved a new router/modem and I cant figure out how to enable NAT Loopback

[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]
[LIST]
[*]Dhiman
[*]12:20PM
[/LIST]
Thank you for contacting Comcast Live Chat Support. We appreciate your business.

[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]
[LIST]
[*]THOMAS
[*]12:21PM
[/LIST]
Hello, I have just received a new router/modem, and I have set up my network, forwarded the ports I need to and everything, but I cant access my network internally, although I can access it remotely. Is there anyway I can get NAT Loopback enabled, I have the ARRIS TG1682G

[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]
[LIST]
[*]THOMAS
[*]12:22PM
[/LIST]
I have tried google, but wasn't able to come up with anything, so I was hoping you guys could help me with the router/modem you sent me

[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]
[LIST]
[*]Dhiman
[*]12:24PM
[/LIST]
Thank you for the information. I assure you that I will do my best to fix the issue for you.

[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]
[LIST]
[*]Dhiman
[*]12:24PM
[/LIST]
To assist you better, I would like to ask you a few questions. Is that alright?

[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]
[LIST]
[*]THOMAS
[*]12:24PM
[/LIST]
yes

[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]
[LIST]
[*]Dhiman
[*]12:24PM
[/LIST]
Thank you.

[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]
[LIST]
[*]Dhiman
[*]12:25PM
[/LIST]
Please connect your computer to the modem through wired (Ethernet cable ) internet connection and let me know if internet works fine?

[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]
[LIST]
[*]THOMAS
[*]12:25PM
[/LIST]
already done and working correctly

[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]
[LIST]
[*]Dhiman
[*]12:26PM
[/LIST]
Thanks for the info.

[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]
[LIST]
[*]Dhiman
[*]12:26PM
[/LIST]
Now please allow me a minute.

[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]
[LIST]
[*]THOMAS
[*]12:28PM
[/LIST]
more information you may need, it's not the internet I'm having issues with, I have a server on my network, and I allow external access to it via a domain that points to my IP [http://24.128.169.65]("http://24.128.169.65/")this is working from outside the network (a computer not connected to this network) but it does not let me load if I am on the network (from my local PC) this is because of the NAT Loopback if I'm not mistaken

[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]
[LIST]
[*]Dhiman
[*]12:30PM
[/LIST]
Thanks for the info.

[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]
[LIST]
[*]Dhiman
[*]12:32PM
[/LIST]
Could you please that you are trying to connect a gaming console or access a VPN network?

[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]
[LIST]
[*]THOMAS
[*]12:32PM
[/LIST]
its a dedicated server, on my network

[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]
[LIST]
[*]THOMAS
[*]12:32PM
[/LIST]
web server

[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]
[LIST]
[*]THOMAS
[*]12:34PM
[/LIST]
it all works remotely, it should load for you [http://its.dirtrif.com]("http://its.dirtrif.com/") (which is just pointing to my IP) the problem is it wont load from a computer on the same network, (this PC) which is because of something to do with the router/modems loopback

[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]
[LIST]
[*]Dhiman
[*]12:35PM
[/LIST]
Thomas, You need to enable port forwarding in order to access the dedicated server on your computer.

[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]
[LIST]
[*]THOMAS
[*]12:35PM
[/LIST]
everything was working fine before I got this new router/modem from you guys

[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]
[LIST]
[*]Dhiman
[*]12:35PM
[/LIST]
It's not a NAT Loopback issue.

[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]
[LIST]
[*]THOMAS
[*]12:36PM
[/LIST]
the port is already forwarded, as you can see [http://24.128.169.65]("http://24.128.169.65/") loads for you correct?

[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]
[LIST]
[*]THOMAS
[*]12:36PM
[/LIST]
it should say "working"

[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]
[LIST]
[*]THOMAS
[*]12:37PM
[/LIST]
it doesnt work from within the network though. I can not go to my ip address unless i use a proxy

[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]
[LIST]
[*]Dhiman
[*]12:39PM
[/LIST]
Thomas, You need to open the port with your new ARRIS TG1682G wireless gateway.

[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]
[LIST]
[*]THOMAS
[*]12:40PM
[/LIST]
the ports are open....

[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]
[LIST]
[*]THOMAS
[*]12:40PM
[/LIST]
HTTP    TCP/UDP    80    80    10.0.0.92 SQL TCP/UDP    3306    3306    10.0.0.92

[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]
[LIST]
[*]THOMAS
[*]12:41PM
[/LIST]
Advanced > Port Forwarding those are what I have open

[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]
[LIST]
[*]THOMAS
[*]12:41PM
[/LIST]
and it works... ONLY from outside the network

[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]
[LIST]
[*]Dhiman
[*]12:41PM
[/LIST]
I certainly understand your concern.

[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]
[LIST]
[*]Dhiman
[*]12:41PM
[/LIST]
Please allow me a minute.

[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]
[LIST]
[*]THOMAS
[*]12:42PM
[/LIST]

[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]it has to be the loopback, and this modem does not allow me an option to enable/disable nat loopback[/FONT][/COLOR]
```

would I be better off just buying my own router/modem in one rather than renting comcast's?  If so which one is a good choice for having a server behind?

---

### Post by papibe on 2016-05-22
> **ryan209 said:**
> would I be better off just buying my own router/modem in one rather than renting comcast's?  If so which one is a good choice for having a server behind?
That's what I do (different provider though).

If access to the server is your main concern, you should be able to access your server from your LAN using its LAN IP, or hostname.

If you handle your own DNS in your network, you can point  **its.dirtrif.com** to your server's LAN IP. This way it would be transparent for any client in your LAN, even if you take it to the outside world (University, library, café, etc). If you choose dnsmasq as you DNS software, the setting for this is one line.

The only caveat, is that in order to setup this, your modem/router should have the option of either pointing its client to a custom DNS, or disabling DHCP. In the last case, you can use dnsmasq to serve both DHCP and DNS.

Hope it helps.
Let us know if that points you in the right direction.
Regards.

---

### Post by Doug S on 2016-05-22
> **papibe said:**
> If you handle your own DNS in your network, you can point  **its.dirtrif.com** to your server's LAN IP. This way it would be transparent for any client in your LAN, even if you take it to the outside world (University, library, café, etc). That is what I do, and it works great. (I use bind thou.)

---

