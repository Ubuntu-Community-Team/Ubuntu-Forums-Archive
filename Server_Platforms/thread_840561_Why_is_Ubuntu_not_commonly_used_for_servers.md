---
title: "Why is Ubuntu not commonly used for servers?"
date: 2008-06-25
forum: Server Platforms
---

### Post by Trickyphillips on 2008-06-25
Can anyone tell me why Ubuntu is less commonly used for servers than distros like Debian or Gentoo?

Is there any good reason for this?

---

### Post by cariboo on 2008-06-25
Ubuntu is Debian based. Ubuntu is seen as a beginners distribution so that maybe why you don't hear of a lot of Ubuntu in commercial settings. If you check out this forum it seems like a lot of people are using the server version.

Jim

---

### Post by DrMega on 2008-06-25
I suspect it is more to do with the way Ubuntu is marketed. It is pushed as a good desktop OS (which it is), and pushed as "Linux for Humans" (or something like that).

There is also the fact that other distros have been around longer. RedHat has been used in serverworld for a very long time.

Other than that, I know of no technical reason why Ubuntu shouldn't be used as a server. In fact I know that it sometimes as, and in fact my machine is configured as a webserver (which took about 30 minutes max) because I had planned to do a web app but haven't got round to it yet.

---

### Post by Trickyphillips on 2008-06-25
Yes, I've seen a lot of individuals using it for small-scale projects and whatnot... I've used it a few times for low-traffic HTTP servers myself. 

It's not common to hear about it being used for larger projects though. Perhaps mainly because the IT admins suggesting other distros are elitists to some degree, or simply more comfortable with other older distros?

---

### Post by DrMega on 2008-06-25
> **Trickyphillips said:**
> Yes, I've seen a lot of individuals using it for small-scale projects and whatnot... I've used it a few times for low-traffic HTTP servers myself. 

It's not common to hear about it being used for larger projects though. Perhaps mainly because the IT admins suggesting other distros are elitists to some degree, or simply more comfortable with other older distros?

I suspect it is as much about sticking with what you know, or stick with what is proven to work.

If you were a consultant managing a project to set up and maintain a business critical web server, your professional reputation is at stake. If it goes wrong, you'll have a seriously hard time getting hired again and that could cost you a great deal financially. In this situation, you would probably choose RedHat if you were choosing Linux, for no other reason than there are thousands upon thousands of successful installations in a myriad of different environments and roles. This doesn't mean that Ubuntu can't do the job just as well, but you don't hear so much of Ubuntu based servers. I also think there is a credibility issue to it for the same reason. If you are the consultant, you have to remember that your client is going to discuss your initial meetings with his business buddies down the pub. If he says "My consultant recommended we use xyz", and they all turn round and say "ah yes, xyz, we used that in our abc server", then your client will be reassured that you have advised him wisely. If on the other hand they turn round and say "What's xyz, I've never heard of that one", then he is going to doubt you to some extent.

---

### Post by lodp on 2008-06-25
> **DrMega said:**
> I suspect it is as much about sticking with what you know, or stick with what is proven to work..

Second that. Ubuntu is fairly new on the market, and it's quite natural that people in a professional environment should be conservative when it comes to those choices. If RedHat or CentOS has been working for you fine for the last 10 years, you're not likely to switch unless the other OS offers something radically better or different (which Ubuntu doesn't do, as far as I'm informed).

I think my case is a good example. I run a mid-sized and growing web-site that I might develop into a business some day. I ran FreeBSD a year, then on CentOS for about 2 years, and when I got an attractive offer from a different web host, I switched to Ubuntu because I had used it as my Desktop OS for a cpl of years, and it felt more comfortable.

Also managing a web server is rather less scary when you've used Ubuntu as your Desktop OS. So more people might be getting into that.

I noticed more and more hosting companies offering pre-installed Ubuntu with their dedicated servers, so it's definitely growing..

---

### Post by John.Klockenkemper on 2008-06-25
If you want to read a good article regarding Ubuntu in the enterprise server market see the link below:

