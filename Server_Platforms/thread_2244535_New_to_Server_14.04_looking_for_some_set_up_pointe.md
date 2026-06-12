---
title: "New to Server 14.04 looking for some set up pointers"
date: 2014-09-17
forum: Server Platforms
---

### Post by vimfuego on 2014-09-17
Hi All,

I've taken it upon myself to get my own server at home working, I'm not too experienced with Linux but I'm willing to put in the hard yards to get it working, I'm sure it will be worth it.
The PC is probably over the top for what I need but it was cheap, it is an Intel Core i3, 4Gb RAM, 250 Gb SSD, with dual LAN ports.

What I want to configure is the set up shown below where the Ubuntu Server is doing the following on Ethernet Port 0.
1 - Talking securely to the outside world via a VPN (something like OpenVPN).
2 - A firewall.
Essentially I want the Server to do the hard work on that side of things so I don't have to have VPN 'apps' installed for the devices on the network (more PC's, iPads etc). 

For Ethernet Port 1 it would be the DHCP server for all devices connected (currently my Wifi modem/rotuer handles this), I have a 24 port 'smart switch' which is actually nearly full so there is quite a number of devices connected for a home set up.

I have downloaded and installed Ubuntu Server 14.04 (which went very smoothly).

Now all I am really after is some pointers to guides which would help me set up the system to achieve the tasks above.

Thanks in advance.
Vim

[IMG]http://i300.photobucket.com/albums/nn13/MPC561/Plan_zpsb14c2656.png[/IMG]

---

### Post by Bucky Ball on 2014-09-17
*Thread moved to **Server Platforms**.*

You may have more luck here.

You are asking a few questions here and might be better to take it in bite sized chunks. You want to set up a VPN, a firewall, use the server as a gateway for the wireless router and the switch ...

I'd tackle it bit by bit. 

Wondering why you don't have the wireless router before the switch, but neither here nor there, I guess. Depending on the router, it might be better to have that before the server even - modem>router>server - as the router is probably capable of VPN and setting up a decent firewall manually. Would make life easier than setting up the server as a wired access point.

---

### Post by vimfuego on 2014-09-17
Thanks for the response Bucky and sorry for posting in the wrong spot.
The reason I have the wireless router connected to the switch is I actually have three of them, at both ends of the house and another out in the garage (I am on a few acres), it seems to work quite well.

So you think it is too hard to set up the server to act like any decent router would with built in firewall and VPN? I tried to enquire with some manufacturers but the support there wouldn't give me a straight yes or no answer. :(

This is probably more like what I have in mind I guess with the Ubuntu Box being the 'VPN Server', does that seem more reasonable?

Cheers.

---

### Post by Bucky Ball on 2014-09-17
Hopefully someone with a bit more server nous will hop on the thread, but that looks workable to me.

PS: I have attached your pic to the post. Please attach large pics rather than inserting them in the post. Click 'Adv Reply' or 'Go Advanced' and use the paperclip icon to attach pics. Keep in mind those with slow connections and vision issues. ;)

---

