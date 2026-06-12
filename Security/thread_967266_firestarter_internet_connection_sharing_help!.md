---
title: "firestarter internet connection sharing help!"
date: 2008-11-01
forum: Security
---

### Post by rhcm123 on 2008-11-01
This is a repost of a thread I posted in another forum, but I don't think it was the right place. Please read through and any advice would be much appreciated. (original thread here: [http://ubuntuforums.org/showthread.php?t=966796](http://ubuntuforums.org/showthread.php?t=966796))

 Cannot connect to the internet through firestarter

This must be my 20'th time attempting to use firestarter, and it is still not working.
I have several machines on my home network. My setup goes somthing like this

Internet - Verizon FiOS modem - router - Firestarter Machine - switch - Rest of network.

Now, anything plugged directly into the router or connected wirelessly works great.

Anything behind Firestarter... Nyet. Nothing. Zip. Zero. Nada. Badabing. Not a hair of internet.

All machines behind firestarter can ping each other fine, but they cannot ping the firestarter machine, or the internet!

I have internet sharing enabled on eth1 and am connected on a workning static ip on eth0 (i can connect to the internet on the firestarter machine)

All machines are running ubuntu 8.04 Desktop, except for the server, which is running 8.10.

Does anybody know what i am doing wrong?:confused:

---

### Post by hyper_ch on 2008-11-02
is there any reason why you installed firestarter first place?

---

### Post by randy78 on 2008-11-02
Go to the Policy tab, select Editing> Outbound and make sure that it's either set to Permissive or if you have it set to restrictive, that you have allowed ports 80 and 443 (at the very least).

Ubuntu doesn't have the nasty spyware that Windows does, and since you're already behind a router, you really have nothing to worry about.

Ubuntu doesn't have any services listening by default, so as long as your hardware firewall is turned on, there isn't really anything that Firestarter is going to do for you that your router isn't doing already.

I was among the "Oh my god, no anti-virus or firewall! I'm Doomed" crowd a couple of years ago when I first switched to Ubuntu, but since then I've learned quite a few things about network security and how hard it is to actually exploit and root a remote Linux box.

Security is a state of mind, and the weakest link of any setup is ALWAYS the user.

