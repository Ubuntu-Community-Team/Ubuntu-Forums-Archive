---
title: "Anyone get hits on Firestarter from 207.68.176.16"
date: 2005-12-29
forum: Server Platforms
---

### Post by alinuxfan on 2005-12-29
I am IP masq'ing my wife's computer thru mine (which became a whole lot easier once i found firestarter)
Anyway,
 I am getting hits on ports in the 2000s a bunch of different ports so I when to [http://www.dnsstuff.com]("http://www.dnsstuff.com")
and it says that the IP is from microsoft at Redmond, WA
Maybe it's just trying to autoupdate or something, but that is just freaking with me
Firestarter is awesome
Adam

---

### Post by Taino on 2005-12-29
There's alot of scanning that happens on the web from microsoft, from other auto-updating programs, and from the government, etc..

Just keep your firewall on and remember Windows comes with a ton of opened ports by default, so your safer just by using Ubuntu, the firewall for Ubuntu is almost unnecessary since Ubuntu installs with all ports closed, the firewall (in Ubuntu's case) is mostly just telling you what attempts are taking place, also if you enable ICMP filtering (in Firestarter) you will basically be invisible, even to being pinged.

I get alot of scan attempts too in the same range you mentioned, its mostly general internet activity, the difference is Linux systems tell you about it, WIndows systems dont and give you a false sense of security.

No worries here.. :)

---

### Post by alinuxfan on 2005-12-29
thanks, i apprecaite it...makes me feel safe(r) to have any and all windows systems routed thru a linux box with only certain ports open as needed
if I could just get pogo.com to work in linux, i might be able to get my wife to ditch windows HAHA

---

### Post by lcg on 2005-12-29
[QUOTE=Taino]also if you enable ICMP filtering (in Firestarter) you will basically be invisible, even to being pinged.[/QUOTE]
Sorry to disappoint you, but there is no such thing as being invisible on an IP network.

Usually, being "invisible" refers to configuring a packet filter to just drop unwanted incoming packets. It doesn't work like that, though. It's just a (marketing) myth, probably by some vendors of personal firewalls.

3 scenarios:
1.) You drop unwanted incoming traffic. The sender thinks the packet is lost and sends again, probably several times until finally giving up, stealing your bandwidth. However, the sender knows there is a computer with the target IP address (because of scenario 3), no matter how quiet or "invisible" you pretend to be.
2.) Your computer responds with an "ICMP destination unreachable, port unreachable" (type 3, code 3) if a port is filtered or with a RES packet. In that case, the sender won't resend packages as there is no need to do so: the packet in fact reached the destination but then got rejected. No bandwidth loss due to resending. However, an attacker might still probe your box again, but he also might do that in scenario 1 while being "invisible".
3.) There really isn't a computer with your destination IP. In that case, the router before your box would reply to the sender "ICMP destination unreachable, host unreachable" (type 3, code 1). Only then does the recipient IP really not exist. And there is no way to make the router before your box send that, so no way of being invisible.

HTH,
Lars

---

### Post by Taino on 2005-12-29
[QUOTE=lcg]Sorry to disappoint you, but there is no such thing as being invisible on an IP network.[/QUOTE]

Seems you might need to study up on network security a few more years, if you dont know how to appear invisible on a network to other users that doesnt mean it cant be done, im doing it right now. :-\"

---

### Post by lcg on 2005-12-30
> **Taino]Seems you might need to study up on network security a few more years,[/QUOTE]
Actually, I know quite a lot about that topic. If you read my post again, you might even find the part where I tried to explain the reasons to you.  said:**
> if you dont know how to appear invisible on a network to other users that doesnt mean it cant be done, im doing it right now. :-\"
If that belief helps you sleep at night ... 
Just be aware that not replying to ICMP echo requests has nothing to do with being "invisible". There might be reasons not to do that, but "invisibility" isn't one of them, I can assure you.

But if you really think you know some magic that I am unaware of, why don't you just tell us what your packet filter is doing? Then we can discuss these rules and their effectiveness.

Lars

---

### Post by alinuxfan on 2005-12-31
so basically it comes down to I am going to get hits, and I most definately did when i ran windows, i just didn't know it.
So long as I keep track of what ports i have open, and monitor my traffic, i should be good...correct?
Now I am getting hits in the 43000 and 44ooo.....

---

### Post by majikstreet on 2005-12-31
i haven't read the whole thread...

LOL billy is trying to hack you..

---

### Post by alinuxfan on 2005-12-31
well damn him...tell him to stop for me would ya?

---

### Post by jdong on 2005-12-31
Think of it this way: If it shows up with Firestarter, it means that whatever it was, you've successfully repelled the attack (if it even was one) and can move on with your life.

If you're a security paranoid type, what should keep you awake in bed night after night is all of those packets that are secretly getting in, and how to detect those ;) j/k

---

### Post by jdong on 2005-12-31
[QUOTE=lcg]Sorry to disappoint you, but there is no such thing as being invisible on an IP network.

Usually, being "invisible" refers to configuring a packet filter to just drop unwanted incoming packets. It doesn't work like that, though. It's just a (marketing) myth, probably by some vendors of personal firewalls.

3 scenarios:
1.) You drop unwanted incoming traffic. The sender thinks the packet is lost and sends again, probably several times until finally giving up, stealing your bandwidth. However, the sender knows there is a computer with the target IP address (because of scenario 3), no matter how quiet or "invisible" you pretend to be.
2.) Your computer responds with an "ICMP destination unreachable, port unreachable" (type 3, code 3) if a port is filtered or with a RES packet. In that case, the sender won't resend packages as there is no need to do so: the packet in fact reached the destination but then got rejected. No bandwidth loss due to resending. However, an attacker might still probe your box again, but he also might do that in scenario 1 while being "invisible".
3.) There really isn't a computer with your destination IP. In that case, the router before your box would reply to the sender "ICMP destination unreachable, host unreachable" (type 3, code 1). Only then does the recipient IP really not exist. And there is no way to make the router before your box send that, so no way of being invisible.

HTH,
Lars[/QUOTE]

One more scenario:

On a switching network, it's almost completely impossible to be fully stealth unless you disconnect from the network, because of ARP requests. Consider me entering the network 192.168.0.x/255.255.255.0. I have an IP of 192.168.0.10.

First off: I can assome that (depending on how the DHCP server works) that 1-9 or 11-254 are good targets to attack since the DHCP server is implying to me that they've been recently used.

Secondly, I can use ettercap and similar tools to poison the switch into redirecting traffic to me. You send a packet, I'll see you, and even have the chance to meddle with your incoming/outgoing data through a MITM attack.

Finally, there's the problem of ARP requests. Most of the times, I locate people on a network by using ARP packets. I find that for whatever reason, I can always get ARP responses back from "perfectly stealth" users. This is one method commonly used to circumvent the wifi portal setups that hotels and airports use to force you to pay for wifi.

---

### Post by alinuxfan on 2006-01-01
no, i am not the paranoid type, just curious why Redmond, WA was trying to get in my computer
and I need to learn this ARP thing....gonna go research...off i go

---

### Post by Omnios on 2006-01-01
Personal perspective, With firestater I got on average about 100 hits a day which seems pretty normal then I got a router with a firewall thingy and that whent down to 1 or 2 every other day.

---

