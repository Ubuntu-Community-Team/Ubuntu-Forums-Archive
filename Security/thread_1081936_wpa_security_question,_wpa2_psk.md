---
title: "wpa security question, wpa2 psk"
date: 2009-02-27
forum: Security
---

### Post by dapim on 2009-02-27
is that wpa secure? 
or somebody can spy or get into my network if i used this?

wpa2 psk , is this secure ? totally prevent some others people to go into?


thanks

---

### Post by kdcoetzee on 2009-02-27
> **dapim said:**
> is that wpa secure? 
or somebody can spy or get into my network if i used this?

wpa2 psk , is this secure ? totally prevent some others people to go into?


thanks


WPA2 is very secure, WPA is not bad ether. just don't use WEP.

If I have the time and resouces, I would get in.
but its very very hard with any of the WPA. 

Just don't use WEP.

---

### Post by Kevbert on 2009-02-27
WPA and WPA2 are not bad. If you're using a wireless router have you changed the default password for it ? (as if anyone can see it they can potentially take control of it). Another thing you might want to try is setting up a limited access list to the router.

---

### Post by kevdog on 2009-02-27
wpa2 right now is the only bastion of security, now that even weakness in wpa have been exploited -- although through a crude dictionary attack method.  A visit to the aircrack site will give you the details.  In either method -- use a really long and random password, since attacks on either method really on dictionary based attacks.  Setting limited access to the router (ie MAC filtering) is one additional layer of assumed security, however its really easy to sniff client's MAC addresses connected to the particular router via kismet or other such program.  You would then be able to clone the particular client's MAC address, and then forcibly boot them from the router and then reconnect in a masquerading fashion.

---

### Post by Kevbert on 2009-02-27
kevdog, how does kismet find MAC addresses ? Can it just sniff out information over the air ? Just interested. Would non-broadcast of name stop this ?
Thanks in advance.

---

### Post by wirelessmonkey on 2009-02-27
> **Kevbert said:**
> kevdog, how does kismet find MAC addresses ? Can it just sniff out information over the air ? Just interested. Would non-broadcast of name stop this ?
Thanks in advance.


MAC addresses are transmitted between the router and the NIC, this is a basic requirement to create a TCP/IP connection. Not broadcasting the SSID would not affect this in any way.


wm

---

### Post by Hobgoblin on 2009-02-27
WPA or WPA2 with a random generated key (not one based on real words, even with some of the letters replaced with numbers) is as secure as you need.

If someone wanted to break in it would be easier for them to break into the property and physically access the network.

---

### Post by joey-elijah on 2009-02-28
I don't think someone will sit in your street and launch an attack on your router, spend hours waiting for your WPA password to be 'guessed' and then surf on with a very lame connection.

Just to put things in perspective.

---

### Post by Thirtysixway on 2009-02-28
Most people who are trying to lift network access will avoid any type of wpa encryption and look for either open or wep networks.

I'm running wpa on my home network right now because I was (for some reason) having issues connecting computers to wpa2.  I might turn it back on when I have time to figure it out.  


> 
Besides the stricter encryption requirements, WPA2 also adds two enhancements to support fast roaming of wireless clients moving between wireless access points.  PMK (Pair-wise Master Key used for each session between an access point and wireless client) caching support in WPA2 allows you to reconnect to an access point that you&#8217;ve recently connected to without the need to re-authenticate.  Pre-authentication support in WPA2 allows a client to pre-authenticate with the access point toward which it is moving, while maintaining a connection to the access point it&#8217;s moving away from.  This new capability allows the roaming to occur in less than 1/10th of a second while a traditional roam without PMK caching and pre-authentication would take more than one second.  Timing-sensitive applications like Citrix, video, or VoIP will all break without fast roaming.


[http://blogs.zdnet.com/Ou/?p=67](http://blogs.zdnet.com/Ou/?p=67)

---

