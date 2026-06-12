---
title: "New to Ubuntu: appalled to find I had to active the firewall"
date: 2017-09-01
forum: Security
---

### Post by ju.pa on 2017-09-01
I took the plunge and migrated from Windows 7 to Ubuntu. I love it.

Although I was appalled to find I had to manually active the firewall via:

```
sudo ufw enable
```

This then raised the question "how do I access the firewall via a GUI?"

Turns out I need to install the firewall GUI via

```
sudo apt-get install gufw
```

As I'm new to Linux perhaps I'm being naive, my questions are:
[LIST=1]
[*]Why isn't the firewall activated by default?
[*]Why isn't the firewall GUI preinstalled?
[/LIST]

Thanks

---

### Post by TheFu on 2017-09-01
First, Linux isn't Windows.  They are very different OSes with different core philosophies.  There are many, many, many things that are different.  Some Linux distros do install and enable a firewall, BTW.

Also, the Linux firewall is part of the kernel, so any program you use to interface with it is completely your choice.  gufw, ufw, iptables, ipset, and there are others.  Each has a dedicated group of maintainers who love THEIR specific interface.

Why doesn't Ubuntu enable the firewall by default?  Because it isn't needed.  By default, there aren't any services listening on an ubuntu server or desktop.  **When we install a service, it is our responsibility to enable and configure the firewall AND other protection methods**.   Most end-users of Ubuntu would never need the firewall.

Depending on the service/daemon installed, it might include protections already.  Many have implemented something like **tcp-wrappers** in their code. This can be used to limit from which subnets any access to a service is allowed.  Samba, ssh/sftp/scp, CUPs all have this support.

Ubuntu isn't just about the GUI.  There are versions that have no GUI, so that is why ufw is installed by default.  I use a mix of ufw and tcp-wrappers and something called fail2ban on my systems.  Fail2ban watches for failed logins and when a limit is seen, dynamically blocks that IP.  This is helpful for services that you don't want to limit by subnet, but don't want to let someone hack on the passwords forever.

BTW, this is a great question.  If you **review the "sticky threads" in the *Security* subforum here**, you'll learn about some other tools and differences.

