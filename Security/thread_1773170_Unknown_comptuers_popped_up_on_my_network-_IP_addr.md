---
title: "Unknown comptuers popped up on my network- IP address only. Should I be worried?"
date: 2011-06-01
forum: Security
---

### Post by Dustin2128 on 2011-06-01
Internet connection went out a few minutes ago (again) so I went to my router's web interface and saw two new devices on the network, IP addresses only on the 192.168 block. When I went to device details, it showed me nothing. I disabled the wireless, then I pulled the phone line and rebooted the router and, though connectivity is now back (obviously) they're still there. When I try to ping them though, I get nothing, also get nothing when I try to remote desktop in.
```

From 192.168.1.66 icmp_seq=2 Destination Host Unreachable
(after ^C)
--- 192.168.1.72 ping statistics ---
13 packets transmitted, 0 received, +9 errors, 100% packet loss, time 12030ms
pipe 3

```

---

### Post by timZZ on 2011-06-01
Can you physically look at the router? If so most likely the new IP is wireless.

Change the PASSPHRASE and see what stops working.

---

### Post by Dustin2128 on 2011-06-01
> **timZZ said:**
> Can you physically look at the router? If so most likely the new IP is wireless.

Change the PASSPHRASE and see what stops working.
Can, and did. It's still there.

---

### Post by NadirPoint on 2011-06-01
Capture some of their traffic and see what they're doing.

---

### Post by Laforge129 on 2011-06-01
If they are using a VPN capturing the traffic won't tell you what they are doing just that they are there.

---

### Post by Throne777 on 2011-06-01
Set up a an IP whitelist on the router, don't include that IP and see if anyone complains.

---

### Post by Laforge129 on 2011-06-01
> **Dustin2128 said:**
> Can, and did. It's still there.

What type of encryption are you using?   WEP or WPA, I hope your using WPA!

---

### Post by Dustin2128 on 2011-06-01
> **Laforge129 said:**
> What type of encryption are you using?   WEP or WPA, I hope your using WPA!
WPA2 as of 10 minutes ago ;) changed the password too. How do I capture traffic?
Changed the password after I changed the encryption of course, I'm not an idiot.

---

### Post by lisati on 2011-06-01
> **Dustin2128 said:**
>  How do I capture traffic?
One option is to use wireshark: it's available in the sofware center.

---

### Post by Macskeeball on 2011-06-01
> **Dustin2128 said:**
> WPA2 as of 10 minutes ago ;) changed the password too. How do I capture traffic?
Changed the password after I changed the encryption of course, I'm not an idiot.

What encryption were you using before?

---

### Post by Laforge129 on 2011-06-01
> **Macskeeball said:**
> What encryption were you using before?

I'd first want to know if there are more than one system hard wired to the router?   It doesn't matter if your hard wired, each device will have a unique IP and that might be what is causing the problem!!\

---

### Post by dozycat on 2011-06-01
try arping <ip-address>
to see the mac.
or the simple ifconfig.
Maybe you have something using virtual interfaces.

---

### Post by kerry_s on 2011-06-01
they could be gone already, check how long your router is set to keep the dhcp lease, I have mine set for 1 hour, cause I want the assigned address to change/rotate.

---

### Post by SeijiSensei on 2011-06-01
You might want to add a whitelist of known legitimate MAC addresses as well and forbid any other machines from getting an address via DHCP.

---

### Post by Macskeeball on 2011-06-01
> **SeijiSensei said:**
> You might want to add a whitelist of known legitimate MAC addresses as well and forbid any other machines from getting an address via DHCP.

That's not necessary now that the OP is using WPA2, provided it's being used with a strong password. Also, MAC addresses can be easily sniffed and spoofed.

---

### Post by Dustin2128 on 2011-06-01
> **Laforge129 said:**
> I'd first want to know if there are more than one system hard wired to the router?   It doesn't matter if your hard wired, each device will have a unique IP and that might be what is causing the problem!!\
2 devices wired into the router, my computer and my multi-server. (VOIP, limited web, games). Both of those show up in addition to the new ones.

---

### Post by Laforge129 on 2011-06-01
> **Dustin2128 said:**
> 2 devices wired into the router, my computer and my multi-server. (VOIP, limited web, games). Both of those show up in addition to the new ones.

I know WPA is not perfect and might of been cracked.   You might want to create a really good password with: 
```
!@#$%^&*() and UPPER and LOWERCASE
```

If it is an easy as just sending out a dictionary attack then that is how they got on!   Also use numbers if you can.   A good resource is the Perfect Paper Passwords:

[https://www.grc.com/ppp.htm](https://www.grc.com/ppp.htm)

that way you can always have the password and not have it on your computer.   This might solve the problem!

---

### Post by SoFl W on 2011-06-01
Make sure it isn't your TIVO, RUKO box or wireless printer.

---

### Post by collisionystm on 2011-06-01
> **Dustin2128 said:**
> Internet connection went out a few minutes ago (again) so I went to my router's web interface and saw two new devices on the network, IP addresses only on the 192.168 block. When I went to device details, it showed me nothing. I disabled the wireless, then I pulled the phone line and rebooted the router and, though connectivity is now back (obviously) they're still there. When I try to ping them though, I get nothing, also get nothing when I try to remote desktop in.
```

From 192.168.1.66 icmp_seq=2 Destination Host Unreachable
(after ^C)
--- 192.168.1.72 ping statistics ---
13 packets transmitted, 0 received, +9 errors, 100% packet loss, time 12030ms
pipe 3

```

Sounds like someone who connected wirelessly. You are most likely just looking at their old address lease. You can delete the leases and monitor your router periodically. I am sure you are fine now that you changed the passcode. Make sure to use wpa2 not wep

---

### Post by Dustin2128 on 2011-06-01
> **collisionystm said:**
> Sounds like someone who connected wirelessly. You are most likely just looking at their old address lease. You can delete the leases and monitor your router periodically. I am sure you are fine now that you changed the passcode. Make sure to use wpa2 not wep
hm, it's weird. I don't know anyone with a wireless device outside my own home for at least a few hundred feet. And I can't access my server at all now- even though I checked a few minutes ago and it's plugged into both the wall and my modem/router.

---

### Post by dozycat on 2011-06-01
reboot your router to default, with the plug.

---

### Post by Dustin2128 on 2011-06-01
> **dozycat said:**
> reboot your router to default, with the plug.
can't do that at the moment, unfortunately. I will as soon as possible though. I wonder: was I DDOS'd?

---

### Post by SeijiSensei on 2011-06-01
> **Macskeeball said:**
> That's not necessary now that the OP is using WPA2, provided it's being used with a strong password. Also, MAC addresses can be easily sniffed and spoofed.

Yes, yes, of course.  That doesn't mean having multiple lines of defense isn't a good thing.  Your assuming that the intruders, if there are any, are sophisticated.  I'm guessing in most cases they're not.

I'm hardly suggesting he replace WPA2 with a weaker encryption scheme backed up by MAC whitelisting.  I'm suggesting defense-in-depth.

---

### Post by spynappels on 2011-06-02
Is your server set to static IP or DHCP (maybe with fixed reservation)? If you rebooted the router, it may have messed with DHCP, and triggering the server to request a new IP and lease.

If it is on static IP, ignore what I just said.

---

### Post by Dustin2128 on 2011-06-02
> **spynappels said:**
> Is your server set to static IP or DHCP (maybe with fixed reservation)? If you rebooted the router, it may have messed with DHCP, and triggering the server to request a new IP and lease.

If it is on static IP, ignore what I just said.
It's dhcp, whenever I reboot the router, it gets a new IP address with which I update my registry. I rebooted my router a minute ago, reconnected my server, configured DMZ, then got a new IP address. However, the other 192.168 addresses are back after I kicked every device off the network until it attempted a reconnect and my server is not working when I try to access, though it is internet connected. EDIT: My server is now disconnected from the network again, inexplicably. Think this is an intentional attack?

---

### Post by dozycat on 2011-06-02
Could you boot your machine from livecd and use it to access your router and do an nmap as I told you before.
Maybe those Ip are services running in your own machine as someone told you.
I am really intrigued by your case and want to know what is happening.

---

### Post by Dustin2128 on 2011-06-02
> **dozycat said:**
> Could you boot your machine from livecd and use it to access your router and do an nmap as I told you before.
Maybe those Ip are services running in your own machine as someone told you.
I am really intrigued by your case and want to know what is happening.
I'll do that in a minute, what's bothering me is that I turned on DMZ and it gave me an 'external IP' which is what I used before, and it won't work- I can only connect to the server on its internal IP.

---

### Post by Dustin2128 on 2011-06-02
OK, this is getting annoying as hell. My router's software marks it as "not connected", yet my SSH session is still up, and I can still access it from a multitude of locations.

---

### Post by dozycat on 2011-06-02
I really don't trust dmz, I prefer to port forward the services I need it could mean to do more research to know how works the service but you will be a bit more secure and only forward you need and block the rest.

---

### Post by Dustin2128 on 2011-06-02
> **dozycat said:**
> I really don't trust dmz, I prefer to port forward the services I need it could mean to do more research to know how works the service but you will be a bit more secure and only forward you need and block the rest.
What's port forwarding exactly, or rather, how would I... use it? And UGH, either my web interface thing isn't working at all or it's working slow as hell. Does anyone know the linux command to get a new IP address from the router?

---

### Post by dozycat on 2011-06-02
all right, it could be your router.
What router do you have?
Check with the homepage of the router if they have an upgrade of firmware.
Port forward is an option to make a kind of bridge between a port in the public side of the network to connect to an port in an private ip in the local network.
For example:

(190.50.50.50) 80 to 80 -> 192.168.1.40

and you have apache running in the 192.168.140 using port 80.

That way you can have homepage without dmz.

---

### Post by Dustin2128 on 2011-06-02
> **dozycat said:**
> all right, it could be your router.
What router do you have?
Check with the homepage of the router if they have an upgrade of firmware.
Port forward is an option to make a kind of bridge between a port in the public side of the network to connect to an port in an private ip in the local network.
For example:

(190.50.50.50) 80 to 80 -> 192.168.1.40

and you have apache running in the 192.168.140 using port 80.

That way you can have homepage without dmz.
2Wire. I set it up properly (I think) now I'll turn off DMZplus and see if it works. But here's the thing: my router incorrectly displays the computer as inactive on the network when in fact it is both connected to and being ssh'd into by another computer on the network. I suspect that's what's giving me the problem with going to the site on the "external IP". Can you think of any solutions? Far from being an attack, it now feels like a glitch in some poor software.

ugh, headdesk headdesk headdesk. It's now giving the ip address as 0.0.0.0. It refuses to report the correct address for reasons beyond me. Does anyone have some solutions before I shoot myself?

... I want to kill something now. I'm accessing the web interface FROM THE SERVER and it still marks it as inactive. What the hell is going on?

---

### Post by dozycat on 2011-06-02
Time to go to support:

[http://support.2wire.com/](http://support.2wire.com/)

I wish you good luck, maybe it is a simple upgrade of firmware.

---

### Post by Macskeeball on 2011-06-03
> **Laforge129 said:**
> I know WPA is not perfect and might of been cracked.
It hasn't been. Not the algorithm itself.

> You might want to create a really good password with: 
```
!@#$%^&*() and UPPER and LOWERCASE
```

If it is an easy as just sending out a dictionary attack then that is how they got on!   Also use numbers if you can.

Yes, systems using a PSK (pre-share key) are subject to offline brute force dictionary attacks so it's important to use a strong password with your strong encryption. Also, a custom SSID helps prevent rainbow tables from working. None of this is due to a weakness in WPA itself, just in passwords chosen by users. 

> A good resource is the Perfect Paper Passwords:

[https://www.grc.com/ppp.htm](https://www.grc.com/ppp.htm)

that wy you can always have the password and not have it on your computer.   This might solve the problem!
Handy as that is for other things like SSH, I would suggest [https://www.grc.com/pass](https://www.grc.com/pass) instead for this particular use. If your OS stores passwords securely, having the computer remember is probably best. Otherwise you're likely to use a weak key.

> **Dustin2128 said:**
> hm, it's weird. I don't know anyone with a wireless device outside my own home for at least a few hundred feet.
Given a good enough antennae on the other person's end, it's possible to connect from up to half a mile away. Also, a WiFi device doesn't have to be something as noticeable as a laptop. It could be someone on their smartphone looking like they're only texting.

> **SeijiSensei said:**
> Yes, yes, of course.  That doesn't mean having multiple lines of defense isn't a good thing.  Your assuming that the intruders, if there are any, are sophisticated.  I'm guessing in most cases they're not.
If they can get past WPA, they're already using a special tool to do that (bruteforcing software). They're sophisticated.

> I'm hardly suggesting he replace WPA2 with a weaker encryption scheme backed up by MAC whitelisting.  I'm suggesting defense-in-depth.
Defense in depth is a great thing, but in this case it adds an extra level of hassle for the OP without actually adding any any security (see above).

---

### Post by SeijiSensei on 2011-06-03
When his security was originally breached, he was not using WPA; WEP probably.

Unfortunately not everyone can easily switch to WPA.  Verizon, for instance,  distributed routers that use WEP by default with the key affixed to a sticker on the bottom.  

Personally I just use WPA2 with a very long mixed-case key that also includes special characters.

---

