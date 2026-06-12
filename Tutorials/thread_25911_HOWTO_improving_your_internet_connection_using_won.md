---
title: "HOWTO improving your internet connection using wondershaper"
date: 2005-04-11
forum: Tutorials
---

### Post by ubuntu_demon on 2005-04-11
I just downgraded my internet connection. I just hate it when a p2p application prevents me from browsing the web fast. So let's do something about it :)

wondershaper is an easy to use traffic shaping script that provides these improvements:

 * Low latency for interactive traffic (and pings) at all times
 * Allow websurfing at reasonable speeds while uploading / downloading
 * Make sure uploads don't hurt downloads
 * Make sure downloads don't hurt uploads

official webpage :
[http://lartc.org/wondershaper](http://lartc.org/wondershaper)

about the ubuntu package :
[http://packages.ubuntu.com/hoary/net/wondershaper](http://packages.ubuntu.com/hoary/net/wondershaper)

/usr/share/doc/wondershaper contains readme files. You might want to read these also.

I'm using firestarter together with wondershaper. Nothing has to be changed to firestarter.

So here we go :
sudo apt-get install wondershaper

use ifconfig to determine which of your networkcards is the one that is connected to your modem (and thus the internet).

$ifconfig

the networkcard that has your normal ip adress is the one (not 192.168.x.x)

Go to a speedtesting website (for example a speedtesting website by your internet provider or [www.speedtest.nl](www.speedtest.nl) if you live in the netherlands) and determine your average upload and download speed. Use these speeds as a guide.

$sudo wondershaper eth1 downspeed upspeed

download a big and uncompressable file while pinging to a fast and stable server on the internet or to your modem and adjust your downspeed until you are satisfied :

$sudo wondershaper eth1 downspeed upspeed

Now do the same with uploading a big and uncompressable file.

You have to tweak these settings a while until you are satisfied. When you are ready you can make these connection settings permanent by :

$ sudo pico /etc/network/interfaces

add these lines under eth1 if eth1 is your internetconnection. Change eth1,upspeed and downspeed to your settings.

```

up /sbin/wondershaper eth1 downspeed upspeed
down /sbin/wondershaper clear eth1

```

And we are done!

edit : removed a bug from interfaces

---

### Post by soul_rebel on 2005-04-11
Thanks for the howto.
In what format are the speeds?
could you hint some extra tweaking? has wordershaper a global config file or any other interesing option?

---

### Post by ubuntu_demon on 2005-04-11
[QUOTE=soul_rebel]Thanks for the howto.
In what format are the speeds?
could you hint some extra tweaking? has wordershaper a global config file or any other interesing option?[/QUOTE]
 speeds are in kilobits per second

you can use clear wondershaper from an network interface using :
sudo wondershaper clear eth1

There are no other configuration options. wonderhaper is easy. If you want more power as far as  I know the best option is to build your own firewall yourself. 

This is a nice howto. But its written for gentoo :

[http://gentoo-wiki.com/HOWTO_Packet_Shaping](http://gentoo-wiki.com/HOWTO_Packet_Shaping)

Maybe I'll write my own Ubuntu howto in the future. I first need to learn about it :)

---

### Post by soul_rebel on 2005-04-11
I just installed that on my suse gateway and I found that the suse package is much more complete as usual (sadly) it has a /etc/sysconfig/wondershaper config file and an /etc/init.d/wondershaper. You edit the config and add the service.
I think ubuntu should learn (and copy) this way of packaging stuff.

---

### Post by rwabel on 2005-04-11
[QUOTE=soul_rebel]I just installed that on my suse gateway and I found that the suse package is much more complete as usual (sadly) it has a /etc/sysconfig/wondershaper config file and an /etc/init.d/wondershaper. You edit the config and add the service.
I think ubuntu should learn (and copy) this way of packaging stuff.[/QUOTE]
 any chance to define the upload speed for a specific application?
I found a tool for doing it, it's called trickle. But somehow it consumed too much ressource with some p2p tools

---

### Post by ubuntu_demon on 2005-04-12
[QUOTE=rwabel]any chance to define the upload speed for a specific application?
I found a tool for doing it, it's called trickle. But somehow it consumed too much ressource with some p2p tools[/QUOTE]
 wondershaper is nice because it's very easy

The best solution is writing your own rules. (A script to set up iptables filter+mangler and using tc do traffic shaping just like you want it) It isn't very hard. I'm reading about it and if I have succeeded I'll probably make an HOWTO.

In this topic I started I invite everyone to comment on the script I'm writing (it isn't finished) :
[http://www.ubuntuforums.org/showthread.php?t=26055](http://www.ubuntuforums.org/showthread.php?t=26055)

---

### Post by Get on 2005-04-16
Very nice, it help me very much, thx for the howto!

---

### Post by ubuntu_demon on 2005-04-16
[QUOTE=Get]Very nice, it help me very much, thx for the howto![/QUOTE]
 glad to help :)

---

### Post by psypher on 2005-04-17
[QUOTE=demon666_nl]speeds are in kilobits per second

This is a nice howto. But its written for gentoo :

[http://gentoo-wiki.com/HOWTO_Packet_Shaping](http://gentoo-wiki.com/HOWTO_Packet_Shaping)

Maybe I'll write my own Ubuntu howto in the future. I first need to learn about it :)[/QUOTE]

I agree with demon, that is one brillaint HOWTO. Also been scouring for a while to find a good one and thats so far the best. As long as you get all the software installed it's doesn't matter if it's gentoo or not, will work on all distros. Thanks for the link!

---

### Post by ubuntu_demon on 2005-04-17
[QUOTE=psypher]I agree with demon, that is one brillaint HOWTO. Also been scouring for a while to find a good one and thats so far the best. As long as you get all the software installed it's doesn't matter if it's gentoo or not, will work on all distros. Thanks for the link![/QUOTE]
 there's more links in this thread :

[http://www.ubuntuforums.org/showthread.php?t=26055](http://www.ubuntuforums.org/showthread.php?t=26055)

I'm going to make my own packet scheduling script fitted for my own situation and post it there with some comments.

---

### Post by ShaneAu on 2005-04-25
How do I go about putting my settings back to default for eth0? :).

---

### Post by ubuntu_demon on 2005-04-25
[QUOTE=ShaneAu]How do I go about putting my settings back to default for eth0? :).[/QUOTE]
 ```
$ wondershaper clear eth0 
```

should do the trick

---

### Post by ShaneAu on 2005-04-26
[QUOTE=demon666_nl]```
$ sudo wondershaper clear eth0 
```

should do the trick[/QUOTE]
 Thank you.. :).

---

### Post by ubuntu_demon on 2005-04-26
[QUOTE=ShaneAu]Thank you.. :).[/QUOTE]
i forgot to type the sudo ;) (editted now)

