---
title: "A Sad Day for my Ubuntu Laptop"
date: 2010-03-01
forum: Testimonials &amp; Experiences
---

### Post by plurworldinc on 2010-03-01
Today I started college and was thrilled to pick of my education in computer forensic. I can say I am looking at this as a new chapter in my life to try something new and increase my addiction for computers. My first class was easy a basic Microsoft refreshed course just to get me started. For the most part I had a very relaxing day, well until I got to the Commons and tried doing a little homework on my computer. I sat with comfort and booted up Ubuntu. I even notices another student glancing over my shoulder, so I thought I would give him a little compiz to watch his eyes open with amazement (they did). 

   Now my campus offer wifi and I thought it would be nice to e-mail my wife to tell her how my first day was going. I connected to the schools wifi, opened my browser and was greeted with the most unfriendly message I have ever read. My OS was not supported by the schools systems and I would not be able to go on-line. Now normally this wold not be a major problem I would just simply not use the wifi. But since this was a school for computer training i must bit my tongue and dual boot.

   So right now I am going to try once again to dual boot my computer and hope everything works this time around. I have never had a good dual boot yet, but everyone around me has. I have dual booted a number of my friends computers but could never get mine to work the way I want it to work. So fingers crossed this evening and i hope to have my laptop up and running in a few short hours if all is well.

  On the bright side, I still have my multi screen system running Ubuntu 9.10 and a netbook doing the same. I just wish to have all of my computer on the same OS to make my life a little easier in the long run.

---

### Post by Chris_cur on 2010-03-01
OUCH!  I am sorry friend!

I had a little issue with setting up my internet at the University at first but I got it quickly settled.  Are you sure you can't jump on the WiFi?  Surely some one over in IT can help you.

---

### Post by uRock on 2010-03-01
That bites. I am taking Internet Forensics right now. We only use Linux apps for labs. The good side is that I do all my classes on line. Next time I go in to see my Cisco teacher, I will see if the school allows wireless Linux there. You should see your IT department and try to get in MSDNAA and get your free copies of MS, then you can boot in a VBox easily. I am not sure how the IP stack works with VBox, but if that would work, then it would save you from having to play with Grub.

If you need help with your install, please feel free to PM me or start a thread and PM the link to me. 3 out of 4 of my systems are dual booting Windows and Ubuntu.

---

### Post by mastablasta on 2010-03-02
whaaa? the OS on computer decided if you can or can't connect to internet? how is that? i never heard of it before. what kind of configuration are they running?

---

### Post by kg4cna on 2010-03-02
That doesn't sound right.  How can the university system determine what os you're using and block it from connecting to the wireless?  As far as I know, wi-fi is not os dependent OR am I missing something?

---

### Post by M1ke on 2010-03-02
> **kg4cna said:**
> That doesn't sound right. How can the university system determine what os you're using and block it from connecting to the wireless? As far as I know, wi-fi is not os dependent OR am I missing something?
 
It's almost certainly the university firewall rather than the wireless standard itself; perhaps similar to the way a website can log which browser you're viewing it with. We've all seen those "Your IP address is X! You are viewing this page with Y and running Z!" (where Y and Z are your browser and OS respectively) signature images on forums.
 
In which case surely anything that can be ID'd, can be spoofed..?

---

### Post by DexterLB on 2010-03-02
> **M1ke said:**
> It's almost certainly the university firewall rather than the wireless standard itself; perhaps similar to the way a website can log which browser you're viewing it with. We've all seen those "Your IP address is X! You are viewing this page with Y and running Z!" (where Y and Z are your browser and OS respectively) signature images on forums.
 
In which case surely anything that can be ID'd, can be spoofed..?
spoofing your OS ID... I think no one's tried that before :(

---

### Post by DexterLB on 2010-03-02
> **DexterLB said:**
> spoofing your OS ID... I think no one's tried that before :(
Why not try setting a Mac mac address? It's a long shot but maybe the system will check it first and think that you're using apple... although unlikely.

---

### Post by M1ke on 2010-03-02
> **DexterLB said:**
> spoofing your OS ID... I think no one's tried that before :(
 
Don't even know if it can be done! I just figured if it's possible to get an addon for your browser to spoof that much, maybe you can take it a step beyond and do the way the OS identifies itself when queried.
 
For all I know it can't even be done, I'm just thinking aloud :)

---

### Post by mastablasta on 2010-03-02
he said it is not supported. this can not be IMO. 
 
