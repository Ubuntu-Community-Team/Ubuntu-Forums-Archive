---
title: "rtorrent over VPN"
date: 2010-03-24
forum: Server Platforms
---

### Post by Heinrisch on 2010-03-24
Is it possible to limit rtorrent to only connect to the net through a VPN tunnel? That is, I want rtorrent to only run actively when it is connected to a specific VPN service so that all traffic from rtorrent is encrypted through that tunnel.

If the tunnel to the VPN is lost, I don't want rtorrent to access the net at all.

If it is possible, how is it done?


Original:
I want to run rtorrent over a vpn service and be sure that rtorrent only runs when I am connected to the vpn. Is that possible? If possible, how would it be done?

---

### Post by Heinrisch on 2010-03-25
Does anyone know?

---

### Post by spynappels on 2010-03-25
I'm not sure what you would do to achieve this, but remember that VPN tunnels will have much lower throughput generally because all traffic is normally encrypted and decrypted at either end of the tunnel. Your speeds WILL suffer.

---

### Post by Heinrisch on 2010-03-25
> **spynappels said:**
> I'm not sure what you would do to achieve this, but remember that VPN tunnels will have much lower throughput generally because all traffic is normally encrypted and decrypted at either end of the tunnel. Your speeds WILL suffer.

Please answer the question instead of questioning it. I know how VPN tunnels work.

---

### Post by mtecknology on 2010-03-25
1) Please read this link: [http://www.ubuntu.com/community/conduct/](http://www.ubuntu.com/community/conduct/)

2) Could you explain what it is that you actually want?
2a) If what you want is to tunnel the traffic over VPN, then just do that. Setup a port for your torrent client, forward the port over the VPN. Easy as pie. There's plenty on google about doing that.

3) Learn patience. Just because you have to wait a little while doesn't mean nobody will answer. It was most likely the bad question that caused nobody to answer you.

---

### Post by Heinrisch on 2010-03-26
> **mtecknology said:**
> 1) Please read this link: [http://www.ubuntu.com/community/conduct/](http://www.ubuntu.com/community/conduct/)

2) Could you explain what it is that you actually want?
2a) If what you want is to tunnel the traffic over VPN, then just do that. Setup a port for your torrent client, forward the port over the VPN. Easy as pie. There's plenty on google about doing that.

3) Learn patience. Just because you have to wait a little while doesn't mean nobody will answer. It was most likely the bad question that caused nobody to answer you.

1) I have read the ubuntu code of conduct and I don't see how it would be relevant in this case. 

2) I want to make sure that rtorrent runs when I am connected to a VPN and otherwise not. spynappels obviously understood the question but did not bother to answer it. His response was completely irrelevant and that is why I got upset. I have seen these kinds of responses from people who only want to get many posts as fast as possible and I am tired of it.
2a) I have tried using google but did not find anything, that's why I asked here.

---

### Post by spynappels on 2010-03-26
I did not answer, because I am not sure of the answer.

If you do not post more detail in the question you will get well-meaning individuals asking if you are sure this is what you want to do because of this or that consequence of doing it that way.

Brusque and rude replies will not get you any more answers. Courtesy will.

If you would like to give a little more background info on the situation you face, someone may be able to help you, or else suggest a different way of achieving the same goal.;)

---

### Post by Heinrisch on 2010-03-26
> **spynappels said:**
> I did not answer, because I am not sure of the answer.

If you do not post more detail in the question you will get well-meaning individuals asking if you are sure this is what you want to do because of this or that consequence of doing it that way.

Brusque and rude replies will not get you any more answers. Courtesy will.

If you would like to give a little more background info on the situation you face, someone may be able to help you, or else suggest a different way of achieving the same goal.;)

But you did answer the thread with an answer that was irrelevant. However, I will apologize, I did not mean to sound rude or attack anyone. I guess I have been hanging in the wrong message boards to much. I am sorry if I upset anyone, and I will try to specify my questions a better in the future. 

What I want to do is limit rtorrent so that it can only access the net through the VPN tunnel and not otherwise. I want to route all my rtorrent traffic through the encryped tunnel. I will try to clearify in my original thread.

---

### Post by stlsaint on 2010-03-26
maybe im also lost on the question but why wouldnt you just connect to the torrent server, start rtorrent client, and when you disconnect from vpn then close the rtorrent client to prevent it from running when your not on it? Again it sounds so simple because im not sure about the question.

---

### Post by Heinrisch on 2010-03-26
> **stlsaint said:**
> maybe im also lost on the question but why wouldnt you just connect to the torrent server, start rtorrent client, and when you disconnect from vpn then close the rtorrent client to prevent it from running when your not on it? Again it sounds so simple because im not sure about the question.

rtorrent is going to run on my server, which is up 24/7. My assumption was that if the tunnel to the VPN server is lost, rtorrent will connect directly to the net. I want to prevent that.

---

### Post by spynappels on 2010-03-26
What VPN are you using?

In OpenVPN, you can run a script on establishment of a tunnel and another when the tunnel closes. in the UP script, start rtorrent and in the DOWN script you could then terminate the rtorrent process.

I don't know enough about IPSEC and other VPNs to know if this is possible using them.

---

### Post by Heinrisch on 2010-03-26
> **spynappels said:**
> What VPN are you using?

In OpenVPN, you can run a script on establishment of a tunnel and another when the tunnel closes. in the UP script, start rtorrent and in the DOWN script you could then terminate the rtorrent process.

I don't know enough about IPSEC and other VPNs to know if this is possible using them.

I have not specified the software yet, waiting for the new hardware :) Doing some testing on my old machine.

I did not think of using the VPN client to solve my problem but that seems reasonable. I was thinking that rtorrent might have some configuration parameter that limits the traffic to flow through only for example eth1, if eth1 is the established tunnel.

---

### Post by stlsaint on 2010-03-26
Yea you are looking for a script of some sort to tell rtorrent when to run. If openvpn has a built-in method of doing this than that would be the best route...or to hand write it.

---

### Post by spynappels on 2010-03-26
More than one way to skin a cat!

That's what I meant about looking at the problem from a completely different angle, once you know exactly what is required.

Have a look at OpenVPN, it is great if you are setting up your own VPN and can control all client access. If you want to use it to connect to other third party VPN end-points, it may not work for you though.

Hope it works out for you.:P

---

### Post by Heinrisch on 2010-03-26
> **spynappels said:**
> More than one way to skin a cat!

That's what I meant about looking at the problem from a completely different angle, once you know exactly what is required.

Have a look at OpenVPN, it is great if you are setting up your own VPN and can control all client access. If you want to use it to connect to other third party VPN end-points, it may not work for you though.

Hope it works out for you.:P

I'll do that and post a solution if I manage to get it up and running.

Thanks for the help! and sorry for me being an *** from time to time :P

---

### Post by spynappels on 2010-03-26
No Probs!

Have fun tinkering!

---

### Post by JCoster on 2010-03-26
I posted something almost identical to this the other day but received no responses so I'll reword the question on this thread...

Does anyone know how to run a script on the termination of a connection over network-manager-pptp?

Cheers,
JC

---

### Post by Melpomene on 2010-09-01
> **mtecknology said:**
> 
2a) If what you want is to tunnel the traffic over VPN, then just do that. Setup a port for your torrent client, forward the port over the VPN. Easy as pie. There's plenty on google about doing that.

I'm trying to do exactly that but I can't seem to find anything relevant on google. How is the "forward the port over the vpn"- part done ? 

I'm trying to get only my torrent client to use the VPN and not any of the other programs connected to the internet. At the moment I only seem able to route all my internet traffic through the VPN.

---