[http://www.desktoplinux.com/news/NS8859258187.html](http://www.desktoplinux.com/news/NS8859258187.html)

While this is an older article, its points are still valid.

Ubuntu is a new player in the enterprise class linux market and sports a rather new business model. While its model and terms of service are very appealing to some users, many other users and especially those in the mission critical data centers want something that they know works, something they know how to work, and someone to call when it doesnt work.

Ubuntu is coming along nicely in the server space. Many people are working to make it so and many want it to succeed. There are just some things it has to fix before it gets there.

---

### Post by Martyn Thompson on 2008-06-25
There are a few web server hosts offering Ubuntu servers - Webfusion and 123-reg.co.uk for example. 

I must agree with other authors here - Ubuntu is a relatively new player in that market but I can imagine it's market-share will grow significantly in the next few years. Debian based - why not?

---

### Post by lodp on 2008-06-25
> There are a few web server hosts offering Ubuntu servers - Webfusion and 123-reg.co.uk for example. 

i can add that all major German hosts offer Ubuntu at least on some of their products (strato, 1&1, server4you, hetzner ..)

---

### Post by Krillin on 2008-06-25
I just had a quick debate with another 20+ year veteran consultant about this very same issue. It appears to be that most comments here are from people who use this for Personal Use. That doesn't help people like us who care for 100's of clients with a 100 servers and 1000's of PC's to support.
 
Your main reasons are:
 
1) Not very well supported with Manufactures. (See anything in stores for 'Linux'?)
2) Clients will be at the mercy of the consultant who installs it.
3) Ubuntu is not very 'Efficent' or 'Productive' as a server should be.
4) It is a liability and useability issue meaning not very user friendly to anyone who is even an avid Windows Client / Server User or administrator.
5) SCO UNIX is the TRUE server product of choice, not the 'Free' Linux Distro.
6) Linux is not unified. So with every distro certian steps need to be done in different ways.
 
Personally, I feel Ubuntu-Server is not as good as its derivitive, Debian. I switched from Mandriva just yesterday for my game server. With some regret and assumed a 'Server' product would be better than a desktop version. We noticed the client's latency (ping) has gone up by 15-20% or more and my LAN ping has gone from 2-15 to 30-45 or higher. Debian I feel is better even on a PIII 1GHz had lower latency then Ubuntu on a P4 2.8a GHz. Moreover: RedHat has a better known reputation and just as expencive as Windows XP Pro is, they went in the wrong direction. Dell and HP/Compaq were pushing Linux Enterprise Servers because they had a pact because Microsoft was expencive in Large Enterprises.
 
I am a veterian in computer consulting (12 years aprox.) and only got into the Unix/Linux sceen as another alternitive product extencively since 2005. Frankly, I do not see what all the fuss is about aside from Price. Even so, large enterprise business is not going to change Kernel because their IT people are not knowledgeable enough to impement such a drastic change in their Server / Desktop policies.
 
That is my two-cents.
Krillin
:-s

---

### Post by lodp on 2008-06-25
The question was whether Ubuntu wasn't so represented as well in comparison to other Linux distros. Not in comparison to Windows or other Unixes..

Nonetheless..

> 1) Not very well supported with Manufactures. (See anything in stores for 'Linux'?)

The main problems with drivers is devices you have little need for on a server, like graphics cards, printers, scanners and that kind of thing. So I don't think that's a real problem there.

> 2) Clients will be at the mercy of the consultant who installs it.

But the same is true of any other OS, isn't it? It's not like operating a Windows 2003 Server doesn't require any skills.. you'll always have to have somebody with the right skills to operate a system.

> 3) Ubuntu is not very 'Efficent' or 'Productive' as a server should be.
 You'd have to flesh that out a bit more..

---

### Post by molotov00 on 2008-06-25
Also, companies tend to buy software/services and then look for the OS that support them. Whereas hobbyists or price sensitive users will look for ways to get Windows apps to work on Ubuntu, the corporate customers will just use Windows because that is the OS that is supported by the software.

Price matters much less because something that "just works" more than pays for itself in terms of saved time.

lodp:
The original poster asked for opinions. You got a well-informed opinion from Krillin. Your post is very defensive of Ubuntu but that really isn't the point of this discussion. The poster wants to know "why" not "why are you pissed about" Ubuntu's lack of acceptance.

---

### Post by lodp on 2008-06-25
> The original poster asked for opinions.

yes, but he specifically asked why ubuntu wasn't deployed so often **in comparison to other linux distros**, not in comparison to windows or other unixes (which is what Krillin wrote about). so we're actually taking the thread off-topic here.
> 
You got a well-informed opinion from Krillin. Your post is very defensive of Ubuntu but that really isn't the point of this discussion. The poster wants to know "why" not "why are you pissed about" Ubuntu's lack of acceptance.


i'm not pissed about ubuntu's lack of acceptance. i just disagree on some of the points Krillin made, so i wrote down my opinion. i don't see what's wrong with that, it's just an exchange of thoughts..

---

### Post by bloodniece on 2008-06-25
We use Ubuntu as a LAMP server at my work.  We could've just as easily gone w/ Debian, but the Ubuntu community is what places it ahead for us.

We also have a FreeBSD SMB and NFS server which also runs our iSCSI targets.  QNX runs our voicemail. Yeah, we use QNX, weird , huh? It never ever needs anything, ever. QNX is a really solid POSIX OS.