It could eb that it is blocking certian OS, but not that it is not supported. Unless you are using some USB encription signature to sign in. in which case your programe is not supported and not the os. like for example at my bank. i can not connect to them via Linux, because the connection programe and the programme that reads the key only runs on MSWin. linux can read the chip but it doesn't udnerstand it.
 
again in this case maybe it is possible for you to use Wine.

---

### Post by armandh on 2010-03-02
re installing and dual booting
BACK UP your stuff first!!!!!!


if your going to reload the original OS remember factory reloads are usually not an install rather a hdd wipe and copy.

win [at least xp] likes to be in the first primary partition ONLY.

I have had the best luck with first restore then reducing the partition, and then installing Ubuntu to the "largest unpartitioned space"

---

### Post by plurworldinc on 2010-03-02
> **mastablasta said:**
> whaaa? the OS on computer decided if you can or can't connect to internet? how is that? i never heard of it before. what kind of configuration are they running?

Yes, i still don't get it myself. When I opened my browser i was greeted with a note that told me i couldn't connected to the schools servers. It then gave the reason my operating system was listed as untrusted. I thank when i go to school next I am going to ask the IT department is there anything I could do beside dual booting.

  I really don't have a huge problem with dual booting at all. I thank it's a great way to get the best of both worlds. But in my case I have limited hard drive space on my laptop and I really don't want to give up space and worry about Windows.

---

### Post by Chris_cur on 2010-03-02
Good luck bro,

Keep us informed.   I personally detest dual booting. Especially when, as *armandh* said, Windows like being the first and primary option.

---

### Post by plurworldinc on 2010-03-02
Well I just finished my first successful dual boot and I guess I am happy with it. I just used the WUBI ( don't quote me on that I could be wrong about the name) and everything went smoothly this time around. The only thing I didn't like was, I was only able to use 30gig of my hard drive. I would have preferred to give Windows 40gigs of my hard drive for school and keep the rest Ubuntu since that is my primary OS. Well since it's for school i will use Windows with Linux until I graduate.

---

### Post by uRock on 2010-03-02
> **mastablasta said:**
> he said it is not supported. this can not be IMO. 
 
It could eb that it is blocking certian OS, but not that it is not supported. Unless you are using some USB encription signature to sign in. in which case your programe is not supported and not the os. like for example at my bank. i can not connect to them via Linux, because the connection programe and the programme that reads the key only runs on MSWin. linux can read the chip but it doesn't udnerstand it.
 
again in this case maybe it is possible for you to use Wine.

Every OS has its traits within its IP stack, which can be detected by the router. It is sad that they would block this, but maybe all it took was one bad egg to spoil it for everyone. They may have had a student running Back|Track and using it to attempt a penetration of the school's servers or other students' PCs. That could be the reason.
Whatever the reason the school owns their network and they can do what they want.

---

### Post by ninjamaster945 on 2010-03-02
Since they're blocking your laptop through the browser, it may be possible they are simply checking the user agent of your browser. If you are using firefox, this addon may be worth a shot. [https://addons.mozilla.org/en-US/firefox/addon/59]("https://addons.mozilla.org/en-US/firefox/addon/59") After you install that, you would just change it to say it's Internet Explorer. Good luck!

---

### Post by lisati on 2010-03-02
> **ninjamaster945 said:**
> Since they're blocking your laptop through the browser, it may be possible they are simply checking the user agent of your browser. 

That sounds likely to me too. If it was some kind of OS-based signature or something based on the MAC address, there probably wouldn't be a connection and the browser wouldn't show a web page.

---

### Post by SonicSteve on 2010-03-02
> **plurworldinc said:**
> 

   Now my campus offer wifi and I thought it would be nice to e-mail my wife to tell her how my first day was going. I connected to the schools wifi, opened my browser and was greeted with the most unfriendly message I have ever read. My OS was not supported by the schools systems and I would not be able to go on-line. Now normally this wold not be a major problem I would just simply not use the wifi. But since this was a school for computer training i must bit my tongue and dual boot.

   .


What kind of crazy network admin would allow Microsoft computers on a network and not Linux? I run a school network and I have the exact opposite policy. Windows is like a milkbone biscuit in a world of hungry virus wolves. I do everything I can to keep the student laptops off the network. The only thing I would give them is access to internet, nothing on the local LAN.  I can't think of one good reason to limit a network to Windows only.

---

### Post by plurworldinc on 2010-03-02
now the way i have been viewing this problem was thought the eyes of a newbie. The only reason I could thank this was happening to me was that Linux gives you total control of your system rather then rent your system out to you. With Microsoft you are some what renting an OS to use, while with Linux you are the owner and have all the power in the world to do whatever you want to do with your OS. I am trying to tell myself, it's to much power given to a single user on a system. 

   But on the other hand it would be nice to be able to just check my e-mail and surf the net with out installing Windows. It's not like I have a problem with Windows, but I just don't trust it. I guess I am just afraid of getting a virus or something along those lines. I just don't want to waste time buying anti spyware software because I never needed it with Linux and it's just money being throw away.I know it's a part of the Windows world , but not LINUX!

---

### Post by mastablasta on 2010-03-03
> **plurworldinc said:**
> I just don't want to waste time buying anti spyware software because I never needed it with Linux and it's just money being throw away.I know it's a part of the Windows world , **but not LINUX**!
 
which is not entirely true, but ok. ;)

