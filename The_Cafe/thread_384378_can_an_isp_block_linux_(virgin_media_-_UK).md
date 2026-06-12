---
title: "can an isp block linux? (virgin media - UK)"
date: 2007-03-14
forum: The Cafe
---

### Post by nandasunu on 2007-03-14
OK, so I got my sister to switch to ubuntu a while back but she had no internet connection at the time. She is getting internet from Virgin Media on Friday, but they say that they don't support linux and so won't set up her internet connection unless she is running windows or mac (at least that seems to be the jist of it).

I think what they mean is that their crappy activation cdrom doesn't work with linux so they are brushing her off.  

My point of this message is that I am pretty sure that once her internet connection is active it will work with ubuntu, but is there a possibility that it won't? Maybe the router they provide is not linux compatible? I am going to have to reinstall windows on her pc so they will activate her connection, but is it worth doing a dual boot if the internet won't work?

Does anyone here use Virgin Media (previously NTL/Telewest)? Does it work for you?

Thanks.

---

### Post by Aetherius on 2007-03-14
NTL (Virgin Media) 10Mb here, not a problem, running a network of 6(7) machines, 1 Mac, 3 Ubuntu, 1 Debian, 2 Arch Linux, none of them have any problem.


You DO need to run the setup CD from windows though.

Borrow someones laptop for the whole 15 minutes you'll need windows.

---

### Post by Tomosaur on 2007-03-14
> **nandasunu said:**
> OK, so I got my sister to switch to ubuntu a while back but she had no internet connection at the time. She is getting internet from Virgin Media on Friday, but they say that they don't support linux and so won't set up her internet connection unless she is running windows or mac (at least that seems to be the jist of it).

I think what they mean is that their crappy activation cdrom doesn't work with linux so they are brushing her off.  

My point of this message is that I am pretty sure that once her internet connection is active it will work with ubuntu, but is there a possibility that it won't? Maybe the router they provide is not linux compatible? I am going to have to reinstall windows on her pc so they will activate her connection, but is it worth doing a dual boot if the internet won't work?

Does anyone here use Virgin Media (previously NTL/Telewest)? Does it work for you?

Thanks.

There is absolutely no reason why an internet connection won't work. It is theoretically possible that they could cut the connection once they discover you are running Linux, but it's probably illegal, and they'll only lose out anyway, so there's no point. What they're saying is that they do not SUPPORT Linux. In other words, if you encounter problems which are related to your machine, and not their net connection, then they won't be able to help you. If your router is only connected to your machine via an ethernet cable, it will work. You configure your router by pointing a web browser at it, not by messing about on your machine (although it is possible, just not necessary). If the router is a wireless router, then the wireless device attached to your machine may not work on Linux. This is a driver issue, and most of these problems are fairly easy to resolve. Ethernet connection WILL work, wireless MAY work. Some modems will only work on Windows (they're called Winmodems, aptly enough), so if you have one of those, you should probably save yourself some hassle and buy a decent router.

Best thing to do, honestly? Just fire up the LiveCD and see if the net connection works. If it does, then you're good to go :)

---

### Post by MikeDX on 2007-03-14
> **Aetherius said:**
> 
You DO need to run the setup CD from windows though.


Do you??? I'm on NTL and I just plugged the cable modem straight into my router and wireless hubs and off I went, happy days. Two ubuntu machines, one windows xp, 2 xbox's, 2 nintendo ds's 3 psps, a nintendo wii and occasionally other family members laptops..

Never had a problem

Actually I never realised how many things we had connected up! :lolflag:

---

### Post by Aetherius on 2007-03-14
from my experience with the NTL modems, they block HTTP traffic until the pin number and MAC address is registered with their exchange. This is done automatically by the CD. Did an engineer install and setup your modem for you? If not then you're just lucky! I've had to help with well over 10 different NTL setups and they all needed the stupid CD run to activate.


IDEA: If you ring ntl and tell them you are ONLY using the internet to connect up your consoles XBOX360, Wii etc. They publicly support this, and must then provide an alternate means for activation......Maybe.

---

### Post by DoctorMO on 2007-03-14
> You DO need to run the setup CD from windows though.

No you don't, with NTL (back when it was) I educated some of their install staff about how to install around a linux machine; you don't need the cd rom you just need to plug it in restart the router and use dhclient tool to request a fake ip address. this will then point any website you go to to the NTL setup website located on the modem/set-top-box.

and I only use dhclient because I don't want to wait for it to automaticly retry, it will connect by it's self and you'll never have to restart the machine so long as you restart the network.

Aetherius, your doing it wrong and giving off the wrong impression to users to boot.

---

### Post by H.E. Pennypacker on 2007-03-14
Just go ahead with the service, because you will not need Windows.  Let us know which router they're providing, but I guarantee you that it will be fine.  The thought of a router not work is almost ludicrous.  

Not supporting Linux is entirely different from not working with Linux.  My ISP says the same thing, and I am just fine.  What are the chances you are in a worse position?  I am using a Broadcom wireless card!

> **Aetherius said:**
> 
You DO need to run the setup CD from windows though.

Borrow someones laptop for the whole 15 minutes you'll need windows.

I am wiling to put money down that says you don't need the CD.  These CDs are only used to see if everything works (e.g. all cables are connected), but they don't actually set anything up.

---

### Post by Aetherius on 2007-03-14
i stand corrected :D

in my defense, my information is assumption mulitplied by ineptitude of NTL support staff

---

### Post by nandasunu on 2007-03-14
Thanks for all the help, I will try and get my hands on an XP laptop and use their CD with that, I'm sure it will be fine.

---

### Post by beercz on 2007-03-14
I'm a Virgin customer too - and you do not need windows to set it up.  Works perfectly well as a LAN connection.

---

### Post by mips on 2007-03-14
> **nandasunu said:**
> ...I will try and get my hands on an XP laptop and use their CD with that, I'm sure it will be fine.

Lol, look at the damage you guys have done :)

