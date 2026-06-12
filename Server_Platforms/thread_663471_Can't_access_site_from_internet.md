---
title: "Can't access site from internet"
date: 2008-01-10
forum: Server Platforms
---

### Post by qwallis on 2008-01-10
Hello
I want to develop sites locally, but need also to be able sometimes to access them from a different computer online.

I have set up a LAMP server on my system, which serves html and php fine: but I am going round in circles trying to get access from the net.
I have done a ton of reading and fiddling andI am a little lost. Can someone advise me on what order to check things to help me get this working please.

So far I have a hostname at dyndns.com, have installed ddclient, replaced the config file, looked at virtualhosts in apache2, port forwarding  etc etc....

The current ste of play is when I try to access myhost.dyndns.com I get the login for my router   :confused:

Cheers

---

### Post by cdenley on 2008-01-10
Some router's will not route a connection to your WAN IP from your LAN back to your LAN. Some will have an option like "local bypass" or something, but not all. If your setup is correct, your site will work from outside your LAN.

---

### Post by MasterXandrex on 2008-01-10
This should be Router configuration, what type of router do you have and what ports are you attempting to run apache on. 

Most router's with web-based configuration use the same port as apache (80), which is why you are getting the router login. Now, on to the other problem. Within a router you need to select the ports you would like forwarded to local machines and which local machines. (If you forward port 80, the outside world will get your server, but inside the network you can still access the router by typing it's IP... this is desirable)

To do this, you need to specify to the router the port and the IP to send it to. This is often problematic if you are using DHCP to dynamically assign an IP to your server as the address may change and then you would be sending the ports to other boxes on the network. You need to either assign a static IP on the same subnet  to your server (directions below) and forward the ports to that or make a DHCP reservation for your server. This latter option is not supported by all routers.

To make a static IP edit the /etc/network/interfaces file and look for something like this:
```
# The primary network interface
auto eth0
iface eth0 inet dhcp

```
and change it to this:

```
# The primary network interface
auto eth0
iface eth0 inet static 
        address 192.168.0.100  # Static IP you want to assign (The first three octals need to be the same as the gateway)
        netmask 255.255.255.0
        gateway 192.168.0.1  #Gateway IP, usually the router IP
```


Then in your router configuration you have to forward the ports, I have attached a screenshot of my configuration, which is a linksys wireless-N model. Most are similar and should be easy enough to figure out.

Hope this helps.

Xan

---

### Post by qwallis on 2008-01-10
Wooooh looks helpful!

I have a ZyXEL P-660-HW Router from Arcor and am a little hampered in that the router administration is in German, which I don't read too well.

I think I get the logic of what you're talking about. Though I can't remember seeing a page in the router admin where it looks like I could do that.

I'll take another look and get back...

Cheers

---

### Post by qwallis on 2008-01-10
That's a shot of the main panel.

Which doesn't look very hopeful. :confused:

---

### Post by MasterXandrex on 2008-01-10
Hmm... Try content filter. And you may have to disable something in Fernverwaltung (Remote Management).

Also, it may be possible to flash this router and put it in english. But beware flashing is dangerous and the police will most likely chase you down before you can get off the field. Seriousely though, there is a chance of harming the router.

Try downloading the latest firmware from this link and flashing:
[ZyXEL p-660HW Firmware]("http://us.zyxel.com/web/support_download_list.php?indexflag=20040906164737&ModelIndexflags=0,420050117110934,420050117110916,420041221102511,420041221102520,420050831093216,420050117110858,420050831095441,420060420160946,420060816160116")

Xan

---

