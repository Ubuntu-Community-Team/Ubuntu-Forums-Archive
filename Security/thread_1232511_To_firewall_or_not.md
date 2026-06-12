---
title: "To firewall or not"
date: 2009-08-05
forum: Security
---

### Post by fisheater on 2009-08-05
Hi all,

The great debate in my mind continues. Activate or not to activate a firewall on my unbuntu 9.04. (I am very new to linux, and searching gave a mixed answer)

The setup:

Cable internet modem
- wireless router (with DDWRT v24-SP1)
o laptop 1 - wireless (wireless router assigns IP)
o laptop 2 - wireless (wireless router assigns IP)
o Desktop via LAN cable (wireless router assigns IP)
o Printserver via LAN (wireless router assigns IP)
o NAS via LAN (static IP, option set in NAS setup)

The question: does my computer need a firewall? I am behind the cable modem and my DDWRT router. Is a firewall redundant and a waste of time?

Thanks!

FE

---

### Post by Stevie78 on 2009-08-05
Ive installed Firestarter through Synaptic just for peace of mind. It doesnt really affect download speeds so Im happy with it.
I regard the firewall as a hassle-free safety net but its not absolutely necessary. In the words of Jon Stewart: Its a little bit like Conneticut - while its nice to have, its not essential. :popcorn:

---

### Post by bodhi.zazen on 2009-08-05
> **fisheater said:**
> Hi all,

The great debate in my mind continues. Activate or not to activate a firewall on my unbuntu 9.04. (I am very new to linux, and searching gave a mixed answer)

The setup:

Cable internet modem
- wireless router (with DDWRT v24-SP1)
o laptop 1 - wireless (wireless router assigns IP)
o laptop 2 - wireless (wireless router assigns IP)
o Desktop via LAN cable (wireless router assigns IP)
o Printserver via LAN (wireless router assigns IP)
o NAS via LAN (static IP, option set in NAS setup)

The question: does my computer need a firewall? I am behind the cable modem and my DDWRT router. Is a firewall redundant and a waste of time?

Thanks!

FE

A better question is what do you want to use a firewall for exactly ?

IMO if you are behind a router, and have not forwarded any ports from your router, you do not need to install any additional firewall.

Actually the firewall in Linux is iptables . Firestarter, UFW, GUFW, etc are merely config tools.

---

### Post by sasho_zl on 2009-08-05
One thing is for sure - the firewall will not harm your system in any way. You can see some instructions that I  have wrote here - [http://ubuntuforums.org/showthread.php?p=7736369#post7736369](http://ubuntuforums.org/showthread.php?p=7736369#post7736369)

---

### Post by fisheater on 2009-08-05
Indeed.

I was setting up my firewall to be a good and safe computer user, even though it sounds like I do not need to.

Removing firestarter will be easy, how do I get rid of my rules that I set up with firestarter? Do I then need to turn off my firewall?

My router (DDWRT) has IP tables in it, that should suffice my firewall needs.

Thanks for you input.

FE

---

### Post by rookcifer on 2009-08-05
> **fisheater said:**
> Hi all,

The great debate in my mind continues. Activate or not to activate a firewall on my unbuntu 9.04. (I am very new to linux, and searching gave a mixed answer)

The setup:

Cable internet modem
- wireless router (with DDWRT v24-SP1)
o laptop 1 - wireless (wireless router assigns IP)
o laptop 2 - wireless (wireless router assigns IP)
o Desktop via LAN cable (wireless router assigns IP)
o Printserver via LAN (wireless router assigns IP)
o NAS via LAN (static IP, option set in NAS setup)

The question: does my computer need a firewall? I am behind the cable modem and my DDWRT router. Is a firewall redundant and a waste of time?

Thanks!

FE

Yes, the firewall is redundant and a waste of time.  DD-WRT is Linux and uses the exact firewall that is used in Ubuntu (Iptables).  Just be sure the firewall on your router is blocking all incoming and you will have nothing to worry about.

---

### Post by lisati on 2009-08-05
> **Stevie78 said:**
> Ive installed Firestarter through Synaptic just for peace of mind. 
Firestarter, UFW and similar aren't firewalls as such, they're GUI configuration tools for the iptables firewall.

---

### Post by Randomperson_1000 on 2009-08-05
iptables is installed on default with the policy of deny incoming and allow outgoing connections. For most people this is okay. You area actually running a firewall already. If you are behind a router then you dont really need a firewall.

However i reccomend you learn iptables because it will only enchance ur knowledge of tcp/ip and firewall systems.

---

### Post by fisheater on 2009-08-05
Thanks everyone! 

/close topic/

FE

---

### Post by The Cog on 2009-08-06
> **Randomperson_1000 said:**
> iptables is installed on default with the policy of deny incoming and allow outgoing connections. For most people this is okay. You area actually running a firewall already. If you are behind a router then you dont really need a firewall.

Wrong. The default configuration for iptables (in a new installlation) is to allow all packets both incoming and outgoing. You can verify this by using the command [b]sudo iptables -nvL[b] on a freshly installed system.

I agree with other posters that installing a firewall is a waste of time and effort unless both the following are true:
* You install a service that listens for incoming connections
* You want to restrict access to that service to certain known IP addresses.
If you don't install a service then a firewall is pointless. If you don't know which IP addresses you want to permit or deny, then you have to permit all of them and again, your firewall is pointless.

The reason for needing a firewall on Windows is that Windows has so many listening services that are otherwise difficult to find and shut down. That's not the case on Linux - Linux does what **you** want, not the other way around.

---

### Post by kg84 on 2009-08-06
> **The Cog said:**
> 

I agree with other posters that installing a firewall is a waste of time and effort unless both the following are true:
* You install a service that listens for incoming connections
* You want to restrict access to that service to certain known IP addresses.
If you don't install a service then a firewall is pointless. If you don't know which IP addresses you want to permit or deny, then you have to permit all of them and again, your firewall is pointless.


If that's the case then, then a firewall would still be good to have, if for no other reason than to log incoming failed connection attempts, scans etc. If of course, you are interested in keeping an eye on this sort of thing.

(I have been busy for the last two days trying to get my head around iptables - its slowly starting to make sense :) )