---

### Post by DawieS on 2010-03-03
> **plurworldinc said:**
> My OS was not supported by the schools systems and I would not be able to go on-line.

IMO, this behavior is totally unacceptable, and may be regarded as illegal. The school has no right to decide on your behalf which Internet browser you may, or may not use, let alone the operating system supporting it, as long as it keeps to the well laid down and accepted standards. This is yet another ploy from Microsoft to protect its market share at all costs.

In the past it was only Microsoft that deviated from previously accepted standards, in what was regarded by its competitors as a deliberate move to catch them off guard, and make their products unusable.

Mainly due to this kind of monopolistic behavior, Microsoft has already paid fines worth about 1.7 billion Euro's. They are now forced in Europe, to provide their users with a choice of 12 other free Internet browsers, with their next update. For more information, read _**[this]("http://mybroadband.co.za/news/Software/11638.html")**_ article.

In my personal experience, about 2 years ago when I was still using XP, I was using Opera Internet browser and found that Opera sometimes suddenly aborted after I received the "We're sorry for the inconvenience.." message while browsing my favorite website. I then got into the nitty-gritty of things and traced the cause to be Microsoft advertisements run by Google on this website. These advertisements only stopped after I threatened the website-owner with legal action, due to his website distributing malicious software causing acts of sabotage.

If I were you, I would formally approach the school, disputing this so-called "incompatibility" and request the standards to which your browser is not compatible to. If that does not help, I would then set up an action group, and even organize demonstrations, where you can officially hand over your grievances to the authorities. Be sure to invite the press as well!

I must admit, that it was a brilliant marketing move by Microsoft, to supply all our local schools with their "free" software, and thereby brainwashing our children into believing that it is the only acceptable operating system to use.

---

### Post by mastablasta on 2010-03-03
> **DawieS said:**
>  
Mainly due to this kind of monopolistic behavior, Microsoft has already paid fines worth about 1.7 billion Euro's. They are now forced in Europe, to provide their users with a choice of 12 other free Internet browsers, with their next update. For more information, read _**[this]("http://mybroadband.co.za/news/Software/11638.html")**_ article.
 
 
yeah about this... most of offered borwsers appear to be some sort of IE versions.
see this article from BBC: [http://news.bbc.co.uk/2/hi/technology/8545237.stm](http://news.bbc.co.uk/2/hi/technology/8545237.stm)
 
what will they come up next. they already took over our e-banking, then the administration units, e-taxes...
 
well for public services the professors and intelectualls protested last month and demanded action from government to open all browsers. it is under review.... so hopefully they will implement changes that will allow to do things with other browsers.

---

### Post by uRock on 2010-03-03
> **DawieS said:**
> IMO, this behavior is totally unacceptable, and may be regarded as illegal. The school has no right to decide on your behalf which Internet browser you may, or may not use, let alone the operating system supporting it, as long as it keeps to the well laid down and accepted standards. This is yet another ploy from Microsoft to protect its market share at all costs.

How could they be breaking a law? They most likely own the routers and servers that provide the school's service. Getting to connect wirelessly is a privilege, not a right.:)

---

### Post by DawieS on 2010-03-03
> **iRock said:**
> Getting to connect wirelessly is a privilege, not a right.:)
There is no such thing as a free lunch. All services provided by schools and universities, are paid for by tuition fees, as well as taxes from you and me, at the end of the day. The school is happy to accept the tuition fee, yet now has a problem in delivering the service for some obscure reason.

Would you regard it legal if your money was accepted at a toll gate, yet you are turned back at the gate just because you are driving an Alfa Romeo, and are now crossing into Ford country?

---

