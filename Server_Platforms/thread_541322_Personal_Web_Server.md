---
title: "Personal Web Server"
date: 2007-09-02
forum: Server Platforms
---

### Post by Red Moose on 2007-09-02
I want to set up a personal web server at home.  Where do I start?  Should I use Ubuntu server edition?  My home network is set up like this:  (See attached image.)
I have some experience with Linux.  
I have a Ubuntu computer that's not connected to the internet that I've installed several linux distros in the past.  However, I don't really have any experience with networking, servers, firewalls, or any of that stuff.

I have an extra "closet" computer that I want to use as a server.
Should I just connect it to the router, or does it need extra security such as a firewall?  If attackers crack my linux server, will they be able to get into my windows computers?

I found this guide: [http://www.howtoforge.com/perfect_setup_ubuntu704](http://www.howtoforge.com/perfect_setup_ubuntu704)
Should I follow it?

As you can see, I have a lot of questions.:confused:

Hopefully someone can answer me. :)
Thank you!

---

### Post by banewman on 2007-09-02
I hope this link helps - [http://www.ubuntugeek.com/category/server/](http://www.ubuntugeek.com/category/server/).

---

### Post by Seti on 2007-09-02
Yeah you could just plug your extra comp into the router, install linux and you'll be good to go. 
Things to consider:
1. what is the nature of your ISP? DSL? Cable? Something else?
2. does your router also work as a firewall? if so, then you don't really need to worry about firewalling the web-server itself; just open port 80 on the router firewall and forward this port to your webserver's IP address.
3. You will want a name for your website. If you have a dynamic IP, you will need a free accout with someone such as dyndns.org to link your IP to a hostname. 
4. You may need to go through a registrar to get your site's name exclusively for yourself.

Good Luck!

---

### Post by Red Moose on 2007-09-02
> **Seti said:**
> Yeah you could just plug your extra comp into the router, install linux and you'll be good to go. 
Things to consider:
1. what is the nature of your ISP? DSL? Cable? Something else?
2. does your router also work as a firewall? if so, then you don't really need to worry about firewalling the web-server itself; just open port 80 on the router firewall and forward this port to your webserver's IP address.
3. You will want a name for your website. If you have a dynamic IP, you will need a free accout with someone such as dyndns.org to link your IP to a hostname. 
4. You may need to go through a registrar to get your site's name exclusively for yourself.

Good Luck!
1.  I don't about any of this stuff...  It's a satellite dish pointed at a tower a couple of miles away...
2.  I think so.  Here is a page I found that describes the router I have: [http://arstechnica.com/reviews/3q00/linksys/befsr41-1.html](http://arstechnica.com/reviews/3q00/linksys/befsr41-1.html)
3.Do I need to buy a domain name first?
4.Ok

Thanks for your help.  A big thing for me is, I need it secure enough so that hackers can't get into my other computers on the network. (I don't know how these things work.)

---

### Post by p_quarles on 2007-09-02
Yes, that router works as a firewall. The NAT (=network address translation) will allow you to configure which requests from the outside are  accepted, and where they should be directed. 

In other words, you can configure it to say that requests for your web site (port 80) are forwarded to the server. This is a very secure setup. 

With NAT, your setup is very secure. There is, however, no such thing as complete security, ever, but you will be safe from most things. And, no, you don't need to worry about bad guys getting to your Windows machines from the Linux box. If these hypothetical attackers were *that* good, they could just go straight to the Windows boxes themselves.

---

### Post by Red Moose on 2007-09-02
Ok, that's good.
I think I going to start with that guide that I posted a link to.
If anyone has anything else you want to tell me, I will be checking back.
Thanks!

---

### Post by p_quarles on 2007-09-02
That's a very good guide. I used a slightly different one, from the same source, when I set up my first server.

The only thing I'd add is this: be aware that the Ubuntu server edition does *not* come with a GUI. You said you've used Linux before, so this I'm guessing you knew this -- but, just in case, here's the command to run to install Gnome:
```
sudo apt-get install ubuntu-desktop
```

---

### Post by gishaust on 2007-09-02
I have been doing the same thing setting up home server.

I have been using webmin its very useful if you are very new, as a visual helps you, that is if you are not using a gui however. Everyone recommends that you don't. I don't know why, but they are the experts,  still use the command line though what ever you  decide very powerful. 

I recommend learning the linux stucture and the commands eg ls(looks into the dir you are in) cd(change dir). 
It takes about one hour do get the basics. There are plenty of tutorials on the net. "Stree" is the command to show the structure. I found as soon as I did this  linux is very fun.

enjoy.

---

### Post by Red Moose on 2007-09-02
Yeah, I knew that.  This computer isn't powerful enough to run Gnome very well anyway.

I'm a little confused about something.  In the tutorial it says:
> In this tutorial I use the hostname server1.example.com with the IP address 192.168.0.100 and the gateway 192.168.0.1. These settings might differ for you, so you have to replace them where appropriate.
Where do I find those numbers?

Also, what exactly is webmin?

Thanks,
Matt

---

### Post by James79 on 2007-09-02
The hostname can be whatever you want, it doesn't really matter.

For the ip, you need to decide wether you want to use dyamic or static IPs for your server. Typically, it makes more sense for a server to have a static (fixed) address so that it can be easily referenced by address.

In your case, a fixed ip* is preferable *if you want to be able to port forward 80 from your router to it. In other words, on your router you will configure it to say "whenever you get a request for port 80, send it to x.x.x.x". Obviously it would be of little use if x.x.x.x changed frequently :)

