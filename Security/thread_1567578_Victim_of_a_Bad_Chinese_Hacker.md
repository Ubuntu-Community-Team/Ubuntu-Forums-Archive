---
title: "Victim of a Bad Chinese Hacker?"
date: 2010-09-04
forum: Security
---

### Post by cj.surrusco on 2010-09-04
Well, I was randomly taking a look at my vsftpd log today, and came across something unusual to myself. About a week ago a computer tried to connect to my computer repeatedly with bogus default usernames. There were many attempted connections with usernames such as 'user', 'root', 'linux', and 'login'. Probably about 1000 attempts, within about 2 seconds of each other.

Here is a small excerpt:

```
Sun Aug 29 08:53:10 2010 [pid 1] [root] FAIL LOGIN: Client "218.15.221.82"
Sun Aug 29 08:53:13 2010 [pid 1] [root] FAIL LOGIN: Client "218.15.221.82"
Sun Aug 29 08:53:17 2010 [pid 1] [root] FAIL LOGIN: Client "218.15.221.82"
Sun Aug 29 08:53:19 2010 [pid 2] CONNECT: Client "218.15.221.82"
Sun Aug 29 08:53:21 2010 [pid 1] [root] FAIL LOGIN: Client "218.15.221.82"
Sun Aug 29 08:53:26 2010 [pid 1] [root] FAIL LOGIN: Client "218.15.221.82"
Sun Aug 29 08:53:30 2010 [pid 1] [root] FAIL LOGIN: Client "218.15.221.82"
Sun Aug 29 08:53:31 2010 [pid 2] CONNECT: Client "218.15.221.82"
Sun Aug 29 08:53:34 2010 [pid 1] [user] FAIL LOGIN: Client "218.15.221.82"
Sun Aug 29 08:53:38 2010 [pid 1] [user] FAIL LOGIN: Client "218.15.221.82"
Sun Aug 29 08:53:41 2010 [pid 1] [user] FAIL LOGIN: Client "218.15.221.82"

```
 
I looked up the IP and it is from Beijing. I don't understand how anyone in China would come across my IP, but it worries me a little bit. Obviously, the hacker wasn't that good, since a connection was never made, but should I be concerned?

Also, about 2 hours after this incident, there were about 50 connections made from IP addresses around the world, but no attempted logins or data transfers, all within an hour. 

Looks like this:
```
Sun Aug 29 11:24:32 2010 [pid 2] CONNECT: Client "110.55.97.65"
Sun Aug 29 11:26:04 2010 [pid 2] CONNECT: Client "121.54.46.67"
Sun Aug 29 11:27:57 2010 [pid 2] CONNECT: Client "82.181.129.80"
Sun Aug 29 11:28:16 2010 [pid 2] CONNECT: Client "95.13.64.75"
Sun Aug 29 11:28:16 2010 [pid 2] CONNECT: Client "119.152.31.22"
Sun Aug 29 11:29:17 2010 [pid 2] CONNECT: Client "95.13.64.75"
Sun Aug 29 11:29:18 2010 [pid 2] CONNECT: Client "119.152.31.22"
Sun Aug 29 11:30:47 2010 [pid 2] CONNECT: Client "95.13.64.75"
Sun Aug 29 11:32:33 2010 [pid 2] CONNECT: Client "95.13.64.75"
Sun Aug 29 11:34:01 2010 [pid 2] CONNECT: Client "95.13.64.75"
Sun Aug 29 11:35:27 2010 [pid 2] CONNECT: Client "95.13.64.75"
Sun Aug 29 11:36:15 2010 [pid 2] CONNECT: Client "95.13.64.75"
Sun Aug 29 11:37:19 2010 [pid 2] CONNECT: Client "95.13.64.75"
Sun Aug 29 11:38:14 2010 [pid 2] CONNECT: Client "119.152.31.22"
Sun Aug 29 11:41:16 2010 [pid 2] CONNECT: Client "95.13.64.75"
Sun Aug 29 11:42:14 2010 [pid 2] CONNECT: Client "119.152.31.22"
Sun Aug 29 11:42:45 2010 [pid 2] CONNECT: Client "95.13.64.75"
Sun Aug 29 11:43:17 2010 [pid 2] CONNECT: Client "119.152.31.22"
Sun Aug 29 11:43:44 2010 [pid 2] CONNECT: Client "95.13.64.75"
Sun Aug 29 11:44:22 2010 [pid 2] CONNECT: Client "78.177.246.141"

```

