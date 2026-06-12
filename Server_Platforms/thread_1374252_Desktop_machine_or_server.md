---
title: "Desktop machine or server ?"
date: 2010-01-06
forum: Server Platforms
---

### Post by s.l.i.m on 2010-01-06
Hi,

i should prepare a linux server for someone who will principally use it as print server, fax server and file sharing server on lan. He will may be use it also for webhosting later. It will be normally ON **24** hours/24.

So my question is what is the best characteristics for the machine ? 

Should i buy a normal Desktop-Machine or a Server ?

sorry for my english :)

---

### Post by quietas on 2010-01-06
To me as a linux admin, I would say this is a perfect job for Ubuntu Server. It's lightweight and is made for 24/7 usage. If need, you can then download the desktop package if you need a GUI on that machine.

As for hardware, again server components would be best. Desktop parts can operate 24/7, but for a business with money on the line, a bit more cash invested is better for that assurance. Dell has decent servers starting at as low as $500 depending on your needs, or geeks.com often has refurbished units cheaper.

---

### Post by s.l.i.m on 2010-01-07
Thanks quietas,

i have another question. What hardwere do you suggest me ? 64 or 32 bit ? and what for ubuntu server version ? should i only use the LTS versions ? If yes can later the update to the 10.04 LTS make some problems ?

---

### Post by wojox on 2010-01-07
Definitely 64 if it's an option for you and you running the server.

---

### Post by kpholmes on 2010-01-07
i have a server that does everything you listed (other then fax server) and i run a 32bit ubuntu server staying of 24/7 only rebooting for updates when needed. and im very pleased with it, but then again it mostly serves me and not an office, sure my family uses it when they need to print but thats maybe like a couple times a month :popcorn: i don't know everything about 64bit computing but to generalize it, you will only NEED 64 bit computing if you want to use more then 4 gigs of ram or this server is going to be doing a lot of hardcore processing. but its usually preferred.

what kind of environment with this server be working in?

---

### Post by quietas on 2010-01-07
32 or 64 bit, it really doesn't matter much for what you are doing. Ubuntu works either way just fine. Like KPholmes says, you only require 64 if you want to use more than 4gb of RAM.

If you are fluent in Linux and Ubuntu LTS is not needed, but realize patches will not be available for a non-LTS as long as it will be for the LTS versions. You can do an upgrade from 8.04 to 10.04 later when it is available if you need. 


On a side note, it's amusing that my Home Server thread has wound up in kpholmes signature. I guess it has definitely made the rounds.

---

### Post by Niets on 2010-01-07
> **quietas said:**
> To me as a linux admin, 
 
 
And I'm afraid unless the user is a Linux admin he is going to see that console prompt staring at him and wonder what the heck am I supposed to do now?  At least with a desktop GUI he can explore, learn how to change permissions so he can share files and actually install a printer on his own.
 
64 bit?  Look at the services required.  32 bit would not even be stressed, not sure why someone would recommend 64 bit.
 
A stable older machine with 8.04 (or other desktop version) would be more than ideal and very cost effective for this application.  This appears to be a home use situation, not corporate with multi-gigabit connections.

---

### Post by HighCommander540 on 2010-01-07
> **Niets said:**
> And I'm afraid unless the user is a Linux admin he is going to see that console prompt staring at him and wonder what the heck am I supposed to do now?  At least with a desktop GUI he can explore, learn how to change permissions so he can share files and actually install a printer on his own.
 
64 bit?  Look at the services required.  32 bit would not even be stressed, not sure why someone would recommend 64 bit.
 
A stable older machine with 8.04 (or other desktop version) would be more than ideal and very cost effective for this application.  This appears to be a home use situation, not corporate with multi-gigabit connections.

Because unless you are stupid use 64-bit. There is literally not reason to not use 64-bit. It is what all computer's will eventually be based on.

None of the rest of you know what you are even talking about with 64-bit. More RAM is not the only thing 64-bit does.

I would recommend the desktop server unless the person you are creating if for knows console stuff. Downside to that is whenever you update you need to reboot with the desktop version. With the server version you don't need to just the services you modify. And apt-get will do that for you.

---

### Post by Niets on 2010-01-07
> **HighCommander540 said:**
> Because unless you are stupid use 64-bit. There is literally not reason to not use 64-bit. It is what all computer's will eventually be based on.
 
 
Hehe - Chill-
 
He is building an appliance, not his main machine.  To make full use of 64-bit you will need native 64-bit applications, and this is where the problem starts for most users.  Enough said.

---

### Post by cascade9 on 2010-01-07
If it was me, I'd avoid high priced 'severs' (the bottom end are just normal desktops, with at best a xeon or opteron server chip, its not like they are runnign dual power supplies, etc at the low end of the market). A nice low power AMD, or just a standard Core 2 Duo would work just  as well, and the low power AMDs will use a lot less power than xeon or opteron chips. 

> **HighCommander540 said:**
> Because unless you are stupid use 64-bit. There is literally not reason to not use 64-bit. It is what all computer's will eventually be based on.

None of the rest of you know what you are even talking about with 64-bit. More RAM is not the only thing 64-bit does.

