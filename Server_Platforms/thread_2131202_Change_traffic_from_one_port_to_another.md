---
title: "Change traffic from one port to another"
date: 2013-04-01
forum: Server Platforms
---

### Post by vikkyhacks on 2013-04-01
Can i change traffic from my proxy server port 6000 and redirect all the traffic it to a HTTP server which receives connection on port 80.

Does any proxy server allow me to do this, i don wish to use iptable or anything like that. Help me !!!

---

### Post by darkod on 2013-04-01
If you are using squid as a proxy you will have to look into its documentation, I don't know it in detail. Or if you are using another program, check its documentation.

But why not using iptables? This would be very easy to do with iptables. Even if you manage to do it with another tool it will probably use iptables as a base too.

---

### Post by vikkyhacks on 2013-04-02
frankly speaking the main reason i don wish to use iptables it because I DON UNDERSTAND it, they ask me to type a long command and If i go wrong I don even know how to properly reverse it back, I lately found out that iptables is used heavily in the networking side and it is not command that we type IT IS SOME FREAKY ALGORITHM. I also checked out some iptables's GUI but still I don get it. I only want to route, accept or reject certain traffic. That is what I am precisely looking for. If there is something which will make my task easier please send it over ... :)

---

### Post by darkod on 2013-04-02
When googling iptables you have to note this: iptables is very old and it has been used for ages. There are very old tutorials from when things had to be done with complicated scripts, so it really looks frightening to a beginner. I know because i was in the same situation few months ago when configuring a firewall machine.
I decided to use ufw as front end of iptables, and later i found out how much easier and simpler would have been to use iptables directly.

These days, you simply create one file with your iptables rules, and you load it at boot with iptables-restore. That's it.

What is it that you actually want to do? Froward traffic entering at port 6000 on one machine to port 80 of another machine?

---

### Post by spynappels on 2013-04-02
+1 to using IPTables directly, using Darko's suggestion of a single file with all rules makes administration much easier. For a good guide, check out BodhiZazen's Sticky post in the Security subforum.

---

### Post by vikkyhacks on 2013-04-03
K I give ip, I think I will have to learn iptables, this is my requirement

I am trying to turn a linux box (Ubuntu 12.04 64 bit) into a router, So:
1. How to block certain websites/domain. (I don care if anyone uses a proxy to bypass it)

2. Change all the traffic from one port to another, like changing the traffic from htppS to just http because I there is some error in the main room which distributes the connection to individual department and I am getting request from my dept. to change the traffic to just ordinary connection (frequently popping up a warning saying "your connection is blab blab blab")

3.  Route traffic from one machine to another specific machine. 
     If the packet is from google forward it to 10.0.1.1
     If the packet is from yahoo forward it to 10.0.1.2
     and also if the packet is from 10.0.1.5 then send it to 10.0.1.9 

IS THERE ANY TEST BED FOR TRYING THIS ??? I DON WANNA END UP WITH A MESS AT MY VERY NEW OFFICE
PLEASE BE EASY ON ME, I AM A PROGRAMMER AND I KNOW ONLY THE VERY BASICS OF NETWORKING, 
[SIZE=3][B]HELP ME WITH SOMETHING I WILL UNDERSTAND
[/B][/SIZE]

---

### Post by darkod on 2013-04-03
Making it into a router is easy and also redirecting all traffic from port X to port Y is easy, but for some of the other demands it might be more complicated. Like packets from google and yahoo. Did you put that only as example or you really need that? I'm not sure iptables can use domains/hosts instead of IPs, but it should be able to.

I usually start "small" with only the basic rules and then grow them.

First thing to do for routing is to enable the ip.forward in /etc/sysctl.conf. There should be a line line #net.ipv4.ip.forward=1. Simply remove the # at front to enable the line, save and close the file.

Then create a new empty file /etc/iptables.rules with this content:
```
*nat
:PREROUTING ACCEPT [0:0]
:POSTROUTING ACCEPT [0:0]

-A POSTROUTING -o <ext interface> -s 10.0.1.0/24 -j MASQUERADE

COMMIT

*filter
:INPUT DROP [0:0]
:FORWARD DROP [0:0]
:OUTPUT ACCEPT [0:0]

-A INPUT -i <int interface> -p tcp -s 10.0.1.0/24 --dport 22 -j ACCEPT
-A FORWARD -i <int interface> -s 10.0.1.0/24 -j ACCEPT (I'm not sure about this command to allow forwarding for local machines, someone might have a better idea)

COMMIT
```

That should be it.

The *nat sections is about routing, the POSTROUTING command says: everything going out on the <ext interface> from a source in the 10.0.1.0/24 subnet, masquarade it with the public IP. The <ext interface> should be your interface connected to the internet, for example eth0. I assumed you are using the 10.0.1.x subnet which means 10.0.1.0/24.

The *filter section is about the filtering of traffic. First you have to have port 22 accepted for SSH (or another port if you changed it) so that the machine will let you connect with a SSH session. On remote machines you have to be careful with iptables and the ssh port because you can lock yourself out.

The second command, about the FORWARD filter should accept all traffic coming from your local subnet 10.0.1.0/24 on the internal interface.

Now, if you run on the server:
sudo iptables-restore < /etc/iptables.rules

it will load the rules. If you load them like this, after you reboot they are gone. Try it like this first, you can easily make them permanent when you see your rules are working as expected. If they are not working as expected, there is no point loading them on boot right now.

That should allow you to use the ubuntu machine as router/gateway for other machines. Test it and let us know.

You can also load iptables rules one by one and that way you can see what works as expected before you put it into /etc/iptables.rules. The syntax is like:
```
sudo iptables -A INPUT .....
sudo iptables -t nat -A PREROUTING .....
```

---

### Post by vikkyhacks on 2013-04-04
Thank you very much for your explanation, I seem to understand it a bit now ... Your explanation was very helpful ... :)

---

