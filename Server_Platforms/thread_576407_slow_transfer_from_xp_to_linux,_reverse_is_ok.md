---
title: "slow transfer from xp to linux, reverse is ok"
date: 2007-10-15
forum: Server Platforms
---

### Post by sartic on 2007-10-15
...talking about samba transfer. It is lowend pc, but everything works in windows when i install xp on separate disk. Linux is Feisty. What can i try? Lan is rtl8139.

---

### Post by sartic on 2007-10-15
addon... i have many dropped and rx errors when i analyze this machine. disk width xp works superb.

---

### Post by koshari on 2007-10-15
IMHO i believe samba is pretty slow sometimes for reasons i have not been able to discover.

one of our computers on the network with a samba share is painfully slow to serve files, however the same files served via apache fly across at full Ethernet speed.

go figure, 

so we just installed LAMP and serve the files through a browser VERY fast :-)

---

### Post by netlogic on 2007-10-15
You should use CIFS and enable wins.  Netbios naming system can get complicated, please spend time reading the Samba doc. Most people don't have issues even with 500 machines.

---

### Post by HermanAB on 2007-10-15
If you have *any* network errors, then you should replace the network adaptor.  They don't last forever, because they are attached to a long wire, they are subject to induced glitches.

Secondly, go to the Samba website and read the Official Howto.  There are lots of examples in there, one of which will be exactly your situation.

Cheers,

Herman

---

### Post by koshari on 2007-10-15
> If you have *any* network errors, then you should replace the network adaptor. They don't last forever, because they are attached to a long wire, they are subject to induced glitches.

if the harware layer is working fine using a different application layer its not the problem, 

and while i grant there may be times where NIC cards will die IMHO its very rare.

---

### Post by netlogic on 2007-10-15
I will be more clear with the questions. I guess I wasn't very clear. Are you using Wins? Did you set the Linux box as the highest level browser master? Are XP machines running in H-node? Are they using the WINS first, then broadcasts? Are you confident that you don't have DNS and WINS naming conflicts? Do you have a basic network diagram? How many nodes? You said you are dual booting. Are you sure both have the &#8220;same&#8221; correct valid Netbios name? Is your security policy set to the deafult on XP? Are you using NTLM?  Which version? What version is your samba? What's the service pack for XP? Have you ran the sniffer? What is constantly repeating that is slowing you down? Have you checked for errors in /var/log/samba/  Can you post your smb.conf file without the hash comments? Can you post errors that are relevant?

---

### Post by netlogic on 2007-10-16
Also, is this on-board nic? Does it utilizes your CPU to transfer? If you ran the sniffer, do you see packet drops or name resolution issues?

