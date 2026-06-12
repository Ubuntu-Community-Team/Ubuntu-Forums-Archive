---
title: "VPN + NAS only = ????"
date: 2008-02-07
forum: Server Platforms
---

### Post by kamasabi on 2008-02-07
Gents,

I think this is the right section of the forum I should post this issue, if not, I apologize :p.  I was wondering if anyone here may be able to help with my little issue.  I have a buddy who wants to set up a VPN at his home so when he travels, he can still have access to his NAS back at home, and I'm trying to help him get it going.

All he wants to have running is his NAS. I wish he had an actual computer, I'd just throw up Hamachi and in 10 minutes be done, but unfortunately that wasn't the case.

As of right now, he is using a [D-Link DIR-330 VPN Router]("http://www.dlink.com/products/?pid=564").  

I have it set up for both ipSEC and L2TP.  I think I have them set up correctly, however, here is a screenshot of the settings I have.

[[IMG]http://img120.imageshack.us/img120/2680/l2tpms2.th.jpg[/IMG]](http://img120.imageshack.us/my.php?image=l2tpms2.jpg)[[IMG]http://img120.imageshack.us/img120/7726/ipsecxb0.th.jpg[/IMG]](http://img120.imageshack.us/my.php?image=ipsecxb0.jpg)

for ipSEC, the Name and Auth/Preshared key is filled out, and L2TP Name, username1 and password are filled out, but blanked for security reasons :p.

Now, for testing purposes I've tried a variety of clients to connect to his VPN, however, it is failing quite miserably.  I've tried using the built in Windows XP VPN connection tool, a Cisco client, TheGreenBow VPN client, all to no success.  Perhaps is there something I could have done incorrectly while setting this up.  Or is there something more to what I have here that I need?  Such as ports forwarded on my end, etc.?  This is the first time I've ever done this, and it is a bit confusing.  If you need more info please give a shout and I'll get it ASAP.  

Thanks!!

Kama

---

### Post by kamasabi on 2008-02-07
anyone?

---

### Post by koenn on 2008-02-07
I'm not really familiar with IPsec and L2TP, but could it be that the clients you tried just aren't compatible with these protocols ? 

In any case, I noticed that router / V D-link also supports PPTP (it's an option on the same page as L2TP).
You coud configure it for pptp ant try to access it with the XP vpn client (or a linux pptp client) and see if
1- does it connect ? can you authenticate ?  -- and if yes,
2- can you get to the NAS ?

If that works, at least you will know that what you have in mind is possible. 
If, for some reason, you prefer not to use PPTP, you can start figuring out why pptp would work while L2TP and IPsec dont.

---

### Post by kamasabi on 2008-02-07
actually I'm kinda glad you mentioned PPTP, because it made me go look at the latest firmware updates, and think there lies the problem, once I update it hopefully it'll work.

---

### Post by kamasabi on 2008-02-07
w00t!  I got it going!   Why oh why would a company release a router with a firmware that is not up to date with all the functions it promises? O.o.  Firmware updated fixed all, thanks though koenn.

---

