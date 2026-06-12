---
title: "Help! How To Use GUFW While At The Same Time Running Squid Proxy Server?"
date: 2010-09-16
forum: Security
---

### Post by AlexanderDGreat on 2010-09-16
Hi, I successfully built a Squid Proxy Server to control access to the Internet from our office computers / workstations.

If you want more info about this, I have a tutorial in YouTube: [http://www.youtube.com/watch?v=MMadVJNoD48]("http://www.youtube.com/watch?v=MMadVJNoD48") which I teach a Basic Usage of a Squid Proxy Server.

However, recently, I've been studying about FireWalls. I installed GUFW in my Lucid Lynx Server which is also the Squid Proxy Server, but all the connections in the office "workstation computers" were LOST. They can't connect to a Single Website.

My real question is, **How Do You Enable Squid Proxy Server While At The Same Time Using A Firewall In This Server?**

I've looked all over and have come here for help.

Can you please help me understand these things as I'm relatively new to Firewalls. Thank you for your time. :)

---

### Post by AlexanderDGreat on 2010-09-16
My setup is very simple. In the server are 2 NIC cards. **Eth0** connected to ISP. Workstation computers are connected to **eth1**

In my /etc/rc.local script I forward the workstation connection to my **eth0**, like this:

sh -c 'echo 1 > /proc/sys/net/ipv4/ip_forward'
iptables -t nat -A POSTROUTING -j MASQUERADE --source 192.168.1.0/24
iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 80 -j REDIRECT --to-port 3128

exit 0

Then workstations get Internet access. Thanks.

---

### Post by bodhi.zazen on 2010-09-17
> **AlexanderDGreat said:**
> My setup is very simple. In the server are 2 NIC cards. **Eth0** connected to ISP. Workstation computers are connected to **eth1**

In my /etc/rc.local script I forward the workstation connection to my **eth0**, like this:

sh -c 'echo 1 > /proc/sys/net/ipv4/ip_forward'
iptables -t nat -A POSTROUTING -j MASQUERADE --source 192.168.1.0/24
iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 80 -j REDIRECT --to-port 3128

exit 0

Then workstations get Internet access. Thanks.

OK, rather then posting a long winded note on iptables, nat, and squid I marked this thread as solved for you =)

---

### Post by AlexanderDGreat on 2010-09-19
Hi bodhi.zazen. My 2nd post is just from the startup scipt **BUT whenever I ENABLE the GUFW -- there's NO Internet Access for workstations!**

---

### Post by AlexanderDGreat on 2010-09-19
So to sum: I run Squid Proxy. But an additional settings required is written in my 2nd post. Now everything is working fine. BUT That is BEFORE I ENABLE the GUFW.

Whenever I enable GUFW, Internet Access Is LOST, I Allow ALL INCOMING & OUTGOING Connections.

Maybe I don't know how to WRITE RULES in GUFW. That's my problem. Thanks for reading.

---

### Post by dino99 on 2010-09-19
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

---

### Post by Alexis Phoenix on 2010-09-19
Did you work this out yet?  If not, I was just thinking, you should make sure you can access the squid server from the workstations - do you get the squid error page when trying to access the web?

Is the firewall rule in your rc.local interfering with gufw?  Maybe you should try disabling it before anything else.

I was just having a look at gufw - if you go to the advanced tab (edit > add rule > advanced) you can specify protocols, ip addresses and port numbers to allow in and out - it looks simple enough to understand.

