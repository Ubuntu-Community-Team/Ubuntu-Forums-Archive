---
title: "Ubuntu as SME server: a plea from the stupid"
date: 2005-01-17
forum: Server Platforms
---

### Post by TonyS on 2005-01-17
Hello gentlepersons,

I write as a linux server owner and user, but confess right now I'm NO Unix admin. However, I've had this on my mind for some time, and thought you might find some value in it.

Are you familiar with SME Server ([www.contribs.org](www.contribs.org)), formerly known as e-smith? 

I think this is a truly outstanding concept, providing small organisations like mine with powerful server functions that at least equal MS Server, and do so on very well on cheap hardware. 

But I hear you say, that's just linux... indeed, but the cool part is that SME Server can be installed and administered by The Ignorant (such as me) with very little difficulty. The install is very straight-forward, asking the very minimum of questions, then all administration is done via a web interface. With almost no knowledge you get an instant web server, mail server, file server, VPN server, etc. Everything is integrated, automatic and SIMPLE.

This means it is a brilliant fit for non-profit organisations, schools or small businesses with scant IT resources, where some poor ill-equipped untrained person like me has to do the best they can with very little, and only at the expense of their "real" work. This must be even more so in third world countries.

So anyway, the problem with SME Server is that, following various corporate shenanigans,  the community surrounding it is in disarray, documentation is scarce and scattered, and there seems every chance that the whole thing might fall over, at least as a living Open Source project.

It seems to me that Ubuntu has everything SME Server lacks in terms of community and momentum, and a number of advantages in its technology too (eg. Debian vs Redhat base).

Is there any way of making an SME Server - like version of Ubuntu? A server that can be installed and run by genuinely non-techies? I think this would make the world a better place by genuinely empowering small tech-poor organisations worldwide...

Cheers,

Tony Sutorius
Wellington, New Zealand

---

### Post by nocturn on 2005-01-18
Hello Tony

Welcome to the community, and I am glad you are looking at Linux.

Ubuntu has nothing like this, but I still suggest it as a server for your purpose.

What Ubuntu has is a good community which can help you through many of the tasks you will need to do on your server.  By doing these tasks yourself, and not via a very simplified web-interface you will acquire more knowledge over time helping you later on when something goes wrong (for example, booting fails), you will know the basics how to repair things yourself.

Good luck

---

### Post by TonyS on 2005-01-19
Hi Nocturn.

Thank you for taking the time to reply to me.

I appreciate your sentiments, and agree that Ununtu's community is  a great resource.

However, I do not subscribe to the common view that learning the intricacies of Linux is inherently good for the soul, and an appropriate built-in hurdle for prospective new users... or rather, it may, but this philosophy drastically reduces how much good Linux can do in the wider community.

