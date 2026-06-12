---
title: "Can virus from Windows 10 laptop on same network affect my Ubuntu desktop?"
date: 2018-06-14
forum: Security
---

### Post by samuelz8 on 2018-06-14
(Sorry if this thread is not in the correct location)
Hi,
Another person in my house has a virus-ridden Windows 10 laptop, which I don't think has been updated in well over a year. It has so many viruses that you would probably have to do a reset to get rid of all of them (which they will not let me do). They are connected to the same Wi-Fi network as my Ubuntu desktop is. Is it possible for one of these viruses to somehow infect my Ubuntu desktop? I've read online about how listening ports on the computer can allow it to send a virus, but I don't know if that's true or not. The two computers do no file sharing of any kind.

Thank you. :)

---

### Post by lisati on 2018-06-14
The absence of file sharing is a good start. 

In general, malware (viruses and other nasty stuff) designed specifically for a Windows machine is unlikely to harm your Ubuntu machine.

If it's *your* WiFi setup (i.e. you have some level of admin control over it) one option might be to limit (or refuse) access to WiFi by the infected machine until the person responsible for it takes action that helps your peace of mind.

---

### Post by TheFu on 2018-06-23
> **samuelz8 said:**
> (Sorry if this thread is not in the correct location)
Hi,
Another person in my house has a virus-ridden Windows 10 laptop, which I don't think has been updated in well over a year. It has so many viruses that you would probably have to do a reset to get rid of all of them (which they will not let me do). They are connected to the same Wi-Fi network as my Ubuntu desktop is. Is it possible for one of these viruses to somehow infect my Ubuntu desktop? I've read online about how listening ports on the computer can allow it to send a virus, but I don't know if that's true or not. The two computers do no file sharing of any kind.

Thank you. :)

I treat all wifi machines like they are on the public, untrusted, internet.  wifi has proven to have issues and shouldn't be trusted, at least not alone as the only security for networking.  Use wired whenever possible and having different subnets for different risk levels of machines and devices is smart.  Along with having strong firewall rules to prevent nasty things.

I have 2 Win7 machines that haven't been patched since Microsoft tried to change the EULA to allow spying. I rejected every attempt they made and determined that not patching was the best choice for me.  OTOH, these win7 machines are not daily drivers and perform extremely low-risk tasks when accessing the internet (stock data and TV schedules) through specific programs, never email, never a browser. 

I will not have win10 on my network.  If a guest brings it, it doesn't matter because they connect to a wifi AP that is outside my network with zero access internally, except to services I provide to everyone in the world already.

My wifi-only devices have to use a full VPN to gain access to the specific internal network services I allow for that set of VPN credentials.  OTOH, it is nice to have the same access to Plex from my tablet without using any Plex clients or even having a Plex login from anywhere in the world. That's just one example. 
Nextcloud is another. Access is only available to  either trusted LAN systems (wired) or with a VPN connection for everyone else.
Calibre is another, scheduling of TV DVRs is another, and of course, I have remote access to almost all systems over ssh, using key-based authentication.  I'm looking into switching to ssh-certs, however.

At a minimum, I'd firewall off the Win10 machine so it has ZERO access to any other LAN resources.  Even allowing it to scan the network can lead to outside attacks.

But many people think I'm overly paranoid.  If you'd like more ideas on how to accomplish this, posting the exact HW router you have and the version of the router firmware would be the first place to start. But I don't trust most small-biz or consumer-level routers to correctly separate traffic.

---

### Post by #&amp;thj^% on 2018-06-23
> **TheFu said:**
> 
But many people think I'm overly paranoid.
No one wise enough here would. ;) just plain old good sense and network safety.

---

### Post by kurt18947 on 2018-06-23
I have nowhere near the networking and security expertise of many here but a guest WiFi network for unknown or known risky clients seems like a simple start. Guest wifi connections aren't supposed to have access to anything but the public internet. How well this is implemented is I guess the question.

---

