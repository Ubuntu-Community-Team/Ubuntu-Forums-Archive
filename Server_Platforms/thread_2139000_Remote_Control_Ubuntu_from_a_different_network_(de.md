---
title: "Remote Control Ubuntu from a different network (desktop and web interface)"
date: 2013-04-25
forum: Server Platforms
---

### Post by semental on 2013-04-25
Hello!

At first I apologize for my grammar and spelling, I'm Argentinian and i do not speak the English language very well.

Let me tell you my question:

I have on my modem firmware DD-WRT, and dhcp enabled.

I am a beginner in network configuration, and would like to have control of my pc when I'm at work or out, and so I could add any torrent from there and have it completed when I get home, or review any file on my pc, etc.

Beforehand I clarify that I do not seek solutions such as application "Team Viewer".
What I want is to control both transmission as jdownloader from its web interface (or remote gui), and access files on my PC, perhaps also control terminal (for updates, etc..)

All this from a pc that does not share the same network, I mean from a completely different place (work, a friend's house, etc..)

I managed to configure both transmission (web interface) as the remote desktop on two pcs on the same network, but I do not understand how to do it between pcs in different networks.

From what I have seen is impossible to do so with dhcp enabled. Is this true?

It would be very tedious to have to put static ip and assign each pc in my house a number.

On the other hand I found some websites that you may (have dhcp enabled) and set up port forwarding to an application to use a static IP, but I could not do it.

Can anyone help me with this?

---

### Post by ahallubuntu on 2013-04-25
~

---

### Post by matt_symes on 2013-04-25
Thread moved to **servers** subforum. 

This may be a better forum for you type of question.

+1 on openVPN. It's safe and secure as already posted. It is available on most dd-wrt installs.

I believe you can configure transmission to start a torrent download when a torrent file is added to a directory. I use rtorrent and you certainly can with that.

Then all you need to do is drop the torrent file into the correct directory and transmission will start downloading it for you.

No need to open any other ports on the router or anything like that. Just configure openVPN on your router, connect to your router and drop the torrent file into the correct directory.

The only thing you will need to know is the public IP address of your router.

I think this is where your confusion may lay (given that you have setup your internal network already). 

The public IP address of your router can be given to you either as a static IP address or, more likely, as a DHCP address from your ISP.

It's this public IP address that can change and it's this IP address that you need to know to connect to your router over the internet.

You can use services such as [www.noip.com]("http://www.noip.com") or [www.dyndns.com]("http://www.dyndns.com") to associate a name against you public IP address. These services will also track your public IP address when it changes for you.

Kind regards

---

### Post by semental on 2013-04-25
First of all, thank you guys for your answers


This are my router/firmware specifications:

Router Model: Linksys WRT54G2 / GS2
Firmware Version: DD-WRT v24-sp2 (10/10/09) micro - build 13064 

How do i know if i have openvpn?

[http://www.dd-wrt.com/wiki/index.php/OpenVPN](http://www.dd-wrt.com/wiki/index.php/OpenVPN)
that page refers to (inside my router web-interface) a "vpn" subtab on the services tab, or a "services" tab under the administration tab, and i didn't find anything like it.

---

### Post by ahallubuntu on 2013-04-26
~

---

### Post by semental on 2013-04-29
Hi guys!

I'm back to update my status and tell you that follongwi the steps in this video:

[http://www.youtube.com/watch?v=ogZE3YPSu14](http://www.youtube.com/watch?v=ogZE3YPSu14)

I managed to use openVPN on my pc

And then, using the free dynamic DNS "no-ip" service, I could:

- View my desktop remotely from another network;
- Access transmission web interface from another network.

So, I put the topic as "solved"

I have one single question left:

I want to know if there is any application or interface to access (or from a GUI or web interface) to my files, since using the remote desktop becomes very slow.

I do not seek solutions like dropbox, (which I have installed).
I want to see all my files (even those I have not synchronized with dropbox) just in case. I also want to be able of transfering files from those 2 pcs.

Googling i found things like AjaXplorer or owncloud.

Are these applications good alternatives?
Is there a better alternative?

---

### Post by CharlesA on 2013-04-29
My first thought about accessing your files would be to use sftp to grab them off your server, but if you want a web based interface, owncloud or ajaxplorer might work for that.

I know a couple people using owncloud, but I haven't gotten around to installing it on my vps yet. I've heard of Ajaxplorer, but have no experience with it either.

---