Check out the Ubuntu Security article by bodhi.zazen here:[http://ubuntuforums.org/showthread.php?t=510812]("http://ubuntuforums.org/showthread.php?t=510812")

Take Care
:popcorn:

---

### Post by rhcm123 on 2008-11-02
I was actually trying to setup firestarter as a project for an internet security demo (demonsrating various effects of packets to inept parents) but i guess i'll just use the linkysis router... sigh. It would have been fun too.

No, outbound is set to permissive, to answer your question.

---

### Post by randy78 on 2008-11-02
You should check out Smoothwall: [http://www.smoothwall.org/get/index.php]("http://www.smoothwall.org/get/index.php")

It sounds exactly like what you're looking for and is much more robust than Firestarter. Check out this review (older, but still relevant): [http://www.linux.com/feature/43249]("http://www.linux.com/feature/43249")

As for "demonstrating the effects of packets", set up the Smoothwall box and use it in conjunction with Wireshark to give a visual representation of how packets are filtered, packet inspection and analysis, etc.

Good luck :)

---

### Post by cariboo on 2008-11-02
If you don't mind setting up Internet connection sharing just using a script give Arno's iptables firewall. It is available in the repositories it is well commented and there is a setup script that runs during installation. You can also download it here:

[http://rocky.eld.leidenuniv.nl/](http://rocky.eld.leidenuniv.nl/)

I used to use this script not so much for the firewall but as a learning tool and for nat, when I switched from ipchains to iptables. I've been using a router for about 4 years and have forgotten most of what I learned using the script. :)

Jim

---

### Post by rhcm123 on 2008-11-03
> **randy78 said:**
> You should check out Smoothwall: [http://www.smoothwall.org/get/index.php]("http://www.smoothwall.org/get/index.php")

It sounds exactly like what you're looking for and is much more robust than Firestarter. Check out this review (older, but still relevant): [http://www.linux.com/feature/43249]("http://www.linux.com/feature/43249")

As for "demonstrating the effects of packets", set up the Smoothwall box and use it in conjunction with Wireshark to give a visual representation of how packets are filtered, packet inspection and analysis, etc.

Good luck :)

The problem with smoothwall is that you have to reformat your hard drive. I'm not particularly against that, but I would like to use that machine for other things (its got a 2 ghz processor and 1 gb ram) and I currently run compiling/long-term chore tasks on it.

---

### Post by rhcm123 on 2008-11-03
Oh, and by the way, i heard a myth that, on the network side of the firestarter machine, there has to be a hub, hub only. Is it okay if i use a switch?

---

### Post by randy78 on 2008-11-03
I don't fully understand what it is that you're trying to do...

"Show the effects of packets" makes no sense at all to me, unless you're talking about ARP poisoning, packet forging or something along those lines.
If you are trying to show why firewall rules should be enforced, why not do a vulnerability test?

You must be more forthcoming in what it is you're trying to accomplish, friend, as I can't read minds and it sounds to me like you're trying to pen-test their network to show why they should use a front-end to IpTables.

If you are trying to show the benefit of using a front-end to IpTables, then download GUFW, or read this on how to configure UFW :[http://www.ubuntugeek.com/ufw-uncomplicated-firewall-for-ubuntu-hardy.html]("http://www.ubuntugeek.com/ufw-uncomplicated-firewall-for-ubuntu-hardy.html")

---

### Post by randy78 on 2008-11-03
> **rhcm123 said:**
> Oh, and by the way, i heard a myth that, on the network side of the firestarter machine, there has to be a hub, hub only. Is it okay if i use a switch?

Okay... I see what you're doing.

You want to sniff network traffic.

Edit: it just hit me... disregard the above and check here: [http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html]("http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html")

---

### Post by rhcm123 on 2008-11-05
> **randy78 said:**
> Okay... I see what you're doing.

You want to sniff network traffic.

Edit: it just hit me... disregard the above and check here: [http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html]("http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html")

Yes. I am trying to sniff out who is sealing my wifi at night.
Not actually, I was trying to use firestarter program to protect my server node of our network, but I had not yet setup connection sharing!
Ok, this i'll actually work!!! :)

---

### Post by randy78 on 2008-11-05
;)

BTW, if somebody really is stealing your wifi, you can build an external directional antenna and use the MoocherHunter tool in the OSWA Assistant security distro! Comes within 6 feet of the culprit!:guitar:

Check it out here:[http://securitystartshere.org/page-training-oswa-moocherhunter.htm]("http://securitystartshere.org/page-training-oswa-moocherhunter.htm")

Scroll down for the video :)

---

### Post by rhcm123 on 2008-11-06
> **randy78 said:**
> ;)

BTW, if somebody really is stealing your wifi, you can build an external directional antenna and use the MoocherHunter tool in the OSWA Assistant security distro! Comes within 6 feet of the culprit!:guitar:

Check it out here:[http://securitystartshere.org/page-training-oswa-moocherhunter.htm]("http://securitystartshere.org/page-training-oswa-moocherhunter.htm")

Scroll down for the video :)

No, nobody was stealing the wi-fi :), but that looks really cool, so perhaps.... (I'm on WEP encryption and I have MAC filtering, so there is really no way to steal it)

---

### Post by randy78 on 2008-11-06
That type of thinking will get you in trouble, and you should really have WPA enabled...

WEP can be broken in just a couple of minutes (seriously, about 2 or 3 minutes) and your MAC address can be spoofed by an attacker looking to gain access to your network.

MAC filtering is great, but also disable SSID broadcasting, enable WPA encryption and use a long, random passphrase of at least 32 characters.

Even though WPA passphrases can be broken by a brute force attack, intruders trying to break a password like: >dQrf7]D#r95HEdIMVsG/Jj!XqkL27Ko aren't going to get anywhere fast.
Stay vigilant and remember to test your own networks for weaknesses every now and then,lock down what you can and change that passphrase up every 30-45 days.

EDIT: Make sure to use WPA2 as I just now read about this: [http://www.infoworld.com/article/08/11/06/Once_thought_safe_WPA_WiFi_encryption_is_cracked_1.html]("http://www.infoworld.com/article/08/11/06/Once_thought_safe_WPA_WiFi_encryption_is_cracked_1.html")

---

### Post by rhcm123 on 2008-11-07
Oh, my... I thought I was paranoid. :)
I've got another thread going about just basic connection sharing here:
[http://ubuntuforums.org/showthread.php?p=6126719](http://ubuntuforums.org/showthread.php?p=6126719)
Perhaps you could help me there too :).

And, even if they break into my WEP (which i have done my self with a perl script i got off a torrent file) they would have to know my mac address to be able to access the list of mac addresses on the router. And I am monitoring the clients on the network. All of my computer hostnames start with USSR (i.e. ussr-server or ussr-laptop) so that if i ever see a machine with annoying_neghibor-desktop i'll be sure to boot them off :)

---