---

### Post by Sniffer on 2005-04-26
Thka for this tip, improving net connect is always a good thing.... :)

---

### Post by Pulsie on 2005-06-30
Thanks for the great HOWTO; it's exactly what I was looking for.  I believe there is one small typo though.  The sample code should read as follows:

```
up /sbin/wondershaper eth1 **downspeed upspeed**
down /sbin/wondershaper clear eth1
```

---

### Post by ubuntu_demon on 2005-06-30
[QUOTE=Pulsie]Thanks for the great HOWTO; it's exactly what I was looking for.  I believe there is one small typo though.  The sample code should read as follows:

```
up /sbin/wondershaper eth1 **downspeed upspeed**
down /sbin/wondershaper clear eth1
```[/QUOTE]
 thnx I editted it :)

---

### Post by bored2k on 2005-08-12
- How would wondershaper improve my internet connection if the only P2P program I use is BitTorrent with the upload rates capped ?

- And btw, after I see my speed results on the speedtest webpage (dslreports.com), am I supposed to input those same numbers to wondershaper or what ?

BTW, that gentoo shaping guide looks hotter than hot.

---

### Post by buildid on 2005-08-12
*just downgraded my internet connection. I just hate it when a p2p application prevents me from browsing the web fast. So let's do something about it * 

with an normal connection and enough upload speed "125 KB/s " , using an upload speed of 100 , i believe the script is not needed .

wit an upload speed that is set to max or close to max setting , then this is probally a good idear .

---

### Post by ubuntu_demon on 2005-08-12
wondershaper improves your connection a bit by moving the upload queue from the cable modem to your computer. 

the upload speed number is best measured like this :
1)do a upload speedtest with no other stuff running that uses the internet connection
2)run bittorrent and upload as much as possible
3)ping a fast server and very slowly cap you bittorrent client down until you have a low and stable ping. 
4) Use this capped speed that the bittorrent client gives you to enter into wondershaper's upload speed
5)cap your bittorrent client a couple of kbytes lower so you can still surf the internet fast

You can experiment a bit with a bit lower numbers than you measure on the speedtest webpage. But moving the download queue from the cable modem to the computer is kinda useless because the packets have arrived anyway. 

I have written myself a more advanced traffic shaper. But it's not very userfriendly so I won't share it yet. I'll create something nice somewhere in the future.

---

### Post by bored2k on 2005-08-12
[QUOTE=ubuntu_demon]wondershaper improves your connection a bit by moving the upload queue from the cable modem to your computer. 

the upload speed number is best measured like this :
1)do a upload speedtest with no other stuff running that uses the internet connection
2)run bittorrent and upload as much as possible
3)ping a fast server and very slowly cap you bittorrent client down until you have a low and stable ping. 
4) Use this capped speed that the bittorrent client gives you to enter into wondershaper's upload speed
5)cap your bittorrent client a couple of kbytes lower so you can still surf the internet fast

You can experiment a bit with a bit lower numbers than you measure on the speedtest webpage. But moving the download queue from the cable modem to the computer is kinda useless because the packets have arrived anyway. 

I have written myself a more advanced traffic shaper. But it's not very userfriendly so I won't share it yet. I'll create something nice somewhere in the future.[/QUOTE]
 Thanks. I'll try it tomorrow when I'm half awake. I'll also read some of Gentoo's guide on this too as it really looked interesting.

BTW, how is manually writting the script better ?

---

