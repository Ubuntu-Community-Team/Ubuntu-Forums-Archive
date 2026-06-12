---
title: "backtrack versus ubuntu - which is more secure?"
date: 2011-03-18
forum: Security
---

### Post by TheNewbieGeek on 2011-03-18
I tested the backtrack firewall with shields up website. It's firewall is better then ubuntu. You have to run backtrack as a root user unlike ubuntu. 

Backtrack is used for hacking though does this mean it's better for keeping your computer safe from hackers. thanks for helping out a newb.

P.S. I am talking about the os only. I know the tools on backtrack will keep your os secure also.

---

### Post by bodhi.zazen on 2011-03-18
Shields up only scans your firewall and unless you are directly connected to the internet you are scanning your router, not your OS.

By default Ubuntu has no significant listening services, so your ports are "closed".

The "stealth" ports (drop in iptables terminology) have never convincingly been shown, to me at least, to be more secure then closed ports or "reject".

The idea that you are somehow "invisible" because your ports are "stealth" in shields up is simply untrue.

Try it, set your firewall to drop all traffic and scan your box with nmap or similar tool. I posted just such a demonstration on the forums here somewhere.

At any rate, if you are interested in security, read the stickies and [http://www.debian.org/doc/manuals/securing-debian-howto/](http://www.debian.org/doc/manuals/securing-debian-howto/). Learn how to configure apparmor.

In terms of Ubuntu vs Backtrack, it depends on the vulnerability. If it is a vulnerability to Firefox, and you are using firefox on backtrack (as root) then you are far more vulnerable then if you are running firefox on Ubuntu (as a non-root user). This is more a problem of running as root then Ubuntu vs Backtrack, and anyone with any experience in security at all will tell you not to run X, let alone firefox, as root.

also, in general, the more packages, the more the potential vulnerabilities. If firefox is not installed, then you are not subject to firefox vulnerabilities. Backtrack has more packages so, in general, backtrack is more vulnerable. Even "security" packages, such as fail2ban, can introduce security holes.

The other factor would be which system is more up to date ? If you are running backtrack as a live CD you are more vulnerable then and an up to date hard drive installation of backtrack or ubuntu.

I could go on, but I think you get the point. Security is a process, not simply using Backtrack vs Ubutnu and vulnerabilities are subject to a number of variables (are you running as root ? Are you using apparmor ?).

Backtrack is not, IMO, more secure, it has tools useful for security. If you are a white hat , it is called Vulnerability (or penetration) testing. If you are black hat it is called cracking (or sometimes the less accurate hacking or l33t h3xor). Same tools , different application / use.

---

### Post by TheNewbieGeek on 2011-03-18
Thanks man...I am gonna head over and more about apparmor :D

---

### Post by Dire_Devourer on 2011-03-20
> **bodhi.zazen said:**
> 
By default Ubuntu has no significant listening services, so your ports are "closed".


Ah, if only that where true CUPS is open by default, the minute you install a service such as for example SSH then you have an open port. Every install of Ubuntu has CUPS running by default.

The more services you add the more ports you open and the more vulnerable you become as the kernel won't just drop packets to a running service.

So in hindsight ways to secure the OS would also include things like the following:

sudo update-rc.d -f ssh remove or sudo update-rc.d -f ssh disable

Followed up by going into /etc/init and editing the ssh.conf file line that reads: start on filesystem and add a # (hashbang) sign in front of that line, then that service will not start automatically on boot and can be controlled by using the command.

service ssh start
or service ssh stop

This gives you a greater degree of control over what you have running automatically upon start-up and allows you to choose if it should be running or not.

Things like postgres_sql or mysql open up services that can present vulnerabilities (Password Brute Force, Privilege escalation, etc)  and its worth bearing these things in mind if your trying to rule the roost with an iron fist.

Things like Apache will not install themselves in a Chroot environment with the Suhosin patch unless you the user & security administrator directly intervene and take the hands on approach to security rather than the security by obscurity approach.

Backtrack is based on Ubuntu and allows you to issue the command adduser so you do not have to be running anything as root!

Hope that helps.

N.B: The way I look at it is thus, running services present a target, ie: if your on a network with loads of ubuntu boxes running CUPS and they are sending Data to and from the Office printer, then is it not feasible that someone could do a MITM (man in the middle) and sniff all the Confidential inter-office memo's going across the LAN to that printer? To my way of thinking that presents a significant threat.. Purely for examples sake, check this little item out [[URL="http://keyllama.com/index.php?main_page=product_info&products_id=38&zenid=76d11e2b3e080bf87c80cbe161bac472"]USB KEYSPY]("https://encrypted.google.com/products/catalog?hl=en&q=hardware+keylogger&um=1&ie=UTF-8&cid=7445890645178792335&sa=X&ei=ojmGTYnwJcWSswbkkqSWAw&ved=0CC0Q8wIwAQ")
[/URL]

---

### Post by bodhi.zazen on 2011-03-20
@Dire_Devourer

Those services are NOT installed by default.

See also : [https://wiki.ubuntu.com/ZeroConfPolicySpec](https://wiki.ubuntu.com/ZeroConfPolicySpec)

Yes, if you install additional services you need to learn to secure them, this is true of any os.

---

### Post by securitymeddler on 2011-03-21
Hey dude, 



  Security is always a loaded question. We need to consider the solution you are implementing software for. As a desktop operating system, for general usage. Or as an offensive security tool? 



  Software is a solution to a problem and IT security is the balancing act of maintaining that solution with acceptable risk. 



  So bottom line, Backtrack isn’t a day to day OS. Ubuntu is. We are comparing Apple and Oranges.

---

### Post by Dire_Devourer on 2011-03-21
> **securitymeddler said:**
> 
We need to consider the solution you are implementing software for. As a desktop operating system, for general usage. Or as an offensive security tool? 

Software is a solution to a problem and IT security is the balancing act of maintaining that solution with acceptable risk. 


I agree. As a Desktop OS or General usage OS or even as an Offensive Security tool Ubuntu works out of the Box and if your prepared to spend a little time learning the in's and outs of finding your way around the command line it all works flawlessly. Look out for Back | Track 5 though codename "Revolution" it's due out near the 10th May and it's going to be full source included and built on Lucid Lynx. I think I might even find myself tempted to have a look at it considering I could just launch the update manager and upgrade it into a revolutionary meerkat. But to be honest I think I would be lost looking at a load of stuff that I just wouldn't want, need or find myself having to use. Building your own OS from the ground up by selecting the stuff you want has always held more appeal.

On top of which I still remember the merry hell I had getting Suricata up and running.. Took me the better part of a whole hour and a half, but the struggle was worth it as now I have inline (NFQUEUE) support and the ability to support Multi-Threading, Automatic Protocol Detection (IP, TCP, UDP, ICMP, HTTP, TLS, FTP and SMB), Gzip Decompression, Fast IP Matching and it's fully compatible with snort rules to detect a variety of attacks & probes by searching packet content.

Does Back|Track 4 have Suricata "Hell No!" they're still using Snort & if I ever sold my netbook, it would probably be worth a fortune as it's got heaps of crap they have never heard of. Tcp-Crypt anyone? [http://tcpcrypt.org/](http://tcpcrypt.org/) :)

TCPCRYPT even has a l33t mode, phear! ;) && If you guys are into forensics, you might want to take a peek at [Malheur]("http://www.mlsec.org/malheur/") a heuristic scanner for analyzing malware.

I could go on as I love finding obscure stuff you wont find on more commonly used Pen-Testing Live CD's but what I find useful you may not. Besides which it would belong in another thread! ;)

---

