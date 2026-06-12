---
title: "Setting up dedicated deluge torrent box - need help with proxy/VPN"
date: 2014-04-08
forum: Server Platforms
---

### Post by Donny Bahama on 2014-04-08
I'm trying to setup a dedicated deluge torrent box on a Precise server using instructions found [here]("http://www.neowin.net/forum/topic/909102-guide-to-creating-a-torrent-slave/"). Problem is, that article doesn't discuss the use of a proxy or OpenVPN. I have an account with Private Internet Access but their support team isn't very helpful when it comes to a server-based setup. They do provide CLI-based setup instructions, but when you want to test your VPN or proxy connection, they direct you to a website. Also, while their GUI agent has a kill switch (that will disable the network connection if the VPN disconnects), the CL version does not, so I need some sort of OpenVPN daemon (or a script that performs that function?)

I would really appreciate suggestions for achieving any of the above. :)

---

### Post by dudumomo on 2014-04-09
Hi Donny,

If I understand correctly, installing Deluge torrent (Daemon + WebUI) is not the issue right? If it is, I suggest read [my own tutorial ]("http://freedif.org/deluge-powerful-torrent-client-with-fancy-web-interface/")if you need to. (I can explain more afterward of course)
If it is to use bind your server connection from VPN, you will need to modify your network conf file.

So, you are using a GUI to connect to VPN or only CLI on your server? 

Also, on what type of hosting are you? 

But it sounds normal that when the VPN break, your network is down. Otherwise it would have been a big security/privacy issue to sunddely popup on non secure connection.

May be you can provide some details (Which VPN provider, etc..)

Thanks!

---

### Post by Donny Bahama on 2014-04-09
Thanks very much for the response, dudumomo! :)
> **dudumomo said:**
> Hi Donny,