[http://blog.jdpfu.com/2017/03/31/learning-linux-condensed](http://blog.jdpfu.com/2017/03/31/learning-linux-condensed) has a few links at the top of the article to jump start your Linux learning.

My signature also has some links you might find useful.

---

### Post by ju.pa on 2017-09-01
Thanks for your response.

I recognise your argument, but I fear you are responding from a Ubuntu Linux POV and not a general end user POV.

I have not used Linux too much previously. But I do a little bit of scientific programming (FORTRAN, Matlab etc) - I've developed the mindset of being able to try new codes and software even if I am unfamiliar with them. Therefore for me to enable the firewall was not a problem as I am not too scared of the terminal.

Now from the POV of the average person who just wants to run their computer trouble free and has no idea what the Linux terminal is, they will likely be coming from a Windows environment (as I did). One of the first questions they will ask when they setup their computer is "how do I protect it from viruses" even though they aren't that common in Linux systems. Therefore it seems to me that an "obvious win" would be to enable ufw (or otherwise) by default for people who don't know what they are doing. For people who do know what they are doing they can easily disable it.

---

### Post by TheFu on 2017-09-01
But it isn't needed at all.  THAT is kinda the point.  Running things that AREN'T needed is how something so bloated as Windows happens.  Linux/Unix has a different philosophy.  That is why Linux runs on $5 computers or $1B super computers.

Out of the box, Windows comes with about 10 services enabled. It **NEEEEEEEEEEDS** a firewall enabled.  They actually should have an outbound firewall enabled too, BTW, IMHO. This is based on risk factors.  Linux desktop systems don't have the same level of risks as Windows does, at least not yet.  

Android/iOS are different questions completely. People aren't paranoid about their tablets and smartphones nearly enough. Ignorance is bliss, it seems. I digress.

Linux isn't for everyone. Ubuntu isn't for everyone.   If you want a Linux distro that enables a firewall by default, use Fedora.  There are others.

[https://ubuntuforums.org/showthread.php?t=1871177](https://ubuntuforums.org/showthread.php?t=1871177) is the sticky thread in the security subforum that I referenced above concerning firewalls and Linux.

Did you already research whether you need AV too?  
See the Security sub-forum for that common question/answer too.

---

### Post by Autodave on 2017-09-01
I have 13 computers running Linux. I am the ONLY one that knows the password for each of them, and that is the only security that I use or need. 2 of the machines are in the open where anyone of the congregation (about 480 members) can get to them. I have never enabled the firewall on any of them. I have never had an issue with any of them.

---

### Post by Bucky Ball on 2017-09-01
You might find some [interesting reading here]("http://linux.oneandoneis2.org/LNW.htm") re. security in Linux/Windows and lots of other things. ;)

---

### Post by 1clue on 2017-09-01
> **ju.pa said:**
> Thanks for your response.

I recognise your argument, but I fear you are responding from a Ubuntu Linux POV and not a general end user POV.


The security paradigm on Linux is different from what it is on Windows.

I just googled "ubuntu security" and the first three links I got are all pertinent to your questions, and I think that every Ubuntu user should read them.

The first thing you need to know is that the people who say "you don't need to do anything" are wrong.

To be honest, if you JUST load Ubuntu and use it from home or your work, and JUST use it for email and web browsing to family-safe sites, AND you understand how to recognize phishing attacks and other browser/email-related security threats, then chances are you could do nothing and go for years without a problem.

The truth is though, that there is no operating system in existence which is secure even when used by an ignorant, careless user. The end. Security always involves education, and I strongly suspect that many of those who claim to have done nothing for security and been clean for years have in fact been compromised and don't even know it. Most modern malware doesn't trash your system, it uses your system as a platform from which to attack other systems. People who do nothing for security could be infected for years and not know it.

Part of the problem with Windows being so horribly susceptible to malware is the mere presence of antivirus software. People think they can load AV software and they're safe from anything, when nothing could be further from the truth. There is no comprehensive way that software can protect you from some con artist writing you an email and convincing you to give them money. Or your password. Or whatever. If you click the link you may be in for a nasty surprise.

> 
I have not used Linux too much previously. But I do a little bit of scientific programming (FORTRAN, Matlab etc) - I've developed the mindset of being able to try new codes and software even if I am unfamiliar with them. Therefore for me to enable the firewall was not a problem as I am not too scared of the terminal.

Now from the POV of the average person who just wants to run their computer trouble free and has no idea what the Linux terminal is, they will likely be coming from a Windows environment (as I did). One of the first questions they will ask when they setup their computer is "how do I protect it from viruses" even though they aren't that common in Linux systems. Therefore it seems to me that an "obvious win" would be to enable ufw (or otherwise) by default for people who don't know what they are doing. For people who do know what they are doing they can easily disable it.

I've been using Linux since before there was a reliable GUI, and a UNIX user from before that. At that point the GUI was a lot of work for some unreliable results, sometimes bizarre and always frustrating. So I'm a bit old school with respect to tools. I'm pretty sure it's been at least a decade since I even saw a GUI firewall tool on Linux, and it wasn't too impressive back then. While you may not be interested, there is absolutely nothing pertaining to security on Linux which requires a GUI tool. I also have become used to the fact that in Linux many times the GUI tool for some package only has the most commonly used features, not the whole set of functionality provided by the package.

As was mentioned before, the firewall in Linux is in the kernel. Any user interface from the command line to the gui will be a wrapper around the same exact core functionality.

Also keep in mind that the firewall is only one thing that people should understand about Linux security. The three links from google are a good place to start.

---

### Post by 1clue on 2017-09-01
For the sake of completeness, the three links I just mentioned, in the order I would recommend reading them, are here:

[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

BasicSecurity is a wiki explaining how security matters in Ubuntu, and how to make your system more secure.

[https://help.ubuntu.com/lts/serverguide/security.html](https://help.ubuntu.com/lts/serverguide/security.html)

The security server guide covers some of the same ground but with a focus on the tools provided rather than conceptual instruction.

[https://usn.ubuntu.com/usn/](https://usn.ubuntu.com/usn/)

USN is Ubuntu Security Notices, and understanding things about this site is core to actually being secure on Ubuntu, or Linux in general.

Linux is a kernel plus a bunch of other software, most of which runs on non-Linux operating systems like freebsd, or some even runs on mac os or windows. In the Open Source world, you have various communities working on their own specific piece of software. Some of that software depends on other software. You're probably familiar with a dependency graph, the one for FOSS (free/open source software) looks a lot like a tree.

A Linux distribution like Ubuntu collects all the software they want to support and they build it into a working system. They make rules for how they want to handle upgrades, who they accept work from, how they handle testing, whatever. Ubuntu, for example, will choose a moment in time for a release and then will snapshot all versions of software they will use for that.  From that point forward they will only accept security/relibility-related patches to those packages, not new features. 

So you have all these communities making software. They add features and fix bugs, and they release updates and sometimes patches. You also have users using the software, and you have some organizations testing specifically for security issues. And you have black hat hackers who are trying to penetrate your system for fun and profit. Any one of these groups, or others not mentioned, can discover a vulnerability. That vulnerability may be ignored or reported, or investigated further by the entity which discovered it.

The white hats (people who work toward securing Linux and software in general, for the good of the public, whether paid or not) will report the bug to some responsible entity, which could be the distribution maintainers, the upstream developers or some sort of computer vulnerability organization.

There are several organizations which maintain computer vulnerability databases for various operating systems. These databases are run by organizations (or the government) intent on maintaining safe, stable computing environments. Package maintainers and software developers will likely be watching these databases, and when something comes in they try to fix it. Generally speaking, if a serious threat becomes known any of the white hats will try to get a private warning to the package maintainers before the bug becomes public.

One of the tasks of Linux distribution maintainers is to apply security patches to their software, both the online software libraries and running systems out in public. They (the maintainers of the distribution) will have a list of packages by version and a list of supported releases of their distribution, and will have a status of each version of each package per release of Linux.  For example [http://people.canonical.com/~ubuntu-security/cve/main.html](http://people.canonical.com/~ubuntu-security/cve/main.html)


Have your eyes glazed over yet?

Here are the key things to understand:
[LIST=1]
[*]Bugs and vulnerabilities exist when the software was initially written.
[*]There is a possibly long time between the release of the software and the discovery of the bug.
[*]There is a span of time between the discovery and the notification of someone who can or will do something about it.
[*]There is a span of time between the above notification and when the vulnerability is fixed.
[*]There is a span of time between when it's fixed and when it's released/announced to the world.
[*]There is a span of time between the package maintainer's announcement and your distro maintainer's merging that change into the repository.
[*]There is a span of time between the merge into the repository and your system getting the update.
[*]During that time, a black hat could have discovered the bug/vulnerability and created an exploit, and used it on you.
[/LIST]

People who insist that keeping your system up to date will keep you secure are wrong. Keeping your system up to date will make you MORE secure, but nothing you can do will supply any degree of certainty that your system will remain free of malware.

Your head is the best security tool you can use.

---

### Post by DuckHook on 2017-09-01
Thread moved to security forum.

@OP

I would strongly recommend reading the stickies at the start of this security forum. The security link in my sig is also helpful.

---

### Post by HermanAB on 2017-09-02
A firewall is mostly a Windows thing.  You need one when you cannot control all the services running on your computer properly.

A default Linux install doesn't need a firewall program.  Relax and enjoy your new computer system.

---

### Post by The Cog on 2017-09-02
> **TheFu said:**
> Why doesn't Ubuntu enable the firewall by default?  Because it isn't needed.  By default, there aren't any services listening on an ubuntu server or desktop.  **When we install a service, it is our responsibility to enable and configure the firewall AND other protection methods**
Until recently, I would have argued the same. But looky here:
```
steve@StevesLappy:~$ sudo netstat -lntp
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name    
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      948/sshd            
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      2123/cupsd          
tcp        0      0 0.0.0.0:5355            0.0.0.0:*               LISTEN      949/systemd-resolve 
tcp6       0      0 :::22                   :::*                    LISTEN      948/sshd            
tcp6       0      0 ::1:631                 :::*                    LISTEN      2123/cupsd          
tcp6       0      0 :::5355                 :::*                    LISTEN      949/systemd-resolve 

```
SSHD - yes I installed that. Along with that action comes a need to consider security (public key login or firewall or both).
cupsd - yes, I installed that. And it's only listening locally (loopback interface) anyway so firewall not needed.
systemd-resolved - **Who ordered THAT????** Not me! There's a service that I didn't install, wasn't warned about, and is listening for incoming connections from anywhere doing who-knows-what. It looks like systemd is busy making Linux so like windows that we now need a firewall even if we don't choose to install any services ourselves. When did that happen? 

A google search says it provides a lookup for **local** applications. So why the hell is it providing a public service to the whole **world**??? ju.pa was appalled to find that a firewall was not enabled by default. I am appalled to find that one might now be needed by default.

---

### Post by TheFu on 2017-09-02
I looked on a 16.04 desktop box (openbox is the GUI).  No Unity.
```
$ sudo netstat -lntp
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 192.168.122.1:53        0.0.0.0:*               LISTEN      2667/dnsmasq    
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      2249/sshd       
tcp        0      0 0.0.0.0:46551           0.0.0.0:*               LISTEN      2701/rpc.statd  
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN      2484/master     
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN      2703/rpcbind
```

ssh is the only service generally available. fail2ban protects it when it isn't on my LAN, behind the router.
NFS has tcp-wrappers to only allow my NFS servers.
dnsmasq is for VMs only.

Guess the point is, be careful which Ubuntu version you install?

---

### Post by ChuangTzu on 2017-09-02
UFW is good to enable in case you install something that opens a port before you can tell it not to.  sometimes services are started automatically before being configured its a Debian/Ubuntu thing.  

a good default setting for most users:
```
sudo ufw enable
sudo ufw default deny
sudo ufw deny ssh (unless you need ssh of course)
```

---

### Post by The Cog on 2017-09-03
I'm using Xubuntu 17.04. When I get time I'll try some other flavours and see what they do. I'm pretty sure Xubuntu 16.10 didn't have this problem though.
Edit:
According to some other postings I have seen while reading about systemd-resolved, it seems that this was introduced in Ubuntu 16.10.

---

