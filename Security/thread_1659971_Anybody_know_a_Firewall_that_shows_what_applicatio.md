---
title: "Anybody know a Firewall that shows what applications are accessing internet?"
date: 2011-01-04
forum: Security
---

### Post by nrundy on 2011-01-04
Is there a way in Ubuntu to see what applications are accessing the internet, that is outgoing requests?

---

### Post by cariboo on 2011-01-04
You can give:

```
netstat -l
```

a try, it will list all the programs listening for a connection.

---

### Post by bodhi.zazen on 2011-01-04
My  favorite is :

```
lsof -i -n -P
```

---

### Post by nrundy on 2011-01-04
Thanks guys. Could you give me a link or a little more info about what I can expect? Will these commands open a gui that shows the applications as they attempt connection? Does it display the application name in Terminal as it attempts connection but nothing more? How do I disable these programs once they are enabled? Thanks. I'm just kinda playing around and watching traffic to just learn how things work and stuff and understand the system's internet traffic.

---

### Post by nrundy on 2011-01-04
using Firestarter and blocking all outgoing traffic I noticed that something tried to connect out from a source address that is not my IP. Most services from this "not mine" IP addres show unknown, but one listing shows Shoutcast. Not sure what this is. But why would it show an IP that isn't mine as the source?

---

### Post by uRock on 2011-01-04
> **bodhi.zazen said:**
> My  favorite is :

```
lsof -i -n -P
```
I like that one. Thanx for sharing!

Cheers,
uRock

---

### Post by bodhi.zazen on 2011-01-04
> **nrundy said:**
> using Firestarter and blocking all outgoing traffic I noticed that something tried to connect out from a source address that is not my IP. Most services from this "not mine" IP addres show unknown, but one listing shows Shoutcast. Not sure what this is. But why would it show an IP that isn't mine as the source?

Yes it is big and scary world out there. Try installing a ssh server and watch your logs =)

This is why "firestarter" is useless in this regard, as is logging dropped packets.

If you look at the logs you will see a ton a traffic. This is normal and it was all dropped and there is really nothing more to know then that.

Take a look at the snort sticky, it is very detailed including screenshots.

You really are going about this the wrong way, I also suggest the security sticky.

You need to answer a number of questions, what services are you running ? By default there are none, so there is nothing to firewall, this is not windows.

If you are running services, did you port forward ? What did you do to secure them ?

There is more to security then a firewall and flashing lights on firestarter.

---

### Post by dodo3773 on 2011-01-05
> **bodhi.zazen said:**
> My  favorite is :

```
lsof -i -n -P
```

Thank you for this. Finally found out what that mystery ip address was  (clock-app).

---

### Post by arapaho on 2011-01-05
Shoutcast is internet radio. Nothing to worry about. Type in google and check.
There is no such firewall you ask about on Linux.

---

### Post by spynappels on 2011-01-05
Listen to Bodhi, he is wise.

You could also look at Wireshark if you want a GUI, takes a little fiddling but worth it as a learning experience.

---

### Post by bodhi.zazen on 2011-01-05
> **spynappels said:**
> Listen to Bodhi, he is wise.

You could also look at Wireshark if you want a GUI, takes a little fiddling but worth it as a learning experience.

As was pointed out by another user on another thread, etherape is also a nice start.

[[img]http://etherape.sourceforge.net/images/v0.9.3-thumb.png[/img]]("http://etherape.sourceforge.net/images/v0.9.3.png")

---

### Post by nrundy on 2011-01-05
The impetus for my post isn't so much security (I took Bodhi's word Ubuntu is secure without Windows "firewalling" a while ago). I will be away for several months for work training. During this time I will be on a mobile broadband setup that only gives me so much data-use a month for internet connection.

Being able to control what applications connect to the internet will allow me to insure that only certain things have internet access and thereby conserve as much internet data usage as I can for the month. For example, in Ubuntu, sometimes just starting an application like Rhythmbox can result in an internet connection initiated by Rhythmbox. I want to block all attempts like this so no data is used when I'm not specifically seeking an internet connection from that application.

