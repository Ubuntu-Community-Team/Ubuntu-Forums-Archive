---
title: "Hack me."
date: 2008-05-21
forum: Security
---

### Post by kaffemonster on 2008-05-21
On a danish news site, citing [this]("http://computerworld.com/action/article.do?command=viewArticleBasic&articleId=9073258&intsrc=hm_list") article, a discussion arose. Did the laptop running Ubuntu survive because Ubuntu is a more secure OS than OSX and Vista, or because the hackers spared it?

In stead of jumping into the usual web forum flamewars, I decided to challenge them...

A standard PC has a fresh install of Ubuntu 8.04 LTS. It has gotten the updates that popped up in update manager, otherwise it is untouched. No measures have been taken to protect it. 

The pc is sitting behind a router. Nothing fancy, just a router designed for home use. No measures have been taken to protect the router other than changing the admin password. This router is on a standard ADSL with the IP adress 83.95.212.118

There is a single user account on the pc, as it is a "virgin" installation. The first person to leave a .txt file with contact info (name/nick and e-mail) on this users desktop will be declared the winner of this little challenge.

Bring it on, hack me.

UPDATE 05/27/08:
Joe Bloggs is now using the computer. 

The router thingymajig that his friend set up confused him, so he's now plugged directly into the DSL line at 83.95.212.118

He uses an email client for downloading his mail via Pop3. He happily posted his new e-mail address in a discussion forum: [email]ubuntujoe1337@gmail.com[/email]

One of these days he might even install flash so he can visit Youtube. His friend told him it has funny videos. Joe likes the funny.

---

### Post by yopnono on 2008-05-21
Were they using routers on the hacking contest? You see a router gives you some protection. Plug it directly to the internet.

---

### Post by kaffemonster on 2008-05-21
Nope, I don't think they were - I'm trying to do a common, end-user setup scenario. 

Will leave the router on for 48 hours from now, then plug it directly to the intarweb :)

---

### Post by Monicker on 2008-05-21
I had read somewhere that the person who hacked the Mac admitted to going into the contest with the specific goal of compromising it.  Personally, I think that most of the people who took part in this contest were more interested in hacking the Mac and Windows boxes first.  These are some very talented people and I think they would have gotten the Ubuntu machine if they had focused on it.

I'll have to dig up a link for where to back up my first sentence.

---

### Post by moonpup on 2008-05-21
Hi,

The test you are conducting above has an unreal expectation. First off, if you are not forwarding any ports from the router to the Ubuntu box, then all you are asking people to do is hack at your router.

To make this a real test, you need to remove the router from the picture or at least put the Ubuntu box in the dmz section of the router so that is out on the internet, otherwise this test is useless.

Put the box out publicly on the internet and run some services.

---

### Post by Dr Small on 2008-05-21
First off, I can not connect. What services have you opened? Apache, SSH ?

Because the real hack would be finding a flaw in the service rather than the system itself.

---

### Post by moonpup on 2008-05-21
Exactly my point above... put the Ubuntu box in the dmz of the router or connect it directly to the internet.

---

### Post by kaffemonster on 2008-05-21
Everybody always claim they don't need no firewall when behind a router, only to have someone tell them that at router offers no protection. I thought I would test this...

Will remove router tomorrow and note that "Routers scares hackers away" :D

---

### Post by robertchahine on 2008-05-21
good luck guys :D

---

### Post by ASULutzy on 2008-05-21
Is this a clean Ubuntu install with absolutely no ports open?

IMO you should make it a more "typical" setup and get ssh going, maybe an apache webserver, VNC server, something. Or else you're just asking people to bang their heads off a wall

---

### Post by Titan8990 on 2008-05-21
Is your IP static? The address given isn't even up ATM as I can't even ping it.

---

### Post by moonpup on 2008-05-21
My initial scan shows this...

 nmap -PN 83.95.212.118