I run a small business, and am involved in a number of community-based voluntary organisations. I use many, many tools to do my work. I have a cellphone, but no idea how the cellphone network works. I have a fax machine, which is kinda neat (and that's pretty much the extent of my expertise in that area!). The international telephone network rocks, but I haven't got a clue how to build one.... 

This is not to say I have nothing to contribute to a community such as this one... I know a lot about marketing, communications and community-building. Pretty relevent I reckon.

My point in all this is that, in the same way that Ubuntu makes a Linux desktop viable for pretty much any PC user, it ALSO has the potential to place the power of a fully-fledged SME server into the hands of many organisations who will not otherwise have access to that power, because they have neither the money to buy Windows Server, nor the resources to grow an in-house linux server expert.

With the power to impliment powerful servers easily, many poor organisations have the power to do tremendous social good in the world. I think this is a fantastic prospect. 

So, I propose that Ubuntu apply its evident "linux for everyone" philosophy to the the SME server space.  Make it easy!

Cheers,

Tony Sutorius
Wellington, New Zealand

---

### Post by nocturn on 2005-01-20
[QUOTE=TonyS]Hi Nocturn.

Thank you for taking the time to reply to me.

I appreciate your sentiments, and agree that Ununtu's community is  a great resource.

However, I do not subscribe to the common view that learning the intricacies of Linux is inherently good for the soul, and an appropriate built-in hurdle for prospective new users... or rather, it may, but this philosophy drastically reduces how much good Linux can do in the wider community.

I run a small business, and am involved in a number of community-based voluntary organisations. I use many, many tools to do my work. I have a cellphone, but no idea how the cellphone network works. I have a fax machine, which is kinda neat (and that's pretty much the extent of my expertise in that area!). The international telephone network rocks, but I haven't got a clue how to build one.... 

This is not to say I have nothing to contribute to a community such as this one... I know a lot about marketing, communications and community-building. Pretty relevent I reckon.

My point in all this is that, in the same way that Ubuntu makes a Linux desktop viable for pretty much any PC user, it ALSO has the potential to place the power of a fully-fledged SME server into the hands of many organisations who will not otherwise have access to that power, because they have neither the money to buy Windows Server, nor the resources to grow an in-house linux server expert.

With the power to impliment powerful servers easily, many poor organisations have the power to do tremendous social good in the world. I think this is a fantastic prospect. 

So, I propose that Ubuntu apply its evident "linux for everyone" philosophy to the the SME server space.  Make it easy!

Cheers,

Tony Sutorius
Wellington, New Zealand[/QUOTE]


Hi Tony

I understand what you are saying.    Yet there is a fundamental difference between a computer (specially a server) and consumer electronics such as a VCR or mobile phone.  If you are not capable of programming your VCR, you can still record shows, but you are not going to come home and find said VCR hacked and used for illegal purposes.  

This is the unfortunate reality of computer systems these days and especially Microsofts 'click-next-to-install' dogma is making things much worse.

If you need a drop-in server for internal corporate use (behind a good firewall) you can use a product such as you described.    But when exposed to the Internet, security considerations take over.  You will need to ensure that your server is defended from outside attacks, you need to be capable to detect incoming attacks and to clean up a compromised host.  These are not things that can be done through a web-gui, neither in windows nor *nix.

Currently, the best thing for a non-profit organisation would be a server, hosted with a technically skilled admin for free (or little money).  It is in my planning to offer free hosting in this way a couple of years down the road (when I have the money and physical space to set up the infrastructure).

All this said, I'm looking arround for an alternative to this for you.

Kind regards

---

### Post by nocturn on 2005-01-20
Does this help:
[http://freshmeat.net/projects/yeslinux/](http://freshmeat.net/projects/yeslinux/)

---

### Post by nocturn on 2005-01-20
Or this:
[http://www.sol-linux.com/Private/SoL/](http://www.sol-linux.com/Private/SoL/)

---

### Post by nocturn on 2005-01-20
And another one:
[http://www.clarkconnect.com/](http://www.clarkconnect.com/)

---

### Post by TonyS on 2005-01-21
Hi Nocturn,

OK, this is a good debate. Thank you for being a good sport about it... I appreciate that I am paddling at the very shallow end of your guy's pool!

A point I wanted to respond to in your comments was the suggestion that security issues are so complex and dynamic (I'm paraphrasing) that individual specialist admin knowledge is required to keep any internet-connected server safe.

You know better than I precisely what these issues are. I am struck though by how similar this sounds to the arguments one used to always hear in linux forums about GUIs... a linux environment is a complex place with many interactions amongst variable components, and if you want to manage it properly you need to overcome your dependence on pretty pictures, they used to say. Harden up, get down with the command line...

At a purely conceptual level, it strikes me that securing a server environment SOUNDS like something that might best be achieved in a communal fashion... with so many new threats coming from so many new directions, on the face of it one would imagine keeping ten thousand identical or near-identical servers  secure might not be much harder than keeping one secure, and presumably the workload could be much more widely spread.

If Ubuntu had a "plug and play" server install option, a "server for dummies" mode if you like, offering a broad but specific range of services and functions designed to be controlled (but not re-engineered) by semi-skilled admins (say, using a web interface with sufficient but highly finite options), couldn't security be handled collectively, and updates rolled out automatically?

Further, it looks to me like this philosophy is the one behind Ubunu for the desktop... strip it back, standardise, but make sure it works painlessly. Makes tremendous sense to me to extend that notion into the SME server space, too.

Cheers,

Tony

---

### Post by nocturn on 2005-01-21
[QUOTE=TonyS]
You know better than I precisely what these issues are. I am struck though by how similar this sounds to the arguments one used to always hear in linux forums about GUIs... a linux environment is a complex place with many interactions amongst variable components, and if you want to manage it properly you need to overcome your dependence on pretty pictures, they used to say. Harden up, get down with the command line...
[/QUOTE]

The thing with GUI's is that they are often limited compared to a configuration file (some programs like Apache have so many possible options that it is impossible to represent these in a GUI).  
GUI's also tend to oversimplify things, introducing mistakes that may not be apparent at first, but can have serious consequences.  The encourage people to do things they really do not understand.

Many admins learn to appreciate a CLI especially when the server in question is located far from your location.    I used to do remote system administration for a bunch of companies located in a radius of about 300 km.    Yet I could do everything from my desk.

> 
At a purely conceptual level, it strikes me that securing a server environment SOUNDS like something that might best be achieved in a communal fashion... with so many new threats coming from so many new directions, on the face of it one would imagine keeping ten thousand identical or near-identical servers  secure might not be much harder than keeping one secure, and presumably the workload could be much more widely spread.

If Ubuntu had a "plug and play" server install option, a "server for dummies" mode if you like, offering a broad but specific range of services and functions designed to be controlled (but not re-engineered) by semi-skilled admins (say, using a web interface with sufficient but highly finite options), couldn't security be handled collectively, and updates rolled out automatically?


The problem with security is that to do it well, it is not a purely technical problem.  You cannot just install a program and be safe.  Your security is build layer upon layer and often the human factor proves to be the weakest layer.  
For example, an intrusion detection system only makes sense if there is someone checking its output.  That person needs to understand what he is seeing and be able to act if something happens.  It is not a security measure by itself, but a complement to firewalls etc.

Any security has to be tuned to your particular situation.    Your server will live in a network, so it will inherit the (in)security of your entire network.  If someone breaches your border router, what happens to the machines inside the net?  
Let's say your server is 100% secure, but it shares data to 5 workstations which are vulnerable, in the end your data will still be compromised.  You need to think of each of these scenarios.  
Also, if a host is compromised, what are the effects?  If the host is in a DMZ, the damage can be limited to that zone only, sparing the machines in the LAN.  But you need someone capable of setting up a DMZ for this...  so you are back to square one.

---

### Post by TonyS on 2005-01-23
Hi Nocturn,

I just want to make sure I understand... your view is that the sort of "server appliance" model I've outlined cannot be engineered to be intrinsically secure when used by non-expert admins?

Which means that you see SME Server, DarkConnect etc, which are obviously designed with the non-expert admin in mind, as inherently insecure when used as intended?

Should I be alarmed about my own servers' security?

Tony

---

### Post by nocturn on 2005-01-24
[QUOTE=TonyS]Hi Nocturn,

I just want to make sure I understand... your view is that the sort of "server appliance" model I've outlined cannot be engineered to be intrinsically secure when used by non-expert admins?

Which means that you see SME Server, DarkConnect etc, which are obviously designed with the non-expert admin in mind, as inherently insecure when used as intended?

Should I be alarmed about my own servers' security?

Tony[/QUOTE]

If you push E-mail, fileserving, webbrowsing and all on one server that is not managed by an admin (possibly remotely).  Yes I think it is insecure.

Should you be alarmed, that depends on what you are running, how well your firewall works.   With something like this on Linux you're probably still better of then any Windows server.

---

### Post by machiner on 2005-01-26
Admins don't sleep because of the alarm level they have at applications attempting to do the job they need.

All-in-ones are asking for trouble. Lack of knowledge in this area will see your network live a painful existence. If you don't want to learn it, or employ someone that does, then you have no business running it.

Do yourself a favor -- learn the stuff, hire some hot-shot high-school kid, or leave this  (and there are some others) forum open at all times.

I don't mean to scare you - but the 10 year old next door will own your network inside of a day if you don't adopt necessary training and proceedures to secure your stuff.

Networks are NEVER 100% secure, all-in-one solutions beg for trouble, and non-diligent admins might just as well stay in bed.

However - you are MUCH better off in Linux, but that is no excuse for apathy, or, reliance on an application.

Hire that kid today.

You cannot hop behind the wheel of a car without learning something of its functionality first. I can appreciate your desire to NOT be the end-all admin of his time, but as an ex sysadmin, network admin - (NT) I can tell you right now - you are begging for trouble.

There are many highly qualified personnel taking part in this forum that will help you - without expectation.

Keep saying this to yourself:

65,535, 65,535.....the 10 year old down the street has the master key to all of those doorways.  I'd be pretty damned diligent.

---

### Post by jinx099 on 2006-07-21
How about instead of telling people that they are not good enough to be their own admin, give advice on steps to take to harden security.  I'm the type of person that learns by doing, so tell me what I should be doing.  I have a m0n0wall firewall/ router and an ubuntu server behind it.  How can I tighten security on my firewall (rules?) and ubuntu server box?

---

### Post by TonyS on 2007-05-11
BUMP

Guys, I've stumbled back on my old post, and wonder how the community's thinking has evolved in this area?

Cheers,

Tony

---

### Post by gso on 2007-05-24
I am certainly interested in this as well TonyS.  I am, however, a veteran Linux user/admin and a software developer and prefer to have servers admin'd via more simple interfaces such as SME Server for a couple of reasons: First, it makes my life simpler and reduces costs for my customers.  Secondly, it helps to provide a higher level of security as it removes the margin of error that is often experienced by even experienced admins.  I've found SME Server to be a splendid blend of configurability and customizability (I've customized it quite extensively and run Vmware Server from it in various corporate settings).

It would be quite nice to see Ubuntu take up the torch and carry this paradigm forward so that we can A) benefit from a strong and (perhaps more than SME Server) active community and B) have a little quicker access to a much larger plethora of packages via dpkg/apt-get.  This would really be a spectacular combination.

If this doesn't happen, I'm truly tempted to make it happen, of sorts, myself if time and monetary resources could become less scarce.

---

### Post by johnman145 on 2007-05-24
> **nocturn said:**
> 
If you need a drop-in server for internal corporate use (behind a good firewall) you can use a product such as you described. But when exposed to the Internet, security considerations take over. You will need to ensure that your server is defended from outside attacks, you need to be capable to detect incoming attacks and to clean up a compromised host. These are not things that can be done through a web-gui, neither in windows nor *nix.


From your post i can see you know a lot more then me about computers. But can you explain why the configuration needs to be complicated? I still don't understand why i have to do all sorts of complicated things when i just want a php+mysql+apache server. Imo, if the configuration is complicated, the chance of a mistake increases. I would rather have a less powerful interface which is very easy to configure safely.

To illustrate this, i have briefly looked at the configuration of the ubuntu firewall and it looks intimidating and confusing. If i look at the configuration of my router's firewall i can block everything with a couple of simple clicks and create a safe network behind the router in minutes. Even if i mange to create a working firewall in ubuntu, i wonder if it will really be safe since everything just looks so complex.

---

### Post by elst on 2007-05-24
Samba 4 may be a big help, particularly for anybody interested in doing LAN server appliances, since it effectively consolidates the functions that people expect from LAN servers, and does them in a Windows-compatible way. Edubuntu is also an interesting alternative take on making network management workable for less technical folks, although it's still evolving. People have asked about modifying Edubuntu for small businesses, cybercafes, and other settings outside education, but AFAIK no actual development work has been done to that end.

---

### Post by mcp_dk on 2008-05-30
even if you push this to the limit i am sorry to say that i don't think Ubuntu will ever make a server that can match up to the SME server. The SMe is so different in the architecture than any other Linux server distro i have seen. The templating system in SME is complex but very usefull. Also to my belief the security of the SME is as good as any other server. Ofcourse as an admin you need to sit down and learn how your system works. But IMHO you don't have to hunt through various textfiles via the CLI.

Ubuntu is an okay server but in my eyes not a match for the SME server. Not many are. 

I am not saying its better or worse butthey are significantly different.

---

