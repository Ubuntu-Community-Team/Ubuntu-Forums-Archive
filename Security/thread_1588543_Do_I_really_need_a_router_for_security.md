---
title: "Do I really need a router for security?"
date: 2010-10-05
forum: Security
---

### Post by WeAreLinux on 2010-10-05
Good Morning

I've read that using your computer behind a router is a must for security because of the NAT+SPI firewall so naturally I became interested in getting one. The thing is, I don't need the other features routers have because I don't do wireless, & I only use one computer. So do I really need one? Do the security benefit(s) gained from using a router warrant spending $50+?? Wouldn't using UFW with default deny rule offer the same level of protection?

Also I want to use my Playstation3 online. What security risks will I be taking if I connect it straight to my modem, instead of through a router?

I don't know much about this topic, so all the information/opinions you can give would be very helpful.

Thank You

---

### Post by Rinzwind on 2010-10-05
Before we end up talking about if it is worth it...
>  I don't do wireless,& I only use one computer
and
> Also I want to use my Playstation3 online
are in contradiction.

If you want both your pc and PS3 to be able to connect at the same time you will need a router. Oh and your PS3 can connect through wireless. You can do it without a router but that would require you to switch cables whenever you need the other machine to access the web.

So it basically is not about if 50 dollars is worth it. You -need- it. Otherwise you are making your life more difficult: juggling with usb sticks to add content from your PC to your PS3, switching cables all the time.

And yes, to me it is worth the extra few dollars to get an 8 ports router but I have a desktop, a PS3, a NAS, a network printer and a notebook (wireless) on my router. 

You only need a 1 port with wireless to connect a PC and PS3. Hard to find; 4 ports w/o wireless is easier to find. These do no go for 50 dollars over here. 20 tops ;)

---

### Post by WeAreLinux on 2010-10-05
> **Rinzwind said:**
> Before we end up talking about if it is worth it...

and

are in contradiction.

If you want both your pc and PS3 to be able to connect at the same time you will need a router. Oh and your PS3 can connect through wireless. You can do it without a router but that would require you to switch cables whenever you need the other machine to access the web.

So it basically is not about if 50 dollars is worth it. You -need- it. Otherwise you are making your life more difficult: juggling with usb sticks to add content from your PC to your PS3, switching cables all the time.


Sorry. Let me clarify.

I basically only want to play games & stream movies/TV shows,etc. online with my PS3. Don't need to transfer files from PC to PS3. Don't need to use my PC & PS3 @ the same time. Don't really care about switching the cable back & forth between PC & PS3 since I've been doing that since the PS2 days without annoyance :D.

So the only reason I would buy a router is for security but if not much is gained, then might as well save my $$$. I really don't know much about the NAT+SPI firewall, so I hope the community here can help me decide.

---

### Post by dmizer on 2010-10-05
You can find routers that do not have wireless. They are also much cheaper than wireless capable routers.

For example: [http://www.newegg.com/Store/SubCategory.aspx?SubCategory=28&name=Wired-Routers&Order=PRICE](http://www.newegg.com/Store/SubCategory.aspx?SubCategory=28&name=Wired-Routers&Order=PRICE)

A router really makes life much easier with broadband access. In my opinion, it also makes things more secure.

---

### Post by Grenage on 2010-10-05
> **WeAreLinux said:**
> Do I really need a router for security?

No.



Routers can help, but they aren't 'really' security devices.  As long as you have a firewall on the PC, and common sense, you should be fine.  I don't know what sort of security the PS3 has.  Personally  I'd use a router, but spending £25 won't ruin me.

---

### Post by Rinzwind on 2010-10-05
> **WeAreLinux said:**
> Sorry. Let me clarify.

I basically only want to play games & stream movies/TV shows,etc. online with my PS3. Don't need to transfer files from PC to PS3. Don't need to use my PC & PS3 @ the same time. Don't really care about switching the cable back & forth between PC & PS3 since I've been doing that since the PS2 days without annoyance :D.

So the only reason I would buy a router is for security but if not much is gained, then might as well save my $$$. I really don't know much about the NAT+SPI firewall, so I hope the community here can help me decide.
Then you do not need one.

Changing cables would annoy me the hell though ;)

