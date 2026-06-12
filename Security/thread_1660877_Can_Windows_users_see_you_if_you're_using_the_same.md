---
title: "Can Windows users see you if you're using the same connection?"
date: 2011-01-06
forum: Security
---

### Post by 3602 on 2011-01-06
Thought about posting in the Networking board, but I believe this is a much more security-oriented thread.
So let's say I bring my computer to a public place, say a library with one open, public, shared wireless network. I connect to that network. Let's assume that everyone else who's connected is using Windows. Can they see my computer (through Network Manager or other software) and attack it (SYN flood or something)? Or does it depend on the network settings?
Thank you very much.

---

### Post by mail2345 on 2011-01-06
You will need samba(windows file sharing service) installed to be seen normally, and even then there is probably an option to disable visibility.

If you happen to be running any services, or have ping respond on (default), port scanners can find your computer. To fix that, setup a firewall rule to ignore inbound connections from any host you don't want to connect, and disable ping reply. This is probably not worth the effort(see the next line).

You can be found with packet sniffers and the like if you connect at all, but nothing can be done about that.

---

### Post by bodhi.zazen on 2011-01-06
> **3602 said:**
> Can they see my computer (through Network Manager or other software) and attack it (SYN flood or something)? Or does it depend on the network settings?
Thank you very much.

Of course they can see and attack you. You can be seen and attacked any time you connect to a network and "the internet".

I suggest you relax though as this is not windows and you are likely to be invulnerable to most things.

On untrusted networks, such a a public wireless access point, I activate my firewall and tunnel traffic over ssl (https) or ssh as the biggest threat, IMO, unique to such a network, is a packet sniffer (thus the encryption).

---

### Post by HermanAB on 2011-01-06
Howdy,

On WiFi, everyone can sniff your packets, but if they are encrypted with WPA, then they won't know what the packets contain.  

Anyhow, if you run Ubuntu, then you need not fear the average Windows Joe.  It is the non-average fellow Linux user that you need to fear.

Remember, you are *not* paranoid, if they really *are* after you...

---

### Post by 3602 on 2011-01-06
> **bodhi.zazen said:**
> 
On untrusted networks, such a a public wireless access point, I activate my firewall and tunnel traffic over ssl (https) or ssh as the biggest threat, IMO, unique to such a network, is a packet sniffer (thus the encryption).

What is this, UFW?

---

### Post by bodhi.zazen on 2011-01-06
> **3602 said:**
> What is this, UFW?