Starting Nmap 4.60 ( [http://nmap.org](http://nmap.org) ) at 2008-05-21 16:16 EDT
Interesting ports on 0x535fd476.arcnxx18.adsl-dhcp.tele.dk (83.95.212.118):
Not shown: 1714 filtered ports
PORT     STATE SERVICE
5190/tcp open  aol

---

### Post by moonpup on 2008-05-21
My follow up scan shows this...

 nmap -PN -p 1-65535 83.95.212.118

Starting Nmap 4.60 ( [http://nmap.org](http://nmap.org) ) at 2008-05-21 16:23 EDT
Interesting ports on 0x535fd476.arcnxx18.adsl-dhcp.tele.dk (83.95.212.118):
Not shown: 65439 filtered ports, 93 closed ports
PORT     STATE SERVICE
4443/tcp open  unknown
5190/tcp open  aol
5566/tcp open  unknown

---

### Post by farruinn on 2008-05-21
All this talk about routers and services running... I think the only reasonable request would be to replicate the scenario from that article. Since the article didn't give many details that will be hard. It did mention, however, that on the first day the hackers were working against just the base system and could not rely on user actions. Later on in the contest additional software was installed and user actions were allowed.

---

### Post by yaztromo on 2008-05-21
I think your test is a good one. A typical usage scenario doesn't involve running services. Joe Bloggs has never heard of apache, ssh etc.

I vote you don't open services. If anyone here is worth their weight as a hacker they shouldn't need it making easy for them.

---

### Post by Dr Small on 2008-05-21
[quote=yaztromo]I vote you don't open services. If anyone here is worth their weight as a hacker they shouldn't need it making easy for them.[/quote]

Pardon me. I am a hacker, but without an access, there is no hacking. In order to hack the box, the system must be accessible via the internet. Without running any services or having any ports open, this system is not accessible.

Basically to hack the system, you must find a flaw in the service that is running, or bruteforce your way in. Either way, there must be a service. Without it, it is like walking around the courtyard of a castle that has no gate.

---

### Post by ASULutzy on 2008-05-21
> **Dr Small said:**
> Pardon me. I am a hacker, but without an access, there is no hacking. In order to hack the box, the system must be accessible via the internet. Without running any services or having any ports open, this system is not accessible.

Basically to hack the system, you must find a flaw in the service that is running, or bruteforce your way in. Either way, there must be a service. Without it, it is like walking around the courtyard of a castle that has no gate.

Yea, I'm a software developer for a living, and I think lots of people watch movies like "Hackers" or watch stuff about "crackers" on 60 minutes and see blacked-out silhouette shady characters talking about their "leet exploits"

If there's no ports open (which I believe is the case of a default Ubuntu install), you're not getting in. Don't you think if it were that easy to get in that no one would be running Ubuntu??

I mean heck, if there were a "hacker" good enough to break into a default Ubuntu install why wouldn't he just write a script that would break into everyone's Ubuntu's install? If it were possible, it'd be widespread.

install some services, leave some ports open, make it fun

---

### Post by yaztromo on 2008-05-21
Okay, of course I don't view hackers as shady shilouetts similar to some Fox News articles I've seen. I also realise that running services gives a determined hacker a lot more chance to find a flaw.

> If there's no ports open (which I believe is the case of a default Ubuntu install), you're not getting in.

I agree that open ports are the way in for hackers 99.9% of the time, I don't think anyone would dispute that.

My feeling is that having no open ports is not like having a room with no doors. Packets are still coming in to the system and the kernel has to look at them in some way, even if to just determine there is no service on the requested port. Since a directly connected machine will examine all data before disregarding it I still feel there are many things a skilled hacker can do to try and trip up a system with no services running.

---

### Post by Dr Small on 2008-05-21
There is ARP poisoning (which 2point0 knows more about than I do) and XSS. Both, I thought had to be done on the network end. Unless a port is open and a service is listening on it, an attacker can not get in, as far as I know.

Opening a port does not only increase the chance, but makes it possible to exploit or bruteforce. Otherwise, I don't think it is possible.

---

### Post by elianthony on 2008-05-21
> **kaffemonster said:**
> ...I'm trying to do a common, end-user setup scenario.

Everyone's asking for you to open up a port or run a service that might give them a vulnerability to exploit.  But then I read that no end user has ever heard of apache, or ssh.  Being as I know nothing of such things myself, my question is what would a typical end-user do to open up a whole to be exploited?  If there is something, then doing that to your machine would really make this a real-world test.  Wouldn't it ??

---

### Post by whoop on 2008-05-21
There is a way to bypass routers with all ports closed. A lot of people have services running behind a router firewall. bypass the router and you can access and therefore exploit those services.

---

### Post by ASULutzy on 2008-05-21
I think opening up ssh is something a typical user would do.
ssh allows you to remotely access your computer, it's something I use every single day at work.
apache is a webserver that allows you to host webpages on your computer, also very common.

There are less common things that could be opened, such as a VNC server, which like ssh allows you to remotely access your computer, but VNC allows for full graphical use, ie I can view my gnome session at home from my laptop.
Then of course there are less known services. I run GNUMP3d so I can listen to my entire music library at work even though it's all located on my home pc.

If there are no open ports, and the user is not doing anything, then you're not getting in.

In Windows, and more specifically older versions of IE, there were simpler ways to gain remote access. Netbios was open for viewing by default on older Windows distros. IE used to allow all sorts of horribly insecure active X controls. I remember it used to be possible to force a Windows user to download and install a trojan just by visiting a webpage. 

Ubuntu and linux in general is a whole nother ball game. It comes with no ports open by default, and the multiuser setup means that nothing that you as a normal user run is ever going to hurt anything more than your /home folder. (Unless you're an idiot and you're logged in as root)

If anyone can hack into a default Ubuntu install with no open ports that's behind a router, my hat's off to them; I don't think it's possible. My logic makes sense doesn't it? If it were possible to hack into an Ubuntu machine that had no open ports/services running, then why aren't all our machines compromised right now?

---

### Post by jrusso2 on 2008-05-21
> **ASULutzy said:**
> Is this a clean Ubuntu install with absolutely no ports open?

IMO you should make it a more "typical" setup and get ssh going, maybe an apache webserver, VNC server, something. Or else you're just asking people to bang their heads off a wall

I disagree it should be a default Ubuntu install with all the patches and security updates currently offered to bring it up to date.  SSH, VNC services,  Apache are not part of the default Ubuntu install.

They are correct about the router however its not a contest to hack the router.

---

### Post by Dr Small on 2008-05-21
> **jrusso2 said:**
> I disagree it should be a default Ubuntu install with all the patches and security updates currently offered to bring it up to date.  SSH, VNC services,  Apache are not part of the default Ubuntu install.

They are correct about the router however its not a contest to hack the router.
Just a reminder though, that with an default ubuntu install and with no serices running, there is zero to no chance of breaking in. I think breaking in was the point here, though.

---

### Post by whoop on 2008-05-21
> **Dr Small said:**
> Just a reminder though, that with an default ubuntu install and with no serices running, there is zero to no chance of breaking in. I think breaking in was the point here, though.

I seriously disagree. Services provide a more easy way to hack a system. With no services running it is still possible to hack a system, it's just much harder. You can for instance let the owner of the system do something stupid; tempting him/her to visit a rigged webpage with the target machine for instance.

---

### Post by Dr Small on 2008-05-21
> **whoop said:**
> I seriously disagree. Services provide a more easy way to hack a system. With no services running it is still possible to hack a system, it's just much harder. You can for instance let the owner of the system do something stupid; tempting him/her to visit a rigged webpage with the target machine for instance.
That would require social engineering, not hacking. Please provide sufficent evidence that it is possible to hack a system that is without any services. As of yet, I have seen no examples nor know of any.

It is possible to hack a system without services, only if physical access is to be had on the system.

---

### Post by whoop on 2008-05-21
> **Dr Small said:**
> That would require social engineering, not hacking. Please provide sufficent evidence that it is possible to hack a system that is without any services. As of yet, I have seen no examples nor know of any.

It is possible to hack a system without services, only if physical access is to be had on the system.

Me thinks social engineering is a part of hacking. 
I think it's quite simple: if all ports are closed you cannot access the system directly, unless there is some flaw in the technology that is keeping the ports closed. In the situation of "all ports closed" the preferred method is accessing the system from the inside out. Hacking from the inside out often requires some social engineering. Especially when you have a specific target.
It often does not even require direct communication. Somebody could even post a link in this thread, hoping that the target system will visit it.

Hell, you can even open up ports of a router/firewall with some html/javascript code...

---

### Post by jrusso2 on 2008-05-21
> **Dr Small said:**
> There is ARP poisoning (which 2point0 knows more about than I do) and XSS. Both, I thought had to be done on the network end. Unless a port is open and a service is listening on it, an attacker can not get in, as far as I know.

Opening a port does not only increase the chance, but makes it possible to exploit or bruteforce. Otherwise, I don't think it is possible.

Thats why the first day no one hacked any of the operating systems.  It was not until other applications were added that they were hacked.  

A known unfixed exploit in safari was used which the hacker had set up an exploit on his website to exploit this vulnerability that he knew about in advance.

---

### Post by The Tronyx on 2008-05-22
I haven't port scanned anything, but based upon what I have read here is the deal:

To hack a system that 100% has no ports facing the internet i.e. open, it needs to be an application or client-side exploit.  For example, I would need to get you to visit a malicious website that could hijack your browser and somehow allow me to execute arbitrary code on your box.

Would that make it hacking or just user stupidity in clicking unverified links? (This was how the Mac was compromised, via a client-side browser exploit, probably related to [http://secunia.com/advisories/29483/](http://secunia.com/advisories/29483/)  Careful, might be an obfuscated URL and I just ninja'ed your computurz! just kidding, click it)

Secondly, let's say you did open SSH on your box and/or router, why in God's name would anyone publish a remote no-auth access exploit?  1) that exploit can be sold for BIG money, 2) that exploit could be used to compromise much more valuable systems.  Any cracker that manages to find an exploit of that magnitude either sells it or keeps it locked down and very private.

Unfortunately I believe your expectations of proving your system (in)security are unrealistic.  The fact of the matter is that no one really cares about rooting a home user's box, the real targets that people look for are misconfigured virtual hosts, vulnerable PHP code, improperly handled CGI scripts and countless more.  You don't have any PHP code to exploit if you have a stone cold "virgin" install, see where this is going?  For the most part, the only people that hit up desktop machines are botnet herders looking for (usually) machines that can easily be identified as vulnerable or talentless children who just got their hands on Metasploit.  This goes back to my original point, if you have no services to exploit, then the attack is reliant on your own stupidity or tricking you into installing a malicious package or getting you to run an application which will allow a hostile attacker to gain control of your system.  In this case, your scenario is simply not condusive to a head on attack.

Then there is a question of how you define being hacked.  A DDOS can knock your connectivity but it isn't rooting the system, so is it 'less' of a hack?  Surely if you define a malicious hack as a disruption of any normal service or system function then a DDoS attack is legitimate.  If you define it as someone being able to root your desktop, not to sound rude...but who cares?

And to answer your other question about pwn2own and why no one hit the Ubuntu box...well, the other machines were Vista and Mac.  Vista is known to be insecure and the Mac...it's a mac, again, who cares?  As *nix servers make up a significant portion of the internet backbone, an attacker would be smart to NOT reveal they have the ability to automagically dominate a system remotely.  Furthermore, Ubuntu has the largest portion of Linux desktops in which case a remote exploit is far more valuable when kept private.

Personally, if I could access any Ubuntu box with some ubermagical pwnz0r exploit the last thing I would do is make it public knowledge but that's just me.

---

### Post by brian_p on 2008-05-22
> **yaztromo said:**
> 
My feeling is that having no open ports is not like having a room with no doors.

That's exactly what it's like. No open ports, no services, no way in.

> Packets are still coming in to the system and the kernel has to look at them in some way, even if to just determine there is no service on the requested port. Since a directly connected machine will examine all data before disregarding it I still feel there are many things a skilled hacker can do to try and trip up a system with no services running.

Wouldn't that be an attack on the kernel's tcp stack? The worst outcome might be a kernel crash but no access to the box.

---

### Post by brian_p on 2008-05-22
> **2point0 said:**
> Would that make it hacking or just user stupidity in clicking unverified links?

I'll go with your second option. There is a vast difference between a burglar bypassing the security on your house and handing the keys to him.

> Personally, if I could access any Ubuntu box with some ubermagical pwnz0r exploit the last thing I would do is make it public knowledge but that's just me.

Keeping it to yourself and not using it makes it a potential exploit. Use it in any significant way and it will be discovered and defended against. So, nothing to worry about.

---

### Post by The Tronyx on 2008-05-22
> **brian_p said:**
>  The worst outcome might be a kernel crash but no access to the box.

Maybe, but maybe not.  If you can crash the machine, it is still a remote no-auth DoS exploit which can be considered a hack seeing as how you would be able to crash a system at will.  Beyond that, it may be possible to create packets which when examined by the kernel which will allow the remote attacker to execute arbitrary code on the machine.  This is in theory mind you.

---

### Post by lucho64 on 2008-05-22
Suppose we send a malformetd TCP header that makes the tcp stack overwrite part of its memory, perhaps an array stored in the stack with no bounds check. So now we overwrite the stack with our data that makes the kernel print /root/.ssh/rsa_id over tcp, upon return from the current function. It might crash afterward, but we got the private ssh key if we were listening. I'm not saying that's likely, but I think I could write a lousy enough tcp stack that could cause that to happen, so it is possible.

---

### Post by yaztromo on 2008-05-22
> **lucho64 said:**
> Suppose we send a malformetd TCP header that makes the tcp stack overwrite part of its memory, perhaps an array stored in the stack with no bounds check. So now we overwrite the stack with our data that makes the kernel print /root/.ssh/rsa_id over tcp, upon return from the current function. It might crash afterward, but we got the private ssh key if we were listening. I'm not saying that's likely, but I think I could write a lousy enough tcp stack that could cause that to happen, so it is possible.

This is the kind of incident I was trying to say could happen earlier, except lucho64 and 2point0 have put it much more eloquently than me. I guess a lot of time and a lot of eyes look at the networking stack and kernel on Linux, but it still doesn't make such an exploit impossible, only extremely unlikely.

---

### Post by brian_p on 2008-05-22
> **2point0 said:**
> Maybe, but maybe not.  If you can crash the machine, it is still a remote no-auth DoS exploit which can be considered a hack seeing as how you would be able to crash a system at will.

100 1MB emails per second to this machine would have an adverse effect on its health. Would that be a hack? A DoS is what it says and does not of itself give access to a machine.

> Beyond that, it may be possible to create packets which when examined by the kernel which will allow the remote attacker to execute arbitrary code on the machine.  This is in theory mind you.

The only thing remotely close to what we are discussing is the 'ping of death' and that produced a kernel crash at worst. Extrapolating to execution of arbitrary code is so theoretical as to be unjustified.

---

### Post by brian_p on 2008-05-22
> **yaztromo said:**
> This is the kind of incident I was trying to say could happen earlier, except lucho64 and 2point0 have put it much more eloquently than me. I guess a lot of time and a lot of eyes look at the networking stack and kernel on Linux, but it still doesn't make such an exploit impossible, only extremely unlikely.

It's about as likely as lucho64 getting his code for a 'lousy tcp stack' into the Linux kernel.

---

### Post by lucho64 on 2008-05-22
Well, remember that we have "vendor" kernels, and now we know that the acceptance thereshold is not too high for critical pieces of code like the openssl libraries

---

### Post by wirelessmonkey on 2008-05-22
> **kaffemonster said:**
> On a danish news site, citing [this]("http://computerworld.com/action/article.do?command=viewArticleBasic&articleId=9073258&intsrc=hm_list") article, a discussion arose. Did the laptop running Ubuntu survive because Ubuntu is a more secure OS than OSX and Vista, or because the hackers spared it?

In stead of jumping into the usual web forum flamewars, I decided to challenge them...

A standard PC has a fresh install of Ubuntu 8.04 LTS. It has gotten the updates that popped up in update manager, otherwise it is untouched. No measures have been taken to protect it. 

The pc is sitting behind a router. Nothing fancy, just a router designed for home use. No measures have been taken to protect the router other than changing the admin password. This router is on a standard ADSL with the IP adress 83.95.212.118

There is a single user account on the pc, as it is a "virgin" installation. The first person to leave a .txt file with contact info (name/nick and e-mail) on this users desktop will be declared the winner of this little challenge.

Bring it on, hack me.

Congrats!  You have allowed me root access to your machine. I choose not to leave a txt file on your desktop, instead I challenge you to figure out how I got in, and what I have changed on your machine.

I suggest you format and reinstall when you're done.


Best of Luck

---

### Post by captainsixxx on 2008-05-22
ya'll scare the hell outta me and my computer, thanks for that, i now remember why i dont use my computer for anything usefull, i do smile at what ya'll think are games and i am sure that it has its uses, have fun i guess and good luck, i mean what really does one say to such things, for all i know one or more of you have already sild through my computer and could tell me what i am wearing, well i hope this is asking nice enough but if any of you would like to clue me in as to how i can better protect my computer for things like this that would be great, oh yeah you will have to use smae words as i dont know crap about any of this stuff, thanks, oh and your best be would be to send a copy of whatever you write as a p.m. so i know that anyone repiled, thanks again

---

### Post by BlackDragonBE on 2008-05-22
I think we have a confused and scared user now with all that talking about hacking :)
To captainsixxx: Don't worry, if you're running Ubuntu you're quite safe as long as you don't login as root, if you want to be even safer install firestarter to open/close ports. I'm glad I'm an Ubuntu user!

Cheers

---

### Post by ASULutzy on 2008-05-22
> **wirelessmonkey said:**
> Congrats!  You have allowed me root access to your machine. I choose not to leave a txt file on your desktop, instead I challenge you to figure out how I got in, and what I have changed on your machine.

I suggest you format and reinstall when you're done.


Best of Luck

good one.
He could just type last, or cat /var/log/auth.log or something else.

We're really beating a dead horse here.

I think we all consider "hacking" a box gaining administrative (root) access on it. Simply booting something off the internet is not "hack" in the more elegant sense, otherwise we could just go grow a bot farm and tell it to flood the crap of the machine, that's boring.

You need to open up ports and services or else this just isn't going to happen.

---

### Post by MDSmith2 on 2008-05-22
You open up some ports that way we can get in.

---

### Post by wootah on 2008-05-22
I suppose a whole bunch of us could just DDOS his router for kicks :lolflag:

---

### Post by Dr Small on 2008-05-22
> **MDSmith2 said:**
> You open up some ports that way we can get in.
I have been trying to say that all along.

---

### Post by wirelessmonkey on 2008-05-23
His DNS became my DNS for a short while, all DNS requests proxied through my device. I used a known exploit for firefox to escalate myself to root, scripted removal of all my data from his sytem logs and bash, and changed his DNS back.  Does that not count?  At 10:42pm that machine lost internet until 10:44pm, after which I removed my poll script, and stopped playing. So, I had to take his router first, but I'd consider that machine pwned.

I did not do anything else, but you should not trust that.  I didn't like his rules, and I expected the criticism my reply has generated. So... believe or not, there is no way to prove whether it really happened, or if this is a bit of social engineering. That is the major problem with providing information, it makes you less secure.

---

### Post by wirelessmonkey on 2008-05-23
> **ASULutzy said:**
> good one.
He could just type last, or cat /var/log/auth.log or something else.

We're really beating a dead horse here.

I think we all consider "hacking" a box gaining administrative (root) access on it. Simply booting something off the internet is not "hack" in the more elegant sense, otherwise we could just go grow a bot farm and tell it to flood the crap of the machine, that's boring.

You need to open up ports and services or else this just isn't going to happen.

Changing last (/var/log/lastlog) and removing references from messages, auth.log, syslog, etc... is trivial.

---

### Post by yaztromo on 2008-05-23
> **wirelessmonkey said:**
> Congrats!  You have allowed me root access to your machine. I choose not to leave a txt file on your desktop, because I couldn't actually get in.

Fixed it for you.

---

### Post by ASULutzy on 2008-05-23
> **wirelessmonkey said:**
> His DNS became my DNS for a short while, all DNS requests proxied through my device. I used a known exploit for firefox to escalate myself to root, scripted removal of all my data from his sytem logs and bash, and changed his DNS back.  Does that not count?  At 10:42pm that machine lost internet until 10:44pm, after which I removed my poll script, and stopped playing. So, I had to take his router first, but I'd consider that machine pwned.

I did not do anything else, but you should not trust that.  I didn't like his rules, and I expected the criticism my reply has generated. So... believe or not, there is no way to prove whether it really happened, or if this is a bit of social engineering. That is the major problem with providing information, it makes you less secure.

I call shenanigans.

---

### Post by honeydew on 2008-05-23
> **ASULutzy said:**
> I call shenanigans.


did he say... shenanigans... SHENANIGANS!

---

### Post by bwhite82 on 2008-05-26
No response from that IP ATM. Is this pwn20wn? We need some sort of reward for our efforts.

---

### Post by MDSmith2 on 2008-05-26
*Sits and starts waging tail with tongue sticking out*

---

### Post by kaffemonster on 2008-05-27
First of all: Thank you guys for all your replies! 

Second: Sorry for my absense! I've been sick for some days and the e-mail notifications have been failing for some reason. 

The machine is sitting at my office at work (on a standard DSL I use for testing VPN connections) and when I came in yesterday, my router was as dead as the aforementioned horse. I was actually sort of disappointed when a quick reset brought it back up :)

I'm plugging the PC directly to the net now, will re-check my IP and post any changes.

I will also be using e-mail on the computer, as well as start browsing the web, i.e. acting as a typical user. Will keep you posted!

---

### Post by kaffemonster on 2008-05-27
The comp is now directly online, no router.

Joe Bloggs is using the computer, his e-mail address is [email]ubuntujoe1337@gmail.com[/email]

He's live and kicking at 83.95.212.118

---

### Post by bwhite82 on 2008-05-27
Excellent. Please leave it up. This stuff takes time. Am running several scans on the box now to identify possible weaknesses/gather information. This is fun stuff! :)

BTW: I'm no hacker but am interested in knowing how secure Ubuntu is, so thought I'd give it a shot.

---

### Post by kaffemonster on 2008-05-27
> **Soldierboy said:**
> Excellent. Please leave it up. This stuff takes time. Am running several scans on the box now to identify possible weaknesses/gather information. This is fun stuff! :)