---

### Post by CharlesA on 2010-10-05
Indeed, you don't need a router if you are doing it that way.

As long as you have a firewall running on the PC when it's connected to the internet, you are going to be fine.

As a sidenote: If you do get a router, you don't really need an 8 port one, if you need more ports, get a wired switch and hook it up to the router.

---

### Post by wacky_sung on 2010-10-05
Indeed you do not need a router to feel secure but with additional router it add anoher layer of security for you such as most routers come along with their builtin firewall.Although it is not very impressive, yet it make it much tougher for cracker to find you within / perform a penetrate test trying to break into your system.It even make it much harder to crack if your NAT address go dynamic in which your cracker trying to locate you within the router. 

[http://www.webopedia.com/TERM/D/dynamic_NAT.html](http://www.webopedia.com/TERM/D/dynamic_NAT.html)

---

### Post by bodhi.zazen on 2010-10-05
If you do not use a router, enable your firewall

```
sudo ufw enable
```

You should then be just fine.

---

### Post by pricetech on 2010-10-05
Do you "need" a router ??? Apparently not.  Should you get one ??? Yes.

You've solicited opinions, so I'll give you mine.  I'd never connect to the Internet without a router with a good solid firewall built in.

Netgear, Linksys, TrendNet, are all good routers. Any other brands I either have no experience with, or extremely bad experiences with, so I don't recommend any others.

---

### Post by bodhi.zazen on 2010-10-05
> **pricetech said:**
> Do you "need" a router ??? Apparently not.  Should you get one ??? Yes.

You've solicited opinions, so I'll give you mine.  I'd never connect to the Internet without a router with a good solid firewall built in.

Netgear, Linksys, TrendNet, are all good routers. Any other brands I either have no experience with, or extremely bad experiences with, so I don't recommend any others.

Not at all.

A router performs 3 basic functions (without getting into the details).

1. Firewall (NAT).

2. Sharing an internet connection. If you have more then one computer you would use a router for tasks such as dhcp, a switch, etc.

3. Wireless (WAP).

Since the OP has a single computer, and has no interest in wireless, we do not need the functions # 2 or 3.

UFW will act as a firewall and is sufficient.

So there really is no need in this case for a router and adding a router does not increase security (over enabling UFW).

---

### Post by psusi on 2010-10-05
You don't need UFW either.  Unlike Windows, Ubuntu does not come with insecure server services installed by default.

---

### Post by cariboo on 2010-10-05
A router just gives me peace of mind, even if I didn't need more than 4 ports, which I do. I'd still use one.

---

### Post by bodhi.zazen on 2010-10-05
> **psusi said:**
> You don't need UFW either.  Unlike Windows, Ubuntu does not come with insecure server services installed by default.

No you do not "need" it, but with a direct connection (no router) I would advise it as the user may inadvertently install server apps, desktop sharing for example.

---

### Post by psusi on 2010-10-05
> **bodhi.zazen said:**
> No you do not "need" it, but with a direct connection (no router) I would advise it as the user may inadvertently install server apps, desktop sharing for example.

Yes, but I would think that if you do install something like that, you expect it to work, so either you will be wondering why it doesn't or open the firewall anyhow.

---

### Post by Rinzwind on 2010-10-05
> **bodhi.zazen said:**
> Not at all.

A router performs 3 basic functions (without getting into the details).

1. Firewall (NAT).

2. Sharing an internet connection. If you have more then one computer you would use a router for tasks such as dhcp, a switch, etc.

3. Wireless (WAP).

Since the OP has a single computer, and has no interest in wireless, we do not need the functions # 2 or 3.

UFW will act as a firewall and is sufficient.

So there really is no need in this case for a router and adding a router does not increase security (over enabling UFW).

He has 2 'computers': a pc and a ps3 ;)

---

### Post by bodhi.zazen on 2010-10-05
> **psusi said:**
> Yes, but I would think that if you do install something like that, you expect it to work, so either you will be wondering why it doesn't or open the firewall anyhow.