I wouldnt have been quite so harsh, but +1. Seriously, its worth it, lots of things get a major boost from 64 bit. Besides, even if there isnt a native 64 program, 32 bit works fine (or at least me and lots of other people here have had no problems anyway).

---

### Post by quietas on 2010-01-07
What what the OP is posting there will be no difference with 64 or 32 bit. Again, I'd recommend the server install and then use apt-get to add the desktop. Server does have a different kernel image than desktop with a different install base.

Also, as for hardware, there is a definite difference on server grade machines, even low end. They are made to run 24/7 stable. Desktops are not. Call HP or Dell and they will tell you the same, talk to any server/network engineer. It isn't just a difference in processor. Hard drives for example will normally be a 15k RPM SAS rather than 7200 RPM SATA, or on the low end you'd have something like a Segate ES2 rather than a Barracuda. Enterprise usage needs the higher grade equipment.

That said, for home use anything will work fine. I prefer lower end, older, server equipment myself.

---

### Post by llawwehttam on 2010-01-07
> **HighCommander540 said:**
> Because unless you are stupid use 64-bit. There is literally not reason to not use 64-bit. It is what all computer's will eventually be based on.

None of the rest of you know what you are even talking about with 64-bit. More RAM is not the only thing 64-bit does.

I would recommend the desktop server unless the person you are creating if for knows console stuff. Downside to that is whenever you update you need to reboot with the desktop version. With the server version you don't need to just the services you modify. And apt-get will do that for you.
  I agree 100%. It has be PROVED that the ubuntu 64 bit kernel IS FASTER!!! Also if it is doing a lot of tasks you will want the extra ram

---

### Post by quietas on 2010-01-07
Don't lose sight of what the topic that the OP posted about. File server, print server, fax server, possibly web in the future. This does not sounds like a big business and neither is it small home use with a fax server.

Hardware will determine if 64bit is even an option. As for hardware, he doesn't need much.

---

### Post by Digger9 on 2010-01-07
> **quietas said:**
> Don't lose sight of what the topic that the OP posted about. File server, print server, fax server, possibly web in the future. This does not sounds like a big business and neither is it small home use with a fax server.

Hardware will determine if 64bit is even an option. As for hardware, he doesn't need much.


+1
Everyone is aware of the advantages of 64 bit.  But 32 bit on older hardware is perfect for the application of file/print/fax server.  Seems everyone is caught up in the "mine is biger than yours" syndrome.  It happens all too often.

---

### Post by quietas on 2010-01-07
Exactly. At work I run an Ubuntu 8.04 server on a Dual P3 1.4 with 1gb RAM. It works perfect with Server 32b bit using Apache, Wordpress, GLPI, OSCNG, and is getting an upgrade to a whopping dual Xeon 3.06 with 4gb RAM. Again, 32bit processors and far more server than is needed, but perfectly adequate.

---

### Post by HighCommander540 on 2010-01-07
> **Digger9 said:**
> +1
Everyone is aware of the advantages of 64 bit.  But 32 bit on older hardware is perfect for the application of file/print/fax server.  Seems everyone is caught up in the "mine is biger than yours" syndrome.  It happens all too often.

> **quietas said:**
> Exactly. At work I run an Ubuntu 8.04 server on a Dual P3 1.4 with 1gb RAM. It works perfect with Server 32b bit using Apache, Wordpress, GLPI, OSCNG, and is getting an upgrade to a whopping dual Xeon 3.06 with 4gb RAM. Again, 32bit processors and far more server than is needed, but perfectly adequate.

No one here is saying that you need to go out and buy a Xeon. Buying even the lowest 64-bit which is like $50 now.

---