BTW: I'm no hacker but am interested in knowing how secure Ubuntu is, so thought I'd give it a shot.

Exactly the reason I'm providing this little challenge - I want to see how secure this stuff is :)

---

### Post by yaztromo on 2008-05-27
Have you opened any services or is this still a default install?

---

### Post by kaffemonster on 2008-05-27
Still just a default user toddling around.

He has no clue about apache or SSH. His friend just set up an Ubuntu box for him. He checks his aforementioned gmail using pop3 in an e-mail client.

He's happy as a clam. One of these days, he'll even install flash for his webbrowser, so he can visit Youtube.

---

### Post by Dr Small on 2008-05-27
```
[drsmall@darkghost ~]$ sudo nmap -PN -F -O 83.95.212.118

Starting Nmap 4.62 ( http://nmap.org ) at 2008-05-27 10:00 EDT
Interesting ports on 0x535fd476.arcnxx18.adsl-dhcp.tele.dk (83.95.212.118):
Not shown: 1274 filtered ports
PORT     STATE SERVICE
80/tcp   open  http
8080/tcp open  http-proxy
Warning: OSScan results may be unreliable because we could not find at least 1 open and 1 closed port
Device type: WAP|switch
Running (JUST GUESSING) : D-Link embedded (94%), TRENDnet embedded (94%), HP embedded (94%)
Aggressive OS guesses: D-Link DWL-624+ or TRENDnet TEW-432BRP wireless broadband router (94%), HP 4000M ProCurve switch (J4121A) (94%)
No exact OS matches for host (test conditions non-ideal).
Uptime: 4.333 days (since Fri May 23 02:01:03 2008)

OS detection performed. Please report any incorrect results at http://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 16.555 seconds
```