Yes and no, deskto sharing (VNC) is the most common crack on these forums, and is, IMHO, too easy to enable.

> **Rinzwind said:**
> He has 2 'computers': a pc and a ps3 ;)

Aye, but if you read the first post, there is no indication the OP wants to configure a LAN (ie the intention seem to be to use one at at time, direct connection to the internet, and save $$ ).

If one wishes to connect the two boxes from time to time, one can do so without a router.

---

### Post by endotherm on 2010-10-05
> **bodhi.zazen said:**
> No you do not "need" it, but with a direct connection (no router) I would advise it as the user may inadvertently install server apps, desktop sharing for example.
my thoughts exactly, which is why I have come to the conclusion that if you have to ask the question, then you should probably have one. not needed, but will help a non-technical user be as secure as possible without having to research the implications therein.

---

### Post by bodhi.zazen on 2010-10-05
> **endotherm said:**
> my thoughts exactly, which is why I have come to the conclusion that if you have to ask the question, then you should probably have one. not needed, but will help a non-technical user be as secure as possible without having to research the implications therein.

I agree 100 % , but, in this case, the OP is looking to save some $$, so I think the question is a bit better thought out then average and, IMO, we should provide support (to save $$).

If $$ were not an issue -> router FTW.

---

### Post by WeAreLinux on 2010-10-05
TY for the replies.

From what I can gather, I should be OK in a Linux environment with iptables enabled using ufw to configure. What about on a PS3 environment since I wont have access to a firewall?

I forgot to mention (actually I just found this out) that the DSL modem my ISP provided me have some firewall features built-in. It also have some features you would find in routers (Port Forwarding, Remote Administration to name 2). With the firewall set above Medium setting, I pass Sheild'sUp. So I'm guessing I'm already using a router/modem (even though there is no extra ports to hook up other computers to) without even knowing it?

If I do go down the route of getting a router. Does every router have a given set of security features or do they vary from brand to brand? What are the must security features I need to make sure it has? I see a store in my area have a Netgear wireless G router for only $30...I can prob. afford that.

---

### Post by CharlesA on 2010-10-05
Super slow connection = double post = blah.

---

### Post by CharlesA on 2010-10-05
I don't know how the PS3 does networking, but it should be fine as well.

As for the router, everyone one has a SPI firewall, and does NAT, and that's the very least that you need.

Should be fine, even with a cheap one.

---

### Post by psusi on 2010-10-05
Ok, here's a quick low-down.  Consumer routers these days perform Network Address Translation.  NAT was originally called ip masquerading and created by the Linux community as a way to share an Internet connection among multiple computers.  It involves having the computer with the Internet connection route packets between the Internet and the local network after translating the addresses in them so that the other local computer(s) can connect to servers on the Internet in such a way that the server thinks it is talking to the router, and the local computer thinks it is talking to the server, but they really are both talking to the router.  Thus effectively the local computer is masquerading as the router as far as the rest of the Internet knows.

As a SIDE EFFECT of this, computers on the Internet can not connect to computers on your local network, because there is only one publicly routable IP address and that belongs to the router, so they can try to connect to the router, but not to your computer.

A firewall is all about BREAKING normal network access on purpose.  NAT breaks it by accident.  Windows machines should not be connected to the Internet without a firewall because by default, they are configured to accept connections for things like file sharing, printer sharing, and sending annoying pop up messages.  These services also frequently have bugs that allow people connecting to them to do things with your computer that you don't want.

An Ubuntu system does NOT let people connect to it and do things you do not want, so no need for a firewall to break the network.

---

### Post by WeAreLinux on 2010-10-06
> **psusi said:**
> Ok, here's a quick low-down.  Consumer routers these days perform Network Address Translation.  NAT was originally called ip masquerading and created by the Linux community as a way to share an Internet connection among multiple computers.  It involves having the computer with the Internet connection route packets between the Internet and the local network after translating the addresses in them so that the other local computer(s) can connect to servers on the Internet in such a way that the server thinks it is talking to the router, and the local computer thinks it is talking to the server, but they really are both talking to the router.  Thus effectively the local computer is masquerading as the router as far as the rest of the Internet knows.

