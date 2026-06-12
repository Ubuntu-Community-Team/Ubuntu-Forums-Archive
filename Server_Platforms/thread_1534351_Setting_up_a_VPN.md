---
title: "Setting up a VPN"
date: 2010-07-19
forum: Server Platforms
---

### Post by Don1500 on 2010-07-19
I am going to be away semi permanently and want to create a VPN that will allow me to act as if my laptop was connected to my home network.

All I want is for the drives to be accessible so I can use them for primary access as if they are in the laptop. 

Questions:
1. Can I set up a Linux VPN that is secure using public WiFi (or however I connect to the net) when I am on the road?
2. I will be using a desktop (32 bit) as the server, what version of Linux would be best for this?
3. If my server is linux and the server drives are NTFS will they be accessible using a windows machine? (I will be double booting the laptop)
4. I would like to set up a pass-code that is stored on the laptop so that only that machine can get access. This can be up to 255 characters and encrypted so it would be very hard to break. Even I would not know what it is. (I would store it on a pen drive and be able to recover it from there.)

One more. I might want to add separate users that only have access to their one drive, not the server drive. Is that OK?

---

### Post by Groodles on 2010-07-20
Is your laptop also Linux or is it Windows?

If it's Linux, then I'd probably go with an OpenVPN solution.  There are lots of guides on how to set this up, just google for it.

If it's Windows, then I'd go with a PPTP solution as Windows has the client for this built-in.  Here's [http://pigtail.net/nicholas/pptp/](http://pigtail.net/nicholas/pptp/) a reasonable guide for setting up a PPTP VPN for a standard road warrior configuration.

---

### Post by spynappels on 2010-07-20
There is an OpenVPN client with a GUI available for Windows which is very easy to set up. We use OpenVPN because of it's cross platform abilities.

---

### Post by Don1500 on 2010-07-20
The laptop will be Linux.
I'll look into OpenVPN today.

Thanks!

---

### Post by spynappels on 2010-07-20
On Ubuntu 10.04 you can import an .ovpn configuration file directly into Network manager and connect and disconnect using this. It really is ridiculously easy to use.

---

### Post by brettg on 2010-07-21
I use ssh vpn to do that. It's easy to setup and secure (ssh is encrypted)

There is a [howto here]("http://tuxnetworks.blogspot.com/2009/09/setting-up-vpn-using-ssh-and-pppd.html")

---