### Post by ubuntu_demon on 2005-08-12
[QUOTE=buildid]*just downgraded my internet connection. I just hate it when a p2p application prevents me from browsing the web fast. So let's do something about it * 

with an normal connection and enough upload speed "125 KB/s " , using an upload speed of 100 , i believe the script is not needed .

wit an upload speed that is set to max or close to max setting , then this is probally a good idear .[/QUOTE]
 actually this script does work. But you can get a much greater profit when you write your own traffic shaper rules because in that way you can prioritize some game above p2p traffic for example.

---

### Post by ubuntu_demon on 2005-08-12
[QUOTE=bored2k]Thanks. I'll try it tomorrow when I'm half awake. I'll also read some of Gentoo's guide on this too as it really looked interesting.

BTW, how is manually writting the script better ?[/QUOTE]
 like I said in the other answer : you can prioritize some traffic above other traffic. You can make it as complicated as you want.

I have had a couple of people playing games on the internet with a good ping while using bittorrent as fast as possible

---

### Post by Trojan1313 on 2005-08-12
Will I get a speed difference if I run a conection-tester in Wine?
I could of course use it on one of my windows computers, but that would be cheating. ;)

---

### Post by ubuntu_demon on 2005-08-12
[QUOTE=Trojan1313]Will I get a speed difference if I run a conection-tester in Wine?
I could of course use it on one of my windows computers, but that would be cheating. ;)[/QUOTE]
 you have to run it on the computer that's directly connected to the cable modem

the speedtest doesn't matter much it's only an indication for the number that you will have to tweak anyway using bittorrent or some other heavy uploading application that you can throttle.(while pinging some fast and reliable/stable server)

---

### Post by Trojan1313 on 2005-08-12
[QUOTE=ubuntu_demon]you have to run it on the computer that's directly connected to the cable modem

the speedtest doesn't matter much it's only an indication for the number that you will have to tweak anyway using bittorrent or some other heavy uploading application that you can throttle.(while pinging some fast and reliable/stable server)[/QUOTE]
Sorry, didn't quite get that.
Isn't it kind of important what you're speed is when tweaking?

What do you mean by trottle while pinging servers...?

---

### Post by ubuntu_demon on 2005-08-12
[QUOTE=Trojan1313]Sorry, didn't quite get that.
Isn't it kind of important what you're speed is when tweaking?
[/QUOTE]

I just meant that it doesn't matter much where you start ... it only takes more time if you start farther away from the ideal speed.

[QUOTE=Trojan1313]
What do you mean by trottle while pinging servers...?[/QUOTE]

just adjust your upload speed in bittorrent while looking at the ping times to a fast server in your terminal. (if they go up or become "unstable" then you are too high)

---

### Post by Trojan1313 on 2005-08-12
[QUOTE=ubuntu_demon]I just meant that it doesn't matter much where you start ... it only takes more time if you start farther away from the ideal speed.



just adjust your upload speed in bittorrent while looking at the ping times to a fast server in your terminal. (if they go up or become "unstable" then you are too high)[/QUOTE]
So what I need to config my connection is a good torrent and a fast server to ping?

---

### Post by FLeiXiuS on 2005-08-12
Great shaper, I've been using it for a while.  If you want to gain even more performance try using Quality of Service (QoS) :-)

Great Tip Demon, I took a much harder route to getting it working this was much simpler.

---

### Post by Trojan1313 on 2005-08-12
[QUOTE=FLeiXiuS]Great shaper, I've been using it for a while.  If you want to gain even more performance try using Quality of Service (QoS) :-)

Great Tip Demon, I took a much harder route to getting it working this was much simpler.[/QUOTE]
 Isn't Wonder Shaper meant to do what QoS does? Or even to shape QoS?

---

### Post by ubuntu_demon on 2005-08-13
[QUOTE=Trojan1313]So what I need to config my connection is a good torrent and a fast server to ping?[/QUOTE]
 yeah. or a client like azureus with a couple of torrents.

---

