---
title: "Best firewall distro?"
date: 2006-06-10
forum: The Cafe
---

### Post by commodore on 2006-06-10
What do you think is the best firewall distribution? I personally think m0n0wall because it's FreeBSD based :P but I don't know because I haven't made a firewall. I think OpenBSD would be a great one but making a live cd yourself is too troubleworthy.

---

### Post by T313C0mun1s7 on 2006-06-10
I have tried many, but mainly the all in one appliance style distros that allow you to NOT USE the features you don't need.

Depending upon the fit for your particular needs I like e-smith (then it became Mitel SME Server, and latter was given back to the community at contribs.org) and IPCop.

IPCop is a better basic firewall applicance distro that focuses on being the layer beween the LAN/WLAN and the Internet cloud. SME Server tries to extend this to be a all in one server platform (Although personally I think a server and a firewall should be kept separate) and it has multiple modes of operation depening upon your needs.

Both of these really shine at being extendable to allow for the easy addition of features and functions not included in the basic distro. I currently am using IPCop at home and I have added ad blocking for all PCs, and Internet filtering to my kids (and all DHCP obtained IPs) computers. The filtering has a daily automatic update. In the past I have used e-smith as a samba file and print server that did inline e-mail virus and spam filtering.

You might also check out the community submitted VMWare applicance images. VMWare is now giving away VMWare Server for free, and there are sever good firewalls already built as images.

---

### Post by evil316 on 2008-01-04
I use IPCop and I like it.  It's pretty simple and secure.  I may attempt to try something different in the near future though.

---

### Post by evil316 on 2008-01-04
> **T313C0mun1s7 said:**
> I have tried many, but mainly the all in one appliance style distros that allow you to NOT USE the features you don't need.

Depending upon the fit for your particular needs I like e-smith (then it became Mitel SME Server, and latter was given back to the community at contribs.org) and IPCop.

IPCop is a better basic firewall applicance distro that focuses on being the layer beween the LAN/WLAN and the Internet cloud. SME Server tries to extend this to be a all in one server platform (Although personally I think a server and a firewall should be kept separate) and it has multiple modes of operation depening upon your needs.

Both of these really shine at being extendable to allow for the easy addition of features and functions not included in the basic distro. I currently am using IPCop at home and I have added ad blocking for all PCs, and Internet filtering to my kids (and all DHCP obtained IPs) computers. The filtering has a daily automatic update. In the past I have used e-smith as a samba file and print server that did inline e-mail virus and spam filtering.

You might also check out the community submitted VMWare applicance images. VMWare is now giving away VMWare Server for free, and there are sever good firewalls already built as images.

Do you use the proxy server on your IPCop machine?  If so what size cache do you use?

---

### Post by Lostincyberspace on 2008-01-04
This thread is kind of old but oh well.

I use mono wall nice and simple but not overly so. 
I have also tried smothwall but there was to much bloat.

---

### Post by anv on 2008-03-17
I lost couple of days ago total intres towar normal router firewalls as in price class 30-50€. Constant problems with internet in communication between bridge and router. many of those popular cheaper modells are built for windows and there is no guarantee that they work so well with linux desktop. also those firewalls are not so good in tight place.  

So what happened? I received old computer (coppermine) I had read some time before of firewall distros. so I went to distrowatch.com choose one of them : SmoothWall. downloaded burned cd installed it in the old box. struggled couple of hours with configuring which now takes couple of minutes. ( I hadn't no earlier experience from this kind of work) 

So now I have good working firewall which intakes signal from my adsl-Bridge and it connects to my Ubuntu desktop. my internet speed went up some amount not in down/upload but like using webreader and stream media. possibly because there is more power to handle these processes which normally are just so little recources in these plastic router/firewall boxes.

Those were "side effects" but as coming to security which is the head point for these firewalls, it is whole different thing as situation before with: Netgear (rp614v4) and Firestarter. as before with wireshark and firestarters own event manager showed quite often "red" , which problem no more exists.

I really warmly recommend to change in one of these Linux-Firewall distros. I founded also this M0n0wall and am going to try it next. I try to seek some kind of opensource firewall distro product which would have in addition kind of wireshark and more network tools like portscan etc. SmoothWal is real secure but I miss more configure options.

P.S. 
feels really good when internet works finally, after D-Link router burned without warnings and Netgear were just one big anchor.

---

