---
title: "IP (public) address question..."
date: 2008-05-23
forum: Security
---

### Post by Th3Professor on 2008-05-23
This is kind of a silly question but worth asking... the Monopoly game, or the "Atlantik" version, is one example of an application that very easily hands out your IP to other users online... is there:
A) a way to prevent the IP from showing in something like Atlantik (or other)?
and
B) any need for concern over the IP being very easily handed over to other users like that?

---

### Post by bwhite82 on 2008-05-24
First be sure that its actually your ip that is showing up in the game and not your ISPs. [http://www.whatismyip.com](http://www.whatismyip.com)

If it is, then yes, there is cause for concern. One route can be to play the game through a proxy server, effectively masking your IP for that of the proxy's. For instance, the tor-privoxy combo. Do note, however, that this combonation slows your net connection dramatically because all of your traffic will be going through multiple tor nodes.

Another route is to have a properly configured firewall, be it software-based or hardware-based. Ubuntu is pretty secure as default however.

---

### Post by FakeOutdoorsman on 2008-05-24
Another option is to create a SSH tunnel.  This would make your ip address appear to be from the machine you created the tunnel to.  It still shows an ip address of course.  You could create a tunnel any machine you have shell access to or even to a home router: [HowTo: SSH Tunnel Firefox]("http://ubuntuforums.org/showthread.php?t=723025")

---

### Post by brian_p on 2008-05-24
> **Th3Professor said:**
> This is kind of a silly question but worth asking... the Monopoly game, or the "Atlantik" version, is one example of an application that very easily hands out your IP to other users online... is there:
A) a way to prevent the IP from showing in something like Atlantik (or other)?

As aleady suggested: a proxy. But your enjoyment of the game will probably suffer.

> B) any need for concern over the IP being very easily handed over to other users like that?

What did you have in mind? You sound concerned and others are encouraging that concern. Why would you need to hide your IP? Has communication gone out of fashion?

---

### Post by Th3Professor on 2008-05-24
> **Soldierboy said:**
> First be sure that its actually your ip that is showing up in the game and not your ISPs. [http://www.whatismyip.com](http://www.whatismyip.com)

If it is, then yes, there is cause for concern. One route can be to play the game through a proxy server, effectively masking your IP for that of the proxy's. For instance, the tor-privoxy combo. Do note, however, that this combonation slows your net connection dramatically because all of your traffic will be going through multiple tor nodes.

Another route is to have a properly configured firewall, be it software-based or hardware-based. Ubuntu is pretty secure as default however.

I'm installing tor and privoxy now... I'll test them out.

What's a good choice for firewall?

> **FakeOutdoorsman said:**
> Another option is to create a SSH tunnel.  This would make your ip address appear to be from the machine you created the tunnel to.  It still shows an ip address of course.  You could create a tunnel any machine you have shell access to or even to a home router: [HowTo: SSH Tunnel Firefox]("http://ubuntuforums.org/showthread.php?t=723025")

Something like that atlantik game isn't played via firefox, or does that tunneling apply to all/any internet use?

> **brian_p said:**
> As aleady suggested: a proxy. But your enjoyment of the game will probably suffer.



What did you have in mind? You sound concerned and others are encouraging that concern. Why would you need to hide your IP? Has communication gone out of fashion?

Have in mind? ...just make the IP address private or show as something else to the public. I'm not particularly concerned, unless there's need to be, hence asking if there is any need for concern. The idea of privatizing the IP is simply a matter of appreciating and taking advantage of having one's own privacy... that is, that's at least what I'm aiming for.

---

### Post by brian_p on 2008-05-24
> **Th3Professor said:**
> Have in mind? ...just make the IP address private or show as something else to the public. I'm not particularly concerned, unless there's need to be, hence asking if there is any need for concern. The idea of privatizing the IP is simply a matter of appreciating and taking advantage of having one's own privacy... that is, that's at least what I'm aiming for.

Providing your IP address whilst participating in a game doesn't identify you or your place of residence so there's no cause for concern if you wish to be anonymous.

---

### Post by bwhite82 on 2008-05-24
> What's a good choice for firewall?

I utilize a hardware firewall myself. If you have an old, spare computer laying around, you can purchase another NIC for it and turn it into one. I recommend Smoothwall to accomplish this.

Having your IP exposed *is* a cause for concern. All it takes is for you to anger someone in the game, whether inadvertently or not, and you can be attacked or your machine compromised. It is not difficult to do. There's a program used for testing security on machines and servers called Nessus. Just read about that program and you'll know why.

-Cheers

---

### Post by Th3Professor on 2008-05-25
> **Soldierboy said:**
> I utilize a hardware firewall myself. If you have an old, spare computer laying around, you can purchase another NIC for it and turn it into one. I recommend Smoothwall to accomplish this.

Having your IP exposed *is* a cause for concern. All it takes is for you to anger someone in the game, whether inadvertently or not, and you can be attacked or your machine compromised. It is not difficult to do. There's a program used for testing security on machines and servers called Nessus. Just read about that program and you'll know why.

-Cheers

I don't see smoothwall in the repo, has it been ported to ubuntu (or debian)?

You mentioned nessus... would that be the client or nessusd?

---

### Post by Dr Small on 2008-05-25
SmoothWall is another distro:
[http://www.smoothwall.org/](http://www.smoothwall.org/)

---

### Post by bwhite82 on 2008-05-25
> I don't see smoothwall in the repo, has it been ported to ubuntu (or debian)?

You mentioned nessus... would that be the client or nessusd?

Yes, Smoothwall is another firewall-specific distro. Its sole aim and purpose it for being a firewall. You would install it on a separate computer that you may have laying around. You place it in between your modem and router.

The Nessus client interacts with NessusD (the server). You need both.

---

### Post by Th3Professor on 2008-05-26
...looks interesting... if I use a spare pc for firewall I will likely use OpenBSD instead, though I've bookmarked SmoothWall, will definitely look into it.

---