This can be correctly labeled, "Mission Impossible".

---

### Post by Pap3r on 2008-05-27
I disagree:
```

pap3r| UBox~| sudo nmap -sS -sV -PI -PT -R 83.95.212.118

Starting Nmap 4.53 ( http://insecure.org ) at 2008-05-27 13:27 EDT
Interesting ports on 0x535fd476.arcnxx18.adsl-dhcp.tele.dk (83.95.212.118):
Not shown: 1711 closed ports
PORT     STATE    SERVICE     VERSION
25/tcp   filtered smtp
119/tcp  filtered nntp
1720/tcp filtered H.323/Q.931

Service detection performed. Please report any incorrect results at http://insecure.org/nmap/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 19.448 seconds
pap3r| UBox~| 


```

---

### Post by Monicker on 2008-05-27
Some of you need to realize that some of these scan results are influenced by your ISP and any filtering that they do. ;)

The following ports will always show filtered for me, no matter what external host I scan, because my ISP will not allow outbound traffic to them from my home ip address: 25, 119, 135-139, 445.

---

### Post by Pap3r on 2008-05-27
My ISP, Verizon, sucks.  However, it does not always show Filtered for ports.  I.e., a port scan on a friend's website last night showed 25 as open.

I haven't come across any ports that my ISP shows as filtered constantly.

