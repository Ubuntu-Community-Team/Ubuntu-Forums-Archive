---
title: "Would appreciate some input on firewalls/security in ubuntu"
date: 2008-05-03
forum: Security
---

### Post by Open-SuSe-A-Me on 2008-05-03
Sorry if this has been addressed before. I am currently dual-booting ubuntu and win xp and would like to phase out windows.  i've recently switched to ubuntu from opensuse 10.3 and am very pleased with ubuntu. my main concern is that my ubuntu setup is not as secure as my windows (ironically). in opensuse i used guarddog firewall which worked very well but firestarter seems flawed/infunctional at times and is generally annoying to work with. i am currently using "gnome-lokkit" which says all ports are closed though no programs i use have trouble connecting to the internet. if i can match the functionality of the zone alarm/peerguardian(for p2p use) combo i have on winxp then windows can go in the garbage. 

i am pretty familiar with how to use linux at this point, but i am not so good on the terminal with most of the fancy commands.

any input on this would be greatly appreciated - thanks.

---

### Post by brian_p on 2008-05-03
> **Open-SuSe-A-Me said:**
> Sorry if this has been addressed before. I am currently dual-booting ubuntu and win xp and would like to phase out windows.  i've recently switched to ubuntu from opensuse 10.3 and am very pleased with ubuntu. my main concern is that my ubuntu setup is not as secure as my windows (ironically).

What do you base your concern on?

>  in opensuse i used guarddog firewall which worked very well but firestarter seems flawed/infunctional at times and is generally annoying to work with.

In what way did guarddog work well for you?

>  i am currently using "gnome-lokkit" which says all ports are closed though no programs i use have trouble connecting to the internet.

You're offering no services externally so a firewall is superfluous. And having no trouble connecting to the internet is good, is it not?

>  if i can match the functionality of the zone alarm/peerguardian for p2p use) combo i have on winxp then windows can go in the garbage. 

Put it in the garbage anyway. Your single machine will gain nothing from having a firewall.

---

### Post by Open-SuSe-A-Me on 2008-05-03
[COLOR="Red"]What do you base your concern on?[/COLOR]

A friend of mine who happens to be a linux novice told me that a firewall is basically unnecessary in linux, but having luck with guarddog i figured i would try firestarter out.  almost immediately after configuration firestarter was blocking hits from various ports but i was startled to see constant blocks on port 54433 which i had been using for incoming connections for bittorrent on windows. is that bad or normal? this leads me to believe that i should maintain some protection but im not completely understanding how firewalls work on linux. i've read that the "iptables" is always active and stealths all ports by default. is that correct? 

my main question now after reading your response would be "if a firewall is superfluous on ubuntu, am i just as safe without one as i am on xp with ZA enabled?"
[COLOR="Red"]
In what way did guarddog work well for you?

[/COLOR]
guarddog just seemed to work properly. if i enabled http:80, firefox would work, with http disabled it didnt, for example. firestarter only seemed to work for certain applications/ports, but its possible that i had it configured wrong.

[COLOR="Red"]You're offering no services externally so a firewall is superfluous. And having no trouble connecting to the internet is good, is it not?
[/COLOR]

what would be considered a service? pidgin, firefox, or azureus maybe? 

[COLOR="Red"]Put it in the garbage anyway. Your single machine will gain nothing from having a firewall.[/COLOR]

even while using, for example, azureus or other p2p apps? i felt somewhat secure with peerguardian blocking over 3 billion bad ip ranges. is there some way to do this in ubuntu?

thanks in advance - i just want to make sure i'm not an online target or having major security flaws. 

-joe

---

### Post by FastZ on 2008-05-03
Open-SuSe-A-Me, first of all, the Linux firewall is called IPTABLES.  Such programs like Firestarter and Guarddog are just GUI front-ends to help make setting up IPTABLES a little easier.  

You're seeing that no ports are open and you can still access the Internet because "no ports open" means that you are not accepting connections from the outside in, but you can still connect from the inside out.

> if i can match the functionality of the zone alarm/peerguardian(for p2p use) combo i have on winxp then windows can go in the garbage.Put Windows in the trash because you've already surpassed the zone alarm/peerguardian functionality by installing Linux in the first place.

(just saw your second post there so I decided to add on)