### Post by cascade9 on 2010-01-09
> **quietas said:**
> Also, as for hardware, there is a definite difference on server grade machines, even low end. They are made to run 24/7 stable. Desktops are not. Call HP or Dell and they will tell you the same, talk to any server/network engineer. It isn't just a difference in processor. Hard drives for example will normally be a 15k RPM SAS rather than 7200 RPM SATA, or on the low end you'd have something like a Segate ES2 rather than a Barracuda. Enterprise usage needs the higher grade equipment.
 
 Not at the bottom end of servers, they dont. 
 
 HP Media Smart Server LX195- 
 Atom 1.6GGhz, DDR2, SATA 7200. 
 [http://www.shopping.hp.com/product/computer/categories/home_servers/1/accessories/FL702AA%2523ABA;HHOJSID=hvLQLLJT39jjwdsg5vp6w5q2nFVJHrhLDyGJJ2mQMdkpvW2mR0VJ!1718639158]("http://www.shopping.hp.com/product/computer/categories/home_servers/1/accessories/FL702AA%2523ABA;HHOJSID=hvLQLLJT39jjwdsg5vp6w5q2nFVJHrhLDyGJJ2mQMdkpvW2mR0VJ%211718639158")
 
 HP Media Smart Server EX490-
 2.2Ghz Celeron!, DDR2, SATA 7200
 [http://www.shopping.hp.com/product/computer/categories/home_servers/1/accessories/FL704AA%2523ABA;HHOJSID=hvLQLLJT39jjwdsg5vp6w5q2nFVJHrhLDyGJJ2mQMdkpvW2mR0VJ!1718639158]("http://www.shopping.hp.com/product/computer/categories/home_servers/1/accessories/FL704AA%2523ABA;HHOJSID=hvLQLLJT39jjwdsg5vp6w5q2nFVJHrhLDyGJJ2mQMdkpvW2mR0VJ%211718639158")
 
 Those machines are pretty much just standard desktops, with 'server' branding.  
 
 Dell Power Edge T100-
 Core2Duo5400 (Xeon an option), single-rank DIMM, SATA 7200 (SAS an option) 
 [http://configure.us.dell.com/dellstore/config.aspx?oc=bemqa2d&c=us&l=en&s=bsd&cs=04](http://configure.us.dell.com/dellstore/config.aspx?oc=bemqa2d&c=us&l=en&s=bsd&cs=04)
 
 Dell Power Edge T110- 
 Xeon, UDIMM, SATA 7200 (SAS an option) 
 [http://configure.us.dell.com/dellstore/config.aspx?oc=beswlb1&c=us&l=en&s=bsd&cs=04&kc=rec_server_networksol](http://configure.us.dell.com/dellstore/config.aspx?oc=beswlb1&c=us&l=en&s=bsd&cs=04&kc=rec_server_networksol)
 
 Same basic setup on the T300 and other low end Dell servers. 
 
 I agree that SAS or 'enterprise' level drives are better drives, but its not like you cant buy them without any trouble from lots of places. 

IMO, lots of the lowend servers are pretty much just desktops. The higher end, yes, they are much more reliable than desktops but you really pay for that. Its not like desktops have that much trouble running 24/7, I have various friends who run 24/7 and never had issues (running everything from pentuim 2s though to Core2Duos and AMD X2/X3/X4s)

> **llawwehttam said:**
> I agree 100%. It has be PROVED that the ubuntu 64 bit kernel IS FASTER!!! Also if it is doing a lot of tasks you will want the extra ram

It has been. BTW, its not a ubuntu kernel, its a linux kernel :P 

> **quietas said:**
> Exactly. At work I run an Ubuntu 8.04 server on a Dual P3 1.4 with 1gb RAM. It works perfect with Server 32b bit using Apache, Wordpress, GLPI, OSCNG, and is getting an upgrade to a whopping dual Xeon 3.06 with 4gb RAM. Again, 32bit processors and far more server than is needed, but perfectly adequate.

Agreed. If the OP ends up with 32 bit only hardware, that is fine, it will do the task.  but if they end up with 64bit capable hardware, why not use 64bit? It makes sense to me.

---

### Post by s.l.i.m on 2010-01-12
Hi,

thank you all !

i think that i will opt for a desktop machine. For the 64bit i affraid to have compatibility problems. I think that the most applications are only 32bit native, so will they work with a 64bit without bugs ? ( i don't have much time for resolving bugs :) )

---

### Post by cmadooly on 2010-01-12
> **s.l.i.m said:**
> Hi,
 
thank you all !
 
i think that i will opt for a desktop machine. For the 64bit i affraid to have compatibility problems. I think that the most applications are only 32bit native, so will they work with a 64bit without bugs ? ( i don't have much time for resolving bugs :) )
 
 
To give you a simple answer.
 
If this machine is being used as a print/fax/file server. You can grab a 5 year old PC and use that. Just make sure you have adequate storage space on it.
 
64-bit machines are obviously going to be faster but IMO, you wont see that big of a difference between 64 and 32 if the server is being used for printing/faxing/storage.

---

### Post by quietas on 2010-01-12
> **cmadooly said:**
> To give you a simple answer.
 
If this machine is being used as a print/fax/file server. You can grab a 5 year old PC and use that. Just make sure you have adequate storage space on it.
 
64-bit machines are obviously going to be faster but IMO, you wont see that big of a difference between 64 and 32 if the server is being used for printing/faxing/storage.

Yeah, he's got it right. Any old machine should work. I'd say upper end P4 or greater. As for 32 bit or 64, it really doens't matter in your case.

---

### Post by Queue29 on 2010-01-12
> **quietas said:**
> Yeah, he's got it right. Any old machine should work. I'd say upper end P4 or greater. As for 32 bit or 64, it really doens't matter in your case.

Ooh, I wouldn't recommend a Pentium 4, they run hotter than hotcakes at the county fair.

---

### Post by quietas on 2010-01-12
If you have no budget and have a working P4, it's better than not buying a system. But a Core2/Athlon X2 would be better, newer by a couple generations.

---

### Post by HighCommander540 on 2010-01-12
> **s.l.i.m said:**
> Hi,

thank you all !

i think that i will opt for a desktop machine. For the 64bit i affraid to have compatibility problems. I think that the most applications are only 32bit native, so will they work with a 64bit without bugs ? ( i don't have much time for resolving bugs :) )

Most 32bit Ubuntu packages can be installed on the 64bit system. Some packages do require that use use a converter/patcher program to make them work, but there are numerous topics in the 64 bit section to tell you how to do this.

---

