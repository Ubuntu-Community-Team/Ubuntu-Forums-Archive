---
title: "port forwarding rj11"
date: 2016-11-06
forum: Server Platforms
---

### Post by iacoposk8 on 2016-11-06
I would create a physical device with "raspberry pi", able to put the entire network under a vpn and TOR.
I would like to do it before the router and not after, then between the router and the phone line and to do that I need (I think) similar adapters:
[http://g02.a.alicdn.com/kf/HTB1HYhrJFXXXXcKXFXXq6xXFXXXS/Free-shipping-Portable-Dial-Up-56k-External-USB-2-0-USB-Fax-Modem-with-Telephone-RJ11.jpg](http://g02.a.alicdn.com/kf/HTB1HYhrJFXXXXcKXFXXq6xXFXXXS/Free-shipping-Portable-Dial-Up-56k-External-USB-2-0-USB-Fax-Modem-with-Telephone-RJ11.jpg)
[http://elestream.com/wp-content/uploads/2014/12/CBL-USB-COPLEY.RJ11.fw_.png](http://elestream.com/wp-content/uploads/2014/12/CBL-USB-COPLEY.RJ11.fw_.png)

1) which keywords should I use on Amazon to look for these adapters?
2) months ago I had a firewall with raspberry and here, correct me if I'm wrong is similar, because I have to take the traffic from the incoming port on the outbound port, putting us in the middle of the rules, in this case tor and vpn.
If the ports are RJ45 (Ethernet) or rj11 change anything?
thank you.

---

### Post by darkod on 2016-11-06
I'm not sure you can do that before the router, and honestly, I don't see the point. Something needs to establish the connection to the ISP, whether that's your router or the RPi...

You can still have the entire LAN behind the vpn even if the RPi is behind the router. Set up the RPi with the desired vpn connection and set in the options all traffic to go through the vpn.

Then on your LAN devices instead of setting default gateway to be the router, you will use the RPi private IP. That way the RPi will act as gateway to the LAN devices, and because the RPi is set up to send all traffic through the vpn that means all LAN devices will send their traffic over the vpn.

I would do it like that and it will be much easier to set up than those usb to RJ-11 adapters you are looking at...

---

### Post by iacoposk8 on 2016-11-07
So if I connect to the router, the raspberry (so I should not even have to buy new adapters), install VPN, TOR etc ... devices connected to the router via wifi with gateway set pointing to the raspberry all packages that send / receive will pass through raspberry?

then the router receives packets via wifi, hijacks them in raspberry, raspberry then sends them to the router to be released them into the wan?
it's correct?

---

### Post by dudumomo on 2016-11-07
Hi,

If you are afraid your router is not doing a good job, you can turn your raspberripi to a tor modem/router. You will basically need to handle 2 projects.
First, turning your rpi into a modem, to initiate the connection with your ISP (Assuming you don't have a separate box and your current router is doing this job). In this case, you will need a rj11; and then making your rpi as a tor router. (Like the onionpi [https://learn.adafruit.com/onion-pi/overview](https://learn.adafruit.com/onion-pi/overview))

I don't see the need to have a rpi turning into a modem. I prefer to use my current setup, and then turn my rpi as a tor router, ensuring all my connection through my ISP is anonymized.

So what I suggest is you turn your rpi into a tor router, disable your wifi in your current router and connect all your equipment to your rpi then.

Good luck

---

### Post by darkod on 2016-11-07
Yes, if you set the RPi LAN IP to be default gateway for any client, then the traffic from that client will go to the RPi. And in case you configure the RPi to send all traffic by default over the vpn, then that's what it will do, making all client traffic to go through the vpn.

---

### Post by iacoposk8 on 2016-11-07
thank you so much for all the help

---

### Post by iacoposk8 on 2016-11-12
Today I decided to do it!
At home I have a classic star network, so the router (192.168.1.1) with all connected devices, including my desktop computer and raspberry.
I gave my raspberry a static ip: 192.168.1.101 and installed tor.
1) if you launch this command:
wget [http://ipinfo.io/ip](http://ipinfo.io/ip) -qO -
I get my public ip but it is the same that appears on the desktop that it should give a different result
2) after fixing the first point, I think that I must turn my raspberry in an access point, right? on google I find only guides it into a WiFi access point, you recommend a guide or key words to do it without wifi?
thank you

---

### Post by darkod on 2016-11-12
How will you do the vpn? Is tor doing that? I don't know how tor works, but at the moment when connecting the RPi to the vpn you have to set it up in a way that the vpn tunnel is default for all traffic on the vpn client (the RPi).

Turning the RPi into a router is easy:
1. Open
```
sudo nano /etc/sysctl.conf
```

And uncomment the line saying 'net.ipv4.ip_forward=1' (remove the # in front). Save and close the file.

2. Set iptables to do masquerading. Probably the easiest is to open /etc/rc.local and before the 'exit 0' line add something like:
```
iptables -t nat -A POSTROUTING -j MASQUERADE
```

That should take care of it. Reboot to apply the changes.

Every client on the LAN that has 192.168.1.101 for its gateway will send the traffic to be routed over the RPi, not your home router.

But for all of this to work as expected it is important the RPi to be sending all traffic over the vpn, which is what you need to set up first.

---

### Post by iacoposk8 on 2016-11-12
thanks for your help, I put the lines in the files that you have shown me, I rebooted and configured the desktop in this way
[[IMG]http://i675.photobucket.com/albums/vv120/iacoposk8/tor_zps2ad7v8ac.png[/IMG]](http://s675.photobucket.com/user/iacoposk8/media/tor_zps2ad7v8ac.png.html)
I can surf the Internet but does not change the ip

---

### Post by darkod on 2016-11-12
The internet working is a good sign. That means you have configured routing correctly on the RPi.

But the vpn default traffic on the RPi still needs finishing it seems. You can check the RPi public ip with:
```
curl icanhazip.com
```

If that shows your router public ip, then the traffic is going through your router, not the vpn tunnel. If it shows another public ip (related to the vpn) then the traffic is going out through the vpn.
You probably need more setup not just installing tor.

---