[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

---

### Post by 3602 on 2011-01-06
> **bodhi.zazen said:**
> [https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

See, I read that actually (from your post in the Firestarter thread) and I don't understand a thing. So I install this and my ports will be open while they're closed by default?

---

### Post by bodhi.zazen on 2011-01-06
> **3602 said:**
> See, I read that actually (from your post in the Firestarter thread) and I don't understand a thing. So I install this and my ports will be open while they're closed by default?

Sounds as if you do not understand the basics of firewalls and ports.

Servers listen on ports, and if a server is installed and listening for a connection the port is open.

By default, Ubuntu has no significant listening servers, so all ports are closed, and there is nothing to firewall.

If you install Apache, it will listen, and thus open port 80.

You can then firewall port 80 or limit connections with a firewall.

If you do not want to do any reading, as I have said, open a terminal and enter

```
sudo ufw enable
```

That will enable your firewall, although it is almost certainly overkill.

If you want to read, start with the security sticky.

Then read:

[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

[https://wiki.ubuntu.com/ZeroConfPolicySpec](https://wiki.ubuntu.com/ZeroConfPolicySpec)

If you have a specific question, ask, but you are asking very basic and broad questions with that last post.

---

### Post by 3602 on 2011-01-06
I read the security sticky, three times actually, and that's why I'm interested in all this. In Windows I didn't even have a firewall, because the router has stuff built-in and I never bring that computer outside. Now I installed Firestarter, removed Firestarter (through Central, I clicked Remove). Do I need to "purge" Firestarter using your command?  The goal of all this is that I don't want other users on the same network (say a library) to see me. Now I understand packet sniffers (setting-up the router makes you read things, hidden SSID and such), then if by default all ports are closed, would installing additional software (UFW) encrypt my connection, as you have said. Does UFW do this? If so, how to configure it to do so? If not, what other software can?

---

### Post by bodhi.zazen on 2011-01-06
You need to use the command line, re-install, and then purge firestarter.

If you simply remove firestarter, it leaves configuration files which conflict with ufw, thus the need to purge.

This is an old firestarter bug and as firestarter is no longer maintained will not likely be fixed any time soon.

A firewall is for managing network traffic in and out of your computer and enabling your firewall does not make you invisible. Due to the nature of "the internet" there is no such thing as being invisible. As long as you are connected to the wireless access point you are visible.

Encrypting your traffic is another issue. Normally one does this by configuring the wireless access point to use encryption (WEP and WPA). This traffic can still be sniffed and decrypted.

You can do two things

1. Connect to a server using ssl (https). For example, 

[https://help.ubuntu.com/](https://help.ubuntu.com/)

Notice the "https" in the url ? Notice the little yellow lock icon in firefox ? This traffic is encrypted.

2. Since not all servers user https by default (most do not) you can tunnel your traffic over ssh (which encrypts the traffic).

See : 

[https://calomel.org/firefox_ssh_proxy.html](https://calomel.org/firefox_ssh_proxy.html)

This  of course requires you have installed and secured a ssh server somewhere, lol.

3. You can tunnel other communications over ssh, or you can install VPN.

4. You can use any of a number of proxy servers, including TOR.

I think a better question is why you think any of this is necessary for security ? Do you think someone at the library is going to specifically target you ?

---

### Post by 3602 on 2011-01-06
Nah, just for peace of mind (read: paranoia).
I knew https protocol. Thanks for the info. I'll look into the SSL.
However what are the "Use TLS" and "Use SSL" built-in in Firefox?

---

### Post by bodhi.zazen on 2011-01-06
use ssl will make firefox use ssl if it is available (if the server uses both http and https).

---

### Post by 3602 on 2011-01-06
Thank you for your info. They should help me a lot.

---

### Post by littlepeon on 2011-01-08
it's really not your system that you need to protect in these settings--its your data that you are transmitting--mostly in the clear---thru the airwaves to this open internet access point.
someone litterally can sit in the middle, sniff the packets being transmitted and recreate what ur seeing on your screen if you aren't using ssl.
most services will use this for logins--but then transmit the data IN THE CLEAR.
for another demonstration of this--goto youtube and there are tutorials on HOW to do this.

check this out:

[http://www.youtube.com/watch?v=eUyrMVkRTlI](http://www.youtube.com/watch?v=eUyrMVkRTlI)


edit:

another tutorial on what can happen in an internet cafe and how to use ssh to prevent it:

[http://www.youtube.com/watch?v=oZC6pro3O1g&playnext=1&list=PLBB779015F89B8B23&index=12](http://www.youtube.com/watch?v=oZC6pro3O1g&playnext=1&list=PLBB779015F89B8B23&index=12)

---

### Post by 3602 on 2011-01-08
OK. That's on an "open", unsecured connection, or does it apply to all connections?
The places that I frequent infrequently use a secured connection, some WEP, some WPA.

---

### Post by chak2005 on 2011-01-08
> **3602 said:**
> OK. That's on an "open", unsecured connection, or does it apply to all connections?
The places that I frequent infrequently use a secured connection, some WEP, some WPA.

Any and all wireless connections are vulnerable to being sniffed. Any information you transmit over the airwaves on a network can be intercepted by anyone on the same network as you with very little network know how.  Encrypted networks deter unauthorized access, once someone is authorized, they can start sniffing. If you want encryption for public places use SSH or a VPN.

I use a windows laptop for most of my mobile endeavors. Though I have a linux  box at home running a radius and file server. So when I am out over a  network I do not know I SSH proxy into my linux box and filter all my  traffic through that. It encrypts my internet traffic to everyone at starbucks or  at a public place and I do not have to worry about someone stealing my  passwords or looking at my browsing history. :popcorn:

Some other bits of information to strengthen wireless security for a home network, this is more just for your general knowledge if you also manage a wireless router at home:

Never leave your router unencrypted. While someone may just steal internet from you, it is more likely someone will hop on and use it to do illegal activity example being downloading/ torrent seeding movies/music over your connection and the MIAA and RIAA will go after you. 

Do not use WEP if you can help it. Vulnerabilities in its implementation make it very easy to crack within minutes. 

At home use WPA2-PSK (AES only) for your wireless network with a 12+ character pass-phrase consisting of Upper and lower case letters and numbers. (symbols too if your router will allow) This will stop 99.9% of potential malicious users looking to use your internet for free or illegal activity. Also do not tell the password to everyone, as that is the weakest link.

If you want over kill you can also use WPA2-ENT with EAP-*TLS* though that will take more time to set up and is not needed unless you have a large office or have multiple users in charge of guarding national secrets.  Since it involves setting up a public key infrastructure and the use of certificates. Not hard, but a little intimidating.

---

### Post by 3602 on 2011-01-08
I have no computer at home and I do have WPA2-Personal with a mixed TKIP and AES. That said, I can't setup a point machine and tunnel to that when I'm outside.
I'm speaking of public access points. A local commerce has an encrypted network, but the SSID and password is stuck on tables, so that.
Also torrenting is not illegal. But let's not go there.

---

### Post by littlepeon on 2011-01-09
5 years ago, when i used to wardrive (google it if you don't know what that is) WEP took 15 minutes to crack at most. WPA was just becoming available and it took a little longer--sometimes 1-3 hours before it was cracked. WPA2 is more secure and although i'm sure it can be cracked, it would take a while.

LOL---- re-read chak's post----he did NOT say that torrents were illegal, he said that you should secure ur internet so that an internet thief wouldn't use ur internet connection for illegal activity....(an internet thief isn't going to care if the torrents he is sharing are legal (ex. linux distros) or illegal (ex. the latest harry potter movie))...the point of his statement is that the 'internet police' --mpaa/riaa would come after YOU .....and you would have to prove that it wasn't your computers doing the illegal activity that YOUR router was connected to.

good luck
-peon

---