Any ideas how I can accomplish this with Ubuntu? (That is, for a n00b that is not yet comfortable with command-line controls and really doesn't know too much about computers?) It's easily done using an application-based firewall with Windows. I'm worried I'll have to use windows while on training to be able to manage what applications have internet access.

---

### Post by cariboo on 2011-01-05
Using your example, rhythmbox, you can turn off the individual plugins that access the internet.  You can turn off network access on a per application basis.

---

### Post by bodhi.zazen on 2011-01-05
> **nrundy said:**
> The impetus for my post isn't so much security (I took Bodhi's word Ubuntu is secure without Windows "firewalling" a while ago). I will be away for several months for work training. During this time I will be on a mobile broadband setup that only gives me so much data-use a month for internet connection.

Being able to control what applications connect to the internet will allow me to insure that only certain things have internet access and thereby conserve as much internet data usage as I can for the month. For example, in Ubuntu, sometimes just starting an application like Rhythmbox can result in an internet connection initiated by Rhythmbox. I want to block all attempts like this so no data is used when I'm not specifically seeking an internet connection from that application.

Any ideas how I can accomplish this with Ubuntu? (That is, for a n00b that is not yet comfortable with command-line controls and really doesn't know too much about computers?) It's easily done using an application-based firewall with Windows. I'm worried I'll have to use windows while on training to be able to manage what applications have internet access.

See if any here help

[http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-linux.html](http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-linux.html)

Not sure if any monitor use by application though.

---

### Post by nrundy on 2011-01-06
> **cariboo907 said:**
> Using your example, rhythmbox, you can turn off the individual plugins that access the internet.  You can turn off network access on a per application basis.

 How exactly do I do this? Wouldn't this entail an enormous amount of work and am likely to miss something? I'm a noob but this just doesn't seem like a practical way to control bandwith usage globally. Maybe on a per application basis though.

---

### Post by nrundy on 2011-01-06
> **bodhi.zazen said:**
> My  favorite is :

```
lsof -i -n -P
```

 Bodhi, not sure I'm doing this one right. I typed in the command in Terminal but nothing happens. it just returns me to a new prompt??? any ideas what I"m doing wrong?

---

### Post by cariboo on 2011-01-06
In answer to your pm, What I di was open rhythmbox, then I opened a terminal and ran nmap on localhost, and it showed :

```
nmap 192.168.1.106

Starting Nmap 5.21 ( http://nmap.org ) at 2011-01-06 16:29 PST
Nmap scan report for 192.168.1.106
Host is up (0.032s latency).
Not shown: 998 closed ports
PORT     STATE SERVICE
111/tcp  open  rpcbind
3689/tcp open  rendezvous
```

Port 3689 was open, I just started turning of plugins and running nmap until it showed that the port was closed.

You can use iptables to block port 3689 from accessing the internet, but turning off the plugins in Edit->plugins was easier. :)

---

### Post by bodhi.zazen on 2011-01-06
> **nrundy said:**
> Bodhi, not sure I'm doing this one right. I typed in the command in Terminal but nothing happens. it just returns me to a new prompt??? any ideas what I"m doing wrong?

Run it as root

```
sudo lsof -i -n -P
```

---

### Post by nrundy on 2011-01-07
Thanks a lot guys. Cariboo and Bodhi, really appreciate it :)

---

### Post by nrundy on 2011-01-07
bodhi, is there a way to keep the lsof working continuously until I close the Terminal window? For example, si it would automatically update as connections are made and display them?

---

### Post by bodhi.zazen on 2011-01-07
> **nrundy said:**
> bodhi, is there a way to keep the lsof working continuously until I close the Terminal window? For example, si it would automatically update as connections are made and display them?

If you want ongoing monitoring try etherape or wireshark.

---

### Post by uRock on 2011-01-07
Bodhi.zazen,

Is there a way to run EtherApe without running it as root?

