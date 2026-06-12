---
title: "Has my router been hacked?"
date: 2012-10-28
forum: The Cafe
---

### Post by x-shaney-x on 2012-10-28
Noticed over the past few days my internet has been running at a crawl at times.  Not all the time, just now and then.

When it happens, the internet light on the router is flashing like mad, as though someone is downloading or something.

The last time it happened, I was poking around the router settings and looked under "Attached Devices".
There were several devices but one had no machine name. Although things don't always have those names it made me suspicious so I checked every wireless enabled device in the house (there are lots) and every device has been accounted for except this one MAC address.

Could this suggest someone has got around the security (WPA/WPA-2)?

My main concern at the moment is that if this is the case, could somebody be using my connection for illegal activities that I would be liable for?

Also what should I do now?  The WPA passcode is pretty random so if I changed it could somebody just as easily get past it again?
Only other thing I can think of is to create an access list to only enable authorized devices, though of course it would be more inconvenient.

<EDIT>
Another thought.  If somebody had just hacked the router, could they then be likely to have access to my computer without me knowing?

---

### Post by VE6EFR on 2012-10-28
Do you have WPS disabled? If not it may be an indication that someone may be trying to access your router. If WPS is on I would suggest turning that off and changing your password.

---

### Post by x-shaney-x on 2012-10-28
What is WPS?

---

### Post by rencemc on 2012-10-28
I myself just use mac address filtering as a means to control wireless access on my router. You just add your devices as needed to the acceptable list. The WPA codes can be cracked. Also make sure you change your router password.

---

### Post by x-shaney-x on 2012-10-28
I found out what WPS is and my router doesn't have it.


I reckon access list is going to have to be the way to go.
Still worried more about what has been done or what might be compromised though.

Did a mac address lookup and it didn't come back with any vendor so could it be spoofed or something?

---

### Post by rencemc on 2012-10-28
It definitely could be a fabricated mac address.

I saw something a long time ago on TV that said mac address control for access on your router was the best way to go. I don't even use encryption on mine.

---

### Post by cariboo on 2012-10-28
> **rencemc said:**
> It definitely could be a fabricated mac address.

I saw something a long time ago on TV that said mac address control for access on your router was the best way to go. I don't even use encryption on mine.

If you are depending on MAC address control, you are almost asking to be cracked, as MAC addresses are very easy to spoof. Enable at least WPA encryption if not WPA2 to be safe.

---

### Post by VE6EFR on 2012-10-28
If you aren't using any type of encryption all of your passwords for email, banking or anything else you happen to be doing are going out in the clear.

---

### Post by alphacrucis2 on 2012-10-28
> **cariboo907 said:**
> If you are depending on MAC address control, you are almost asking to be cracked, as MAC addresses are very easy to spoof. Enable at least WPA encryption if not WPA2 to be safe.

+1. Also use a **STRONG** preshared key so it is not remotely vulnerable to any sort of dictionary attack. In this situation I would also change the WIFI access point's admin password.

---

### Post by Ji Ruo on 2012-10-29
Ok some points here:

Use the strongest encryption available. If you have WPA2, use that.

Hopefully you are correct about not having a router with WPS. This is unfortunately an easy way to crack into a router and the strength of your other security will not matter if this is enabled.

If you are worried about someone cracking your password, make sure it is actually a strong one. Length is the most important component, but use of other characters will help too. I suggest you use a random combination of upper and lowercase, numbers and special characters and at least 12 characters long. Write it down on a piece of paper. Anyone who can get access to this already has physical access to your router anyway. You will have to change the password on all of your devices but at least you will know that no one is using your internet.

The light on a router will blink like crazy if it is working properly, it does not indicate heavy use.

MAC addresses can be changed and thus spoofed very easily, and it is no problem to pick up MAC addresses from allowed devices by listening in, no password needed. This part of the transmission is not encrypted. So MAC address filtering is unfortunately not effective.

Change the default password to your router configuration as well, I'd say at least 90% of people do not do this and are using a default password which can be found through an online search (admin/admin, etc). It means if they have access to your network, they have access to your router configuration.

I wouldn't worry too much about access to your computer. It would be a rare hacker who knows how to exploit a Linux computer on a local network. It's much more likely any intruders are just using your connection to torrent stuff, which would explain the slow connections.

---

### Post by coldraven on 2012-10-29
In my routers Firewall configuration section it has two settings. I'm away from home right now so this is from memory. One setting was something like "Normal" and the other is "SPI". Nowhere in the help or the instruction manual did it say what SPI means.
Anyway, one day my internet connection was going very slow so I checked to see if there where any ports open by going to ShieldsUp here:
[https://www.grc.com](https://www.grc.com)

It revealed that I had three ports open,FTP, Telnet and HTTP
So I enabled the "SPI" setting and now ShieldsUP cannot find any ports, in fact it tells me that my machine is invisible to the outside world. It cured the slow response so maybe someone **was** trying to hack in.
I found it hard to believe that the makers of my router (Edimax) shipped it with those ports enabled.
This may not be your problem but for peace of mind check it.

---

### Post by Paqman on 2012-10-29
> **VE6EFR said:**
> If you aren't using any type of encryption all of your passwords for email, banking or anything else you happen to be doing are going out in the clear.

Important stuff like banking will still be https, so not quite in the clear, but there's really no reason to use an unencrypted wifi connection at home.

WPA passwords are relatively laboursome to crack, assuming you don't use a dictionary word, but chaniong it if you suspect funny business would be a good idea, and switch to MAC address filtering as an added check. At the very least you'll find that if something unexpected stops working you might have accounted for your extra MAC and can sleep easy.

---

### Post by x-shaney-x on 2012-10-29
Thanks for all the replies and info.

The bit of research I have done suggests that as Ji Ruo indicated, it wouldn't be that hard to get into a router and it seems it isn't hard to spoof or even clone an existing MAC address so I certainly wouldn't want to rely on MAC filtering alone.

In any case, I have discovered that the router will no let me add devices to the accept list if they don't have a device name and neither my PS3 or wireless printer have device names come up so I can't use it at all.

I have contacted my ISP with my concerns so I'll see what they have to say or if they can check into it.

On my part I have always changed router passwords when I get them but I do use the default pre-shared key for convenience.

---

### Post by rencemc on 2012-10-29
I don't really do anything involving online banking or anything like that so I'm not too concerned about encryption. I am also in a sparsely populated area - I can barely see any neighbors wireless networks. If I lived in a more densely populated area, I would probably use encryption. So right now I am at peace just keeping wardrivers off my network. But yeah, if I thought people were jumping on it, I would enable encryption.

---

