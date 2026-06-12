---
title: "TuxGuardian - application based firewall"
date: 2010-10-09
forum: Security
---

### Post by arapaho on 2010-10-09
I added Package Request for TuxGuardian - application based firewall. If you want it, please vote for it.
[https://bugs.launchpad.net/ubuntu/+bug/657249](https://bugs.launchpad.net/ubuntu/+bug/657249)

Features:
Detects unauthorized applications trying to act like a client or a server;
Operates with or without user intervention;
Verifies the applications' integrity so that maliciously modified software won't be able to send or receive data through the network;
Uses a three-layered architecture of independent modules, which eases the task of addings new features and functionality;
[http://tuxguardian.sourceforge.net/screenshot.png](http://tuxguardian.sourceforge.net/screenshot.png)
[http://tuxguardian.sourceforge.net/](http://tuxguardian.sourceforge.net/)

---

### Post by cariboo on 2010-10-09
The last time TuxGaurdian was updated, was in 2006, why use something that could potentially have security flaws, when there are already iptables front ends in the repositories. The preferred tool is ufw/gufw.

---

### Post by arapaho on 2010-10-10
Please, read description. Gufw doesn't have this functionality and as far as I know will not have. 
Anyway, when something is in repository it is your choice what to install and what not. 
I think that developers are able to check if it is secure or maybe develop similar application. It has a 'wish' status now.

---

### Post by wacky_sung on 2010-10-10
It sound good but seem working like a window based firewall.

---

### Post by bodhi.zazen on 2010-10-10
> **arapaho said:**
> I added Package Request for TuxGuardian - application based firewall. If you want it, please vote for it.
[https://bugs.launchpad.net/ubuntu/+bug/657249](https://bugs.launchpad.net/ubuntu/+bug/657249)

Features:
Detects unauthorized applications trying to act like a client or a server;
Operates with or without user intervention;
Verifies the applications' integrity so that maliciously modified software won't be able to send or receive data through the network;
Uses a three-layered architecture of independent modules, which eases the task of addings new features and functionality;
[http://tuxguardian.sourceforge.net/screenshot.png](http://tuxguardian.sourceforge.net/screenshot.png)
[http://tuxguardian.sourceforge.net/](http://tuxguardian.sourceforge.net/)

While such a thing may sound like a good idea if you are coming from Windows, it has not caught hold in the Linux community as of yet.

Part of the reason is that Linux is not Windows and this type malware does not exist in Linux.

Another issue is that people use alternate tools such as selinux or apparmor.

Another issue is that Linux sysadmins have much more control over what servers are or are not installed on the clients.

Last, the amount of "damage" any potential clinet could do is very limited on Linux. Sure it could affect things in /tmp or /home, but not system files.

tuxguardian is very buggy and as has been pointed out no longer maintained.

All I can say, this is not windows and they type of application firewall you suggest has not really been needed.

So -1 from me.

---

### Post by arapaho on 2010-10-10
> **bodhi.zazen said:**
> 
Part of the reason is that Linux is not Windows and this type malware does not exist in Linux.
You can't guarantee that it will not be created. When this happen linux users will not be prepered.
> **bodhi.zazen said:**
> 
Another issue is that people use alternate tools such as selinux or apparmor.
These tools are to difficult for new linux users. And apparmor works differently. First you have to allow certain application to run and then create a policy. It may be too late.
Anyway, maybe it is great tool for IT professionals but for desktop, an application working like tuxguardian would be simpler and better solution at least for newbies. And second thing the choice should be left for user. It doesn't have to be default firewall. I only want it to be in repositories.
> **bodhi.zazen said:**
> 
Another issue is that Linux sysadmins have much more control over what servers are or are not installed on the clients.
I don't work on servers and I really don't care about servers.

> **bodhi.zazen said:**
> 
tuxguardian is very buggy and as has been pointed out no longer maintained.
Maybe something similar could be developed. It would be more important for me then a new font in Ubuntu.

---

### Post by cariboo on 2010-10-10
> **arapaho said:**
> Please, read description. Gufw doesn't have this functionality and as far as I know will not have. 
Anyway, when something is in repository it is your choice what to install and what not. 
I think that developers are able to check if it is secure or maybe develop similar application. It has a 'wish' status now.

All of these orphaned applications have package maintainers, that make sure the app works with  the latest distro release, there may be some bug fixing, but nothing major. Don't count on a package maintainer to fix any major flaws. 

There must be a reason why the original author abandoned the application, but we aren't privy to it. 

As for learning new ways of doing things, any operating system is hard to learn, we weren't born knowing how to use Windows, it took many years for you to gain the knowledge you have now. Give Linux the same amount of effort.

---

### Post by bodhi.zazen on 2010-10-10
> **arapaho said:**
> You can't guarantee that it will not be created. When this happen linux users will not be prepered.

That sentiment is understandable as you are likely coming from Windows.

As I have tried to indicate, Linux is not Windows and we do not have the same vulnerabilities.

There are many reasons this type of vulnerability is extremely unlikely, probably the main one being the Repositories. Most if on all applications are installed from trusted sources and as such adware or spyware of the kind you are worried about is non-existant.

Security is much tighter in Linux for a variety of reasons and without debating each and every point with you I am explaining to you why the interest in such an application is low.

Just because you are new to Linux and you are unfamiliar with security does not mean Linux users are not unprepared. Linux and Ubuntu are designed from the ground up to be secure.

There is a reason we do not have spyware, and it most certainly is not security through obscurity.

As I said this is not Windows.

See the stickies and you might also like :

[http://librenix.com/?inode=21](http://librenix.com/?inode=21)

[Securing Debian Manual]("http://www.debian.org/doc/manuals/securing-debian-howto/") 

[SecurityTeam/FAQ - Ubuntu Wiki]("https://wiki.ubuntu.com/SecurityTeam/FAQ#Sudo") 
[U]
[https://wiki.ubuntu.com/SecurityTeam](https://wiki.ubuntu.com/SecurityTeam)
[/U]

And similar.

---

### Post by Dorotheos on 2010-10-12
Ok guys, I don't know exactly what your backgrounds are, but an application based firewall is needed for linux to gain popularity and maintain it's high security. I use appamor, selinux, snort, and a host of other hids services to maintain my host. However, to run online games that access multiple ip addresses or even use services such as skype witch uses p2p to communicate, an application based firewall is needed. I definately don't want to open all the ports needed for those services on my host for anytime use, and i don't want to keep turning everything off to use them. An application based firewall is needed to continue to maintain our call to the world that ubuntu is ready to be used as your home os.

---

### Post by Abir Valg on 2010-10-14
I contacted the initial developer of Tuxguardian - he dropped the project because the underlying linux kernel infrastructure (namely LSM modules API) has been changing so dramatically, it has become impossible to keep up and maintain the project. In newer kernels the possibility to plug-in an LSM modules has been removed, thus Tuxgardian can' work there.
The only other similar project I came across was linux-firewall.org ,although it didnt work as promised on my machine, so I cant vouch for it.
I believe that application based firewall for linnux has been long overdue. It is needed not so much to guard off malware and viruses which are largely non-existant because all packages are vetted in the repositories, as to give a privacy-minded user a sense of complete control of what's going on on his machine.

---

### Post by OpSecShellshock on 2010-10-14
> **Dorotheos said:**
> Ok guys, I don't know exactly what your backgrounds are, but an application based firewall is needed for linux to gain popularity and maintain it's high security. I use appamor, selinux, snort, and a host of other hids services to maintain my host. However, to run online games that access multiple ip addresses or even use services such as skype witch uses p2p to communicate, an application based firewall is needed. I definately don't want to open all the ports needed for those services on my host for anytime use, and i don't want to keep turning everything off to use them. An application based firewall is needed to continue to maintain our call to the world that ubuntu is ready to be used as your home os.

Don't know about gaming, but Skype works just fine with UFW in a default-deny configuration. That is to say, if the connection is initiated by the user on the client side, then the established and related connections will work just fine. It just doesn't allow unsolicited connections to be initiated from external devices. For Skype, all I have to do is start the client and sign in; no need to open any ports or anything like that. I don't deny anything on the egress side since the only things that connect that way are things that I've started in the first place. Denying outbound traffic doesn't really improve security (on the Linux desktop), but can restrict functionality greatly, or worse, can lead users to make granular changes which undermine whatever protection they thought they were setting up in the first place.

---

### Post by chocolateboy on 2010-10-25
> **Abir Valg said:**
> The only other similar project I came across was linux-firewall.org ,although it didnt work as promised on my machine, so I cant vouch for it.


Another old one is [_Program Guard_]("http://pgrd.sourceforge.net/"), which was last updated in 2005.

There's also [_snet_]("http://www.synack.fr/project/snet/snet.html") (2009). There's a good discussion of it [_here_]("http://lwn.net/Articles/316940/").

---

### Post by mainerror on 2010-10-26
> **arapaho said:**
> You can't guarantee that it will not be created. When this happen linux users will not be prepered.

I think you have to get comfortable with the underlaying structure and way Linux works to judge.

> **arapaho said:**
> Anyway, maybe it is great tool for IT professionals but for desktop, an application working like tuxguardian would be simpler and better solution at least for newbies.

Believe me real IT professionals won't use that neither will they use Linux based firewalls at all. IT professionals use BSD based firewalls for good reasons. You might want to investigate a bit on that to see why.

> **arapaho said:**
> I don't work on servers and I really don't care about servers.

This is quite bad. Servers require the most security possible as the host sensible data. You can definitely look at how servers get secured and learn from that. This is like the Formula 1 of the IT world. Good ideas and concepts can be adapted for normal cars to get them more efficient and so on. Same applies for security.

> **Dorotheos said:**
> Ok guys, I don't know exactly what your backgrounds are, but an application based firewall is needed for linux to gain popularity and maintain it's high security.

A application based firewall will only give you a false feeling of security like it does on Windows. Sure you might feel secure to have one but you definitely are no more secure than without.

---

### Post by KonfuseKitty on 2010-10-26
As a simple end user who isn't getting much if anything out of the usually promoted solutions such as apparmor, I must say I find the attitude expressed by the experts here in response to the OP highly regrettable.


I for one, would greatly appreciate a solution that let me simply create a rule "This application can't access the internet".  I've tried achieving this with apparmor, by doing a test on so constraining Opera, to no effect (and have posted about it in a thread a few weeks ago).  Perhaps this can be done with ufw/iptables, but I haven't managed to work it out.


Again, to all the experts, please accept that some of us are too busy accomplishing "real world" tasks with Linux and don't have the time or the inclination to learn complex solutions.  We do need simple and powerful options as suggested by the OP.  Maybe Tuxguardian isn't the right tool, but the idea is sound.

---

### Post by OpSecShellshock on 2010-10-26
> **KonfuseKitty said:**
> As a simple end user who isn't getting much if anything out of the usually promoted solutions such as apparmor, I must say I find the attitude expressed by the experts here in response to the OP highly regrettable.


I for one, would greatly appreciate a solution that let me simply create a rule "This application can't access the internet".  I've tried achieving this with apparmor, by doing a test on so constraining Opera, to no effect (and have posted about it in a thread a few weeks ago).  Perhaps this can be done with ufw/iptables, but I haven't managed to work it out.


Again, to all the experts, please accept that some of us are too busy accomplishing "real world" tasks with Linux and don't have the time or the inclination to learn complex solutions.  We do need simple and powerful options as suggested by the OP.  Maybe Tuxguardian isn't the right tool, but the idea is sound.

I do understand this; however, when looking for solutions it's important to first define a problem. Does it take an additional application to prevent something that isn't happening in the first place?

The development framework for the desktop environment is modular. Software that needs to access the internet is created specifically to access the internet and says so in its descriptions. For example, if something is running in a web browser, it will be accessing the internet. A weather applet installed in the panel or on a dock is going to be accessing the internet. Same for an applet that alerts on new mail. An IM client is going to as well. Those applications are made to do that.

Things like word processors and other productivity applications probably don't need to most of the time, and so they won't. When there's an active link in a PDF or doc file, it will open a browser if there's not one already open, rather than simply connecting itself (well, except for Adobe Reader, which for whatever reason allows the running of scripts and can access the web directly, but that's just bad design and there are alternatives).

Shell scripts can be read as text files before running them to see what they do. If they can't be, or if they're obfuscated or encoded in some weird way, then we all have the option to not run them.

I'm sorry to come across as so exasperated, but I'm having a difficult time understanding exactly what purpose an application based firewall would really serve. I think it would be easier to constrain things on an individual basis, if it's necessary to do so at all. It's probably easier to get support for specific tasks/constraints on specific applications as well.

---

### Post by fmfrisch on 2010-10-27
> **OpSecShellshock said:**
> Shell scripts can be read as text files before running them to see what they do. If they can't be, or if they're obfuscated or encoded in some weird way, then we all have the option to not run them.


But the average user linux and ubuntu is starting to attract won't read a shell script.

I'm absolutely no expert on this topic, on the contrary im a complete n00b. But the general idea of linux being safe out of the box and that there is a discussion whether it's possible to hack this or that instead of WHEN it's going to happen seems rather distant to me. (again im no expert so feel free to unload your expertise on me. I need the education). 

I mean a 14 year old hacked FBI. Seems to me most things are possible in this digital world!

---

### Post by OpSecShellshock on 2010-10-27
> **fmfrisch said:**
> But the average user linux and ubuntu is starting to attract won't read a shell script.

I'm absolutely no expert on this topic, on the contrary im a complete n00b. But the general idea of linux being safe out of the box and that there is a discussion whether it's possible to hack this or that instead of WHEN it's going to happen seems rather distant to me. (again im no expert so feel free to unload your expertise on me. I need the education). 

I mean a 14 year old hacked FBI. Seems to me most things are possible in this digital world!

Well don't get me wrong; Linux computers get successfully intruded upon all the time. It's just that when it happens, it's due to something the user did (enabling remote administrative access, installing malicious packages or running bad scripts), rather than something they failed to do (such as installing some "security" tool).

---

### Post by Googleler on 2010-10-28
Without a firewall I think you are virtually exposed to the hackers with or without Linux environment. I've used TuxGuardian in the past and I think is a pretty well application for computer security.

---

### Post by mainerror on 2010-10-28
Yes indeed a firewall should be required anyway but not as a software which probably is even running in user space on the machine itself. A nice OpenBSD box for example behind the router (or if versed enough even as the router) would be optimal.

---

### Post by cariboo on 2010-10-28
A firewall really doesn't do anything on a default installation, as there are no ports open to the outside world, and if you are behind a router, it's a belt + suspenders type of activity.

it's just like the poster earlier that tried to block Opera from accessing the Internet. Web browsers and many other programs use random high ports for out going connections, so it's pretty hard to block a port if you don't know which one it is using, and it changes every time you use a program, have a look at this example:

```
netstat -tn
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 192.168.1.215:**43915**     209.85.225.125:5222     ESTABLISHED
tcp        0      0 192.168.1.215:**56053 **    192.168.1.235:22        ESTABLISHED
tcp        0      0 127.0.0.1:**7634 **         127.0.0.1:53732         TIME_WAIT  
tcp        1      0 192.168.1.215:**44341**     96.8.82.129:80          CLOSE_WAIT 
tcp        1      0 192.168.1.215:**51431**     96.8.82.129:80          CLOSE_WAIT
```

I've bolded the outgoing ports, these change every time a program is opened.

---

### Post by bodhi.zazen on 2010-10-28
> **cariboo907 said:**
> A firewall really doesn't do anything on a default installation, as there are no ports open to the outside world, and if you are behind a router, it's a belt + suspenders type of activity.

it's just like the poster earlier that tried to block Opera from accessing the Internet. Web browsers and many other programs use random high ports for out going connections, so it's pretty hard to block a port if you don't know which one it is using, and it changes every time you use a program, have a look at this example:

```
netstat -tn
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 192.168.1.215:**43915**     209.85.225.125:5222     ESTABLISHED
tcp        0      0 192.168.1.215:**56053 **    192.168.1.235:22        ESTABLISHED
tcp        0      0 127.0.0.1:**7634 **         127.0.0.1:53732         TIME_WAIT  
tcp        1      0 192.168.1.215:**44341**     96.8.82.129:80          CLOSE_WAIT 
tcp        1      0 192.168.1.215:**51431**     96.8.82.129:80          CLOSE_WAIT
```

I've bolded the outgoing ports, these change every time a program is opened.

For outgoing connections it is easier to block the dport rather then the source port.

```
sudo iptables -A OUTPUT --dport 80 -j DROP
```

Will block opera (and other web browsers) =)

---

### Post by WinstonChurchill on 2010-10-28
> **arapaho said:**
> I added Package Request for TuxGuardian - application based firewall. If you want it, please vote for it.
[https://bugs.launchpad.net/ubuntu/+bug/657249](https://bugs.launchpad.net/ubuntu/+bug/657249)

Features:
Detects unauthorized applications trying to act like a client or a server;
Operates with or without user intervention;
Verifies the applications' integrity so that maliciously modified software won't be able to send or receive data through the network;
Uses a three-layered architecture of independent modules, which eases the task of addings new features and functionality;
[http://tuxguardian.sourceforge.net/screenshot.png](http://tuxguardian.sourceforge.net/screenshot.png)
[http://tuxguardian.sourceforge.net/](http://tuxguardian.sourceforge.net/)
This program is incredibly silly - not only can all its functionality be accomplished easily with iptables, the entire idea is pointless: simply running 'sudo netstat -nep' will quickly tell you exactly what programs are accessing the internet. Anything that can make itself invisible to netstat would have to be some sort of rootkit, and by definition a rootkit could easily bypass filtering like TuxGuardian. There are several GUI frontends for the kernel iptables functionality out there - if you're too lazy to use the shell, use those.

This is exactly the thing that would sound like a great idea to someone unfamiliar with Linux, when in reality it is a greater detriment to security than the service it provides is worth. It reeks of Windows, and I don't like it.

**-1 **from me.

---

### Post by cariboo on 2010-10-28
> **bodhi.zazen said:**
> For outgoing connections it is easier to block the dport rather then the source port.

```
sudo iptables -A OUTPUT --dport 80 -j DROP
```

Will block opera (and other web browsers) =)

I was just using my post as an example, destination port will work, but then wouldn't you also need to specify 443 plus any other none standard ports that http may be running on?

---

### Post by bodhi.zazen on 2010-10-28
> **cariboo907 said:**
> I was just using my post as an example, destination port will work, but then wouldn't you also need to specify 443 plus any other none standard ports that http may be running on?

Yes.

As with INPUT, it is easier to write rules that allow traffic, and then deny the rest, either with a DROP at the end of the chain or as the default policy.

---

### Post by arapaho on 2010-10-30
> **WinstonChurchill said:**
> This program is incredibly silly - not only can all its functionality be accomplished easily with iptables, the entire idea is pointless: simply running 'sudo netstat -nep' will quickly tell you exactly what programs are accessing the internet.
I don't wont spent my time watching connections and block conections after they are already running - this is really  **silly **thing to do. I want to be informed before anything program or proces use internet. And apparmor is too complicated for new users. Simple solution is needed:
"block THIS program or process from accessing the Internet"

Let's face it: most Ubuntu users come from Windows, and they want to use their programs not thinking about watching connections or study security books, applications like apparmor, snort or guess whether this or that program has potentially danger script.

Until linux developers understand this linux will not become more popular.

Obviously by that time I will have to use this user **unfriendly** applications and your advice to feel more secure.

---

### Post by Leebo on 2010-10-30
I agree that probably most new Ubuntu users come from windows, but in my opinion those that are looking for, I believe, a better OS experience than Windows, extra learning is involved as someone mentioned earlier. There is a learning curve to Ubuntu or any other linux distro. I'm not trying to deter anyone from moving to linux from windows at all, but I feel that if you are just wanting to click and make it happen without knowledge of how it works then Windows may be ideal. Ubuntu/Linux is becoming the click and make it happens but most of the time you need to at least have some knowledge of how the whole process works because custom configuration has always been a plus to linux, in my opinion.

---

### Post by arapaho on 2010-10-30
@Leebo
You are right that to use linux one must change their approach, but developers should understand that if they want Ubuntu to became more popular changing only look for Unity will not attract many new users.  
At least something like GUI for apparmor in Ubuntu would be welcomed. In my opinion that would be more welcomed by Ubuntu users than Unity.

---

### Post by mainerror on 2010-10-30
> **arapaho said:**
> I don't wont spent my time watching connections and block conections after they are already running - this is really  **silly **thing to do. I want to be informed before anything program or proces use internet. And apparmor is too complicated for new users. Simple solution is needed:
"block THIS program or process from accessing the Internet"

Let's face it: most Ubuntu users come from Windows, and they want to use their programs not thinking about watching connections or study security books, applications like apparmor, snort or guess whether this or that program has potentially danger script.

Until linux developers understand this linux will not become more popular.

Obviously by that time I will have to use this user **unfriendly** applications and your advice to feel more secure.

Please forgive me if I sound rude but I believe it has to be said.

People have to start change their mind about how to operate their computers. W still are in the stone age it's time to start evolving and for that users have to simply understand that it is very important to understand what your computer does and why.

I'm very well aware that most users are not ready for this. Some come from Windows where they just adopted a pattern they follow instead of thinking but I feel this has to change. You can't remain in stone age for ever. It should be our goal not to make it easier to just not think but to make thinking a requirement as this is the only real way to enhance security.

---

### Post by cariboo on 2010-10-30
> **arapaho said:**
> I don't wont spent my time watching connections and block conections after they are already running - this is really  **silly **thing to do. I want to be informed before anything program or proces use internet. And apparmor is too complicated for new users. Simple solution is needed:
"block THIS program or process from accessing the Internet"

Let's face it: most Ubuntu users come from Windows, and they want to use their programs not thinking about watching connections or study security books, applications like apparmor, snort or guess whether this or that program has potentially danger script.

Until linux developers understand this linux will not become more popular.

Obviously by that time I will have to use this user **unfriendly** applications and your advice to feel more secure.

I fail to understand why people assume that all the knowledge they have gained from years of using Windows, will transfer to a Linux based distribution. 

If you are that interested in security, do some testing yourself, instead of trying to apply a Windows solution to a problem that doesn't exist. There have been plenty of examples in this thread, and in this sub-forum of how to check what programs are connecting to the internet. Most of these methods don't work in Windows without installing extra programs. For an average user fresh from Windows the default Ubuntu installation is more secure than the same installation in WIndows.

I've been using a Linux variant for longer than some of our members have been using Windows. On a desktop system, I have never gone out of my way to add extra security, I rarely enable a firewall, as I'm behind a router. The only time I've installed any anti-malware programs is to help someone with a problem. I think before I click that link. Personally I think that knowledge is more important than trying to use software to make myself feel secure.

---

### Post by mainerror on 2010-10-30
> **cariboo907 said:**
> I fail to understand why people assume that all the knowledge they have gained from years of using Windows, will transfer to a Linux based distribution. 

If you are that interested in security, do some testing yourself, instead of trying to apply a Windows solution to a problem that doesn't exist. There have been plenty of examples in this thread, and in this sub-forum of how to check what programs are connecting to the internet. Most of these methods don't work in Windows without installing extra programs. For an average user fresh from Windows the default Ubuntu installation is more secure than the same installation in WIndows.

I've been using a Linux variant for longer than some of our members have been using Windows. On a desktop system, I have never gone out of my way to add extra security, I rarely enable a firewall, as I'm behind a router. The only time I've installed any anti-malware programs is to help someone with a problem. I think before I click that link. Personally I think that knowledge is more important than trying to use software to make myself feel secure.

100% agreed.

---

### Post by LucasAdams on 2010-10-31
Unfortunately the average user is notoriously good at getting infected from anything from rootkits to "free" screensavers. If it looks good they'll click on it, install it and click yes to every warning. Unfortunately for us this is the group of users we are pandering to.

While Ubuntu has done an excellent job providing a secure OS, and the community has helped refine and improve it, there still remains a need to run potentially malicious programs locally. It therefore becomes important to provide as many tools as possible to "sandbox" applications. While experts can block communication on certain ports, certain protocols and IP addresses; there is still a need to block communication on a program level. We need an interactive method of stopping communication before it initiates and deciding whether to Allow or Deny.

---

### Post by KonfuseKitty on 2010-10-31
The argument that this is somehow an issue of Windows versus Linux, ignorance versus knowledge, is disingenuous and quite dangerous. There is no good reason to not strive for simple and powerful solutions if such is possible. Blacklisting, or better yet, whitelisting applications that can or can't connect to the internet - why should that be seen as the user avoiding having to learn how a Linux computer works? I could learn all there is to learn about Linux security, but would still appreciate a simple instruction "Nothing but Opera and Evolution can connect to the internet". Not 100% secure, but a good deal better than having to listen to packets, grep the results, interpret, etc. etc. I regret to say that the attitude of the experts here, the fact that they resort to the "You're coming from Windows so you don't know" non-argument is anything but helpful.


I've just noticed in my logs that on every startup and wakeup my computer is connecting to Canonical servers, even though automatic checks are disabled in the Update Manager. If I had the tool as discussed in this tread, this wouldn't be an issue. But as things are, I have to fiddle with some networking startup script to deal with it.

---

### Post by mainerror on 2010-10-31
> **KonfuseKitty said:**
> I've just noticed in my logs that on every startup and wakeup my computer is connecting to Canonical servers, even though automatic checks are disabled in the Update Manager. If I had the tool as discussed in this tread, this wouldn't be an issue. But as things are, I have to fiddle with some networking startup script to deal with it.

Ah I see the old "oh-gosh-windows-is-communicating-with-microsoft" problem. With the risk to sound very rude you simply don't seem to understand that much about the OS you are operating on and apparently would like to just block all whats unknown to not further care about. Instead people should try to investigate whats going on.

I'm quite certain that the communication going on might be related to the statistics gathering which you have agreed to then installing Ubuntu. You know the checkbox asking you for permission to collect anonymous statistics about preferred packages. Even if it's not the case I'm more than 100% certain that it's not the NSA neither Canonical trying to get your bank account information.

I don't quite understand why people tend to be that paranoid about such stuff but then click on a IM message that they can win a iPhone 4 or that there is an awesome video on YouTube they just have to watch. Peoples common sense and the sense for security seems to be extremely off which is exactly the point I'm talking about.

Try to teach the new generation and the old generation too to a certain extent what security means and what to keep an eye on. Just creating a mechanism to make them click and forget is so wrong. It will only help them to not bother anymore about it and their sense of security remains off.

I know this sounds like a rant and in fact it also is a rant that most new to Linux in general seem to not want to understand and learn their OS and they seem to not want to understand and learn about security neither but instead they want to have what they were used to. Install a anti-virus, a firewall program and then forget about all that networking and security crap.

We are definitely moving towards a future where knowledge about computers and how they work will be required even more day to day so I fail to understand why people still don't want to open their minds and learn about new things as they simply have to. Maybe not today but soon enough.

/rant

---

### Post by Kinstonian on 2010-10-31
> **mainerror said:**
> Ah I see the old "oh-gosh-windows-is-communicating-with-microsoft" problem. With the risk to sound very rude you simply don't seem to understand that much about the OS you are operating on and apparently would like to just block all whats unknown to not further care about. Instead people should try to investigate whats going on.


That "block all whats unknown to not further care about" is called "default deny."  It's a best practice and comes from the principle of least privilege.  I think he wants to follow that principle and wants more visibility and control over what happens on his computer.  Where I come from, regardless of the OS, those are good things.

---

### Post by Dave_L on 2010-10-31
> **mainerror said:**
> ...
We are definitely moving towards a future where knowledge about computers and how they work will be required even more day to day so I fail to understand why people still don't want to open their minds and learn about new things as they simply have to. Maybe not today but soon enough./rant

No offense, but that's merely wishful thinking. :)

The average user doesn't want to learn more about computers. To him, a computer is just another appliance like a washing machine or a microwave oven. He wants to be able to push a few buttons and not have to think about it.

And since most computers are bought by average users, their needs will be prioritized, because that's where the profit is for hardware manufacturers and software vendors.

---

### Post by LucasAdams on 2010-10-31
When I was installing Ubuntu 10.10 a slide show played. It said I should experiment with the OS because it was "safe".

Users don't care about how it works. They want and need their hand to be held. Even experts need their hand held. Ever ran an application that wasn't in the repositories? You just exposed yourself to attack. What about backdoors in the repository? How would you even know it was there?

These kind of tools are necessary to ensure Ubuntu stays safe. Sure it will make some people complacent but its better than not having it at all.

---

### Post by mainerror on 2010-10-31
> **Kinstonian said:**
> That "block all whats unknown to not further care about" is called "default deny."  It's a best practice and comes from the principle of least privilege.  I think he wants to follow that principle and wants more visibility and control over what happens on his computer.  Where I come from, regardless of the OS, those are good things.

Well thats perfectly fine for firewalls I would never argue about that but it should not be applied to everything. I don't refer to network traffic but more to the general thinking pattern.

And Ubuntu doesn't listen on unused ports by default.

---

### Post by OpSecShellshock on 2010-10-31
> **Kinstonian said:**
> That "block all whats unknown to not further care about" is called "default deny."  It's a best practice and comes from the principle of least privilege.  I think he wants to follow that principle and wants more visibility and control over what happens on his computer.  Where I come from, regardless of the OS, those are good things.

Right, but what people have been trying to say is that's the way Ubuntu already is, without having to use any additional tools. Things like web browsers, mail and chat clients and package/update managers access the internet as part of their intended functions. Unless the user starts them up they won't even run, much less establish network connections (though obviously the update manager can be configured--by the user--to check automatically). Sure, it's true that the connections from those applications won't be "blocked" in the strictest sense, but they also won't even be made or attempted until the application is specifically launched, which works out to the same thing without having to do anything.

Having said that, when I first started using Ubuntu I also denied all outbound traffic and then put in exceptions. The only things that ended up happening were that my messages log was filled with a bunch of DHCP failures and my clock was always wrong because my NTP requests weren't getting out. Eventually I made exceptions for those, after learning what they were (and there was no way around having to do that, see).

A couple years later I started really reading the forums here, including the security stickies and some other threads about network activity management. That was how I found out that by default, nothing connects from the outside in without it being a response to a request initiated locally. So what I did was I compared what my network activity looked like with only incoming connections denied but outgoing connections allowed to what it looked like under my old rules of denying everything in and out with a list of exceptions. It was the same. It turned out that what I'd been doing before was making things more difficult for myself but had been gaining absolutely nothing.

My hope is that a testimonial from my own experience as a new user will be more helpful than a simple repetition of the same things long-time users always say.

---

### Post by Kinstonian on 2010-10-31
> **mainerror said:**
> **Well thats perfectly fine for firewalls I would never argue about that** but it should not be applied to everything. I don't refer to network traffic but more to the general thinking pattern.

Good, because this thread is about firewalls. :)

> And Ubuntu doesn't listen on unused ports by default.

Secure by default is great and I love it.  However, it only means you have to do less to harden the OS before you start using it.

It's a term that only covers the very beginning of security, and doesn't mean you're secure tomorrow when you install additional software/services, have to install patches, determine what action to take after getting a security warning in FireFox/NoScript, back up your important data, choose strong passwords for websites, etc.  Secure by default is a small part of security, and it has an increasingly smaller impact on security as time goes by.

Even if you don't have any services you can still get hacked through a client side vulnerability.  That's why you need to keep things like your browser updated and use NoScript, etc.

---

### Post by Kinstonian on 2010-10-31
> **OpSecShellshock said:**
> Right, but what people have been trying to say is that's the way Ubuntu already is, without having to use any additional tools. Things like web browsers, mail and chat clients and package/update managers access the internet as part of their intended functions. Unless the user starts them up they won't even run, much less establish network connections (though obviously the update manager can be configured--by the user--to check automatically). Sure, it's true that the connections from those applications won't be "blocked" in the strictest sense, but they also won't even be made or attempted until the application is specifically launched, which works out to the same thing without having to do anything.

Having said that, when I first started using Ubuntu I also denied all outbound traffic and then put in exceptions. The only things that ended up happening were that my messages log was filled with a bunch of DHCP failures and my clock was always wrong because my NTP requests weren't getting out. Eventually I made exceptions for those, after learning what they were (and there was no way around having to do that, see).

A couple years later I started really reading the forums here, including the security stickies and some other threads about network activity management. That was how I found out that by default, nothing connects from the outside in without it being a response to a request initiated locally. So what I did was I compared what my network activity looked like with only incoming connections denied but outgoing connections allowed to what it looked like under my old rules of denying everything in and out with a list of exceptions. It was the same. It turned out that what I'd been doing before was making things more difficult for myself but had been gaining absolutely nothing.

My hope is that a testimonial from my own experience as a new user will be more helpful than a simple repetition of the same things long-time users always say.

True, but the point of this kind of firewall isn't about being notified or preventing web browsers and email.  I think it would be nice to be notified as soon as wget or ftp were used, and be able to permit/block it if necessary.  Preventing an attacker's toolkit from getting on your computer is critical and can mean the difference between a minor or major incident.  Wouldn't you want to know if a process like Nmap or a new process you don't know about wants to make an outbound connection to the Internet out of the blue?

---

### Post by mainerror on 2010-10-31
> **Kinstonian said:**
> Good, because this thread is about firewalls. :)



Secure by default is great and I love it.  However, it only means you have to do less to harden the OS before you start using it.

It's a term that only covers the very beginning of security, and doesn't mean you're secure tomorrow when you install additional software/services, have to install patches, determine what action to take after getting a security warning in FireFox/NoScript, back up your important data, choose strong passwords for websites, etc.  Secure by default is a small part of security, and it has an increasingly smaller impact on security as time goes by.

Even if you don't have any services you can still get hacked through a client side vulnerability.  That's why you need to keep things like your browser updated and use NoScript, etc.

Well thank you very much for posting this as this is exactly what I'm ranting about the last couple of pages. I'm talking about that absolute security is an illusion where a simple front-end giving you the option to simply mark a checkbox to block something only amplifies this illusion.

I'm nowhere in contradiction with what you've posted right now. This thread is not only about firewalls but also about the security of Ubuntu where I just tired to highlight that it won't help to move Ubuntu to the thinking patterns of new users migrated from another OS but instead we should invest energy in helping those new users to adopt a new thinking pattern.

---

### Post by LucasAdams on 2010-10-31
> **mainerror said:**
> ....
I'm nowhere in contradiction with what you've posted right now. This thread is not only about firewalls but also about the security of Ubuntu where I just tired to highlight that it won't help to move Ubuntu to the thinking patterns of new users migrated from another OS but instead we should invest energy in helping those new users to adopt a new thinking pattern.
A new thinking pattern is important but that doesn't mean we should ditch the techniques of the old. While the Windows security model was fundamentally broken it doesn't mean the techniques used to patch it are broken too. Those techniques were built on foundations of sand and that's the why they failed, not because they were flawed too.

---

### Post by Kinstonian on 2010-10-31
> **mainerror said:**
> Well thank you very much for posting this as this is exactly what I'm ranting about the last couple of pages. I'm talking about that absolute security is an illusion where a simple front-end giving you the option to simply mark a checkbox to block something only amplifies this illusion.


Is absolute security an illusion?  Yes.  However, no one is saying an application based firewall is absolute security.  Besides, I'm willing to bet you use NoScript, even though that also fits your idea of "marking a checkbox to block something."

---

### Post by mainerror on 2010-10-31
> **Kinstonian said:**
> Is absolute security an illusion?  Yes.  However, no one is saying an application based firewall is absolute security.  Besides, I'm willing to bet you use NoScript, even though that also fits your idea of "marking a checkbox to block something."

I use only AdBlock Plus to get rid of adds'n stuff. No NoScript.

The problem is that for the average user a firewall application symbolizes total security as the don't know better and they don't have to further think about anything because "Hey, I have a firewall; I'm secure!". This is exactly the thinking I always encounter and I'm doing private support almost 7 years now. There only a handful of people I know which think further.

---

### Post by Kinstonian on 2010-10-31
> **mainerror said:**
> I use only AdBlock Plus to get rid of adds'n stuff. No NoScript.

The problem is that for the average user a firewall application symbolizes total security as the don't know better and they don't have to further think about anything because "Hey, I have a firewall; I'm secure!". This is exactly the thinking I always encounter and I'm doing private support almost 7 years now. There only a handful of people I know which think further.

Yes, and those people probably don't even know what a firewall is, and have almost certainly never heard of TCP/IP.  I don't think the people you are ranting at here are the same computer illiterate people you've been helping for the past 7 years.

---

### Post by cariboo on 2010-10-31
> **Kinstonian said:**
> True, but the point of this kind of firewall isn't about being notified or preventing web browsers and email.  I think it would be nice to be notified as soon as wget or ftp were used, and be able to permit/block it if necessary.  Preventing an attacker's toolkit from getting on your computer is critical and can mean the difference between a minor or major incident.  Wouldn't you want to know if a process like Nmap or a new process you don't know about wants to make an outbound connection to the Internet out of the blue?

Are you assuming a system is already compromised when the programs you mention are started? If not, it is the user that starts those programs, and that is what most of us in this thread are saying. Wget, ftp and nmap don't start by themselves and normally when you start the program you have to add where it is connecting to.

If you don't want something to open a port to the wild, don't start the program.

---

### Post by LucasAdams on 2010-10-31
An idea that implements most of what we want but fails to mention how much additional effort application based security would require: [http://brainstorm.ubuntu.com/idea/23333/](http://brainstorm.ubuntu.com/idea/23333/)

This article simple disregards the linux-is-superior-to-MS arguments: [http://lwn.net/Articles/316940/](http://lwn.net/Articles/316940/)

It appears that someone will work on stacking linux-security-modules. That way other connection and file permission applications can operate at the same time. Does anyone have an update on the progress of this?

In the meantime firestarter is an interactive firewall with limited application based functionality. We need something with a bit more polish and focus on the application side of things.

---

### Post by mainerror on 2010-11-01
> **Kinstonian said:**
> Yes, and those people probably don't even know what a firewall is, and have almost certainly never heard of TCP/IP.  I don't think the people you are ranting at here are the same computer illiterate people you've been helping for the past 7 years.

And you think only computer literate will find their ways to Ubuntu? This would be very naive at best. All kinds of people with all kinds of knowledge will find their way to Ubuntu, which is something very good as long as they try to open their minds a bit and learn about how Linux and Ubuntu work. As long as people come here and start thinking about how to restore their old way security we won't make progress; well we will but not forward. Those new people should invest their energy in learning about Linux and Ubuntu instead of trying to start unnecessary projects for inexistent problems. Maybe inexistent problems isn't the right definition the problem is between chair and keyboard.

---

### Post by arapaho on 2010-11-03
> **mainerror said:**
> The problem is that for the average user a firewall application symbolizes total security as the don't know better and they don't have to further think about anything because "Hey, I have a firewall; I'm secure!". This is exactly the thinking I always encounter and I'm doing private support almost 7 years now. 
Don't generalize and don't exaggerate. I'm interested in all kind of security stuff like apparmor, iptables and I try to implement some good advise from forum, but I don't want to became a computer geek. Having more simple solution doesn't contradict security knowledge.

---

### Post by brian_p on 2010-11-03
> **arapaho said:**
> Don't generalize and don't exaggerate. . . . . . .

He is generalising but not exaggerating. Ask most people why they use a firewall and the answers will extend from 'don't know, but it is recommended' to 'it makes you safer'. If you are wise you do not persue it.

---

### Post by arapaho on 2010-11-04
> **brian_p said:**
> If you are wise you do not persue it.
He, he. Maybe I'm not so average.:)
Besides, my point is: most users will choose the most simple solution and operating system, also considering safety solutions simplicity. And even Unity desktop won't increase Ubuntu popularity considerably.
Observing what Canonical is doing, they want to make Ubuntu more popular and user friendly. At least they should think about apparmor GUI with "block THIS application from accessing Internet' feature. OpenSuse has a GUI for apparmor and apparmor will be included in 2.6.36 kernel, so it is the right time to think about it.

---

### Post by mainerror on 2010-11-04
I don't think that here is anyone arguing that it is bad to have a GUI for apparmor. What I've been trying to say of the past few pages is that only with a nice little GUI for apparmor and also only with apparmor, or iptables and all other security applications you ain't done. If users demand to make a certain distro more like an older distro just so they don't have to learn anything new then we will be moving in circles.

Linux and thus Ubuntu is getting more and more popular as many of you have observed. That will certainly draw attention to the malware coding scene and they will also definitely start concentrating to find ways to exploit security holes and so on. With users denying to learn about security we are going to end up same as in the past only the operating system name will change on all those quotes from people not understanding whats really going on "Meh I've been hacked ... Ubuntu sucks." but hey before they were secure because "Hey I have a nice GUI to control an application which enhances security even tho I don't have any clue about what security is. But I'm secure because this software is supposed to protect me against any bad.".

Sure I'm generalizing because fact is that the majority of the people out there have no clue about security but believe me I'm not exaggerating; not even a slightly bit. It's what the majority of people understand as being secure. Having a firewall on their system makes them unbelievably secure as no one really tried to understand is because no one really tried to teach them what security is in am easy to understand way. I'm not saying that I'm the one who can teach everyone what security is at least not in an easy to understand way but I know that there are very talented people out there (talented in terms of teaching).

So to sum it up. Is it good to have a GUI for a security application? Definitely; it makes it easier for people to control them. Is it enough to just create a GUI or more security tools without teaching people about security? Probably if you deny history if you are someone like me who'd like to not let history repeat then definitely no.

---

### Post by bodhi.zazen on 2010-11-04
> **mainerror said:**
> I don't think that here is anyone arguing that it is bad to have a GUI for apparmor. What I've been trying to say of the past few pages is that only with a nice little GUI for apparmor and also only with apparmor, or iptables and all other security applications you ain't done. If users demand to make a certain distro more like an older distro just so they don't have to learn anything new then we will be moving in circles.

Linux and thus Ubuntu is getting more and more popular as many of you have observed. That will certainly draw attention to the malware coding scene and they will also definitely start concentrating to find ways to exploit security holes and so on. With users denying to learn about security we are going to end up same as in the past only the operating system name will change on all those quotes from people not understanding whats really going on "Meh I've been hacked ... Ubuntu sucks." but hey before they were secure because "Hey I have a nice GUI to control an application which enhances security even tho I don't have any clue about what security is. But I'm secure because this software is supposed to protect me against any bad.".

Sure I'm generalizing because fact is that the majority of the people out there have no clue about security but believe me I'm not exaggerating; not even a slightly bit. It's what the majority of people understand as being secure. Having a firewall on their system makes them unbelievably secure as no one really tried to understand is because no one really tried to teach them what security is in am easy to understand way. I'm not saying that I'm the one who can teach everyone what security is at least not in an easy to understand way but I know that there are very talented people out there (talented in terms of teaching).

So to sum it up. Is it good to have a GUI for a security application? Definitely; it makes it easier for people to control them. Is it enough to just create a GUI or more security tools without teaching people about security? Probably if you deny history if you are someone like me who'd like to not let history repeat then definitely no.

Linux is not Windows and Unix has been around for longer then Windows.

Linux is designed from the ground up to be secure and at this time we do not have the same problems with malware.

It is not as if *nix is not a target as *nix has a high penetration in the server market.

The suggestion that Linux users somehow ignore security is a false assumption.

If such a problem develops the general solution is to patch the code, ie security updates.

This thread is essentially a discussion with new users applying Windows mentality to Linux making broad claims that Linux needs to somehow change.

The take home message more experienced users are trying to convey comes down to several items.

1. Relax. This is not Windows.

2. Linux is secure by default. The developers have taken care of security for you.

3. If you want to harden your system it will require a bunch of reading. A graphical front end may help, but you still need to know a fair amount about Linux in order to configure apparmor, GUI or no.

If you are interested in security, start reading. Start with the security sticky and move to the Apparmor and HIDS/NIDS threads.

Only when you do some reading and learning will you fully understand security.

See also:

[http://www.debian.org/doc/manuals/securing-debian-howto/](http://www.debian.org/doc/manuals/securing-debian-howto/)

[http://www.debian.org/doc/manuals/securing-debian-howto/ap-harden-step.en.html](http://www.debian.org/doc/manuals/securing-debian-howto/ap-harden-step.en.html)

---

### Post by arapaho on 2010-11-05
bodhi.zazen - You are 'The Great Guru of Ubuntu Security' and it is easy for you to operate all this mysterious applications like apparmor. 

And definitely I will read, read and read but - my first experience with apparmor started like this:
[http://ubuntuforums.org/showpost.php?p=10075007&postcount=155](http://ubuntuforums.org/showpost.php?p=10075007&postcount=155)
I downloaded apparmor profiles and put them into enforce mode and now I can't even make a pdf from web page because cups are blocked by apparmor. Firefox doesn't work too, it is blocked somehow.

Now I have to learn how to interpret all this logs and apparmor messages. It is a way too much for a newbee like me. It makes me frustrated. :(
Besides I'm a humanist and this IT stuff is so difficult to understand to me even when I try. Please, tell Ubuntu developers that a simple solution for NON geeks is requested.
I really don't want to apply Windows mentality but apparmor profiles and logs are too difficult.

I discovered 
[http://brainstorm.ubuntu.com/idea/21652/](http://brainstorm.ubuntu.com/idea/21652/)
This idea is a duplicate of Idea #8827: gui apparmor.

Why Ubuntu developers haven't implemented it yet? Why Unity desktop is more important?

Can you also comment on what chocolateboy wrote about snet #12 and LucasAdams #47?

---

### Post by bodhi.zazen on 2010-11-05
> **arapaho said:**
> bodhi.zazen - You are 'The Great Guru of Ubuntu Security' and it is easy for you to operate all this mysterious applications like apparmor. 

And definitely I will read, read and read but - my first experience with apparmor started like this:
[http://ubuntuforums.org/showpost.php?p=10075007&postcount=155](http://ubuntuforums.org/showpost.php?p=10075007&postcount=155)
I downloaded apparmor profiles and put them into enforce mode and now I can't even make a pdf from web page because cups are blocked by apparmor. Firefox doesn't work too, it is blocked somehow.

Now I have to learn how to interpret all this logs and apparmor messages. It is a way too much for a newbee like me. It makes me frustrated. :(
Besides I'm a humanist and this IT stuff is so difficult to understand to me even when I try. Please, tell Ubuntu developers that a simple solution for NON geeks is requested.
I really don't want to apply Windows mentality but apparmor profiles and logs are too difficult.

I discovered 
[http://brainstorm.ubuntu.com/idea/21652/](http://brainstorm.ubuntu.com/idea/21652/)
This idea is a duplicate of Idea #8827: gui apparmor.

Why Ubuntu developers haven't implemented it yet? Why Unity desktop is more important?

Can you also comment on what chocolateboy wrote about snet #12 and LucasAdams #47?

Linux is not windows.

I suggest you relax and use Ubuntu "as is" without attempting to change anything.

If you have a problem, post here for assistance.

I think your problem boils down to applying Windows mentality to Ubuntu.

I am not suggesting you should ignore security, keep reading and asking questions. But understand the vast majority of people run Ubuntu without any additional hardening and without any of the problems you may have experienced with other OS.

I think a better question is, what makes you think you need to harden Ubuntu ?

Gui front ends do not help with apparmor. You need to read and understand the warnings in your logs. A GUI front end that simply asks "Do you want to allow this (Y/N)?" does nothing as you do not understand what you are allowing or what the implications of allowing such access. IMO, you might as well just disable apparmor if you are going to allow everything without understanding the underlying principles.

You can not write an apparmor profile for firefox that applies to everyone because everyone uses firefox differently. Only you can know how you use firefox and what you wish to add or disable.

If you are new to apparmor, firefox is not the place to start as firefox is a complex application with very broad and variable needI (everything from internet access to audio/video to PDF files to apt-url). Start with a simpler application such as say Privoxy (as one example) and build up to firefox.

How long have you used Windows ? Give yourself 6-12 months to learn the OS, then you will understand better.

---

### Post by arapaho on 2010-11-05
> **bodhi.zazen said:**
> I think a better question is, what makes you think you need to harden Ubuntu?
I'd like to use programs from different sources like for example from this site
[http://www.linuxlinks.com/Software/](http://www.linuxlinks.com/Software/)
not only from repositories. And I'm not sure if they are safe and if they can contain a spyware or a keylogger. So, just in case I'd like to block them right at the installation process.

---

### Post by brian_p on 2010-11-05
> **arapaho said:**
> I'd like to use programs from different sources like for example from this site
[http://www.linuxlinks.com/Software/](http://www.linuxlinks.com/Software/)
not only from repositories. And I'm not sure if they are safe and if they can contain a spyware or a keylogger. So, just in case I'd like to block them right at the installation process.

You were doing very well with your argument until now.

You think something from linuxlinks may contain some malware. Maybe it does, maybe it doesn't. But it's what you think that counts. So why download it and install it.? Are you sure you really want to use programs from this source?

But now you want the installation process to say - "don't do this, it's dangerous!". The computer is not a replacement for your brain.

---

### Post by arapaho on 2010-11-05
> **brian_p said:**
> But now you want the installation process to say - "don't do this, it's dangerous!". The computer is not a replacement for your brain.
No, I want to block it just in case if it could help to be more secure. Some time ego there was a dangerous code in gnome screensaver. I think linux users should be protected somehow by software. The only question is to what degree. But even if I had a very large and smoothly running brain I wouldn't be able to prevent all possible present and future dangers myself. And limiting users only to repository won't make linux more popular. 
So, definitely there should be easy programs supporting users and _warning_ them. I don't see it strange. It is rather normal in windows that for example firewall or antivirus pop-ups a message. Linux doesn't have to be like windows but I have to admit that being user friendly is a good feature and doesn't contradict user awareness and knowledge about security issues.  

That's sad that I can't use application from other sources. 
How about commerce application in Canonical store? Does Ubuntu team check them if they don't have any dangerous code, do they have access to source code? For example PowerDVD? What is its licence?
[http://shop.canonical.com/product_info.php?products_id=243](http://shop.canonical.com/product_info.php?products_id=243)
How can I be sure that they don't gather information for some marketing/commercial purpose?

If your advice is not to use any software from outside repository it greatly limits functionality of the system, because OS is for running applications and is only functional to the degree applications for this OS are.

Anyway, I have the feeling that this discussion doesn't change anything.

---

### Post by CharlesA on 2010-11-05
It's a port of PowerDVD for Linux. What's the problem (outside of it not being listed as able to be used with 10.04 and 10.10.

Most software is in the repos, but there are some stuff that isn't, which you can find in PPAs or by compiling them from source.

As long as you know the file is from a reputable source you'll be fine.

---

### Post by brian_p on 2010-11-05
> **arapaho said:**
> No, I want to block it just in case if it could help to be more secure.

If you install a program which you consider to be insecure or which you don't completely trust how does 
blocking it make it more secure?

> If your advice is not to use any software from outside repository it greatly limits functionality of the system, . . . . . 

There are 30,496 packages in Debian unstable. I've never noticed any limitation in functionality of the system.

---

### Post by oldos2er on 2010-11-05
> **arapaho said:**
> No, I want to block it just in case if it could help to be more secure. Some time ego there was a dangerous code in gnome screensaver. 

That is not something that would've been caught by a firewall. I don't even know if AppArmor would've; I doubt it, but don't know enough to say one way or the other.

---

### Post by HermanAB on 2010-11-06
Hmm, got to add my 2 Fils worth:
You are not going to get much support for this type of application, since it has already been beaten to death six ways to Sunday:
SELinux
Tomoyo Linux
AppArmor
Iptables
Sudo
TCPwrappers
ACLs

OK, seven.

Therefore, you would probably do better by learning the above systems first, before reviving an abandoned project.

---

### Post by Abir Valg on 2011-01-11
Leopard Flower does per-application firewalling on linux
[https://sourceforge.net/projects/leopardflower/](https://sourceforge.net/projects/leopardflower/)
Cheers

---

### Post by arapaho on 2011-01-15
> **Abir Valg said:**
> Leopard Flower does per-application firewalling on linux
Thank you for information. I wish some advanced users would test it and share their opinions.

---

### Post by opendoors on 2011-02-28
bodhi.zazen made a few observations in post #5 that I feel are worthy of further discussion:

> **bodhi.zazen]
Part of the reason is that Linux is not Windows and this type malware does not exist in Linux.
[/QUOTE]

[QUOTE=bodhi.zazen]
Last, the amount of "damage" any potential clinet could do is very  limited on Linux. Sure it could affect things in /tmp or /home, but not  system files.
[/QUOTE]

First, the definition of malware is very broad, and it is often difficult to draw the line between harmful software and "undesirable" software. By "undesirable", I mean software that may send information about your system configuration to some remote server. For example, if I use certain printers, I am forced to install the "driver" provided by the manufacturer, which actually consists of a bundle of undesirable software that I have no choice but to install, since I can only install the driver by installing the entire bundle. Despite any boxes I uncheck, I still do not trust this bundle when it tries to access the Internet, whether it's asking me to register or simply trying to call home with some "nonpersonal" system information. I think it's important to remember that while some people might not care about their system information being phoned home, others (such as me) feel that this is a threat that should be stopped. For this and other reasons, it is not easy to simply classify every threat to your security as "malware". Even if it is true that no malware conceived of in the same sense as bodhi.zazen exists on Linux, it is certainly not true that nothing more subtle but nonetheless undesirable exists. In such cases, I think a user could at least potentially benefit from having an application firewall similar to what has been called "windows based". Even if malware/undesirableware (for lack of a better word) could not affect system files, that doesn't mean it can't phone home with personal information or non system files. It wouldn't require a "specific vulnerability" in Ubuntu for this to happen.

I'm not going to make the claim that software downloaded from repositories are unsafe. However, I do want to emphasize that it's sometimes impossible to stick only to software in repositories. A printer driver, much like the one I described, or even an important application that has to be run in Wine, is sometimes unavoidable. In fact, when installing Ubuntu for the first time, users will often see the explicit suggestion that they install third party drivers for better functionality (e.g. for their video card). In such situations, users often don't have a choice. They have to use the software, but they also want to maintain their privacy. With a proper application firewall, they won't have to sacrifice their privacy for the sake of functionality.

[QUOTE=OpSecShellshock]
Things like word processors and other productivity applications probably don't need to most of the time, and so they won't. When there's an active link in a PDF or doc file, it will open a browser if there's not one already open, rather than simply connecting itself (well, except for Adobe Reader, which for whatever reason allows the running of scripts and can access the web directly, but that's just bad design and there are alternatives).
[/QUOTE]

"Most of the time" isn't good enough if good security is a concern. For those who still need Microsoft Office, it does try to access the Internet for no good reason even if all you're doing is word processing. Using a packet sniffer to try to determine exactly what it and similar applications might be phoning home is both impossible and impractical. There are so too many applications whose developers consider accessing the Internet a right rather than a privilege. In situations where using an alternative is not an option, it would be much simpler to simply block all connection attempts until a user gives their explicit approval through a popup prompt.

[QUOTE=cariboo907]A firewall really doesn't do anything on a default installation, as there are no ports open to the outside world, and if you are behind a router, it's a belt + suspenders type of activity.

it's just like the poster earlier that tried to block Opera from accessing the Internet. Web browsers and many other programs use random high ports for out going connections, so it's pretty hard to block a port if you don't know which one it is using, and it changes every time you use a program, have a look at this example:
[/QUOTE]

I think you are actually proving the point that an application firewall is important in at least some situations. Since it's so difficult to predict exactly what port an application might be trying to access, it would be easier to add the ability to restrict access by application rather than by port. Of course, good Windows firewalls allow both said:**
> This program is incredibly silly - not only can all its functionality be accomplished easily with iptables, the entire idea is pointless: simply running 'sudo netstat -nep' will quickly tell you exactly what programs are accessing the internet. Anything that can make itself invisible to netstat would have to be some sort of rootkit, and by definition a rootkit could easily bypass filtering like TuxGuardian. There are several GUI frontends for the kernel iptables functionality out there - if you're too lazy to use the shell, use those.

This is exactly the thing that would sound like a great idea to someone unfamiliar with Linux, when in reality it is a greater detriment to security than the service it provides is worth. It reeks of Windows, and I don't like it.

-1 from me.

I will agree that an application firewall is not an adequate defense against rootkits, but I also think you are missing the point of such a program. For everything that is not hidden but not necessarily desirable, an application firewall could be an excellent response.

I also found it interesting that you claim an application firewall would be a "greater detriment to security than the service it provides is worth". Jake Edge quotes Paul Moore on the "user request" feature of personal firewalls: "my opinion is that it is a poor option for security and typically only results in training the user to click the 'allow' button when the pfwall [dialog] box pops up on his/her screen". The problem with Moore's claim is overgeneralization. Not all users are typical; therefore, not all users will blindly click "allow" when the dialog pops up, especially users who specifically seek such a feature. What typical users do is irrelevant anyways if you consider that most users don't care about their security. What matters is what the atypical/conscientious users do, and I think there are at least some users in this latter group that could benefit from an application firewall.

[QUOTE=mainerror]
I don't quite understand why people tend to be that paranoid about such stuff but then click on a IM message that they can win a iPhone 4 or that there is an awesome video on YouTube they just have to watch. Peoples common sense and the sense for security seems to be extremely off which is exactly the point I'm talking about.
[/QUOTE]

How exactly is stereotyping people being productive/helpful in a community like this? The same people who worry about the collection of statistics are not always the same people that click on an IM message that they can win an iPhone 4.

[QUOTE=OpSecShellshock]
Having said that, when I first started using Ubuntu I also denied all outbound traffic and then put in exceptions. The only things that ended up happening were that my messages log was filled with a bunch of DHCP failures and my clock was always wrong because my NTP requests weren't getting out. Eventually I made exceptions for those, after learning what they were (and there was no way around having to do that, see).
[/QUOTE]

[QUOTE=mainerror]Those new people should invest their energy in learning about Linux and Ubuntu instead of trying to start unnecessary projects for inexistent problems. Maybe inexistent problems isn't the right definition the problem is between chair and keyboard.[/QUOTE]

I agree. There is no way around learning what to make exceptions for. But with a proper application firewall, the process can certainly be made easier. If you were prompted to allow out the requests to automatically correct your clock, you could then find out what the request was for instead of looking through your logs for everything that might be legitimate and then making an exception for it. Allowing everything and blocking everything else is good if security is the only thing you care about or if you're an expert who already knows exactly what to allow. But for the rest of us who aren't experts, it would help if there was an application firewall to accelerate the process of learning. Even if you disagree with oversimplifying everything, it surely wouldn't hurt to help us learn some of what the experts already know.

[QUOTE=OpSecShellshock]
My hope is that a testimonial from my own experience as a new user will be more helpful than a simple repetition of the same things long-time users always say.[/QUOTE]

Thanks! Your testimonial has definitely been helpful! I think it helps to know that allowing some things and blocking everything else is at least a start.

[QUOTE=mainerror]Well thank you very much for posting this as this is exactly what I'm ranting about the last couple of pages. I'm talking about that absolute security is an illusion where a simple front-end giving you the option to simply mark a checkbox to block something only amplifies this illusion.[/QUOTE]

To be fair, I don't think that anybody is disagreeing that absolute security is an illusion. We all know that rootkits can bypass application firewalls. But I think it's also important to note that application firewalls can help a new user more quickly learn about legitimate processes and enhance security in at least some situations. So at the very least, being able to mark a checkbox can do much more than simply amplify an illusion of absolute security. On the other hand, if anyone believes there is such a thing as absolute security, the lack of a checkbox certainly won't help matters.

Still not convinced? See this: [http://lwn.net/Articles/129729/](http://lwn.net/Articles/129729/)

---

### Post by cariboo on 2011-02-28
> **opendoors said:**
> I think you are actually proving the point that an application firewall is important in at least some situations. Since it's so difficult to predict exactly what port an application might be trying to access, it would be easier to add the ability to restrict access by application rather than by port. Of course, good Windows firewalls allow both; first, you define whether an application is allowed Internet access at all. Then, you specify which (if any) ports it is allowed to access.


It may be worth your while to actually check how services connect to each other. If a web browser wants to connect to for example to ubuntuforums.org it opens port 77540 to connect to port 80 at 72.14.213.102, if you now want to connect to [www.google.com](www.google.com), a new random high port to is opened to make the connection to port 80 at google. It works the same for any other service too. It would be pretty hard to block the source port for every application, as they use different source ports for every connection that is initiated.

Here's another example, I'm connected to my G3 via ssh this is what the port info looks like:

```
ssh        **2002** cariboo    3u  IPv4  19211      0t0  TCP 192.168.1.215:**41201**->192.168.1.235:**22** (ESTABLISHED)
```

If I connect to the same computer a second time while still connect via the first instance the connection looks like this:

```
ssh       **12629** cariboo    3r  IPv4  78494      0t0  TCP 192.168.1.215:**36754**->192.168.1.235:**22** (ESTABLISHED)
```

As you can see the pid for both instances is different, as well as the source ports. I've bolded the pid, source and destination ports. So if you have no way of identifying the service, and source ports before the application is tarted, it's going to be pretty hard to selectively block applications.

---

### Post by bodhi.zazen on 2011-02-28
> **opendoors said:**
> bodhi.zazen made a few observations in post #5 that I feel are worthy of further discussion:

<clip>
</clip>



If you are wanting to micromanage your internet connections you will need to use a tool such as tcpdump and / or wireshark.

You then limit connections with iptables.

Start by blocking all outbound traffic and then whitelist those connections you wish to allow.

If the white list is too long, go the other way, allow  all, and black list ip addresses you wish to block.

---

### Post by wdtd on 2011-03-01
I have seen ***in Windows***, installation packages come with "phone home" software. I don't want my printer or my camera program or any other pieces of software to "phone home"  without my permission but I need to install that entire Windows installation package to get my stuff to work.

Now, almost all of the **Linux** programs we use are written by people who respect that **I** own my computer and I should be able to decide what it does. 

BUT, I fear as we see more businesses provide "Linux installable" packages, they may start to add "phone home" functionality here as well and we won't always have an Open Source alternative, especially for specialized devices.

Therefore, I would love an additional tool in my security toolbox that would provide a default deny and/or notification per application to compliment our great port based tools.

---

### Post by ikt on 2011-03-02
> **wdtd said:**
> BUT, I fear as we see more businesses provide "Linux installable" packages, they may start to add "phone home" functionality here as well and we won't always have an Open Source alternative, especially for specialized devices.

What is the problem with using GUFW to block all outgoing programs by default and add the programs as you need?

---

### Post by bodhi.zazen on 2011-03-02
> **ikt said:**
> What is the problem with using GUFW to block all outgoing programs by default and add the programs as you need?

gufw blocks ports (80, 443, 53, etc) and not applications.

So if you allow port 80 , all applications can use port 80.

---

### Post by wdtd on 2011-03-03
Okay, this discussion has inspired me to better understand how IPTables work. :popcorn:

IPTables seem to be the core of Ubuntu's firewall protection and is a powerful set of "chains" to control port access with the functionality of ```
-m owner --uid-owner {UID}
```I could move programs or users to their own UID then just LOG them using IPTables by their UID or GUID, yes?

---

### Post by bodhi.zazen on 2011-03-04
> **wdtd said:**
> Okay, this discussion has inspired me to better understand how IPTables work. :popcorn:

IPTables seem to be the core of Ubuntu's firewall protection and is a powerful set of "chains" to control port access with the functionality of ```
-m owner --uid-owner {UID}
```I could move programs or users to their own UID then just LOG them using IPTables by their UID or GUID, yes?

yes you could.

See also:

[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

---

### Post by opendoors on 2011-03-04
[QUOTE=wdtd]I have seen ***in Windows***, installation packages come with "phone home" software. I don't want my printer or my camera program or any other pieces of software to "phone home"  without my permission but I need to install that entire Windows installation package to get my stuff to work.

Now, almost all of the **Linux** programs we use are written by people who respect that **I** own my computer and I should be able to decide what it does. 

BUT, I fear as we see more businesses provide "Linux installable" packages, they may start to add "phone home" functionality here as well and we won't always have an Open Source alternative, especially for specialized devices.

Therefore, I would love an additional tool in my security toolbox that would provide a default deny and/or notification per application to compliment our great port based tools.[/QUOTE]

I agree with you about the "phone home" functionality. This is not just a Windows problem. For some of my hardware devices, the manufacturer offers installation packages for both Windows **and** Linux. The Windows installation package phones home. Thus, I have every reason to believe that the Linux installation package also phones home and no reason to believe that it doesn't. The only difference is, in Windows, I have a way to tell that it's trying to phone home and I can stop it. In Linux, I either can't or I have to spend exorbitant amounts of time and effort to achieve the same goal.

As people have already argued, even software from supposedly trustworthy developers phones home. Do you want to trust others to safeguard your information or would you prefer to have some control over it yourself? Trust alone is clearly not an adequate solution.

---

### Post by cariboo on 2011-03-04
@opendoors, you keep talking about programs that phone home, could you please give us some examples of programs you have installed from the repositories that do this. If you install programs from untrusted sources, of course, then all bets are off. 

Using a Linux variant takes a different state of mind, from using Windows, we don't download and install packages from just anywhere. All Linux distributions have trusted repositories, and in most cases if you can't find a package in the repositories, you probably don't need it.

My personal opinion is that if you are a gamer, keep your windows system, and use an older system to run a Linux variant.

---

### Post by opendoors on 2011-03-05
[QUOTE=cariboo907]@opendoors, you keep talking about programs that phone home, could you please give us some examples of programs you have installed from the repositories that do this. If you install programs from untrusted sources, of course, then all bets are off. 

Using a Linux variant takes a different state of mind, from using Windows, we don't download and install packages from just anywhere. All Linux distributions have trusted repositories, and in most cases if you can't find a package in the repositories, you probably don't need it.

My personal opinion is that if you are a gamer, keep your windows system, and use an older system to run a Linux variant.[/QUOTE]

"Drivers for hardware devices" is as specific as I will get. I don't publicly disclose my hardware for security reasons. If it turns out there's a specific flaw in the firmware, I don't want to put myself at risk. Naming a specific device won't help this discussion anyways. I would probably not be here if I was lucky enough to not fall into this unfortunate category. I know some people also like to run games in Wine. This too would suffer from the same security problem.

As people have pointed out, packages in the repositories phone home also, even if some believe it's for innocuous purposes. I don't care if it's just reporting anonymous statistics. They have no right to get any information from me, no matter how trivial they might think it is. If I haven't given my explicit consent, then nothing should be getting out.

---

### Post by cariboo on 2011-03-05
With that kind of paranoia, I can see where you are coming from. How do you justify using the internet then?

---

### Post by opendoors on 2011-03-05
[QUOTE=cariboo907]With that kind of paranoia, I can see where you are coming from. How do you justify using the internet then?[/QUOTE]

Ad hominem. The focus should be less on what hardware I'm using and more on the problem at hand. You asked for examples, and they were given. Can you guarantee that even programs in the repositories don't phone home at all? Even if you can, not everyone is willing to use only software in the repositories, as useful as they might be.

---

### Post by cariboo on 2011-03-06
I've been using Ubuntu since 2006, aside from Ubuntu checking for updates, and a time server on every reboot, I haven't found anything on a default installation that phones home. None of the packages installed from the repositories that I use on a daily basis phone home. 

If you use a media program that downloads album covers and lyrics, you may call that phoning home, but you can turn those features off when setting up the programs.

If you aren't installing packages from trusted repositories, you are doing it wrong, and leaving yourself open to vulnerabilities that may come from unsigned packages.

Btw even without using a firewall of any sort, except for my router, I can tell you exactly which programs are making connections to the internet, can you do the same with your favorite operating system?

---

### Post by The Cog on 2011-03-06
This is becoming a very windows-think vs nix-think discussion. I hope it doesn't descend into a bun-fight.

I think overall, I'm in the nix camp. In general, if you don't trust a program, don't install it. 

The "Windows Way" is to install any old rubbish you can find anywhere on the net, and it can be a hard habit to break. It does of course mean that your PC ends up being everybody else's except yours. Sticking plasters like application based firewalls can stop some of the stuff, but it's a bit like a Keep Off The Grass sign - it won't stop those that really want to.

The *nix way is to not install any old rubbish that you don't trust. Just say no. This has worked well for a long time, though it does mean that sometimes you have to go wthout $cool_software because a trustworty one doesn't exist. 

There are probably an infinite number of shades of grey in between. And software that you know is OK apart from a phone-home habit that you can't switch off is an interesting one. I think such software should be running under AppArmour's watchful eye. Especially since if it won't let you stop it phoning home, it clearly doesn't feel that it works for you, but for someone else. I would put it in the Untrusted category because you don't know what else they might want to do without your permission.

I have doubts about using a blanket application-based firewall. Firstly, if you have to block untrusted software from using the internet, you should also wonder what else is it doing that needs blocking. Maybe starting other applications in the background, and getting them to use the internet on your behalf? Installing a rootkit?

As for drivers, my guess is that if you install an untrusted driver then you really are pwned. And an "application based" firewall - what application is it going to think that is - the kernel??? It occurs to me that I have no idea how you could tell what application caused a socket to open anyway. Was it Firefox, or the program (bash, gnome etc) that chose to launch Firefox? Or the program that chose to launch the program that launched Firefox? **init**? It's not a facecious question - I occasionally see network activity and look at netstat -p to see what it is, only to find that it's wget and I wonder "Who is using that???" Really, how far up the process tree should one go before declaring "THAT's the application that did it!". Ultimately, it's **init** that did it all.

As for user based filtering, I think that has some possibilities. But I'm not sold on running different applications as different users in order to achieve something like application based filtering. That would involve having different people (hubby and wifey for instance) run firefox as different users (hubby-ff and wifey-ff perhaps) whch gets complicated and rules hour setuid - they would probably have to use a password to launch firefox every time. White-listing web sites by user is something that iptables could reasonably do though.

If firefox is phoning home as soon as it starts, you need to wipe ~/.mozilla and start again in my view.

In all, I feel that if you really want to run software that you can't trust, you should do it in a VM or in a AppArmour jail, or in an AppArmour jail in a VM. The expression "It's turtles all the way down" comes to mind.

Yes, I'm rambling. But in all, I don't think that "application based" firewalling is practicable or useful. Certainly not in the case where different users must have different rights with the same application.

---

### Post by opendoors on 2011-03-13
[QUOTE=The Cog]
There are probably an infinite number of shades of grey in between. And software that you know is OK apart from a phone-home habit that you can't switch off is an interesting one. I think such software should be running under AppArmour's watchful eye. Especially since if it won't let you stop it phoning home, it clearly doesn't feel that it works for you, but for someone else. I would put it in the Untrusted category because you don't know what else they might want to do without your permission.
[/QUOTE]

Running such software in a virtual machine is an interesting, but  somewhat cumbersome solution. I would hate to have to transfer  everything I need to print to the virtual machine (which would also be  running Ubuntu as a guest OS). But this is just one of the problems.  You're right that there's an almost infinite number of shades of grey in  between. Unfortunately this calls for multiple virtual machines with  different sets of restrictions on what (and how) things can run. I think  at some point, virtual machines alone aren't a perfect solution.

My printer's driver is one such software that does phone home. What do you mean by AppArmor's "watchful eye"? Would AppArmor be able to stop the phone home functionality? Based on what I've read, it can't.

Ideally, I want to block absolutely everything (including the clock) until allowed (I would of course keep an eye on what's happening with Wireshark, then allow things one by one). If AppArmor is not the right tool for the job of blocking everything, what is? Right now, I only know of tools that block by port, but not by application or destination IP, which is a problem. Even if I'm willing to do all the work of monitoring by myself (I am as long as it's a whitelist, rather than a blacklist solution), I still need an effective blocking mechanism. Without one, I'd have to rely completely on trust rather than being able to make my own decisions. Is there anything that would allow me to do this now that Tuxnet has been abandoned?

---

### Post by arapaho on 2011-03-14
I wonder what Canonical think about this issue. If it comes up all over again it would be nice if they share their opinion. 
I'm glad to know what advanced users think but I don't their attitude at all. 
I don't think Ubuntu security model is the best possible. Definitely, it can be improved.
I had a look at Canonical web site but there is no way to contact them, unless one wants to pay for support.
It would be nice if somebody from Canonical team could comment on brainstorm idea referred in my footnote.

---

### Post by iiiears on 2011-03-14
It wasn't until opendoors offered a point by point explanation that i really understood the rift. Thank You for doing that.
 

 This thread is long, informative and in places undeniably humorous.  Many Thanks.


 
 Best wishes.

---

### Post by cariboo on 2011-03-14
@arapaho most communications with developers is done through mailing lists. I don't know how busy it is, but if you have security questions, I suggest you ask them on the [ubuntu-hardened]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-hardened") mailing list.

---

### Post by wdtd on 2011-03-14
I Love Linux and as long as we only stick with the Repositories and there are no breeches  in trust or major coding issues; we will be fine. This is what I do but  I would still feel better if I had a program that would **more easily  track which programs access** the Internet both to control my "pay per  use" Internet access and if there is a problem. This is especially true now that so many programs use port 80 and/or so many temporary ports. 

(Thank you for the suggestions for how to track with the current super-tools. :) I am looking at making them work but they are complex.)  

 I have seen  newer users download stuff from the Repos that turned on smbd, nmbd,  sendmail, and postfix services over the years without their realizing or  intending it. Thank goodness I think to look when they ask me and  that UPnP wasn't on while their firewalls were. I still don't know how  they did it but an application firewall could have warned them before I did.

Canonical-census caused philosophical debates with the OEM installs and when phone-home is okay.

The Debian OpenSSL PRNG bug shows we aren't perfect.

Sourceforge was cracked (but with great recovery on their part... ) and malware was hidden inside a screensaver on gnome-look. Doesn't the Wine  install pull from Sourceforge?

For a few, linux hardware  drivers and embedded Linux are still an issue. especially for  specialized hardware like accessibility and business devices including  tablets. I have a friend who is using the  manufacturer's drivers for his special monitor since he couldn't get it  working on SUSE with the open drivers.

When I need to use metered (pay per use) Internet use and just want to check my webmail I have to remember to turn off all the Internet functionality of my music player, my email program, etc. then remember to turn them all back on when I can use unmetered use.

The point of this long rambling post is that different people have different needs and I appreciate everyone discussing this issue so we can find solutions for all of us. Thank you! :KS

---

### Post by butler360 on 2011-05-31
OMFG, wow... this is the most exasperating post to read.   ](*,)](*,)](*,)](*,)](*,)

The average user is **never** going to futz around with IPTABLES, ***ever***. I know you'd like to see that, but it's never going to happen.

Does the average person know how to change their oil? Nope, and that's vastly easier than anything computer related.

At any rate, allow me to sidestep the whole security argument. What about programs that are just annoying? Say Adobe starts making software for Linux and they stick with their Windows-style updater and such? Let me guess your response, "They wouldn't do that on Linux." We don't know that, so let's say they do. It would be nice to not have to block ALL internet traffic in order to block the Adobe updater.

Or as the person above me states, it would be useful to control bandwidth. Maybe you want to schedule certain programs to only connect at certain times of the day?

Either way, the real insanity here is that some cannot even concede that this would ever in any way be useful on Linux, since "that's not the Linux way, you're thinking like Windows, which sucks." Well Linux is much superior, right, so why not match the capabilities of Windows?

---

### Post by bodhi.zazen on 2011-05-31
> **butler360 said:**
> Either way, the real insanity here is that some cannot even concede that this would ever in any way be useful on Linux, since "that's not the Linux way, you're thinking like Windows, which sucks." Well Linux is much superior, right, so why not match the capabilities of Windows?

Welcome to Linux. One of your new found freedoms is to write just such an application for yourself.

You could try to convince a more experience Linux user to assist you or possibly write it for you, but you have two problems.

1. More experienced uses do not see the need.

2. Your posting style comes across as rather demanding, and this is not a good tone to use if you are seeking assistance of others.

---

### Post by butler360 on 2011-05-31
> **bodhi.zazen said:**
> Welcome to Linux. One of your new found freedoms is to write just such an application for yourself.

You could try to convince a more experience Linux user to assist you or possibly write it for you, but you have two problems.

1. More experienced uses do not see the need.

2. Your posting style comes across as rather demanding, and this is not a good tone to use if you are seeking assistance of others.

You've got it wrong again. Where did I ask anyone to DO anything? Like I said, it shouldn't be that hard to just concede that this would be useful.

Please point out where I demand that someone write this program for me?

---

### Post by CandidMan on 2011-05-31
> **butler360 said:**
> 

The average user is **never** going to futz around with IPTABLES, ***ever***. I know you'd like to see that, but it's never going to happen.


I quite agree with this sentiment. And while I was using it COMODO firewall was actually really user-friendly and intuitive.
I actually learnt more about networking from those help pages than I did from anything built into my operating system.
But I see that application as 'training wheels' now. And like a bike's training wheels they need to be ditched eventually if you're ever going to get a proper experience.
I'd imagine the reluctance to continue to develop an app like TuxGuardian is due to a combination of an understanding of the Linux ecosystem, arrogance, elititsm, lack of demand and a lack of (perceived)need.

I'm not against TuxGuardian or similar but have you actually looked at iptables?
```
sudo iptables -I OUTPUT -p all --destination badsite.com -j DROP
```
and that's it. No more connections to badsite.com
Computers are complex pieces of equipment. Would you be comfortable if you were on a plane and the pilot told you they didn't know how anything worked? That all they had to do was flick a few switches?
Guess what I'm trying to say in a roundabout way is that if you don't understand something you become entirely dependent on those who do...or the warez they're offering.(And no I don't completely understand Linux either :D)

---

### Post by butler360 on 2011-05-31
> **CandidMan said:**
> Would you be comfortable if you were on a plane and the pilot told you they didn't know how anything worked? That all they had to do was flick a few switches?

No, I would not be comfortable. But what percentage of people are pilots versus the number of people who travel in airplanes? The sentiment here is that everyone should be a pilot, it seems.

I know it's easy to block connections to a specific site, but that's just a workaround to accomplish something that could be much easier by just selecting the application you don't want to give access to.

---

### Post by CandidMan on 2011-05-31
Yeah, I know what you're saying. And reading my own posts I think I sound dangerously close to being a geek elitist at times. You don't have to be a pilot, but it does help if you have an interest in planes :)
Have you looked at apparmor?
iptables has lots of options, not sure if you can impose data-cap limits but you impose restrictions based on time, user, packet count etc. It's not so bad if you know exactly 
There's one line you can insert into a profile that I *think *prevent network access:
```
deny network
```
Voila, no network capabilities!!

---

### Post by butler360 on 2011-06-01
> **CandidMan said:**
> Yeah, I know what you're saying. And reading my own posts I think I sound dangerously close to being a geek elitist at times. You don't have to be a pilot, but it does help if you have an interest in planes :)
Have you looked at apparmor?
iptables has lots of options, not sure if you can impose data-cap limits but you impose restrictions based on time, user, packet count etc. It's not so bad if you know exactly 
There's one line you can insert into a profile that I *think *prevent network access:
```
deny network
```
Voila, no network capabilities!!

Well, I don't currently have a *need* for these capabilities since I'm running Ubuntu as a VM, but it's something I'd like to have if I switched over.

---

### Post by dreaminhere on 2011-06-01
My main interest in application firewall capabilities is something that wtdt mentioned. All my interenet is pay per mb and expensive. I don't have another choice. I would love to not get surprises in a huge bill because something decided to update or I forgot to turn something off.

---

### Post by brownb2 on 2011-08-21
I'm also looking for an application based firewall. I recently went abroad with my netbook and £40 (around $70, premium rate bandwidth on foreign network) worth of 3G was blown before I even started using it properly because:

- I left Prey anti-theft running (which can only be disabled via the website).
- Ubuntu auto updates was enabled.
- I also suspect I had a couple of rogue apps connecting on port 80.

I'm pissed Ubuntu let me do this and if legit apps can connect to the Internet without my (at the time) knowing so can rogue apps and something for tracking these sort of outgoing connections is (still) needed. I'm now actually considering having a Windows dual boot system *just* so I can use a real personal firewall.

UPDATE: I've emailed the author of "linux-firewall.org" about getting the source code for his application ( [http://linux-firewall.org/](http://linux-firewall.org/) ) as that seems to be exactly what most people need but I don't trust random binary installers on the 'net offering exactly the kind of thing Ubuntu needs...

---

### Post by bodhi.zazen on 2011-08-21
> **brownb2 said:**
> I'm also looking for an application based firewall. I recently went abroad with my netbook and £40 (around $70, premium rate bandwidth on foreign network) worth of 3G was blown before I even started using it properly because:

- I left Prey anti-theft running (which can only be disabled via the website).
- Ubuntu auto updates was enabled.
- I also suspect I had a couple of rogue apps connecting on port 80.

I'm pissed Ubuntu let me do this and if legit apps can connect to the Internet without my (at the time) knowing so can rogue apps and something for tracking these sort of outgoing connections is (still) needed. I'm now actually considering having a Windows dual boot system *just* so I can use a real personal firewall.

UPDATE: I've emailed the author of "linux-firewall.org" about getting the source code for his application ( [http://linux-firewall.org/](http://linux-firewall.org/) ) as that seems to be exactly what most people need but I don't trust random binary installers on the 'net offering exactly the kind of thing Ubuntu needs...

So basically you are mad at Ubuntu because of the way you configured it and you somehow think some kind of a firewall application would have helped.

Basically the "rogue apps" are exactly those you configured yourself.

Considering you would have allowed such traffic in the first place I do not see how you can come to that conclusion.

If you are interested, there are ways of monitoring your bandwidth and determining what is using your bandwidth.

[http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-linux.html](http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-linux.html)

see also tools such as htop.

---

### Post by cryptotheslow on 2011-08-21
> **brownb2 said:**
> 
<snip>

- I left Prey anti-theft running (which can only be disabled via the website).
- Ubuntu auto updates was enabled.
- I also suspect I had a couple of rogue apps connecting on port 80.

I'm pissed Ubuntu let me do this and if legit apps can connect to the Internet without my (at the time) knowing so can rogue apps and something for tracking these sort of outgoing connections is (still) needed.

</snip>

:confused::confused::confused: What??

Ubuntu should magically spot that you have travelled abroad and are using expensive bandwidth, then automagically reconfigure itself not to update, automagically log into your Prey account and disable that and automagically disable those rogue apps?

:confused::confused::confused: What???? Seriously you are joking right?

How about taking some responsibility for yourself?

---

### Post by CandidMan on 2011-08-21
> **brownb2 said:**
> if legit apps can connect to the Internet without my (at the time) knowing so can rogue apps
I'm not sure this follows. Unless your rogue apps and legit apps are one and the same. You could try using wireshark to see what's being sent and netstat to see what's sending the data. 
Some culprits that spring to mind are the weather applet and ubuntuone.

---

### Post by brownb2 on 2011-08-23
> **cryptotheslow said:**
> 
:confused::confused::confused: What???? Seriously you are joking right?

How about taking some responsibility for yourself?

This is exactly the negative sort of comment/troll that plagues the linux community, do us a favour mate.

Users cannot possibly be expected to keep track of each app individually and if you read the title of this thread you'd understand that a central point, the firewall, one that used to work, is an ideal place to block these types of connections on a per app basis. Previously my "taking some responsibility" was assuming (g)ufw was up to the job and I would be prompted for outgoing connections ala Sunbelt Firewall et al.

With respect to the other posters, I really don't want to do network analysis on a netbook on holiday especially when I see in Windows I can just disable outgoing connections for everything but Thunderbird and Firefox. How easy is this with ufw/ipchains (and if it is easy, if it's command line based, again it's not suitable unless you're a developer/techie - which I am, BUT it's not something I can recommend to others)?

Related, the linux-firewall.org owner never responded to requests for source code so I'm making the assumption that it's unstable and/or unsecure (in all senses).

---

### Post by bodhi.zazen on 2011-08-23
> **brownb2 said:**
> This is exactly the negative sort of comment/troll that plagues the linux community, do us a favour mate.

Users cannot possibly be expected to keep track of each app individually and if you read the title of this thread you'd understand that a central point, the firewall, one that used to work, is an ideal place to block these types of connections on a per app basis. Previously my "taking some responsibility" was assuming (g)ufw was up to the job and I would be prompted for outgoing connections ala Sunbelt Firewall et al.

With respect to the other posters, I really don't want to do network analysis on a netbook on holiday especially when I see in Windows I can just disable outgoing connections for everything but Thunderbird and Firefox. How easy is this with ufw/ipchains (and if it is easy, if it's command line based, again it's not suitable unless you're a developer/techie - which I am, BUT it's not something I can recommend to others)?

Related, the linux-firewall.org owner never responded to requests for source code so I'm making the assumption that it's unstable and/or unsecure (in all senses).

If the default settings on Ubuntu caused the problem then it would be Ubuntu's fault.

But in this case the user specifically configured Ubuntu to use a higher then the default bandwidth, but then blamed Ubuntu for the increased bandwidth.

So yes, this is an example where the user is indeed at fault.

---

### Post by scruffyeagle on 2011-08-25
I just finished carefully reading every single post in this thread, and have a couple of things to say:

*) Using the term "Windows mindset" or repeating "this isn't Windows" is a cop out - a way of avoiding discussing the details, by lumping dissenting voices into a generic stereotyping.

*) Phone home software in drivers IS an issue, and it's unavoidable. It has absolutely no connection with questions re. repositories vs. other sources. It's the consequence of equipment manufacturers working hard to dig deeper into the pockets of their customers, and working hard to leverage their sales/transactions into further profit regardless of the ethics of their methods. Use of those drivers is a necessity; the equipment is designed from scratch to insist on it. This problem won't go away just because this is Linux, and the time-honored traditional methods & tools in Linux are insufficient to obstructing this new threat to privacy. Therefore, new tools & methods are required.

Based on what I've read in this thread, process #'s are insufficient for this task, as are port #'s. The problem in limiting outgoing connections on a per-application basis, is that the Linux environment doesn't maintain a comprehensive table of program I.D. #'s. (Please correct me, if I'm wrong about that.) In the absence of a comprehensive table of program I.D. #'s, it's not possible to maintain a table of which programs own which current connections - or, to block programs from making connections. Such a table of program I.D. #'s would have to be updated & maintained during every instance of program installation, including assigning separate I.D. #'s for each & every driver. Given such a table to reference, it would be easy to implement per-program internet access privileges. The registration table would have 3 columns: Text of program name, numeric program I.D. # assigned at installation time, and numeric value indicating privileges.

If such a table existed, then establishing a connection could be allowed or refused based on the value of the privileges info in the table. A request for an outgoing connection would require the requesting program to provide a valid I.D. #. Administrators would be able to review &/or edit the privileges in the table on an as-needed basis. A session log would be maintained of programs owning current outgoing connections, with start & end times. The drawback to this framework, is the possibility of programs accessing the table's values for the purpose of spoofing I.D. #'s & associated privileges. I'm not proposing that this would be a replacement for IPtables - it would be an associated accesory, plugging a gap in the security measures.

I don't know the details of operation, re. TuxGuardian, so I don't know if it does what I've proposed here. All I'm really sure of, is that software to do what I've written in the previous 2 paragraphs is needed.

But, please don't tell me that if I want such a feature in the OS then I should write it myself. My programming activities were limited to BASIC - however, my experience in flowcharting, principles of program design, and complex systems analysis are still valid & useful. Of course, if you think it would be right & proper for the entire Linux community to wait until I somehow manage to master writing software in a new language like C++ or Python...?

To sum up: A new problem exists, and traditional methods are insufficient for dealing with it. A method for controlling this problem exists - all that's required is for the community of Linux developers to recognize & acknowledge the problem, then create software that applies the remedy.

---

### Post by bodhi.zazen on 2011-08-25
If you find a driver that "phones home" in the Ubuntu repositories then please show it to us and file a bug report.

Otherwise , do not install 3rd party software. If you are concerned about such third party hardware, do not buy it.

There are several vendors that sell computers with Linux pre-installed:

[http://linuxpreloaded.com/](http://linuxpreloaded.com/)

[https://wiki.ubuntu.com/UbuntuFriendlyHardwareSuppliers](https://wiki.ubuntu.com/UbuntuFriendlyHardwareSuppliers)

[http://www.ubuntu.com/partners](http://www.ubuntu.com/partners)

There is no security model that can protect you when you are going to install third party, closed source applications or driver(s). You run the installer as root and it has full access to your system, including the ability to deactivate any "application based firewall" you might write or install.

You complain about the "windows mentality" , although you have little or no experience with Linux or linux security. This is the problem. The first step is for you to understand how linux works, then how linux security is designed.

Rather then bothering to take the time to understand how Linux works, you come in here demanding some feature of the developers. Such an attitude does not go far here on the forums, and even less with developers.

Because you do not understand Linux, you come across as making unreasonable demands, and people (developers) loose interest in listening to such demands very, very, very fast.

If you want an insight to how developers think read:

[http://www.redhat.com/magazine/020jun06/features/bugzilla/](http://www.redhat.com/magazine/020jun06/features/bugzilla/)

sure it is red hat, but you get the idea.

[http://www.chiark.greenend.org.uk/~sgtatham/bugs.html](http://www.chiark.greenend.org.uk/~sgtatham/bugs.html)

If you file a bug report about a third party driver, such as nvidia, "phoning home" with any major Linux project, Ubuntu, Debian, Fedora, etc, it will be marked as invalid, and rightly so.

---

### Post by Dangertux on 2011-08-25
> **scruffyeagle said:**
> I just finished carefully reading every single post in this thread, and have a couple of things to say:

*) Using the term "Windows mindset" or repeating "this isn't Windows" is a cop out - a way of avoiding discussing the details, by lumping dissenting voices into a generic stereotyping.

*) Phone home software in drivers IS an issue, and it's unavoidable. It has absolutely no connection with questions re. repositories vs. other sources. It's the consequence of equipment manufacturers working hard to dig deeper into the pockets of their customers, and working hard to leverage their sales/transactions into further profit regardless of the ethics of their methods. Use of those drivers is a necessity; the equipment is designed from scratch to insist on it. This problem won't go away just because this is Linux, and the time-honored traditional methods & tools in Linux are insufficient to obstructing this new threat to privacy. Therefore, new tools & methods are required.

Based on what I've read in this thread, process #'s are insufficient for this task, as are port #'s. The problem in limiting outgoing connections on a per-application basis, is that the Linux environment doesn't maintain a comprehensive table of program I.D. #'s. (Please correct me, if I'm wrong about that.) In the absence of a comprehensive table of program I.D. #'s, it's not possible to maintain a table of which programs own which current connections - or, to block programs from making connections. Such a table of program I.D. #'s would have to be updated & maintained during every instance of program installation, including assigning separate I.D. #'s for each & every driver. Given such a table to reference, it would be easy to implement per-program internet access privileges. The registration table would have 3 columns: Text of program name, numeric program I.D. # assigned at installation time, and numeric value indicating privileges.

If such a table existed, then establishing a connection could be allowed or refused based on the value of the privileges info in the table. A request for an outgoing connection would require the requesting program to provide a valid I.D. #. Administrators would be able to review &/or edit the privileges in the table on an as-needed basis. A session log would be maintained of programs owning current outgoing connections, with start & end times. The drawback to this framework, is the possibility of programs accessing the table's values for the purpose of spoofing I.D. #'s & associated privileges. I'm not proposing that this would be a replacement for IPtables - it would be an associated accesory, plugging a gap in the security measures.

I don't know the details of operation, re. TuxGuardian, so I don't know if it does what I've proposed here. All I'm really sure of, is that software to do what I've written in the previous 2 paragraphs is needed.

But, please don't tell me that if I want such a feature in the OS then I should write it myself. My programming activities were limited to BASIC - however, my experience in flowcharting, principles of program design, and complex systems analysis are still valid & useful. Of course, if you think it would be right & proper for the entire Linux community to wait until I somehow manage to master writing software in a new language like C++ or Python...?

To sum up: A new problem exists, and traditional methods are insufficient for dealing with it. A method for controlling this problem exists - all that's required is for the community of Linux developers to recognize & acknowledge the problem, then create software that applies the remedy.


First iptables is not now nor has it EVER been an application firewall. If you want application based firewalling and containment you need to check out things like SELinux or Apparmor, many applications have their own application (for instance mod-security) for Apache.  

As far as applications becoming a server or creating connections -- there are methods around this without reinventing the wheel. Iptables can and does provide the functionality to prevent this. Granted -- this is not in the default UFW configuration, that does not mean it does not exist. 

For Windows mindset I think that might be the case here : it seems like you are looking for something like Zone Alarm to pop up a warning that something is trying to access the network. While there may be front ends for this, Linux largely assumes you know what you are doing -- and most Linux users find functionality like this inconvenient to say the least. 

When it comes to pid's and connection tracking, again the functionality is there (not in default configuration) , and in my opinion regardless of the platform, and regardless of the method of controlling it application inventories have ALWAYS been a personal responsibility. While creating an application to automate this task might be beneficial to some I doubt it. The reason being, most users who would need something like this are "clickers" they click yes to everything, with the hopes that whatever task they are trying to complete is successful. 

Bottom line , I think there is quite enough of this functionality for users who really want it. While it is there it remains un-intrusive for those who do not wish to deal with an operating system that looks and feels like Windows.

As far as writing your own functionality -- if you want a niche application request filled you may have to pony up and write it for yourself. When writing something like an operating system you have a very wide and diverse range of needs and wants. You can't meet them all. So it's not unreasonable to say if you want something that the majority doesn't want go ahead and learn C and create it.

---

### Post by bubba2 on 2011-08-26
Have a look at my post here:
[http://ubuntuforums.org/showthread.php?t=1789594](http://ubuntuforums.org/showthread.php?t=1789594)

---

### Post by scruffyeagle on 2011-08-27
> **Dangertux said:**
> First iptables is not now nor has it EVER been an application firewall. If you want application based firewalling and containment you need to check out things like SELinux or Apparmor, many applications have their own application (for instance mod-security) for Apache.  

As far as applications becoming a server or creating connections -- there are methods around this without reinventing the wheel. Iptables can and does provide the functionality to prevent this. Granted -- this is not in the default UFW configuration, that does not mean it does not exist. 

For Windows mindset I think that might be the case here : it seems like you are looking for something like Zone Alarm to pop up a warning that something is trying to access the network. While there may be front ends for this, Linux largely assumes you know what you are doing -- and most Linux users find functionality like this inconvenient to say the least. 

When it comes to pid's and connection tracking, again the functionality is there (not in default configuration) , and in my opinion regardless of the platform, and regardless of the method of controlling it application inventories have ALWAYS been a personal responsibility. While creating an application to automate this task might be beneficial to some I doubt it. The reason being, most users who would need something like this are "clickers" they click yes to everything, with the hopes that whatever task they are trying to complete is successful. 

Bottom line , I think there is quite enough of this functionality for users who really want it. While it is there it remains un-intrusive for those who do not wish to deal with an operating system that looks and feels like Windows.

As far as writing your own functionality -- if you want a niche application request filled you may have to pony up and write it for yourself. When writing something like an operating system you have a very wide and diverse range of needs and wants. You can't meet them all. So it's not unreasonable to say if you want something that the majority doesn't want go ahead and learn C and create it.

*) Yes, I'll be checking out SElinux & AppArmor - but that takes time. Dealing with the new problem of secret connections from drivers shouldn't need to wait for a new user to spend 3 months studying before being able to stop those connections.

*) Please elaborate on how iptables can stop outgoing connections from drivers.

*) Yes, ZoneAlarm is the model of what's needed - but, I'm not suggestion a ported app to do that task. Who cares about notifications? Not me. Instead, I'm suggesting an iptables-style utility within Linux to provide an extra layer of security. I have the feeling that many long-time users of Linux bend over backwards to avoid doing anything similar to Windows, as if they think that if Windows does it then it can't be beneficial. That's self-defeating, because being close-minded to good ideas will result in lost opportunity for improvement. There's an old saying: "Emulate success."

*) "Clickers"? My, how condescending and demeaning. Haven't you noticed the many posts in this thread, with people saying they believe this functionality has become necessary, and they wish it existed? Those aren't "clickers". Some of those may not be experts, but as a group those are people who study the OS & programs, and the internet access environment. They aren't lax or lazy.

*) I actually did take a step toward getting back into programming, earlier this evening. I downloaded "Gambas2". Now, I'll need to learn to use it.

---

### Post by cariboo on 2011-08-28
I have to ask some off why are you using Ubuntu? What was it that made you start using it?

If it was because of problems you had with Windows,  did you ever think that it may be the reliance on tools that do things automatically for you?

I use a Linux variant for the freedom it gives me to do what I want with my system, without having to rely on tools that don't work that well in the Windows world.

---

### Post by scruffyeagle on 2011-08-29
> **cariboo907 said:**
> I have to ask some off why are you using Ubuntu? What was it that made you start using it?

If it was because of problems you had with Windows,  did you ever think that it may be the reliance on tools that do things automatically for you?

I use a Linux variant for the freedom it gives me to do what I want with my system, without having to rely on tools that don't work that well in the Windows world.

I can't answer for other people, but I can tell you why I've spent the last 2 months trying to master Linux in general, and Ubuntu in particular:

*) The 3 primary options for personal computing are
   a) Microsoft Windows,
   b) Apple comuters & OS's, and
   c) Linux

Microsoft Windows has been defective from the start. I've read how Gates was selling Windows at a trade fair before even a single line of code was written; that, all he had was a graphical shell program illustrating what the OS would do when created. It was rushed to market to meet the delivery deadlines, and they've been trying to compensate for its shortcomings ever since. The one thing they do most expertly, is digging into the public's pockets and extracting money. If I was wealthy, I could afford to go along with it indefinitely, purchasing the "Pro" versions of each new OS... But, I'm poor, so that's a unfavorable option for me.

Apple Computers are (I'm told) excellent machines w/ excellent OS's - but, as a general rule, higher quality comes at a premium price. And, price was very much an issue for me.

I've been increasingly aware of how much extra cost was being added to my electric bill by using my old Dell tower machine w/ old tube monitor as vs. using a laptop w/ LED or LCD display. I decided that although I couldn't really afford a new machine, the savings of a more energy efficient computer would eventually pay for itself. It took a while to find a deal I could cover the cost of, but I managed to purchase a used laptop w/o OS recently. Now that I had a more energy efficient machine, I had to obtain & install an OS - and what choices did I have for getting it running? I decided to buckle down, and invest the time & effort to learn the free OS, Linux. I'd been researching and reading about the various types of Linux, and settled on Ubuntu as the best option for a beginner like myself.

Now, I've made the plunge. I've invested money into a machine that needed Ubuntu. I've invested a huge amount of time & effort during the past couple of months, learning about Linux in general, and Ubuntu in particular. Linux is and always has been a community endeavor. And, this community is where I now find myself. Here is where I've arrived, and the best paths for how to proceed are all within the environment of Ubuntu. So I'm doing my best to become an upstanding member of this community, learning all I can from the people I meet who know more than me, sharing what I've learned with those I might be able to help, and doing my best to contribute in a beneficial manner toward the improvement of Ubuntu.

With that, I've answered your question re. why I'm using Ubuntu.

---

### Post by Laysan_A on 2011-12-05
Hi,

Honestly, I'm a little disappointed at the attitude of the  ubuntu forums staff members, and their complete obstinance regarding  this issue - even to the extent that they WILL NOT allow, in the  remotest sense, that an application based firewall MIGHT be useful for  some people, and in some situations. It makes me wonder if there's an  agenda of some kind at work behind the scenes...

I admit to  feeling pretty secure on my linux box, but I also admit to wishing I had  some application level control over what comes in and goes out of my  machine - even if I never really need to use it. 

I read with interest [LucasAdams  post]("http://ubuntuforums.org/showpost.php?p=10054876&postcount=47") with the link to the brainstorm thread about  [LittleSnitch]("http://brainstorm.ubuntu.com/idea/23333/"), a Mac  firewall applet that appears to look and act just like a windows  application-based firewall. It seems to me if apple can do it, so can  linux. 

AppArmour is a great program, but it's hopelessly  complex. What I, and the others here, are looking for is something that  doesn't require an hour of coding, or memorization of a syntax in order  to block or allow anything we want, at any time we want, in a few  seconds - especially if we don't know what it is ahead of time - while  continuing to go about our normal routine. That's not too much to ask,  is it?

While it's true that most of my software is from the  repositories, I do have some from outside. I consider them to be  "reliable", but you never really know, do you? I would be very surprised  if anyone reading this could say that they have never installed  something from outside. In fact, I would be surprised if most of us here  did not have at least one program installed right now that at least  began life outside the repositories (installed it before it was in  there).

Then there's the problem of zero day vulnerabilities.  These can affect any program - even the kernel. If (when) linux malware  becomes more prevalent, even mousing-over an invisible link on an  otherwise innocuous webpage can begin an infection. Yes, I admit it will  be harder to infect a linux box, and even more difficult to affect  anything beyond the user's own files and folders, but not impossible. 

Application-based  firewalls appear to me to have one big advantage over port-based ones,  and that is the ability to monitor and affect what goes in and comes out  (albeit in crude fashion) in real time. They combine the virtues of a  net monitor, with the ability to actually stop the transfer of data with  a click of the mouse. That may not seem important to you, and if it's  not, well, okay. I would like to be able to do it.

I admit to  being pretty much in the dark when it comes to the experience of a  malware attack on a linux system. I have no idea what one would be like.  I have heard of people's home folders being trashed. Linux systems are  very secure, but they do get hacked on occasion - a friend's linux  server was hacked a while ago, and they are not invulneralble. Imagine  if someone installed a backdoor to your system, or installed a  keylogger, without your knowledge. Perhaps you might only discover it,  or at least you might first discover it, when it tried to connect to its  master (and a little alert popped-up).

To those who say that  application-based firewalls turn users into "clickers", I would say that  in combination with a port-based configuration, "allowing" everything  would be as secure as a port-based configuration alone. I don't see the  problem...

You nay-sayers may be right. There likely isn't enough  interest at the developer level to support this right now. Linux is  very safe - especially if you're careful and at least a little bit  educated. But I predict that a time will come when malware for linux  will become more prevalent and at that time an application-based  firewall will finally be developed and maintained. It's not a panacea,  and no one's suggesting it is (in point of fact, it's a pain in the  ***). It's just one more tool for the security conscious person (okay,  the excessively paranoid) to monitor and control their system. It fits  very nicely between the port-based firewall and a packet analyzer.

---

### Post by CharlesA on 2011-12-05
> **Laysan_A said:**
> Hi,

Honestly, I'm a little disappointed at the attitude of the  ubuntu forums staff members, and their complete obstinance regarding  this issue - even to the extent that they WILL NOT allow, in the  remotest sense, that an application based firewall MIGHT be useful for  some people, and in some situations. It makes me wonder if there's an  agenda of some kind at work behind the scenes...

Staff members are just volunteers like normal members. What sort of agenda would there be "behind the scenes" ? Keep in mind that there have been security professionals posting in this thread as well.

> I admit to  feeling pretty secure on my linux box, but I also admit to wishing I had  some application level control over what comes in and goes out of my  machine - even if I never really need to use it. 

Why not just configure a default outbound policy to deny all and then only allow traffic you want? [A firewall isn't really a "catch-all"]("http://dangertux.wordpress.com/2011/10/03/a-firewall-is-not-a-catch-all/") but you can strengthen it with strong outbound rules.

> AppArmour is a great program, but it's hopelessly  complex. What I, and the others here, are looking for is something that  doesn't require an hour of coding, or memorization of a syntax in order  to block or allow anything we want, at any time we want, in a few  seconds - especially if we don't know what it is ahead of time - while  continuing to go about our normal routine. That's not too much to ask,  is it?

The thing about AppArmour is that you need to tailor each profile to your needs. There is no "end all, be all" profile to something like firefox since everyone's needs are different. There are quite a few howto's on it around the forum. It might be a pain in the butt when you first start, but once you have the profiles that are suitable to you, then you are golden.

> While it's true that most of my software is from the  repositories, I do have some from outside. I consider them to be  "reliable", but you never really know, do you? I would be very surprised  if anyone reading this could say that they have never installed  something from outside. In fact, I would be surprised if most of us here  did not have at least one program installed right now that at least  began life outside the repositories (installed it before it was in  there).

Security involves different levels of trust. I don't trust a random website as much as I would trust a known website.

If you trust something enough to install it, then you potentially open yourself up to security issues, if any are discovered (and patched). If you don't trust an application, then don't install it. I stick to the repos as much as I can but for some things (RAID card) I need to compile a third-party driver, which I get from the manufacturer's site. Could that be used in an exploit? Maybe, but to what benefit?

> Then there's the problem of zero day vulnerabilities.  These can affect any program - even the kernel. If (when) linux malware  becomes more prevalent, even mousing-over an invisible link on an  otherwise innocuous webpage can begin an infection. Yes, I admit it will  be harder to infect a linux box, and even more difficult to affect  anything beyond the user's own files and folders, but not impossible.

The only way I can see getting an "infection" by mousing over a link is to have a malicious script run on mouseover which pokes a hole in your defenses. That would not happen if you are running something like Apparmour or NoScript (preferably both). 

> Application-based  firewalls appear to me to have one big advantage over port-based ones,  and that is the ability to monitor and affect what goes in and comes out  (albeit in crude fashion) in real time. They combine the virtues of a  net monitor, with the ability to actually stop the transfer of data with  a click of the mouse. That may not seem important to you, and if it's  not, well, okay. I would like to be able to do it.

That is still the bit of "Windows" mentality. If you do not install dubious programs, you wouldn't have to worry if something has compromised your box. The number one thing that causes machines to be cracked is SSH and VNC, both of which are disabled on the default install of Ubuntu. What would an application level firewall do for a program that is running as a daemon (service) ?

> I admit to  being pretty much in the dark when it comes to the experience of a  malware attack on a linux system. I have no idea what one would be like.  I have heard of people's home folders being trashed. Linux systems are  very secure, but they do get hacked on occasion - a friend's linux  server was hacked a while ago, and they are not invulneralble. Imagine  if someone installed a backdoor to your system, or installed a  keylogger, without your knowledge. Perhaps you might only discover it,  or at least you might first discover it, when it tried to connect to its  master (and a little alert popped-up).

A good user checks log files every now and then for suspicious activity. If someone got into your box without you knowing it, it would be hard to tell if it was accessed since the attacker would more likely then not sanitize any evidence they were there by wiping log files and whatnot.

> 
You nay-sayers may be right. There likely isn't enough  interest at the developer level to support this right now. Linux is  very safe - especially if you're careful and at least a little bit  educated. But I predict that a time will come when malware for linux  will become more prevalent and at that time an application-based  firewall will finally be developed and maintained. It's not a panacea,  and no one's suggesting it is (in point of fact, it's a pain in the  ***). It's just one more tool for the security conscious person (okay,  the excessively paranoid) to monitor and control their system. It fits  very nicely between the port-based firewall and a packet analyzer.

An application based firewall won't protect you from malware. That is still the Windows mindset. Linux has Apparmor/SELinux, iptables/netfilter built into the kernel among other things to keep you safe.

Have a read on the thread [here]("http://ubuntuforums.org/showthread.php?t=1873643") and the wiki page (which is based on that thread) [here]("https://wiki.ubuntu.com/BasicSecurity").

---

### Post by Dangertux on 2011-12-05
> 

Honestly, I'm a little disappointed at the attitude of the  ubuntu forums staff members, and their complete obstinance regarding  this issue - even to the extent that they WILL NOT allow, in the  remotest sense, that an application based firewall MIGHT be useful for  some people, and in some situations. It makes me wonder if there's an  agenda of some kind at work behind the scenes...


As Charles said , this is silly.

> 
I admit to  feeling pretty secure on my linux box, but I also admit to wishing I had  some application level control over what comes in and goes out of my  machine - even if I never really need to use it


You have a ton of options for this -- we'll get into that in a moment... 

> 
I read with interest [LucasAdams  post]("http://ubuntuforums.org/showpost.php?p=10054876&postcount=47") with the link to the brainstorm thread about  [LittleSnitch]("http://brainstorm.ubuntu.com/idea/23333/"), a Mac  firewall applet that appears to look and act just like a windows  application-based firewall. It seems to me if apple can do it, so can  linux.


Linux can do it -- it wouldn't be that hard to make a Python front end for the tools already available to give you the GUI you want. That being said there are essentially two large crowds in the Linux community. The Linux is safe and nothing can hurt us anyway so we do nothing group. Also there is the I've been using Linux since Torvalds dreamed it up and I can edit apparmor profiles using nothing but stream editor crowd. There is a small group in between that realizes they want more but won't get it without embracing the learning curve. 

> 
AppArmour is a great program, but it's hopelessly  complex. What I, and the others here, are looking for is something that  doesn't require an hour of coding, or memorization of a syntax in order  to block or allow anything we want, at any time we want, in a few  seconds - especially if we don't know what it is ahead of time - while  continuing to go about our normal routine. That's not too much to ask,  is it?


Apparmor -- it's a proper noun, a product by Novell, you shouldn't change the spelling to be dialect specific.  Again -- it's not that complicated, and there are MANY pre-made profiles available in repos for you to use. The syntax (though intimidating) is actually pretty easy, maybe a 2 -3 hour learning curve for most intermediate users. 

Is it too much to ask? Maybe... It might be -- I'm going to tell you why. The tools you have available to you give you a LOT of control , more than a silly little GUI. Those silly little GUI's are often ineffective. They sit there, on your desktop giving you a false sense of security, when in reality they are trivial to bypass most of the time. Mandatory Access Controls, are not by any stretch of the imagination trivial to bypass if configured properly.

> 
While it's true that most of my software is from the  repositories, I do have some from outside. I consider them to be  "reliable", but you never really know, do you? I would be very surprised  if anyone reading this could say that they have never installed  something from outside. In fact, I would be surprised if most of us here  did not have at least one program installed right now that at least  began life outside the repositories (installed it before it was in  there).


Neither is reliable beyond a shadow of a doubt -- what is your point?

> 
Then there's the problem of zero day vulnerabilities.  These can affect any program - even the kernel. If (when) linux malware  becomes more prevalent, even mousing-over an invisible link on an  otherwise innocuous webpage can begin an infection. Yes, I admit it will  be harder to infect a linux box, and even more difficult to affect  anything beyond the user's own files and folders, but not impossible. 


If you want any sort of mitigation from OH-DAY you're going to need MAC, and even then that's not fool proof. Anything else is a gimmick. Bottom line 99% of the time 0 day will own you and there is nothing you can do about it. By the way, browser based exploits do exist for Linux, though they are not widely in use by malware developers, they are developed much the same way windows browser exploits are. I've demo'ed them multiple times recently. Use something like NoScript (if you want the demo check my blog, no you won't get XSS'ed). Also it's not easier or more difficult to "infect" a Linux box then a Windows box.

> 
Application-based  firewalls appear to me to have one big advantage over port-based ones,  and that is the ability to monitor and affect what goes in and comes out  (albeit in crude fashion) in real time. They combine the virtues of a  net monitor, with the ability to actually stop the transfer of data with  a click of the mouse. That may not seem important to you, and if it's  not, well, okay. I would like to be able to do it.


That's called host based IDS, check the security stickies -- even application based firewalls like the one you linked above aren't doing that, they are simply monitoring connections made by each application. Think netstat+some iptables rules. Also if this were made on Linux it would no doubt use netfilter's conntrack so it wouldn't be in real time.

> 
I admit to  being pretty much in the dark when it comes to the experience of a  malware attack on a linux system. I have no idea what one would be like.  I have heard of people's home folders being trashed. Linux systems are  very secure, but they do get hacked on occasion - a friend's linux  server was hacked a while ago, and they are not invulneralble. Imagine  if someone installed a backdoor to your system, or installed a  keylogger, without your knowledge. Perhaps you might only discover it,  or at least you might first discover it, when it tried to connect to its  master (and a little alert popped-up).


You can hide processes and sockets from applications not running in kernel space, additionally you can hook another application -- so if I were goign to do this and make a return connection you can bet it would look like firefox to port 80 or 53 (how are you going to choose to block that? Exactly you won't).

> 
To those who say that  application-based firewalls turn users into "clickers", I would say that  in combination with a port-based configuration, "allowing" everything  would be as secure as a port-based configuration alone. I don't see the  problem...


Umm no.

> 
You nay-sayers may be right. There likely isn't enough  interest at the developer level to support this right now. Linux is  very safe - especially if you're careful and at least a little bit  educated. But I predict that a time will come when malware for linux  will become more prevalent and at that time an application-based  firewall will finally be developed and maintained. It's not a panacea,  and no one's suggesting it is (in point of fact, it's a pain in the  ***). It's just one more tool for the security conscious person (okay,  the excessively paranoid) to monitor and control their system. It fits  very nicely between the port-based firewall and a packet analyzer.

Again IDS/IPS...It sounds like what you want.

Hope this helps.

---

### Post by bodhi.zazen on 2011-12-05
> **Laysan_A said:**
> Honestly, I'm a little disappointed at the attitude of the  ubuntu forums staff members, and their complete obstinance regarding  this issue - even to the extent that they WILL NOT allow, in the  remotest sense, that an application based firewall MIGHT be useful for  some people, and in some situations.

What the staff, and others, are trying to tell you boils down to 3 issues:

1. It is not as simple as you envision. You might think it is trivial to write some kind of graphical front end to do this, but the technology you envision as an "application firewall" is equally trivial to circumvent.

2. Superior tools already exist. Apparmor, selinux, iptables, snort, wireshark, etc. Yes there is going to be a learning curve, but no more or less then a graphical interface to these tools would offer.

For example, SUSE has a graphical interface for writing apparmor profiles, you still need to understand apparmor before you can write a profile.

This is what it looks like

[img]http://media.techtarget.com/digitalguide/images/Misc/suse_app_armor_2.jpg[/img]

And this is a demo: 

[http://searchenterpriselinux.techtarget.com/tip/Using-SUSE-AppArmor-to-profile-a-workstation-application-in-FireFox](http://searchenterpriselinux.techtarget.com/tip/Using-SUSE-AppArmor-to-profile-a-workstation-application-in-FireFox)

So if you look, you will see that there is a learning curve and customization required even with a graphical interface.

The advantage of apparmor is it is easier to learn then selinux. The disadvantage it requires you to maintain it more then selinux.

I highly suggest you look at Fedora / Selinux. selinux on Fedora is much more mature then apparmor.

I have to disagree with Dangertux on this. I would agree selinux is not perfect, but it has been shown, as has apparmor, to help stop would be zero day exploits.

3. Interest in developing such a tool, buy developers, is low. You will either need to learn to code yourself or learn to communicate with the developers in a way that motivates them to code for you. It is not the responsibility of the forums staff to take your demands to the developers and force them to code for you, neither the forums staff nor the open source community works that way.

Now the staff, and others, may be willing to help you, but your posting style does not motivate me to help you.

---

### Post by Dangertux on 2011-12-05
To clarify I meant the 99% statement to be without MAC -- so you probably do agree with me just not the way I worded it lol.

I would certainly hope mandatory access controls do something in terms of 0 day since that's pretty much the only reason people use them. Though when you start talking about browser exploitation and other client side attack vectors the game changes considerably, as most client side apps need access to whatever is the target in the first place. So 0day still has a good chance of owning you.

---

### Post by bodhi.zazen on 2011-12-05
> **Dangertux said:**
> To clarify I meant the 99% statement to be without MAC -- so you probably do agree with me just not the way I worded it lol.

I would certainly hope mandatory access controls do something in terms of 0 day since that's pretty much the only reason people use them. Though when you start talking about browser exploitation and other client side attack vectors the game changes considerably, as most client side apps need access to whatever is the target in the first place. So 0day still has a good chance of owning you.

Browsers are a problem , take a look at the firefox apparmor profile.

I think the only answer there is to not use them for such diverse activity, I don't.

Convenience and security are often at odds. Sure it is nice for flash to "just work", but not so nice to be pwned by flash.

For an example of what selinux will do for you:

1. I confine all my users with selinux.

2. See [selinux sandbox](http://danwalsh.livejournal.com/28545.html).

[http://blog.bodhizazen.net/linux/selinux-sandbox/](http://blog.bodhizazen.net/linux/selinux-sandbox/)

3. SELinux (and apparmor) can indeed be effective against some zero day exploits

[http://danwalsh.livejournal.com/45194.html](http://danwalsh.livejournal.com/45194.html)

[https://media.blackhat.com/bh-us-11/Elhage/BH_US_11_Elhage_Virtunoid_Slides.pdf](https://media.blackhat.com/bh-us-11/Elhage/BH_US_11_Elhage_Virtunoid_Slides.pdf)

But not all, for example, the recent BIND exploit. 

[http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2011-4313](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2011-4313)

I do not think MAC (selinux or apparmor) would help with that ^^

---

### Post by Dangertux on 2011-12-05
> **bodhi.zazen said:**
> Browsers are a problem , take a look at the firefox apparmor profile.

I think the only answer there is to not use them for such diverse activity, I don't.

Convenience and security are often at odds. Sure it is nice for flash to "just work", but not so nice to be pwned by flash.

For an example of what selinux will do for you:

1. I confine all my users with selinux.

2. See [selinux sandbox]("http://danwalsh.livejournal.com/28545.html").

[http://blog.bodhizazen.net/linux/selinux-sandbox/](http://blog.bodhizazen.net/linux/selinux-sandbox/)

3. SELinux (and apparmor) can indeed be effective against some zero day exploits

[http://danwalsh.livejournal.com/45194.html](http://danwalsh.livejournal.com/45194.html)

[https://media.blackhat.com/bh-us-11/Elhage/BH_US_11_Elhage_Virtunoid_Slides.pdf](https://media.blackhat.com/bh-us-11/Elhage/BH_US_11_Elhage_Virtunoid_Slides.pdf)

But not all, for example, the recent BIND exploit. 

[http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2011-4313](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2011-4313)

I do not think MAC (selinux or apparmor) would help with that ^^

No the Bind issue it wouldn't help with as it's exploiting functionality of the named service itself, which would have to be permitted or named would fail to function.

SELinux sandbox...have it on fedora want it on Ubuntu -- the python sandbox app will not work until debian upstream fixes se-tools DESPERATELY WANT!!! I think it would be a nice thing to have in the event of these "how to sandbox" an app discussions, SELinux makes it MUCH easier than Apparmor.

---