FWIW, I used to use shorewall, which gives you much more control over what happens, and lets you specify interfaces. It is (or used to be anyway) easy enough to set up once you read the docs, though daunting at first (and this is me that still doesn't really understand iptables rules very well!) May be would be more appropriate to your circumstances.

Good luck anyway.

---

### Post by bodhi.zazen on 2010-09-19
> **Alexis Phoenix said:**
> Did you work this out yet?  If not, I was just thinking, you should make sure you can access the squid server from the workstations - do you get the squid error page when trying to access the web?

Is the firewall rule in your rc.local interfering with gufw?  Maybe you should try disabling it before anything else.

I was just having a look at gufw - if you go to the advanced tab (edit > add rule > advanced) you can specify protocols, ip addresses and port numbers to allow in and out - it looks simple enough to understand.

FWIW, I used to use shorewall, which gives you much more control over what happens, and lets you specify interfaces. It is (or used to be anyway) easy enough to set up once you read the docs, though daunting at first (and this is me that still doesn't really understand iptables rules very well!) May be would be more appropriate to your circumstances.

Good luck anyway.

IMHO, iptables is easier to use.

The "problem" with many front ends for iptables , in this case ufw, they often do not do NAT easily.

See :

[http://www.cyberciti.biz/tips/linux-setup-transparent-proxy-squid-howto.html](http://www.cyberciti.biz/tips/linux-setup-transparent-proxy-squid-howto.html)

If you want to use ufw you will need to manually edit  /etc/ufw/before.rules

I give an example of how to do this here :

[http://blog.bodhizazen.net/linux/how-to-transparent-proxy/](http://blog.bodhizazen.net/linux/how-to-transparent-proxy/)

Between those two links you should be able to adapt.

If you are having problems, you will need to give us more details. What are your rules and how have you configured ufw ?

---

### Post by AlexanderDGreat on 2010-09-19
@dino99 - thanks I'm reading them as of now.

> make sure you can access the squid server from the workstations - do you get the squid error page when trying to access the web? - Yes. Everything is OK with Squid.

> Is the firewall rule in your rc.local interfering with gufw? Maybe you should try disabling it before anything else. - I don't think so. Maybe GUFW still CAN'T SUPPORT NAT'ing?

@Alex Phoenix - thank you for your support.

> The "problem" with many front ends for iptables , in this case ufw, they often do not do NAT easily. - Exactly!

@bodhi - I will post what I've for a solution, you certainly helped! :)

---

### Post by AlexanderDGreat on 2010-09-19
Thanks everyone for helping out, I studied a little about iptables and building a transparent Squid proxy.

So after much consideration and tinkering in my cpu lab at home, here's my solution:

I have 2 NICs, eth0 and eth1, eth1 is used by the workstations, I first edit my /etc/rc.local:

```
sh -c 'echo 1 > /proc/sys/net/ipv4/ip_forward'
iptables -F FORWARD
iptables -F -t nat

iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 80 -j REDIRECT --to-port 3128

iptables -A FORWARD -i eth1 -p tcp --destination-port 5051:8000 -o eth0 -j DROP
iptables -A FORWARD -i eth1 -p udp --destination-port 5051:8000 -o eth0 -j DROP
iptables -A FORWARD -i eth1 -p tcp --destination-port 9000:65535 -o eth0 -j DROP
iptables -A FORWARD -i eth1 -p udp --destination-port 9000:65535 -o eth0 -j DROP

iptables -t nat -A POSTROUTING -j MASQUERADE --source 192.168.1.0/24

exit 0
```

The forwarding is important in my setup, I redirect it to Squid Port, then I block ALL UNUSED PORTS (for torrents --> successful from 200kb -> down to 10kb in torrent users without sacrificing Internet speed)

As you can see, I skipped port 8001 - 8999 because we have an Internet application that uses port 8080.

That's all. I'll mark this solved, but if anyone has any comment on improving my rc.local script. It's appreciated. Thanks. :)

---

### Post by bodhi.zazen on 2010-09-19
iptables is, IMO, an elegant solution.

In the time it takes to learn some of the configuration tools, one could learn iptables. Once you understand iptables you can apply that knowledge to any Linux distro or install (Desktop or server).

You might want to look at iptables-save , iptables-apply, iptables-restore, etc

It may simplify your rc.local (or you can call iptables-restore in /etc/network/interfaces as a post-up statement).

---

### Post by AlexanderDGreat on 2010-09-19
Thanks bodhi. Yup I'm still reading your articles about iptables! More power to your contributions. :)

---

### Post by bodhi.zazen on 2010-09-19
> **AlexanderDGreat said:**
> Thanks bodhi. Yup I'm still reading your articles about iptables! More power to your contributions. :)

If you have questions, post back. If you have suggestions for improvements, send me a PM =)

---

### Post by AlexanderDGreat on 2010-09-20
Sure thing! :)

---