### Post by uRock on 2010-03-03
> **DawieS said:**
> There is no such thing as a free lunch. All services provided by schools and universities, are paid for by tuition fees, as well as taxes from you and me, at the end of the day. The school is happy to accept the tuition fee, yet now has a problem in delivering the service for some obscure reason.

Would you regard it legal if your money was accepted at a toll gate, yet you are turned back at the gate just because you are driving an Alfa Romeo, and are now crossing into Ford country?

It is up to their IT team to decide what is best for the school. Linux has a lot of free penetration tools and they may have had students who are learning the network security trade there who tested their talents against the school's network.

With your analogy in mind, do you think it is right that heavy haul tractor trailor drivers are not allowed to drive during rush hour nor on Sundays in many states? Said companies pay a lot more for their taxes than us car drivers yet, we are not limited in that manner.

---

### Post by Ghost|BTFH on 2010-03-03
> **iRock said:**
> It is up to their IT team to decide what is best for the school. Linux has a lot of free penetration tools and they may have had students who are learning the network security trade there who tested their talents against the school's network.

Your tuition pays for you to have access.  If you have a working computer that *can* access the network in a reasonable way, they *have* to allow you access - or provide you with an alternate access solution.  They cannot deny you access without recourse.  As a paying student, you have equal rights for access, just as any other student does.

But here's a simpler way of looking at this - if they allow Macs (And what university wouldn't?), they essentially allow BSD, thus they should allow Linux.  Since Mac OS X is POSIX compliant, many software packages written for the *nix, BSD's or Linux environments can be recompiled to run on it.

Ergo, the same risk factor that Linux would inherently have on their network, Macs have.  Therefore, in all fairness, if they continue to refuse access to Linux, they should remove all Mac access as well.

That would be a solid and logical argument that could be taken up with IT, the Student Council and the Dean of Students if necessary.  However, I've found most of the times, one polite conversation with the powers that be (ie, IT staffers) and the problem simply "goes away" for you.

Cheers,
Ghost|BTFH

---

### Post by uRock on 2010-03-03
It is the school's network, they can do what they want. I am sure that if one walked up to the dean and asked, he could easily say that your tuition only covers paying for the class and nothing more. Maybe some simple talk with the IT department could open the door for Linux, maybe not.

Hopefully the OP can use the add-on mentioned earlier to get his Firefox to connect.

---

### Post by lisati on 2010-03-03
> **mastablasta said:**
> which is not entirely true, but ok. ;)
+1. 
I "need" AV software on my server which runs Ubuntu, even though malware doesn't come with the same risk to my Ubuntu installations as it would with Windows, because (a) it helps keep my ISP happy, (b) I have Windows installations on my network which I don't want to mess around with fixing and/or reinsalling, (c) some of my non-tech-savvy in-laws sometimes bring infected media devices for me to get files from, and (d) transmitting malware from my Ubuntu installations, accidentally or otherwise, isn't a very nice thing to do.
> **iRock said:**
> It is the school's network, they can do what they want.
I agree. Sometimes the rules imposed by others don't seem to make sense at first, and fostering a good relationship with those who set the rules is always a useful exercise. Whatever the OP decides, it will good to make sure that it doesn't come back and cause problems later.

---

### Post by DawieS on 2010-03-03
> **iRock said:**
> It is up to their IT team to decide what is best for the school.
If you take a closer look in our local environment, you will find that in most cases these decisions are NOT taken by the IT teams, but by somebody higher up, who has accepted the "free lunch", and now has to deliver on the promises made.

Any reputable IT team would rather recommend Linux, purely from the viewpoint of virus infections, which seem to waste most of their valuable time. Just the other day I had the pleasure of recovering some important data off a local PC, that was infected with +600 instances of +80 different species of trojans and viruses, and which their IT experts was unable to recover. The virus scanners themselves were infected, and contributed towards spreading! Ubuntu 9.10 Live CD came to the rescue!
 > Linux has a lot of free penetration toolsThere are even more Windows-based malicious tools out there. However, should a student prefer to use Linux for some malicious activity, it would anyway be easy for him to provide the server with the login credentials that it wants to hear, in order to gain access.

It is unfair to decline access to the majority of well meaning honest students, who may have some pride in their Linux installations, and now feel rejected and branded as unwanted. 

The overall security of the school network should in all instances conform to the highest standards, regardless of the operating systems used. If this is achievable in normal business environments, it should be possible at schools as well.
> With your analogy in mind, do you think it is right that heavy haul tractor trailor drivers are not allowed to drive during rush hour nor on Sundays in many states?I would agree with this, but I would rather compare a Mozilla Firefox browser, well secured and enforced by apparmor, and equipped with Adblok Plus and Noscript, to a Ferrari or a Porche, instead of a heavy haul tractor trailer.:grin:

---

### Post by uRock on 2010-03-03
> **DawieS said:**
> If you take a closer look in our local environment, you will find that in most cases these decisions are NOT taken by the IT teams, but by somebody higher up, who has accepted the "free lunch", and now has to deliver on the promises made.

Any reputable IT team would rather recommend Linux, purely from the viewpoint of virus infections, which seem to waste most of their valuable time. Just the other day I had the pleasure of recovering some important data off a local PC, that was infected with +600 instances of +80 different species of trojans and viruses, and which their IT experts was unable to recover. The virus scanners themselves were infected, and contributed towards spreading! Ubuntu 9.10 Live CD came to the rescue!
 There are even more Windows-based malicious tools out there. However, should a student prefer to use Linux for some malicious activity, it would anyway be easy for him to provide the server with the login credentials that it wants to hear, in order to gain access.

It is unfair to decline access to the majority of well meaning honest students, who may have some pride in their Linux installations, and now feel rejected and branded as unwanted. 

The overall security of the school network should in all instances conform to the highest standards, regardless of the operating systems used. If this is achievable in normal business environments, it should be possible at schools as well.
I would agree with this, but I would rather compare a Mozilla Firefox browser, well secured and enforced by apparmor, and equipped with Adblok Plus and Noscript, to a Ferrari or a Porche, instead of a heavy haul tractor trailer.:grin:
Read my last post. They own the network and they will most likely tell you that your money pays for your classes and not their network. They will also tell you that you are welcome to use their computer lab to do your schoolwork. Who even said the OP was going to a state or community college? Your taxes don't pay for private schools such as ITT Tech, Randolph-Macon, Liberty University, just to name a few.

---

### Post by DawieS on 2010-03-03
> **iRock said:**
> Your taxes don't pay for private schools such as ITT Tech, Randolph-Macon, Liberty University, just to name a few.
Sorry, but in my country there is not a single educational enterprise, however private it may be, that does not get some kind of state subsidy.

---

### Post by leclerc65 on 2010-03-03
> Hopefully the OP can use the add-on mentioned earlier to get his Firefox to connect.
I'd just tried that, I had to remove it right away because my Chromium-Browser stopped working (at home).
I have the same problem as the OP, with the free public wifi in Montreal downtown.

---

### Post by plurworldinc on 2010-03-05
Update...



   Well I was able to dual boot system, yah ( it worked )

  In the end I went with Ubuntu Ultimate Edition just because it seemed to work a little better with the install I was trying to go for. I mainly wanted my system to remain mainly Linux with 30% set aside for school. I thought that would be enough room, but only time can tell.

   One thing I was really surprise about was after doing all of the updates and getting my Ubuntu just the way I wanted. I restarted my laptop and walked away for a moment, Ubuntu popped up first leaving Windows at the very bottom of the Grub list. So i am thrilled with that because I would hate to have to wait to find Linux every time I start my computer.

  Well that's all for now, i would still like to figure out how to make the grub look a little better, but that's no big deal, it still looks very professional the way it is.:p

---

### Post by solitaire on 2010-03-05
OK Sounds like they are looking at the browsers "User Agent" setting (it states what OS the browser is running on)

Start Frirefox, go to Tools, Addons, then search for "User Agent Switcher"
install it and set it to "windows 7 IE8" (or another Windows version) then you should be fine..

---

### Post by Brightneon_Latte on 2010-03-05
> **plurworldinc said:**
> Update...



   Well I was able to dual boot system, yah ( it worked )

  In the end I went with **Ubuntu Ultimate Edition **just because it seemed to work a little better with the install I was trying to go for. I mainly wanted my system to remain mainly Linux with 30% set aside for school. I thought that would be enough room, but only time can tell.

   One thing I was really surprise about was after doing all of the updates and getting my Ubuntu just the way I wanted. I restarted my laptop and walked away for a moment, Ubuntu popped up first leaving Windows at the very bottom of the Grub list. So i am thrilled with that because I would hate to have to wait to find Linux every time I start my computer.

  Well that's all for now, i would still like to figure out how to make the grub look a little better, but that's no big deal, it still looks very professional the way it is.:p
Is there something as Ubuntu Ultimate Edition?
j/k, just pointing a funny mistake in there :D

---

### Post by uRock on 2010-03-05
Google it. It exists. [Created by a third party.]("http://ultimateedition.info/")

---