[http://www.dd.iij4u.or.jp/~okuyamak/Documents/tuning.english.html](http://www.dd.iij4u.or.jp/~okuyamak/Documents/tuning.english.html)

How to debug Samba
[http://searchenterpriselinux.techtarget.com/tip/0,289483,sid39_gci1270003,00.html](http://searchenterpriselinux.techtarget.com/tip/0,289483,sid39_gci1270003,00.html)

Also, list all your XP services to us...
Make sure Webclient service is disabled. It can slow you down.

---

### Post by sartic on 2007-10-16
> **netlogic said:**
> You should use CIFS and enable wins.  Netbios naming system can get complicated, please spend time reading the Samba doc. Most people don't have issues even with 500 machines.

Done that. I am old bbser. rtfml is done. Users decide what they want not me... they want samba.

---

### Post by sartic on 2007-10-16
> **netlogic said:**
> You should use CIFS and enable wins.  Netbios naming system can get complicated, please spend time reading the Samba doc. Most people don't have issues even with 500 machines.

there is no choice here. only lan pci rtl8139. today i will replace for same one and try again.

---

### Post by sartic on 2007-10-16
> **netlogic said:**
> I will be more clear with the questions. I guess I wasn't very clear. Are you using Wins? Did you set the Linux box as the highest level browser master? Are XP machines running in H-node? Are they using the WINS first, then broadcasts? Are you confident that you don't have DNS and WINS naming conflicts? Do you have a basic network diagram? How many nodes? You said you are dual booting. Are you sure both have the “same” correct valid Netbios name? Is your security policy set to the deafult on XP? Are you using NTLM?  Which version? What version is your samba? What's the service pack for XP? Have you ran the sniffer? What is constantly repeating that is slowing you down? Have you checked for errors in /var/log/samba/  Can you post your smb.conf file without the hash comments? Can you post errors that are relevant?

didn't touch anything about wins. have no wins server or wins clients. i will have some time today and i will try another lan card and play width some wins... but exactly the same configuration of linux - xp works 4 me in more than 10 situations but all them r medim end pc. this machine is width via c3 800 cpu (something like pentium 233mmx). Linux is Feisty, clients r xp sp2. I

---

### Post by sartic on 2007-10-16
> **koshari said:**
> if the harware layer is working fine using a different application layer its not the problem, 

and while i grant there may be times where NIC cards will die IMHO its very rare.

This card works perfectly on xp on same machine, but i will change it 4 the same in store today...

---

### Post by sartic on 2007-10-16
> **netlogic said:**
> Also, is this on-board nic? Does it utilizes your CPU to transfer? If you ran the sniffer, do you see packet drops or name resolution issues?

[http://www.dd.iij4u.or.jp/~okuyamak/Documents/tuning.english.html](http://www.dd.iij4u.or.jp/~okuyamak/Documents/tuning.english.html)

How to debug Samba
[http://searchenterpriselinux.techtarget.com/tip/0,289483,sid39_gci1270003,00.html](http://searchenterpriselinux.techtarget.com/tip/0,289483,sid39_gci1270003,00.html)

Also, list all your XP services to us...
Make sure Webclient service is disabled. It can slow you down.

Nope it isn't onboard. Onboard is off (partly because Feisty doesn't see iit) It is low end pc. Cpu is Via c3 800 and it has 512mb so swaping isn't problem either. Will try that url... thx.

---

### Post by tombstoneind on 2007-10-16
XP can slow you down, so can Vista. Outbound information on some XP/Vista machine get "jammed". 

I have two XP machines, and they wont talk to each other sometimes. Turning Off your Realtime-Antivirus scans, might help too... most of them lock down your machine, so its only ports are what the AVP (anti virus program) says is allowed.

Windows has this thing about liscences too. If your network is Microsoft, and you are using Ubuntu, its going to ask about liscences. 
On the other foot, if you decide to use a Non-MS Network (Server), and your using XP or Vista, it works better... mostly.

Afterthought--
Have you looked at flow control of routers/switches in that network, they can gum up the works too.

---

### Post by tansa on 2007-10-17
hi i have the same problem with xp and samba 
the frist share it is ok but when the second pc open the same share it go 
too slow thanks for help

---

### Post by tansa on 2007-10-17
sorry if i did not understand  but my problem is if i 'm on my xp machine and i open the share on the Linux machine it go too slow
10x for help

---

### Post by sartic on 2007-10-17
> **tansa said:**
> sorry if i did not understand  but my problem is if i 'm on my xp machine and i open the share on the Linux machine it go too slow
10x for help

Did u try auto negotian for lan speed on xp workstation?

I didn't solve my problem width new lan card. The best transfer i get when i use wii-tool to set speed to 10 FD. I will try to find some technical data about realtek 8139 under linux today..

---

### Post by tansa on 2007-10-17
hi man the problem you think is from the network card? 
it is my first day on this forum thank for helping me

---

### Post by sartic on 2007-10-17
> **tansa said:**
> hi man the problem you think is from the network card? 
it is my first day on this forum thank for helping me

Nope, i had many same problems when autonegation wasn't set to auto on network properties of your lan under xp. Check it.

---

### Post by tansa on 2007-10-18
ok 10x i will try it

---

### Post by sartic on 2007-10-28
Anyone? Still didn't solved this. Maybe to recompile kernal width some better driver for realtek lan?

---

### Post by Mcavity on 2007-10-28
I seem to be having the same problem.  
using gutsy gibbon I can transfer files to the XP fileseferver over samba no problem.
i.e. 175 meg file - 40 seconds..
but if I try and pull the file from the server it takes much longer
like 3 min.  [previously it was running at about 20 min to copy the file]
any ideas?

While the Nic is working I'm not sure I'm getting full support under the 2.6 kernel. The Nic has a makefile for support under 2.4 but nothing for 2.6
this is a Trendet TEG-PCITXR H/W2.1R


mike@mike-ubuntu:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:01:06.0
       logical name: eth0
       version: 10
       serial: 00:18:e7:07:b5:3e
       size: 1GB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.0.102 latency=64 link=yes maxlatency=64 mingnt=32 module=r8169 multicast=yes port=twisted pair speed=1G

---

### Post by sartic on 2007-10-29
Owner decided 2 buy xp pro. MS wins this time...

---

### Post by netlogic on 2007-10-29
Imagine, paid $120 for an OS that will last for 2.3 yrs compared to $5 nic. I guess 2.3 years later, $600 pc can be easily justifiable.

---

### Post by Mcavity on 2007-10-30
[SIZE="2"]well.. more along the lines of spending money for an OS hes pretty sure he can get the support level he wants. Linux is making huge stride.. but still lags behind in a few areas. device support is one of tho[/SIZE]se.

---

### Post by netlogic on 2007-10-30
> **Mcavity said:**
> [SIZE="2"]well.. more along the lines of spending money for an OS hes pretty sure he can get the support level he wants. Linux is making huge stride.. but still lags behind in a few areas. device support is one of tho[/SIZE]se.

Only very few vendors develop Linux drivers. Most drivers are made by the community. If you  assume MS actually made all the drivers for Windows, it isn't true. They certify the drivers. It is a huge difference.

---

### Post by netlogic on 2007-10-30
Also, companies over 100 people have a hardware standardization in place, so this isn't an issue in a corporate environment. In the home environment, it can be an issue. I just don't understand how a company is not willing to pay $5 for a nic. It  just sounds really odd.

---

### Post by sartic on 2007-10-31
> **netlogic said:**
> Also, companies over 100 people have a hardware standardization in place, so this isn't an issue in a corporate environment. In the home environment, it can be an issue. I just don't understand how a company is not willing to pay $5 for a nic. It  just sounds really odd.

I tried all "5$" lans that i can buy in my  country. All r same realtek chipset. They all do same in feisty on this. Xp pro works perfectly width all i tried pci lans, feisty failed width all the same way. I do not blame owner. I didn't count hours i spent trying 2 push linux 1 more time. Didn't ask cent because i still believe in ubuntu, but problems width samba transfers can not solved width "it works on my machine i do not know why yours ..." .. i tried all. The best i did is transfer equal 2 10mbit lan .. who needs that?!

---

### Post by MJN on 2007-10-31
Maybe try the $10 cards? ;)
 
Seriously, it's a shame you didn't manage to track down the cause of the problem and it's a shame noone was able to come up with anything concrete to progress your issue. Sometimes it's like that though and given there wasn't much to go on (not your fault by the way, it's often better/easier when it doesn't work at all as opposed to just badly!) there probably wasn't much hope from the outset unless someone else had your card/configuration (even then the 'well mine works' response is not much help!).
 
Remember, MS may have won this battle but there's a still a war on out there... ;)
 
Mathew

---

### Post by Mcavity on 2007-10-31
so far I can live with the problem with my nic.. but waiting for the fix. 
[i can send data fast to an XP server but pulling data is slow. ]
Things improved a bunch when i disabled ipv6 though.

---

### Post by netlogic on 2007-10-31
> **sartic said:**
> I tried all "5$" lans that i can buy in my  country. All r same realtek chipset. They all do same in feisty on this. Xp pro works perfectly width all i tried pci lans, feisty failed width all the same way. I do not blame owner. I didn't count hours i spent trying 2 push linux 1 more time. Didn't ask cent because i still believe in ubuntu, but problems width samba transfers can not solved width "it works on my machine i do not know why yours ..." .. i tried all. The best i did is transfer equal 2 10mbit lan .. who needs that?!

Here is a thing. Samba is super fast. Sometimes, people have hardware and nic issues. Once in a while, it is how the network was designed in the first place. I would say on a stripped down servers, Samba will RAPE 2003 on the speed. You don't have to believe me. I have personally tested many times before I accepted the RHEL test papers. Also, you never answered any questions I asked you. The concept of plug and play network is plug and pray, which was designed by MS. Samba took IBM/MS file-sharing design and tweaked to work faster that MS. That means you have to understand how NetBios network function to get it running in Linux in order to avoid extra time on Windows machines making mistakes. In Windows, it will make tons of noise and behave like kids if you ran the sniffer. Even try to logon to wrong servers and try to give out passwords. There is  a reason why everyone says if you are a sysadmin, you must learn how to use a sniffer. If you don't, you will always plug and pray and pray to BILL GATES.

---

### Post by sartic on 2007-11-02
> **netlogic said:**
> Here is a thing. Samba is super fast. Sometimes, people have hardware and nic issues. Once in a while, it is how the network was designed in the first place. I would say on a stripped down servers, Samba will RAPE 2003 on the speed. You don't have to believe me. I have personally tested many times before I accepted the RHEL test papers. Also, you never answered any questions I asked you. The concept of plug and play network is plug and pray, which was designed by MS. Samba took IBM/MS file-sharing design and tweaked to work faster that MS. That means you have to understand how NetBios network function to get it running in Linux in order to avoid extra time on Windows machines making mistakes. In Windows, it will make tons of noise and behave like kids if you ran the sniffer. Even try to logon to wrong servers and try to give out passwords. There is  a reason why everyone says if you are a sysadmin, you must learn how to use a sniffer. If you don't, you will always plug and pray and pray to BILL GATES.

U sound so angry, do not be. Take it easy. Sorry i don't have knowledge of yours and u do not want 2 level width me :)
The problem exist not only on this machine, maybe is not samba, maybe it is in kernel, maybe it is feisty... i read many forums... even users width rh and mandriva have similar problems on some hw.

---

### Post by sartic on 2007-11-02
> **MJN said:**
> Maybe try the $10 cards? ;)
 
Seriously, it's a shame you didn't manage to track down the cause of the problem and it's a shame noone was able to come up with anything concrete to progress your issue. Sometimes it's like that though and given there wasn't much to go on (not your fault by the way, it's often better/easier when it doesn't work at all as opposed to just badly!) there probably wasn't much hope from the outset unless someone else had your card/configuration (even then the 'well mine works' response is not much help!).
 
Remember, MS may have won this battle but there's a still a war on out there... ;)
 
Mathew

U give me hope in this forum. I like objectiviness and last phrase ! :)
I didn't believe in gutsy from my observation of beta, but it suprise me. It solved my problems width installing on and stability on some nvidia chipsets and nvidia onboard gpu. Still I have problems width some onboard lans on that mobo, but I am satisfied where ubuntu desktop is going. I am not satisfied width server edition, there should be some soho version for small users width webgui admin (didn't try gutsy and ebox still so do not attack me :). MS is loosing every day because of s****s of Vista. Still do not understand why they didn't develope something like linux/bsd in core and gui like xp. Now was the time to change from old x86 code to something 64bit from ground. Maybe because of Office but the s**w in this point because from my point Office 2000 was the last good sw in this area. 