---

### Post by gtdaqua on 2008-06-26
> **Krillin said:**
> 
....

I am a veterian in computer consulting (12 years aprox.) and only got into the Unix/Linux sceen as another alternitive product extencively since 2005. Frankly, I do not see what all the fuss is about aside from Price. Even so, large enterprise business is not going to change Kernel because their IT people are not knowledgeable enough to impement such a drastic change in their Server / Desktop policies.
 
That is my two-cents.
Krillin
:-s

Obviously, you have not worked in multi-nationals where Linux is extensively used on infrastructure and is increasing steadily. And also these sectors do not usually hire private consultants to implement Linux-based computing systems. Another reason why you have very little exposure to this side of the sector. They do hire consultants for networking, security, design etc - but not specific for migrating to linux.

The fuss about linux is that it is stable and several web servers have a fantastic uptime upto 7 years. They do not require much updates and frequent restarts as windows does. Also, it does not require frequent administrative intervention. 

Plus, you've gotta be a techie yourself to be able to suggest Linux. Not just a business analyst looking at ROI and TCO. Thats not the only way you should always go!

Am not surprised about your extensive consultancy, but only merely pointing why you have not come across linux extensively in your experience. If you were a sysadmin responsible for 100s of servers doing several things, then linux will start looking more and more attractive to you.

To the initial poster of the thread: Ubuntu is relatively new and picking up. Its built on the proven-solid architecture of Debian. A lot of people here like Debian more. But what does Ubuntu offer more? Its this very community support that you get. These forums are very very active with a lot of discussions and friendly people around to help you. Makes a good choice if you want an excellent support for your ubuntu-based servers/systems.

---

### Post by caraboy on 2008-08-07
I use ubuntu server since version 6.06 LTS on my production server. No major problems so far. 