---

### Post by nandasunu on 2007-03-14
> **beercz said:**
> I'm a Virgin customer too - and you do not need windows to set it up.  Works perfectly well as a LAN connection.

Did they activate it for you without using the cd/windows?

---

### Post by bonzodog on 2007-03-14
You DO NOT need windows to use an ntl connection. I'm an ex-ntl engineer, and know how this thing works. 
First thing you do, is go to the registration website (this is the only website which will load successfully) and confirm the connection there. 

The modem will connect using the ethernet connection (usually eth0). 

The engineer who delivers the modem will give you an activation code and pass which you type into the website.

It takes about 10-20 minutes for the server to update. 

After that, you should have your ntl mail address set-up (or virgin media as it is there now!), and be free to browse the web. Make sure the eth0 connection is showing as being 'up', and you have a gateway IP, and a DNS server IP. Use a generic DHCP connection, with dynamic IP allocation.

However, you are on your own with setting it up. The engineer will only do the cable connection and plug the modem in - you will have to plug in the ethernet cable and set-up the connection yourself - when you are on linux, there is no support from them.

---

### Post by beercz on 2007-03-14
> **nandasunu said:**
> Did they activate it for you without using the cd/windows?
From memory (it was about 5 years ago with Telewest) they only wanted my MAC address.  I gave them my cable (wireless) router.

It could have changed I suppose.  Perhaps someone has a more recent experience.

Does it say anything on their website?

---

### Post by Redache on 2007-03-14
> Thanks for all the help, I will try and get my hands on an XP laptop and use their CD with that, I'm sure it will be fine.

3 words

Ofcom,Ofcom,Ofcom

They have no right in the world to deny service or to give you the missconception that because you use an Alternate OS you can't have internet.

I'd kick up a fuss because it is utter crap. 

This is why people like Virgin should stick to talentless musicians :P

---

### Post by MikeDX on 2007-03-14
> **nandasunu said:**
> Thanks for all the help, I will try and get my hands on an XP laptop and use their CD with that, I'm sure it will be fine.

If you really must go down the XP route (or any windows route) just install win98 via the evaluation version of vmware - you must know somebody with a win98 cd.. :guitar:

---

### Post by Spr0k3t on 2007-03-14
Here's something to think about... there are devices out there which do not run Windows or Mac software that are not Linux which can be connected to the internet.  Some of these devices include Palm based PDAs, Playstations, XBoxs, WIIs, Internet Settop Boxes.  Having them deny you the right to access the internet without the requirement of a Windows or Mac system with a CDRom is monopolistic behavior and they are required to give you information on how to register the user information without it.

A few weeks back I had a very similar situation where a nearby family had just set up their Wii and they wanted broadband.  They were told in a few choice words by the DSL provider to get lost.  I stepped in and asked the right questions... five minutes later they were registered and on the internet without a windows or mac system.  The right questions entail information such as DSN IPs, user ID creation pages, static ip addresses, gateways, and how to go about changing your internet password once your account is already created.  Turned out the CD to install the software was nothing more than just a skinned/themed browser based off of internet explorer.

Ultimately it can be done... they may not support your endeavors with Linux connectivity but the internet is oblivious to what is connected to it.  So, best of luck and post your results so others like your sister may be able to do the same.

Oh yeah, don't forget to submit information to the broadband provider on how to go about setting up the modem without the install CD.  Generally it will upset the executives but make the tech support people fairly happy.

---

### Post by H.E. Pennypacker on 2007-03-14
You guys, we're pretty sure at this point that this is not some anti-Linux stance on behalf of Virgin.  They simply don't want to give the user the impression that they provide technical support for Linux.  Others using the same service have been perfectly happy, and of course, their Internet works for them just as it works for others.  

I don't know why you're borrowing an XP laptop when you were told you won't need Windows at all.

---

### Post by nandasunu on 2007-03-16
So the installation guy has been and gone now, it was actually a lot easier than I thought it would be. I just followed the "Mac" installation guide, basically go to such and such website and enter your details.. now its up and running fine! and I didn't have to do anything silly like install/borrow windows :)

Virgin should train their support staff better so they don't confuse people more than they have to, they don't have to offer complete support, but to have told my sister that the internet wouldn't work with linux is just silly..

Thanks for all the help and suggestions!

---

### Post by TorqueyPete on 2008-04-27
> **nandasunu said:**
> 

Virgin should train their support staff better so they don't confuse people more than they have to, they don't have to offer complete support, but to have told my sister that the internet wouldn't work with linux is just silly..

Thanks for all the help and suggestions!



All they need to say is that they can't offer tech support for Linux users! :roll: 
 That's what the guy told me on the phone 3.5 yrs ago when i decided to try Mandrake.

---

