---
title: "Paranoia dual-boot question"
date: 2013-07-11
forum: Security
---

### Post by chainlinkfence on 2013-07-11
I want to dual boot windows 7 and a linux distro; linux for everyday use, and windows for... LoL.  I've been paranoialy researching security and anonymity for the past month, and have only a few questions that remain unanswered.  The only documentation I could find is in [http://www.centos.org/docs/5/html/5.2/Deployment_Guide/s3-bootloader-grub.html](http://www.centos.org/docs/5/html/5.2/Deployment_Guide/s3-bootloader-grub.html) saying to use a bootloader password so an attacker can't boot into an insecure operating system.  So my question is this:  How insecure is dual-booting with an insecure os (windows)? while using windows would a remote attacker be able to look in my linux partition and compromise my system?  Thanks in advance.  I know this may be a silly question, but I still don't know all that much about security and how attacks work, so I have to assume anything is possible.  Also, what's the best way to be anonymous while online? I had thought VPN->TOR and 4 (or so) anonymous re-mailers for communication, but I recently read an article on here that said maybe TOR wasn't the best option.

---

### Post by sudodus on 2013-07-12
Welcome to the Ubuntu Forums :-)

I think the user habits (how you browse the internet, manage your mail, and install security updates) are more important than special tools to increase the security of your system. But anyway, see this link