### Post by ubuntu_demon on 2005-08-13
[QUOTE=Trojan1313]Isn't Wonder Shaper meant to do what QoS does? Or even to shape QoS?[/QUOTE]
 [http://en.wikipedia.org/wiki/Quality_of_service](http://en.wikipedia.org/wiki/Quality_of_service)

> 
In the fields of packet-switched networks and computer networking, the traffic engineering term Quality of Service (QoS) refers to the probability of the telecommunication network meeting a given traffic contract, or in many cases is used informally to refer the probability of a packet succeeding in passing between two points in the network.


wondershaper is a traffic shaper and all traffic shapers aim to optimize QoS

---

### Post by Trojan1313 on 2005-08-14
Okej then. Now I'm going to get Azureus working, start about 5 torrents, then write "ping www.sunet.se". After that, wich speed is it I should start adjusting, is it download or upload?

---

### Post by ubuntu_demon on 2005-08-15
[QUOTE=Trojan1313]Okej then. Now I'm going to get Azureus working, start about 5 torrents, then write "ping www.sunet.se". After that, wich speed is it I should start adjusting, is it download or upload?[/QUOTE]
 upload

you can try the same with the download speed but it won't have much effect (maybe a little bit more effect if you have a real crappy ISP)

---

### Post by Trojan1313 on 2005-08-15
[QUOTE=ubuntu_demon]upload

you can try the same with the download speed but it won't have much effect (maybe a little bit more effect if you have a real crappy ISP)[/QUOTE]
 Ok, I'm going to try it later today. :)
I don't have a crappy ISP, I have 5,5/5mbps (well, somewhere around that). :)

---

### Post by Trojan1313 on 2005-08-15
Now I tried pinging [www.sunet.se](www.sunet.se) while changing the speeds, but I just can't see a very big difference, I get around 15ms all the time. :s

And still my connectivity with Jpopsuki is set as "bad". :(

---

### Post by Nano on 2005-08-15
I use another way which seems to me much simplier.
I use "Trickle", which is another bandwidth shaper but extremely simple and does its job perfectly.

As you know, if you limit your upload speed in amule your download speed will also be affected, for this I use trickle.

```

sudo apt-get install trickle

```

Once trickle is installed I launch amule with the following command:

```

trickle -u 10 -d 100 amule

```

So amule will always run inside that bandwidth limit (10 upload, 100 download) but it will think it's because my ISP doesn't allow me to have more.

Of course, this can be used for any kind of app.

Should I write another HOWTO for this, folks?

---

### Post by Trojan1313 on 2005-08-15
But that's just for aMule, right? Or can you use trickle for other apps as well?

---

### Post by Nano on 2005-08-15
[QUOTE=Trojan1313]But that's just for aMule, right? Or can you use trickle for other apps as well?[/QUOTE]
 as I said 2 lines above your reply:

"Of course, this can be used for any kind of app."

:)

---

### Post by Trojan1313 on 2005-08-15
[QUOTE=Nano]as I said 2 lines above your reply:

"Of course, this can be used for any kind of app."

:)[/QUOTE]
 Wops, I missed that. :p :)
Do you specify bandwidth in kilobits or megabits?

---

### Post by Nano on 2005-08-16
[QUOTE=Trojan1313]Wops, I missed that. :p :)
Do you specify bandwidth in kilobits or megabits?[/QUOTE]
 In kb...

Once you install trickle it also installes trickled, which is a daemon you can also use for prioritize applications. 
For more info type: man trickle.

Cheers

---

### Post by ubuntu_demon on 2005-08-16
[QUOTE=Nano]I use another way which seems to me much simplier.
I use "Trickle", which is another bandwidth shaper but extremely simple and does its job perfectly.
...
...
Should I write another HOWTO for this, folks?[/QUOTE]
 would be nice if you would write another howto for that. I'm sure there are people who want it.

---

### Post by Nano on 2005-08-16
[QUOTE=ubuntu_demon]would be nice if you would write another howto for that. I'm sure there are people who want it.[/QUOTE]
 Ok, I'll write it down today when I'm back from the gym.
Word.

---

### Post by Trojan1313 on 2005-08-21
[QUOTE=ubuntu_demon]use ifconfig to determine which of your networkcards is the one that is connected to your modem (and thus the internet).

$ifconfig

the networkcard that has your normal ip adress is the one (not 192.168.x.x)[/QUOTE]
But if you have a router and it's the router that's connected to the Internet, then this would be it, right?

As in my case...

eth0      Link encap:Ethernet  HWaddr 00:80:48:1E:77:B0
          inet addr:192.168.0.168  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::280:48ff:fe1e:77b0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:390564 errors:0 dropped:0 overruns:0 frame:0
          TX packets:555156 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:84422430 (80.5 MiB)  TX bytes:746013932 (711.4 MiB)
          Interrupt:21 Base address:0xc800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:178980 errors:0 dropped:0 overruns:0 frame:0
          TX packets:178980 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:25614583 (24.4 MiB)  TX bytes:25614583 (24.4 MiB)


Since it's just internal and loopback I don't see the danger in posting it. :p

---

### Post by ubuntu_demon on 2005-08-23
[QUOTE=Trojan1313]But if you have a router and it's the router that's connected to the Internet, then this would be it, right?

As in my case...

eth0      Link encap:Ethernet  HWaddr 00:80:48:1E:77:B0
          inet addr:192.168.0.168  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::280:48ff:fe1e:77b0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:390564 errors:0 dropped:0 overruns:0 frame:0
          TX packets:555156 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:84422430 (80.5 MiB)  TX bytes:746013932 (711.4 MiB)
          Interrupt:21 Base address:0xc800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:178980 errors:0 dropped:0 overruns:0 frame:0
          TX packets:178980 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:25614583 (24.4 MiB)  TX bytes:25614583 (24.4 MiB)


Since it's just internal and loopback I don't see the danger in posting it. :p[/QUOTE]
 if you have a router you have to do the shaping on the router. If the router is not a regular pc most of the time shaping isn't possible. If the router is a pc you should run linux (ubuntu :-P) or bsd to do the shaping.

It doesn't make sense at all to do shaping on a pc that's connected using a router.

---

### Post by Trojan1313 on 2005-08-24
[QUOTE=ubuntu_demon]if you have a router you have to do the shaping on the router. If the router is not a regular pc most of the time shaping isn't possible. If the router is a pc you should run linux (ubuntu :-P) or bsd to do the shaping.