---

### Post by umattu on 2008-05-27
nmap -P0 83.95.212.118

Starting Nmap 4.03 ( [http://www.insecure.org/nmap/](http://www.insecure.org/nmap/) ) at 2008-05-27 13:47 CDT
Interesting ports on 0x535fd476.arcnxx18.adsl-dhcp.tele.dk (83.95.212.118):
(The 1666 ports scanned but not shown below are in state: closed)
PORT    STATE    SERVICE
25/tcp  filtered smtp
119/tcp filtered nntp
135/tcp filtered msrpc
136/tcp filtered profile
137/tcp filtered netbios-ns
138/tcp filtered netbios-dgm
139/tcp filtered netbios-ssn
445/tcp filtered microsoft-ds


He has plenty of penetrable ports open. 

Now go get 'em!!:popcorn:

EDIT:

But on second look seems the OS in question is Mac!?!?!?! :lolflag: I guess it IS Much less reliable, or someone is fibbing

sudo nmap -PN -F -O -P0 83.95.212.118

Starting Nmap 4.03 ( [http://www.insecure.org/nmap/](http://www.insecure.org/nmap/) ) at 2008-05-27 14:09 CDT
[COLOR="Red"]Warning:  OS detection will be MUCH less reliable because we did not find at least 1 open and 1 closed TCP port[/COLOR]
Interesting ports on 0x535fd476.arcnxx18.adsl-dhcp.tele.dk (83.95.212.118):
(The 1225 ports scanned but not shown below are in state: closed)
PORT    STATE    SERVICE
25/tcp  filtered smtp
119/tcp filtered nntp
135/tcp filtered msrpc
136/tcp filtered profile
137/tcp filtered netbios-ns
138/tcp filtered netbios-dgm
139/tcp filtered netbios-ssn
445/tcp filtered microsoft-ds
Device type: general purpose
Running: Apple Mac OS 8.X
OS details: Apple Mac OS 8.5

Nmap finished: 1 IP address (1 host up) scanned in 15.223 seconds

---

### Post by Pap3r on 2008-05-27
It seems as though my nmap results are inconclusive...

---

### Post by bwhite82 on 2008-05-27
Well here's a Nessus scan. Dunno if that mdns port is exploitable or not. Kinda startin' to have to agree with the others. There needs to be something to exploit in order for it to be exploited.

```
83.95.212.118


Scan time :
Start time : 	Tue May 27 15:01:41 2008
End time : 	Tue May 27 15:08:25 2008
Number of vulnerabilities :
Open ports : 	1
Low : 	5
Medium : 	0
High : 	0
Information about the remote host :

Operating system : 	Linux Kernel
NetBIOS name : 	(unknown)
DNS name : 	0x535fd476.arcnxx18.adsl-dhcp.tele.dk.

[^] Back to 83.95.212.118
Port mdns (5353/udp)
mDNS Detection

Synopsis :

It is possible to obtain information about the remote host.

Description :

The remote host is running the Bonjour (also known as ZeroConf or mDNS)
protocol.

This protocol allows anyone to dig information from the remote host, such
as its operating system type and exact version, its hostname, and the list
of services it is running.

An attacker may use this information to perform a more accurate attack.

Solution :

filter incoming traffic to UDP port 5353

Risk factor :

None

Plugin output :

We could extract the following information :

Computer name : Testmaskine.local.
Ethernet addr : 00:1a:a0:b1:de:5a
Computer Type : I686
Operating System : LINUX


Nessus ID : 12218

[^] Back to 83.95.212.118
Port general/tcp
Ping the remote host
The remote host is up

Nessus ID : 10180
Host FQDN
83.95.212.118 resolves as 0x535fd476.arcnxx18.adsl-dhcp.tele.dk.

Nessus ID : 12053
OS Identification

Remote operating system : Linux Kernel
Confidence Level : 30
Method : mDNS


The remote host is running Linux Kernel

Nessus ID : 11936
```

---

### Post by yaztromo on 2008-05-27
I thought cups might've been accessible at least just to get a local only message.

```

xxxxx@nebulous:~$ sudo nmap -PN -F -O 83.95.212.118

Starting Nmap 4.53 ( http://insecure.org ) at 2008-05-27 23:45 BST
Interesting ports on 0x535fd476.arcnxx18.adsl-dhcp.tele.dk (83.95.212.118):
Not shown: 1264 closed ports
PORT     STATE    SERVICE
25/tcp   filtered smtp
119/tcp  filtered nntp
135/tcp  filtered msrpc
137/tcp  filtered netbios-ns
138/tcp  filtered netbios-dgm
139/tcp  filtered netbios-ssn
445/tcp  filtered microsoft-ds
593/tcp  filtered http-rpc-epmap
1434/tcp filtered ms-sql-m
4557/tcp filtered fax
6001/tcp filtered X11:1
Warning: OSScan results may be unreliable because we could not find at least 1 open and 1 closed port
Device type: general purpose|firewall
Running: Linux 2.4.X, Secure Computing Linux 2.4.X
OS details: Linux 2.4.22 (Fedora Core 1, x86), Secure Computing SG560 Firewall (Linux 2.4.31-uc0 based)
Network Distance: 14 hops

OS detection performed. Please report any incorrect results at http://insecure.org/nmap/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 6.524 seconds

```

I noticed how we're all showing different OS results.

---

### Post by Dr Small on 2008-05-27
That's what I don't get. Why are different scans showing different OSes and open ports by the same software (nmap)?

Dr Small

---

### Post by bwhite82 on 2008-05-27
> **Dr Small said:**
> That's what I don't get. Why are different scans showing different OSes and open ports by the same software (nmap)?

Dr Small

NMAP's OS fingerprinting has been notoriously wrong, primarily because no one submits unidentified fingerprints like they should.

---

### Post by umattu on 2008-05-27
> **Dr Small said:**
> That's what I don't get. Why are different scans showing different OSes and open ports by the same software (nmap)?

Dr Small

I can't see why this would cause the results to differ so drastically, but everyone has been using a slightly different syntax.

Really I'm surprised that noone has asked the obvious.

kaffemonster, is this your very own network that you are asking people to try and penetrate. A simple whois has this to say:

NetRange:   83.0.0.0 - 83.255.255.255 
CIDR:       83.0.0.0/8 
NetName:    83-RIPE
NetHandle:  NET-83-0-0-0-1
Parent:     
NetType:    Allocated to RIPE NCC
NameServer: NS-PRI.RIPE.NET
NameServer: SEC1.APNIC.NET
NameServer: SEC3.APNIC.NET
NameServer: SUNIC.SUNET.SE
NameServer: TINNIE.ARIN.NET
NameServer: NS3.NIC.FR
Comment:    These addresses have been further assigned to users in
Comment:    the RIPE NCC region. Contact information can be found in
Comment:    the RIPE database at [http://www.ripe.net/whois](http://www.ripe.net/whois)
Comment:    
RegDate:    2003-11-17
Updated:    2004-03-16

Seems that this I.P. is in their range, even though it may be your machine that you are asking people to hack, you could very well be asking people to "hack" on someone else's network which depending on their terms of service, and more likely than not, is illegal.

Do you have authority to authorize pentesting on this network?

---

### Post by PmDematagoda on 2008-05-27
This thread is closed based on the following points:-
1) Threads should not encourage people to scan random IPs just because another user tells them to.

2) There is no way to ascertain whether or not he owns the computer or the IP in question.

3) This post may very well encourage malicious behavior of forum members and furthermore, potentially perpetuate the notion that it is acceptable to say "hack me," and have it be open season with no concern for the reprocussions of their actions.

4) On a final note, if this is his computer and it is his machine, beyond the ISP's permission, which you need in order to even remotely legally transmit hostile potentially hostile data, if this guy did get hacked, he could find himself in a far worse position that he had expected.

Any more threads like this are liable to be closed as well.

---