[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

For tasks, where you need extra security, you can use

[https://tails.boum.org/](https://tails.boum.org/)

---

### Post by HermanAB on 2013-07-12
Well, if someone has physical access to your machine, then it is game over, unless you use so called 'full disk encryption'.  The boot loader password and BIOS password serve to further reduce the size of the unprotected system information.

---

### Post by chainlinkfence on 2013-07-13
@sudodus:
Thanks!  ...Oh yeah... user habits... I also use Windows 7 for porn...
That was one of the first security documentation I read for linux, and I will refer to it when I install and configure my linux distro.  Everything I agree with in it except that I hear SELinux is more secure than apparmor? something to do with the kernel and whatnot?  I already had the Noscript, AdBlock Plus, and ghostery addons for firefox on Windows 7, and the sticky for Noscript on here was godly in helping me understand what it actually did and how to configure it better.
I'll check out using Tails, but its still TOR, which doesn't quell my rising doubts about the privacy of TOR.

@HermanAB:
I have a couple CKT versions of PGP I can use for that... also that brings up another question: can I use my CKT PGP instead of GnuPG with linux?
I'm more worried about remote attacks than physical attacks though.

---

### Post by windows2003 on 2013-07-13
If you mean attacks from the internet to your computer...You can prevent this by buying a good firewall router (not the cheap models!).
Then you computer is behind a hardware firewall! So, this will already take longer to hack into your computer (check your logs on this firewall, from time to time, to see if somebody tries, some models give option to send you mail, if somebody try's!). The second option you can do, but normally ubuntu is already standard configured with ufw (software firewall), is activate this one! You can always add there some ip-tables into ufw to get more protection, or to block more...
Then you can also encrypt your documents with an encryptor like advanced encryptor package! 

Take a good and difficult root & administrator password...don't install things you did not ask....don't work in root mode....

You can always install Windows on different HD and Linux on other HD and don't make use of there bootloaders! You can select this normally also by the BIOS function. 
You do this, by entering your BIOS -> go to tab MAIN -> enable Boot option menu , save and restart when PC restart press F12 (this is for acer, check this on google for other computers if this F-key is same) then you get menu from BIOS and select wich harddrive you want to start!

If you google a little bit, you can find lot's of ways to this!

---

### Post by chainlinkfence on 2013-07-14
I don't have money, so I have to use coffee shop wifi (I know, I know).  I know to use least privileges and whatnot with SELinux and firewalls and whatnot... I read an article about someone who used 3 software firewalls to protect his computer (I think it was Windows), would this be an alternative option for Linux?  I haven't heard of AEP, I will check it out, but isn't PGP/GnuPG enough/better?  It's an Asus, and it's esc.  As I said before, no money = using different partitions... or could I run something like DSL from a live cd, and fit everything I want on that cd?

---

### Post by cariboo on 2013-07-14
I think you are really confused as to what a firewall actually is, there is only one firewall, that is built into the kernel, called netfilter. All the rest are just front-ends, ufw, gufw, iptables etc, to make it easier to create firewall rules. Everything else you mentioned in your last post, are just different secure methods for other services. AEP is a is a secure, remote application access gateway, pgp/gnupgp is a way of encrypting email.

The best thing you can do to secure your Ubuntu installation is to read and understand the stickies at the top of this [sub-forum]("http://ubuntuforums.org/forumdisplay.php?f=338").

If you were really paranoid, you should be using one of the [BSD's]("http://en.wikipedia.org/wiki/Berkeley_Software_Distribution"), and completely get rid of any [Linux distributions]("http://en.wikipedia.org/wiki/Linux_distribution") and WIndows.

---

### Post by chainlinkfence on 2013-07-14
> **cariboo907 said:**
> I think you are really confused as to what a firewall actually is, there is only one firewall, that is built into the kernel, called netfilter. All the rest are just front-ends, ufw, gufw, iptables etc, to make it easier to create firewall rules. Everything else you mentioned in your last post, are just different secure methods for other services. AEP is a is a secure, remote application access gateway, pgp/gnupgp is a way of encrypting email.  The best thing you can do to secure your Ubuntu installation is to read and understand the stickies at the top of this [sub-forum]("http://ubuntuforums.org/forumdisplay.php?f=338").  If you were really paranoid, you should be using one of the [BSD's]("http://en.wikipedia.org/wiki/Berkeley_Software_Distribution"), and completely get rid of any [Linux distributions]("http://en.wikipedia.org/wiki/Linux_distribution") and WIndows.  [http://www.securityfocus.com/columnists/320](http://www.securityfocus.com/columnists/320) (I think this is the article I was referring to) And by stacking firewalls I don't mean stacking GUI's, I mean firewalls such as InJoy and IPCop.  Did I not mention that I've spent a month researching security?  Just because I thought my original question may have been a little over the top and therefore possibly 'retarded' doesn't mean that I am retarded.  Please refrain from assuming that I am.

---

### Post by monkeybrain2012 on 2013-07-14
What do you use Windows for? Unless you play games or short of ram just put it in Virtualbox and save yourself the hassles of partitioning and rebooting . It doesn't even need to connect to the internet.

---

### Post by cariboo on 2013-07-14
> **chainlinkfence said:**
> [http://www.securityfocus.com/columnists/320](http://www.securityfocus.com/columnists/320) (I think this is the article I was referring to) And by stacking firewalls I don't mean stacking GUI's, I mean firewalls such as InJoy and IPCop.  Did I not mention that I've spent a month researching security?  Just because I thought my original question may have been a little over the top and therefore possibly 'retarded' doesn't mean that I am retarded.  Please refrain from assuming that I am.

I just said you seemed confused, this is a Ubuntu support forum, and as such, we are talking about securing your Ubuntu installation. I don't use WIndows enough, to even comment on how to secure your system. As for multiple firewalls, the Windows users in my household have the standard Windows firewall enabled, and I have a router with the firewall enabled, so I guess you could say that they are using two firewalls, I personally don't have any firewall rules set on my Ubuntu/Debian installs, as I feel the router firewall is enough for me. My feeling is that if you are running multiple firewalls, it is a sort of belt and suspenders approach, if a belt is good enough to hold up your jeans, then using suspenders along with the belt must be twice as good. :-P

I have to say though, that if I'm out and about with my netbook, running gnome-shell, I enable the firewall rules, before I even leave home, and in many cases, run a port scan against it to see if there are any open ports.

---

### Post by chainlinkfence on 2013-07-14
> **monkeybrain2012 said:**
> What do you use Windows for? Unless you play games or short of ram just put it in Virtualbox and save yourself the hassles of partitioning and rebooting . It doesn't even need to connect to the internet.  LoL = League of Legends = best game ever.  [QUOTE=canboo907]I just said you seemed confused, this is a Ubuntu support forum, and as such, we are talking about securing your Ubuntu installation. I don't use WIndows enough, to even comment on how to secure your system. As for multiple firewalls, the Windows users in my household have the standard Windows firewall enabled, and I have a router with the firewall enabled, so I guess you could say that they are using two firewalls, I personally don't have any firewall rules set on my Ubuntu/Debian installs, as I feel the router firewall is enough for me. My feeling is that if you are running multiple firewalls, it is a sort of belt and suspenders approach, if a belt is good enough to hold up your jeans, then using suspenders along with the belt must be twice as good.  I have to say though, that if I'm out and about with my netbook, running gnome-shell, I enable the firewall rules, before I even leave home, and in many cases, run a port scan against it to see if there are any open ports. [/QUOTE]  Well... a linux distro for sure, I just came to like some of the contributors on the Ubuntu forum :).

---

### Post by duke.tim on 2013-07-14
[ 						 							]("http://ubuntuforums.org/member.php?u=77104")[**[COLOR=#990303][B]cariboo907**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=77104")Why do you suggest using a bsd over linux if a user wants to be really paranoid/secure?

---

### Post by cariboo on 2013-07-14
> **duke.tim said:**
> [ 						 							]("http://ubuntuforums.org/member.php?u=77104")[**[COLOR=#990303][B]cariboo907**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=77104")Why do you suggest using a bsd over linux if a user wants to be really paranoid/secure?

The BSD's and especially OpenBSD are designed for security by default, all the packages are audited, and as bug free and free from security holes as possible. The trade-off is that for the average user it is much harder to install and configure than a Linux installation. For more info, have a look [here]("http://www.openbsd.org/").

---

### Post by Velnias on 2013-07-15
All DEFAULT install packages are audited ( it includes Apache, Bind, Sendmail and few others ). Other packages and ports - may be audited. Install ( and configuration ) is really easy and quick. Though for advanced user only - you need to know what are you doing.

---

### Post by Tom_ZeCat on 2013-07-16
Under Windows, whether its a dual-boot system or not, make it more like Linux.  End your days of working, especially online, as root.  If you have an account set up exactly how you want it (and it's an administrator account), create a new administrator account, password protected, of course.  Then use that new account to demote your regular account to a limited acccount (XP terminology) or a standard acccount (Win 7 terminology).  Under Windows 7 Home Premium if anything attempts to install in your standard account, you're prompted for a password.  In Win 7 Professional or Ultimate, you have to log into the administrator account to install anything.  The bottom line is use your standard/limited account for most everything.  Only use the admin account when you have to.  

I do like the idea of sticking Windows into a virtual box though.  Never tried that.

---

### Post by Hungry Man on 2013-07-16
As said, only the *default* installation of OpenBSD is audited to that extent. As this is for a desktop system there is a massive amount of attack surface that will be installed after installation - impractical to vet all of it. I consider a properly configured Linux to be more secure than a properly configured OpenBSD/*BSD.


@chain,

You can secure Windows decently, especially if you only use it for games. Set up EMET 4.0 and disable any services not necessary for LoL (many, I'd imagine).

---

### Post by Velnias on 2013-07-16
> **Hungry Man said:**
> I consider a properly configured Linux to be more secure than a properly configured OpenBSD/*BSD.


Care to explain? because sometimes I see "OpenBSD not affected" or "Fixed months ago" when talking about vulnerabilities.

---

### Post by monkeybrain2012 on 2013-07-16
I found this article, [http://aboutthebsds.wordpress.com/2013/03/31/bsd-vs-linux/](http://aboutthebsds.wordpress.com/2013/03/31/bsd-vs-linux/)

Basically it says BSD is crap in terms of usability and its security (e.g software audit) is exaggerated way out of proportion by a small group of hardcore advocates. Obviously very partisan but I have no idea how much is accurate since I never use BSD. Maybe more knowledgeable people here can weigh the arguments and tell us how true (or false) they are. :)

The author of the article claimed

> On top of that, BSD project managers willingly allow spying agencies to  put backdoors it thier OSes which make BSD even more insecure. An  example is in 2011 where by Theo de Raadt (Head of the OpenBSD  project) made an agreement with the FBI to plant a backdoor in OpenBSD,  OpenSSH and PF.

But there was no source. Is there any truth to this?

---

### Post by sandyd on 2013-07-16
If you want to be secure, a few things first- 

Here is a nice link for the OP on how NAT (well, that is what most routers have today anyways...) works: [https://www.grc.com/nat/nat.htm](https://www.grc.com/nat/nat.htm)
And to clear up the fact that NAT is not a firewall... [http://security.stackexchange.com/questions/8772/how-important-is-nat-as-a-security-layer](http://security.stackexchange.com/questions/8772/how-important-is-nat-as-a-security-layer)

Link about how NAPT is useful, but plain NAT is not, and how it plays a role in security : [http://blog.ioshints.info/2011/12/is-nat-security-feature.html](http://blog.ioshints.info/2011/12/is-nat-security-feature.html)

That said, I am a bit paranoid myself, and filter out all incoming traffic by default on both my server networks, and home network; only opening ports for my webservers, ftp servers, and established sessions. UPNP (does vyatta even have UPNP???) is [also disabled]("http://www.zdnet.com/how-to-fix-the-upnp-security-holes-7000010584/")

Personally, I believe that if you restrict what you actually do on your Windows computer (only boot into Windows to play game, and boot back into linux when done, .etc .etc), there is a _much_ lowered chance of getting infected/viru/hacked. I think I would be a bit more worried about a Spetsnaz team dropping through the window and stealing the computer itself ;)

---

### Post by tubbygweilo on 2013-07-17
> **sandyd said:**
> . . .I think I would be a bit more worried about a Spetsnaz team dropping through the window and stealing the computer itself ;)

Plus sneak and peek and no knock warrants;);)

---

### Post by Velnias on 2013-07-17
> **monkeybrain2012 said:**
> 
But there was no source. Is there any truth to this?

Source? - BSDs are open source like Linux - finding backdoor is simple ;-)

Sadly there are few BSD offending sites. Me wonders if Dr.SmallAndSoft is indirectly involved. Divide and conquer!

And Linux vs BSD flame wars starts too because of different mindsets - BSD devs are like a grandpas ( this and that worked well last 20 years - why to change to something new? Damn kids... ) and Linux devs behave like young men ( I need it badly now - and if it works, who cares about correctness and all that old <snip>! OK OK, ill revise later... ).

Anyway its little off topic.

---

### Post by SchnappiJedi on 2013-07-18
In my humble opinion here is the most secure way to use a computer:

Full drive encryption using AES first layered with Blowfish using a strong password and/or a keyfile kept on a USB stick for your main operating system. Install Ubuntu (or any other operating systems) within a virtual machine. If your computer is acquired once the power is pulled your drive (with your virtual machines and all of the corresponding files) is secure. You cannot get more physical security than this.

As for Firewall's, what most people forget is that a Firewall should protect outgoing traffic as well.

As for TOR, try hosting a Tor server and looking at the post packets just for starters. That being said I believe that what I am talking about is unethical, but point being TOR is only as good as the servers it is running through. I guarantee that people are running TOR servers with bad intentions. I guess it just depends if you go through "honest" TOR servers or not when you traffic is being randomly routed. My problem is that instead of worrying about the coffeeshop sniffing your data you now are opening yourself up to 15 servers that can possibly sniff you packets as they pass through when using TOR.

If you want to browse securely use vpn or ssh tunnel through a network you control with a provider you trust.

And secure is not the same as anonymous. Using a vpn or ssh tunnel you are far from anonymous, but you are secure. You need to use multiple proxies to be anonymous (what TOR does)...but you are inherently not secure when going through proxies you don't control.

In my opinion being secure comes at the cost of being anonymous. When you build a castle it isn't hard to find out who you are, but that doesn't mean that people can see what you are doing inside your castle. If you use a VPN to a server it is easy to trace the ip back to the owner of the network on which the vpn server resides, but whomever is doing this still has no idea what you were transmitting while at the coffee shop. I think secure is more important than anonymous in most situations.

My two off topic in terms of Ubuntu cents.

---

### Post by chainlinkfence on 2013-07-20
Thanks everyone, I appreciate the discussion here.       I think I've decided on a Debian installation (sorry Ubuntu fans)... I wanted RHEL, but from what I understood, you have to pay for updates... and then CentOS, but from what I've been reading apt-get > yum (in terms of security)... so Debian! (but please keep this BSD vs. Linux argument going :), it's interesting and helps me learn).    I think now that if I do secure windows 7 as well as Debian that I will be safe and secure... Hugging six rabbits for added comfort.    @Tom-ZeCat:  User-access control gets annoying, but I already do that and IMHO it's worth the annoyance    @Hungry Man: Thanks for the tip, I hadn't heard of EMET before, Getting it now :)    @sandyd:  I saw a DEFCON vid on Youtube... How I Met Your Girlfriend... Interesting video with a funny guy.  He got through NAT easy enough... now I just have to reinforce my windows :P    @schnappi2:  If the VPN doesn't keep logs and TOR is used in conjunction, wouldn't that make me secure and anonymous (knowing they're not the same thing).  Uh... sorry for my lack of real contribution and inability to separate things into a non-cluttered manner... can anyone help me with this?

---

### Post by SchnappiJedi on 2013-08-09
> **chainlinkfence said:**
> Thanks everyone, I appreciate the discussion here.       I think I've decided on a Debian installation (sorry Ubuntu fans)... I wanted RHEL, but from what I understood, you have to pay for updates... and then CentOS, but from what I've been reading apt-get > yum (in terms of security)... so Debian! (but please keep this BSD vs. Linux argument going :), it's interesting and helps me learn).    I think now that if I do secure windows 7 as well as Debian that I will be safe and secure... Hugging six rabbits for added comfort.    @Tom-ZeCat:  User-access control gets annoying, but I already do that and IMHO it's worth the annoyance    @Hungry Man: Thanks for the tip, I hadn't heard of EMET before, Getting it now :)    @sandyd:  I saw a DEFCON vid on Youtube... How I Met Your Girlfriend... Interesting video with a funny guy.  He got through NAT easy enough... now I just have to reinforce my windows :P    @schnappi2:  If the VPN doesn't keep logs and TOR is used in conjunction, wouldn't that make me secure and anonymous (knowing they're not the same thing).  Uh... sorry for my lack of real contribution and inability to separate things into a non-cluttered manner... can anyone help me with this?

If you used TOR over a VPN that would make the TOR packets originate from the network hosting the VPN before traversing the TOR servers. In the end the packets still travel unencrypted over multiple TOR servers. Does that make sense?

---