### Post by rolnics on 2008-04-27
> **nandasunu said:**
> Virgin should train their support staff better so they don't confuse people more than they have to, they don't have to offer complete support, but to have told my sister that the internet wouldn't work with linux is just silly..

Thanks for all the help and suggestions!

This is the thing about linux being in the minority of the OS world! I'm sure years ago there were similar threads on MAC forum's! I'm sure one day linux will have a better share of the market and that will be the time why the support staff will learn about it, fingers crossed!

---

### Post by billgoldberg on 2008-04-27
don't know if this applies to virgin media, but my ISP (belgacom) also had a "activation cd".

Since I didn't have access to a windows pc, I just opened up the web interface of my router (192.168.1.1) and entered the details myself.

I was on the web in 1 minute, running the cd would have taken at least 10 minutes.

---

### Post by Eclipse. on 2008-04-27
Virgin media actually do support ubuntu and linux in general.

They have mirrors for:

Tucows Mac  [http]("http://mac.tucows.virginmedia.com/")  
Linux Kernel  [http]("http://kernel.virginmedia.com/")  [ftp]("ftp://ftp.virginmedia.com/sites/www.kernel.org/")  
Fedora Linux  [http]("http://fedora.virginmedia.com/")  [ftp]("ftp://mirrors.virginmedia.com/sites/ftp.fedora.org/")
Tucows PDA  [http]("http://pda.tucows.virginmedia.com/") 
 Freebsd  [http]("http://freebsd.virginmedia.com/")  [ftp]("ftp://ftp.virginmedia.com/sites/ftp.freebsd.org/")
Debian Linux  [http]("http://debian.virginmedia.com/")  [ftp]("ftp://mirrors.virginmedia.com/sites/ftp.debian.org/")  
Openoffice  [http]("http://openoffice.virginmedia.com/")  [ftp]("ftp://ftp.virginmedia.com/sites/www.openoffice.org/")
Tucows Games  [http]("http://tucows.virginmedia.com/") 
 Tucows  [http]("http://tucows.virginmedia.com/")  
Tucows Linux  [http]("http://linux.tucows.virginmedia.com/")  
Gentoo  [http]("http://gentoo.virginmedia.com/")  [ftp]("ftp://ftp.virginmedia.com/sites/gentoo/")  
OpenBSD  [http]("http://openbsd.virginmedia.com/")  [ftp]("ftp://ftp.virginmedia.com/sites/OpenBSD/")  
Ubuntu linux  [http]("http://ubuntu.virginmedia.com/")  [ftp]("ftp://ftp.virginmedia.com/sites/ubuntu/")  
Slackware Linux  [http]("http://slackware.virginmedia.com/")  [ftp]("ftp://mirrors.virginmedia.com/sites/ftp.slackware.com/")  
Tucows Themes  [http]("http://themes.tucows.virginmedia.com/")  
Apache  [http]("http://apache.virginmedia.com/")  