> what would be considered a service? pidgin, firefox, or azureus maybe? 
What brian_p is talking about when he said "you're offering no services externally" is that you're not running any server applications, like apache web server, FTP, etc.  Basically services that are accessed from outside your network are considered "external services".  Pidgin and the others aren't what he was talking about.

---

### Post by brian_p on 2008-05-03
> **Open-SuSe-A-Me said:**
> [COLOR="Red"]What do you base your concern on?[/COLOR]

A friend of mine who happens to be a linux novice told me that a firewall is basically unnecessary in linux, but having luck with guarddog i figured i would try firestarter out.  almost immediately after configuration firestarter was blocking hits from various ports but i was startled to see constant blocks on port 54433 which i had been using for incoming connections for bittorrent on windows. is that bad or normal?

Nothing was listening on port 54433 so the connection attempts were going nowhere. You'll have more peace of mind by removing firestarter and knowing what services you do have running.

>  this leads me to believe that i should maintain some protection but im not completely understanding how firewalls work on linux. i've read that the "iptables" is always active and stealths all ports by default. is that correct? 

iptables keeps its rules in memory. You could use that memory for better purposes.

> my main question now after reading your response would be "if a firewall is superfluous on ubuntu, am i just as safe without one as i am on xp with ZA enabled?"

Yes. And you rid yourself of the overhead which comes with ZA.

> what would be considered a service? pidgin, firefox, or azureus maybe? 

Already answered but you could add mail servers and ssh.

> [COLOR="Red"]Put it in the garbage anyway. Your single machine will gain nothing from having a firewall.[/COLOR]

even while using, for example, azureus or other p2p apps? i felt somewhat secure with peerguardian blocking over 3 billion bad ip ranges. is there some way to do this in ubuntu?

Yes. Any serious security issue with an open source p2p application would be fixed very quickly. If you have a need to restrict who can connect you could look at tcpwrappers (/etc/hosts.allow and /etc/hosts.deny)

> thanks in advance - i just want to make sure i'm not an online target or having major security flaws. 

If you allow external access to your machine keep the software up to date and configure it sensibly. That's all that's needed.

---

### Post by FastZ on 2008-05-03
> **brian_p said:**
> Nothing was listening on port 54433 so the connection attempts were going nowhere. You'll have more peace of mind by removing firestarter and knowing what services you do have running.



iptables keeps its rules in memory. You could use that memory for better purposes.



Yes. And you rid yourself of the overhead which comes with ZA.



Already answered but you could add mail servers and ssh.



Yes. Any serious security issue with an open source p2p application would be fixed very quickly. If you have a need to restrict who can connect you could look at tcpwrappers (/etc/hosts.allow and /etc/hosts.deny)



If you allow external access to your machine keep the software up to date and configure it sensibly. That's all that's needed.

I don't really think suggesting that he strip his machine of any firewall whatsoever is a very good thing to do.  At a minimum, you should keep a default iptables configuration on your machine.  There are viruses out there written for Linux as well so it's better to be safe than sorry in my opinion.

---

### Post by brian_p on 2008-05-03
> **FastZ said:**
> I don't really think suggesting that he strip his machine of any firewall whatsoever is a very good thing to do.  At a minimum, you should keep a default iptables configuration on your machine.  There are viruses out there written for Linux as well so it's better to be safe than sorry in my opinion.

The default iptables configuration will suit the OP well. It has served me splendidly for many years.

You're not after thinking a firewall can deal with malware, are you? How does it do that?

---

### Post by SjRaptor on 2008-05-04
> **brian_p said:**
> The default iptables configuration will suit the OP well. It has served me splendidly for many years.

You're not after thinking a firewall can deal with malware, are you? How does it do that?

What default iptables configuration? This?


[HTML]# iptables -nL
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination[/HTML]

---

### Post by brian_p on 2008-05-04
> **SjRaptor said:**
> What default iptables configuration? This?


[HTML]# iptables -nL
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination[/HTML]

Yes, that's the one. It's a superb configuration for the OP's circumstances.

---

### Post by Open-SuSe-A-Me on 2008-05-04
thanks for all the input...i'll stick with the default.  is there a way i can confirm that this is how my firewall is configured (in a terminal probably)? should i rely on the "shields up" website?


