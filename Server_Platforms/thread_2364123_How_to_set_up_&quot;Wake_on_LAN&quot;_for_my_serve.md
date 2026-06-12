---
title: "How to set up &quot;Wake on LAN&quot; for my server computer running Ubuntu Desktop 16.04 LTS"
date: 2017-06-19
forum: Server Platforms
---

### Post by agarwaldvk on 2017-06-19
Hi Everyone


I have my home server now running for a little while (with the help of a lot of help from people on this forum, thanks for that) now. This computer is accessed from a number of other devices including mobile phones, tablet, and other laptops and PC's running Windows 64 bit OS. I was wondering if I might be able to setup "Wake On LAN" for this server computer as it becomes quite inconvenient to go downstairs every time to turn it on if its off - this is home environment and it hasn't got not server grade components in it and hence doesn't run 24/7 every day. It is turned off when no one is using it.

Can this be realized with relative ease or this is something that falls in the realm of the "geeks" and I shouldn't attempt it?

I am fairly new to Ubuntu and my knowledge on Ubuntu type coding is limited to what I need to run and maintain this server adequately - nothing particularly great. Hence, I might need a little more than high level assistance for a solution that you might propose.


Best regards


Deepak Agarwal

---

### Post by TheFu on 2017-06-19
[https://help.ubuntu.com/community/WakeOnLan](https://help.ubuntu.com/community/WakeOnLan) might be helpful.

---

### Post by agarwaldvk on 2017-06-19
Hi TheFu


Thanks for your response.

I did have a look at this one before I posted.

Just wondering if there is something a trifle  more basic that this that I start with.


Best regards


Deepak

---

### Post by sp40140 on 2017-06-19
You first need to make sure if your mobo supports WOL or not. If it does, check bios to ensure that feature is enabled.
That's all I had to do. It's connected to network over powerline adapter. I do run an old Dell Precision desktop with C2D cpu though. So, it being enterprise workstation supported WOL.
I run Full Ubuntu Unity as well as xfce desktop on it. 
Use "fing" app on android to send WOL packet to it. Never had problem with it.
I suggest you first try to do this without messing with any settings in the os (like I did). There is a good chance that you will get lucky.

---

### Post by TheFu on 2017-06-19
Checklist:
* WoL enabled in BIOS
* WoL settings installed on server  (ethtool/interface file changes)
* WoL client installed on any clients (only works on the LAN, not over the internet)
* WoL clients configured with the network card MAC

Happiness.
Pretty simple.

I use a perl script for my WoL client.
```
$ wake.pl 00:2A:5B:3C:2D:37
```

---

### Post by audun-m on 2017-06-19
Wake on lan is actually really easy, and is almost always enabled in the BIOS of the machine you want to wake, especially if the network card is integrated.
The hard part is going into the BIOS of the machine you want to wake, look around in the menus for something that sounds like WOL or Wake on LAN and enable it.

It can help to go google for the motherboard/computer manual and read that on how to enable Wake on lan.



The easy part is then finding a wake-on-lan client which works for you, input the mac address and watch the computer turn on. You may have to try a few before you find one which works. Many good suggestions in this thread.

Most machines with integrated network supports wake-on-lan nowadays.

---

### Post by agarwaldvk on 2017-06-21
Hi Everyone


I think I have quite far in that I have enable 'Wake on PCIE' in BIOS, installed 'ethtoo' and this is the output of the ifconfig -a command :-

```


agarwaldvk@MyHomeServer:~$ sudo ifconfig -a
[sudo] password for agarwaldvk:
enp3s0    Link encap:Ethernet  HWaddr d8:50:e6:4e:71:42 
          inet addr:192.168.1.15  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::d242:4f67:5f57:a6b4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:26857 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22709 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4051400 (4.0 MB)  TX bytes:7882550 (7.8 MB)

lo        Link encap:Local Loopback 
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:61641 errors:0 dropped:0 overruns:0 frame:0
          TX packets:61641 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1
          RX bytes:77354411 (77.3 MB)  TX bytes:77354411 (77.3 MB)


```

Does that mean that my mac address is the one starting with 'd8...'?

Now how do I test 'waking on lan' my Ubuntu server from one of my Windows PC either through wired connection or wifi over my home network - I don't know Perl. Is there a script or a command that I can write is VB Script etc.?

There is this software that I found called 'WakeMeOnLan' - will that do it - this apparently only works with wired connections, not wireless over the network?


Best regards


Deepak

---

### Post by cariboo on 2017-06-21
WOL should work for either connection wifi or wired. You don't need to know to any programming.

I don't use Windows, but this is a screenshot of the app I use:

[[img]https://s7.postimg.org/5scsoamzr/Screenshot_2017-06-21_13-59-34.png[/img]](https://postimg.org/image/5scsoamzr/)

---

### Post by agarwaldvk on 2017-06-21
Hi Cariboo


That is OK. I want to do just that. You use the application 'gWakeOnLan' from another Ubuntu or Linux based computer, right? So, you must be logged on to a Ubuntu or Linux based computer and are then using this software to send out this magic packet to wake another computer on the network, yeah?

And that's exactly what I am asking - what application can I use to wake this Ubuntu computer (which acts as my server computer on my home network) from another windows PC. The sever computer is the only Ubuntu computer I have at home. All the other conputers are Windows based. So how do I send the magic packet to my Ubuntu Server to 'wake it up on LAN' - it obviously is asleep at the moment.

I now know that you don't use Windows but do you know what application can I  use from a windows PC to send this magic packet or wol command to the Ubuntu computer?


Best regards


Deepak

---

### Post by TheFu on 2017-06-21
You can use any WoL client that you want.  For Ubuntu, search in the software center. For android, search the play store.  For Windows, search however you would normally search.

The protocol is standard, so any application (or tiny script) can do it. You don't need any specific application, any WoL will work.  You could have tried 20 already and had this working.

---

### Post by agarwaldvk on 2017-06-22
Hi Everyone


I did try to wake by Ubuntu server using 'WakeOnLANx2' wol client from my Windows 10 PC but it doesn't seem to wake up.

I found the MAC address for my server computer from the output of 'ifconfig -a' command - the one with 6 sets of 2 character alpha numeric entries.


Any suggestions to help me to get it wake up using wol?


Best regards


Deepak

---

### Post by cariboo on 2017-06-23
Use ethtool on your server to check if WOL is set on the ethernet adapter:

```
sudo ethtool <nic>
```

where <nic> = your ethernet device, it should show an output something like this:

```
sudo ethtool enp2s0
[sudo] password for cariboo: 
Settings for enp2s0:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Supported pause frame use: No
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Advertised pause frame use: Symmetric Receive-only
	Advertised auto-negotiation: Yes
	Link partner advertised link modes:  10baseT/Half 10baseT/Full 
	                                     100baseT/Half 100baseT/Full 
	Link partner advertised pause frame use: Symmetric Receive-only
	Link partner advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pumbg
	Wake-on: g
	Current message level: 0x00000033 (51)
			       drv probe ifdown ifup
	Link detected: yes
```

Note where it says:

```
Wake-on: g
```

if you don't see the **g** then follow this wiki page [here]("https://help.ubuntu.com/community/WakeOnLan")

---

### Post by agarwaldvk on 2017-06-23
Hi Cariboo


I did check the output from the code "sudo ethtool enp3s0" and it did show "wake-on : g"

But I am still not able to wake my computer. I was using Solar Wind WakeOnLAN software to do so but it doesn't seem to wake up.

Do I need to change any settings on any system file or something?

I will include the output fro the above command once I turn it on manually and run the command on it.

P.S

Here is the code and the output from it:-
```

agarwaldvk@MyHomeServer:~$ sudo ethtool enp3s0
[sudo] password for agarwaldvk: 
Settings for enp3s0:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Supported pause frame use: No
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised pause frame use: Symmetric Receive-only
	Advertised auto-negotiation: Yes
	Link partner advertised link modes:  10baseT/Half 10baseT/Full 
	                                     100baseT/Half 100baseT/Full 
	Link partner advertised pause frame use: Symmetric
	Link partner advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pumbg
	Wake-on: g
	Current message level: 0x00000033 (51)
			       drv probe ifdown ifup
	Link detected: yes
agarwaldvk@MyHomeServer:~$ 


```


Also, I read somewhere that someone installed "tlp" on his 17.04 LTS installation and it worked after that. Do I need to install "tlp"?



Best regards


Deepak

---

### Post by CatKiller on 2017-06-23
For Wake-on-LAN you send a magic packet containing the MAC address of the NIC you want to wake up (in your case **d8:50:e6:4e:71:42**) to the broadcast address of the network it's on (in your case **192.168.1.255**). To do this I use either **wol** from a Linux machine or **Wake on Lan** on my Android phone, depending on where I am.

In a previous version of Ubuntu, I also needed to stop the NIC being turned off when the computer turned off. I don't know if that is still necessary. It was a long time ago, so I can't remember which file it was that I changed to do that, but I'll see if I can find out.

EDIT: I believe that the change I made was to the **halt** script. I believe I changed **NETDOWN=yes** to **NETDOWN=no** in **/etc/init.d/halt**.

---

### Post by TheFu on 2017-06-23
There is a moral to this thread.
Sometimes things are really easy.  Sometimes, usually with less-friendly-hardware, things are harder.  For many people, WoL "just works" by setting up the remote system and installing a client. Nothing more is needed.  Then there are all the other situations which a full how-to attempts to cover.  Of course, there are exceptions to everything and sometimes the last 1% have a hard time or skipped an earlier, required, step OR their hardware setup just isn't capable of supporting WoL.  Everything in the process has to be setup AND it has to work correctly.

* Does the OS work with suspend perfectly?
* BIOS set for WoL?
* OS set for WoL?
* Network card configured for WoL?
* Try a few different WoL clients.  Sometimes sending 3 packets is needed over a few seconds.

If all these things are done and it isn't working, start checking the log files for issues and start over. Sleeping on the issue could refresh some eyes when looking at the settings the next day too.

Then there are some systems on which WoL never works. Nobody figures out why.

---

### Post by agarwaldvk on 2017-06-24
Hi CatKiller


I did change the NETDOWN=no in both the files :-

/etc/init.d/halt and
/etc/default/halt


but still nothing

Do I need to install tlp?


Best regards


Deepak

---

### Post by agarwaldvk on 2017-06-24
Hi Everyone


I got it to work. Thanks for all the help provided. Please accept my most sincere apologies for giving the wrong information to you all in that the MAC address that I was using was incorrect - 2 of the characters got swapped.

However, one other issue has cropped up - when I wake it up on LAN then I am not able to power it off using the Webmin interface that I normally use to turn it off (power it off) on my mobile. Any suggestions on what might be causing this. Is my setting on the two 'halt' files of 'NETDOWN=no' could be causing it?


Best regards


Deepak

---