[http://mirrors.virginmedia.com/](http://mirrors.virginmedia.com/)

---

### Post by ssam on 2008-04-27
you know there are ISPs that activly support Linux and free software [http://www.ukfsn.org/](http://www.ukfsn.org/) (they also managed to give me 8mb/s on a line that tiscali said could only do 512kb/s)

---

### Post by xpod on 2008-04-27
> Virgin should train their support staff better so they don't confuse people more than they have to, they don't have to offer complete support, but to have told my sister that the internet wouldn't work with linux is just silly..

Thanks for all the help and suggestions!

If Virgin blatantly told your sister that the interet wouldn`t actually work with Linux then that is pretty outrageous but then Virgins tech support can barely support their Windows using customers at the best of times so i would`nt worry about it too much.:)

> Virgin media actually do support ubuntu and linux in general.


I do like my 5 minute ISO`s:)

---

### Post by Astinsan on 2008-04-27
Tech Support isn't usually connected to the company. It is very expensive to setup and train people to do TS. They usually will script out questions and responses.  

You will notice when some TS agents stop listening to you and keep reading off steps. 

Then there is the affiliate / franchise call centers. Those are the dirty centers that try to sell you upgrades that you don't need. 

Bottom line is all ISP's use Unix based software on the in side. Even MSN has Unix Based software on the in side. So they all support Unix based operating systems. the TCP stack is the same on most operating systems anyways.

---

### Post by robelliott2125 on 2008-04-27
If i'm not mistaken, you don't need to use the disk to actually activate the Modem (Depending on what modem, who serves the area).

For instance, the NTL 250, and 255, have a CD, but you can do the setup in a weblink.  You'll need to ask them about this.

What VM mean about the OS bit, is they will not support your OS.  Not that they can't install the broadband, as that would be rediculous.

If you overcomplicate things for them, they don't understand, and get confused.  

For instance;
whats a router?
Whats Linux, is that a new Windows?

Phone them, and just say your having problems with the installation cd, and you've heard of a webpage based setup, and can you have the link?

Also, VM refuse to install on any systems which happen to have over complicated AV's (Considering Nod32 isn't overcomplicated).
They only know what they trust and have used for years, such as Whinedoze and Mac.  -  Tbh, ISP's have only recently started supporting Macs, and don't use them themselves (Previous knowledge from working for Sky Broadband in Belfast).

Some Engineers however know their stuff.  One Engineer who came out recently actually solved an issue i had with my installation, which I was starting to change my mind about Ubuntu.

Hope you get it sorted though... Let me know if this works for you.

---

### Post by starfunker on 2008-04-27
I'm also a customer of Virgin Media and I've had no problems using Ubuntu with the modem or router.

---

### Post by robelliott2125 on 2008-04-27
> **Astinsan said:**
> Tech Support isn't usually connected to the company. It is very expensive to setup and train people to do TS. They usually will script out questions and responses.  

You will notice when some TS agents stop listening to you and keep reading off steps. 

Then there is the affiliate / franchise call centers. Those are the dirty centers that try to sell you upgrades that you don't need. 

Bottom line is all ISP's use Unix based software on the in side. Even MSN has Unix Based software on the in side. So they all support Unix based operating systems. the TCP stack is the same on most operating systems anyways.

I hope you don't think i'm about to flame, but I'm an experienced Technical Agent, and have been in the call centre scene for five years.
Having worked for some of the worlds leading Manufacturers, you'd be surprised to know that most Tech based call centres don't infact have scripts, this is mostly down to Customer Services, since they'll have limited knowledge and resources.

Technical Support is exactly as it says on the tin, they do tech support.
In my time of working on the scene, i've been trained in both Mac, Windows, Servers and when I was about to learn Linux, I left the company (not because of the training, but relocated).  So now I'm running Linux 100% at home, no dual boots, no Windows backup etc, just running Linux on its own, and learning for myself.

I have spent upto 2/3 hours supporting customers with their issues, and made sure they get what they've paid for, to the point where I climbed through a company 3 times in a year, which was good going for me.

Also, the Franchise call centres are mostly outsource centres, a cheaper alternative to getting their own staff to do the crap work, for instance, Hotmail / MSN outsource to Belfast, to a company called Gem.
Gem also have Expedia, Play.com, Match.com King.com and various other companies.
Vodafone have about 8 different outsource centres, one called Firstsource, also Belfast based.
Sky Broadband / HSBC / UKOnline - Teletech.

Its just crap pay, crap people, and the training is again crap, since their turnovers are high, so why train people fully to support the customers when its cheaper to throw them out there, and learn ad-hoc.

The job I climbed three times in a year, I only left due to relocation, but loved the job, loved the pay, and most of all, was loving the fact that they actually trained you in things you wanted to learn.
I unfortunately left without learning HTML, but yet know how to configure a server, strip and fully repair a laptop (with and without soldering) and various other things, considering I went in and left as just a mere Technical Agent.

I do apologise if I seem to have flamed on here, but I just wanted to make a polite point, that not all Tech Agents are useless.

---

### Post by ronacc on 2008-04-27
I dont know if this applies to Virgina media since I am in the US but all I have ever had to do with an isp that "don't support  linux" is give them the mac address of my modem and setup networking on my end.

---

### Post by jeyaganesh on 2008-04-27
I am also a virgin media user for more than 8 months. I am using belkin wireless adapter for internet. It works fine. Please,check your computer settings to fix this problem.

---

### Post by GOROSSI on 2008-04-27
I set up with Virgin on 2mb (NTL as it was then) 2 1/2 years ago. 

I refused to used the install CD (properly boxed not a WORM disc, given to me by the Engineer) Spybot search and destroy (on my windows machine) flagged software on it as being spyware, Plus when I tried it the installer didn't work anyway.

So as an alternative  was given an IP address to go to in Firefox to set the service up.

any ever since the connections been fine for me apart from at 4pm till about 8pm the download speed haves to about 120k/s which was a pain when I was downloading Hardy but I used their mirror so it was consistent fortunately.

---

### Post by xpod on 2008-04-27
> I refused to used the install CD (properly boxed not a WORM disc, given to me by the Engineer) Spybot search and destroy (on my windows machine) flagged software on it as being spyware, Plus when I tried it the installer didn't work anyway.


Generally the only time anyone should actually need the VM setup CDRom is if they require the USB drivers from it,in Windows anyway(even their provided USB Network adapter actually worked out the box in Ubuntu for me).
Now that Virgin have the wireless option available there will be those drivers to consider too i suppose.
 
> any ever since the connections been fine for me apart from at 4pm till about 8pm the download speed haves to about 120k/s which was a pain when I was downloading Hardy but I used their mirror so it was consistent fortunately.

It probably wont just be between 4pm & 8pm that your connection slows down if you hits those limits of theirs now.
[http://www.trustedreviews.com/networking/news/2008/04/21/Virgin-Trials-Complex-Traffic-Management/p1](http://www.trustedreviews.com/networking/news/2008/04/21/Virgin-Trials-Complex-Traffic-Management/p1)

---

### Post by imronak on 2008-04-27
why dont you guys boycott those bastards, its this monopolistic attitude thats hurts linux.



To them, 
"Hello, wake up."

You pay for the service, if they say they dont give, you demand service or dont pay them. I am of the belief that if I am paying $ to someone, I demand service. Why to get bogged down.

Beware of these companies, they want make you puppets. :x

---

### Post by xpod on 2008-04-27
> why dont you guys boycott those bastards, its this monopolistic attitude thats hurts linux.



To them,
"Hello, wake up."

You pay for the service, if they say they dont give, you demand service or dont pay them. I am of the belief that if I am paying $ to someone, I demand service. Why to get bogged down.

Beware of these companies, they want make you puppets. 

There are probably even better reasons besides the STM to be boycotting Virgin just now but as far as we`re concerned the only other option for BB is an ADSL line and a potential 8Mb so i`ll stick with our 20Mb,for which i pay the price of their old 4Mb line.Thats not counting the separate 1Mb STB connection we still have too.
We never really use enough bandwidth to be triggering the limits(the old ones) at the best of times so it`s not that much of a concern here.
The heavy P2P/Newsgroup users are not as easily pleased though it seems:)