It doesn't make sense at all to do shaping on a pc that's connected using a router.[/QUOTE]
 Meaning I can't shape when on a router? 
That's odd, when I read about how shaping worked it would seem that it just limits my bandwidth so that there won't be any queues at my ISP, since that takes a lot of time sending information back and forth.

Basicly what I'm saying is, isn't it the other PCs connected to the router that's causing my problem and not the router itself? Am I making any sense?

But how come then my connection worked prefectly in Windows and... well... bad, in Linux? Isn't Linux supposed to be teh network OS? This doesn't make sense to me. (and no, I do not want to return to Windows, I just want a Windows-like Internet connection ;))

---

### Post by ubuntu_demon on 2005-08-25
[QUOTE=Trojan1313]Meaning I can't shape when on a router? 
That's odd, when I read about how shaping worked it would seem that it just limits my bandwidth so that there won't be any queues at my ISP, since that takes a lot of time sending information back and forth.
[/quote]

for the best effect you should shape at your router (or direct connected pc) and not on the pc connected to the router. You want to move the upload queue from your cable modem to your router.

[QUOTE=Trojan1313]
Basicly what I'm saying is, isn't it the other PCs connected to the router that's causing my problem and not the router itself? Am I making any sense?
[/quote]

uploading a lot of stuff from one pc will always have some effect on quality of the internet connection

Do you have a ubuntu pc configured as router ?

[QUOTE=Trojan1313]
But how come then my connection worked prefectly in Windows and... well... bad, in Linux? Isn't Linux supposed to be teh network OS? This doesn't make sense to me. (and no, I do not want to return to Windows, I just want a Windows-like Internet connection ;))[/QUOTE]

I don't know anything about your network setup or problems. It's best if you create a sperate thread for this. PM me the url and I will try to help you if I have time.

---

### Post by Trojan1313 on 2005-08-25
[QUOTE=ubuntu_demon]uploading a lot of stuff from one pc will always have some effect on quality of the internet connection

Do you have a ubuntu pc configured as router ?[/QUOTE]
No, I have a DLink 604. And no PC with dual network ports to be connected before the router.


[QUOTE=ubuntu_demon]I don't know anything about your network setup or problems. It's best if you create a sperate thread for this. PM me the url and I will try to help you if I have time.[/QUOTE]
What URL?

---

### Post by ubuntu_demon on 2005-08-26
[QUOTE=Trojan1313]No, I have a DLink 604. And no PC with dual network ports to be connected before the router.
[/QUOTE]

wondershaper won't do much good for you then

