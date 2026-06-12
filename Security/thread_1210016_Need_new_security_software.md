---
title: "Need new security software"
date: 2009-07-10
forum: Security
---

### Post by GNUway Tech on 2009-07-10
I recently moved into a new home and I am planning on setting up a network consisting of 3 computers. 2 will run Kubuntu, and 1 will run Edubuntu. All of them will be on Jaunty Jackalope. I am looking for some good reliable security software to run on my network. Now, I know that you generally do not need an antivirus program with Linux. However, since I am running a broader network now, I would rather not go without the security.

I have tried 3 programs in the past; Clamav/Klamav, AVG Free, and Avast. The 1st 2 quit working for me, and Avast keeps getting stuck when it scans. I've actually started looking for possibly a good proprietary program like Kaspersky or Norton. I would be willing to pay a little bit of money for something good and reliable, so long as it doesn't cost too much like a Business or Enterprise version.

I'm not just interested in antivirus, but any kind of necessary or worthwhile security programs. Any suggestions?????????????

---

### Post by cariboo on 2009-07-11
If all you are running is three computers running Ubuntu, you don't need an antivirus program that only scans for windows viruses. Please read the [Ubuntu security]("http:///ubuntuforums.org/showthread.php?t=510812") sticky at the top of the page.

---

### Post by note32 on 2009-07-11
this might help out a big [http://www.itsecurity.com/features/ubuntu-secure-install-resource/](http://www.itsecurity.com/features/ubuntu-secure-install-resource/)

---

### Post by sasho_zl on 2009-07-11
You can think about better securing your home network by placing a good firewall on the internet gateway. You can check firewall software with Network Intrusion Detection Systems like "Smoothwall" or "IPCop". I think this would give you all the security you need.

---

### Post by ktrnka on 2009-07-11
Just setup a custom firewall/gateway. The one with the most features for home use that I've seen so far is Untangle. It is absolutely my favorite!

[http://www.untangle.com/home]("http://www.untangle.com/home")

---

### Post by GNUway Tech on 2009-07-12
Okay, I'm interested in Untangle. But, since this would be my first time looking at a program like this, I have quite a few questions.

According to their website, Untangle boots from the disk and installs it's own operating system. So, if I try to install it on a computer already running Kubuntu, will it run inside Kubuntu, run outside Kubuntu, or format and take over the hard drive?????? In general, can I run both systems on 1 computer, or am I going to have to designate 1 computer to use as a gateway with Untangle alone??????

Also, if it runs outside Kubuntu, will I be able to access it from inside Kubuntu???? And, I have a Netgear wireless-G router will it work in conjunction with that??????????

Please bear with me if my questions seem ignorant. I'm only used to running a small home network on a wireless-G router with it's own firmware.

---

### Post by cariboo on 2009-07-12
If your Netgear router has a built in firewall, you really have no need for another firewall, I have had cable internet access since 2001 and so far I have never had a problem with anybody breaking in to my system. The thing to be be careful about is don't run any services you don't need, and any services you do run should have strong password protection.

---

### Post by GNUway Tech on 2009-07-12
It's not just a firewall I'm looking at. Untangle has a lot of other things to (antivirus, antispam...). I just want to know if I can run it on the same computer as Kubuntu.

---

### Post by ktrnka on 2009-07-12
Untangle needs to be installed on it's own dedicated machine. U might consider acquiring another machine that can be your dedicated firewall. You can use untangle inline with your netgear router. Untangle's documentation shows you. It just bridges the two nics together. If you view the specs that Untangle suggests, they are pretty high but in the Wiki people have been successful in using lower hardware requirements.

---

### Post by jimv on 2009-07-13
Don't get insulted, but you are being paranoid.  Your router uses Network Address Translation (NAT) to allow your three computers to connect to the net with the single IP of your router.  This is essentially a firewall, and no one is getting through.  Unless you've opened ports to allow servers through (like SSH, FTP, HTTP), there is pretty much no way that anyone is going to hack or attack you form the internet.  You'd have to be a pretty attractive target for anyone to bother putting in the massive effort it would take, and I doubt that you are.

The chances of getting infected are pretty much zero.  The only way that's going to happen is if you install virus yourself or someone puts one in a repo, which will never happen with any of Ubuntu's default repositories, as all of their packages must be signed by their private key.

Programs like Untangle simply add unnecessary overhead to your gateway.  Malware protection is unneeded.  Spam should be handled on the server, not the clients.  The only thing you might want is web filtering if you have kids, and that can be handled by using OpenDNS.

---

### Post by GNUway Tech on 2009-07-14
You can call me paranoid if you want, but one of these computers I'm planning on setting up is going to be used by my daughter. This will be the 1st time she's had a computer of her own, and I want total control of it and everything she sees and does on it. Especially, online.

I'm well aware that Linux and Ubuntu are highly secure already. But I'm also well aware, as is anybody else, what kind of people that she could encounter online. Not to mention, the kind of elaborate measures they could be willing to take to find her.

I'm sure you're about to tell me not to give her a computer if I'm that concerned about her being online. But, she starts 1st Grade in a month and a half, and I'm a little concerned that the school is going to start teaching her, and every other student her age, how to use a computer to do everything they want them to do. The schools all want to "go green" by placing their students' homework, and everything else, online and not use any paper.

It's almost a totally different world for learning in now than what it was when I was my daughter's age, and a little scary. I know I'm showing my age by saying that, but we never had these kind of sophisticated tools for learning at our disposal. I don't want to hold her back my not giving her the tools of the trade. I just want complete control over her security.

---

### Post by cariboo on 2009-07-14
If you are worried about your daughters internet experience you are going about things the wrong way. I would suggest you have a look at dansgaurdian, it  is in the repositories, it is a web filter plus more. From synaptic:

> DansGuardian filters the content of pages based on many methods
including phrase matching, PICS filtering and URL filtering. It does
not purely filter based on a banned list of sites.

It provides real-time virus scanning capabilities for content access.

DansGuardian is designed to be completely flexible and allows you to tailor
the filtering to your exact needs. It can be as draconian or as
unobstructive as you want. The default settings are geared towards what a
primary school might want but DansGuardian puts you in control of what you
want to block.

DansGuardian requires squid or another similar caching proxy server
on your local network.

---

### Post by GNUway Tech on 2009-07-14
Ok, that's something that I wasn't aware of before. I'll have to have a look at that to. At this point, I'm just leaving no stone unturned. I want my network bolted down like a sherman tank and I want complete control over my network from any computer I'm at.

---

### Post by dragos2 on 2009-07-14
> **GNUway Tech said:**
> You can call me paranoid if you want, but one of these computers I'm planning on setting up is going to be used by my daughter. This will be the 1st time she's had a computer of her own, and I want total control of it and everything she sees and does on it. Especially, online.

I'm well aware that Linux and Ubuntu are highly secure already. But I'm also well aware, as is anybody else, what kind of people that she could encounter online. Not to mention, the kind of elaborate measures they could be willing to take to find her.

I'm sure you're about to tell me not to give her a computer if I'm that concerned about her being online. But, she starts 1st Grade in a month and a half, and I'm a little concerned that the school is going to start teaching her, and every other student her age, how to use a computer to do everything they want them to do. The schools all want to "go green" by placing their students' homework, and everything else, online and not use any paper.

It's almost a totally different world for learning in now than what it was when I was my daughter's age, and a little scary. I know I'm showing my age by saying that, but we never had these kind of sophisticated tools for learning at our disposal. I don't want to hold her back my not giving her the tools of the trade. I just want complete control over her security.

I am sorry but you seem like a control freak. Leave the kids alone :P

---

### Post by jimv on 2009-07-14
It's not a matter of keeping people out of your network.  That's not even an issue.  No one is getting into your network...by default it is locked down like a tank.  What you want to do is control where she goes, and if you're really concerned, then you should monitor where she goes and what she types in.  Also, keep the machine somewhere that you can easily see what she is doing at all times.

The internet isn't going to come after her onto your network, but you have to be careful where she goes on the internet.

---

### Post by GNUway Tech on 2009-07-14
As I saud before, it's not the internet i'm afread of. It's the kind of people that can be found on it.

My intention is to be able to determine exactly which sites she can and cannot be on. Also, to be able to look in on her and see what she's doing from another computer in the network.

Is it possible to run a remote desktop connection from within Kubuntu without having to use a VNC program??????????

---

### Post by scorp123 on 2009-07-15
> **GNUway Tech said:**
>  ... and I want total control of it and everything she sees and does on it. Especially, online. ...

I'm well aware that Linux and Ubuntu are highly secure already. But I'm also well aware, as is anybody else, what kind of people that she could encounter online. Not to mention, the kind of elaborate measures they could be willing to take to find her.

I just want complete control over her security.

I am father of a daughter myself. But my daughter is only 3 years old and for now she has no need and no use for computers. So right now I am not facing the problem that you are confronted with.

But .... If by some divine intervention you and me were to switch places so that I'd be facing your task now, and knowing what I know I would create this solution:


1.) Forget about PC's.

What you want is a thin-client. I know: "thin-client" can mean a lot of things. What I mean by "thin-client" here is a minimal PC that has only so much firepower and software on it that it could boot and start a Firefox web browser ... and that's it. This device could have a VIA C7 or AMD "Geode" CPU, or maybe it could be something Intel "Atom" based. 256 MB RAM will do. We won't be running 3D games on this thing anyway.

Ideal devices for such a "homebrew thin-client" are micro-PC's that come in "mini ITX" form factors. You'd have to google around.

Or you buy a real thin-client and convert it to suit your needs? Look here:

[http://www.vxl.net/products/tc4341-ce.html](http://www.vxl.net/products/tc4341-ce.html)

See that thing? It's just slighty larger and thicker than a VHS tape cover, comparable to a thick book. It's basically a super small PC. I got mine from the dumpster -- someone at a neighbouring company didn't know what to do with that thing and they had thrown it away ... and they didn't mind me picking it up from the container. 

The only thing that bothered me was that stupid 32 MB IDE-Flash drive (those things are not SSD's!!) that containes Windows CE .... What in the world would I want with Windows CE? So I replaced that stupid 32 MB IDE-Flash drive with a 8 GB model from Transcend:

[IMG]http://www.transcendusa.com/Products/images/IFD/DOM_IDE//DOM40V-S_530x400-8G.jpg[/IMG]

[http://www.transcendusa.com/Products/ModDetail.asp?ModNo=26&LangNo=0&Func1No=1&Func2No=159](http://www.transcendusa.com/Products/ModDetail.asp?ModNo=26&LangNo=0&Func1No=1&Func2No=159)

[http://www.cdfreaks.com/hardware/product/73938-Transcend-8GB-IDE-Flash-Module.html](http://www.cdfreaks.com/hardware/product/73938-Transcend-8GB-IDE-Flash-Module.html)


That "VXL" mini-PC I picked up from the container just so happens to have 2 x internal IDE connectors. So with the cover removed I hooked up a spare CD-ROM drive, connected both the spare CD-ROM drive and that mini-ITX motherboard to an external standard ATX power supply ... and I was good to boot.

Now with the 32 MB Flash that contained Windows CE replaced by a 8 GB Transcend IDE-Flash disk I installed Ubuntu on this thing.

I tweaked and tuned this thing so everything I need would fit into those 256 MB RAM this thing has (I tried upgrading the RAM but that didn't work; seems the CPU or the BIOS can't see beyond 384 MB RAM ??)

So what you want is a device like this. A PC so small and so "thin" that only a minimum Linux installation can fit on it, nothing more.



2.) Sun Secure Global Desktop

This software is not free, unfortunately:
[http://www.sun.com/software/products/sgd/index.jsp](http://www.sun.com/software/products/sgd/index.jsp)

In fact, it's very very far from "free". Depending on the features you want or don't want the oOfficial prices are somewhere between USD 199.-- and USD 349.-- **_per concurrent user._**  Yes. That's a lot. Maybe you can get some educational discount somewhere somehow?? (I have  corporate customers who have bought this software for 2000+ concurrent user connections ... Yes, that would be 2000 x 349 = USD 698'000.-- just for this software!)

**_But the software is worth it._** It can do some amazing nifty things.

Especially thanks to this plugin (which again costs a few 100.-- Euros per concurrent user):

"ToolBox Backplane Service"
[http://www.tbsol.de/index.php?article_id=63&clang=1](http://www.tbsol.de/index.php?article_id=63&clang=1)

This software is like a video camera and can record anything --including keystrokes-- that happens inside a session.


3.) The solution

Your daughter would be using the homebrew "thin client" and connect to the "Sun Secure Global Desktop" server and in fact get her Linux and/or Windows desktop session from there. This can be all configured in such a way that she won't even see any login page or anything. She won't realise that the computer she's working on is in fact getting its applications from a different machine. She turns on this mini-PC thing, and voila: She's in her GNOME desktop. She doesn't need to know the details.

But: Thanks to SSGD and the TBS plugin whatever happens inside her session and whatever she types on her keyboard is recorded and protocolled. You as administrator can login to the "Management Desk" application and check on the recordings any time you wish. It looks a bit like YouTube. You can even "checkout" movies as ZIP archives and then send the material to e.g. authorities, should you ever catch any strange activities.

Thanks to HTTPS tunneling (Sun calls that "Firewall traversal" in their documentation) you could control all these things even from your office via a easy-to-use web administration console. You'd just need to configure your SSGD installation and your router accordingly so HTTPS traffic ends up on the right machine.

Voila. Total control. At all times. Big brother is watching. And you are "big brother".

That's what I would do. I earn my money day by day with implementing this software for big corporations who want total control on their external consultants accessing the highly sensitive IT infrastructure -- so the main purpose of this software is "total control VPN replacement for companies who can afford it" ..... But apart from the hefty price tag there is no reason why this product combo wouldn't also work as "parental control" solution.

As I said ... I were to switch places with you, and given that I know what I know and given what I earn my money with every day, then the above would be what I would do.

---

### Post by GNUway Tech on 2009-07-15
I already have 3 computers, and I was just planning on setting one of them up for her, as opposed to buying a more specialized machine for her to use. But, that's a lot I'm definitely going to have to look over. Especially that software.

Since you have a lot of experience and knowledge in networking, do you happen to know of a small and inexpensive gateway device???? I'm wondering if I can find one the size of a router, that I can install my own firewall/securithy software on and run in-line with my router.

---

### Post by scorp123 on 2009-07-16
> **GNUway Tech said:**
>  do you happen to know of a small and inexpensive gateway device???? I'm wondering if I can find one the size of a router, that I can install my own firewall/securithy software on and run in-line with my router. That's again something where I'd go with "mini ITX" form factor "micro PC's".

Where I work we use lots of "Soekris" equipment:

Soekris EU Shop:
[http://www.soekris.eu/shop/](http://www.soekris.eu/shop/)

Soekris USA Shop:
[http://www.soekris.com/shop/](http://www.soekris.com/shop/)

Basically those things are extremely small PC's. Barely bigger than the Linksys or Netgear stuff that you'd find in any computer shop. But as I said: Basically they're PC's. So you can put anything you like on it: Debian, Ubuntu, FreeBSD ... or any of the specialised Firewall distros that are around: m0n0wall, pfSense ... and many others. And of course: nobody is stopping you from putting your own sticker on the casing. And nobody is stopping you from putting your own Linux or BSD-distro on these things. That's why we love to use them.

Look here:
[http://www.pcengines.ch/wrap1e203.htm](http://www.pcengines.ch/wrap1e203.htm)

That's a so called "WRAP". It comes with three Ethernet interfaces on-board. Nice. Now all you need to do is to find a suitable casing for this thing. Not hard to find, just google around.

Talking of Google: Try "WRAP", "Alix", "mini ITX" ... or the links to various hardware vendors on this pfSense web page:

[http://www.pfsense.org/index.php?option=com_content&task=view&id=44&Itemid=50](http://www.pfsense.org/index.php?option=com_content&task=view&id=44&Itemid=50)

---

### Post by cariboo on 2009-07-16
Many routers have built utilities to restrict usage to certain hours of the day, and what days of the week the computer can connect to the internet, you can also restrict which computers by ip address.They can also do web site filtering by url or key word. I have a Linksys wrt54gs that has this ability.

---

### Post by bodhi.zazen on 2009-07-16
You can restrict outgoing packets, by user, by time of day, with iptables.

/me hides

---

### Post by GNUway Tech on 2009-07-17
Thanks, Scorp123!!!! I'm definitely gonna have to take a good long look at all those things now and start enquiring about them.

---

### Post by PRC09 on 2009-07-17
Hi there,
    I too have kids that have had their own computers since age 5 or 6 but my only concern in regards to security is not who is trying to get into my systems but what information the kids are giving out.With all the social networking sites,messenger,facebook,myspace etc. all the home security software/hardware in the world is of no use if they say ,Hi my name is Suzy Smith and I live on 123 street. Teach them what they need to do and not do online.Monitor what she does by all means and block what you feel she shouldnt have access to.It has worked for me.

---

### Post by GNUway Tech on 2009-07-18
I understand very well what you're saying, and I have every intention of monitoring her in every way. That all plays a big part in my plans.

In fact, I intend to set restrictions on what sites she is and is not allowed to visit. I intend to use monitoring software to keep a close watch on where she is going and what she is doing. I want to be able to use a remote desktop connection to see what she is doing from another computer on the network....and so on.

I just intend to leave no stone unturned as far as my network goes.

---

### Post by grayn0de on 2009-07-18
You can always do that stuff with a good firewall distro, although it will take some configuration. Personally, I use Astaro. It's pretty easy to manage and setup through the sweet webUI. You can use IPCop (which can log IM traffic in realtime and includes a preconfigured snort IDS) or similar, as well. All it takes is a spare machine, which does not have to be very powerful, and two NICs.

Edit:

I went out and bought a dell dimension desktop (used) for under $100USD and an extra NIC, threw Astaro (ISO) on there and was up, running and configured in less than two hours. The reason I chose Astaro was because it is a commersial, enterprise grade solution that anyone with some basic IT skills can use.

They have a live demo that you can check out and play with to see if it is what you like: [http://www.astaro.com/our_products/astaro_security_gateway/hardware_appliances/live_demos](http://www.astaro.com/our_products/astaro_security_gateway/hardware_appliances/live_demos) ((Choose Astarto Security Gateway))

Also, even though it is a commercial firewall, they offer it free (10-user liscence) for home users, with support (email/forums).

---

### Post by GNUway Tech on 2009-07-19
Looks like I'm gonna have to do some serious comparisons between Untangle and Astaro. Untangle looks like a really easy setup and interface. But, if Astaro can offer me all that with commercial grade security, that will be the way I go.

You said you set it up to run on a laptop. Scorp123 has me sold on using a thin client gateway server with a network input and output. That way I can run it in-line with my router. Any particular legalities I should keep in mind about Astaro since it's proprietary????????

---

### Post by ktrnka on 2009-07-19
FYI Untangle also has commercial plugins as well as open-source free ones.

---

### Post by GNUway Tech on 2009-07-19
Yeah, I saw that on their website. The commercial grade setup costs money, and the open source options are free.

With Astaro, the commercial options are offered free to home network users. Astaro, however, is proprietary. That may be a reason for me not to use it.

I've become accustomed to using open source programs as much as possible, because of licensing laws and restrictions. But, I wouldn't be above using something proprietary for commercial grade security....so long as it's not too hands-off restrictive to use, and it doesn't cost me anything.

---

### Post by bodhi.zazen on 2009-07-19
Just to play devils advocate, what makes you feel you need any of that ?

Linux is modular and you can almost certainly get what you want from the Ubuntu repositories. You say you already have a router, you almost certainly do not need anything beyond that.

Most of what you need to know about security is here :

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812") 

Antivirus scanners really do not increase Linux security, there are no known active Linux viruses.

For Firefox see :

[How to Secure Firefox - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=671604") 

If you feel you want a firewall on each workstation, you already have one, iptables.

You can configure it with ufw or if you want a gui front end user GUFW.

[Uncomplicated Firewall - UFW - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw") 

```
sudo ufw enable
```

Unless you have a specific need I doubt you need anything more.

---

### Post by ktrnka on 2009-07-19
> **bodhi.zazen said:**
> Just to play devils advocate, what makes you feel you need any of that ?

Linux is modular and you can almost certainly get what you want from the Ubuntu repositories. You say you already have a router, you almost certainly do not need anything beyond that.

Most of what you need to know about security is here :

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812") 

Antivirus scanners really do not increase Linux security, there are no known active Linux viruses.

For Firefox see :

[How to Secure Firefox - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=671604") 

If you feel you want a firewall on each workstation, you already have one, iptables.

You can configure it with ufw or if you want a gui front end user GUFW.

[Uncomplicated Firewall - UFW - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw") 

```
sudo ufw enable
```

Unless you have a specific need I doubt you need anything more.

One very simple reason, Ease of Setup. It is very trivial to setup Untangle (Have not tried Astaro but will look at it) and is completely ready to go and contains everything the creator of this thread has asked for. Antivirus is very useful if he has guests with Windows laptops. There are also antispam, IDS, and many many more. It comes down to ease of setup, use and options available.

I believe it is a perfect choice for what this user has asked.

---

### Post by GNUway Tech on 2009-07-19
Amen, Ktmka!!!! I happen to believe that you can never be too careful running a network these days. Unless, of course, you're running more than 1 of any given type of program (firewall, antivirus,...etc.).

I also think that it would be more practical, and more secure, to have as many of those features as I can get running at the gateway instead of at the individual computers. That way they're all stopping everything at the source.

---

### Post by bodhi.zazen on 2009-07-20
Well, again to play devils advocate, I think it is better to understand what and why you are doing things to secure your OS.

There is also a downside of adding all these things to your gateway.

First, are they really needed ? 

What servers are you running ? I suggest you secure your server, host side.

There is a reason  routers are minimal OS, the more  packages you add to your router the more potential  sites of attack. 


If you are a "standard" desktop user behind a router I bet you have no need for those packages. I, and many others, have been running Linux desktops for years, behind routers, with no problems at all. If a problem occurs it is almost fixed by a security update.

Linux is not windows is all I am saying. If you have good reason, beyond paranoia and misunderstanding, to run those things, and have looked at the default and native apps, then it sounds you are making a good choice. Otherwise it may not be needed.

Edit : Ah found it.

In regards to your comment on "you can never be too careful running a network these days" you reminded me of master foo =)

[Master Foo and the Nervous Novice](http://catb.org/esr/writings/unix-koans/nervous.html)

---

### Post by spike_naples on 2009-07-20
If its a purely *buntu network then I would rather setup a firewall than go for anti virus software that detects windows/apple kinds.

I agree with the Linux legion of users who are confident that viruses for Linux are either grown in the "lab" or made exclusively for Microsoft compatible software.

---

### Post by GNUway Tech on 2009-07-20
Again, I understand that Linux and Ubuntu are extraordinarily secure by nature, that's not the issue. The issue is that this is a larger network than I've ran before, and my daughter is going to be using it.

I do not intend to run too many of any given thing, but I intend to have everything available to use. I'm thinking both as a security zealot and as a father protecting his daughter. If it were just me using it, I wouldn't bother. Since she is, I will bother.

Please, do not say, again, that I should be monitoring her usage and not the gateway. I have already gone over this 2 or 3 times on this thread. I intend to monitor everything she does, and that's one thing I've been asking about this whole time.

---

### Post by ktrnka on 2009-07-20
> **bodhi.zazen said:**
> Well, again to play devils advocate, I think it is better to understand what and why you are doing things to secure your OS.

There is also a downside of adding all these things to your gateway.

First, are they really needed ? 

What servers are you running ? I suggest you secure your server, host side.

There is a reason  routers are minimal OS, the more  packages you add to your router the more potential  sites of attack. 


If you are a "standard" desktop user behind a router I bet you have no need for those packages. I, and many others, have been running Linux desktops for years, behind routers, with no problems at all. If a problem occurs it is almost fixed by a security update.

Linux is not windows is all I am saying. If you have good reason, beyond paranoia and misunderstanding, to run those things, and have looked at the default and native apps, then it sounds you are making a good choice. Otherwise it may not be needed.

Edit : Ah found it.

In regards to your comment on "you can never be too careful running a network these days" you reminded me of master foo =)

[Master Foo and the Nervous Novice](http://catb.org/esr/writings/unix-koans/nervous.html)

Have you used Untangle? It's plugins are modular and can be installed and removed with the click of a mouse. It can be used as just a plain old firewall/router, but also much more. It allows him to easily choose if he wants to install and I7 layer filter to block bad websites very easily and if he wants/needs an IDS, he can easily install that as well. These are distros tailored for specific uses. 

Like I said before, it will allow him to choose what he needs. The endpoint antivirus is excellent idea if he has any friends or family that are NOT running Linux. If he feels that he no longer needs to be running an antivirus at the Endpoint Firewall, then he can easily remove the plugin with a couple of clicks. This firewall/router setup goes beyond just the OSes he is currently using and will protect anyone and anything connected. 

Linux, Windows, Mac, BSD, Solaris - It doesn't matter.

Say his machine somehow gets compromised and his system starts mailing spam or other email with a virus attached, Untangle can scan the OUTGOING mail and prevent the spread of these viruses and spam. Linux/Ubuntu may not be affected, but others most certainly are. I'm sure that will make his ISP much happier.

---

### Post by bodhi.zazen on 2009-07-20
> **ktrnka said:**
> Have you used Untangle?

I have never found the need , so no.

If you read my post you will see I provided an alternate opinion is all and ever :

> If you have good reason, beyond paranoia and misunderstanding, to run those things, and have looked at the default and native apps, then it sounds you are making a good choice.

No need to be so rude and make an issue where none exists.

---

### Post by ktrnka on 2009-07-20
> **bodhi.zazen said:**
> I have never found the need , so no.

If you read my post you will see I provided an alternate opinion is all and ever :


I understand and totally agree with you in that Linux is secure on it's own which is one reason why it's in so many embedded devices. I use to run Untangle when I had several roommates running Windows boxes. I finally got them on ubuntu and I switched to pfsense for my firewall router. If I have guests over, they are isolated to a vlan with an Untangle gateway. 

Bodhi I totally agree with your minimal standpoint but there are circumstances where more is requested/needed.

---

### Post by GNUway Tech on 2009-07-20
> beyond paranoia and misunderstanding

About the rudeness issue...I would appreciate it if people would stop calling to me/us paranoid. We've established very well now that we are all using the same highly secure operating system that is not vulnerable to threats the way that others are. There are just some of us, and I'm obviously not the only one on this thread, that would like to have those options at our disposal.

I don't expect everybody to understand, or to agree with us. And, I'm not going to keep rehashing my reasons for wanting these tools to use. We have our reasons.

---

### Post by ktrnka on 2009-07-20
Alright so we can close this thread now?

---

### Post by GNUway Tech on 2009-07-21
Looks like that's about all that's left to do. All we're doing now is going round and round with people questioning our motives, and I've pretty much got all the answers I need. As long as I can refer back to it later, I'm good.

I'll mark this thread as Solved. Thank you, everybody, for you help and advice.

---

### Post by grayn0de on 2009-07-21
> **bodhi.zazen said:**
> Well, again to play devils advocate, I think it is better to understand what and why you are doing things to secure your OS.

There is also a downside of adding all these things to your gateway.

First, are they really needed ? 

What servers are you running ? I suggest you secure your server, host side.

There is a reason  routers are minimal OS, the more  packages you add to your router the more potential  sites of attack. 


If you are a "standard" desktop user behind a router I bet you have no need for those packages. I, and many others, have been running Linux desktops for years, behind routers, with no problems at all. If a problem occurs it is almost fixed by a security update.

Linux is not windows is all I am saying. If you have good reason, beyond paranoia and misunderstanding, to run those things, and have looked at the default and native apps, then it sounds you are making a good choice. Otherwise it may not be needed.

Edit : Ah found it.

In regards to your comment on "you can never be too careful running a network these days" you reminded me of master foo =)

[Master Foo and the Nervous Novice]("http://catb.org/esr/writings/unix-koans/nervous.html")

I am going to have to agree to the necessity of understanding, here. However, I would also add that with the understanding of security comes the knowledge that layered security, though creating more complexity, is often a good thing. 

TBQH, outside of my 'God Mode' admin complex and the desire to have total (more centralized) control over my home network, I myself am really only running such a hefty firewall for skill development and reinforcement. :D I think there are many reasons to want to use more than a hardened system behind a router that do not stem from (too much) paranoia. Again, that takes me back to the layered security model.

> About the rudeness issue...I would appreciate it if people would stop calling to me/us paranoid.I'd say you are just being cautious. In a world where security risks are great and wide, being cautious helps. :) ...Especially where children are involved.

---

### Post by GNUway Tech on 2009-07-21
Thank you!!!!!!!!! I appreciate that!!!!!!!!!!!!

---

