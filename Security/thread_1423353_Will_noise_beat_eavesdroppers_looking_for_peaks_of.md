---
title: "Will noise beat eavesdroppers looking for peaks of traffic?"
date: 2010-03-06
forum: Security
---

### Post by Ulysses_ on 2010-03-06
Say we want to post anonymously to a public forum like linuxquestions. We can do it through a service like [https://proxify.co.uk/](https://proxify.co.uk/). This uses a secure link so any eavesdropper in my LAN cannot see the url I am connecting to.  

If this eavesdropper in my LAN suspects I am posting on linuxforums.com, they can look at times when my suspected posts appear in this public forum, and compare them with peaks in the traffic from my computer, and if the times match, it's a strong indication I am the same person.

If I somehow fill the virtual private connection with a dummy data stream, can the eavesdropper still tell I am posting to linuxquestions?

---

### Post by uRock on 2010-03-06
If you flood your LAN with noise, your router will bog down and so will your NIC. Secure your network. If you are "borrowing wireless," then you are at the mercy of the owner and the law. TCPDump can see every packet on the network and a knowledgeable operator of said software can find anything he/she wants. Noise such as that made by port scanners are obvious and easy to ignore.

---

### Post by Ulysses_ on 2010-03-06
> **iRock said:**
> If you flood your LAN with noise, your router will bog down and so will your NIC.

People put up with long delays if that is what it takes to be anonymous with TOR.  By the way, it's only my link to the internet that I want to flood, only the internet side of the router will bog down.  

But I wonder, will there still be peaks in the traffic traffic when you post to the forum over an adsl link that also carries another very demanding stream?

> TCPDump can see every packet on the network and a knowledgeable operator of said software can find anything he/she wants. Noise such as that made by port scanners are obvious and easy to ignore.

Thanks, so is there any way to put both connections (the useful connection to the forum and the noise stream) over one encrypted connection so it is impossible to tell them apart?  I thought that's what a VPN does, it prevents TCPdump from telling what's going on.

---

### Post by OpSecShellshock on 2010-03-06
VPN traffic is encrypted within the tunnel between your home network and the VPN server. Beyond that it's the same as any other connection, so it will depend on the protocol and the data being passed. People who have access to the VPN server's logs can see your home IP and the IP that the server has assigned to you, but if they're monitoring outgoing connections from that point it can hardly be called eavesdropping, since it's their network. If you have an agreement with them that says they won't do that, you're fine no matter what you do. If it's your employer's network, you are bound to their policy as long as you use their stuff.

So I guess it's a question of what kind of network you're on. The owner of the LAN, by definition, can't "eavesdrop" since it's their stuff (unless you have a contractual relationship that says otherwise). If it is your LAN, then as long as you follow best practices you can be fairly certain that no one is snooping (at least between your devices and your ISP's connection). You should know that increasing the noise won't deter anyone who is dedicated, but might make someone who is lazy or just not that interested in what you're doing give up. Either way, I'd think you and others on your LAN would be put off by it more than your would-be spy.

---

### Post by Ulysses_ on 2010-03-06
> **OpSecShellshock said:**
> if they're monitoring outgoing connections from that point it can hardly be called eavesdropping, since it's their network. If you have an agreement with them that says they won't do that, you're fine no matter what you do. If it's your employer's network, you are bound to their policy as long as you use their stuff.

Don't forget, it is an eavesdropper in my LAN I want to prevent telling it is me posting on the forum.  My IP becoming available to the VPN server ([proxify.co.uk]("https://proxify.co.uk/")) owner is no problem.  Even my IP leaking to the forum by means of javascript is not much of a problem either.

> You should know that increasing the noise won't deter anyone who is dedicated, but might make someone who is lazy or just not that interested in what you're doing give up.If someone is dedicated, what are the technical means to tell if the VPN link contains just the noise stream or the noise stream and my occasional data?

---

### Post by Ulysses_ on 2010-03-06
This may be in fact a math question, does encrypted data have different statistical properties than encrypted true noise?  

If yes, then perhaps the eavesdropper can detect the times when data packets appear and compare them with the times of posts on the public forum.

---

### Post by uRock on 2010-03-06
Is there a truck sitting outside your house with little radars on top?

---

### Post by Ijan on 2010-03-06
Ulysses_: You could ask the guys over at the Tor project. They should know what is possible in terms of time based side channel attacks on encrypted network traffic. There has been some research going on in that field around their software IIRC.

[edit]
Oh, and my uniformed guess on your scenario: Depending on stuff like the predictability of the forum's webserver, it's traffic load etc. - but probably possible.
[/edit]

---

### Post by tgalati4 on 2010-03-06
You mean the panel van that says "Flower Delivery"?

---

### Post by Ulysses_ on 2010-03-07
> **Ijan said:**
> Ulysses_: You could ask the guys over at the Tor project. They should know what is possible in terms of time based side channel attacks on encrypted network traffic. There has been some research going on in that field around their software IIRC.

[edit]
Oh, and my uniformed guess on your scenario: Depending on stuff like the predictability of the forum's webserver, it's traffic load etc. - but probably possible.
[/edit]

What if the data is put inside the dummy stream. Then there would be no need to flood the internet connection because there would be no peaks to hide, and end-to-end timing attacks would be  challenged as there would be no detectable start or end of useful data packets because there would be no multiple connections that start and end, only one.

There must be software that can pass several connections through one connection already.  Anyone know of such software?

---

### Post by Kinstonian on 2010-03-07
> **Ulysses_ said:**
> What if the data is put inside the dummy stream. Then there would be no need to flood the internet connection, no peaks to hide, and end-to-end timing attacks would be  challenged as there would be no detectable start or end of useful data packets, there would be just a single connection.

There must be software that can pass several connections through one connection already.  Anyone know of such software?

You may be thinking of [Covert Channels](http://en.wikipedia.org/wiki/Covert_channel#Data_Hiding_in_LAN_Environment_by_Covert_Channels).  However, in order for them to work, both sender and receiver must use additional software.  It's not like you can just start browsing websites.  Also, some of the covert channels such as [Loki](http://en.wikipedia.org/wiki/ICMP_tunnel) are pretty easily detected with something like Snort.  Others may require more detailed analysis of the communication.

---

### Post by Ijan on 2010-03-07
> **Ulysses_ said:**
> 
There must be software that can pass several connections through one connection already.  Anyone know of such software?

That probably depends bery much on the level of sophistication you want to protect yourself against. Running a Tor-relay will probably generate some encrypted traffic you can possibly hide in: [https://wiki.torproject.org/noreply/TheOnionRouter/TorFAQ#RelayAnonymity](https://wiki.torproject.org/noreply/TheOnionRouter/TorFAQ#RelayAnonymity)

---