---

### Post by bodhi.zazen on 2009-08-06
> **kg84 said:**
> If that's the case then, then a firewall would still be good to have, if for no other reason than to log incoming failed connection attempts, scans etc. If of course, you are interested in keeping an eye on this sort of thing.

(I have been busy for the last two days trying to get my head around iptables - its slowly starting to make sense :) )

See my first post on this thread =)

I agree that firewalls can be helpful, but you need to answer the question :

What do you want to use a firewall for.

In your case, monitoring network traffic, IMO, snort is a better tool.

If you want to learn iptables, would you mind looking at this ?

[http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

It is a work in progress , but it is targeted to new users so any feedback you wish to give would be appreciated (PM or email it to me).

The next sections I should work on are :

1. Breaking it into a few separate pages.

2. Perhaps more on logging.

3. I need to work on NAT (one-to-one , many-to-one, etc).

---

### Post by kg84 on 2009-08-06
> **bodhi.zazen said:**
> See my first post on this thread =)

I agree that firewalls can be helpful, but you need to answer the question :

What do you want to use a firewall for.

In your case, monitoring network traffic, IMO, snort is a better tool.

If you want to learn iptables, would you mind looking at this ?

[http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

It is a work in progress , but it is targeted to new users so any feedback you wish to give would be appreciated (PM or email it to me).

The next sections I should work on are :

1. Breaking it into a few separate pages.

2. Perhaps more on logging.

3. I need to work on NAT (one-to-one , many-to-one, etc).

Hello bodhi.zazen...

Yep. I read your tutorial 2 nights ago and last night, I printed it off so that I can read and mark it with questions / things I dont understand. I'll be happy to provide you with feedback on the tutorial once I start to get a handle on iptables.

I have also had a read of this: [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

Your statement regarding the necessity for a firewall is noted (as was The Cog's). This makes perfect sense to me now that I understand how Linux is different to WIN with respect to services listening on ports. Still, I would like to get to know iptables more, for no other reason than I am finding it interesting. 

Can I run Snort whilst running iptables? This too, I will have a look at.

I have a few questions arising from your tute already (just regarding things that I didnt fully understand when I read it). I will hang on to these for now, until I have done some more reading and then proceed to ask the questions here.

Cheers.

---

### Post by bodhi.zazen on 2009-08-06
Yes you can run snort with / along side iptables.

Happy reading =)

---

### Post by lisati on 2009-08-06
> **bodhi.zazen said:**
> 
What do you want to use a firewall for.

That is a good question to ask, as unrealistic expectations of any software can be an incredible waster of time, particularly if there's a better solution to be found in other software.

---

### Post by kevdog on 2009-08-06
> **Randomperson_1000 said:**
> iptables is installed on default with the policy of deny incoming and allow outgoing connections. 


Actually this isnt true -- its set to allow all incoming and outgoing connections -- the default packet policy for INPUT and OUTPUT is ACCEPT.

---