Virgin are the only viable Cable provider just now and as much as i myself dislike some of their underhand practices it is only a broadband connection at the end of the day and not not someone deciding the fate of our first born.
Thats not to say i might not change in the future but for now i`m going nowhere.

---

### Post by scouser73 on 2008-04-28
There won't be a problem with your sister using Linux with Virgin Media, the CD that they give is for setting up Outlook Express and PC Guard. Once her connection is established then she can start enjoying Linux.  I would recommend that she gets Thunderbird (alternate Email client).

---

### Post by jespdj on 2008-04-28
> **nandasunu said:**
> OK, so I got my sister to switch to ubuntu a while back but she had no internet connection at the time. She is getting internet from Virgin Media on Friday, but they say that they don't support linux and so won't set up her internet connection unless she is running windows or mac (at least that seems to be the jist of it).

I think what they mean is that their crappy activation cdrom doesn't work with linux so they are brushing her off.
I would switch to a different ISP immediately if my ISP would tell me something like this.

---

### Post by rolnics on 2008-04-28
> **imronak said:**
> why dont you guys boycott those bastards, its this monopolistic attitude thats hurts linux.



To them, 
"Hello, wake up."

You pay for the service, if they say they dont give, you demand service or dont pay them. I am of the belief that if I am paying $ to someone, I demand service. Why to get bogged down.

Beware of these companies, they want make you puppets. :x

Yeah but the thing is broadband over here in the UK is stuck in the dark ages for speed!

> **xpod said:**
> There are probably even better reasons besides the STM to be boycotting Virgin just now but as far as we`re concerned the only other option for BB is an ADSL line and a potential 8Mb so i`ll stick with our 20Mb,for which i pay the price of their old 4Mb line.


ADSL doesn't compare to cable. We moved from a Telewest (now Virgin) area to a non-cable area, oh my god what a shock to the system! When we were with Telewest the net was just there, in about 3 or so yrs we had it i only had about 1days outage. ADSL is a pain, sometimes i need to reset my modem 3 or 4 times to just get a connection! And when i do get a connection it's naff! I've got the "Upto 8Mb" package and that's a joke, if i get 3Mbs i'm doing well!!


@nandasunu have you got it up and running though that's the important thing? And how'd you manage it?

---

### Post by scouser73 on 2008-05-06
> **rolnics said:**
> Yeah but the thing is broadband over here in the UK is stuck in the dark ages for speed!



ADSL doesn't compare to cable. We moved from a Telewest (now Virgin) area to a non-cable area, oh my god what a shock to the system! When we were with Telewest the net was just there, in about 3 or so yrs we had it i only had about 1days outage. ADSL is a pain, sometimes i need to reset my modem 3 or 4 times to just get a connection! And when i do get a connection it's naff! I've got the "Upto 8Mb" package and that's a joke, if i get 3Mbs i'm doing well!!


@nandasunu have you got it up and running though that's the important thing? And how'd you manage it?

The UK is stuck in the dark ages for speed!?, no, there have been trials run in certain parts of Kent which Virgin Media cable users can have 50Mb, ok so they won't necessarily get the full amount of speed, but it's going in the right direction.

Maybe you should ask Virgin Media if they have any plans for getting cable in your area.

---

### Post by terry_gardener on 2008-05-06
found this website might be helpful 

[http://www.cableforum.co.uk/board/94/33602415-how-set-up-your-ntl-broadband.html](http://www.cableforum.co.uk/board/94/33602415-how-set-up-your-ntl-broadband.html)

---

### Post by ecomoney on 2008-11-30
Hi, I run a company that provides recycled computers running linux (both ubuntu or a in-house customised version of puppy linux). Over the years I must have set up over a hundred people with NTL bradband and it will *definetely* work...in fact better than any other OS!!!

Until recently, all that was required was to go to [url] http://80.5.178.26 [url] and follow the setup steps, entering a code "Code:- NTL-CT8-CJ486" when asked (I think this is particular to our area of lincolnshire). However, virgin have recently introduced a change for initially registering their modems.

New installs (at least in this area) will redirect you to their new sign in page, upon clicking the "activate" button their website dos a check to see what OS you are running through the browser, and if you are not running OSX or winblows then it will reject you....OFCOM?

Having a quick search on the net reveals this blog

[http://blog.hands.com/2007/12/21#virginmedia](http://blog.hands.com/2007/12/21#virginmedia)

This tells you to go to [https://autoreg.autoregister.net/](https://autoreg.autoregister.net/) which appears to be a back door that skips the OS check and will allow you to register using linux. However, Ive just tried this at a customers hous and it appears to be no longer active, after asking you whether you want to register broadband or dial-up, the connection just times out. :(

Short of having to install winblows on my support laptop (waste of disk space IMHO), Im going to try this firefox addon [https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59) to see if I can bypass the pointless OS check. I am returning to the customers house tommorow where I will verify this method and post back.

I really cannot understand a commercial company like Virgin media denying linux users in this way unless there was some sort of commercial reason (like they cant install spyware or monitor your downloads of their mediocre collection of artists for example).

---

### Post by Swagman on 2008-11-30
BT said the same kind of thing to me..... Except I was putting an **AMIGA** G4 online.

---

### Post by bruce89 on 2008-11-30
> **ecomoney said:**
> New installs (at least in this area) will redirect you to their new sign in page, upon clicking the "activate" button their website dos a check to see what OS you are running through the browser, and if you are not running OSX or winblows then it will reject you....OFCOM?


This really should be referred to Ofcom, it seems ridiculous that this would be the case.

---

### Post by dmn_clown on 2008-11-30
> **Tomosaur said:**
> There is absolutely no reason why an internet connection won't work.

You've obviously never ran into any of the supposed "high speed" dialup services that use login protocols that aren't supported by linux based dialers.

---

### Post by mick222 on 2008-12-01
I recently set up a virginmedia connection on my computer ,8.04 at the time,
all i had to do phone them as i already had a cable to the house and  they activated the line . No setup cd as it's a lan connection which doesnt require a log in.
 virgin media hosts ubuntu on there servers

---

### Post by brokenreality on 2008-12-01
> **billgoldberg said:**
> don't know if this applies to virgin media, but my ISP (belgacom) also had a "activation cd".

Since I didn't have access to a windows pc, I just opened up the web interface of my router (192.168.1.1) and entered the details myself.

I was on the web in 1 minute, running the cd would have taken at least 10 minutes.

Even if the ISP provided a install cd, I still have never needed to use it.

---

### Post by xpod on 2008-12-01
> However, virgin have recently introduced a change for initially registering their modems.

If your customer has a Virgin landline you can call them free on 150 and all you should need to do is register the Mac address of the modem to get online.

---

### Post by ecomoney on 2008-12-01
> If your customer has a Virgin landline you can call them free on 150 and all you should need to do is register the Mac address of the modem to get online. 

That is interesting, i will give that a go. 

I tried registering my new customers modem today using the [user agent switcher extention](https://addons.mozilla.org/en-US/firefox/addon/59) which I brought on my memory stick, and I managed to get past the browser check using it. To install it with the computer offline I hide to go to file>open on firefox and point it at the file on my memory stick.

Bad news though, after the next screen (where the user has to enter their surname and postcode), we were presented with a screen that installed a load of virgin toolbar spam and set the home page to virgin.net. As linux doesnt allow this kind of scurf on, it wouldnt progress. It asked me to add a new search engine (which it did) but then clicking on the "next" button did nothing. Ive recovered a screen shot, and the source of the page in the hope that someone may be able to decode it and tell me how to get further on.

I managed to pursade my customer to lend me the unregistered modem for a few days so I have it here to "prod with a stick" if anyone has any advice. For the moment he is using my wireless dongle to access through his neighbours wireless so is happy for the moment.

Any help appreciated

---

### Post by xpod on 2008-12-01
Could have had them online with a phone call by now.:)
Having the Modem at your house wont be much good because it will only work with the registered account i believe.Legally anyway.

150?

---

### Post by billgoldberg on 2008-12-01
> **nandasunu said:**
> OK, so I got my sister to switch to ubuntu a while back but she had no internet connection at the time. She is getting internet from Virgin Media on Friday, but they say that they don't support linux and so won't set up her internet connection unless she is running windows or mac (at least that seems to be the jist of it).

I think what they mean is that their crappy activation cdrom doesn't work with linux so they are brushing her off.  

My point of this message is that I am pretty sure that once her internet connection is active it will work with ubuntu, but is there a possibility that it won't? Maybe the router they provide is not linux compatible? I am going to have to reinstall windows on her pc so they will activate her connection, but is it worth doing a dual boot if the internet won't work?

Does anyone here use Virgin Media (previously NTL/Telewest)? Does it work for you?


Thanks.

It's just their activation cd that won't work.

It's extremely easy to set that up yourself from a browser connected to the router.

On your sisters pc, go to firefox and go to your routers interface (it will most likely be [http://192.186.1.1](http://192.186.1.1)) and enter your info given to you by your ISP (username and password).

--

I guess they could cut you off if they want to. That being said, there is no way they'll do it (they would lose money and gain nothing).

I don't know why they don't just give instructions to do this manually if you use Linux. 

It's so easy, I don't get why they don't do it.

---

### Post by billgoldberg on 2008-12-01
> **brokenreality said:**
> Even if the ISP provided a install cd, I still have never needed to use it.

Well if you get a new internet connection, it won't just work by itself.

So you either run their cd or you do it manually.

---

### Post by Yownanymous on 2008-12-01
> **billgoldberg said:**
> It's just their activation cd that won't work.

It's extremely easy to set that up yourself from a browser connected to the router.

On your sisters pc, go to firefox and go to your routers interface (it will most likely be [http://192.186.1.1](http://192.186.1.1)) and enter your info given to you by your ISP (username and password).

--

I guess they could cut you off if they want to. That being said, there is no way they'll do it (they would lose money and gain nothing).

I don't know why they don't just give instructions to do this manually if you use Linux. 

It's so easy, I don't get why they don't do it.

It works like this: Branson thinks "Surely if they don't make profit like I do, they should be ignored. Haha, money money money. What a silly idea to give things out for free..." Oh, and it doesn't just go for Branson, it goes for the vast majority of profit makers.

---

### Post by Astinsan on 2008-12-01
Comcast has a simalar issue too.. but you can call them on the phone and get setup. They don't have issues with linux. Linux isn't a large enough market share to warrant support. 

Cost is a big factor I am sure.

---

### Post by ecomoney on 2008-12-01
> Could have had them online with a phone call by now.
Having the Modem at your house wont be much good because it will only work with the registered account i believe.Legally anyway.

150?

Hi, Ive found virgin modems will work anywhere when they are moved and plugged in to an existing socket, even ones where the account has been disconnected. I wouldnt know about any "legalities" of this though.

If I had known about the 150 phone I may have used it, but I would really like to know how to bypass this without phoning them. Most of my clients are on extremely low incomes and I advise them not to take a phone line in case they run up a huge bill and get everything cut off. I put skype or Gizmophone on for them. Plus, most of my clients are new to linux and I dont want their first experience of it to be technical and off putting. If I can get them set up myself then they are much more likely to start their linux adventures with a positive view of it (which is why in the screenshot Ive got it dressed up as XP/IE7!!!!) - but that is a discussion for another thread.

---

### Post by xpod on 2008-12-01
> Hi, Ive found virgin modems will work anywhere when they are moved and plugged in to an existing socket, even ones where the account has been disconnected. I wouldnt know about any "legalities" of this though.

I`ll rephrase.
Having the modem at your house wont be much good for the account holder/customer:)

