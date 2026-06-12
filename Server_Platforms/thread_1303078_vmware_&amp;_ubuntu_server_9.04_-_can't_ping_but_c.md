---
title: "vmware &amp; ubuntu server 9.04 - can't ping but can resolve"
date: 2009-10-27
forum: Server Platforms
---

### Post by fastiopt on 2009-10-27
Hi there!

I'm trying to set up an ubuntu server in my vmware, but I'm stuck at this point:

It cannot ping anything outside my LAN, like google.com, but it can resolve the name to ip.

I can sucessfully ping other computers I have in the LAN, including the firewall; and the others computers and firewall can ping the server. The others computers and also the firewall can ping outside the network (like google.com).

By firewall, I use a Clarkconnect box (cc box), which is the DHCP and DNS server in the network.

I've checked the resolve.conf and the dns server is correct (it points to the cc box).
Getting the ip by DHCP or by manually editing it (/etc/network/interfaces), the problem still mantains.

Any help to resolve this?

Thanks in advance!

---

### Post by windependence on 2009-10-27
Try doing a traceroute to some site ouside the LAN. Let's see where the packets are being stopped.

-Tim

---

### Post by fastiopt on 2009-10-27
I don't have the traceroute tool, only traceroute6, for the ipv6...

But I've use the tracepath tool:

```

mlobo@ubuntu-server:~$ tracepath google.com
1: ubuntu-server.lobos.lan (192.168.1.182)                 0.142ms pmtu 1500
1: yx-in-f100.1e100.net (74.125.45.100)                     0.191ms reached
1: yx-in-f100.1e100.net (74.125.45.100)                     0.189ms reached
  Resume: pmtu 1500 hops 1 back 128

```According to this, I can assume that the destination is reached, right? If so, why cannot I ping it? I think it's something in the virtual machine (AKA server), because in the host machine (my laptop) I can ping google.com...

---

### Post by windependence on 2009-10-27
I think it's probably because your firewall is not allowing the pings back in your network. That's not a bad thing necessarily.

For traceroute I forgot for some dumb reason it doesn't come in the distro. You can install it:

```
sudo apt-get update
    sudo apt-get install traceroute
```


-Tim

---

### Post by fastiopt on 2009-10-27
> **windependence said:**
> I think it's probably because your firewall is not allowing the pings back in your network.

Sorry, but I don't agree with you about this :) If that is happening, why can I ping trough the other machines? I've had other ubuntu virtual machines and this problem never happen. The lan config didn't change since then.

About the apt-get update... I cannot do it. It gives me a '111 Connection Refused' error. Maybe because it doesn't reach the net?...

Thanks for your quick replies Tim ;)

---

### Post by windependence on 2009-10-28
Turn off the firewall on your Ubuntu box. That's the problem, I'm sure.

-Tim

---

### Post by fastiopt on 2009-10-28
> **windependence said:**
> Turn off the firewall on your Ubuntu box. That's the problem, I'm sure.

-Tim

ufw is disabled by default.
I've tried pinging with ufw enabled, but with no sucess.

Today I've tried in my faculty network... same problem. I've checked the resolve.conf, and it was changed correctly, to the network dns server.

---

### Post by HaOsLsE on 2009-10-28
Hey...my first post. You stated it works fine internally.  So of course, your dns is going to resolve right (since your dns server stores and resolves these by itself).

Are you using IPv6 on your network ? If not, then configure all your IPv4 stuff then try.  From all you stated..it is a setting on your device...or perhaps a setting on your vmware server, but I doubt it's the server if you are running other vmware things off of it.

1. You can ping anything on your "internal" network
2. Everything can ping your vmware ubuntu server internally
3. Unable to get "OUTSIDE" of your "Internal" network

So you're not really getting too far...sounds like your IP is right...since you're resolving, and able to ping other internal devices. I'd double check your Subnet mask and your gateway on your new ubuntu server...that's all it could be since it resides on the same network as your other devices getting out.

Good Luck,
Bill

---

### Post by fastiopt on 2009-10-28
Bill thanks for your reply!

I decided to run an ubuntu desktop 9.04 live cd on vmware, to make the 'final test', and noticed that the problem also occurs!

So my only guess, and everything points to that, is some problem on vmware. But what is strange is that both virtual machines can obtain the ip by dhcp, which is outside the vmware stuff...

Well, now I'm going to see what could be wrong in vmware.

---

### Post by fastiopt on 2009-10-28
Found the problem!!

It was the my personal firewall that was blocking the traffic :p dumb one, I know...

---

### Post by windependence on 2009-10-28
Had a feeling that was the problem. Glad you got it fixed!

-Tim

---

### Post by HaOsLsE on 2009-10-29
Glad to hear ya got it.  It sounded like something simple like that.  You were just looking too far out.  Had to zoom in. :)

---

