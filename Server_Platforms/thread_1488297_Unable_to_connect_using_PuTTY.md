---
title: "Unable to connect using PuTTY"
date: 2010-05-19
forum: Server Platforms
---

### Post by rm06 on 2010-05-19
I have an Ubuntu 9.10 server I use as a file server. I am able to allow Mac computers and other Linux users to access it but I am unable to connect from a Windows computer using PuTTY. Perhaps I am doing something wrong in PuTTY? I am inputting the host name on port 22 (default) and I receive a network timeout.

I just confirmed through a friend that he is able to access my server remotely and I am still unable to. Is there another step I am missing?

---

### Post by terazen on 2010-05-21
From the windows computer can you ping the linux server by hostname?

---

### Post by CharlesA on 2010-05-21
Try it using the IP address instead of the host name. Windows uses broadcasts for name resolution (probably NetBIOS), while Linux/Macs do not.

---

### Post by 1serveyou on 2010-05-21
> **CharlesA said:**
> Try it using the IP address instead of the host name. Windows uses broadcasts for name resolution (probably NetBIOS), while Linux/Macs do not.

I agree with Charles, sometimes I first have to put the ip, but then after a bit it will let me use the host name. I don't know the technical reason behind it, but i just know it works :)

---

### Post by rm06 on 2010-05-24
I cannot ping either by name or IP address. I get three "request timed out" with one reply from an address in my subnet followed by a "destination host unreachable" - I'm assuming this is the ISP's router.

When attempting to ping by name, it does list the correct IP address which I've confirmed on my DynDNS page though I am unable to reach it by using said IP address.

One friend is still able to access it using his Mac and another is using WinSCP, which I've also tried without success. I have two separate ways I've tried to connect from the outside, one from my office and another using my cell phone as a tethered modem from my laptop.

---

### Post by CharlesA on 2010-05-24
Do you have DenyHosts or Fail2Ban installed?

---

### Post by rm06 on 2010-05-24
> **CharlesA said:**
> Do you have DenyHosts or Fail2Ban installed?

Not that I'm aware of. . .

---

### Post by terazen on 2010-05-25
> **rm06 said:**
> I cannot ping either by name or IP address. I get three "request timed out" with one reply from an address in my subnet followed by a "destination host unreachable" - I'm assuming this is the ISP's router.

When attempting to ping by name, it does list the correct IP address which I've confirmed on my DynDNS page though I am unable to reach it by using said IP address.

One friend is still able to access it using his Mac and another is using WinSCP, which I've also tried without success. I have two separate ways I've tried to connect from the outside, one from my office and another using my cell phone as a tethered modem from my laptop.
When you say "from my office" are you in the same location as the server or connecting to a home server from work?  Is there any nat or port forwarding involved?

---

### Post by clrg on 2010-05-25
Is it possible your company's security responsible is prohibiting SSH traffic from leaving your corporate LAN?

---

### Post by CharlesA on 2010-05-25
> **clrg said:**
> Is it possible your company's security responsible is prohibiting SSH traffic from leaving your corporate LAN?

That sounds like the most plausible explanation.

---

### Post by rm06 on 2010-05-25
It turns out to be my avast! anti-virus or some component of it. I should have tried to disable it before I started the thread, I just assumed it was something I was doing wrong while trying to establish a SSH session.

I will contact avast! to see if there is some way I can poke a hole in it to allow SSH at least outgoing.

---

### Post by CharlesA on 2010-05-25
You should be able to add an exception.

---