(connecting a pc before router doesn't make much sense by the way)

[QUOTE=Trojan1313]
What URL?[/QUOTE]

the url of your new thread about your problems

---

### Post by Trojan1313 on 2005-08-27
[QUOTE=ubuntu_demon]wondershaper won't do much good for you then

(connecting a pc before router doesn't make much sense by the way)



the url of your new thread about your problems[/QUOTE]
 [http://ubuntuforums.org/showthread.php?t=55192](http://ubuntuforums.org/showthread.php?t=55192)

Didn't someone just say that I could shape a PC connected before the router to get the same effect as shaping my router?

---

### Post by rastilin on 2005-09-09
Yes they did and you can. I think the subtle point being missed here is that on ADSL the router is the modem.

I'm running on adsl. My computer is connected to the router which is connected to the internet, I use wondershaper and everything works perfectly. Doing the shaping on the P2P program like aMule or Bittorrent is not the same because (to my understanding) they lack the same control over packets that wondershaper has. 

One thing I've noticed is that wondershaper's download shaping is unreliable and tends to drop connections randomly. I always set the downspeed to double my actual downspeed to fix this.

---

### Post by rastilin on 2005-09-09
Sorry for the double-post, would you believe lag caused it?

---

### Post by ubuntu_demon on 2005-09-10
[QUOTE=Trojan1313][http://ubuntuforums.org/showthread.php?t=55192](http://ubuntuforums.org/showthread.php?t=55192)

Didn't someone just say that I could shape a PC connected before the router to get the same effect as shaping my router?[/QUOTE]
 If you want the best control over your packets it's best to use a pc configured as a router connected to a hub(which is connected to the rest of the network). And running shaping stuff on your pc configured as router. Wondershaper doesn't give you very much control but it's easy.

If people have a hardware router just don't do shaping : it isn't worh it.If you want more control consider the previous option. (of course you can control the speeds of most p2p clients but that's not the kind of shaping I'm talking about)

---

### Post by fekimoki on 2005-11-21
can wondershaper limit connection based on IP ? (not eth)
thx

---

### Post by ubuntu_demon on 2005-11-21
[QUOTE=fekimoki]can wondershaper limit connection based on IP ? (not eth)
thx[/QUOTE]
no. wondershaper is quite basic.

People can write their own iptables script. I think part of the reason there is no easy advanced traffic shaper is because it may be almost as hard/simple for the user as writing it yourself.

---

### Post by mm004 on 2006-02-04
What would be a good limit for a 6000/600 ADSL-Line?

Maybe 5000/500 or am I totally wrong?

---

### Post by Lukian on 2006-06-12
I'm on 512/128 ADSL in Australia. 

Using: "wondershaper eth0 430 108"

Results for pinging my first hop (not adsl modem/router) for downloading:
My best case ping time dropped from 866 ms to 31 ms, a 96% improvement.
My average ping time dropped from 1100 ms to 96 ms, a 91% improvement.
My worst case ping time dropped from 1144 ms to 200 ms an 83% improvement.

Even more substantial savings are seen on the upload side.


Using 400/100 for simultaneous upload and download results in:
10.8 kB/s average upload, ~48kB/s max download (43kB/s average).

Which, using the same format above (and an extended test):

My best case ping time dropped from 1922 ms to 20 ms, a 99% improvement.
My average ping time dropped from 1984 ms to 154 ms, a 92% improvement.
My worst case ping time dropped from 2145 ms to 441 ms an 80% improvement.


Here is the process I went through:

Step 1
= 192.168.0.254 (203.24.101.21)

Step 2
Downloads
= rtt min/avg/max/mdev = 866.612/1100.784/1144.405/57.681 ms, pipe 2
Uploads
= rtt min/avg/max/mdev = 1765.802/1983.802/2144.569/83.101 ms, pipe 3

Step 3
= wondershaper eth0 430 108

Step 4

Downloads
- full
= rtt min/avg/max/mdev = 866.612/1100.784/1144.405/57.681 ms, pipe 2
- 580
= rtt min/avg/max/mdev = 95.229/944.739/1222.928/299.123 ms, pipe 2
- 447
= rtt min/avg/max/mdev = 55.382/749.904/1154.461/369.719 ms, pipe 2
- 300
= rtt min/avg/max/mdev = 17.392/59.722/122.071/35.790 ms
- 400
= rtt min/avg/max/mdev = 30.289/90.659/646.169/119.851 ms
- 420
= rtt min/avg/max/mdev = 29.728/123.466/906.391/194.766 ms
- 425
= rtt min/avg/max/mdev = 18.290/154.646/730.922/175.216 ms
- 430
= rtt min/avg/max/mdev = 19.113/156.270/734.939/178.813 ms
= rtt min/avg/max/mdev = 31.893/96.125/200.525/38.941 ms

Uploads
- full
= rtt min/avg/max/mdev = 1765.802/1983.802/2144.569/83.101 ms, pipe 3
- 128 516096 bytes sent in 34.92 secs (14.4 kB/s)
= rtt min/avg/max/mdev = 44.629/1270.464/2089.048/675.210 ms, pipe 3
- 108 401408 bytes sent in 28.56 secs (13.7 kB/s)
= rtt min/avg/max/mdev = 45.745/122.369/209.850/45.753 ms
- 78
= rtt min/avg/max/mdev = 19.710/124.655/207.612/65.378 ms
- 64 188416 bytes sent in 25.43 secs (7.2 kB/s)
= rtt min/avg/max/mdev = 18.091/42.916/189.956/43.567 ms

Both (Ouch!)
- full 434176 bytes sent in 29.35 secs (14.4 kB/s), Recv: 28K/s
= rtt min/avg/max/mdev = 1992.774/2201.422/2325.480/87.792 ms, pipe 3

- 300/64 196608 bytes sent in 24.08 secs (8.0 kB/s), Recv: 23K/s
= rtt min/avg/max/mdev = 20.532/91.630/152.785/41.263 ms
- 430/64
= rtt min/avg/max/mdev = 19.782/195.306/304.776/78.140 ms

- 400/100 425984 bytes sent in 39.35 secs (10.9 kB/s), Recv: 43K/s
= rtt min/avg/max/mdev = 23.285/199.640/289.105/71.486 ms (wow!)
= rtt min/avg/max/mdev = 35.679/170.856/279.028/60.425 ms (retest)
= rtt min/avg/max/mdev = 33.936/164.258/271.638/76.092 ms (final test)

- 400/108 401408 bytes sent in 32.29 secs (12.1 kB/s), Recv: 46K/s
= rtt min/avg/max/mdev = 206.607/377.948/731.014/125.181 ms (too high)

- 380/100 352256 bytes sent in 31.14 secs (11.0 kB/s), Recv: 38K/s
= rtt min/avg/max/mdev = 22.854/145.867/270.938/60.671 ms ()

Estimated optimal value for download below or equal to 400?
Estimated optimal value for upload lies between 100-108.

rtt min/avg/max/mdev = 23.285/199.640/289.105/71.486 ms
rtt min/avg/max/mdev = 35.679/170.856/279.028/60.425 ms
rtt min/avg/max/mdev = 33.936/164.258/271.638/76.092 ms

Extended test (10MB download with upload running):
rtt min/avg/max/mdev = 20.438/153.810/440.522/78.096 ms


During the process I also determined that it's best to wait before pinging, as wondershaper takes a second or two to initialise and shape the streams.

I do not guarantee the accuracy of the data here, or any results you may experience while using this information.

---

### Post by ShirishAg75 on 2008-03-29
hi all, 
Sorry for not reading the in-between 10 odd pages & also sorry for bringing an old-old topic to life. But why is wondershaper not in Ubuntu anymore ? Specifically on Hardy ? :(

---

### Post by onlainari on 2008-04-19
Hi.

I have only 2 lines in my /etc/network/interfaces

> 
auto lo
iface lo inet loopback


The how-to tells me to add 2 lines in the file after the interface that uses my internet connection. In my case "eth0". At least iIf I just add the lines under those 2 lines, it seems to not work.

edit:

Since no one has posted anything since my post, i'll just edit this.

I found out that it is all ok to have only those 2 lines in the /etc/network/interfaces (to be connected to internet) it just means that i was using the internet thru my net applet nm-applet, and that it was using "auto roaming" option. Now, when i wanted to get my eth0 recognized, i had to tweak options in the nm-applet. First i took the auto roaming option away, and then i decided to use static ip:s (since i could choose that or dhcp) I set my ip settings in nm-applet and had it offline and back online. After that /etc/network/interfaces had an entry for eth0. Then I tried sudo ifdown eth0 , but I was still given "interface eth0 not configured". So i rebooted, and after the boot, i could ifdown and ifup the eth0. After that I proceeded wtih the edits in /etc/network/interfaces described in the first post of this thread and wondershaper seems to be working.

---

### Post by onlainari on 2008-04-20
bump for this new question.

Using wondershaper:

I am trying to limit my UL rate with wondershaper, because I have a UL limit of 800MB/day (or face 7days internet ban) I also like to use a program called qsopcast, which is a p2p tv. It is possible that 800MB exceeds in less than 4 hours with that program. 

1.  I set DL rate 9999999 and UL rate 38 --> download speed (in a test) 200KB/s ; 

2. I dont use wondershaper --->  -> DL rate 2.5MB/s ( in a same test)

Using wondershaper has some kind of effect on my download even when I set the limit very high. Because of this effect the qsopcast transmission is not working properly, and is lagging. I can hardly get peers(?) It's not that I would care to have 2.5MB/s. Sopcast requires like 40kb/s download to have it working, but with wondershaper it seems to find it hard.

In windows, it is easy to set a 40kb/s limit with netlimiter, and it doesnt have an effect on the download rate or on the availability-on-getting-peers-from-sopcast.

I figured there is another simple program to use called Trickle. If I were to use that one, I will be out of convenience. First of all trickle jams qsopcast, because inside of qsopcast there are other commands executed for the actual transfer.
I would have to try something like: 
trickle -s -d 99999 -u 38 sp-sc sop://broker6.sopcast.com:3912/6543 3912 8908 
...and then open up a vlc player separately with a proper port etc.
....and would that jam my connectivity(download) rate just like wondershaper did ?

---

### Post by karq on 2008-05-03
Maybe someone can help me, I just dont get it how to conf wondershaper?

---

### Post by agent8131 on 2008-05-03
It should be noted that you do not want to use wondershaper if you have a home LAN.  Wondershaper does not differentiate between LAN and WAN traffic and therefore whatever rate you limit your interface to will also be the maximum LAN speed, which is almost certainly not what anyone wants.

---

### Post by karq on 2008-05-04
I have 2 pc in my home network. And my connection speed is 1mb/s so I want to share it so that I have 512 and it dosent go over it and the other pc has 512.

---

### Post by kripz on 2008-05-04
Hello, is wondershaper designed to be used on clients or more the router computer.

This is my current network:

Internet > Modem/Router > Switch > Computers.

If i install wonder shaper on my computer will it:

a. Affect LAN traffic?
b. Work at all in my setup?

---

### Post by Jean-Marc Liotier on 2008-06-02
I thought some people here might be interested in a modified version of the original Wondershaper script that I made to achieve better VOIP performance on my loaded ADSL link. It works for me so maybe an it is a drop-in replacement for the Debian/Ubuntu script.

You'll find [the code here]("http://www.ruwenzori.net/code/wondershaper/wondershaper.jml") and [some explanations here]("http://serendipity.ruwenzori.net/index.php/2008/06/01/modified-wondershaper-for-better-voip-qos").

---

### Post by BUGabundo on 2008-06-11
> **onlainari said:**
> 
Using wondershaper has some kind of effect on my download even when I set the limit very high.


any change to the upload limit will also affect donwload, because of the amount of packets that need to be sent/piggyback

---

### Post by BUGabundo on 2008-06-11
> **agent8131 said:**
> It should be noted that you do not want to use wondershaper if you have a home LAN.  Wondershaper does not differentiate between LAN and WAN traffic and therefore whatever rate you limit your interface to will also be the maximum LAN speed, which is almost certainly not what anyone wants.

I needed a way to limit my laptop, when connected to our company router, so I wouldnt mess our VOIP QoS.
well i inicially found trickle/trickled but that didnt work for me, then i started using wondershaper.
its a great app, but i still need to differentiate between LAN and WAN. any tips?

---

### Post by Sam Lars on 2008-07-04
I tried running it and got this:
```
:~$ sudo wondershaper wlan0 720 120
What is "flowid"?
Illegal "police"
:~$
```

---

### Post by BUGabundo on 2008-07-05
> **Sam Lars said:**
> I tried running it and got this:
```
:~$ sudo wondershaper wlan0 720 120
What is "flowid"?
Illegal "police"
:~$
```

this have been fixed on the next version, on Intrepid, and I think there is a backport version of it on proposed.

---

### Post by Sam Lars on 2008-07-05
Thanks for the info, I've got proposed enabled but it's still installed from universe.

---

### Post by Sam Lars on 2008-07-12
I think it's been backported now, working on 64-bit Hardy. :)
I'm not seeing a huge improvement... I don't want to limit uploads too much... It seems that I have to pull the limit too far down.

---

### Post by BUGabundo on 2008-07-12
> **Sam Lars said:**
> I don't want to limit uploads too much... It seems that I have to pull the limit too far down.

it works exactly as expected to me.
what command line are you using_

at work, i use:
sudo wondershapper 8000 50 eth0

and i get an upload limit of 8KiBytes/sec, as expected.

---

### Post by Sam Lars on 2008-07-12
```
sudo wondershaper wlan0 720 120
```
I can usually get an upload of 10 kB/s or more, but I have to limit it to 5 kB/s or less to get any responsiveness.  I could get that responsiveness by just limiting the upload to 5 kB/s without this wondershaper.

---

### Post by Runaway1956 on 2008-09-29
> **agent8131 said:**
> It should be noted that you do not want to use wondershaper if you have a home LAN.  Wondershaper does not differentiate between LAN and WAN traffic and therefore whatever rate you limit your interface to will also be the maximum LAN speed, which is almost certainly not what anyone wants.

I have a LAN, which is unaffected by Wondershaper.  The internet is on eth0 and the LAN is on eth1

I issue the command wondershaper eth0 285 150 (as sudo)

All traffic destined for the internet, whether it originates from the gateway machine, or from the LAN, is throttled, so that no one takes more than a ¨fair share¨ of the bandwidth.  A humongous download started from the son´s room doesn´t put an end to my online game, where lag means death.

---

### Post by agent8131 on 2008-09-29
> **Runaway1956 said:**
> I have a LAN, which is unaffected by Wondershaper.  The internet is on eth0 and the LAN is on eth1

I issue the command wondershaper eth0 285 150 (as sudo)

All traffic destined for the internet, whether it originates from the gateway machine, or from the LAN, is throttled, so that no one takes more than a ¨fair share¨ of the bandwidth.  A humongous download started from the son´s room doesn´t put an end to my online game, where lag means death.

I apologize for not being clear.  You can run wondershaper on a gateway machine as long as it is the only machine connected to the WAN.  You do not want to run wondershaper on the machines on the LAN, including laptops, unless either you can differentiate LAN and WAN traffic or you have no need to connect to other machines on the LAN.

---

### Post by Runaway1956 on 2008-11-21
Sorry, wrong post

---

### Post by rantarou on 2009-04-19
what if I set a pppoe on the ubuntu desktop..? should i set the wondershaper on eth0 or ppp0 ...?

thanks before

---

### Post by danbuk on 2009-04-23
hi ubuntu demon...
i wanna ask bout using wondershaper...
firstly.
when i was install my wonder shaper there is no problem,but when i want to configure 'sudo wondershaper eth0 downspeed upseed' (my networkcard eth0),,there is another script appears like this :
illegal "rate"
illegal "rate"
RTNETLINK answer : invalid argument
RTNETLINK answer : invalid argument
RTNETLINK answer : invalid argument
RTNETLINK answer : invalid argument
illegal "rate"
illegal "police"

why was like that appears ubuntu demon ?
help please..
thx a lot..
blessed all..

---

### Post by Pithikos on 2011-01-03
For this to work your computer must be a router for other computers right? Else I don't see how this can have an effect as it assigns bandwidths to netword cards. Is that right?

---

### Post by emptythevoid on 2011-03-03
I've been reading Wondershaper's documentation, and there's something that's not clear to me.  Wondershaper puts priority on interactive traffic and slows down bulk traffic.  But when you specify the upload/download speeds, does that cap ALL kinds of traffic to the specified upload/download speeds, or just bulk traffic?  I'm wanting to use an Ubuntu box running as a bridge on one segment of our network, and use Wondershaper as a "valve" to slow that segment down without worrying about IPs or ports.  Here's a schematic of the network

[http://imgur.com/1R0Li](http://imgur.com/1R0Li)

I want to be able to use the Bridge (Wondershaper) to throttle down ALL traffic from segment 2, regardless of the type of traffic, and leave segment 1 alone, so it gets all the traffic that's left.  Segment 1 is plugged into one port on the router, and the Bridge/Segment 2 is plugged into another.

Does this look like it would work?  I know that this wasn't how Wondershaper was intended to be used.  I can run it and test segment 2 with speedtest.net and it looks like traffic is being throttled correctly, but I can't tell if *all* traffic is throttled.   I don't want *any* traffic to escape the upload/download speeds I specified.

---

### Post by The Midnighter on 2012-04-25
Did anyone experience severe packet loss after using Wondershaper? (sudo wondershaper eth0 1000 1000)

---

