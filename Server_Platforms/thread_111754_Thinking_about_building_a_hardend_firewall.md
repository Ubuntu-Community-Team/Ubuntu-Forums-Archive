---
title: "Thinking about building a hardend firewall"
date: 2006-01-02
forum: Server Platforms
---

### Post by AndyW on 2006-01-02
Im thinking about building a hardend firewall with linux and I have a few questions:
Would Ubuntu be good for this? I will not have a monitor or keyboard or mouse connected, so I would need to have some kind of web interface or something.
Or would a specific distro like [Ipcop]("http://www.ipcop.org/") be better?

Would this eliminate the need of a software firewall on the Windows computers? (this would make alot of internal network things easier)

And one last thing, on one of my windows computers running Kerio Personal Firewall and I see this in the logs:
[IMG]http://img.photobucket.com/albums/v358/Awal/other/trojan.jpg[/IMG]
I see that its coming from an internal ip address, so does that mean the other computer has a trojan?

Thanks in advance.:KS

---

### Post by Sef on 2006-01-02
Yes, I would check that other computer for that trojan.  If you can't get to it right away, you should disconnect it from the net, so you don't infect other computers on your net or others on the internet.

---

### Post by alamba on 2006-01-02
Well you could always use ubuntu as a firewall and install webmin on it for using a GUI for iptables. I can't remember the name of the module but it's pretty easily available.

Akshay

---

### Post by LoclynGrey on 2006-01-02
Why don't you look at IP Cop.

[website]("http://www.ipcop.org/")

---

### Post by AndyW on 2006-01-03
I decided to install Ubuntu, because I decided that I dont have another computer to spare. Ill use it as a firewall and workstation.

Anyways I have two ethernet cards installed and I want to connect (bridge) the two.
eth1 is comming from the modem and eth0 is going to the router.
How do I do this?

---

### Post by AndyW on 2006-01-04
Ok, I bridged the connections on the two interfaces
and I can connect on the computers on myside of the firewall. But the firewall itself cant access the internet.
Anyone have any ideas ?

btw I used brctl commands after installing a package.

---

### Post by alinuxfan on 2006-01-05
I found that just by installing firestarter and using it to play with the iptables and set it up...
I used to use the IP masq how to from the linux documentation project...they should work the same...
The howto has a bunch of steps to test eash part of the setup
here is a link[http://www.tldp.org/HOWTO/IP-Masquerade-HOWTO/]("http://www.tldp.org/HOWTO/IP-Masquerade-HOWTO/")
I hope this helps

Edit:
 I remember I had the same problem the other day when i changed firestarter to "restrictive by default"
I had to add the internal IP address of this machine and it was able to find the net soon after
I have been IP masqing for a couple of years now and with a strong ruleset and making the windows machines use firefox or something other than IE, I have had a lot less virii on my other computers

---

### Post by AndyW on 2006-01-05
Yea, I messed around with Firestarter, but it kept giving me errors when I tried to set it up. First it was Eth0 is not ready. And the next time it was just and "unknown error". I think it was because the two ips have to be on a different subnet. Is that correct?

Ill mess around with it and see what I come up with.

---

### Post by AndyW on 2006-01-06
Woot! Got it to work. This is awesome. 
I just started messing with the ip's and it just worked.

---

