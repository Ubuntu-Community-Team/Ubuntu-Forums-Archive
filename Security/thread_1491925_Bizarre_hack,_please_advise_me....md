---
title: "Bizarre hack, please advise me..."
date: 2010-05-24
forum: Security
---

### Post by mark-9- on 2010-05-24
Hello,

First off, this not a joke/troll or anything else. I just want to understand some very bizarre behavour I saw on my Ubuntu box yesterday (current LTS version, fully patched)

I have a WiFi network (secured by WPA2, and a 20 character random password). I left an instance of Firefox open on some ubuntu related pages, and a root shell open. Since I am the only person in my flat, leaving the shell open seemed ok!

I left my PC for a few hours, and in that time I am 100% certain no-one physically touched my PC. However on my return I found that a command had been entered, from memory these were:

- systemroot/cmd32.exe
- an attempt to get IEXPLORE.exe from an FTP server
- an attempt to DEL the old IEXPLORE

**I am aware those are windows commands! **Which is why they failed to do anything. But what concerns me is they appeared in MY ROOT SHELL WINDOW.

I can only guess that someone managed to break the WPA2 on the WiFi (which puzzles me as it is a long random key), then somehow get root on my Ubuntu desktop...!!

Another oddity is those commands appeared on the screen, but not in the .bash-history : does that mean they were copied and pasted? Not typed?

Anyone got any ideas what happened??? I am more than a little concerned as the reason I was using Ubuntu over windows was the "security" !

As as side note, how is that someone could hack WPA2 with a strong password, and then fail to realise it wasn't a windows box? Utterly bizarre.

Any help in what I should do to stop this re-occurring would be appreciated.

Cheers

---

### Post by Grenage on 2010-05-24
Almost certainly, VNC.  I presume you have remote desktop listed in your startup apps, and a weak or non-existent password.

System/Preferences/Startup Applications.

---

### Post by mark-9- on 2010-05-24
Thanks for the reply : thinking about it more,  a remote desktop does make sense.

What I still don't understand is how someone could crack a long, random WPA (not WPA2) password on the Wifi ... does anyone know if WPA is vunerable to attacks? It is a Linksys router, WRT54G.

---

### Post by mhgsys on 2010-05-24
> **mark-9- said:**
> Thanks for the reply : thinking about it more,  a remote desktop does make sense.

What I still don't understand is how someone could crack a long, random WPA (not WPA2) password on the Wifi ... does anyone know if WPA is vunerable to attacks? It is a Linksys router, WRT54G.

Erhm , Yes.: It is.

I'm not sure if it's ok to provide information or discuss about aircrack etc on these forums, 
But here's a hint; [http://www.google.com/search?client=ubuntu&channel=fs&q=crack+wpa&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=crack+wpa&ie=utf-8&oe=utf-8)

---

### Post by Grenage on 2010-05-24
> What I still don't understand is how someone could crack a long, random WPA (not WPA2) password on the Wifi ... does anyone know if WPA is vunerable to attacks? It is a Linksys router, WRT54G.

They wouldn't need to; they'd access your computer over not internet, not directly through the wireless.

WPA/WPA2 et cetera only protect against a connection to your network via wireless devices.

---

### Post by mark-9- on 2010-05-24
Thanks for the replies ! :-)

My thinking was that the remote desktop connection was made on the local network (hence my concern about WPA)

The Linksys does NAT and (supposedly) firewall. Surely a VNC connection could not be initiated from outside the LAN ?

EDIT: Just found these, which are exactly what happened to me:

[http://ubuntuforums.org/archive/index.php/t-980832.html](http://ubuntuforums.org/archive/index.php/t-980832.html)
[http://forums.penny-arcade.com/showthread.php?t=75759](http://forums.penny-arcade.com/showthread.php?t=75759)

Certainly I will be removing that pesky VNC. I am suprised that VNC is not LAN-only by default. Seems to me this is a risky default? 

I will now be setting my paranoia dial to 11, and it was previously at 10 ;-)

---

### Post by Grenage on 2010-05-24
> **mark-9- said:**
> Thanks for the replies ! :-)

My thinking was that the remote desktop connection was made on the local network (hence my concern about WPA)

The Linksys does NAT and (supposedly) firewall. Surely a VNC connection could not be initiated from outside the LAN ?

Technically, it wasn't.  Your VNC server used uPnP with the router, which automatically forwarded the port(s) to your machine.

---

### Post by wojox on 2010-05-24
Sounds like script kiddies. Have you ever played around with Wireshark?

---

### Post by mark-9- on 2010-05-24
Thanks Grenage - and everyone else too. I had no idea VNC worked like that. Stupid me! 



[U]
[/U]

---

### Post by Rubi1200 on 2010-05-24
First off, read this:

[http://tldp.org/HOWTO/Security-HOWTO/after-breakin.html](http://tldp.org/HOWTO/Security-HOWTO/after-breakin.html)

Then, disconnect from the internet, turn off the router.

Restart your computer and look for signs of compromise e.g. strange files or folders, anything missing etc.

Look at the log files in /var/log especially auth.log and messages to see if there are signs of unusual activity.

If you are sure this was a one-off incident and that nothing major has been compromised then reconnect your router BUT use the cable and change your password to something secure. I repeat do not access the router via the web interface; plug it into your computer and reset it there first before going on the internet again.

If you are using remote desktop, VNC, or ssh; secure it.

Read this:

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

If you have more questions, people here will try and help.

---

### Post by doas777 on 2010-05-24
my best advice on UPNP, is to jsut disable it on the router. I don't want apps opening ports without my express intervention.

---

### Post by Grenage on 2010-05-24
> **mark-9- said:**
> Thanks Grenage - and everyone else too. I had no idea VNC worked like that. Stupid me!__

Most people don't realise it; but it's not just VNC, many applications support and use uPnP.

---

### Post by Rubi1200 on 2010-05-24
Would you care to elaborate on some of the common applications that do this and how you would secure them?

---

### Post by wojox on 2010-05-24
> **Grenage said:**
> Most people don't realise it; but it's not just VNC, many applications support and use uPnP.

True that. Most bittorents are the same way.

---

### Post by Grenage on 2010-05-24
Torrent clients (deluge, etc) are prime examples, you'll find it under preferences. Even if the application does not list uPnP as an option, there's no guarantee it's not automatically attempted.

I'm with **doas777** on this one, it's best disabled.

---

### Post by Rubi1200 on 2010-05-24
Would you say that using an AppArmor profile for something like Transmission would do the job? 
Would it still be advisable to turn UPnP off in the router?

---

### Post by Grenage on 2010-05-24
I have never used AppArmor, nor know its workings well enough to say either way, bit you would at least have to have a profile for every program?  For me, it's just easier to turn uPnP off, and forward ports when required.

---

### Post by Rubi1200 on 2010-05-24
Thanks Grenage, I appreciate the input.
:)

---

### Post by bodhi.zazen on 2010-05-24
> **Rubi1200 said:**
> Would you say that using an AppArmor profile for something like Transmission would do the job? 
Would it still be advisable to turn UPnP off in the router?

It is easier to turn UPnP off.

Apparmor probably can not do this.

---

### Post by Rubi1200 on 2010-05-24
As it turns out uPnP was turned off by default in my wireless router.

@ bodhi.zazen

Two questions:

1. if uPnP was turned off, was Transmission port forwarding from the outset when I ran it?

2. if I add an AA profile from your link to etc.apparmor.d (does it go in the main folder or a sub-folder) do I just then use the enforce command to enable it?

Thanks in advance.

---

### Post by doas777 on 2010-05-24
I'm not sure AA is the correct response to this kind of issue. I would start by doing an audit of the firewall and try to determine how the access was made. then perhaps your wireless security, but that is pretty unlikely, unless you neighbor fancies themselves a 1337 hax0r.

---

### Post by bodhi.zazen on 2010-05-24
> **Rubi1200 said:**
> As it turns out uPnP was turned off by default in my wireless router.

@ bodhi.zazen

Two questions:

1. if uPnP was turned off, was Transmission port forwarding from the outset when I ran it?

2. if I add an AA profile from your link to etc.apparmor.d (does it go in the main folder or a sub-folder) do I just then use the enforce command to enable it?

Thanks in advance.

The second question first, yes use aa-enforce for the transmission profile.

The first question is a bit more complex. Connections are NEW, RELATED, or ESTABLISHED. You router should block NEW connections, but allow RELATED and ESTABLISHED.

With that piece of info, we would need to look at your network, ie port scan. You can port scan your router with shields up (we are interested in Open ports). You can portscan your LAN with nmap.

On your box you can monitor your network traffic with Wireshark.

---

### Post by Rubi1200 on 2010-05-24
> **bodhi.zazen said:**
> The second question first, yes use aa-enforce for the transmission profile.

The first question is a bit more complex. Connections are NEW, RELATED, or ESTABLISHED. You router should block NEW connections, but allow RELATED and ESTABLISHED.

With that piece of info, we would need to look at your network, ie port scan. You can port scan your router with shields up (we are interested in Open ports). You can portscan your LAN with nmap.

On your box you can monitor your network traffic with Wireshark.

Thanks.

I checked via ShieldsUp and it reports that all my ports are in stealth mode. I was just curious though how Transmission connects to the internet if uPnP was disabled and with no other firewall running than the one on my wireless router. Correct me if I am wrong, but I thought the firewall on the router only blocks incoming traffic?

I should add that I only use Transmission infrequently.

Again thanks.

---

### Post by bodhi.zazen on 2010-05-24
> **Rubi1200 said:**
> Thanks.

I checked via ShieldsUp and it reports that all my ports are in stealth mode. I was just curious though how Transmission connects to the internet if uPnP was disabled and with no other firewall running than the one on my wireless router. Correct me if I am wrong, but I thought the firewall on the router only blocks incoming traffic?

I should add that I only use Transmission infrequently.

Again thanks.

I would assume your router allow all outbound traffic.

For inbound traffic NEW connections are blocked. ESTABLISHED and RELATED connections are allowed (which is why you can browse the web). If all incoming connections were blocked you would not be able to connect to the internet as you would never get a response to ping or be able to use Firefox.

HTH.

If not, see the first few sections of this post :

[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

Read the entire post if you are interested.

---

### Post by Rubi1200 on 2010-05-24
Many thanks for the patient responses; much appreciated.

---

### Post by halloween2311 on 2010-05-25
To the original post,

If you are still worried about WiFi security, I would recommend using a longer pass phrase.  Yes 20 random characters is strong but WPA can use up to 63 characters. Since you only have to enter this once at initial setup, why not use the maximum amount?

I use multiple random password generators to generate portions of the pass phrase, copy and paste them together, then I change a few of the characters to random ones I think up to try and make it as unique as possible.

As a back up I save the new pass phrase to an encrypted thumb drive, hidden in a file of gibberish.

It's not paranoia if they are really after you!

---

