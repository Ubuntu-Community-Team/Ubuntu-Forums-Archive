---
title: "Swedish vpn service for €50/year"
date: 2007-09-07
forum: The Cafe
---

### Post by PartisanEntity on 2007-09-07
A friend of mine sent me a link to a Swedish service offering vpn for about €50/year. He has been testing it with his Mac and XP machines, using it for surfing and bittorrent.

Has anyone heard of this? Can it be set up with Ubuntu? Sounds interesting and the price is quite acceptable.

It is called relakks.com

Opinions?

---

### Post by PartisanEntity on 2007-09-13
I have been looking through the forum to find out how to connect Ubuntu to a vpn service, so far the methods I have found, don't seem to work with my current set up:

I connect to the net through Network Manager wirelessly to my router which is connect to my cable modem.

The methods I have found so far assume you are connected through ethernet.

Anyone have some experience with this or some good links and tutorials? I would really like to be able to use this service with UBuntu.

---

### Post by mips on 2007-09-13
Should be doable.

Look in the howto section for VPN, also google Ubuntu vpn. Might want to look at OpenVPN.

---

### Post by adl80l on 2007-09-13
I'm not sure if its does what your looking for,  but hamachi is a free vpn service.  They have windows and linux clients, but nothing for macs.

---

### Post by PartisanEntity on 2007-09-13
> **adl80l said:**
> I'm not sure if its does what your looking for,  but hamachi is a free vpn service.  They have windows and linux clients, but nothing for macs.

I have never heard of hamachi, will have to look into it, but a friend of mine is using relakks on his Mac for many things and is quite happy with it.

---

### Post by [h2o] on 2007-09-13
There's an openvpn and cisco-vpn plugin for NetworkManager. I have not tried them though, but they are installable from synaptic.

---

### Post by AriciU on 2007-09-13
Why do you need one?

It's not gonna give you better download speeds or stuff like that.

---

### Post by PartisanEntity on 2007-09-13
Well there is no specific need, I use TOR a lot too when I am surfing for example, I like having a number of tools and methods to keep my privacy and security, so when I read about Swedish privacy laws and this Swedish vpn service, and the idea of IP shifting it appealed to me and I wanted to try it out.

Anyway, I would like to let those interested know that I got it working thanks to [this post]("http://ubuntuforums.org/showpost.php?p=2662749&postcount=42"). I am using Ubuntu instead of Kubuntu so I simply substituted the applications with GNOME versions.

There is a very slight difference in speed, but for surfing it really is quite acceptable. IM's are working too, so is Azureus.

---

### Post by 23meg on 2007-09-13
> **PartisanEntity said:**
> I am using Ubuntu instead of Kubuntu so I simply substituted the applications with GNOME versions.


What exactly are they? And can you seamlessly switch between a VPN session and your normal connection? Any difficulties or problems with Network Manager?

---

### Post by PartisanEntity on 2007-09-13
Well instead of Knetwork Manager, Network Manager and instead of Kvpnc, vpnc. Then just follow the instructions in the post.

So far no issues at all with Network Manager, and the switch is seamless.

---

### Post by 23meg on 2007-09-13
Thanks, I'll look into it.

* thinks of possible ways to combine Tor with a VPN *

---

### Post by Boomy on 2007-09-13
Why use this vs. having a server at home and using a Linksys router with hardware VPN? Not criticizing it, just curious.

---

### Post by AriciU on 2007-09-13
Because they can still trace the IP back to his house probably.

---

### Post by PartisanEntity on 2007-09-13
Yes IP shifting was the interesting part for me.

---

### Post by mips on 2007-09-14
> **PartisanEntity said:**
> Yes IP shifting was the interesting part for me.

If that is all you are interested in then it is probably not worth your while to run a VPN as it is just as traceable as any other service. The downside is the actual VPN probably adds a tax to your link.

---

### Post by jsteidl on 2007-10-24
I think the main motivation is to move the exit-point of the first unecrypted traffic away fom your home-connection and maybe even in another country with a "better" legal situation for privacy. At least that would be my motivation.

As far as i understood it all outgoing traffic is going through the vpn-tunnel, encrypted and exits there anonymously at relakks. It brings you a certain amount of security, since running a vpn isn't illegal (yet!?) but the content you might be tunneling could be that or just private enough to protect it.

i haven't used vpn, but as far as i understand it the traffic is (or at least can be) encrypted. Correct me if i am wrong! :)

another thing i haven't understood yet: if i establish a connection via vpn to relakks or any other service of that kind is it possible only to use it with a certain program such as an Email-Application while using your home-connection for your "normal" business in the internet.
I ask this because if ALL traffic is going via that tunnel and i log into a website (lets say googlemail) i give away my identity - which is absoultely not my intention.

i am getting confused. ... help! ;):popcorn:

---

### Post by PartisanEntity on 2007-10-24
> **jsteidl said:**
> I think the main motivation is to move the exit-point of the first unecrypted traffic away fom your home-connection and maybe even in another country with a "better" legal situation for privacy. At least that would be my motivation.

As far as i understood it all outgoing traffic is going through the vpn-tunnel, encrypted and exits there anonymously at relakks. It brings you a certain amount of security, since running a vpn isn't illegal (yet!?) but the content you might be tunneling could be that or just private enough to protect it.

i haven't used vpn, but as far as i understand it the traffic is (or at least can be) encrypted. Correct me if i am wrong! :)

another thing i haven't understood yet: if i establish a connection via vpn to relakks or any other service of that kind is it possible only to use it with a certain program such as an Email-Application while using your home-connection for your "normal" business in the internet.
I ask this because if ALL traffic is going via that tunnel and i log into a website (lets say googlemail) i give away my identity - which is absoultely not my intention.

i am getting confused. ... help! ;):popcorn:

Yes this is the main reason I use Relakks, it's due to the tight privacy laws in Sweden.

And yes, all traffic between your computer and Relakks is encrypted.

As far as giving away your identity, I will check with Relakks whether all customers share the same IP number, in that case it would be like looking for a needle in a hay stack.

I am not sure if you can use Relakks with only certain applications.

I have been using this service for some time now and am quite happy with it, setting up the VPN connection was very easy.

---

### Post by PartisanEntity on 2007-10-27
I checked with Relakks, customers share a specific range of IP addresses.

---