thanks-joe

---

### Post by c007c on 2008-05-04
This may have been answered already, but I'm curious, whats between you and the internet? Are you directly connected to a cable modem, or do you have a router?

---

### Post by brett611 on 2008-05-04
I've had many problems with Firestarter myself and have been told a thousand different things, ranging from "you don't need it" to "you don't have a problem" yet if I did any tests I would find my system was wide open.

This link here is engraved in concrete in my office as it is the only thread that actually resolves the problem and provides clear instructions.

[http://ubuntuforums.org/showthread.php?t=542756](http://ubuntuforums.org/showthread.php?t=542756)

Brett

---

### Post by Open-SuSe-A-Me on 2008-05-04
i am connected to a linksys router (wired). i know that a router has somewhat of a firewall-type functionality, though im not 100% clear. i have been opening ports through the 192.168.x.x page and it seems to work, though i still cant change the yellow smiley face in azureus to green.

---

### Post by ghostknife on 2008-05-04
> **Open-SuSe-A-Me said:**
> i am currently using "gnome-lokkit" which says all ports are closed though no programs i use have trouble connecting to the internet.

Note that in Windows firewalls block outgoing ports because of the huge virus/spyware problems. Linux doesn't have that problem by design, so blocking outgoing ports is sort of pointless, except for controlling users.

Just thought I'd add my salt to the flavor.

---

### Post by c007c on 2008-05-04
> **Open-SuSe-A-Me said:**
> i am connected to a linksys router (wired). i know that a router has somewhat of a firewall-type functionality, though im not 100% clear. i have been opening ports through the 192.168.x.x page and it seems to work, though i still cant change the yellow smiley face in azureus to green.

Most, if not all home routers today are also firewalls by default, all use some sort of "iptables" setup. I see no reason to run a second firewall on your system. If your having to forward ports, your router is pretty tight. Local firewall SW is used primarily for people that plug the computer directly to the ISP Cable/DSL modem. I would suggest you spend more effort at the router. Depending on the model, you can get rid of the Linksys Firmware, and use a third party, like DD-WRT, or Tomato, which offer a lot of enhanced functions. I am very familiar with them, and prefer Tomato, because of the QoS functionality. If you post your router model, I can suggest.

Scan with this from the internet...There are sections to specify ports you are concerned with

[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

---

### Post by Open-SuSe-A-Me on 2008-05-04
c007,
the shields up site says my first 1056 or so ports are stealthed, but i failed the "ping echo" test. should i remedy this? 

also if you have any more information about using the router firewall that would help. my router is a linksys "wrt54g", though i would be hesitant about modifying the firmware because (1) the router itself is connected to a different pc in my house, and (2) others in my house rely on the routed connection for work purposes so i wouldnt want to cause any internet connection headaches.

thanks- joe

---

### Post by brian_p on 2008-05-04
> **Open-SuSe-A-Me said:**
> thanks for all the input...i'll stick with the default.  is there a way i can confirm that this is how my firewall is configured (in a terminal probably)? should i rely on the "shields up" website?

Remember that grc.com will be probing your router not your machine. I failed and received dire warnings of impending doom so had to have a little lie down before writing this.

```
nmap -sT localhost
```

in a terminal probes your computer. Add -p 20-65535 to scan more ports. Some care is needed to interpret the output.

On this machine I get:

```
Starting Nmap 4.11 ( http://www.insecure.org/nmap/ ) at 2008-05-04 15:53 BST
Interesting ports on localhost (127.0.0.1):
Not shown: 65507 closed ports
PORT      STATE SERVICE
22/tcp    open  ssh
25/tcp    open  smtp
111/tcp   open  rpcbind
113/tcp   open  auth
631/tcp   open  ipp
2208/tcp  open  unknown
6000/tcp  open  X11
49055/tcp open  unknown
49654/tcp open  unknown
```

I know I have smtp and rpcbind configured to only listen to localhost. Similarly, cupsd (ipp) rejects jobs coming from the internet. So they are ok.

What are the unknown services?

```
sudo lsof -Pni :49654
```

outputs

```
COMMAND  PID  USER   FD   TYPE DEVICE SIZE NODE NAME
python  2615 hplip    4u  IPv4   6938       TCP 127.0.0.1:49654 (LISTEN)
```

hplip is part of the printing system. No problems there. And so on .....

---

### Post by brian_p on 2008-05-04
> **Open-SuSe-A-Me said:**
> c007,
the shields up site says my first 1056 or so ports are stealthed, but i failed the "ping echo" test. should i remedy this? 

Gibson likes putting the frighteners on Windows users:

> Ping Reply: RECEIVED (FAILED) — Your system REPLIED to our Ping (ICMP Echo) requests, making it visible on the Internet. Most personal firewalls can be configured to block, drop, and ignore such ping requests in order to better hide systems from hackers. This is highly recommended since "Ping" is among the oldest and most common methods used to locate systems prior to further exploitation.


The last sentence twists the knife a little and is misleading. There can be no 'further exploitation' because all the ports on your router are closed. Even if some were open the services would be secure because your software is up to date. There is nothing to remedy. Visibility is good.

---

### Post by Open-SuSe-A-Me on 2008-05-04
this is what i get from nmap:

Starting Nmap 4.53 ( [http://insecure.org](http://insecure.org) ) at 2008-05-04 11:39 EDT
Interesting ports on localhost (127.0.0.1):
Not shown: 65512 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
631/tcp  open  ipp
8118/tcp open  privoxy
9050/tcp open  tor-socksport


i have privoxy and tor installed though i havent been using them or letting them run...i used them alot in windows so i know how they work but i havent had any luck getting them to work in ubuntu. should these ports be open if i'm not using the services?

on a side note...should i be saying "yoo-bun-too", or "oo-boon-too"?

---

### Post by c007c on 2008-05-04
> **Open-SuSe-A-Me said:**
> c007,
the shields up site says my first 1056 or so ports are stealthed, but i failed the "ping echo" test. should i remedy this? 

also if you have any more information about using the router firewall that would help. my router is a linksys "wrt54g", though i would be hesitant about modifying the firmware because (1) the router itself is connected to a different pc in my house, and (2) others in my house rely on the routed connection for work purposes so i wouldnt want to cause any internet connection headaches.

thanks- joe

Stealthed means from the outside, the attacker can't tell if the ports are open or closed, not responding to a ping is good, external programs use pings to verify the existence of a victim to exploit. Both are good. You could enable pings from the linksys GUI for the test, then put it back. Remember, internet based tests reflect the router's security, not the local system. Notice the IP with the test. Its not the NAT IP your system uses. You would have to remove the router, connect the PC directy to see what the system has.

Your router is basically a system with only the HW and SW (Firmware) required to perform networking functions, including firewall. Depending on the vendor, the firmware has more or less capability. 

Third party router firmwares are like what Ubuntu is to Windows. Added performance and functionality, for free, with the support of users. They use unix! Ever try calling Linksys with a problem? Thats when I first flashed my router 3 years ago, and can't imagine going back.

So to answer your question, your router and network will function the same, just faster, with more options. I have flashed close to 20 54g routers for people, with no probs. The reliability of the 54g factory firmware (vxworks) is known for internet drops, network hangs, poor throughput, and connection port forwarding problems, Depending on the version number on the bottom of the router, you will know how bad (1-4 decent, 5-6 bad, 7-8 worst). And if your not using QoS, when you run a torrent or p2p program, your network grinds to a halt.

a 54g runs great with DD-WRT. Do some reading here, poke around the forum, and you'll see its just like Ubuntu, a whole community of router dudes. 

[http://www.dd-wrt.com](http://www.dd-wrt.com)

---

### Post by brian_p on 2008-05-04
> **Open-SuSe-A-Me said:**
> this is what i get from nmap:

Starting Nmap 4.53 ( [http://insecure.org](http://insecure.org) ) at 2008-05-04 11:39 EDT
Interesting ports on localhost (127.0.0.1):
Not shown: 65512 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
631/tcp  open  ipp
8118/tcp open  privoxy
9050/tcp open  tor-socksport


i have privoxy and tor installed though i havent been using them or letting them run...i used them alot in windows so i know how they work but i havent had any luck getting them to work in ubuntu. should these ports be open if i'm not using the services?


An open port means a service is being offered. You may not be deriving any benefit from them but privoxy and tor are running.

```
sudo /etc/init.d/privoxy stop
```

and do nmap -sT again.

---

### Post by hyper_ch on 2008-05-05
> **brett611 said:**
> yet if I did any tests I would find my system was wide open.Brett
Can you elaborate more how your system was wide open?

> **Open-SuSe-A-Me said:**
> i am connected to a linksys router (wired). i know that a router has somewhat of a firewall-type functionality, though im not 100% clear. i have been opening ports through the 192.168.x.x page and it seems to work, though i still cant change the yellow smiley face in azureus to green.
You need to forward all according ports... easiest would be to set your router to UPnP (on Windows I would advice against it, on Linux - if you know what you have installed - I don't see much of a problem there).

> **c007c said:**
> like DD-WRT, or Tomato [...] I am very familiar with them, and prefer Tomato, because of the QoS functionality. If you post your router model, I can suggest
Been a long time dd-user and just changed to tomato. The way QoS is handled on Tomate is just great.

> **Open-SuSe-A-Me said:**
> my router is a linksys "wrt54g"
That runs DD and Tomat perfectly well.. you should test that.

> **Open-SuSe-A-Me said:**
> (1) the router itself is connected to a different pc in my house, and (2) others in my house rely on the routed connection for work purposes so i wouldnt want to cause any internet connection headaches.
You'll just have to setup all that again. Best have a look at your current setup, take notes on where you did set what... where you route what to... I think you can even export the current config... Once that done, install tomato or dd firmware.
[http://www.dd-wrt.com/dd-wrtv3/index.php](http://www.dd-wrt.com/dd-wrtv3/index.php) --> [http://www.dd-wrt.com/dd-wrtv2/downloads/release%20candidates/DD-WRT%20v24%20RC1/GENERIC%20BROADCOM%20(Linksys,%20Asus%20etc.)/dd-wrt.v24_mini_wrt54g.bin]("http://www.dd-wrt.com/dd-wrtv2/downloads/release%20candidates/DD-WRT%20v24%20RC1/GENERIC%20BROADCOM%20(Linksys,%20Asus%20etc.)/dd-wrt.v24_mini_wrt54g.bin")

[http://www.polarcloud.com/tomato](http://www.polarcloud.com/tomato) --> [http://www.polarcloud.com/f/Tomato_1_19.7z](http://www.polarcloud.com/f/Tomato_1_19.7z)

---

### Post by c007c on 2008-05-05
> **hyper_ch said:**
> 

That runs DD and Tomat perfectly well.. you should test that.




Careful! Only the older versions (v1-4, 8mb flash) of the WRT54g can run Tomato. Linksys made the flash smaller in the newer models (v5-current, 2mb flash), so he would only use DD-WRT micro (1.7mb) on those. The Tomato trx file is 2.8mb. Why I told him to tell me the version in an earlier reply.

---

### Post by hyper_ch on 2008-05-05
they cut it down to 2mb???

---

### Post by c007c on 2008-05-05
Yes - in an attempt to thwart third party firmware installs, they shrunk the flash, and went backwards in time, and replaced busybox with vxworks, which is incompatible with what seems like any open source. There's so many of them, and so many problems. I bet there's tons of posts in here for  various wireless/networking issues, that actaully are the result of the "vxworks internet drop syndrome". Especially noticeable with Comcast Cable. 

So now the process is, get back to busybox using a "vxworks killer" program from bitsum, install DD-WRT bin. I've flashed and tested almost every model out there, and the GL models are the only good Linksys models left, which is sad. I always recommend Buffalo, but they were recently banned from the US until patent issues get ironed out.

---

### Post by Open-SuSe-A-Me on 2008-05-05
c007c, 

my firmware version is indeed v8, though i havent had any connection problems as far as i know. could this be why azureus is having trouble reaching "green smiley" status?  my torrent connections worked fine in windows and i am a little stumped. also i have a fat32 formatted portable hd and i can read the files within but cant write onto the disc - i get an error, any suggestions?

thanks - joe

---

### Post by brett611 on 2008-05-07
Hyper-CH:  by wide open I mean that every time i restarted my pc if i didn't also manually start Firestarter iptables would have Policy ACCEPT for everything...vs Policy DROP.

---