---

### Post by p_quarles on 2007-09-02
> **Red Moose said:**
> Yeah, I knew that.  This computer isn't powerful enough to run Gnome very well anyway.

I'm a little confused about something.  In the tutorial it says:

Where do I find those numbers?

Also, what exactly is webmin?

Thanks,
Matt
Good. Running X11 on a server can actually be a security risk.

To find out the LAN IP address range, you can type this:
```
ifconfig -a
```This will produce something like this:
```
eth0      Link encap:Ethernet  HWaddr 00:18:F3:E7:7E:6C  
          inet addr:**10.0.0.4**  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::218:f3ff:fee7:7e6c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19324 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19750 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13864580 (13.2 MiB)  TX bytes:2027593 (1.9 MiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10537 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10537 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:560601 (547.4 KiB)  TX bytes:560601 (547.4 KiB)
```The part in bold, above, is my local IP address. In all likelihood, the gateway/router address will be the first three numbers and ".1" (the address range, btw, will be either 10.0.0.x, 172.16.0.x or 192.168.0.x). 

You should also be able to log into your router's configuration utility to find this out, but the first step will be useful if you don't know what the router's address is. 

If you're comfortable with the command line, don't worry about Webmin. Basically, it's a web-based graphical interface for operating your server. I used it for a while, and it helps with some things, but it's pretty buggy, and not completely secure.

EDIT: Meant to add this link that explains local area network IP ranges:
[http://en.wikipedia.org/wiki/Private_network](http://en.wikipedia.org/wiki/Private_network)

---

### Post by Red Moose on 2007-09-03
Wow!  Y'all are a lot of help!:)

> **James79 said:**
> The hostname can be whatever you want, it doesn't really matter.

For the ip, you need to decide wether you want to use dyamic or static IPs for your server. Typically, it makes more sense for a server to have a static (fixed) address so that it can be easily referenced by address.

In your case, a fixed ip* is preferable *if you want to be able to port forward 80 from your router to it. In other words, on your router you will configure it to say "whenever you get a request for port 80, send it to x.x.x.x". Obviously it would be of little use if x.x.x.x changed frequently :)
I attached some screenshots of my router settings.  If I choose a static IP, do I need to disable the local DHCP server?
How do I configure the port forwarding on my router. (See second picture)

@p_quarles:
Thanks, it looks like that ifconfig -a will come in handy.

So here's what I think I need to do:  (Please correct me if I'm wrong.)
1. Change the routers settings to static IP
2. Start installing the server.
3. configure the router to forward port 80 to the server's IP

Is that right?
Also, when I choose Static IP from the dropdown box, (see 4th pic) the IP address is 0.0.0.0.  Do I need to set my own IP?

---

### Post by p_quarles on 2007-09-03
1. You don't need to/shouldn't do that. If you set the server to always try to obtain the same address (and the guide you're using walks you through that), you'll be fine. The only problem you could face is that the static address isn't available at bootup time -- if you set the server's address to a high fourth number, though, this won't happen unless you have dozens ofcomputers on the loacl network.

So, keep the DHCP server enabled, and use the server's own settings to set its IP address. Most router's also have the option of "reserving" an IP address for a specific machine. This can be done without disabling DHCP. 

2 & 3: Correct.

---

### Post by James79 on 2007-09-04
> **Red Moose said:**
> 
I attached some screenshots of my router settings.  If I choose a static IP, do I need to disable the local DHCP server?


No - you do not need to. In fact, keep it enabled out of convenience so you won't have to reconfigure all the other computers around your house. Notice on your 1st screenshot there's a field called "Start IP address". This is the address from which your router will begin assiging dynamic IPs from. In other words, the first computer to request an address will be given 192.168.1.100, the next 192.168.0.101, and so forth.

Assign your server an address greater than .1 (your router's ip) and lower than .100 (first dhcp ip) and you'll be fine. Say, 192.168.1.50. That way you'll avoid collisions and duplicates with your other computers which are auto-configured. If you do this there will be no need to "reserve" the server's ip on the router.

> **Red Moose said:**
> 
How do I configure the port forwarding on my router. (See second picture)


Go to the screen from your 2nd screenshot.

Application: Apache (can be whatever you want, it's just a label)
Start: 80
End: 80
Protocol: TCP
IP Address: 192.168.1.50 (whatever you decided from above)
Enabled: Yes

> **Red Moose said:**
> 
Also, when I choose Static IP from the dropdown box, (see 4th pic) the IP address is 0.0.0.0.  Do I need to set my own IP?

DON'T set your router to static ip (like in your 4th screenshot) - leave it to "obtain IP automatically". This refers to the IP that's assigned to you, it's non-negociable and this is the setting you need to use for most internet providers.

---

### Post by Red Moose on 2007-09-04
Thanks a lot that's going to help.
I might not be able to set it up this week.  I got really busy somehow.:(
Other than that, I think I'm ready.  I just need time.:)

---