ps: ...live long and prosper... ;)

---

### Post by netlogic on 2007-11-02
> **sartic said:**
> U sound so angry, do not be. Take it easy. Sorry i don't have knowledge of yours and u do not want 2 level width me :)
The problem exist not only on this machine, maybe is not samba, maybe it is in kernel, maybe it is feisty... i read many forums... even users width rh and mandriva have similar problems on some hw.

It isn't Samba. RHEL revenues close to 70 million a year. Many people got it working without any problems. Also, it is a good idea to learn to use a network sniffer if you believe in your career.

---

### Post by Mcavity on 2007-11-05
I don't think its a amba issue. I do think there is an issue with the defaults.

IPV6 as default with IPV4 as backup / rollover?  um not good right now. many people [myself included] do not have IPV6 enabled routers. this means network access will be slow. there should be an easy way to disable IPV6 or set it to rollover after IPv4.  set IPv6 as the main protocol after more than 50% of networks out there start using it. 

Once I disabled IPv6 things got much better. [not perfect yet though]
I can still send files faster than I can receive them. but at least Its listed in minutes rather than hours now. 


Things are still improving by leaps and bounds on the linuz side, and vista is not really much of an improvement over xp.. so I think Linux is catching up very quickly. someday I hope to be able to have a Microsoft free home.

---

