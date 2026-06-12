---
title: "Is someone connected to my PC?"
date: 2008-08-04
forum: Security
---

### Post by RavUn on 2008-08-04
I setup samba to allow all access so I could easily get into my computer from my brother's computer... I was only going to have it open for a couple of hours.  When I came back I see inbound and outbound connections.

One is an IP address on local service/port netbios-ssn.  The others are outbound connections.  Some were xx.xxx.x.google.com (don't remember the numbers and letters) and dal-lv3-n8.panthercdn.com.  

Was someone on my PC?  I was downloading files from my PC onto my other computer on my network but that wouldn't show as an inbound and the IP address wasn't my brother's IP address.  I closed samba and the inbound went away but the outbound lingered for a bit.  Could anyone shed light on this situation?

---

### Post by hvc123 on 2008-08-04
dunno, 
i personaly use sFTP through ssh t o grab files.. 

my works squid only allows 80 + 443 through so i setup my ssh on 443 and use sFTP to transfer,, much more secure

you must of had the share open to the world and its brother ( security = share)

---

### Post by mbp on 2008-08-04
It sounds like someone was connected to your PC.  There are people who scan the net for machines that are accepting connections so they may have found it that way.

You can look in the Samba log files (under /var/log) to see what happened.

It will depend on whether you set it up to require authentication, and what directories were exposed and whether they were readonly or writable.  If you exposed the whole filesystem writable you should probably assume your machine has been cracked. :-/

---

### Post by Dr Small on 2008-08-04
> **mbp said:**
> It sounds like someone was connected to your PC.  There are people who scan the net for machines that are accepting connections so they may have found it that way.

You can look in the Samba log files (under /var/log) to see what happened.

It will depend on whether you set it up to require authentication, and what directories were exposed and whether they were readonly or writable.  If you exposed the whole filesystem writable you should probably assume your machine has been cracked. :-/
That statement is a little bit bold.

---

### Post by hyper_ch on 2008-08-05
disable upnp on your router and if you have a wireless network use at least wpa

---

### Post by RavUn on 2008-08-05
If I set the path to a directory in my home folder could they get access outside of that?  Hopefully nothing bad happened.  I don't know how to check.  I checked some log files in the samba folder but didn't see much.

I figured people could only get in if they were connected to our LAN.  Our WLAN is encrypted, also.  Live and learn I guess.

I had it setup with authentication but hadn't setup a password yet (or couldn't remember it if I had) so I couldn't access it.  I setup the password but when I tried to login from the XP computer it was saying I didn't have privileges.  I figured I'd just allow open access for a bit and didn't think anyone could get in unless they were on our network.

---

### Post by hyper_ch on 2008-08-05
> **RavUn said:**
> Our WLAN is encrypted, also.

How? If it's WEP you are not secure at all. It's a matter of a few seconds to crack a WEP password.

---

### Post by RavUn on 2008-08-05
> **hyper_ch said:**
> How? If it's WEP you are not secure at all. It's a matter of a few seconds to crack a WEP password.

Oh, I'm pretty sure it's WEP.  My brother has it set up.  

So, it'd still have to be someone in my neighborhood who was connected then right?

EDIT: wow, I just read about cracking WEP and I can't believe it's that simple.

---

### Post by Dr Small on 2008-08-05
> **RavUn said:**
> Oh, I'm pretty sure it's WEP.  My brother has it set up.  

So, it'd still have to be someone in my neighborhood who was connected then right?

EDIT: wow, I just read about cracking WEP and I can't believe it's that simple.
There is no security with WEP. You must use WPA if you want protection.

---

### Post by hyper_ch on 2008-08-05
lucky for me I don't encrypt my wifi at all ;)

---

### Post by Dr Small on 2008-08-05
> **hyper_ch said:**
> lucky for me I don't encrypt my wifi at all ;)
I don't either, since I live in the middle of no-where on a knoll. If someone came up through my yard to steal my wifi, I'd be opening my window firing a couple rounds down at him. :)

---

### Post by hyper_ch on 2008-08-05
No, in order to protect me I don't encrypt the wifi ;)

---

### Post by moonpup on 2008-08-05
You may want to reconsider :)

[http://www.theregister.co.uk/2008/08/01/terrorist_email/](http://www.theregister.co.uk/2008/08/01/terrorist_email/)

---

### Post by hyper_ch on 2008-08-05
> **moonpup said:**
> You may want to reconsider :)

[http://www.theregister.co.uk/2008/08/01/terrorist_email/](http://www.theregister.co.uk/2008/08/01/terrorist_email/)

not really.

---

### Post by mupto on 2008-08-05
yea encryption is for sissys

---

### Post by hyper_ch on 2008-08-05
not really... but I am not liable for an open wifi and my system is fully encrypted. As I don't have to prove my innocence but others my guilt I profit from the open wifi as I can very easily say someone else might have done it while being logged onto my wifi - and as there are normally 3-4 other people using it the open wifi make me feel safe :)

---

### Post by moonpup on 2008-08-05
It's no wonder why computers continue to get cracked, hijacked and personal data stolen with that mindset... :)

---

### Post by hyper_ch on 2008-08-05
please elaborate. How does a open-wifi compromise my computer?

---

### Post by moonpup on 2008-08-05
My statement above was more generalized, meaning that lax security and not encrypting sensitive data ultimately leads to trouble sooner or later. 

Anyway, having an open access point is fine in the right context. Hence, providing free wireless at a hotel, coffee shop etc that is properly segmented and controlled. Having an open access point on your home network just invites trouble makers right onto your local home network to do as they wish. Not something I would do personally, but to each his own. 

Anyway, I'm not trying to move this thread off topic so I'll shut up now :)

---

### Post by RavUn on 2008-08-05
That's almost like having a house and people doing drugs in it but you're innocent since you didn't partake.

---