You dont need to call from 150 and can use 0845 454 1111 instead,although that will cost.

---

### Post by ecomoney on 2008-12-01
Thank you xpod, I will keep those numbers. I have the modem here so I can hack with it as I dont believe it matters from which connection its registered from...just what OS!!! The customers are online wirelessly and happy for the moment  (even though I had to throw in a free set of speakers!). If I cant get it to register then I will ring those numbers (this customer does have a landline as it happens) and do it the way you have helpfully suggested.

---

### Post by xpod on 2008-12-02
> I can hack with it as I dont believe it matters from which connection its registered from...just what OS!

It`s actually the other way round.

The only real reason i kept my XP install around was for Virgins benifit.
Not because of *getting* online but because of some of the terrible service(speeds etc) once online.
I`d always start a call with *buntu of course and i`d argue the point till i was blue in the face.9 times outta ten though i`d have to eventually admit defeat and go get XP connected directly to the modem.

I had some fun & games on that phone back then and even had one Tech Support chap promise he was off to download Ubuntu after i`d hung up.
He had heard of it but never had any dealings with Linux,or indeed Linux users,until then.:)
Thankfully i`ve not had any reason to call Virgin for quite some time,other than to get our new Modem registered & connected when we moved house just recently.:)

---

### Post by andras artois on 2008-12-02
I've got virgin and as far as I can tell they only need to setup the internet connection, nothing actually needs to be done to the computer. When my internet connection was first put in we had one computer since then we got another 4 laptops and the original computer's OS was wiped. Everything works fine and it's all wireless.

