---
title: "Static IP Help"
date: 2011-11-19
forum: Server Platforms
---

### Post by jlacroix on 2011-11-19
I'm setting up Ubuntu Server 11.10 on a spare computer, and I cannot get it to set a static IP. I've followed the [guide]("https://help.ubuntu.com/11.10/serverguide/C/network-configuration.html"), following the directions to edit /etc/network/interfaces but every single time I boot, I get a DHCP address, not the address I put in interfaces. I tried to remove "dhcp-client" thinking that would cause it, but it tells me that virtual packages cannot be removed. I spent two hours on Google to find a way to set a static IP in Ubuntu Server 11.10, but they ALL tell me to do it the way I already did it.

Am I missing something?

---

### Post by papibe on 2011-11-19
Hi jlacroix.

Try checking for an IP conflicts in your network. That is, two machines that have the same LAN IP address. Remember that even if you do the static LAN IP configuration within your server, you have to 'coordinate' that address with the rest of the LAN and router. For example, you have to use the router static IP range for your server.

Just a thought,
Regards.

BTW, I myself find much easier to leave the configuration of the server as it is, and set an DHCP reservation on the router (when supported of course).

---

### Post by jlacroix on 2011-11-19
> **papibe said:**
> Hi jlacroix.

Try checking for an IP conflicts in your network. That is, two machines that have the same LAN IP address. Remember that even if you do the static LAN IP configuration within your server, you have to 'coordinate' that address with the rest of the LAN and router. For example, you have to use the router static IP range for your server.

Just a thought,
Regards.

BTW, I myself find much easier to leave the configuration of the server as it is, and set an DHCP reservation on the router (when supported of course).
Thanks, but the address isn't in conflict with another address. The problem is that it gets a DHCP address, even though I set a static address in interfaces. It's completely ignoring /etc/network/interfaces altogether. I checked for network-manager, but that isn't installed. My guess is that there is a package that is superceding interfaces, but I don't know which one.

---

### Post by lisati on 2011-11-19
My preference is to allow my router (or other similar device) to hand out IP addresses, setting the IP for specific machines as static in the router as required. Although it appears not to be an issue here, it can help avoid address conflicts, and can help avoid breaking something in /etc/network/interfaces

---

### Post by papibe on 2011-11-19
Could you post your /etc/network/interfaces ?

Regards.

---

### Post by jlacroix on 2011-11-19
> **lisati said:**
> My preference is to allow my router (or other similar device) to hand out IP addresses, setting the IP for specific machines as static in the router as required. Although it appears not to be an issue here, it can help avoid address conflicts, and can help avoid breaking something in /etc/network/interfaces
While I understand your point, I'm setting a static IP because that is my preference.

> **papibe said:**
> Could you post your /etc/network/interfaces ?

Regards.
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
address 172.16.254.5
netmask 255.255.255.0
network 172.16.254.0
broadcast 172.16.254.255
gateway 172.16.254.1

```

OH. MY. GOD. The problem was staring me right in the face. Not a single set of instructions I Googled mentioned to change "dhcp" to "static". I never even noticed that was there until I posted it here.

---

### Post by lisati on 2011-11-19
> **jlacroix said:**
> While I understand your point, I'm setting a static IP because that is my preference.


And my point is that it's sometimes easier and safer to do so using your router rather than in your computer.

---

### Post by jlacroix on 2011-11-19
> **lisati said:**
> And my point is that it's sometimes easier and safer to do so using your router rather than in your computer.
But with all due respect, if I wanted to do it that way, I would've done it that way. ;)

---

### Post by jlacroix on 2011-11-19
Thanks for your help everyone. :)

See my edit in a post above. I can't believe I missed that!!!

Sorry to waste everyone's time, but I appreciate everything anyway.

---

### Post by lisati on 2011-11-19
> **jlacroix said:**
> But with all due respect, if I wanted to do it that way, I would've done it that way. ;)

I don't have a problem with you wanting to learn about different ways of doing things.

Now that you've found the answer to your question, you are free to mark this thread as "solved"

---

### Post by jlacroix on 2011-11-19
> **lisati said:**
> I don't have a problem with you wanting to learn about different ways of doing things.

Now that you've found the answer to your question, you are free to mark this thread as "solved"
Thanks again. I am curious why you feel that a reservation is safer than a static IP? This particular server will hold nothing important (literally not even a single file) but you got me curious.

---

### Post by lisati on 2011-11-19
> **jlacroix said:**
> Thanks again. I am curious why you feel that a reservation is safer than a static IP? This particular server will hold nothing important (literally not even a single file) but you got me curious.

My preference for using a reservation in a router is geared more to a portable device like a laptop or netbook where there might be a need to connect to different networks from time to time and where the need to avoid addressing conflicts is present. It doesn't matter so much for a server that is unlikely to be moved.

---

### Post by papibe on 2011-11-19
> **jlacroix said:**
> Sorry to waste everyone's time, but I appreciate everything anyway.
Don't worry. I'm glad you solve it :D

Kind Regards.

---

### Post by jlacroix on 2011-11-19
> **lisati said:**
> My preference for using a reservation in a router is geared more to a portable device like a laptop or netbook where there might be a need to connect to different networks from time to time and where the need to avoid addressing conflicts is present. It doesn't matter so much for a server that is unlikely to be moved.
Thank you. I keep a spreadsheet of all my IP's and use it religiously so that shouldn't be a problem. But I am curious if doing it through reservations in the router would make the computer pingable by hostname?

---

### Post by papibe on 2011-11-19
Yes, that's one the advantages.

However, note that not all routers work as a DNS. Some of them just set the same ISP DNS for the local machines. In that case, accessing by name won't work. 

Regards.

BTW, between Linux machines you can use the zero configuration domain, and access any machine using an address like this:
```
myserver.local
```

---