While looking for an answer to that, I stumbled upon this page, [http://www.debianadmin.com/network-traffic-analyzer-for-your-ubuntu-system.html](http://www.debianadmin.com/network-traffic-analyzer-for-your-ubuntu-system.html), which mentions an application called DarkStat. Darkstat is in the repos, so I am giving that one a try as well.

---

### Post by bodhi.zazen on 2011-01-07
> **uRock said:**
> Bodhi.zazen,

Is there a way to run EtherApe without running it as root?

While looking for an answer to that, I stumbled upon this page, [http://www.debianadmin.com/network-traffic-analyzer-for-your-ubuntu-system.html](http://www.debianadmin.com/network-traffic-analyzer-for-your-ubuntu-system.html), which mentions an application called DarkStat. Darkstat is in the repos, so I am giving that one a try as well.

My guess is most of these tools will want to run as root.

You can try the same fix as is used for wireshark.

---

### Post by Jive Turkey on 2011-01-25
If your goal is to reduce your bandwidth usage I would suggest using a custom hosts file (works with windows and mac also) as described on these sites:

[http://someonewhocares.org/hosts/zero/](http://someonewhocares.org/hosts/zero/)

or 

[http://www.mvps.org/winhelp2002/hosts.htm](http://www.mvps.org/winhelp2002/hosts.htm)

That prevents the downloading of adverts and miscellaneous garbage you don't need.  You could also get some of the same benefit from using the adblock plus plugin for firefox/chrome.

If you are really serious you could disable the automatic downloading of images on webpages all together, or increase your cache size for your browser(s) and adjust settings to make the browsers keep/use the cached content longer.

---

### Post by matt_symes on 2011-01-25
Hi

I don't know if this is relevant for you but if you need to tool to see what applications are using bandwidth at a given moment then install nethogs.

```
sudo apt-get install nethogs
```

I use this along with other tools and if my bandwidth, at a given moment, starts to spike i can check what is using it and kill it if required.

I just thought i would throw this into the mix.

Kind regards

---

### Post by crashed111 on 2011-01-26
No one has mentioned "netstat -a". Shows active connections. I use it almost every day for some reason or another

---

### Post by uRock on 2011-01-26
> **crashed111 said:**
> No one has mentioned "netstat -a". Shows active connections. I use it almost every day for some reason or another
That also shows internal communications. Can be confusing to some.

---

### Post by nrundy on 2011-01-26
yeah, i had no idea what i was looking at when i ran netstat -a. 

im too newbie to make sense of it.

---

### Post by bodhi.zazen on 2011-01-26
> **nrundy said:**
> yeah, i had no idea what i was looking at when i ran netstat -a. 

im too newbie to make sense of it.

lsof is better for new users, IMHO.

---

### Post by nrundy on 2011-01-27
> **bodhi.zazen said:**
> lsof is better for new users, IMHO.

I have a question about lsof. When I run it i see 3 kinds of listings. some say LISTENING (cups printer on loopback for example), ESTABLISHED (if I open firefox for example), and then some entries display neither (like avahi-dae, dhclient and ntpd)

Are dhclient and ntpd connected to the internet? What is it saying when they list but it doesn't say ESTABLISHED or LISTENING?

---

### Post by Kir_B on 2011-03-07
Bump!

I'm also quite curious about this subject, as I've currently got a fairly fresh install of ubuntu lucid and there's something unknown using up bandwidth. It's not using much, but it's been bugging me for quite some time.

I've tried everything suggested (Thanks bohdi & cariboo), but have yet to narrow it down.

Thanks again guys.
Kirby ](*,)

---

### Post by bodhi.zazen on 2011-03-08
> **Kir_B said:**
> Bump!

I'm also quite curious about this subject, as I've currently got a fairly fresh install of ubuntu lucid and there's something unknown using up bandwidth. It's not using much, but it's been bugging me for quite some time.

I've tried everything suggested (Thanks bohdi & cariboo), but have yet to narrow it down.

Thanks again guys.
Kirby ](*,)

If the above commands do not answer your question try things such as tcpdump , wireshark, or ntop.

tcpdump is preferred, but is command line only. Wireshark gives a graphical interface.

---

### Post by EJeanmaire on 2011-03-09
Little Snitch does exactly what you guys are looking for, the only problem is that it is Mac OS X only.

---