EDIT: the install CD was used on the first computer but that got wiped and none of the other computers have used it sooo.....

---

### Post by xpod on 2008-12-02
> I've got virgin and as far as I can tell they only need to setup the internet connection, nothing actually needs to be done to the computer. When my internet connection was first put in we had one computer since then we got another 4 laptops and the original computer's OS was wiped. Everything works fine and it's all wireless.

EDIT: the install CD was used on the first computer but that got wiped and none of the other computers have used it sooo.....

The only Virgin Broadband service that required faffing about each time you used a different computer was the Set Top Box BB.I dont even think that new customers get any STB BB services now although i could be wrong.
Without a router or cloned Mac being used any new machine connected to the STB required the user re-visiting the provisions page and registering the new Mac Address. 

With a Modem powered cocnnection though it`s just a case of rebooting everything.Unless it`s a new connection of course then the Modems Mac needs registered.

---

### Post by ecomoney on 2008-12-22
Just to let everyone know, I did get the line connected in the end. Taking no chances I rang them up and told them our customer had a broken CD drive, but I had heard they could register the MAC code from the back of the modem manually over the phone. A minute later it was connected.

Personally I think that, as well as the lower "market share" (as they think of us, it is as much to do with the registration procedure and the "toolbar" installation/homepage that they insist on you completing. On linux this stuff wont work. Hope they arnt trying to do what Similar to the [sony rootket?](http://en.wikipedia.org/wiki/2005_Sony_BMG_CD_copy_protection_scandal). They are a record company first and foremost. What with the current measures they have instigated against filesharing, and our many customers that we have that have told us about their bank accounts being emptied (or worse) via "erroneous" direct debits, we are seriously thinking about not recommending them in the future.

---

### Post by OrbJinzo on 2008-12-22
My ISP TimeWarner (Roadrunner) has a stance they dont care what you use no activation CD no nothing just a plugin and go service. I just hate there help line for other stuff i have with em...

---

### Post by Listen2TheTruth on 2008-12-22
Read this post before it gets deleted and my account suspended.

I guess there will always be people who can look at gold and throw it away and think its "fake" or "can't be" or "im an ignorant moron". Pick one of the above im pretty sure you are right up there with any of the above described. 

Ok to clarify. I've build and been using an HHO system in my car for the past 6 months. If anyone can tell you about results, its not a oil lobbied PhD holder, a fake scientist or a opinionated freak who is so paraniod thinking his birth is a conspiracy, no..but someone like me- a regular consumer who has used it and loves it to death!

I drive a volvo that gets 31 MPG HWY with my HHO system off, 53MPG HWY with it on. Any questions? Didnt think so! 

Besides some of you (removed by moderator) forgot that Hydrogen can be extracted from water using electroalysis with solar panels, windenergy etc. so although the extraction process may not be 100% efficient, it sure as hell can be "FREE" if we choose to. 

Oil requires a hell lot of energy to obtain too. Researching, Drilling, Extracting, destilling etc...look at all the processes that it has to go through before it can be made available as a combustable gas. Do some research before you post your ignorant, nonsensical opinions on a topic you have no idea about! 

Do a google search on zero point energy or zero field energy, a guy in kansas invented a device that produces more energy (output)than the energy put into the system to extract it (input). Thats the future of energy "creation" and if you are one of those misleading, good-for-nothing opinionated pinheads thinking "oh matter can neither be created nor distroyed - i learned that in High School...waahhh waahhhh cryyy cryyy" then all i have to say is "you have been living on the moon" for science and technology is a dynamic world and it changes every nanosecond of your existence! So get with the plan and stop being ignorant and crying about a solution that really works!

Lastly, watch ZEITGEIST 1 + 2 and be changed forever.

---

### Post by Astinsan on 2008-12-29
> **ecomoney said:**
> Just to let everyone know, I did get the line connected in the end. Taking no chances I rang them up and told them our customer had a broken CD drive, but I had heard they could register the MAC code from the back of the modem manually over the phone. A minute later it was connected.

Personally I think that, as well as the lower "market share" (as they think of us, it is as much to do with the registration procedure and the "toolbar" installation/homepage that they insist on you completing. On linux this stuff wont work. Hope they arnt trying to do what Similar to the [sony rootket?](http://en.wikipedia.org/wiki/2005_Sony_BMG_CD_copy_protection_scandal). They are a record company first and foremost. What with the current measures they have instigated against filesharing, and our many customers that we have that have told us about their bank accounts being emptied (or worse) via "erroneous" direct debits, we are seriously thinking about not recommending them in the future.

I don't think that is what they are trying to do. It is probably more or less about training people to do this over the phone.  Anyone who has worked in a call center will tell you that the turn around is almost constant. [lets face it.. support calls are not all going to be worm) If it was about giving you the eula.. you already have it from when you had the cable installed. They also like to hide it on the back of billing invoices marked with "disclosure".

---

### Post by uberdonkey5 on 2008-12-29
wow, I got exactly that rubbish when I swapped to ubuntu. Basically many internet service providers are the cheapest staff they could employ and just know about their cute little disk they pass out.

---

### Post by Sealbhach on 2008-12-29
my router actually runs on Linux, my ISP had to publish the fact under the terms of the GPL.

[http://www.btyahoo.com/broadband/adhoc_pages/gplcode.html](http://www.btyahoo.com/broadband/adhoc_pages/gplcode.html)

Most routers probably run on Linux.


.

---

### Post by ajcham on 2008-12-29
> **Sealbhach said:**
> my router actually runs on Linux, my ISP had to publish the fact under the terms of the GPL.

[http://www.btyahoo.com/broadband/adhoc_pages/gplcode.html](http://www.btyahoo.com/broadband/adhoc_pages/gplcode.html)

Most routers probably run on Linux.


.

Mine too - I have a D-Link.

And unlike BT, who dragged their heels a bit over what code they had to release, D-Link appear to have gone above and beyond the requirements of the GPL.  As I understand it, the GPL only requires them to provide the source for software actually intsalled on the router, but they also provide a load of alternative kernels so that it can be compiled for different architectures (i386, x86_64, ppc, ARM, Sparc and many more).

---

### Post by Cfossy2 on 2011-04-14
> **nandasunu said:**
> OK, so I got my sister to switch to ubuntu a while back but she had no internet connection at the time. She is getting internet from Virgin Media on Friday, but they say that they don't support linux and so won't set up her internet connection unless she is running windows or mac (at least that seems to be the jist of it).

I think what they mean is that their crappy activation cdrom doesn't work with linux so they are brushing her off.  

My point of this message is that I am pretty sure that once her internet connection is active it will work with ubuntu, but is there a possibility that it won't? Maybe the router they provide is not linux compatible? I am going to have to reinstall windows on her pc so they will activate her connection, but is it worth doing a dual boot if the internet won't work?

Does anyone here use Virgin Media (previously NTL/Telewest)? Does it work for you?


I use Virgin Mewdia, and found on the net a guide to get the Virgin Media to respond using a few cli commands to get the virginmedia to see \Firefox in Linux as a Internet Explorere Here is the URL for the blog:
[http://www.ecalpemos.org/2010/04/how-to-activate-virgin-media-broadband.html](http://www.ecalpemos.org/2010/04/how-to-activate-virgin-media-broadband.html)  This link should be able to be pasted into your browser.



Hope this helps !![http://ubuntuforums.org/images/smilies/icon_smile.gif](http://ubuntuforums.org/images/smilies/icon_smile.gif)
Thanks.
 
Cfossy.

---

### Post by Elfy on 2011-04-14
Closing old thread

---

