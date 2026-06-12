---
title: "Why everybody want a firewall ??????"
date: 2005-08-05
forum: Server Platforms
---

### Post by frodon on 2005-08-05
Well, I create this thread because I am really surprised by the number of users who want to install a firewall.
I know it's a reflex when you come from windows BUT if you don't have services on your computer you really DON'T need to have a firewall. When someone ask for a good firewall the first answer should be : why do you want a firewall ?
(my computer run 24h-24h on internet for 5 month without any problem ... and without firewall)

I would like this thread to be a discution about the utility of a firewall under linux, of course there's some good reasons to have a firewall and I would like noobs to know when and why use a firewall.

thanks for giving your opinion. :) 

edit : I will not be able to answer the next 2 week.

---

### Post by dave9191 on 2005-08-05
Even if you have no running services you might still want to hide your computer from the internet. Instead of having closed ports, have stealthed ones. Or if your computer acts as a gateway for a network. Or possibly you wish to run things like apache and keep it on localhost only. Just in case you messed up on the configuration or there is some exploit out there. 

And with iptables well configured you can try and stop things like dos attacks and packet spoofing. Even if it might not be needed on a default ubuntu install, it can still provide peace of mind and give you protection if you mess something up :)

Dave

---

### Post by frodon on 2005-08-05
[QUOTE=dave9191]Even if you have no running services you might still want to hide your computer from the internet. Instead of having closed ports, have stealthed ones. Or if your computer acts as a gateway for a network. Or possibly you wish to run things like apache and keep it on localhost only. Just in case you messed up on the configuration or there is some exploit out there. 

And with iptables well configured you can try and stop things like dos attacks and packet spoofing. Even if it might not be needed on a default ubuntu install, it can still provide peace of mind and give you protection if you mess something up :)

Dave[/QUOTE]
Yep dave9191,  I aggre with you.
Firewall is needed when you have a local network or when you run services (like apache, FTP, SQL, ...), but what i want to say is that if you just use internet (web browser, amule, bittorent, IRC, ...) and don't have shared connection or local network .... there's not any security problem. Of course if you're really really unlucky a good hacker can always introduce in your computer (even if you're running firestarter).
Also very often just changing the common used ports (80 for exemple) is more efficient than a firewall, maybe it should be the first reflex for security before installing a firewall.

Even if i haven't a firewall for the moment i'm going to add one because i'm going to open my FTP server to anonimous access and it's the only reasons why i'm going to do that.

thanks dave for the interrestings infos you gave, I hope noobs will understand why and when use a firewall (however peace of mind could be a good reason  ;-) )

---

### Post by bin on 2005-08-05
Yup to all that - plus of course, not all Linux distros behave the same. Some DO install open services which you may or may not know about - some live cd's as well. So, having a physical firewall is probably a lot more beneficial than software/iptables alone.

in light 

bin

---

### Post by trash on 2005-08-05
> Yep dave9191, I aggre with you.
Firewall is needed when you have a local network or when you run services (like apache, FTP, SQL, ...), but what i want to say is that if you just use internet (web browser, amule, bittorent, IRC, ...) and don't have shared connection or local network .... there's not any security problem. Of course if you're really really unlucky a good hacker can always introduce in your computer (even if you're running firestarter). 

Thats kinda scary considering most newbs opt for firestarter because of it's awesome GUI.
I've mentioned it before but got no responses on this forum about IPKUNGFU, that claims an easy install/setup and is already available in Debian unstable for x86,ppc and amd. Easy install/setup makes it makes it a better candidate than Shorewall, which is anything but easy.
Can anybody tell me why IPKUNGFU is being overlooked?

---

### Post by LordHunter317 on 2005-08-05
[QUOTE=dave9191]Even if you have no running services you might still want to hide your computer from the internet.[/quote]Which a firewall doesn't do.

> Or if your computer acts as a gateway for a network.Which for all intents and purposes, would be consider a service in the OP's post.

> And with iptables well configured you can try and stop things like dos attacks and packet spoofing.No, you really cannot.

[quote=frodon]Also very often just changing the common used ports (80 for exemple) is more efficient than a firewall, maybe it should be the first reflex for security before installing a firewall.[/quote]Except that has **no** security value whatsoever.

---

### Post by dave9191 on 2005-08-05
[QUOTE=trash]Thats kinda scary considering most newbs opt for firestarter because of it's awesome GUI.
I've mentioned it before but got no responses on this forum about IPKUNGFU, that claims an easy install/setup and is already available in Debian[/QUOTE]

Every single firewall application in Linux that I have ever come accross is just a front end to iptables. Iptables are used on high quality hardware firewall solutions. Firestater and Ipkungfu just setup the iptables scripts. So it doesnt matter too much which you use, as long as they configure iptables properly. Best thing to do is write your own iptable scirpts and cut out the gui, you can set up anything you want, but its not for the faint harted and needs a good understanding of how to edit config files :) So not for beginers. 


[QUOTE=bin]So, having a physical firewall is probably a lot more beneficial than software/iptables alone.
[/QUOTE]