I think it`s a matter of getting used to a new os on the market. I use Ubuntu every day on my desktop PC, beying familiar with it was also easy to set it up on my server. 

It`s still a young OS, give it some time, I am sure it`s market share will grow on the server-side in the near future.

---

### Post by windependence on 2008-08-07
Well I have to say, and I'm not trashing Ubuntu in any way, that my experience in production has not been as good as CentOS, SuSE, and especially FreeBSD. Sometimes Ubuntu server just will not load on hardware and the others load and run flawlessly. I have a brand new dual quad core box with a SuperMicro board that loads Ubuntu just fine but after it's running for a few hours it just kernel panicks. I have no idea why, and I don't have time to try to troubleshoot it. All the hardware is plain vanilla on purpose but it looks like I will be using something else.

That being said, I WANT Ubuntu to work. I like the fact that I can get a distro without all the junk in it, and the package manager is superb, but if I can't keep it stable all that doesn't matter. 

I was using it as a base for VMware Server, but now that ESXi is free, I will probably not be using any Linux on any of my servers and sticking with *BSD which.....well just works, and is designed much cleaner than any Linux distro. For things I must use Linux for, I will conintue to try Ubuntu before other distros, hoping they will fix some of the problems I have encountered.

Also to the OP's question, much of the software out there is supported on RedHat, SuSE, or CentOS but not on Ubuntu, so I think that's why uptake seems slow. That will change I am sure.

-Tim

---

### Post by StickyStyle on 2008-08-07
I use Ubuntu 6.06 on all my servers (in a while I will start evaluating 8.04).  
I had been a long time debian guy before, but ubuntu's LTS release cycle is what made me switch.  Knowing for a fact that I don't have to think about a planed upgrade on my production servers till 2011 rather than debian's one year after each stable (after the sarge mess) release means that they are only supporting security updates for about two years for each version - that's a lot of upgrading for me.

All my servers are server class dell boxes that I have never had any compatibility issues with, so that's never been an issue for me.  

Also we don't use any vendor software (such as Oracle) that dictates what distro we have to use, everything is FOSS, compatible with ubuntu, or built in-shop.  So that is a bit of a luxury I have that I know others may not.

---

### Post by windependence on 2008-08-07
I agree, 6.06 has been way more stable than any of the newer releases for me. Most of my Zimbra boxes are running 6.06.

-Tim

---

### Post by Krillin on 2010-03-30
When my clients hear "Linux" they would rather hall *** in the other direction. Having to learn a new operating system is not on their agenda these days.

I am all for 'Linux' and been trying to push a cheaper more cost effective product with clients. But as I stated earlier. The client will be at the mercy of the consultant. They do not want to have to call me every time they need something done, even I am too busy to be bothered to change permission on a folder every time they have a change or hire new staff members.

Let's face the facts boys. Liniux-Ubuntu is NOT very user friendly as it is with the day-to-day operation as a Windows Box is.

Everyone has their opinions but my statements are NOT opinions, they are actual comments from clients when given their choice of operating systems for a new computer or server. Moving a client to Windows to Linux is a daunting task and no one will pay for in our current economy.

As for those who must pick apart my statement, especially ones no where near my area of the good ole USA. Get a life, stick to your geographical location and sector your region not others.

Bare in mind, most of my clients are emergency services (Fire, Police etc). So if you want to pick apart my statement again understand where I am coming from before you make yourself look like ***... But it is apparently too late for that though. Oh Well.

Krillin
:popcorn:

---

### Post by steev182 on 2010-03-30
That's probably the problem.

If you were consulting for companies which host high load websites or webapps, you'd see more often than not that they are running Linux for their servers.

However, I haven't seen a Directory server admin app as easy to look after as Active Directory, and I think this is one thing stopping Linux in this area.

The thread was asking why ubuntu as a distribution isn't as widespread on servers as it could be. We know how prevalent Linux is for servers.
The last company I worked in had a mix between RHEL for live web and application servers, SuSE enterprise Linux for the data warehouse, CentOS for staging environments and the developers and techy users liked to install a mix of Ubuntu, Debian, Gentoo. 

I think the main thing with production servers is that the Directors like to know that there's that last line of support, so paying Red Hat or Novell throught the teeth for it is a safe option for them and reduces risk a little bit.

---

### Post by jrssystemsnet on 2010-03-30
> **Krillin said:**
> 5) SCO UNIX is the TRUE server product of choice, not the 'Free' Linux Distro.Wow.  Just... wow.

I'm sure the rest of what you said has some validity with the specific market you're familiar with, but this statement makes it pretty clear how narrow the blinders you're wearing are.

"SCO UNIX is the TRUE server product of choice"?  Never thought I'd hear *that* one... OpenServer's still around in a lot of large enterprise simply because "it's what they always had", but it's essentially a dead platform with no major releases in the last five years.  It's also saddled with a parent company that's filed for Chapter 11 and doesn't look like it's much longer for this world.  You don't see many *new* installs of OpenServer... and no, a new Taco Bell store in your neighborhood doesn't really count as a "new" install; it's just another office in the same enterprise that still has the same old legacy dependencies.


> Even so, large enterprise business is not going to change Kernel because their IT people are not knowledgeable enough to impement such a drastic change in their Server / Desktop policies.Redhat's P&L's would seem to indicate otherwise.  IBM's, too, when you come right down to it.

For reference, I'm a consultant who's been in business since '97, I started selling FreeBSD (to both local small/medium business and to internet hosting outfits local and remote) in 2002, and I'm still selling FreeBSD and Ubuntu Server now... along with Windows.  They all have their place, if you actually understand their strengths and weaknesses.

---

### Post by steev182 on 2010-03-30
Reading Krillin's comments more, I feel like he's a time traveller from 1992 :D

---

### Post by jrssystemsnet on 2010-03-30
Answering the OP's original question: you don't see much Ubuntu Server, comparatively speaking, because it's basically Debian and Debian's been around longer.  So, most of the folks who wouldn't reflexively pick RHEL or CentOs to begin with are already familiar with Debian and have a track record with it - so why switch downstream to a Debian variant?

Ubuntu Server is gaining traction now, IMO, for largely the reason that Windows gained traction in the server market - because it's made big inroads in the desktop Linux market, so Linux guys who are familiar with it on the desktop tend to favor it in the server room.  I certainly fall in that camp; sure, I *could* go with Debian, but since I already support my own Ubuntu desktop installs, why saddle myself with more different platforms to support than I absolutely need?  If Ubuntu Server didn't perform well or reliably for me, I wouldn't use it; but it does, and as an added bonus it's the same distro I'm familiar with on the desktop, so it makes a lot of sense for me to deploy it.

I also thoroughly approve of the regular release cycle and the LTS support policies, and I've had really good results with in-place major version upgrades, so it's a no-brainer for me.

Some of the stuff Canonical is pushing now may make bigger inroads in Linux admins who already have a different preference of distro now, though; I haven't played with it myself yet, but the promise of Ubuntu Server Enterprise Cloud is pretty intriguing, and if it hangs together well as a useful and reasonably easy to deploy product, it may turn a lot of heads over the next few years.

---

### Post by spynappels on 2010-03-30
I have currently got approximately 50 Ubuntu Servers deployed in numerous locations in production systems. I have found them stable and easy to work on, and will continue using Ubuntu Server.

I did come from an Ubuntu Desktop background though....

These forums are one of the reasons I like Ubuntu,it is easy to get help when testing and developing new setups.

---