I never broadcast my FTP. It's used only for transferring files with my friends. My IP address would be available to anyone using the TOR network, but I don't understand why anybody would want my files. It especially odd since those IPs were scattered from all around the world.   

Thanks in advance for any advice.

---

### Post by BkkBonanza on 2010-09-04
There's always a lot of people out there doing network scans trying to find vulnerable machines. Nothing out of the ordinary here. Just make sure you have strong passwords.

They found your IP because they randomly scan wide ranges of IPs. 

Do a ShieldsUp scan of your self to make sure nothing obvious is open and vulnerable,
[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

And don't enable VNC (Remote Desktop) without at very least a strong password.

---

### Post by OpSecShellshock on 2010-09-04
Where there is a server listening for connections from the open web, there will be attempts to access it. It's a fully automated process. As you've been able to see, sometimes it's all done from one place whereas other times it's distributed either by using TOR nodes or by using a small army of compromised Windows desktops whose users probably aren't even aware it's happening. Most of the time they've got a list of commonly-used or default usernames and then a list of statistically most-often-used passwords or maybe a brute force script if they don't care about the noise it creates.

In this case, rampant login failures are a good sign.

As for what they want, well, the easiest explanation is that they want the server itself. Maybe they want to stash some files there rather than retrieve any of yours. Maybe they collect servers in order to obfuscate the origins of their other activities. Could be any number of things.

Is root even allowed to access the server from the web? If so, that should be changed anyway.

---

### Post by cj.surrusco on 2010-09-04
Thanks for the advice.

Good to know that my IP isn't being targeted for any specific reason. I do have anonymous FTP login enabled, it is chrooted, but I do allow anonymous users to upload files. I think I will probably change that so anonymous users can only download files, and not upload. 

I have the following ports opened up to my server:
20/21- FTP
22 - SSH
80 - Apache (Plan on taking a HTML class next semester)
9001 - Tor Network
9091 - Transmission Web Interface (protected with password)
5900-5910 - Remote VNC (protected with decent password)
11000-11010 - Torrent peer connections
6000-7000 - Passive FTP transfers

Does it seem secure enough to you guys?

---

### Post by an0dos on 2010-09-04
> **cj.surrusco said:**
> Thanks for the advice.

Good to know that my IP isn't being targeted for any specific reason. I do have anonymous FTP login enabled, it is chrooted, but I do allow anonymous users to upload files. I think I will probably change that so anonymous users can only download files, and not upload. 

I have the following ports opened up to my server:
20/21- FTP
22 - SSH
80 - Apache (Plan on taking a HTML class next semester)
9001 - Tor Network
9091 - Transmission Web Interface (protected with password)
5900-5910 - Remote VNC (protected with decent password)
11000-11010 - Torrent peer connections
6000-7000 - Passive FTP transfers

Does it seem secure enough to you guys?

Two of the most common ways that peoples systems get compromised are ssh and vnc with passwords. You should read the security sticky at the top of the security forum to see how to tunnel vnc over ssh and how to configure ssh to use keys instead of passwords.

---

### Post by BkkBonanza on 2010-09-04
The general rule with security is the less attack surface the better. You have lots of open ports so just keep in mind that when you don't *need* something you should disable it. Always strong passwords and use keys where possible. 

With open ports the problem is that the program servicing it may have unknown vulnerabilities. ftp is considered to be an insecure protocol due to everything being in clear text. It's also pretty well studied and scanned.

With ssh there are several common strengthening tips. 

1. Change the port to some random high port so that 99% of scanners won't find it. They always scan port 22, but they only rarely scan ALL ports because it takes longer and cuts down how many IPs they can do.

2. Use key authentication if possible. It's easy to setup, more convenient and much safer. Disable password login after it has been tested working.

3. You can use something like fail2ban to block IPs who repeatedly try to gain access.

For VNC you are much better off running it over ssh. There are tutorials here for that but I don't have the link offhand.

Anything you can do to harden up is a good thing. Not that you will get hacked, just that every hardening step cuts out potential attacks. You don't want to be the low hanging fruit on the net.

---

### Post by msandoy on 2010-09-04
Hi, just to add to your paranoia, install logwatch, and it will tell you all about all those pesky IP adresses trying to invade you. Right now, I'm just facinated about the variety of countries these IP adresses come from. I use Denyhosts, and it automatically blocks the IP if there is more than a set ammount of failed logins. I've heard it's similar to fail2ban. Never tried the latter. Lately I have observed a shift in the location of the atacking IP adresses, they used to come from china and korea, but now it is mostly eastern/central EU and USA. Don't know if it is due to schools starting, and kids getting a hold of public IP adresses or what, but just harden your system, and you'll be fine. :-)

---

### Post by BkkBonanza on 2010-09-04
> **msandoy said:**
> they used to come from china and korea, but now it is mostly eastern/central EU and USA. 
You'll never know. It could just be they're using proxies or it could be different people. According to what I've read the USA is still the biggest source of this stuff. Too many geeks! Yay!

---

### Post by cj.surrusco on 2010-09-04
Okay, I've closed the VNC port on my router and plan on doing it over ssh from now on, which I have set to a high port (over 14000). 

I've also checked out logwatch and plan on figuring it out later.

One more question: Can I expect a port to be safe if it is not forwarded to a computer on my router?

---

### Post by OpSecShellshock on 2010-09-04
The US is probably the largest source due to the large numbers of compromised computers. There's a lot of hardware in general, most of which is running out of date software, by users who don't know what's going on. That's a lot of homes and offices full of bots with no one the wiser.

---

### Post by linux18 on 2010-09-04
1 out of 3 chineese schoolkids want to be a hacker when they grow up. Think about it, thats as much as 200,000,000 people in one country trying to hack YOU. even if they are no more than amatures, the combined portscan/ip scanning alone is its own ddos atack and you probably wouldn't last more than 10 minutes on an unsecured connection/machine. On the plus side, many people could turn to linux to keep secure.

---

### Post by BkkBonanza on 2010-09-04
> **cj.surrusco said:**
> 
One more question: Can I expect a port to be safe if it is not forwarded to a computer on my router?

If it's not forwarded then it should be either closed or "stealth" (which just means ignored, dropped, non-respondent) and should be safe. Some routers treat them as closed but I think most now act as stealth. (Stealth is better because it causes scanners to wait a timeout period vs. getting a response saying closed which allows them to move on more quickly.)

You can scan your router from the web to see how it behaves. If the port is reported as stealth or just not reported (when scanned) then that is a good thing.

Safety is always relative. I know there are various tricks that can be used to piggyback on udp traffic across your firewall, and even perhaps on tcp traffic, but they would depend on vulnerabilities and as far as I know they're either not very widely known or easy to do. 

Monitoring (keeping an eye on things) is part of a best defense strategy.

---

### Post by BkkBonanza on 2010-09-04
Since you're using VNC over ssh, you may as well close your torrent control panel as well and do it over ssh too. Just one less potential access point.

Using the -D (dynamic, socks5) mode of ssh you can do anything you need inside your network via ssh just as easily from the outside, and only need one port open.

---

### Post by cj.surrusco on 2010-09-04
> **BkkBonaza said:**
> If it's not forwarded then it should be either closed or "stealth" (which just means ignored, dropped, non-respondent) and should be safe. Some routers treat them as closed but I think most now act as stealth. (Stealth is better because it causes scanners to wait a timeout period vs. getting a response saying closed which allows them to move on more quickly.)

You can scan your router from the web to see how it behaves. If the port is reported as stealth or just not reported (when scanned) then that is a good thing.

Safety is always relative. I know there are various tricks that can be used to piggyback on udp traffic across your firewall, and even perhaps on tcp traffic, but they would depend on vulnerabilities and as far as I know they're either not very widely known or easy to do. 

Monitoring (keeping an eye on things) is part of a best defense strategy.

ShieldsUP showed my first 1000 ports as stealth, port 20 as closed, port 21 and 80 as open. So it looks pretty good.

Thanks for the help.

---

### Post by Soul-Sing on 2010-09-05
> **linux18 said:**
> 1 out of 3 chineese schoolkids want to be a hacker when they grow up. Think about it, thats as much as 200,000,000 people in one country trying to hack YOU. even if they are no more than amatures, the combined portscan/ip scanning alone is its own ddos atack and you probably wouldn't last more than 10 minutes on an unsecured connection/machine. On the plus side, many people could turn to linux to keep secure.


Please...1 out of 3? How do you know this?
200.000.000 people to hack you? Where did you get your info from?

---

### Post by BkkBonanza on 2010-09-05
National Enquirer, no doubt.

---

### Post by an0dos on 2010-09-05
> **BkkBonaza said:**
> National Enquirer, no doubt.

And those hackers can make your computer explode.

---

### Post by an0dos on 2010-09-05
> **cj.surrusco said:**
> ShieldsUP showed my first 1000 ports as stealth, port 20 as closed, port 21 and 80 as open. So it looks pretty good.

Thanks for the help.

Do you have your server set up in a DMZ? If not, you should review your port-forwarding rules on your router.

---

### Post by wacky_sung on 2010-09-05
> **an0dos said:**
> And those hackers can make your computer explode.

You are a real joker and get me having a good laugh.:popcorn:

---

### Post by cj.surrusco on 2010-09-05
> **an0dos said:**
> Do you have your server set up in a DMZ? If not, you should review your port-forwarding rules on your router.

It's not set up in a DMZ, The ports that are open are ones that I have forwarded myself.

---

### Post by BkkBonanza on 2010-09-05
You don't want to be setup in a DMZ either. 
A DMZ is a server exposed directly to the internet. 
You are doing fine as is.

---

### Post by cj.surrusco on 2010-09-05
> **BkkBonaza said:**
> You don't want to be setup in a DMZ either. 
A DMZ is a server exposed directly to the internet. 
You are doing fine as is.

Okay, that's what I thought. 

Thanks for your help.

---

### Post by Donalt2010 on 2010-09-05
That GRC site is awesome. My computer is totally hidden and in stealth mode.. The Ubuntu ninja i likes it alot!!

---

### Post by an0dos on 2010-09-05
> **BkkBonaza said:**
> You don't want to be setup in a DMZ either. 
A DMZ is a server exposed directly to the internet. 
You are doing fine as is.

Just for the record I was not advocating putting the computer in a dmz. That is usually a terrible idea. It just happens that most of the time when people tell me that Shields Up showed their computer as having open ports, it was because they accidentally put their computer in a DMZ.

---

### Post by an0dos on 2010-09-05
> **Donalt2010 said:**
> That GRC site is awesome. My computer is totally hidden and in stealth mode.. The Ubuntu ninja i likes it alot!!

Actually, in most cases GRC will just report on the status of your router's firewall. You would probably get the same result from their site if you were using windows XP.

I once sold a desktop to someone who connected it directly to the Internet (no router) with a default install of Windows XP and no antivirus installed. That being said, he did install limewire on it. The poor computer did not last long before he called me about the problems it was having. I ended up installing ubuntu on it and telling him to get a router and stop stealing software (he had downloaded a copy of Microsoft office). Having a router sure is helpful.

---

### Post by wacky_sung on 2010-09-06
Repeated.

---

### Post by wacky_sung on 2010-09-06
> **Donalt2010 said:**
> That GRC site is awesome. My computer is totally hidden and in stealth mode.. The Ubuntu ninja i likes it alot!!

Ninja,i dislike it because eat too much system resources if your pc is low on ram and speed.

---

### Post by Donalt2010 on 2010-09-06
Luckily ive 4gb of ram and dual core amd athlon processors. I havent the patience for slow computers. Thats why i chose Ubuntu. 

So my routers firewall is doin its job nicely then. Its all good in the hood.

---