If I understand correctly, installing Deluge torrent (Daemon + WebUI) is not the issue right?That's correct. At least, it's not the issue YET. (I haven't actually gotten that far yet - at the moment I'm more concerned about getting the proxy and VPN set up - but when it's time to get deluge setup, I'll definitely use your tutorial. It looks much more in-depth than the one I linked in my previous post.
> If it is to use bind your server connection from VPN, you will need to modify your network conf file.I'm kind of an "experienced novice"... which file(s) do I need to edit and what changes do I need to make?
> So, you are using a GUI to connect to VPN or only CLI on your server? No GUI at all. That's why I can't understand how I'm supposed to test my VPN and proxy once they are setup. 
> Also, on what type of hosting are you? I'm confused by this question. How is my web hosting an issue in this?
> But it sounds normal that when the VPN break, your network is down. Otherwise it would have been a big security/privacy issue to sunddely popup on non secure connection.So you're saying that is the default behavior (if things are setup properly? If so, that's good news!
> May be you can provide some details (Which VPN provider, etc..)VPN provider is Private Internet Access. Not sure what other details you need... ISP is Cox. My web host is A Small Orange but I don't understand how that factors into this.

Thanks again for the help!

---

### Post by dudumomo on 2014-04-09
Sorry Doony, I thought you were using a dedicated server hosted somewhere else.

So, you need to download the conf files of PIA (Should be a zip file with City/Country.ovpn file.
You need to install openvpn and run  sudo openvpn --config ovpnXXX.ovpn to try it out first.

Does it work like that?

And could this tutorial help: [http://raspinotes.wordpress.com/2013/06/04/setup-vpn-with-privateinternetaccess-com/](http://raspinotes.wordpress.com/2013/06/04/setup-vpn-with-privateinternetaccess-com/)

---

### Post by Donny Bahama on 2014-04-09
> **dudumomo said:**
> Sorry Doony, I thought you were using a dedicated server hosted somewhere else.That makes perfect sense. Sorry, I should have figured that out!
> So, you need to download the conf files of PIA (Should be a zip file with City/Country.ovpn file.
You need to install openvpn and run  sudo openvpn --config ovpnXXX.ovpn to try it out first.

Does it work like that?I did all that, and yes, it seemed to work -- but I'm not sure how to test it without going to a whatsmyip site.
>  And could this tutorial help: [http://raspinotes.wordpress.com/2013/06/04/setup-vpn-with-privateinternetaccess-com/](http://raspinotes.wordpress.com/2013/06/04/setup-vpn-with-privateinternetaccess-com/)that looks like just what I need! Between that and your deluge tutorial, hopefully I'll be all set. Thanks so much for the help!

---

### Post by dudumomo on 2014-04-09
Glad to know it works.

To see if it works, you will need to test your IP indeed, using command line you could do:
```
wget -qO- http://ipecho.net/plain ; echo
```
and see if it has changed.

Cheers!

---

### Post by Donny Bahama on 2014-04-09
dudumomo, you've been totally awesome and SOOOO helpful! THANK YOU!!! But I need just a little more help (please?)... 

When I got home tonight, I went to try the tutorial you so kindly suggested ("Setup VPN with PrivateInternetAccess.com") - but the first thing it wants me to do is install network-manager-openvpn* - *and I CAN'T!

As I've tried to make this work, I've tried a bunch of different things... some to do with proxy, others to do with VPN. I've tried so many things that I can't even remember all the things I've tried... At some point, though, I broke my ability to apt-get install [anything]. Everything returns
```
Connection failed [IP: xxx.xxx.xxx.xxx 1080]
```

I vaguely remember setting something somewhere to port 1080 (as per the instructions from Private Internet Access) - but I can't remember how/what/where!
I've gone back through my CL buffer, but the only nano entries are for /etc/network/interfaces (from when I gave my server a static IP), /etc/resolv.conf (from failed attempts to set nameservers - which I subsequently figured out), and /etc/environment (which does contain proxy lines for setting proxies - with port 1080 - but they are all commented out). Any suggestions on how to fix what I have somehow messed up?

---

### Post by dudumomo on 2014-04-10
Ouch!

1) First, you tried to reboot?
2) Then can you ping google?
```
ping www.google.com
```
3) Can you copy the content of your /etc/network/interfaces, /etc/resolv.conf and /etc/environment?

It might come from the /etc/environment file from what I can see.

4) Can you refresh the environment?
```
source /etc/environment
```

You have modified some others files otherwise?

---

### Post by andrew-peart on 2014-04-26
Hi I have just went through the process of setting up deluge on a headless box with a VPN and iptables to limit access to only the vpn.
When you get you connection back I can hopefully help.

---

### Post by rbuanno on 2015-01-09
> **andrew-peart said:**
> Hi I have just went through the process of setting up deluge on a headless box with a VPN and iptables to limit access to only the vpn.
When you get you connection back I can hopefully help.

What iptables commands did you use?
I'm going to attempt this setup on my raspberry pi for practice before implementing on my dedicated server.
This is an awesome thread! Exactly what I have been looking for.
How we can finish it up with the iptables stuff :D

Later,
Ronald

---

### Post by alta2 on 2015-03-06
[LEFT]I have perfect VPN service provider [http://www.vpnanswers.com/anonymous-surfing-software/](http://www.vpnanswers.com/anonymous-surfing-software/) enabling me to get different European IPs to bypass Geo-blocking and enjoy with unlimited free internet access.[/LEFT]

---

### Post by brendan3 on 2015-04-14
In the interest of not clouding things with a new thread.. Could anyone here tell me if they think OpenVPN is a good way to go?
my goal is to use a transmission server alongside my ubuntu kodi server out in the lounge room. And make it hidden online.. So 
do i setup a OpenVPN server on the ubuntu server and then I'm good to go? or can i run server & client on the same machine? 

I don't really think i need to protect the rest of my network as they will only be copying the files the server has done the dirty work 
for.. 

Does that all make sense? Iv tried the OpenVPN thing so far but i need to understand how its suppose to work before i can 
see if i am doing it right.

---

