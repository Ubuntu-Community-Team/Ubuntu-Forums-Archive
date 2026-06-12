---
title: "Server security at home"
date: 2013-02-13
forum: Security
---

### Post by tricky78 on 2013-02-13
Hi
I was hoping to get a few pointers on server security specific for my situation. I'm a complete novice and have just installed the ubuntu server 12.04LTS (not desktop) using Virtualbox yesterday as I want to host my own website (a Joomla CMS) from a home pc.

I've watched numerous youtube videos and read several threads (including stickies) but don't yet know enough to be able to understand what most of it means and my brain is getting fried!

I realise I have to start somewhere so was wondering if it's possible to set up the server on my pc and then simply block all external ips trying to connect to it (as I won't need external access), thus eliminating the possiblility of hacking.

With all the different posts on security (talking about stuff I don't yet understand) I've been unable to find one that tells me if such a straight forward approach is a viable place to start, or whether it will offer any real protection.

Also, I won't be using the pc for anything else at all e.g. web browsing, so would it be OK to install the server through the desktop version of Ubuntu so I can use Webmin to access it through Firefox as I don't yet understand enough about using commands to get everything up and running without some kind of user friendly interface.

Are there any threads that specifically deal with the above situation as I haven't been able to find any and am fed up reading pages of info that are full of terminology I don't understand?

Thanks in advance

---

### Post by TheFu on 2013-02-13
Congratulations!

As long at the "server" is not available from the internet, there is very little risk of being hacked.  However, if a single port, 1 protocol are forwarded to the server, then you are at risk and it can become the ***Trojan Horse*** for your entire internal network.

Security is really hard to do well.  Every internet server needs to be patched, constantly. Sometimes you don't get to choose when. Today an announcement about a new critical security issue in Rails happened. A new version of some software that I run/manage uses Rails, so I had to clear 2 hrs of my day to research the upgrade and make it happen.  I had other things planned, but nothing more important than keeping my server from being powned. Any complex software stack will need similar care and feeding. Joomla is very complicated.  Others will say that they run server X, Y, Z and have never been hacked. That may or may not be true.  They may simply know now it.

Have you ever received a phishing email with a link back somewhere?  It was to a hacked content server ... running WP, Joomla, Apache, Drupal, ... or any of hundreds of other "CMS" tools.  All of them can be hacked.  

Automatic tools search the internet constantly looking for ways to hack in.  Webmin is a huge target too. Do not allow Webmin to be accessible on the internet. If you don't know how to do that, learn - FAST.

There are a few Ubuntu Security how-to guides here. Google, read, understand, and configure your system in those ways.

Many of the "how-to" guides that I've seen on the internet show how-to get something working, but usually have very little concern for security.  Security is not a single setting or 50 settings. It is part of the system and network architecture.  There is much to know and I certainly do not know it all.

I've had to explain to a CEO that our website would be hacked at some point. There was nothing we could do except to have a plan to restore it ASAP afterward and to quickly block the attackers while we researched the root cause. It was not a fun conversation, but he did like knowing that Operations and Security had a plan.

The cornerstone of our "plan" was lots of backups, retained for a long time.  Lots of logs, retained for a long time and pushed to different systems that cannot be reached any other way.

Definitely start using your server on the LAN, learn, have fun, but be prepared for the realities that anyone anywhere in the world can find your service and try to break in at any instant.

For example, I do not run any PHP programs on the internet.  Personal choice. I don't think the average quality of PHP software is high enough that I can trust it. Still, my blog and other websites are almost constantly hit with "/wp-login.php" attempts.  Webmin attempts are almost as constant.  Computers on the internet are seeking ways to hack inside to my tiny, barely read blog.  I shutter to think what would be happening if we were a larger website.

A few resources:
* [http://www.amazon.com/Real-World-Linux-Security-2nd/dp/0130464562](http://www.amazon.com/Real-World-Linux-Security-2nd/dp/0130464562) authored by my friend Bob Toxen can help teach more.
* O'Reilly sells a "Practical UNIX Security" book - [http://shop.oreilly.com/product/9781565921481.do](http://shop.oreilly.com/product/9781565921481.do)
* [http://www.unixmen.com/9-best-practices-to-secure-your-linux-desktop-and-server/](http://www.unixmen.com/9-best-practices-to-secure-your-linux-desktop-and-server/)
* Find your local DefCon group, join, attend a few meetings. Ask smart questions.
* Check out SANS security

Gaining a good understanding of networking and network architecture is extremely important for computer security - especially servers.

We were all where you are at some point.  I didn't know a 5.x.x.x subnet from a 10.0.0.0 subnet. There is a bunch to learn for everyone - always.

It is a dangerous internet out there.
But we have a plan. ;)

---

### Post by lykwydchykyn on 2013-02-13
If your PC is behind a router, then there's no way anyone is getting to it from the outside by default.  You would have to set up port forwarding on your router; even then, most residential ISPs (in the US anyway) block incoming web traffic (unless you pay for a "business class" connection).

You can install server packages on the desktop version of Ubuntu.  The only difference between Ubuntu desktop and Ubuntu server is what packages are installed by default.  They pull from the same package repositories and have the same core OS.

---

### Post by tricky78 on 2013-02-13
Thank you for the quick replies guys
@Fu - I really appreciate your detailed post and I'm definitely at the stage where I don't know the difference between a 5.x... and 10... subnet - in fact, I don't even know what a subnet is so I accept I am currently a hacker's paradise. Thanks for the links but I can't face the thought of ordering and reading books atm although I realise more reading is required at some stage when all this new info starts sinking in.

@lykw.. - Thanks, I did a bit of reading after my first post and now can see that I can use apt-get install firefox x-window-system gnome-core to run firefox. My pc is behind a router but I opened port 80 to allow my website to be viewed externally (I can see both face palming when you read that lol) and it is so I'm on the right track which gives me some hope for the future.

I'm not too stressed that my home test server may get hacked right now as there's nothing on it that's sensitive although it is on the same network as our home pc  but on a different operating system so they aren't linked (I assumed this wouldn't be an issue though?)

Is it possible to just use a .ftpaccess file as this is what I've previously used with a host company to prevent external ip addresses gaining access or some kind of setting to only allow 127.0.0.1 server admin access?

---

### Post by TheFu on 2013-02-13
ftpaccess files have ZERO to do with web servers.  That controls ftp only.  For web servers, you are probably thinking about .htaccss ... that that isn't much authentication or security, especially on a shared web server.

Almost nobody should use FTP these days.  sftp, yes, ftp definitely NOT.  Using FTP is exactly like using telnet. There is a reason telnet has been replaced by ssh. FTP needs to be replaced by sftp.

How to secure a web server is a very complicated question.  I'd feel better if you were doing this on some VPS outside your home network unless you block all external access and do a little reading.

Your "test server" when connected to the internet can be a gateway to all the machines inside your LAN.  If the website you make available has any flaws, someone or a computer scanning the internet will probably find it, hack inside and start using your machine for other purposes.  Once on the box, they can trick you into running a permission escalation tool - from that point on, your machine is theirs.

When I first connected my Linux box to the internet over dial up all those years ago, within 20 minutes, it had been cracked, my account removed and the root password changed.  20 minutes over a phone connection.

Around 2000, another of my boxes was cracked. This time, I'd been running Linux servers for about 6 yrs. I knew better, but was a few months behind on some patches.  They got in and started trying to gain root using every method they knew. Fortunately, almost every attempt was logged to a different machine and I was reviewing the logs over coffee - saw the intrusion and took action.  Thanks to backups, I was able to discover when they'd got in, which account they'd used, and all the files they'd touched.  

THAT is why I'm paranoid.  I hope you don't need to be hacked to be paranoid too. OTOH, I thought everything would be just fine - after all, I was a professional admin for many years and nothing bad happened.  

Since 2000, I've been paranoid.  My backups are better now than ever.  Backups are the main tool against crackers.  It is part of "the plan", but not being an easy target is also part of "the plan."

---

### Post by kleenex on 2013-02-14
Hi, I'm sorry, but I have a question to the **lykwydchykyn** user. I'm using a TP-LINK router with several security options (such as firewall, DoS protection etc.) for one computer and laptop (WiFi). 

**Question:** if I disable WiFi option, so laptop can not use a wireless connection, but computer is still connected (classical cable) to the router, does router firewall still  protects this one computer or all of these security related  options are only for a laptop and WiFi and this computer is not protected? 

Generally this connections/configuration looks like this: [ISP box][COLOR=Green]=>[/COLOR][Router][COLOR=Green]=>[/COLOR][Computer [COLOR=Gray]*classical cable*[/COLOR]],[WiFi]. I have to apologize, because I have already asked a similar question[COLOR=Red]*[/COLOR] and I got the answer, but honestly, I'm probably too paranoid. :- )

Thanks and sorry once again especially users who's responded to my previous thread about router firewall question. Thank You all!
__________________
[COLOR=Red]*[/COLOR] [http://ubuntuforums.org/showthread.php?p=12498692#post12498692](http://ubuntuforums.org/showthread.php?p=12498692#post12498692)

---

### Post by tricky78 on 2013-02-14
> **TheFu said:**
> Your "test server" when connected to the internet can be a gateway to all the machines inside your LAN. If the website you make available has any flaws, someone or a computer scanning the internet will probably find it, hack inside and start using your machine for other purposes.Thanks for the advice - I've closed port 80 until I've done some more research. Can't I just disable file and printer sharing on our home pc (running Windows 7) to prevent the test server for being able to 'see' it on my home network?

---

### Post by lykwydchykyn on 2013-02-14
> **kleenex said:**
> 
**Question:** if I disable WiFi option, so laptop can not use a wireless connection, but computer is still connected (classical cable) to the router, does router firewall still  protects this one computer or all of these security related  options are only for a laptop and WiFi and this computer is not protected? 


I am not familiar with the particulars of your model of router, but I have yet to see a router that *only* firewalled the wireless connections.  Generally everything connected to the LAN side of a router (wired or wireless) is on the same private network, and unless you explicitly forward ports into your private network, the machines on it are inaccessible from the outside.

---

### Post by kleenex on 2013-02-15
Hi **lykwydchykyn**. Thank you for your answer. My router model is TP-LINK (if you mean it). So, the router firewall and other features protects only wifi and laptop, right? Computer are not protected.

---

### Post by SeijiSensei on 2013-02-15
All the machines are protected by the router whether they are connected by wire or wireless.  I can't imagine why you would think this isn't true.  It's the whole reason for having a firewall router in the first place!

Remember that any address in 10/8, 172.16-31/16, and 192.168/16 are "private" addresses.  No Internet router passes traffic intended for these addresses.  All the machines behind your router have private addresses like these. They are not visible to the outside world unless you specifically forward ports on the router back to target(s) behind the router.

---

### Post by lykwydchykyn on 2013-02-15
> **kleenex said:**
> Hi **lykwydchykyn**. Thank you for your answer. My router model is TP-LINK (if you mean it). So, the router firewall and other features protects only wifi and laptop, right? Computer are not protected.

That's almost, but not entirely, the exact opposite of what I just said.:confused:

---

### Post by kleenex on 2013-02-20
Hi **lykwydchykyn**,  it seems to be my fault. Sorry. It is nice to know, that this little, white TP-Link device can do such things!

---

### Post by TheFu on 2013-02-21
> **kleenex said:**
> Hi **lykwydchykyn**,  it seems to be my fault. Sorry. It is nice to know, that this little, white TP-Link device can do such things!

Depending on the exact TP-Link box, you might be able to turn it into a $500-$5000 cisco router by loading F/LOSS aftermarker firmware.  You sound new to networking, so you probably want someone to help who has more experience.  Google openwrt, dd-wrt, or tomato to see which, if any, support your exact model.  I have a TP-Link wifi router that supports newer dd-wrt, but had to jump through some hoops to get it loaded.  Initially, the WAN port was disabled and dd-wrt doesn't enable it, so going through 3 other firmwares, 1 was German, before getting the version I wanted to run was necessary so that the WAN port would work at all.

BTW, most home routers do those things and have for the last 15 yrs. Nothing special at all, except that most home routers also have dumb security features that make it trivial to hack.  Just like we patch our computers, we need to be patching our routers. They do provide the most protection.
Here's a wifi router security checklist: [http://blog.jdpfu.com/pages/wifi-security](http://blog.jdpfu.com/pages/wifi-security) to help.

---

### Post by kevdog on 2013-02-23
Honestly -- I don't know if he's interested in setting up a web server that is available to the world, or rather a restricted audience.  Employment of some type of firewall -- iptables, ufw, gufw, -- would be the first place I would tell this user to start.  You could restrict the IP address that have access to this box while also limiting access to other listening servers on different ports. 

Setting up Apache is very easy, but it does take frequent monitoring and updating (or patching) since security holes are discovered -- or zero-day exploits.  Obviously setting up listening services such as php or mysql add a large layer of complexity in terms of security.

---

### Post by TheFu on 2013-02-23
> **tricky78 said:**
> Thanks for the advice - I've closed port 80 until I've done some more research. Can't I just disable file and printer sharing on our home pc (running Windows 7) to prevent the test server for being able to 'see' it on my home network?

The answers is "it depends."

If you patch your Linux VM religiously - weekly - and do not run any normal end-user programs on it, disable all access to the VM from the outside world by not forwarding any ports to it, then I would only be concerned about computers inside the LAN ... like the Windows hostOS ... performing automatic attacks against it.  Javascript can be used to attack computers both on the internet AND on the local network.  Windows PCs are a huge target of attacks, so if you use Java, flash and/or PDF files, then you are at a much higher risk for attack than if you don't use those tools.  Again, javascript is used to cause PCs inside LANs to do things of which the operator is not aware.

Will disabling file/print on your Windows PC protect it?  Only from file/print attacks.  There are many other ports open on every PC of every OS.  For example, I used **nmap** to scan a Windows7 Ultimate box on my network:
```
$ sudo nmap -sT win7ult

Starting Nmap 5.00 ( http://nmap.org ) at 2013-02-23 07:27 EST
Interesting ports on win7ult (10.10.10.8):
Not shown: 992 filtered ports
PORT      STATE SERVICE
135/tcp   open  msrpc
139/tcp   open  netbios-ssn
445/tcp   open  microsoft-ds
554/tcp   open  rtsp
2869/tcp  open  unknown
3389/tcp  open  ms-term-serv
5357/tcp  open  unknown
10243/tcp open  unknown
MAC Address: 52:54:00:7B:8A:13 (QEMU Virtual NIC)

Nmap done: 1 IP address (1 host up) scanned in 5.28 seconds

```Port 139/445 is file sharing?
Port 3389 is RDP - remote desktop. That is how I manage the machine.
I have no idea what the rest are. If I firewall them off, things break. This machine records TV from a network tuner, so those ports definitely need to be open, at least to the tuner box.

MS-Windows has an unknown number of zero-day attacks that are being used to attack systems right now.  It is definitely more than 10 and probably less than 1,000. By the time the AV tools know about these, anyone running Windows may already have been compromised.  You and I are probably not the targets of a new zero-day exploit. Those are almost always used to attack extremely high value targets like Fortune 100 companies and governments.  However, we can be at the wrong place at the wrong time can get attacked too.  All OSes are very complicated, so all OSes have likely zero-day exploits, including Linux.

If you'd like more security information in a more end-user-friendly way, Brian Krebs (formerly of the Washington Post newspaper) has a nice blog for end-users: [https://krebsonsecurity.com/](https://krebsonsecurity.com/)

For Linux servers, staying current on your patches, running a firewall, and not using a server as a desktop is the best advice.  

Right now, just like every other Saturday morning, I'm patching the 20 systems I'm responsible for. That includes my personal desktop and my Mom's PC 4 states away.  So much easier to patch than Windows, I promise.  Of course, I have a script that does the work, I just need to watch it run, log the results, review the logs and determine if anything failed that needs extra attention.  That almost never happens. Thinks generally work, unless a server runs out of storage.

---