Having a **well configured** iptables on your machine or having a hardware one shouldn't make too much difference. But it might be benefcial to setup a seperate computer with a minimal linux distro for routing and firewall. As whatever changes you do to your own machine will not effect your security. 

And if you are in search of a good firewall, you are better of using an old computer rather then buying a hardware firewall. You will have more control, superior firewall capabilities and it will be cheaper.

---

### Post by LordHunter317 on 2005-08-05
> **dave9191]Every single firewall application in Linux that I have ever come accross is just a front end to iptables.[/quote]That's because writing a kernel-leve said:**
> Iptables are used on high quality hardware firewall solutions.By a select few vendors without much marketshare.

> Having a **well configured** iptables on your machine or having a hardware one shouldn't make too much difference.Yeah it does.

As a general rule, the value of host-based filtering is less than doing network-based filtering at the network ingress/egress points.

> And if you are in search of a good firewall, you are better of using an old computer rather then buying a hardware firewall. You will have more control, superior firewall capabilities and it will be cheaper.If that's really true, then why do so many companies buy Cisco PIXes?

---

### Post by dave9191 on 2005-08-05
[QUOTE=LordHunter317]If that's really true, then why do so many companies buy Cisco PIXes?[/QUOTE]

I was refering to typical home users and small networks, I should have really mentioned that. Cisco products are capable of more through put then an old beat up computer with a couple of NIC's. They also provide high quality firewall capabilities. And by all means get one for your home machine, if you have a couple of thousand pounds lying around spare. 


Now compare iptables on my machine to a cheap Linksys or Netgear firewall solution. Its far more flexible. And having a dedicated computer on your network as a firewall / router compared to firewall / router products that are in the price range of typical home users. 

Dave

---

### Post by sooqing on 2005-08-05
i am running without a firewall too.. and i managed to get my bsd pc to remain steath by hacking the kernel, eg. enable tcp_drop_synfin option, etc..

---

### Post by frodon on 2005-08-05
[QUOTE=trash]Can anybody tell me why IPKUNGFU is being overlooked?[/QUOTE]
Do you think it's a better alternative than firestarter for noobs, can you give me some reasons which make you prefer IPKUNGFU than another userfriendly solution ? (i'm curious  ;-) )

Endeed the best solution to get a really good firewall is to use an old computer as router/firewall, hardware firewall is also a good solution, ..... but I keep in mind that really few users need a good firewall .... how many of us run servives or have a local network ? 

Do you think (like me) that for basic use (no services, no connection share, no local network) firestarter is useless ?
Linux kernel is enough strong for this kind of use (it's just my opinion, maybe someone more knowledgable could confirm that).

---

### Post by DW5 on 2005-08-05
I just installed Firestarter today.  I noticed constant inbound traffic on my nic applet.  Being a newbie end user, I wondered what it was.  I browsed around and found some instructions about running lsof -i, which I did, but didn't trust myself to really be understanding what lsof -i was telling me.  So, I thought, maybe I should put in a firewall in case something weird is happening.  Afterall, I had just piddled with postfix to get mutt working so I could have cron send me some end of month reminders (not that you care), but hey, what if I did something wrong and ....  

Firestarter told me that the only service I had going with an established connection was IPP, (which is what lsof told me, too, but I was reassured). I interpret that as a bunch of networked printer babble.

 Will I run it constantly?  Probably not, I'm just an end user.  But it's nice to think that I have it if I suspect something uncommon is happening and don't have the time to search around on the web for the right instructions to sniff it out.  That might be purely assanine thinking (as in someone saying "Yeah, and by that time it's too late"), and I'm ready to stand corrected, but that's the state of my mind at the moment.

DW

---

### Post by trash on 2005-08-05
> **frodon]Do you think it's a better alternative than firestarter for noobs, can you give me some reasons which make you prefer IPKUNGFU than another userfriendly solution ? (i'm curious   said:**
> 

I've never tried it, thats why I have asked about it.
Hearing how easy it is and that it is as I said available for x86,ppc and amd, where as shorewall is not easy and firestarter is not available for ppc(broken), and it is being used in debian repos. Hence my question.

[QUOTE]Do you think (like me) that for basic use (no services, no connection share, no local network) firestarter is useless ?
Linux kernel is enough strong for this kind of use (it's just my opinion, maybe someone more knowledgable could confirm that).

I never said firestarter was useless(just want to clarify that), in fact I liked it. I found Ipkungfu after looking for a firewall for ppc and finding shorewall too complicated and firestarter broken. Why I started looking was because of running services, otherwise I wouldn't care as much. Yes I could run a second machine to deal with the firewall as in the past, but for my needs now it kind of seems like overkill hehe.

---

### Post by dave9191 on 2005-08-05
[QUOTE=frodon]
Do you think (like me) that for basic use (no services, no connection share, no local network) firestarter is useless ?
Linux kernel is enough strong for this kind of use (it's just my opinion, maybe someone more knowledgable could confirm that).[/QUOTE]


I agree that linus without any services like a fresh ubuntu intsall doesnt really need a firewall. However, having ip tables configured wouldnt hurt either. And it would provide the protection should a user who doesnt really know what they are doing start enabling services. So an added saftey net so to speak by default would be nice IMO.

Dave

---