As a SIDE EFFECT of this, computers on the Internet can not connect to computers on your local network, because there is only one publicly routable IP address and that belongs to the router, so they can try to connect to the router, but not to your computer.

A firewall is all about BREAKING normal network access on purpose.  NAT breaks it by accident.  Windows machines should not be connected to the Internet without a firewall because by default, they are configured to accept connections for things like file sharing, printer sharing, and sending annoying pop up messages.  These services also frequently have bugs that allow people connecting to them to do things with your computer that you don't want.

An Ubuntu system does NOT let people connect to it and do things you do not want, so no need for a firewall to break the network.

Ok, let me see if I understand how NAT works.

When trying to establish a connection, my ISP assigns me a dynamic or static IP Address (Public IP). This Public IP Address then goes through the connected router & gets translated by NAT to another IP (Private IP Address) which I can specify via router settings. This Private IP is then shared with the other computers connected to the router. The Side Effect of NAT you listed above is what keep your computers safe from the internet. Only authorized connections from computers on your LAN are allowed to the Internet via how the router handle the packets. The internet can not connect directly to your computer, since they will only see your router's single Private IP Address hence your computers on the LAN are invisible to the internet. SPI protects your router from unauthorized connections/modification.

Do I got it right? [img]http://ubuntuforums.org/images/icons/icon7.gif[/img]

---

### Post by bodhi.zazen on 2010-10-06
> **WeAreLinux said:**
> Ok, let me see if I understand how NAT works.

When trying to establish a connection, my ISP assigns me a dynamic or static IP Address (Public IP). This Public IP Address then goes through the connected router & gets translated by NAT to another IP (Private IP Address) which I can specify via router settings. This Private IP is then shared with the other computers connected to the router. The Side Effect of NAT you listed above is what keep your computers safe from the internet. Only authorized connections from computers on your LAN are allowed to the Internet via how the router handle the packets. The internet can not connect directly to your computer, since they will only see your router's single Private IP Address hence your computers on the LAN are invisible to the internet. SPI protects your router from unauthorized connections/modification.

Do I got it right? [IMG]http://ubuntuforums.org/images/icons/icon7.gif[/IMG]

Close.

The part abut authorization is off, most routers will permit your clients to access the internet. the more you $$ the more control you may have.

The internet can not connect directly:

1. You can not your a private IP address over "the internet".

2. Your router acts as a firewall and will block incoming "NEW" packets. Returning ESTABLISHED or RELATED connections are allowed.

---

### Post by psusi on 2010-10-06
Almost.  The router has two IP addresses: the public one assigned by your ISP, and a private one on your local network, which is usually 192.168.1.1.  Your computers on the local network also get addresses in the 192.168 block.  Whenever your computer tries to connect to a server on the Internet, it sends the packet to the router to forward.  The router learns about the connection and remembers it, then changes the local address to its public address, then forwards the packet to your ISP.  When packets belonging to that connection come back, the router recognizes they are part of the connection with your computer, and knows it needs to change the address from the public back to the private address before passing it to your computer.  If it doesn't recognize which connection the packet belongs to, then it does not know what private address to replace the public one with and which computer on the local network to hand it to, so it just has to drop it.  The net result is that your computers can establish connections to servers on the Internet, but servers on the Internet can not establish connections to your computers, since the router doesn't know which one they want.  Unless you configure the router and tell it which computer it should forward incoming connections to.

---

### Post by WeAreLinux on 2010-10-07
Nice. NAT is a neat little feature. Learned something new today [img]http://ubuntuforums.org/images/icons/icon10.gif[/img]

EDIT: Removed Question

Thank You for all the information & opinions. I now have enough information to make a decision.

---

### Post by HermanAB on 2010-10-07
Howdy,

Note that the dinky little commercial routers are little Linux machines.  If your desktop machine is a Linux machine, then you can add a one or two more ethernet cards to it and use it as a router.  You won't really gain anything by putting it behind another little router, except a little convenience.

---

