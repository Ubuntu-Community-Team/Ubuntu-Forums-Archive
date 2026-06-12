---
title: "Noob questions about security? Help please :)"
date: 2009-11-11
forum: Security
---

### Post by Limeni on 2009-11-11
So im connected to an wireless hot spot. Im not using any AV programs couse i know there are now registret viruses for linux. I have questions about Firestarter, GUI for Ubuntu firewall and about opened ports.

This are my questions:

1. how can someone attack and break into my computer, through open ports? When i start Firefox it opens port 80, then skype opens some other ports, pidgin too, so is this dangeraus? Can someone hack into my computer through that ports?

2. I have couple of Events in Firestarter, Blocked Connections, and there is this, Port 34189, Source and here is some IP, Protocol TCP, Service Unknown. And I get firestarter notification you are hit, or something like that, and icon is not blue but read and then I see that Events. I have 4 of them now. So is this someone tried to hack into my computer? 

3. If im on a Hot spot wireless network, and all my ports are closed, am I secure? Hackers can hack into my system only through opend ports right? 

4. I know anyone can monitor trafic on hot spot with Wireshark or some other tool. So if I use Thunderbird can someone on that network view my emails, facebook pages and places I visit while surfing under linux/Ubuntu? I think it can but i ask to be 100% sure. And is there a good way of protecting my surfing? So I encrypt my trafic somehow so no one can read my trafic?

Thanks in advance, noob here so be gentle :)

---

### Post by Bunnybugs on 2009-11-11
Well, if you are using your computer just for IM and Browsing, you don't really have trouble with your ports...

Someone needs to open ports that are not scanned, they need a virus to do that... There are so less virus' available for linux distributions, that it's almost impossible to hack!

---

### Post by sarloth on 2009-11-11
I shall answer your questsions as best I can.

> **Limeni said:**
> So im connected to an wireless hot spot. Im not using any AV programs couse i know there are now registret viruses for linux. I have questions about Firestarter, GUI for Ubuntu firewall and about opened ports.

As long as you are only installing software that is in the repositories, you shouldn't have much to worry about in the way of virii. If you do decide to download an executable file, that is where the risk comes in. Fortunately there is little reason to do this since most things are available through the add/remove software lists or apt-get.

> **Limeni said:**
> 1. how can someone attack and break into my computer, through open ports? When i start Firefox it opens port 80, then skype opens some other ports, pidgin too, so is this dangeraus? Can someone hack into my computer through that ports?

An open port on a computer is not like a hole in the wall. It is more like a door. It allows traffic to travel into a specific application. For instance when you surf the web you do not really open ports, you allow certain servers to respond to your requests. So no one will get in this way. (Unless you visit a site that uses an exploit in Firefox to execute something on your machine, this is very rare and hard to do if you stick to high-traffic and trustworthy sites.) Your IM clients and such are similar. There is little to worry about with them if you are patched and browsing safely.

> **Limeni said:**
> 2. I have couple of Events in Firestarter, Blocked Connections, and there is this, Port 34189, Source and here is some IP, Protocol TCP, Service Unknown. And I get firestarter notification you are hit, or something like that, and icon is not blue but read and then I see that Events. I have 4 of them now. So is this someone tried to hack into my computer? 

I know nothing about Firestarter.

> **Limeni said:**
> 3. If im on a Hot spot wireless network, and all my ports are closed, am I secure? Hackers can hack into my system only through opend ports right? 

If you are not running any services (Apache, NFS, IMAP Server, ect.) you should be safe. (There are ways to hijack your unsecure connection to a webpage and feed you malicious code which could compromise your system, but if you are using https you are protected against this. It is also extremely difficult and time consuming to set up.)

> **Limeni said:**
> 4. I know anyone can monitor trafic on hot spot with Wireshark or some other tool. So if I use Thunderbird can someone on that network view my emails, facebook pages and places I visit while surfing under linux/Ubuntu? I think it can but i ask to be 100% sure. And is there a good way of protecting my surfing? So I encrypt my trafic somehow so no one can read my trafic?

If you are not using HTTPS everything you send across the network can be read like plain text. Using HTTPS requires the site you're accessing to have it enabled as well as have a valid certificate. That or you can set up a home VPN or SSH Tunnel to send encrypted traffic to your home server and then it sends the traffic outside for you, relaying it back.

> **Limeni said:**
> Thanks in advance, noob here so be gentle :)

No problem. :)

---

### Post by Limeni on 2009-11-11
Thank you guys veeeery much :D

Now its more cleat to me. So, ports are not problems, ports are opened by programs that need internet connection, but if I use trusted software i will be save beacuse trusted software wont exploit my opened ports.

If i surf on hot spot wireless network everything i open in browser is visible if someone on the network is monitoring packages, but if I use HTTPS im safe, and if site Im visiting supprots https ofcourse. 

So im pretty much secure from attacks if I update Ubuntu and use trusted software. Only thing we should take care about is surfing on hot spots and watch when we log in into facebook or sites like that, so someone dosent sniff our packages and get our username&pass, Great!

---

### Post by cdenley on 2009-11-12
> **Limeni said:**
> 
Now its more cleat to me. So, ports are not problems, ports are opened by programs that need internet connection, but if I use trusted software i will be save beacuse trusted software wont exploit my opened ports.

If you use "trusted" software, and if that software happens to act as a server, you configure it properly. One of the most common ways a linux computer gets compromised is openssh-server + password authentication + weak password.

> **Limeni said:**
> 
If i surf on hot spot wireless network everything i open in browser is visible if someone on the network is monitoring packages, but if I use HTTPS im safe, and if site Im visiting supprots https ofcourse.

As long as the site using HTTPS is using a valid certificate signed by a trusted certificate authority. If this is not the case, any browser would give you a very obvious warning.

> **Limeni said:**
> 
So im pretty much secure from attacks if I update Ubuntu and use trusted software. Only thing we should take care about is surfing on hot spots and watch when we log in into facebook or sites like that, so someone dosent sniff our packages and get our username&pass, Great!
Pretty much. I actually suggest you protect any traffic over the internet as if you were using a hotspot. The internet is one big cloud, and your traffic is not considered safe while traveling through it. Hotspots make it especially easy to intercept your internet traffic, but you should always consider it a possibility.

---

### Post by Limeni on 2009-11-12
Thank you veeeery much cdenley, and others who posted on this topic, now I understand what are the risks of using internet and where to be extra careful.

---

