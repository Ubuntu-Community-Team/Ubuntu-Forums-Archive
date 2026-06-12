---
title: "I need an outbound GUI software firewall"
date: 2011-02-27
forum: Security
---

### Post by opendoors on 2011-02-27
By "outbound", I mean I need to be able to control which programs are allowed to access the Internet; that is, connect to some remote server from my computer. I'm not very experienced at Ubuntu, but all of the firewalls I've looked at for Ubuntu so far only allow me to control incoming connections. A router would be able to do the same thing.

Is there any such firewall for Ubuntu? I would prefer one that is friendly to newbies, but this isn't required as long as it's GUI instead of command line.

---

### Post by cariboo on 2011-02-27
There is no need to block outbound connections, as there aren't any until you the user initiate them. I'd suggest you spend more time getting familiar with Ubuntu, instead of trying to use Windows solutions for problems that don't exist.

To check what outbound connections you have running, open a terminal and type::

```
sudo lsof -i -P -n
```

---

### Post by opendoors on 2011-02-28
> **cariboo907 said:**
> There is no need to block outbound connections, as there aren't any until you the user initiate them. I'd suggest you spend more time getting familiar with Ubuntu, instead of trying to use Windows solutions for problems that don't exist.

To check what outbound connections you have running, open a terminal and type::

```
sudo lsof -i -P -n
```

I can't be checking what outbound connections I have running 24/7. I need a blocking solution, not a checking solution. I will be installing software that isn't from the repository out of necessity (e.g. at least some hardware drivers that come packaged with stuff I don't want to use but that I have to). If it is legal to do so, I may also be installing Windows games and playing them using Wine. I don't want these games phoning home. Finally, even if I install software from repositories, I don't want them accessing the Internet all the time. And these are only a few examples. I could go on, but I've seen far too many similar threads devolve into a discussion over necessity, and I don't want the same thing to happen to this one.

I am still looking for a firewall that can block outbound connections.

---

### Post by cariboo on 2011-02-28
Like I said, in my post, there isn't anything making outbound connections until you start the program. Most programs have configuration files, where the ability to connect to the internet is allowed or dis-allowed. It is up to you whether they connect or not, there is now set and forget solution

---

### Post by bodhi.zazen on 2011-02-28
> **opendoors said:**
> I can't be checking what outbound connections I have running 24/7. I need a blocking solution, not a checking solution. I will be installing software that isn't from the repository out of necessity (e.g. at least some hardware drivers that come packaged with stuff I don't want to use but that I have to). If it is legal to do so, I may also be installing Windows games and playing them using Wine. I don't want these games phoning home. Finally, even if I install software from repositories, I don't want them accessing the Internet all the time. And these are only a few examples. I could go on, but I've seen far too many similar threads devolve into a discussion over necessity, and I don't want the same thing to happen to this one.

I am still looking for a firewall that can block outbound connections.

Any firewall can block outbound connections.

What you are asking for is a so called "application firewall" and most of the people who ask for such a thing are people coming from a Windows background.

Basically you have a few options :

1. Use iptables.

```
sudo iptables A OUTPUT -j DROP
```

You can configure iptables with any number of tools from ufw to gufw ;)

2. Turn your computer off when you are not using it.

3. Disconnect from the network when you are not using it.

4. Learn to use apparmor or selinux or grsecurity.

5. Write an application yourself.

---

### Post by opendoors on 2011-02-28
Among iptables, apparmor, selinux, and grsecurity, is there one that alerts me every time an application tries to access the Internet instead of requiring me to know every program that makes such an attempt?

---

### Post by smurphy_it on 2011-02-28
Have you tried "firestarter".  Its gui, and does all of the work in the background with iptables.

[http://www.fs-security.com/](http://www.fs-security.com/)

sudo apt-cache search firestarter
firestarter - gtk program for managing and observing your firewall

---

### Post by scorp123 on 2011-02-28
> **opendoors said:**
> I can't be checking what outbound connections I have running 24/7.  And why should you even need to?? This is not Windows here :)

I use Linux since 1996 and never had any problem with programs doing strange things behind my back :D

Let go of your Windows ways.

---

### Post by bodhi.zazen on 2011-02-28
> **opendoors said:**
> Among iptables, apparmor, selinux, and grsecurity, is there one that alerts me every time an application tries to access the Internet instead of requiring me to know every program that makes such an attempt?

You can monitor your network traffic best with tcpdump or wireshark.

You can also log all packets with snort or iptables.

Apparmor / selinux / grsecurity will all certainly alert you alright =) Of the 3 I would go with Fedora and selinux, nice graphical tools.

But no, if you want to do this, it is an active process and will require time and effort on your part.

---

### Post by opendoors on 2011-02-28
[QUOTE=smurphy_it]Have you tried "firestarter".  Its gui, and does all of the work in the background with iptables.

[http://www.fs-security.com/](http://www.fs-security.com/)

sudo apt-cache search firestarter
firestarter - gtk program for managing and observing your firewall[/QUOTE]

Thanks, firestarter is definitely a good start. If as bodhi.zazen says, I can't be alerted at the moment an application tries to access the Internet, I still would like to do what others have done: deny everything, then whitelist stuff gradually. Firestarter  falls a little short in this respect because:

1. The log doesn't log blocked outbound connection attempts.
2. I can set a restrictive outbound policy (i.e. block everything except allowed connections/services), but I cannot specify an application as a whitelisted item.

I also looked into GUFW because of bodhi.zazen's stickied thread, but it also doesn't let me allow applications instead of ports.

So basically, at this point I'm willing to use any firewall GUI that has a restrictive policy similar to firestarters (blocking everything that isn't whitelisted) and allows me to specify applications as whitelisted items (instead of just ports or destination IPs). All I would need is a log that shows all the blocked outgoing connections so I can decide what to whitelist later. I think such a product should exist because of this: [http://ubuntuforums.org/showpost.php?p=10052438&postcount=38](http://ubuntuforums.org/showpost.php?p=10052438&postcount=38)

What I should try next?

---

### Post by bodhi.zazen on 2011-02-28
> **opendoors said:**
> What I should try next?

Wireshark.

---

### Post by opendoors on 2011-02-28
[QUOTE=bodhi.zazen]Wireshark.[/QUOTE]

What good would Wireshark do? It's not a firewall. I'm looking for a way to block applications from accessing the Internet. I still don't have this important first step. Once I have this, then maybe Wireshark would be of some use determining what's trying to get out.

This looks pretty interesting, but it doesn't seem to be GPL because it says users are not allowed to "copy or modify this software": [http://www.linux-firewall.org/](http://www.linux-firewall.org/)

I'm still looking.

---

### Post by cariboo on 2011-02-28
This is just to let you know that firestarter hasn't been updated since 2005, except for a few bug fixes by the maintainer. Leaving the gui running to monitor connections could also be a security problem, as you have to run it as root.

---

### Post by Jive Turkey on 2011-03-01
There really isn't an interactive GUI program for outbound connections.  AFAIK you could set a ufw or gufw rule to deny and log outbound connections and then if something doesn't work you could check the log.  That would be just silly imho because many outgoing connections are made from random local ports.  You don't really need this functionality in Linux systems.

---

### Post by opendoors on 2011-03-01
I spent quite some time explaining here why I believe at least some application filtering is required: [http://ubuntuforums.org/showthread.php?t=1591340](http://ubuntuforums.org/showthread.php?t=1591340) (see post #65 on page 7)

Filtering by application would solve the problem with ports that you describe, but based on what everyone has said and what I've found by searching on my own, such a product simply doesn't exist in Linux yet (or at the very least is in very early stages of development).

Unfortunately, because of what I have to run, it does mean I'll have to stick with Windows for now. I guess I'll check back in a few years. Thanks for all the replies.

---

### Post by HermanAB on 2011-03-01
Howdy,

"You are not paranoid, if they really are out to get you..."

I can understand where you are coming from, but really, if you are running Linux, then you are running a system with a totally different security model than what you are used to.

Linux doesn't do things behind your back.  Linux doesn't suffer from drive-by downloads.  Linux doesn't have viruses. Linux doesn't install programs without your knowledge and express consent.  A default Linux system is more secure than a Windows system with all the latest and greatest aftermarket security solutions installed.

Yes, it really is secure.

Yes, it really is that simple.

Don't worry, be happy.

So, relax and enjoy your brand new, secure Linux system.

---

### Post by KonfuseKitty on 2011-03-01
I'm with opendoors on this one, the demand for whilisting/blacklisting/per application firewall type software won't go away. I've read all the responses as to why it's not required or even not a good idea and they've failed to convince me. I see it as an issue of simplicity and time saving. A little while ago I discovered that the clock update thingy was connecting to the servers even though I'd turned it off. So clearly, Ubuntu isn't as 100% well-behaved as some like to claim. And instead of going through the rigmarole of how to truly turn the thing off, it would have been so much simpler and faster to devise a rule "nothing but Opera can connect to internet". Then it wouldn't matter one iota what else is trying to connect, and I wouldn't have to spend time learning all about it to deal with it.

---

### Post by HermanAB on 2011-03-01
"I wouldn't have to spend time learning all about it to deal with it."

That is the difference between a Windows and Linux point of view.

In a Windows system, you apply multiple layers of band-aids one atop the other, until the problem eventually mostly goes away, or the machine dies under the strain of trying to figure out what you really want it to do.  

In Linux, you fix the problem and move on to better things.

---

### Post by arapaho on 2011-03-01
I see that this discussion starts all over again. See this:

[http://ubuntuforums.org/showthread.php?t=1591340](http://ubuntuforums.org/showthread.php?t=1591340)

Idea #26902: Give users "global control" over applications' outgoing internet connections
[http://brainstorm.ubuntu.com/idea/26902/](http://brainstorm.ubuntu.com/idea/26902/)

> **HermanAB said:**
> Yes, it really is secure.
It's really a matter of trust to developers than a real security.
Even PPA programs are described as untrusted/trusted not untested/tested.

""Untrusted" means that absolutely anyone can register on Launchpad and create a PPA - i.e. it is up to you to decide how much you trust the owners of the PPA.

The use of PGP keys only enables you to validate that the files you have downloaded were not tampered with outside of the Launchpad systems which control PPA publication.

PPAs are not, in general, officially overseen by Ubuntu team members."
[https://answers.launchpad.net/launchpad/+question/141780](https://answers.launchpad.net/launchpad/+question/141780)

Please, don't tell me again that users should't install software from outside of repository. Sticking only to repository would make this system almost useless.

---

### Post by wdtd on 2011-03-01
If I understand the OP correctly, they would like to be able to approve or deny if an application can access the Internet. 

Since I have seen programs on a variety of operating systems (including smart phones) call home and/or "update" themselves without the owner's permission, :frown: I can understand why this program would be appealing.

:idea: Might one of these approaches work as an stopgap measure?

1) Set your (G)UFW/iptables to default deny all outgoing expect a couple of specific unusual ports and redirect allowed programs to use those ports.

2) Create apparmor profiles or use SELinux to contain and notify you about potential problematic programs. 

3) Run potential problematic programs under a different user to track and control access that way.

4) Use a Virtual Machine to control access.


I am very glad to be using an OS and a distribution where I haven't had to worry about these problems yet.

---

### Post by opendoors on 2011-03-01
[QUOTE=HermanAB]"I wouldn't have to spend time learning all about it to deal with it."

That is the difference between a Windows and Linux point of view.

In a Windows system, you apply multiple layers of band-aids one atop the  other, until the problem eventually mostly goes away, or the machine  dies under the strain of trying to figure out what you really want it to  do.  

In Linux, you fix the problem and move on to better things.[/QUOTE]

I think you may be misinterpreting that statement. I pointed out in the other thread [http://ubuntuforums.org/showthread.php?t=1591340](http://ubuntuforums.org/showthread.php?t=1591340) (post #65 on page 7) that having an application firewall would save time by helping the user discover which programs require Internet access and which ones don't. The user isn't learning any less by doing this. It's just that they save time by not having to do so much trial and error. Wouldn't this be consistent with your philosophy of "fix the problem and move on to better things"? What's wrong with saving some time but still learning the same things? This is not laziness, but efficiency.

As for the idea of layered security that you seem to be describing, it most certainly isn't a purely Windows concept. The machine only dies under the strain if you don't have the right layers.

[QUOTE=wdtd]If I understand the OP correctly, they would like to be able to approve or deny if an application can access the Internet. 
[/QUOTE]

Yes, that's a feature I would need to see in Ubuntu to switch over. I don't think I like Windows any more than a lot of people here do, but given the way I've set it up, I certainly am not suffering from a lack of security or features because I'm not using Linux either. In fact, I would have to do a lot more work initially to get similar functionality on Ubuntu. I don't mind this at all. I simply liked that Linux was open source, but until this feature is taken more seriously, there's no way I can switch. If it simply doesn't exist yet, there's nothing I can do about it except wait a while longer, but a good start would be acknowledging that there is a good reason for such a program.

[QUOTE=wdtd]
Since I have seen programs on a variety of operating systems (including smart phones) call home and/or "update" themselves without the owner's permission, :frown: I can understand why this program would be appealing.

:idea: Might one of these approaches work as an stopgap measure?

1) Set your (G)UFW/iptables to default deny all outgoing expect a couple of specific unusual ports and redirect allowed programs to use those ports.

2) Create apparmor profiles or use SELinux to contain and notify you about potential problematic programs. 

3) Run potential problematic programs under a different user to track and control access that way.

4) Use a Virtual Machine to control access.


I am very glad to be using an OS and a distribution where I haven't had to worry about these problems yet.[/QUOTE]

You have some very interesting approaches. I have to admit I don't fully understand all of them, but I will try. If I misunderstood, please correct me.

I think 1) would work in most cases, but it is still possible that an undesirable application happens to access the Internet through one of those allowed ports. For example, if you only allow port 1234 and redirect all traffic through port 1234, programs that you would rather have no Internet access at all might still happen to connect through port 1234. The chance of this happening isn't very good, but it's certainly possible if you use your computer long enough and have enough things installed.

2) Does SELinux notify me about all connection attempts? I'm not sure how apparmor works, but this might work if I could start out blocking everything and then allow only specific applications based on SELinux's logs. I will need some help setting this up though.

3) I've seen this idea elsewhere, but I don't have the experience to implement it. Someone suggested it here: [http://www.linuxquestions.org/questions/linux-security-4/linux-firewall-with-application-dependant-blocking-of-outgoing-connections-710407/#post3471470](http://www.linuxquestions.org/questions/linux-security-4/linux-firewall-with-application-dependant-blocking-of-outgoing-connections-710407/#post3471470)

If you know how to set this up, please let me know.

4) How would this work?

Thanks

---

### Post by cariboo on 2011-03-01
Personally I think you should install Ubuntu and run it for six months exclusively, then come back and tell us how many malware, crack attempts and other incidents you have experienced.

---

### Post by wdtd on 2011-03-01
I am still learning so not sure but based on what I have seen:

1) The odds of a "phone home" finding several specific ports out of 65535 seems fairly small (but non-zero).

2) There are great SELinux and apparmor documents available to look at including the stickies in this subforum. I would say that you shouldn't have to worry about anything in the Ubuntu repositories (using the default profiles already made) so you only have to make profiles for those few "special" programs that you cannot otherwise avoid using. 

3) sudo (for command line) and gksudo (for GUI) using non-root accounts that don't have Internet access or have limited access is even easier.

4) [https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox) would be a good place to start.

Also, I saw reference to [http://fireflier.sourceforge.net](http://fireflier.sourceforge.net) (almost abandoned) and [http://leopardflower.sourceforge.net](http://leopardflower.sourceforge.net) (in the UbuntuForums).


I wish you best of luck.

---

### Post by Soul-Sing on 2011-03-02
> Please, don't tell me again that users should't install software from outside of repository. Sticking only to repository would make this system almost useless.

Maybe....but what applications are you talking about? what sofware
do you need from outside the repositories. please stick to the off. ubuntu software sources. It is the best way (and general advise) to secure your system. If you know your way via opensource projects/sourceforge/ etc.for additional software,ok, but it takes time and effort to find "safe" external software-sources.

Security is about restrictions: apparmor,selinux,bastille,internet related chat via ssl/sasl(tor), webmail via ssl, privoxy, noscript.
Security is a system.

---

### Post by rookcifer on 2011-03-02
--sigh---

If you simply do not install malicious software there is no need for an "outbound" firewall.  A non-malicious piece of software will only initiate connections out if it has a legitimate reason to do so (such as a web browser).  All of your "listening" services that accept connections from the WAN can easily be firewalled with iptables/UFW, which is already included.

---

### Post by opendoors on 2011-03-02
[QUOTE=leoquant]Maybe....but what applications are you talking about? what sofware
do you need from outside the repositories. please stick to the off. ubuntu software sources. It is the best way (and general advise) to secure your system. If you know your way via opensource projects/sourceforge/ etc.for additional software,ok, but it takes time and effort to find "safe" external software-sources.

Security is about restrictions: apparmor,selinux,bastille,internet related chat via ssl/sasl(tor), webmail via ssl, privoxy, noscript.
Security is a system.[/QUOTE]

[QUOTE=rookcifer]--sigh---

If you simply do not install malicious software there is no need for an  "outbound" firewall.  A non-malicious piece of software will only  initiate connections out if it has a legitimate reason to do so (such as  a web browser).  All of your "listening" services that accept  connections from the WAN can easily be firewalled with iptables/UFW,  which is already included.[/QUOTE]

[http://ubuntuforums.org/showthread.php?t=1591340](http://ubuntuforums.org/showthread.php?t=1591340) (see post #65 and up starting on page 7)

---

### Post by rookcifer on 2011-03-03
> **opendoors said:**
> [http://ubuntuforums.org/showthread.php?t=1591340](http://ubuntuforums.org/showthread.php?t=1591340) (see post #65 and up starting on page 7)

If something has kernel level access a firewall probably will not be able to stop it from doing what it wants to do.

But that aside, can you give any examples of programs you use on your Ubuntu box that are "phoning home?"

---

### Post by Soul-Sing on 2011-03-03
> **rookcifer said:**
> If something has kernel level access a firewall probably will not be able to stop it from doing what it wants to do.

But that aside, can you give any examples of programs you use on your Ubuntu box that are "phoning home?"

canonical-census

---

### Post by Ghost|BTFH on 2011-03-03
I believe I know what the problem is here.

"I WANT TO PLAY WINDOWS GAMES ON LINUX" (paraphrased)

If you want to play them and make sure they don't "phone home" then there's two ways I know of that would solve your issue without the whole "I wanna see what everything is doing in a pretty GUI"

First option, secure Linux so you don't get any network connection on a specific user:

> nodalus [Mar 06]: I don't know how much of wine's source would need to be changed to disallow all network commands, but I know that this kind of thing is possible using iptables (particularly with the owner extension).

If you create a new user id (which will be the one you use to start the application, using su or sudo), something like 'nonet', then run the following:

    iptables -I OUTPUT -m owner --uid-owner nonet -j REJECT --reject-with imcp-net-unreachable 

or something like that (I haven't tested it), it will block the 'nonet' user and any applications started as it from sending network packets. wine archive

Ed: this is not a per-application setting to disable network access, but blocks all running under user nonet.

Second option is to simply change the proxy settings in WINE to a non-existant proxy setting that will cause WINE to dead-end into no-network-land:

> In Bug 5625 H. Leidekker [March 08]wrote: Current git obeys the http_proxy environment variable for which graphical configuration screens exist in KDE and GNOME. The environment variable can be overridden by setting this registry key:

[HKCU\Software\Microsoft\Windows\CurrentVersion\Internet Settings]
"ProxyEnable"=dword:00000001
"ProxyServer"="http://proxyserver:8080"

And if you really really really really wanna know what's open right now, type:

sudo lsof -i -P -n

in a terminal.

Otherwise, it's NOT FREAKIN' NECESSARY if you're using trusted repositories to load a program on top of everything else to play mother-may-I? in Linux.  If you're not using trusted repositories, then you should really brush up on AppArmor and SELinux.

Sorry we don't have a pretty GUI per-software outgoing firewall program like ZoneAlarm, but funny thing is, we don't need it because our software isn't junk.

Cheers,
Ghost|BTFH

---

### Post by KonfuseKitty on 2011-03-03
> **Ghost|BTFH said:**
> If you're not using trusted repositories, then you should really brush up on AppArmor and SELinux.
*
Sorry we don't have a pretty GUI per-software outgoing firewall program like ZoneAlarm, but funny thing is, we don't need it because our software isn't junk.


What if some of us happen to think that AppArmor is junk? What then? Oh, I think I know what, you'll all jump on me like a ton of bricks to tell me how it's all my fault that I can't use it. But I've got better news for you: I'm a Ubuntu user, as valid as any other, and I've disabled and deleted AppArmor from my system because I find its philosophy non-sensical. Sorry.


I think this has now become more about power than anything else. The power that some users assume, telling others what they can or cannot have. The demand is there and if you don't like the solution being asked for you don't have to use it.

---

### Post by arapaho on 2011-03-03
Believe me I don't play games. I'm to old for that. But security can't be only a matter of trust. I would like to install some apps from other sources just because I need a variety of software. For example I download some opensource software from sourceforge like Nevernote or from other sources that don't have even PPA, like Chandler, Sunbird, Cherrytree. I need more functionality. Even if I trusted the developers they can make mistake or create some vulnerabilities without intention. So, don't tell me that I should trust. Trust is not a valid argument for me as far as security is concerned. And recently sourceforge has been compromised. I don't know if the apps I downloaded has been compromised or not but just in case I need to be able to control them before they to any harm to my system without watching logs 24/7. Apparmor might be good for servers and for advanced users. But its philosophy of blocking what already is out is just crazy. And its difficult to learn and doesn't have good documentation.

---

### Post by bodhi.zazen on 2011-03-03
> **arapaho said:**
> Believe me I don't play games. I'm to old for that. But security can't be only a matter of trust. I would like to install some apps from other sources just because I need a variety of software. For example I download some opensource software from sourceforge like Nevernote or from other sources that don't have even PPA, like Chandler, Sunbird, Cherrytree. I need more functionality. Even if I trusted the developers they can make mistake or create some vulnerabilities without intention. So, don't tell me that I should trust. Trust is not a valid argument for me as far as security is concerned. And recently sourceforge has been compromised. I don't know if the apps I downloaded has been compromised or not but just in case I need to be able to control them before they to any harm to my system without watching logs 24/7. Apparmor might be good for servers and for advanced users. But its philosophy of blocking what already is out is just crazy. And its difficult to learn and doesn't have good documentation.

If you do not want to trust, that is fine, you then need to learn to monitor.

If you wish to monitor your network, learn to use tcpdump, wireshark, and/or snort.

For HIDS I suggest OSSEC.

I also suggest you learn to use pax / grsecurity, apparmor, or selinux.

The tools are available to you, some even have graphical or web front ends - wireshark, selinux (on fedora 14) and ossec with the web panel would be my suggestions if you want graphical tools.

Apparmor is easier to learn then selinux and it would be trivial to write a profile for any and all applications, third party or no, but there are no graphical front ends.

So pick your poison - learn to trust or learn the tools available to you. This endless debate will not solve your problem.

---

### Post by Ghost|BTFH on 2011-03-03
> **KonfuseKitty said:**
> What if some of us happen to think that AppArmor is junk? What then? Oh, I think I know what, you'll all jump on me like a ton of bricks...

Wrong.  That's why I said "or SELinux" which is also a fine viable solution.  That's one of the beauties of Linux - if you don't like one program, there's more around.

The issue is that what's being requested would be the same thing as someone asking for a transmission for their transmission in a car.  Not even going into the logistical nightmare of why that's a stupid idea, the person just insists that it's what they want because "one of their old cars had it and it worked just fine for them!"

No mechanic is going to screw up a car, just to please someone who wants to drive one.  You're asking a programmer to basically screw up Linux just so you have the option of having it screwed up, because your old operating system worked that way just fine.

Now granted, that doesn't mean that eventually someone won't make the stupid program, it's just that those of us who have used the OS for awhile are stating, quite plainly, it's not necessary to get the job done.

What is being asked for is like a shoe shine on suede shoes.

Only sounds great if you don't know what you're talking about.

Cheers,
Ghost|BTFH

---

### Post by KonfuseKitty on 2011-03-04
> **Ghost|BTFH said:**
> Only sounds great if you don't know what you're talking about.


Indeed, this is partly what this is about, speaking purely for myself. I don't have the time to learn it all, monitoring traffic with Wireshark, setting up rules with Iptables, maintaining AppArmor profiles, learning SELinux, the list goes on. I need a sledgehammer tool that blocks all internet traffic. Then I'll feel secure with my system, knowing that despite my ignorance, nothing is connecting. Then I can make the exception for Opera and Evolution, Nautilus when needed, and I'm done. It may not be the "right way to do Linux", but it would be right for me. And I would pay for such a "stupid" program too.

---

### Post by nrundy on 2011-03-04
> **opendoors said:**
> By "outbound", I mean I need to be able to control which programs are allowed to access the Internet; that is, connect to some remote server from my computer. I'm not very experienced at Ubuntu, but all of the firewalls I've looked at for Ubuntu so far only allow me to control incoming connections. A router would be able to do the same thing.

Is there any such firewall for Ubuntu? I would prefer one that is friendly to newbies, but this isn't required as long as it's GUI instead of command line.

Hi opendoors :)

use GUFW. It can pass GRC shields up, which is important to most newbies :) and it gives you decent control over outbound stuff.

don't use Firestarter because it is no longer supported.

If you have any specific questions on config feel free to PM me or repost.

---

### Post by bodhi.zazen on 2011-03-04
> **KonfuseKitty said:**
> Indeed, this is partly what this is about, speaking purely for myself. I don't have the time to learn it all, monitoring traffic with Wireshark, setting up rules with Iptables, maintaining AppArmor profiles, learning SELinux, the list goes on. I need a sledgehammer tool that blocks all internet traffic. Then I'll feel secure with my system, knowing that despite my ignorance, nothing is connecting. Then I can make the exception for Opera and Evolution, Nautilus when needed, and I'm done. It may not be the "right way to do Linux", but it would be right for me. And I would pay for such a "stupid" program too.

The problem is that you are starting with a false assumption.

Out of the box, Linux is quite secure and you do not need to do anything to harden it.

Linux out of the box is more secure then hardened Windows.

If you are not satisfied with the answer, then yes you will have to do reading, there are no short cuts. Start with the security sticky at the top of these forums. Yes, you would have to learn apparmor / wireshark/ pax/grsecurity etc to harden your system further.

If you want a firewall, you have only to run a single command :

```
sudo ufw enable
```

It is not really necessary as there are no significant open ports by default.

---

### Post by opendoors on 2011-03-04
To claim that work has to be done in order to achieve certain things on Linux is one thing, but to claim that there is no need for an outbound application firewall is quite another. The conflation of these two claims is a roadblock to progress and is responsible for much unnecessary antipathy in many forums. Let's keep them separate.

[QUOTE=nrundy]Hi opendoors :)

use GUFW. It can pass GRC shields up, which is important to most newbies :) and it gives you decent control over outbound stuff.

don't use Firestarter because it is no longer supported.

If you have any specific questions on config feel free to PM me or repost.[/QUOTE]

Thanks for letting me know that Firestarter is no longer supported, but what do you mean by "decent" control? Based on what bodhi.zazen said in post #70 here, gufw only blocks ports, which of course results in the weakness that any application (including malicious ones) can use the ports that *are* allowed. On the other hand, if no ports are allowed, then you won't have Internet access at all: [http://ubuntuforums.org/showthread.php?t=1591340&page=7](http://ubuntuforums.org/showthread.php?t=1591340&page=7)

Passing GRC's shields up only indicates whether any of your ports are open to the outside world, not whether you have anything trying to connect out. A router could do the same thing. It's as good as useless to those that want control over what's on the inside. On the other hand, if we're talking about how resistant the system is to modification by malicious programs, that's a related, but different topic. This leads me to my next point.

[QUOTE=bodhi.zazen]The problem is that you are starting with a false assumption.

Out of the box, Linux is quite secure and you do not need to do anything to harden it.

Linux out of the box is more secure then hardened Windows.

If you are not satisfied with the answer, then yes you will have to do  reading, there are no short cuts. Start with the security sticky at the  top of these forums. Yes, you would have to learn apparmor / wireshark/  pax/grsecurity etc to harden your system further.
[/QUOTE]

The argument that Linux is quite secure out of the box is repeated everywhere. There are at least 2 major problems with this argument:

1. People don't leave their computers "out of the box". Regardless of the operating system you use, people tinker with it. This can either make it more or less secure. The default configuration of any system is not a reliable predictor of how secure the system could or should be.

2. As for "hardened" Windows, it really depends what kind of security you are talking about. Even if a Linux system may be more resistant to changes to important system files, the statement that Linux is more secure in *any* situation and in *every* way than any hardened Windows system is an overstatement at best.

In the end, everyone will decide what they need and what works best for them. However, I have to admit that the exponential amount of work required on Linux to achieve precisely the same functionality as Windows (i.e. the blocking of applications trying to connect out) greatly dampens my initial enthusiasm for Linux. For every user, there is a point at which the costs (i.e. time, effort) of using an operating system or program outweights the perceived benefits (i.e. greater security). If someone would simply create a tool that can more easily do the work that currently requires about 5 different programs and too much unnecessary time/effort, I'm sure more users would make the switch. There's no point to using 10 people to push a car when you can simply tow it with a truck. Not having a truck is one thing, but denying that one might be needed in at least some situations is quite another.

---

### Post by CandidMan on 2011-03-04
Having read through this thread, I would have to agree with those members saying right now there's no need for such  a program in Ubuntu
Scenario 1:

I start to install a potentially malicious program
I give it root access(at which point all bets are off)
=====>At this point it is either going to<=====
a) completely circumvent this 'security', complete pwn the computer, sending my bank details/directory listings/pgp keys to the bad guys. Leaving me safe in the knowledge that my 'security'
b)It's actually fine and maybe it sends some genuinely anonymous usage statistics.

Scenario 2:
I have the program sit in /home/ somewhere
I run it there as myself
I check where it's connecting with netstat/wireshark/lsof -i

Scenario 3:
I decide I don't trust the program at all and suspect it may have the mark of the beast (chmod 666 :))
=====>After careful contemplation I...<=====
a) install it
b) forget about it

For the record I only use Apparmor as Selinux just seems over my head at the moment(plus overkill)

---

### Post by robsoles on 2011-03-04
Seems like ex-Windows users coming to Ubuntu and feeling that it must be insecure because it does not have 'obvious dressing', like good old Windows XP immediately warning you if it can't find your intended anti-virus as soon as it boots for the first time or after having the anti-virus software uninstalled.

In Linux if you install it from a trusted source then it will be installed with all due permissions and is very likely to work, at least fairly, neatly for you - if it "phones home" then it is a behaviour that was accepted by people with a great deal more expertise than me and I accepted their judgement when I installed Ubuntu on my PC(s).

If you give root permissions to an installer from a 3rd party then you are entrusting your security to that 3rd party and if they want to data-mine you or use your system as any form of bot then they certainly can and no amount of AppArmor or SELinux can stop them - you gave them root after all, usually safe enough to do with genuine open source where you can review the source code before you compile it but accepting binaries this way is risky to such an extent that some people simply won't unless it's the only way they can make their new device 'play ball' with their system.

If you don't use AppArmor or SELinux or a (worthwhile) simile then a malicious binary, that ***somehow or other gets it's execute permission bit set, doesn't so much need root to access enough to data-mine you or use your computer for someone else's purposes.

If it's Windows *stuff* being ran in Wine then the suggestion to give Wine a bad proxy should be a fine way to stop the Windows *stuff* even seeing the internet, let alone 'phoning home'. An alternative might be to use [www.virtualbox.org]("http://www.virtualbox.org") to run a Windows session and don't even give the virtual machine a network interface - an OS with no connection can't provide support to programs trying to access the internet.


*** It is unlikely that an 'un-vetted' binary has it's execute bit set without your knowledge if you (1) read most of any prompt/page before pressing/clicking buttons and (2) don't run *just anybody's* binary with root permissions.

---

### Post by rookcifer on 2011-03-05
I think OP still doesn't understand the whole privilege thing. As has been repeated numerous times, when you install programs they usually require root access.  If a program has root access, it can do absolutely anything it pleases regardless of any outbound firewalls.  

Therefore, this means:

1) The program you just installed is malicious and is designed to phone home to some command and control IRC server somewhere. If this is the case, then it follows that the coder probably included means for this program to circumvent any firewall rules and mess around other system files to avoid detection (this is known as a rookit).  Now, let's say the coder wasn't smart and didn't include any means for his malicious code to circumvent iptables.  Thus, even if an outbound firewall would stop the program from phoning home, it doesn't much matter at that point because you have been root compromised.  And when you're root compromised, you MUST format and reinstall.

2) The program is not malicious and therefore doesn't phone home. 

3) The program is not malicious but likes to phone home for some sort of data mining.  I am not aware of any mainstream FOSS software that does this.  If you can give examples, I would be happy to listen.

As for AppArmor and SELinux -- SELinux is extremely fine grained and can restrict very minute things like the ability to open sockets, etc.  But if you are already compromised at the root level, then SELinux can likely be bypassed.  Same thing for AppArmor.  These tools (MAC's as they are called) are really only for stopping attacks on already existent services or to mitigate the damage that can be done via flaws in the code. They are also helpful for stopping an attack on one object from affecting other objects (a sandbox, essentially). (SELinux has some other features too, like MLS, that AppArmor doesn't have but it doesn't apply here).

Moral of the story:  Only install software from the official repositories (there's like 30,000 titles there).  If you must go outside the repos, then try well vetted PPA's first.

---

### Post by opendoors on 2011-03-05
[QUOTE=CandidMan]Having read through this thread, I would have to agree with those members saying right now there's no need for such  a program in Ubuntu
Scenario 1:

I start to install a potentially malicious program
I give it root access(at which point all bets are off)
=====>At this point it is either going to<=====
a) completely circumvent this 'security', complete pwn the computer, sending my bank details/directory listings/pgp keys to the bad guys. Leaving me safe in the knowledge that my 'security'
b)It's actually fine and maybe it sends some genuinely anonymous usage statistics.
[/QUOTE]

This is black and white thinking. Some programs are completely harmless, some are malicious, and some are questionable. The questionable ones phone him with information that you might or might not like. To assume that a program is either completely benign or completely malicious is to set up a false dichotomy.

[QUOTE=CandidMan]
Scenario 2:
I have the program sit in /home/ somewhere
I run it there as myself
I check where it's connecting with netstat/wireshark/lsof -i

Scenario 3:
I decide I don't trust the program at all and suspect it may have the mark of the beast (chmod 666 :))
=====>After careful contemplation I...<=====
a) install it
b) forget about it
 [/QUOTE]

As I've already said, not everyone is willing to use many different  programs to maybe achieve the same level of functionality that one  product might be able to provide. If you are running it as root, like  you said, "all bets are off". I don't expect an application firewall to  block something completely malicious that is allowed to run as root, but  this doesn't mean it can't serve other functions.

[QUOTE=robsoles]Seems like ex-Windows users coming to Ubuntu and feeling  that it must be insecure because it does not have 'obvious dressing',  like good old Windows XP immediately warning you if it can't find your  intended anti-virus as soon as it boots for the first time or after  having the anti-virus software uninstalled.
[/QUOTE]

I was hoping the title of this thread was clear enough in that I intended to discuss only the need for firewalls and not antivirus. I guess I was wrong. Please show me where I argued that a Linux computer was insecure because it didn't have an antivirus.

[QUOTE=robsoles]
In Linux if you install it from a trusted source then it will be  installed with all due permissions and is very likely to work, at least  fairly, neatly for you - if it "phones home" then it is a behaviour that  was accepted by people with a great deal more expertise than me and I  accepted their judgement when I installed Ubuntu on my PC(s).
[/QUOTE]

Some things are more a matter of preference than a matter of "expertise". If someone decides not to allow anything to phone home, that should be their own decision. If someone decides not to care, that should also be their own decision.

[QUOTE=robsoles]
If you give root permissions to an installer from a 3rd party then you  are entrusting your security to that 3rd party and if they want to  data-mine you or use your system as any form of bot then they certainly  can and no amount of AppArmor or SELinux can stop them - you gave them  root after all, usually safe enough to do with genuine open source where  you can review the source code before you compile it but accepting  binaries this way is risky to such an extent that some people simply  won't unless it's the only way they can make their new device 'play  ball' with their system.
[/QUOTE]

Too bad for "some people" then, because sometimes, installing the driver provided by the manufacturer is the **only** way to make their new device work on their system. It's also too bad that not all drivers are open source.

[QUOTE=robsoles]
If it's Windows *stuff* being ran in Wine then the suggestion to give Wine a bad proxy should be a fine way to stop the Windows *stuff* even seeing the internet, let alone 'phoning home'. An alternative might be to use [www.virtualbox.org]("http://www.virtualbox.org/")  to run a Windows session and don't even give the virtual machine a  network interface - an OS with no connection can't provide support to  programs trying to access the internet.
 [/QUOTE]

This only works if you actually want to deprive the game of Internet access. What if it's a LAN game that does need some Internet access? Wouldn't you want some straightforward way to specifically define what IPs and ports that particular application is allowed to access?

[QUOTE=robsoles]
*** It is unlikely that an 'un-vetted' binary has it's execute bit set  without your knowledge if you (1) read most of any prompt/page before  pressing/clicking buttons and (2) don't run *just anybody's* binary with root permissions.
 [/QUOTE]

I don't think we disagree here. Where I do think we disagree is in situations where the user must let the binary execute, but wants some control over what it's allowed to do afterwards.

[QUOTE=rookcifer]I think OP still doesn't understand the whole privilege  thing. As has been repeated numerous times, when you install programs  they usually require root access.  If a program has root access, it can  do absolutely anything it pleases regardless of any outbound firewalls.   
[/QUOTE]

I think you're proving my point by conceding that in situations where  programs don't have root access, an application firewall can be of some  use.

[QUOTE=rookcifer]
Moral of the story:  Only install software from the official  repositories (there's like 30,000 titles there).  If you must go outside  the repos, then try well vetted PPA's first.
 [/QUOTE]

I don't see how quantity is relevant here. If you need a specific driver  and there's no open source version of it, it doesn't matter if there's  300,000,000 titles. I think it's been stated repeatedly that not  everyone can or is willing to stick to the repositories.

---

### Post by robsoles on 2011-03-05
You've got me there about antivirus but I only mentioned it as the immediate obvious 'flag' that Windows XP shows on first boot after installing it 'clean'.



> **opendoors said:**
> ...

As I've already said, not everyone is willing to use many different  programs to maybe achieve the same level of functionality that one  product might be able to provide. If you are running it as root, like  you said, "all bets are off". I don't expect an application firewall to  block something completely malicious that is allowed to run as root, but  this doesn't mean it can't serve other functions.



CandidMan mentioned three different ways that the same (or really really similar at least) job could be done - netstat can show you everything connecting, wireshark is very revealing if you set it up correctly and lsof -i appears to list connections in such a pace that if you ran that in terminal and left that running while you start a program you would quickly see what connections that program causes/uses.

Three different tools, you can use them simultaneously but you only need run one momentarily while you try to operate the suspect software.

---

### Post by KonfuseKitty on 2011-03-05
> **rookcifer said:**
> I think OP still doesn't understand the whole privilege thing. As has been repeated numerous times, when you install programs they usually require root access.  If a program has root access, it can do absolutely anything it pleases regardless of any outbound firewalls.


I take that to mean that an outbound firewall would need to be in the kernel to catch everything, with root access and without, right? Because if that wouldn't work, then what you're really saying is that by design Linux can't have effective outbound protection, and I don't believe that to be the case.

---

### Post by Ghost|BTFH on 2011-03-05
The bottom line to all of this is - we're not talking about software from the repositories, nor even 3rd party vendors.  We're talking about running Windows programs in WINE.  Let's look at this from a logistics and programming perspective:

Scenario A:  You run a program that is questionable as a limited access user (ie, non-root) and observe a terminal output for holes.  Having found 3 ports being used by the program, you surmise that 2 of them phone home, only 1 of them is useful.  At this point, since you despise any of the current solutions for security on Linux, you simply access your router and activate its port blocking features (very common on today's routers) and restrict any/all outgoing data to/from those ports.

The program believes it can access out, the router just simply drops all packets.  Problem solved.

Scenario B:  You run a program that is questionable (with or without root, depending on the program's needs) with confidence because you have a top layer GUI permissions table that monitors all outgoing traffic and pops up to let you know what's being used and to ask for permission to allow access.

Unfortunately however, you're running the program in WINE.  The GUI permissions table does not see "Horny Rabbits With Chainsaws" running, it sees WINE running.  It would see WINE opening ports and it would be WINE that it would ask you for permissions on.

With this program, your GUI permissions table program now has a ruleset for WINE - not the game you just played, but all of WINE.  

This permissions ruleset now makes it so that other programs in WINE will have to follow the same rules.  The more programs you run through WINE, the more restrictions you put on it because of various issues in various games and therefore the more clogged WINE's access to the outside world becomes.

At this point we must look at one of two solutions - scrap the whole thing because it will not effectively do what we want; or make the program "forget" permissions rules every time we restart it.

The first solution brings us back to where we are - with no GUI permissions table software for you.

The second solution allows you to play your games - after potentially crashing everything multiple times (and hopefully eventually getting the permissions set that you wanted).  You see, when you run games in WINE and then have things pop up, just like in Windows there's a chance it could lock the system up.  Unlike Windows, it usually won't lock the WHOLE system up - but it will most likely take down your GUI interface.  

It's also more likely to happen in WINE than in Windows.  That's the price you pay for trying to run something in a non-native environment.

In short, those of us who do not trust anything, learn to code.  We download the source and scour through it.  Those of us who do not wish to do so, learn to trust those who do in this community.

We do not pretend to be super secure just because we have program XYZ.  We are aware that if we do not trust anything, then logically, we cannot trust program XYZ either, unless we ourselves write it from scratch.

Linux is about trust - if you trust the community, you will be as safe as the community will let you be...just know that the rest of the community relies on the same security as you for the most part, so it is in their best interest to protect the whole community.

If you do not trust, you must learn to program.

Here ends the gospel reading according to St. Python.

Let us code...

~Ghost|BTFH

---

### Post by CandidMan on 2011-03-05
> To assume that a program is either completely benign or completely malicious is to set up a false dichotomyI apologise if I've failed to explain what I meant clearly.

What I meant was that subjectively, from a user's point of view, a program is either benign or malevolent. what other classification is there? Benign but displays "questionable" behaviour? Malign but well behaved?

Like, I don't know Adobe reader vs LOIC?

---

### Post by opendoors on 2011-03-05
> **Ghost|BTFH]The bottom line to all of this is - we're not talking  about software from the repositories, nor even 3rd party vendors.  We're  talking about running Windows programs in WINE.  Let's look at this  from a logistics and programming perspective:
[/QUOTE]

Actually, we're talking about all 3 of these. An application firewall has the capability to:

1) Prevent software from repositories from phoning home
2) Control the Internet access of software from 3rd party vendors such  as installation packages that contain drivers for hardware devices
3) Control the Internet access of Wine (and therefore anything running in Wine)

[QUOTE=Ghost|BTFH]
Scenario A:  You run a program that is questionable as a limited access  user (ie, non-root) and observe a terminal output for holes.  Having  found 3 ports being used by the program, you surmise that 2 of them  phone home, only 1 of them is useful.  At this point, since you despise  any of the current solutions for security on Linux, you simply access  your router and activate its port blocking features (very common on  today's routers) and restrict any/all outgoing data to/from those ports.

The program believes it can access out, the router just simply drops all packets.  Problem solved.
 [/QUOTE]

You "surmise" that 2 of them phone home and that only 1 of them is  useful? I think your example perfectly illustrates a problem with  inductive logic and the strength of an application firewall. There are 2  problems that you present with scenario A:

1) No matter how many times you observe the program accessing the  Internet, you can never be sure (unless you have an application firewall  configured to properly control access) that it will only use those  ports. To be completely sure without an application firewall, you will  need to sit there 24/7 watching it without making a single mistake. Are  you willing to do this?

2) Restricting a port as the only method of controlling access (instead  of restricting an application) suffers from 2 different problems:
a. A program can simply phone home through a different port that isn't  blocked. If you haven't blocked the application, you haven't blocked  anything.
b. If you allow any particular port (and you have to allow some ports,  or you won't have Internet access), a program can simply phone home  through that allowed port. If you have an application firewall to  control access at the level of the program, you don't have to take any  chances playing Roulette with your security.

[QUOTE=Ghost|BTFH]
Scenario B:  You run a program that is questionable (with or without  root, depending on the program's needs) with confidence because you have  a top layer GUI permissions table that monitors all outgoing traffic  and pops up to let you know what's being used and to ask for permission  to allow access.

Unfortunately however, you're running the program in WINE.  The GUI  permissions table does not see "Horny Rabbits With Chainsaws" running,  it sees WINE running.  It would see WINE opening ports and it would be  WINE that it would ask you for permissions on.

With this program, your GUI permissions table program now has a ruleset  for WINE - not the game you just played, but all of WINE.

This permissions ruleset now makes it so that other programs in WINE  will have to follow the same rules.  The more programs you run through  WINE, the more restrictions you put on it because of various issues in  various games and therefore the more clogged WINE's access to the  outside world becomes.

At this point we must look at one of two solutions - scrap the whole  thing because it will not effectively do what we want said:**
> 
So you're questioning the technical possibility of one specific use of  an application firewall? I have 2 responses. First, even if we assume  that an application firewall is less effective for  restricting/controlling Internet access for programs running within  Wine, that doesn't mean it's useless for everything else. As I pointed  out earlier, an application firewall can control Internet access for  programs in the repositories, programs from third party vendors, AND  (potentially) programs running in Wine. All you've said is that if you  take all the software that can possibly run on Ubuntu, some of it might  not work with an application firewall. But this is always going to be  the case for any program. It certainly doesn't mean the program  shouldn't exist.

Second, what are the implications of this technical problem? There are  two possibilities: either we can get around it, or we can't. If we  recognize that there are good reasons to have GUI application firewalls,  then it should be our goal to increase the chances that it could work  better with Wine (i.e. restrict individual applications within Wine  instead of just Wine as a whole). Our recognition and support for  developers who might want to take on this challenge would further this  goal. On the other hand, even if we absolutely can't get around this  technical problem, simply go back to my first response: there are other  good reasons for application firewalls to exist.

[QUOTE=Ghost|BTFH]
 The second solution allows you to play your games - after potentially  crashing everything multiple times (and hopefully eventually getting the  permissions set that you wanted).  You see, when you run games in WINE  and then have things pop up, just like in Windows there's a chance it  could lock the system up.  Unlike Windows, it usually won't lock the  WHOLE system up - but it will most likely take down your GUI interface.   
  
Yes, you are correct that it is possible in Windows for a  popup to lock the system up if you happen to get an alert after you've  started a game. This is another technical problem, but in this case,  there are already multiple solutions. First, a good firewall would not  allow anything without your explicit consent, so if your system locked  up, nothing was allowed yet. Simply reboot the computer forcibly using  the power button, check your logs to see what was blocked, then make a  rule to allow it before starting your game again. You might have to  repeat this a few times in the worst case, but your problem is solved.

Second, some firewalls such as Zonealarm have "game mode". According to the company, game mode does the following:

"Understanding Game Mode 
 Game Mode minimizes interruptions while you play computer games by doing the following: 
 
 Lets you temporarily allow or deny all program permission requests, so that requests are answered without displaying alerts. 
 Postpones automatic scans and product updates.
 Suppresses all Informational alerts and all alerts in which you are prompted to make a decision. This includes:
 Alerts caused by Ask settings in the Programs List, such as permission  alerts triggered by programs trying to send mail or act as servers. 
 OSFirewall alerts, which prompt you to allow or deny behavior considered unusual or suspicious. 
 ID Lock alerts and Outbound Mailsafe alerts. 
 Game Mode settings do not override Block or Allow settings in your  Programs List. If you have configured ZoneAlarm security software to  always block a specific program, it continues to block that program even  if you activate Game Mode with a setting of Allow. 
 
 Game Mode remains active until you turn it off, or until you turn off ZoneAlarm security software or your computer."

Clearly, game modes in firewalls is an imperfect solution and could use  much work. But it could work for those who do not care about their games  going online (again, a personal choice). I'm not trying to endorse any  product here. All I'm trying to do is illustrate that there **are**  solutions to this technical problem that you mention in Windows. Why?  It's simple: application firewalls have existed in Windows for far  longer than they have in Linux, so they are more well developed. But if  we recognize that there's a similar need in Linux, then we've taken the  first step towards catching up.

[QUOTE=Ghost|BTFH]
It's also more likely to happen in WINE than in Windows.  That's the  price you pay for trying to run something in a non-native environment.
   [/QUOTE]
Even if this is true, it shouldn't come as a surprise. A price is paid  to run many programs in Wine when those programs don't run perfectly. If  we try anyways, then we're accepting that price. This is more a problem  with Wine than a fundamental problem with application firewalls.

[QUOTE=Ghost|BTFH]
In short, those of us who do not trust anything, learn to code.  We  download the source and scour through it.  Those of us who do not wish  to do so, learn to trust those who do in this community.

We do not pretend to be super secure just because we have program XYZ.   We are aware that if we do not trust anything, then logically, we cannot  trust program XYZ either, unless we ourselves write it from scratch.
[/QUOTE]

Even if you learn to code, do you really have the time to go through  every single line of code (some of which may be obfuscated) in the  source? Most people only have the time to check that it's open source  and trust it based on that.

But the problem is more complicated than this. There are different kinds  of trust. Trusting a program to run is not the same as trusting it with  Internet access.

I don't think anybody is pretending to be super secure just because they  have an application firewall, but questioning whether its developer is  trustworthy is another matter. It's like questioning whether your bank  is trustworthy enough to hold all of your money. Obviously, some trust  is necessary. All I've claimed is that trust **alone** is not always an adequate solution to security, and that an application firewall can help fill in the gap.

[QUOTE=Ghost|BTFH]
Linux is about trust - if you trust the community, you will be as safe  as the community will let you be...just know that the rest of the  community relies on the same security as you for the most part, so it is  in their best interest to protect the whole community.

If you do not trust, you must learn to program.

Here ends the gospel reading according to St. Python.

Let us code...
~Ghost|BTFH[/QUOTE]
Exactly. But the statement that  "you will be as safe as the community will let you be" is,  unfortunately, true in more than one way. Just as you might be safer  with your default settings because you're in the community, you are also  limited by what the community has to offer. For example, if the  community currently lacks an application firewall, then you will not be  able to take advantage of one. If it is true that you are only as safe  as the community will let you be, then I would hope that the community  offers you more options, and I know I am not alone in this sentiment,  even if we may be in the minority at the moment.
 
[QUOTE=CandidMan]I apologise if I've failed to explain what I meant clearly.

What I meant was that subjectively, from a user's point of view, a program is either benign or malevolent. what other classification is there? Benign but displays "questionable" behaviour? Malign but well behaved?

Like, I don't know Adobe reader vs LOIC?[/QUOTE]

No apology needed, this is just a discussion after all! In fact, I think I should have been more clear about what I meant also. What I meant was along the lines of where you were going with Adobe reader and LOIC. Here's one way (out of many) that you can classify programs on the scale from benign to malevolent. This is just an example!

1. Completely malicious: Destroys data, allows remote control of the computer, phones home with credit card information, etc.
2. Undesirable: Pesters the user with advertisements or installs unnecessary software without giving you a choice of opting out but doesn't steal any personal information or destroy data (e.g. Adobe Reader installs useless junk like Adobe Air)
3. Somewhat undesirable: Phones home with your hardware configuration or usage statistics without giving you a choice to opt out or disregarding your choice, installs undesirable software that has no overt function (e.g. Oracle JRE phones home with your system information and installs a browser plugin that doesn't seem to be malicious but also has no obvious function)
4. Completely benign: Doesn't try to phone home at all or only accesses the Internet for legitimate reasons such as getting updates. Always tells you when it tries to access the Internet. No nasty surprises.

There are probably more categories anywhere between completely malicious and completely benign, depending on what you consider undesirable. The important point is that the user should have a choice by having the ability to control Internet access with an application firewall, no matter what they view as benign or malicious.

---

### Post by robsoles on 2011-03-05
> **opendoors said:**
> ...

4. Completely benign: Doesn't try to phone home at all or only accesses the Internet for legitimate reasons such as getting updates. Always tells you when it tries to access the Internet. No nasty surprises.

...

I really appreciate it when I run a program for the first time and it basically asks me flat out if it may phone-home and let it's Author know 'someone' uses it - I usually allow that but it's rare the software announces all such intentions.

Between iptables and AppArmor (or SELinux) there effectively exists a software firewall, albeit not having all of it's power exposed to novice users via a GUI yet. It probably can target individual WINE applications but I haven't stumbled onto how to do so - if it's possible then **I** am less likely to find it because I test suspect software in a Virtual Machine of it's native OS and only ever install apps I trust into WINE.


My viable alternative: [www.virtualbox.org]("http://www.virtualbox.org"), make a Virtual Machine of your least despised flavour of Windows and install your favoured Windows firewall into that and then run your suspect programs there.

---

### Post by Ghost|BTFH on 2011-03-05
> **opendoors said:**
> Actually, we're talking about all 3 of these. An application firewall has the capability to:

1) Prevent software from repositories from phoning home
2) Control the Internet access of software from 3rd party vendors such  as installation packages that contain drivers for hardware devices
3) Control the Internet access of Wine (and therefore anything running in Wine)

All of which you could really do through your router, to be perfectly blunt.  Sure, it's "possible" to do so in the OS.  But what you're asking for is like asking for someone to put a manual safety on a Glock.  It's got 3 friggin' safeties on it already, basically when you pick it up and point it and squeeze the trigger, you're engaging them all.  Why would you want a manual safety that screws up the function and performance of the gun in the first place?

That's really the only issue I have with what you're asking for.  You're asking for programmers to create something that makes the system bog down, perform poorly, basically...to run like Windows.  If that's what you want, you should stick with Windows to be honest.  An operating system that comes from an open source community is great - if you trust the community.  You obviously don't, so perhaps closed source written by people who are known for putting back doors into even the base operating system would be a better idea.

> **opendoors said:**
> You "surmise" that 2 of them phone home and that only 1 of them is  useful? I think your example perfectly illustrates a problem with  inductive logic and the strength of an application firewall. There are 2  problems that you present with scenario A:

1) No matter how many times you observe the program accessing the  Internet, you can never be sure (unless you have an application firewall  configured to properly control access) that it will only use those  ports. To be completely sure without an application firewall, you will  need to sit there 24/7 watching it without making a single mistake. Are  you willing to do this?

Absolutely not, I'll send it to a logfile and read it in the morning.

> **opendoors said:**
>  Restricting a port as the only method of controlling access (instead  of restricting an application) suffers from 2 different problems:
a. A program can simply phone home through a different port that isn't  blocked. If you haven't blocked the application, you haven't blocked  anything.
b. If you allow any particular port (and you have to allow some ports,  or you won't have Internet access), a program can simply phone home  through that allowed port. If you have an application firewall to  control access at the level of the program, you don't have to take any  chances playing Roulette with your security.

Point well taken - floating port protocols could be an issue.  However, so can installing a program that is untrusted as root, even with a protective piece of software monitoring everything - such a program can be deactivated by a root installed piece of software.  If you give it root, you're potentially giving it 100% control over your system.  There IS no way around this issue, no matter how much you want to argue it.  Installing untrusted software voids this whole discussion because, in fact, it's untrusted and root.  Period.

> **opendoors said:**
> On the other hand, even if we absolutely can't get around this  technical problem, simply go back to my first response: there are other  good reasons for application firewalls to exist.


Not to sound like a pain in the posterior, but I'm still waiting to hear the first good reason.  "Because I don't trust the makers of the OS" just doesn't cut it for me or most of the others because...well...everyone here is part of that community.  We (hopefully) help out all the time - reporting bugs, writing code, reviewing code...and getting put into the official repos is not as simple as going, "Lawl, I just wrote up a new program d00d, check it out!!!"  It goes through a very strict process to pass muster.

Basically, you're saying, "You do all this great stuff, you're an honest and fully open community - but because I can't read what you're writing down, I don't trust you."  From our perspective, the issue isn't us or how we do things.  It's how your mind still thinks in Windows mode.

> **opendoors said:**
> It's simple: application firewalls have existed in Windows for far  longer than they have in Linux, so they are more well developed. But if  we recognize that there's a similar need in Linux, then we've taken the  first step towards catching up.

Yes, they have existed in Windows.  They don't exist in Linux.  Let's look at this from a logical perspective.  One of the following statements must be true:

A) We're behind the times and Windows just blows us away in application capabilities and security matters.

B) We've never had a need for application firewalls, so we never wrote one.

Considering at the last DefCon there were 3 laptops up for grabs (Pwn2Own) and the Apple laptop was raped in under a minute...the Windows one in under an hour...and the Ubuntu one stood standing for the whole weekend...I'm thinking we can safely presume that A) is false.

Which leads us to the conclusion that B) is the correct answer.

> **opendoors said:**
> 
Even if you learn to code, do you really have the time to go through  every single line of code (some of which may be obfuscated) in the  source? Most people only have the time to check that it's open source  and trust it based on that.

Actually, for some people, that's their entire job.  For others, it's a hobby, and for even more, it's an obsession.  Yes, there are many people who pore through every line of code, some of them even mention Easter Egg code hidden in programs as running jokes with other programmers.

So yeah, a lot of us don't have the time to check the code - but you can bet your bottom dollar if it hit the repos, a LOT of people DID take the time to read EVERY...SINGLE...LINE.

> **opendoors said:**
> Exactly. But the statement that  "you will be as safe as the community will let you be" is, unfortunately, true in more than one way. Just as you might be safer with your default settings because you're in the community, you are also limited by what the community has to offer. For example, if the community currently lacks an application firewall, then you will not be able to take advantage of one. If it is true that you are only as safe as the community will let you be, then I would hope that the community offers you more options, and I know I am not alone in this sentiment, even if we may be in the minority at the moment.

I'm limited by having virtually any kind of conceivable program I could NEED sitting in a trusted repository that is created with very strict rules and guidelines.

The bottom line is, I thought the same way you did when I first made the switch - I wasn't born on Linux, I'm a Windows convert - of the worst kind!  I work on computers for a living, fixing issues and securing systems for end users.  So when I used to set up a Windows box, it didn't crash, it was secure, I removed backdoors that 99% of the population didn't even know existed.

When I switched to Linux, the first thing I wanted to know was, "How do I secure my box?!?!?" and I was told, by (I now realize) an amazingly patient Linux geek, that it was pretty darned secure right out of the box.

I didn't believe it.  I wanted programs, bells, whistles...all the things I had on Windows that made me feel safe and secure.  Things that alerted me to ANYTHING that attempted to misbehave on my computer.

Eventually I realized - if it's from the trusted repos, it's going to behave.  If I had to install something outside of the repos, for whatever reason (And believe me, I learned to avoid it at all costs if I can - hardware drivers for some oddball equipment and the drivers didn't come from the repos or the company itself?  I'll go buy new hardware that works with Linux instead) then I knew I was taking a risk.  It was a question of was it worth the risk for that one thing, or was it better for me to find a more viable alternative and stay safe and secure?

The answer I learned was - it's better to stay safe and secure without having to have a million bells and whistles to give you a false sense of security.  And it is false - as I said, let's say we write a program that detects all application activity.

Evil coder writes a backdoor into program X.  Not knowing about the backdoor, you feel that program X is something you need.  You download it, and install it as root.  Unless you understand EVERY SINGLE THING it's doing while installing, you have no clue that it just opened all permissions in the application firewall.  Or maybe just gave itself full permissions and left the rest as it was.

Either way, they've just rooted your system.  Because the application firewall failed?  No, because you gave root access to an untrusted program.

No matter what else you want to debate, you cannot argue this fact and that makes this entire discussion moot.  An application firewall is a waste of time.

~Ghost|BTFH

---

### Post by opendoors on 2011-03-06
Ok, that's it. I'm not going to bother responding anymore because I would be going in circles. Nothing will happen in the forseeable future anyways, no matter how much time I waste repeating myself. Unless someone actually makes some *new* arguments, I'm done with this thread.

---

### Post by scorp123 on 2011-03-07
> **opendoors said:**
>  I would be going in circles. That's because you try to apply Windoze solutions to Linux :D

I told you to let go of your Windows ways. And nobody is forcing you to use Linux ... if you're more comfortable with Windows then by all means, use that. Or buy a Mac? Apple Mac's are nice too.

And while we're at it, please read this again?

**_Linux is not Windows_**
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

---

### Post by KonfuseKitty on 2011-03-08
Yup, a waste of time. But the Linux distribution that implements this solution first is the distribution that will earn my trust. The discussion in this thread has only served to undermine whatever trust I previously had in the Ubuntu ecosystem. For the time being I'm resigned to what I perceive as ulterior motives at play, but going forward, there's more to Linux than Ubuntu. I can leave it at that.

---

### Post by robsoles on 2011-03-08
> **KonfuseKitty said:**
> Yup, a waste of time. ...

For the time being I'm resigned to what I perceive as ulterior motives at play, 

...

I'd reckon the ulterior motives, that the people with the required skills have, is that the firewall requirements are all there and looking for weaknesses in that and writing improvements in it are much more their agenda than making a (more) GUI for it.


In my honest opinion; the only way to know for sure whether or not the OS you have installed in your PC is using your connection to phone home on *anybody*'s behalf is to have the routing system log connections from the suspect PC.

If you have a modem router that has good software then you can make a firewall wall using the suspect PC's IP address as the source and WAN/Internet as the destination with rule match logging set to "matches rule" and see all outgoing connections the PC makes in a session in the router's logs.

You can block all requests and go through the log to figure out what ranges to disallow/allow to gain the desired functionality of a suspect system or program.

If you have a PC with two ethernet ports you can set it up for NAT and have it log outgoing connections for  a specific IP address using it's routing facility and completely expose all unauthorised activity that way too.


There are too many ways I can achieve what you want to with the tools that install straight off Ubuntu 10.xx LiveCDs and using blocking/allowing/logging at the router system - I haven't bothered mucking around with my router since about a week and a half after I switched my main PCs to Linux.

---

### Post by bodhi.zazen on 2011-03-08
> **KonfuseKitty said:**
> Yup, a waste of time. But the Linux distribution that implements this solution first is the distribution that will earn my trust. The discussion in this thread has only served to undermine whatever trust I previously had in the Ubuntu ecosystem. For the time being I'm resigned to what I perceive as ulterior motives at play, but going forward, there's more to Linux than Ubuntu. I can leave it at that.

Security on any OS is a complex issue and requires a fair amount of reading and understanding of how the underlying system works.

Ubuntu out of the box is more secure then hardened installations of Windows or OSX, simply search the results of pwn2own

[http://dvlabs.tippingpoint.com/blog/2008/03/19/cansecwest-pwn-to-own-2008](http://dvlabs.tippingpoint.com/blog/2008/03/19/cansecwest-pwn-to-own-2008)

Each of these OS has various security features and you can NOT simply apply Windows security mentality to Linux any more then you can apply Linux security to Windows.

The type of "software firewall" as you envision is it not available in Linux as it is simply ineffective technology. While you might be of the opinion it is effective, in reality it is trivial to circumvent, even on Windows.

The solution to your question is to :

1. Learn to monitor your network traffic.

2. Learn how to deploy selinux or apparmor.

There is no simple solution to what you are asking for in either Linux or Windows.

If you are wanting to harden your Linux installation you have much to learn.

[http://www.ashidakim.com/zenkoans/1acupoftea.html](http://www.ashidakim.com/zenkoans/1acupoftea.html)

Like the professor, you are full of your own ideas.

---

### Post by KonfuseKitty on 2011-03-08
> **bodhi.zazen said:**
> Like the professor, you are full of your own ideas.


Not quite. A little trip down the rabbit hatch reveals that the functionality being asked for basically used to be available in the shape of the --pid-owner filter in iptables. At some point it became incompatible with SMP, which is most computers nowadays, and/or was taken out of newer versions.


If we still had this filter it would be next to trivial to set up an outgoing firewall, blocking and whitelisting applications. Surely GUIs would have evolved alongside.


So the issue is one of an update to functionality gone missing, not of me and others being "full of your own ideas". And I must say, sharing back some of your own medicine, that having found this information, I'm not so impressed by all you "experts" here. You all basically made yourselves busy talking about Linux ain't Windoze and making people look silly, but you didn't once mention that the functionality used to be there already.

---

### Post by HermanAB on 2011-03-08
Howdy,

I am glad that you started to read up on things.  Keep going.  It is time well spent.

The functionality to make a program specific filter is still in iptables.  Security is more easily enforced using users and groups, not with ephemeral things like PIDs.

Define a unique group with addgroup.  Create an iptables filter that triggers on the group.  Use sg to run your application as that group.

For example:
```
/sbin/iptables -A OUTPUT -d 127.0.0.1 -m owner --gid-owner uniquegroup -j ACCEPT
/sbin/iptables -A OUTPUT ! -d 127.0.0.1 -m owner --gid-owner uniquegroup -j REJECT
```

Then run the application with:
```
sg uniquegroup /usr/local/bin/application
```

Use webmin or UFW or whatever to manage iptables if you want a GUI.

BTW, if you really want to know how iptables works, read the man page about 5 times.  It will eventually start to make some sense.  There is no easy way.

---

### Post by KonfuseKitty on 2011-03-08
Nah, I read too much as it is, really do. Like the post above, for example. Suggesting that a workaround is better than the real thing. I'm done - Cheerio!

---

### Post by Irihapeti on 2011-03-08
Here's a possibility: find a programmer and pay him/her well to write an outbound GUI application-based firewall. If the demand is as great as suggested, then there should be no trouble selling it to newcomers.

One thing does have me wondering, though: why should the writer of such a firewall program be inherently any more trustworthy than other programmers? Even if one is paying him/her, he/she can still sneak something nasty into the code.

---

### Post by HermanAB on 2011-03-09
> Nah, I read too much as it is, really do. Like the post above, for example. Suggesting that a workaround is better than the real thing. I'm done - Cheerio!
It is green they say, on the far side of a hill.

---

### Post by Grenage on 2011-03-09
> **bodhi.zazen said:**
> Out of the box, Linux is quite secure and you do not need to do anything to harden it.

To be honest, Ubuntu itself isn't a great example of that.  The Remote Desktop feature runs by default, and will happily use uPnP to open up ports on a home router.  Most users don't know it's even there or running, and I've read *plenty* of forum threads by users who got hacked through it.

While it's easy to say 'it should work like this', 'don't install software you don't trust', or 'that's a Windows mentality', a GUI based firewall can offer peace of mind. I've seen software become successful for less.

I wouldn't use one, I configure my gateway without uPnP and without any all-out rules, but I believe that such software would be quite successful.

---

### Post by Irihapeti on 2011-03-09
My experience with quite a few installs of Ubuntu is that remote desktop is installed but not listening for connections by default. If someone has no idea that it's there, they won't be vulnerable to connections, because they have to go in and click on that box to allow connections. 

My suspicion is that people see it and think "What a cool feature!" without thinking the whole security thing through. Probably much the same as installing a SSH or FTP server without realising that you need more than the kind of password you can get away with on many work machines.

I'd still prefer not to have remote desktop installed by default, and I remove it from my own installations.

---

### Post by Grenage on 2011-03-09
> **Irihapeti said:**
> My experience with quite a few installs of Ubuntu is that remote desktop is installed but not listening for connections by default. If someone has no idea that it's there, they won't be vulnerable to connections, because they have to go in and click on that box to allow connections. 

My suspicion is that people see it and think "What a cool feature!" without thinking the whole security thing through. Probably much the same as installing a SSH or FTP server without realising that you need more than the kind of password you can get away with on many work machines.

I'd still prefer not to have remote desktop installed by default, and I remove it from my own installations.

That's possible; I'd go and check, but like you I have removed it from all of my installs.

---

### Post by doas777 on 2011-03-09
> **Grenage said:**
> To be honest, Ubuntu itself isn't a great example of that.  The Remote Desktop feature runs by default, and will happily use uPnP to open up ports on a home router.  Most users don't know it's even there or running, and I've read *plenty* of forum threads by users who got hacked through it.

While it's easy to say 'it should work like this', 'don't install software you don't trust', or 'that's a Windows mentality', a GUI based firewall can offer peace of mind. I've seen software become successful for less.

I wouldn't use one, I configure my gateway without uPnP and without any all-out rules, but I believe that such software would be quite successful.
+10.
I'm more than a little tired of people telling me I don't want firewall monitoring software. I actually do want it, even if certain users think I'm too stupid to realize that I don't. 

in the end, I had to set up a logserver (using rsyslogd) and phpConLog (quite an exercise since there are no howto's) to get the info i wanted in any kind of gui tool. 

everyone seems to forget that verification is an important part of the security game. monitoring the connections after a change in the firewall is an essential step in testing the change.

---

### Post by cariboo on 2011-03-09
@doas777, would you care to create a howto for those that feel they need what you have done?

---

### Post by doas777 on 2011-03-09
> **cariboo907 said:**
> @doas777, would you care to create a howto for those that feel they need what you have done?
I've really been considering it (would be my only claim to fame). hopefully i will have a long weekend soon to duplicate it from the ground up documenting each step.

---

### Post by EJeanmaire on 2011-03-09
Actually, there are some privacy issues at stake which may require the use of an application firewall (I only know of Little Snitch for Mac OS X, I do not have one on my Ubuntu boxes), many programs like to phone home with your personal data and preferences to the software vendor.  For example, by default, and only changable in the advanced configuration, Firefox automatically reports every website you visit to some variant of safe-browsing.google.com.  Which may be intended as a phishing filter, however many users may not like this idea.  Also last I checked, turning off the phishing filter in the settings does not stop this.

---

### Post by bodhi.zazen on 2011-03-09
> **doas777 said:**
> monitoring the connections after a change in the firewall is an essential step in testing the change.

I have advocated monitoring throughout this thread.

There are several tools available for such monitoring, ntop, wireshark, tcpdump, snort to name a few.

Personally I use snort as I do not want to review all the traffic.

For the times when I want to see all traffic tcpdump FTW !!!

If you want a graphical tool, wireshark.

---

### Post by rookcifer on 2011-03-09
> **Grenage said:**
> To be honest, Ubuntu itself isn't a great example of that.  The Remote Desktop feature runs by default, and will happily use uPnP to open up ports on a home router.  Most users don't know it's even there or running, and I've read *plenty* of forum threads by users who got hacked through it.

That's incorrect.  VNC or "remote desktop" does ***not*** run by default.  The user has to activate it first.  

Now, once activated it does automatically use unpnp and open up a port on the WAN as you say.  And this has resulted in a lot of people getting compromised.  But it does not run by default.

I think the Ubuntu team should adjust the way remote desktop works so that it doesn't default to listening on the WAN.  I will agree 100% on that point.

---

### Post by Grenage on 2011-03-09
> **rookcifer said:**
> That's incorrect.  VNC or "remote desktop" does ***not*** run by default.  The user has to activate it first.

Thank you for the correction.

---

### Post by doas777 on 2011-03-09
> **bodhi.zazen said:**
> I have advocated monitoring throughout this thread.

There are several tools available for such monitoring, ntop, wireshark, tcpdump, snort to name a few.

Personally I use snort as I do not want to review all the traffic.

For the times when I want to see all traffic tcpdump FTW !!!

If you want a graphical tool, wireshark.
thats a good point, all of them are great tools, but none of them seem to fulfill my basic desire to be able to right click an log entry, and select something like "Allow Connections from Host", or whatever other common action.

---

### Post by robsoles on 2011-03-10
> **doas777 said:**
> thats a good point, all of them are great tools, but none of them seem to fulfill my basic desire to be able to right click an log entry, and select something like "Allow Connections from Host", or whatever other common action.

mmmh, I am not claiming to be a horribly advanced coder but I am basically a coder and I've been looking at this from the perspective of trying to write what some people are asking for and seeing a nightmare.

Your post makes me think of another couple of reasons why people who have the skills, and knowledge, required to provide *this* won't.

They might be trying to be 'altruistic' about it - if they provide the functionality that *you* are asking for then too many users might use it to allow their PCs to be a member of a bot-net or, at least, allow their PCs to be used by a 3rd party without their consent, and those outcomes are something they can't happily lift a finger towards.

Where this all-in-one solution does not exist, and a new user has installed using a reliably secure distro, they will either have to do something that they understand 'leaves their installation "nude"' or they will have to learn how to use the existing to reach their goal - from the 'altruistic standpoint' this is better than giving anybody a potentially false sense of security.



To be honest, I expect that I could churn out a GUI wrapper for the existing tools (my choice of a set of those tools, a bigger problem in itself - "which are the best tools to focus on for 'the solution'?") in about six~twelve months of really diligent study and application - when I released it I would include in the README that users shouldn't just blindly trust my judgement and then my code because I know that the tools for which I have provided 'GUI Wrapping' are evolving and no matter how diligent I am I could have missed something *important*...

How many people would just take my 'solution' and use it in blind faith, having never read the TOS/README. How would I feel if (something like) three months later I was just reviewing my code (reminiscing, worrying, gloating - lot's of reasons) and saw a major flaw that could render all security, on a machine relying on my wrapper of the existing tools, absolutely null and void *silently* - never warning or indicating (even to a tech, let alone novice) that it was 'nude' ?

To be brutally honest; when I really want something coded, for the convenience of using it myself or for the kudos of supplying (usually fairly specific) demand, I usually produce it in a startlingly short period of time - someone would have to offer me AUD350 an hour to even contemplate taking on this kind of *challenge* and I'd be making people I know and trust review **all** of my source code and test the 'solution' **vigorously** before I released the first beta - then I'd be watching my feedback channels as stressed as hell.


Not much of an example, in the scheme of things, that I can code but if you think you've been reading a liar/exaggerator  then please visit robsfreespace.com/software/free-basic-games/ and forgive me that they are from my Windows dependency days - I've been fairly seriously engaged by "9-5" from before I fully transited my workstation(s) to Linux and my 'serious' work is *usually* to sole recipients to whom I grant all rights over the binaries in situations where selling the 'product' would not be advantageous for them...

---

### Post by opendoors on 2011-03-13
For anyone still reading this thread, I actually posted this a while ago, but different topics were dominating the discussion at the time. What do you think of this?

[http://www.linux-firewall.org/](http://www.linux-firewall.org/)

Now of course I don't buy that it can deal with situations in which you've been rooted, but how does it look for everything else? (e.g. for people who want to control their bandwidth usage).

I'm not sure what license it is under, but it is in the repositories, so it might be worth a look. Is it open source? And any comments from the security experts like bodhi.zazen?

Someone in another thread mentioned Leopard Flower as a firewall capable of application filtering as well:

[http://sourceforge.net/projects/leopardflower/](http://sourceforge.net/projects/leopardflower/)

However, Leopard Flower seems to be in a very early stage of development.

---

### Post by HermanAB on 2011-03-14
Well, a GUI (interactive) firewall is mostly a waste of time.  I certainly don't want to sit and look at the network traffic going into and out of my systems all day long and watching thousands of machines in a data centre, or on client sites around the world, is simply impossible. I have better things to do than sit and stare at network traffic.  

A properly configured and hardened system should be able to run for several years, till the hardware eventually fails, without any incidents.

That is why most experienced guys around here don't want to hear about these 'mickey mouse' firewall ideas - they are impractical, cannot work in an industrial setting and are a total waste of time, even for a home user.

So, the best suggestion is to properly harden your system, then relax and forget about the network issues.  Out of the box, Ubuntu is sufficiently hardened for home users and if you are not a Home user, then you already know what to do...

'Hope that helps!

---

### Post by robsoles on 2011-03-14
> **opendoors said:**
> For anyone still reading this thread, I actually posted this a while ago, but different topics were dominating the discussion at the time. What do you think of this?

[http://www.linux-firewall.org/](http://www.linux-firewall.org/)

Now of course I don't buy that it can deal with situations in which you've been rooted, but how does it look for everything else? (e.g. for people who want to control their bandwidth usage).

I'm not sure what license it is under, but it is in the repositories, so it might be worth a look. Is it open source? And any comments from the security experts like bodhi.zazen?

Someone in another thread mentioned Leopard Flower as a firewall capable of application filtering as well:

[http://sourceforge.net/projects/leopardflower/](http://sourceforge.net/projects/leopardflower/)

However, Leopard Flower seems to be in a very early stage of development.

Assuming we can review it's source code and compile it ourselves (a usual trait of being hosted by sourceforge.net) I don't mistrust and despise leopardflower *as much* as I do linux-firewall - looks exactly the kind of crap I'm capable of; all closed source and disclaimers...

> **linux-firewall.org homepage][FONT=sans-serif][COLOR=#ff0000][COLOR=Black]When starting the download, you agree that you are not allowed to copy or modify this software. We will not guarantee that this program works correctly.[/COLOR][/COLOR][/FONT][/quote][FONT=sans-serif][COLOR=#ff0000][COLOR=Black]

But then, HermanAB made some really good points said:**
> [/COLOR][/FONT][QUOTE=HermanAB;10557845]Well, **a GUI (interactive) firewall is mostly a  waste of time**.  I certainly don't want to sit and look at the network  traffic going into and out of my systems all day long and watching  thousands of machines in a data centre, or on client sites around the  world, is simply impossible. I have better things to do than sit and  stare at network traffic.  

**A properly configured and hardened system should be able to run for  several years, till the hardware eventually fails, without any  incidents.**

That is why most experienced guys around here don't want to hear about  these 'mickey mouse' firewall ideas - they are **impractical**, **cannot work  in an industrial setting** and **are a total waste of time, even for a home  user**.

So, the best suggestion is to properly harden your system, then relax  and forget about the network issues.  **Out of the box, Ubuntu is  sufficiently hardened for *home users*** and if you are not a Home user,  then you already know what to do...

...

---

### Post by bodhi.zazen on 2011-03-14
> **HermanAB said:**
> Well, a GUI (interactive) firewall is mostly a waste of time.  I certainly don't want to sit and look at the network traffic going into and out of my systems all day long and watching thousands of machines in a data centre, or on client sites around the world, is simply impossible. I have better things to do than sit and stare at network traffic.  

A properly configured and hardened system should be able to run for several years, till the hardware eventually fails, without any incidents.

That is why most experienced guys around here don't want to hear about these 'mickey mouse' firewall ideas - they are impractical, cannot work in an industrial setting and are a total waste of time, even for a home user.

So, the best suggestion is to properly harden your system, then relax and forget about the network issues.  Out of the box, Ubuntu is sufficiently hardened for home users and if you are not a Home user, then you already know what to do...

'Hope that helps!

+1

This is why you would need to use something like snort to monitor you network traffic, to sift thought the thousands of connections and alert you to things to check.

Be warned, snort tends to throw false positives as well.

---

### Post by doas777 on 2011-03-14
> **HermanAB said:**
> Well, a GUI (interactive) firewall is mostly a waste of time.  I certainly don't want to sit and look at the network traffic going into and out of my systems all day long and watching thousands of machines in a data centre, or on client sites around the world, is simply impossible. I have better things to do than sit and stare at network traffic.  

A properly configured and hardened system should be able to run for several years, till the hardware eventually fails, without any incidents.

That is why most experienced guys around here don't want to hear about these 'mickey mouse' firewall ideas - they are impractical, cannot work in an industrial setting and are a total waste of time, even for a home user.

So, the best suggestion is to properly harden your system, then relax and forget about the network issues.  Out of the box, Ubuntu is sufficiently hardened for home users and if you are not a Home user, then you already know what to do...

'Hope that helps!


I'm sorry, but it seems like you are saying that because the app they want isn't right for you, that no one should pay any attention to them. this general attitude is pretty offensive to those on the opposite side, so please don't be so blasse about it.

---

### Post by SeijiSensei on 2011-03-14
I hate getting involved in flame wars, but I'm puzzled how any sort of ZoneAlarm type of system could even work in a multi-user environment like Linux.  If I'm an ordinary user, I won't be able to control applications running with root privileges or processes running as users other than myself.  A Linux system could be running dozens of processes owned by many different users.  How could a single application-level "firewall" even begin to work in this type of environment?

If you really care about these things, you need to get down and dirty with something like AppArmor or SELinux.

---

### Post by tgm4883 on 2011-03-14
> **SeijiSensei said:**
> I hate getting involved in flame wars, but I'm puzzled how any sort of ZoneAlarm type of system could even work in a multi-user environment like Linux.  If I'm an ordinary user, I won't be able to control applications running with root privileges or processes running as users other than myself.  A Linux system could be running dozens of processes owned by many different users.  How could a single application-level "firewall" even begin to work in this type of environment?

If you really care about these things, you need to get down and dirty with something like AppArmor or SELinux.

It could show current user processes with the option for root processes as well. Any changes that needed made would require admin password.

:EDIT: The application could also be just a frontend for UFW/IPtables that shows current unauthorized traffic. :/EDIT:

To some of the previous posters, this would be something for home users. Corp users would have configuration done by the admin and the machines locked down. For home users, yes, An Ubuntu OOTB installation is pretty secure. But as soon as you start installing things, applications start listening on ports, attempting outbound connections, etc. The more you install, the less secure your machine is. This type of firewall would help the less technical users keep their machine more secure by being more of a visual aid in showing what application was requesting internet access and allowing the user to make the decision if the application is allowed.

---

### Post by opendoors on 2011-03-14
[QUOTE=HermanAB]Well, a GUI (interactive) firewall is mostly a waste of time.  I certainly don't want to sit and look at the network traffic going into and out of my systems all day long and watching thousands of machines in a data centre, or on client sites around the world, is simply impossible. I have better things to do than sit and stare at network traffic.  

A properly configured and hardened system should be able to run for several years, till the hardware eventually fails, without any incidents.

That is why most experienced guys around here don't want to hear about these 'mickey mouse' firewall ideas - they are impractical, cannot work in an industrial setting and are a total waste of time, even for a home user.

So, the best suggestion is to properly harden your system, then relax and forget about the network issues.  Out of the box, Ubuntu is sufficiently hardened for home users and if you are not a Home user, then you already know what to do...

'Hope that helps![/QUOTE]

With all due respect, HermanAB, I find it hard to believe how anybody could possibly agree with your completely contradictory post. My purpose in using a GUI firewall would not be to stare at network traffic, but to let IT do the job for me. If I just wanted to look at traffic, I wouldn't use a GUI firewall. I would just type in a command in the terminal and sit there 24/7. But of course nobody wants to do that. We all have better things to do, don't we? Your first argument is basically: "I have better things to do than stare at network traffic all day. Therefore, I'm going to avoid using something that frees me from this task."

Your argument about impracticality is just as self defeating. Let's look at it again: "they are impractical, cannot work in an industrial setting and are a total waste of time, even for a home user." First of all, not everyone works in an industrial setting, and secondly, you just claimed that having to stare at network traffic all day was a waste of time. So now something that saves you that time is a waste of time too? Yeah, these arguments sure make a lot of sense.

Wake up. You're not the only one in the world with better things to do than stare at network traffic all day. Why do you think I made this thread in the first place? Partly so that we don't have to stare at network traffic all day, then figure out what to block! Maybe you should have read post #3 before replying. Clearly, you didn't.

This is the kind of stuff new Linux users are hoping NOT to find when they first enter a new community. Instead of productive discussion, they find offensive and bigoted posts that make absolutely no sense at all. Linux operating systems may be far superior to Windows and Mac, but if everyone in your community has your attitude, HerbertAB, then you will be the only one to know about it, because nobody else will want to join such a hostile community. Imagine if someone came across this thread a year from now while Googling for some topic related to this thread. What would they think if they saw your post? There are people who haven't even bothered to register, and you're sending them the wrong message before they make even that important decision. I suppose it's hard to refrain from such abuses when most of the community is simply so vehemently opposed to the mere *possibility* that an application firewall might be of some use in certain situations.

But back on topic. I saw the same red flag as robsoles did, and I mentioned it in an earlier post in this thread. I think even if it was an open source product, it wouldn't allow anybody to modify the source, which is a huge problem (you're allowed to see all the problems, but not fix them! Only we have that exclusive privilege!) That's why I hesitated to use linux-firewall.org. But I guess its existence (along with the Sourceforge.net hosted Leopard Flower) demonstrates that this type of filtering is at least possible. I think Leopard Flower may be worth watching. Its license is "public domain" according to Sourceforge. I'm not a legal expert; does anybody know what this means for what we can do with the source? (the source is offered for download on Sourceforge).

Like I said, even if I'm willing to block everything from Internet access, then allow things one by one as determined by Wireshark/whatever logs, I still need an effective blocking mechanism, and I don't think one exists right now. Can apparmor/selinux/grsecurity block by application instead of IP/port? These were mentioned earlier, but I don't think any of them can actually do such blocking. Apparmor seems to restrict what an application can do to important system files, but not prevent it from accessing the Internet. selinux may allow blocking by port at most, as does gufw. Finally, grsecurity does TCP/UDP blackholing, but not the type of filtering that we're discussing.

So as things stand, it looks like there are ways to tell what's connecting out (tcpdump, Wireshark, snort, iptables), but no way of blocking anything from connecting out (please correct me if I'm wrong), much less being selective about it. Sorry, turning off my computer when I'm not using it is not really an answer. Things can connect out all the time, whether or not I need it.

---

### Post by CandidMan on 2011-03-14
I don't know anything about programming except that it exists.

But, do some programs completely lack the ability to establish network connections? As in the actual capability isn't included in the source code and the finished product.

If that's the case then would it be possible to remove network capability beyond localhost when a program's being installed?

Sorry about the generalities. Not so 1337 :D

---

### Post by robsoles on 2011-03-14
> **CandidMan said:**
> I don't know anything about programming except that it exists.
Fair enough.> **CandidMan said:**
> 
But, do some programs completely lack the ability to establish network connections? As in the actual capability isn't included in the source code and the finished product.
 Plenty of programs out there that either don't connect at all or only  connect for their obvious purpose the user has put them to.> **CandidMan said:**
> 
If that's the case then would it be possible to remove network capability beyond localhost when a program's being installed?
 At it's most clumsy: You could unplug your ethernet lead or select 'disconnect' regarding your wireless connection - fair sure thing nothing is going to connect behind your back :roll:> **CandidMan said:**
> 
Sorry about the generalities. Not so 1337 :D
Me neither really.

---

### Post by CandidMan on 2011-03-14
Okay, thanks, that's what I thought.

In that case, the way I see the issue is that the OP doesn't care so much about how and where a program connects to the network but that it does in the first place

In short they don't care about the whys and the wherefores, they just a kill-switch for network access.
Is that a fair assessment?

That's why I asked about network capabilities in the source code

---

### Post by HermanAB on 2011-03-15
> Can apparmor/selinux/grsecurity block by application instead of IP/port?

Yes of course they can and iptables can too. I gave an example somewhere already.

There is no shortage of GUIs for firewalls, but if you are not satisfied by the defaults, then you need to learn how to craft your own rules.  

Linux is not unfriendly, it is just a little choosy about who exactly its friends are...

---

### Post by wdtd on 2011-03-15
Quote:
                                                 > Can apparmor/selinux/grsecurity block by application instead of IP/port?                      As I understand it, IPtables can filter by users and groups, not by the  application, so you will have to set each application you want to secure to run as a  specific user or group and filter it that way with IPTables. (Linux is  very strong when it comes to user and group control.) HermanAB's post earlier has an example of that method.

And/Or you need to make/run an Apparmor profile for each application you want to secure.

What  would be really nice is to have a "default" Apparmor profile that would be used by everything that didn't have profile but I don't think that is  currently possible. Maybe I am wrong though :)

---

### Post by doas777 on 2011-03-15
> **wdtd said:**
> Quote:
                                                 As I understand it, IPtables can filter by users and groups, not by the  application, so you will have to set each application you want to secure to run as a  specific user or group and filter it that way with IPTables. (Linux is  very strong when it comes to user and group control.) HermanAB's post earlier has an example of that method.

And/Or you need to make/run an Apparmor profile for each application you want to secure.

What  would be really nice is to have a "default" Apparmor profile that would be used by everything that didn't have profile but I don't think that is  currently possible. Maybe I am wrong though :)

IPTables and AppArmor/SelLinux are very different tools with very different purposes within the security stack.

IPTables filtering works on data contained in datagram headers including items like protocol (ICMP/TCP/UDP/etc), port number (which does in fact imply an application), and source/destination. it does not however function based on users/groups. network flows do not have a "user" associated with them, because users are system-specific, and network flows by very definition transcend systems.

apparmor/sellinux and other MAC-sublayers control what applications can do on your system. for instance a aa profile for firefox might constrain it to use only a handful of local directories, within the users home, so that no matter what kind of browser malware you might encounter, it can;t affect anyone but your user.

---

### Post by wdtd on 2011-03-15
[http://bodhizazen.net/Tutorials/iptables#Additional_Tips](http://bodhizazen.net/Tutorials/iptables#Additional_Tips) 

> **Limit network access**

 by user / group
 Use the owner module
 This module applies to **locally generated packets**, not incoming or  forwarded packets, and is thus used in the **OUTPUT (filter) chain**.
 You may specify a user/group by name, uid, or gid.  In the following examples I use the group "net" to demonstrate  restricting access to root and members of the group "net". "net" is  a custom group and you will need to create this group and add members to it.
 General syntax:
-m owner --uid-owner 0
-m owner --uid-owner root
-m owner --gid-owner net


I also think we are approaching the end of the days where which application is accessing the Internet can be determined by port only. Lots of connections go through port 80.

---

### Post by cariboo on 2011-03-15
Port 80 is only used for incoming/outgoing connections when you have a web server installed. I check regularly, and I've never seen anything outgoing on port 80 on a standard desktop installation.

---

### Post by bodhi.zazen on 2011-03-15
> **wdtd said:**
> And/Or you need to make/run an Apparmor profile for each application you want to secure.

Apparmor is nice, but the downsides are:

1. Lack of graphical tools.

2. One needs to write profiles, and this is simply inefficient.

If you want such tools I highly advise :

1. pax/grsecurity. This will require you patch an compile a custom kernel, but it is otherwise very nice.

2. I go with selinux, and this means Fedora 14. Selinux is quite mature and there are graphical tools available.

---

### Post by KonfuseKitty on 2011-03-15
> **tgm4883 said:**
> It could show current user processes with the option for root processes as well. Any changes that needed made would require admin password.
*
:EDIT: The application could also be just a frontend for UFW/IPtables that shows current unauthorized traffic. :/EDIT:
*
To some of the previous posters, this would be something for home users. Corp users would have configuration done by the admin and the machines locked down. For home users, yes, An Ubuntu OOTB installation is pretty secure. But as soon as you start installing things, applications start listening on ports, attempting outbound connections, etc. The more you install, the less secure your machine is. This type of firewall would help the less technical users keep their machine more secure by being more of a visual aid in showing what application was requesting internet access and allowing the user to make the decision if the application is allowed.


I wasn't going to post here again, but I must say a big thank you to tgm4883 for his post. He summed it up perfectly and has restored my confidence in the Ubuntu team. Greatly appreciated!

---

### Post by norseman-has-a-laptop on 2011-03-15
> **scorp123 said:**
> And why should you even need to?? This is not Windows here :)

I use Linux since 1996 and never had any problem with programs doing strange things behind my back :D

Let go of your Windows ways.
yes...join us join us

---

### Post by nogoodnamesleft on 2011-03-16
> **opendoors said:**
> For anyone still reading this thread, I actually posted this a while ago, but different topics were dominating the discussion at the time. What do you think of this?
[http://www.linux-firewall.org/](http://www.linux-firewall.org/)


1) Is there source code it? If not, WHY NOT?

2) Currently, application firewalls are snake oil - unless you are playing cracked online games and want to keep your game account and virtual gold safe. (For those unfamiliar with the concept, online games require the use of a user account; pirated online games often contain keyloggers to steal said user accounts).

First, I can think of better platforms than Linux to use for windows games.

Second, you need to allow the game to connect to the Internet *anyway* so how exactly will an application firewall help? Do you want to allow OnlineGame to connect to the Internet? (Yes/No) [most of them dont list the address]

Third, OK he injected his code into a different process. OK. That's a valid concern. That's what I would do. So just block every IP/connection except the game binaries, to the game's servers, while running the game, and you're fine. While not running the game, if WINE was still up, that would be kinda obvious ...

Multi-platform exploits? Possible but highly unlikely at the current moment in time. You have to draw the line somewhere. Do you check your keyboard for added hardware each time you return to your PC?

3) Also you keep saying you are leaving, but then you keep coming back. This does little for your credibility.

4) The type of user who clicks OK to "Do you want to  download game.exe (y/n)" from a popup on a pirate site is going to get malware no matter what technical measures are in place.** Security requires user education in addition to technology.**

5) This being said I can see application firewalls becoming useful in the future for people running Android mobile apps etc in Linux, but right now there doesn't seem to be much need. Even Apple "we police the app store" has had problems with rogue iPhone and iPad apps phoning home (or people copying a legit app and re-listing it under a different name with added ID Theft code), so the time will come, but in all honesty, Linux can already deal with most or all of it, if correctly configured and the user is educated.

However Ubuntu being "linux for humans", if/when the need for an application firewall arises, I'm sure canonical will do something about it, that doesn't require the user to type commands in a terminal - even if that thing is just user education.

6) app firewall don't stop well written malware anyway.

---

### Post by arapaho on 2011-03-16
> **nogoodnamesleft said:**
> 4) ** Security requires user education in addition to technology.**

However Ubuntu being "linux for humans", if/when the need for an application firewall arises, I'm sure canonical will do something about it, that doesn't require the user to type commands in a terminal - even if that thing is just user education.


User education doesn't contradict existance of easy to use programs. 

"Super-fast and great-looking, Ubuntu is a secure, intuitive operating system that powers desktops, servers, netbooks and laptops. Ubuntu is, and always will be, absolutely free." 
[http://www.ubuntu.com/](http://www.ubuntu.com/)

1) Apparmor, SElinux, Snort etc. are not intuitive at all! 
2) Ubuntu by default is not very secure if users are suggested to use Apparmor etc. This especially refers to Internet security.

---

### Post by wdtd on 2011-03-16
I have submitted a [needs packaging] request for Leopard Flower here [https://bugs.launchpad.net/ubuntu/+bug/736258](https://bugs.launchpad.net/ubuntu/+bug/736258) for those Ubuntu users who would want to use such a program but keep within the safe Repositories.

That is the great thing about Open Source and Ubuntu, if you don't want to use it, you probably don't have to.

---

### Post by arapaho on 2011-03-16
I submitted question on ubuntu-hardened -- Ubuntu security discussion mailing list:
[https://lists.ubuntu.com/archives/ubuntu-hardened/](https://lists.ubuntu.com/archives/ubuntu-hardened/)

[https://lists.ubuntu.com/archives/ubuntu-hardened/2011-March/000541.html](https://lists.ubuntu.com/archives/ubuntu-hardened/2011-March/000541.html)
I'm especially curious what is Canonical's point of view. I'm sure they realize that if they want more market share, an easy to use Internet control solution would be an advantage.

---

### Post by cariboo on 2011-03-16
I'm not sure what you mean by easy to use. If you mean like the way Windows firewalls work, where they pop up a windows saying foo wants to access the internet, what do you want to do, that may be easy to use, but look at all the problems it causes in Windows, where most users just click OK or cancel to get the window out of the way. 

Security should not be passive, the user should take an active role in securing their system.

---

### Post by robsoles on 2011-03-16
> **cariboo907 said:**
> ...

Security should not be passive, the user should take an active role in securing their system.

Unfortunately, it seems, most people are lazy and will be wanting someone else to do it for them - those who 'grew up' with Windows without learning much of the nitty gritty of networking are especially prone to feeling positive someone else should do it for them.

Most Windows immigrants must find it very hard to accept that if they install Ubuntu and just work out of the repositories then someone else literally did do it for them and if they get stuff from outside of the repositories it is not that awkwardly difficult to test and secure it if it has a valid purpose but does some 'behind user's back' reporting or similar.

Education is the way but some people never accept facts no matter how much you ram them down their throat - I've known people to deny obvious truths I have demonstrated and (probably) about half seem to discover that I was showing and telling the truth by some other revelation (sometimes much later) and the other half just crash on regardless.

The point about 'just clicking OK or CANCEL to make the prompt go away, without really understanding whether or not that is a valid connection they are allowing or denying, is rather valid in my opinion - not willing to learn the necessary and take proper charge of it then unlikely to benefit from somebody 'doing it that way' for them :roll:

---

### Post by nogoodnamesleft on 2011-03-16
Sure some people just click "whatever" to make the security popup disappear, then turn it off so it doesn't bother them - as/if the internet becomes more important and everything is connected, that would be like not obeying a medical quarantine and killing half the city(!)

Users must be educated to recognise threats and the basic things to do to keep their own computers secure - exactly the same way as they are educated not to drink dirty water or spread contagious diseases.

I am not saying don't make firewall software.

I am saying that user education must go hand in hand with it, or it's not going to work and at some time in the future there is a chance it might be compulsory.

I bet most trojans are picked up via social engineering and firewalls won't do anything against that.

---

### Post by wdtd on 2011-03-16
Easy to me means I don't need to setup IPtables or Apparmor profiles for *everything* I think I may need to prevent having from Internet access. Easy means I don't have to dig through the preferences of every program *everytime* I want to turn on or off its Internet functionality. Easy means not having to setup Snort for a laptop.

Easy means having notifications pop up to "hey look at this" the same way I have for my system temperatures, new email, and new Ubuntu updates. Easy means looking in one spot to turn off and back on Internet functionality for various programs instead of many.

The type of person who would install this application is not the kind of person who would just "click through" without looking. If you care enough to install it, you will care enough to look at the notification and make an informed decision if that program should be accessing the Internet at this time. I see this as *another tool* like adding electronic stability control in addition to the already installed antilock brakes, airbags, and seat belts.

Remember that a program like this can be used for multiple purposes.
1) Easily restrict Internet usage when you are close to bandwidth limits or using pay-per-use access.
2) Easily restrict programs you don't want to run on certain networks (no IRC when on the work LAN) but do on other networks.
3) Help troubleshoot network/bandwidth problems ... what program is auto-running on port 80 according to UFW?
4) Act as an additional layer of protection for incorrect or accidentally program setup that they might not otherwise discover until too late.

---

### Post by nogoodnamesleft on 2011-03-17
> **wdtd said:**
> The type of person who would install this application is not the kind of person who would just "click through" without looking. If you care enough to install it, you will care enough to look at the notification and make an informed decision if that program should be accessing the Internet at this time.

Not necessarily true - the difference here is that you know what you are doing, but not everyone else does, and that the number of rows returned by "select * from users where clue = 0" will only increase as Ubuntu gains popularity.

The growth of Linux and the greater accessibility of newer distros (GUI installers, package managers) mean we can't really make any assumptions as to the technical competency of Linux users any more, and to do so might be irresponsible.

People install stuff because they were told to, or because it came installed, or they click through because they don't understand how it works and thinks it just protects them like magic. In the case of a 2 way app firewall, which we are discussing, gaga users who have no idea are going to install that because they think it will protect them and because almost every PC has one.

---

### Post by arapaho on 2011-03-17
> **cariboo907 said:**
> Security should not be passive, the user should take an active role in securing their system.

Sure, I agree. But the tools should be easy. I looks like you are worrying about people compromising their own system because they will make stupid things. I'm sure situation will be no worse then now when most users are just told to enable Gufw and don't worry. So they block outgoing and they don't care about other security problems. Isn't it passive? It's up to the user to decide how he/she takes care about security. The program they use easy or not easy is another story.

In windows security is not passive either. User has to think about what to block or not. If he/she makes stupid things that's not my problem. But at least on windows there are easy to use tools. Firewalls can be setup properly and provide both incoming and outgoing security in an easy way. In Ubuntu there are no easy, intuitive tools.

It all comes down to how this program can be developed. I just want to have more functionality with easy tools. And it doesn't contradict learning. 
This discussion seems crazy to me. One side tells give us easy to use program, other don't give them.
If you don't want a new program just don't worry, don't use it, stick to apparmor.

I don't mind to have program "select from" if it tells select from what...

> **nogoodnamesleft said:**
>  gaga users who have no idea are going to install that because they think it will protect them
The same with Gufw. And it protects. Doesn't it? And it is easy. Isn't it? But it lacks functionality.

\\:D/ Please, vote: \\:D/
[[IMG]http://brainstorm.ubuntu.com/idea/26902/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/26902/)

---

### Post by bodhi.zazen on 2011-03-17
You should use Fedora 14.

selinux is enabled by default and it is as easy as it gets, there are several graphical tools to manage any problems you might have.

With that said, problems with selinux are rare and applications such as firefox are confined by selinux.

If you wish, use xguest.

[http://www.linuxtopia.org/online_books/fedora_selinux_guides/fedora_10_selinux_user_guide/fedora_10_selinux_sect-Security-Enhanced_Linux-Confining_Users-xguest_Kiosk_Mode.html](http://www.linuxtopia.org/online_books/fedora_selinux_guides/fedora_10_selinux_user_guide/fedora_10_selinux_sect-Security-Enhanced_Linux-Confining_Users-xguest_Kiosk_Mode.html)

---

### Post by wdtd on 2011-03-17
>  People install stuff because they were told to, or because it  came installed, or they click through because they don't understand how  it works and thinks it just protects them like magic. In the case of a 2  way app firewall, which we are discussing, gaga users who have no idea  are going to install that because they think it will protect them and  because almost every PC has one.Wouldn't the above  kind of user be the same one who would be engaging in so much other risky behavior anyway that a simple application-based firewall they ignore doesn't matter?

They turn on services without securing them, login as root, have UPnP activated on their router then enable Remote Desktop to access their home PC at work, download some random .deb on the web, and type "sudo r ](*,) -rf /" because an IM told them so. Saying that Ubuntu is so secure that it doesn't need a firewall might be giving them as much of a false sense of security as giving them tools like an outgoing application-based firewall and GUFW.

[FONT=Tahoma][SIZE=3][SIZE=2]New users: Ubuntu is secure if you don't turn on any services, only use the Ubuntu Repositories, and update regularly. Period. The other tools are for experienced computer geeks and server machines[/SIZE].[/SIZE][/FONT]

---

### Post by tgm4883 on 2011-03-17
> **bodhi.zazen said:**
> You should use Fedora 14.

selinux is enabled by default and it is as easy as it gets, there are several graphical tools to manage any problems you might have.

With that said, problems with selinux are rare and applications such as firefox are confined by selinux.

If you wish, use xguest.

[http://www.linuxtopia.org/online_books/fedora_selinux_guides/fedora_10_selinux_user_guide/fedora_10_selinux_sect-Security-Enhanced_Linux-Confining_Users-xguest_Kiosk_Mode.html](http://www.linuxtopia.org/online_books/fedora_selinux_guides/fedora_10_selinux_user_guide/fedora_10_selinux_sect-Security-Enhanced_Linux-Confining_Users-xguest_Kiosk_Mode.html)

So if I want a secure distro (or at least a distro that meets my security needs), I shouldn't use Ubuntu?

> **wdtd said:**
> Wouldn't the above  kind of user be the same one who would be engaging in so much other risky behavior anyway that a simple application-based firewall they ignore doesn't matter?

They turn on services without securing them, login as root, have UPnP activated on their router then enable Remote Desktop to access their home PC at work, download some random .deb on the web, and type "sudo r ](*,) -rf /" because an IM told them so. Saying that Ubuntu is so secure that it doesn't need a firewall might be giving them as much of a false sense of security as giving them tools like an outgoing application-based firewall and GUFW.


The type of firewall in discussion here isn't for that type of user. It's for the user that actually wants to be secure and know what is happening on their systems. 

> **wdtd said:**
> 
[FONT=Tahoma][SIZE=3][SIZE=2]New users: Ubuntu is secure if you don't turn on any services, **don't install any additional software**, and update regularly. Period. The other tools are for experienced computer geeks and server machines[/SIZE].[/SIZE][/FONT]

I fixed your comment for you.


When I install an application, it is because I want to use it. I don't want to read through each bit of documentation looking for what ports it might be listening on. I don't want to test the software in a test environment for a week checking to see if it is listening on any undocumented ports, or making any outgoing connections without my approval. The assumption that the people who are against this type of firewall are making is that Ubuntu is secure, and if you stick to the repositories it will remain secure. There are two flaws to this argument.

1) This assumes that software in the repository doesn't listen on any ports. This simply isn't the case, as there is a lot of software in the repos that listens for incoming connections and can make outgoing connections.

2) This assumes that all software in the repos has had a thorough security inspection. This also is simply not the case. The REVU process is basically checking that packaging is good and doesn't fail any of the predefined tests.

---

### Post by bodhi.zazen on 2011-03-17
> **tgm4883 said:**
> So if I want a secure distro (or at least a distro that meets my security needs), I shouldn't use Ubuntu?

You are obviously taking my comment out of context.

You should use the distro / tools that meets your security needs.

In the content of the comments in this thread, IMHO, Fedora meets the security requirements listed by several users in this thread in that selinux on Fedora is quite mature, works out of the box, and has graphical tools.

If you read the entire thread you will see that IMO, on Ubuntu, the best solution would be to use Apparmor.

The "problem" with apparmor, according to others, is basically that it is not enabled out of the box (for ALL applications) and that is it not "easy" which basically means graphical tools.

So, for you personally, Ubuntu may meet your needs, with or without apparmor, and that is fine. That does not mean Ubuntu meets everyone's needs or that others should not look at alternate solutions.

Along those lines, I do not know how much or little you know about Fedora, but if you have the time and/or interest, and you have not looked at the various security (selinux) features / graphical tools to manage selinux / xguest on Fedora you might want to look. If after looking you may decide Ubuntu is best for you, or you might change. But that does not mean your decision is best for everyone or that your decision is the only option.

---

### Post by tgm4883 on 2011-03-17
> **bodhi.zazen said:**
> You are obviously taking my comment out of context.

You should use the distro / tools that meets your security needs.

In the content of the comments in this thread, IMHO, Fedora meets the security requirements listed by several users in this thread in that selinux on Fedora is quite mature, works out of the box, and has graphical tools.

If you read the entire thread you will see that IMO, on Ubuntu, the best solution would be to use Apparmor.

The "problem" with apparmor, according to others, is basically that it is not enabled out of the box (for ALL applications) and that is it not "easy" which basically means graphical tools.

So, for you personally, Ubuntu may meet your needs, with or without apparmor, and that is fine. That does not mean Ubuntu meets everyone's needs or that others should not look at alternate solutions.

Along those lines, I do not know how much or little you know about Fedora, but if you have the time and/or interest, and you have not looked at the various security (selinux) features / graphical tools to manage selinux / xguest on Fedora you might want to look. If after looking you may decide Ubuntu is best for you, or you might change. But that does not mean your decision is best for everyone or that your decision is the only option.

Fedora was great when I used it last (admittedly, FC6) but I enjoy other things about Ubuntu much more. My point though, is not that Ubuntu is insecure, but that the tools provided aren't helping the main audience of Ubuntu. I agree that AppArmor is the way to go, and that we need to improve the tools available so that everyone can use them. Unfortunately it seems that while every Ubuntu release seems to focus on the shiny, there doesn't seem to be much of an effort to create tools that people can use. Sure everyone can dig though man pages and configure things via text file (heck, we even tell people to do that when offering instructions), but the issue is that text files and command lines aren't intuitive.

---

### Post by CandidMan on 2011-03-17
For those of you with the diligence and time to use SELINUX as opposed to Apparmor, I'm reading this article breaking down in layman's terms how SELINUX works.

[http://www.fosteringlinux.com/articles/selinux/selinux-part-1/](http://www.fosteringlinux.com/articles/selinux/selinux-part-1/)

I might consider switching if my paranoia goes beyond healthy

Also, anyone considered switching to OpenSuse. It has Yast, which is like an all-in-one admin tool

---

### Post by bodhi.zazen on 2011-03-17
> **CandidMan said:**
> For those of you with the diligence and time to use SELINUX as opposed to Apparmor, I'm reading this article breaking down in layman's terms how SELINUX works.

In general you do not need to fuss with selinux very often, for the most part it works out of the box.

If you want to modify a policy or if you install an application outside of the repos, change a default port (22 for example), then yes, that will take some work.

---

### Post by nogoodnamesleft on 2011-03-17
> **wdtd said:**
> [FONT=Tahoma][SIZE=3][SIZE=2]New users: Ubuntu is secure if you don't turn on any services, only use the Ubuntu Repositories, and update regularly. Period. [/SIZE].[/SIZE][/FONT]

Don't visit any websites either.

But, you say, that means my Ubuntu can never be secure unless I never turn it on! Well you're right. User education again: they need to know what they can and CANNOT click on. (Like obvious dodgy site). Ubuntu is a very good OS but implying it's 'safe' with loose criteria is the sort of comment leads to poor user education and people clicking on things at random, exactly the sort of user we want to avoid. This is also the sort of comment "its secure!" that leads to user sending all their stuff over public wifi and ID theft. (It's OK, it's secure! I updated and used only Ubuntu repository! They can't steal my identity over Wifi!)

I know you yourself know how to be secure and keep a secure system, but when there is need to communicate that to a user of unknown technical ability i believe one should avoid statements like "this system is secure".

---

### Post by opendoors on 2011-03-17
> **nogoodnamesleft]
1) Is there source code it? If not, WHY NOT?

2) Currently, application firewalls are snake oil - unless you are playing cracked online games and want to keep your game account and virtual gold safe. (For those unfamiliar with the concept, online games require the use of a user account said:**
> 

Third, OK he injected his code into a different process. OK. That's a valid concern. That's what I would do. So just block every IP/connection except the game binaries, to the game's servers, while running the game, and you're fine. While not running the game, if WINE was still up, that would be kinda obvious ...

Multi-platform exploits? Possible but highly unlikely at the current moment in time. You have to draw the line somewhere. Do you check your keyboard for added hardware each time you return to your PC?

3) Also you keep saying you are leaving, but then you keep coming back. This does little for your credibility.

4) The type of user who clicks OK to "Do you want to  download game.exe (y/n)" from a popup on a pirate site is going to get malware no matter what technical measures are in place.** Security requires user education in addition to technology.**

5) This being said I can see application firewalls becoming useful in the future for people running Android mobile apps etc in Linux, but right now there doesn't seem to be much need. Even Apple "we police the app store" has had problems with rogue iPhone and iPad apps phoning home (or people copying a legit app and re-listing it under a different name with added ID Theft code), so the time will come, but in all honesty, Linux can already deal with most or all of it, if correctly configured and the user is educated.

However Ubuntu being "linux for humans", if/when the need for an application firewall arises, I'm sure canonical will do something about it, that doesn't require the user to type commands in a terminal - even if that thing is just user education.

6) app firewall don't stop well written malware anyway.

1) Uh, yeah, that's kind of exactly what I said in post #78:

> **opendoors]
But back on topic. I saw the same red flag as robsoles did, and I  mentioned it in an earlier post in this thread. I think even if it was  an open source product, it wouldn't allow anybody to modify the source,  which is a huge problem (you're allowed to see all the problems, but not  fix them! Only we have that exclusive privilege!) That's why I  hesitated to use linux-firewall.org. But I guess its existence (along  with the Sourceforge.net hosted Leopard Flower) demonstrates that this  type of filtering is at least possible. I think Leopard Flower may be  worth watching. Its license is "public domain" according to Sourceforge.  I'm not a legal expert said:**
> 

2) Not everyone plays cracked online games (do you?). If they do, I don't think they're necessarily the same people that are asking for an application firewall. Stop trying to misrepresent the purpose of an application firewall in hopes of suppressing legitimate demands for one. It's not going to work. Many legitimate reasons for having an application firewall were already given.

A decent application firewall not only allows the user to define which application can access the Internet, but through which port and through which IP address or IP address ranges.

You **do** have to draw the line somewhere. If someone has physical access to your computer and can plant hardware keyloggers, it's over anyways. But this argument is pretty much the same as the rootkit argument. It basically says "if X happens, then an application firewall becomes useless". Well, yes, but this argument doesn't answer my point: "Under at least A, B, and C circumstances, an application firewall can be useful and effective. Therefore, it is necessary under at least those contexts".

3) After seeing people like you repeat the same ridiculous arguments over and over again, most reasonable people would be frustrated. When I did come back, I responded to posts that were made. Got a problem with that? Could it be because you don't want anyone pointing out the problems with your arguments? So much for your credibility.

4) Yes, security requires requires user education **in addition to** technology. Does this mean that said technology is useless because of user education? No. In fact I just noticed that arapaho made this point already:

[QUOTE=arapaho]User education doesn't contradict existance of easy to use programs. 


Here's an argument similar to yours: Safety on the road requires driver education in addition to safe cars. Therefore, if we can have driver education, we no longer need safe cars. See the problem now?

5) Well, many other uses for application firewalls were pointed out aside from mobile apps. Why don't we do something about those first?

6) See 2)

[QUOTE=cariboo907]I'm not sure what you mean by easy to use. If you mean  like the way Windows firewalls work, where they pop up a windows saying  foo wants to access the internet, what do you want to do, that may be  easy to use, but look at all the problems it causes in Windows, where  most users just click OK or cancel to get the window out of the way. 

Security should not be passive, the user should take an active role in securing their system.[/QUOTE]

See 4) above

[QUOTE=nogoodnamesleft]
I am not saying don't make firewall software.

I am saying that user education must go hand in hand with it, or it's  not going to work and at some time in the future there is a chance it  might be compulsory.
[/QUOTE]

First, however, we need the firewall software. Otherwise, what is there to educate users on? And nothing should be compulsory. Users install the firewall software if they want to educate themselves (or they could be very disappointed if they have unrealistic expectations). If they don't want to install it, nobody is forcing them to do it. But they should still have that choice.

[QUOTE=wdtd]
The type of person who would install this application is not the kind of  person who would just "click through" without looking. If you care  enough to install it, you will care enough to look at the notification  and make an informed decision if that program should be accessing the  Internet at this time. I see this as *another tool* like adding electronic stability control in addition to the already installed antilock brakes, airbags, and seat belts.
[/QUOTE]

Exactly. I have no doubt that physical access, having a rootkit  installed, or many other situations can easily bypass an application  firewall, and I install it with that in mind, in order to use it for its  intended purpose. I install it to give myself more control.

[QUOTE=nogoodnamesleft]Not necessarily true - the difference here is  that you know what you are doing, but not everyone else does, and that  the number of rows returned by "select * from users where clue = 0" will  only increase as Ubuntu gains popularity.

The growth of Linux and the greater accessibility of newer distros (GUI  installers, package managers) mean we can't really make any assumptions  as to the technical competency of Linux users any more, and to do so  might be irresponsible.

People install stuff because they were told to, or because it came  installed, or they click through because they don't understand how it  works and thinks it just protects them like magic. In the case of a 2  way app firewall, which we are discussing, gaga users who have no idea  are going to install that because they think it will protect them and  because almost every PC has one.[/QUOTE]

Yes, not **necessarily** true, but it does **not** have to be to justify the need for firewall software, because as long as there are some people who don't fall into your stereotypes (I can assure you that there are plenty), the need will exist. It doesn't matter how many times you and other people keep pointing out that "some" users blindly click through things. Some people don't want to drive cars. Does this mean cars should not exist?

---

### Post by nogoodnamesleft on 2011-03-18
> **opendoors said:**
> 
4) Yes, security requires requires user education **in addition to** technology. Does this mean that said technology is useless because of user education?

@opendoors: No it means we're trying to educate you into understanding how you don't need an application firewall right now, and how useless they are anyway. Specifically what have you installed or downloaded that needs it?

Some real examples please.

Cracked windows games don't count because you said you don't play them (and have been told how to stop them phoning home, anyway).

---

### Post by wdtd on 2011-03-18
> **nogoodnamesleft said:**
> Some real examples please.

I need a solution for both metered (pay-per-use/bandwidth caps) and unmetered internet access.  (BTW, AT&T is planning on putting caps on their DSL service too.) I also have ToS restrictions with some of my Internet access points.

I want to easily restrict/allow Internet access for some programs in situ depending on which Internet access I have and how close I am to to bandwidth caps. (For example, no IM on this client's network and no automatic podcast downloading when on mobile tethering.)

I would love the additional layer of notification for problems. (For example, accidentally set up a program to download every hour instead of every day.)

As an extra, it would be great to see which programs connect to the Internet when they try instead just during log review.

To achieve these goals with the current tools I have available means I go to another distro, setup IPtables or Apparmor profiles for *everything*  I think I may need to prevent having from Internet access, remember to dig through the preferences of every program *everytime* I want to turn on or off its Internet functionality, or setup some other advanced cumbersome system.

What I would love is one place to control Internet access for each program from and  receive notifications like I already have for my system temperatures, new email, and Ubuntu  updates.


And if it could make coffee in the mornings too, it would be absolutely perfect :D

---

### Post by opendoors on 2011-03-21
[QUOTE=nogoodnamesleft]@opendoors: No it means we're trying to educate you into understanding how you don't need an application firewall right now, and how useless they are anyway. Specifically what have you installed or downloaded that needs it?

Some real examples please.

Cracked windows games don't count because you said you don't play them (and have been told how to stop them phoning home, anyway).[/QUOTE]

If we both agree that cracked windows games "don't count", then why do you keep bringing them up? Not only were you the first to mention them, but you simply won't let the issue die, even when it is clear that nobody in this thread is interested in them except you. I know how fond you are of ripping off game publishers, but frankly, as much as I appreciate constructive comments and criticism, I think you should at least try to read some of my other responses to your first post before you try to "educate" me. All you're doing with your patronizing attitude is standing in the way of progress.

To wdtd's list, I add printer drivers (or, more generally, drivers for any hardware for which there is no open source alternative) and any program that provides no opt out for the phoning home of statistics and system information. But more importantly, there are specific things that are not just "installed or downloaded". For example, it would be useful to be able to filter any program by IP instead of just port (even to the point of allowing some IPs while denying others), and to do so quickly, easily, and efficiently, without having to combine 3-4 different tools. These are just a few of the functions that, imho, Linux could benefit from having.

And before you tell me that cracked games (your favorite example) or rootkits can render an application firewall useless, just remember that those 3-4 (or more) tools are all rendered equally useless. So if you're going to make that argument, either you concede that this partial list of needs is legitimate but that an application firewall is not the right way to meet those needs, or you claim that these needs are not needs at all. But yet, contrary to the latter case, there are people using such tools and wishing there was a more efficient way to do things. Right now, such a way doesn't exist.

---

### Post by The Cog on 2011-03-22
Here is a general question that puzzles me: 

Would you block wget from having internet access? By my understanding, if you block it, you can't perform software updates, or even check if any are available. If you don't block it, any old script can freely download anything it wants.

I have a feeling that "application firewalls" fundamentally won't work on *nix because applications aren't monolithic executables the same way they are on windows. A *nix application will make use of lots of existing tools such as wget or curl, whereas on windows, applications tend to be self-contained.

---

### Post by tgm4883 on 2011-03-22
> **The Cog said:**
> Here is a general question that puzzles me: 

Would you block wget from having internet access? By my understanding, if you block it, you can't perform software updates, or even check if any are available. If you don't block it, any old script can freely download anything it wants.

I have a feeling that "application firewalls" fundamentally won't work on *nix because applications aren't monolithic executables the same way they are on windows. A *nix application will make use of lots of existing tools such as wget or curl, whereas on windows, applications tend to be self-contained.

If you wanted to use wget directly, then yes, you would allow it.

An application firewall would look at the parent process of whatever called wget, and see if it was allowed access.

---

### Post by The Cog on 2011-03-22
Hmm, yes, but how far up the tree does that go? I mean, if you follow all the way up, **init** is the process that launched all the others. How do you know where to stop and treat a particular process as **the** program that you are trying to police?

I'm not trying to be awkward or play games, I really don't see an easy way for an application firewall to know what "the application" is. How to know if you should be policing a process, its parent, grandparent etc?

---

### Post by tgm4883 on 2011-03-22
> **The Cog said:**
> Hmm, yes, but how far up the tree does that go? I mean, if you follow all the way up, **init** is the process that launched all the others. How do you know where to stop and treat a particular process as **the** program that you are trying to police?

I'm not trying to be awkward or play games, I really don't see an easy way for an application firewall to know what "the application" is. How to know if you should be policing a process, its parent, grandparent etc?

There would actually be a few stopping points, where the process right below it would be the main process. (stopping points being init, /usr/bin/terminal, etc)

Looking at pstree I have things like chromium-browser, miro, and dropbox under init, so obviously those would be what the user should be notified about. Chromium-browser may take additional work if you wanted to get granular about plugins and such.

I also have a few bash scripts that require network access. These are showing up under init -> /usr/bin/terminal. Obviously we don't want to set /usr/bin/terminal as the main process, so the script below it would need to be the configured process. May need to base that on md5hash instead of just filename.

---

### Post by HermanAB on 2011-03-23
Howdy,

> Hmm, yes, but how far up the tree does that go? I mean, if you follow all the way up, init is the process that launched all the others.

This is exactly why a firewall rule should NOT look at the application PID, but rather at the user or group that the process is running as.  

This is why Daemons are launched as a special users.  For example Apache run as the apache user.  An FTP server runs as the ftp user.  In the same way, you can launch any program with its own group (using the sg command) and then use a simple iptables rule to filter on that group.  I have given an example of that way back at the front of this long and winding thread.

The netfilter tools already exist - you just need to use them.

---

### Post by robsoles on 2011-03-23
> **HermanAB said:**
> ...

The netfilter tools already exist - you just need to **use them**.

Exactly; trouble is that the majority of people who don't currently know how to use them would prefer to learn how to use them in terminal (or perhaps not) from behind the (at least perceived) safety of having a graphical manager for them that looks something like a full-on and enhanced Windows firewall.


I'm thinking more and more that it is a pity that the rate of change/updates for the tools, and the sheer complexity of some of their functionality, make it somewhat less likely that anybody will complete an all inclusive "Security Centre" for the GUI.

It is a bigger pity that through learning enough about the tools to make such a thing most people will decide it's better managed the way it is, in terminal by and large.


The people making points about new-comers and Windows refugees have won me over - I wouldn't use more of the GUI functionality of a 'Security Centre' than mostly checking that the last rule for each form of network traffic was 'drop' but funnily enough I don't bother with gufw (or any other) because they don't seem as strong an interface to the tools as just opening terminal is :roll:


Some people may not appreciate me *even* putting it this way, but: Releasing the GUI/Destop versions of the best OS (in my humble opinion = Ubuntu) without an extensive and integrated GUI wrapper for the excellent security tools that are already 'under the hood', particularly to offer to new-comers and (especially) Windows converts/refugees, is *a bit ordinary*.

On the other hand though, it would aggravate me terribly if the tools were extensively re-written to better suit management by a GUI interface and it made managing the tools uglier (or inaccessible) in terminal.


Now, just before anybody has a go at me for *anything* in particular: I realise the majority of *my* sentiments/ideas I express in this post have already been posted. I am very very *ordinary* and am practically nobody and a nothing; Certainly by comparison to anybody who contributes, in any way at all, to bringing us Ubuntu or even this forum - thanks for reading.

---

### Post by Duncan Williams on 2011-03-26
This is one my first posts since moving to ubuntu from windows a couple of weeks ago.
The original post in this thread *`I need an outbound GUI software firewall'*  is a valid request and the basic reasons were given.
After reading through this thread (which I find quite long) there seems to be a focus on ubuntu not needing security software.

If the op wants to setup control of any outbound traffic for his own reasons then that is all that is relevant.

At some stage cloud based security software will be available and needed by the linux community.

It is not overdressing to have what the op is asking for.

In fact in general use:
A good effective linux only anti-virus solution.
A fully configurable firewall (in/out traffic)
A comprehensive network monitoring solution.
would be good tools and realtime benefits for a lot of users.

the way things are going:
[http://en.wikipedia.org/wiki/Linux_malware](http://en.wikipedia.org/wiki/Linux_malware)

the way things are going: (nearly cloud-based anti-malware for linux.
[http://apps.facebook.com/bd-safego/](http://apps.facebook.com/bd-safego/)

---

### Post by CandidMan on 2011-03-26
> the way things are going: (nearly cloud-based anti-malware for linux.
[http://apps.facebook.com/bd-safego/](http://apps.facebook.com/bd-safego/)

Not sure I get this. Surely that's a facebook/user problem not a Linux problem. That app is only meaningful on Facebook. What about the rest of the web?
I could click on hundreds of links and make stupid decisions online, but that would ruin my privacy not my security.
Having said that, I guess in certain situations there are merits to having this outbound GUI firewall + antivirus.
[]("http://apps.facebook.com/bd-safego/")

---

### Post by Duncan Williams on 2011-03-26
Safego is an example of a malware deterent that is basically cross platform and cloud based.

As more virus, trojans, worms possibly occur for linux the problem needs addressing:
[http://en.wikipedia.org/wiki/Linux_malware#Threats](http://en.wikipedia.org/wiki/Linux_malware#Threats)

---

### Post by SeijiSensei on 2011-03-26
> **Duncan Williams said:**
> [http://en.wikipedia.org/wiki/Linux_malware#Threats](http://en.wikipedia.org/wiki/Linux_malware#Threats)

Most of the experienced users here will tell you that article contains a lot of hogwash.  Providers of security software benefit from maintaining a climate of fear among computer users.  Since we don't really know who is posting to this article (which has a *very* long revision history, by the way), it's tough to say how much "astroturfing" is going on there.

Also let me point to this sentence at the beginning of the section to which you linked: "The following is a partial list of known Linux malware; however, *few if any are in the wild, and most have been made obsolete by updates*. (emphasis mine)"  Of course, the author(s) hasten to add that new stuff may be coming down the pike so beware (and maybe buy our Linux anti-virus software while you're at it).

If you think I sound like Pollyanna, I've been running Linux for over fifteen years and have never had any sort of "infection" on any machine I've maintained.  A decade ago, I had a server running Apache mildly compromised, but that was my own fault for not keeping current with security updates that included a patch for the problem.  I've never had a problem with machines behind a decent firewall, both servers and desktops.

---

### Post by Duncan Williams on 2011-03-26
I am very impressed with ubuntu and linux. I intend to use it as my main system soon (currently dual boot with windows XP-3)

There are different forms of malware evolving and linux is not completely immune to it,

As per my last post. I am using.
firestarter (firewall)
system monitor ( as network monitor)

I had a look at clamav but decided against it (anti-virus)

I would like.
more comprehensive firewall management.
more options to monitor my internet connection (including daily usage etc.)
A basic cloud based scan for all known linux malware.

I believe that these tools will become available at some stage.

---

### Post by HermanAB on 2011-03-26
Just to give you some idea of why a special firewall is not really needed:

$ uptime
 02:36:29 up 515 days, 13:42

This machine is my web and mail server and has been running for over 500 days with ZERO maintenance, while directly exposed to the wild wild web on a high speed optical fibre link.  No updates, no restarts, no problems, nothing, nada, nietz, nee, nichts.

My previous web and mail server ran for over 4 years, at which point the PSU failed - and I have many more client machines that are essentially the same!

So, if you *are* getting malware on your computer, then you are doing something very wrong.

---

### Post by tgm4883 on 2011-03-26
> **HermanAB said:**
> Just to give you some idea of why a special firewall is not really needed:

$ uptime
 02:36:29 up 515 days, 13:42

This machine is my web and mail server and has been running for over 500 days with ZERO maintenance, while directly exposed to the wild wild web on a high speed optical fibre link.  No updates, no restarts, no problems, nothing, nada, nietz, nee, nichts.

My previous web and mail server ran for over 4 years, at which point the PSU failed - and I have many more client machines that are essentially the same!

So, if you *are* getting malware on your computer, then you are doing something very wrong.

I'm not sure how you having a SERVER running for 515 days compares to a user's DESKTOP in terms of needing or not needing a firewall. The use case for those two types of systems is very very different

---

### Post by brian_p on 2011-03-26
> **HermanAB said:**
> 

This machine is my web and mail server and has been running for over 500 days with ZERO maintenance, while directly exposed to the wild wild web on a high speed optical fibre link.  No updates, no restarts, no problems, nothing, nada, nietz, nee, nichts.

I'm not going to pit my measly 96 days against your 500+ days but - no updates! It is the one thing I always do and advise others to do. Not every day, but it's always done at some time (which is why my uptime is only 96 days - a kernel security upgrade). So . . . . .

---

### Post by robsoles on 2011-03-26
> **HermanAB said:**
> ...

This machine is my web and mail server and has been running for over 500 days with ZERO maintenance, while directly exposed to the wild wild web on a high speed optical fibre link. ** No updates**, no restarts, no problems, nothing, nada, nietz, nee, nichts.

...

Does that specific machine host a site that gets more than 300 hits a month?


I have 7 sites out there that I take care of. Five are Joomla, two of those integrate Virtuemart. Six of the sites have less than 300 visitors per month, the one with the biggest footprint and best implementation of Virtuemart is approaching 100 visits per day. It belongs to a two man company which really took good ownership of what I made for them.

I update everything about two of the three servers involved in keeping these sites online, the third server is a managed shared server which is updated more religiously than I update my servers, it has the popular site on it. The fellow in the company making a decent fist of their site is only becoming proficient at Content Management Systems so I remain their admin...

Their site has been hacked twice since I rebuilt it, both times about a month, or slightly less, before the Joomla Security team put out updates which happened to address the issues I had to circumvent to keep the site clean on discovery of the hacks.


The point of some updates is to defeat security flaws that have been found and if you don't apply these SECURITY updates (even to the most unpopular lemon of a site/service ever - one of mine too, I'm sure :p) then I absolutely believe you will be lucky to retire from managing servers without a nasty experience or two to regret for it!


I keep a headless server in the corner of my bedroom, it runs 24/7 (from time to time I investigate quieter cooling options :roll:) and it provides my LAN with DHCP, DNS, Samba and Time service. I have virtualbox providing a headless VM of Windows so I can use the one physical machine to mirror either a Linux or Windows server's service.

That machine is Ubuntu 10.04 LTS Server Edition, I set it up to download updates and install the ones marked 'security' straight away - when I notice a service from it being absent, or sluggish, I SSH in and restart it. Once in the last year I had to lend it my main PC's second monitor when the SSH was borked.

When I installed 10.04 on it I did very little beyond checking to secure it. The teenagers here have some fairly clever friends and they haven't managed to penetrate it *yet*. I am saying that it was fairly well set out of the box.


I am in no way suggesting that a 'production server' should be set to automatically apply security updates or patches, **it is a mugs caper to just directly apply any update to a production server: Mirror it, update the mirror, test the mirror thoroughly, backup (re-mirror :roll:) and only apply the updates to the production server if you 'liked' what they did to the mirror**.

Have a nicer day, both of my production servers are set to ignore updates and I've just remembered my semi-popular mail server I think I ignored last time I played the updating game!

---

### Post by HermanAB on 2011-03-27
Yup, I look at the security updates and if it is not important, or directly applicable, I ignore it.  There was a SSL update that was taken care of when I built the new server.  My philosophy is "Don't fix it if it ain't broke"...

On desktop and notebook machines, I do pretty much the same thing as with servers.  I turn auto screw-ups^Wupdates off once the system is installed, stable and working properly and then do a complete re-install once a year, rather than run the auto-update service.  

In my experience, auto-updates cause more problems than security exploits, because the updates happen all the time and exploits almost never.  It is different with Windows systems of course, but this is Linux we are talking of.

BTW, I put an iptables rate limiting rule on all my machines, which slows any hack attempt down to a crawl, and PAM enforces looooooooooong passwords for everybody, so my machines don't get hacked (anymore!).

---

### Post by opendoors on 2011-03-27
[QUOTE=tgm4883]There would actually be a few stopping points, where the process right below it would be the main process. (stopping points being init, /usr/bin/terminal, etc)

Looking at pstree I have things like chromium-browser, miro, and dropbox under init, so obviously those would be what the user should be notified about. Chromium-browser may take additional work if you wanted to get granular about plugins and such.

I also have a few bash scripts that require network access. These are showing up under init -> /usr/bin/terminal. Obviously we don't want to set /usr/bin/terminal as the main process, so the script below it would need to be the configured process. May need to base that on md5hash instead of just filename.[/QUOTE]

I like the idea of having specific stopping points. For greater flexibility, the user could be allowed to decide which stopping point to use in certain situations (if they wish). To help the user make a decision, the entire process tree could be (optionally) displayed. I for one wouldn't mind doing more work if it meant that I could have greater control; that's what an application firewall is all about after all.

IMHO, using the md5 (or an even stronger hash) is a desirable idea anyways. A file can change its name and even its location, but if the hash remains the same, then it is highly likely that it is the same file. I don't think it's very easy to produce 2 different files with a hash collision but that still have the same file size and functionality. I'm not too worried about this possibility, but if it becomes a problem, an additional hash can always be used (e.g. SHA1). That way, an attacker would have to produce 2 hash collisions in order for the file to be assumed the same. If this becomes necessary, then the MD5 and the SHA1 would both have to match in order for the file to be deemed unchanged. An application firewall that controlled access by checksum, file size, file location, and name (or a desired combination of any of those) would be more useful than one that just discriminated based on the file name alone. The process would then be further restricted by port and IP address (or IP range). Such a level of control would be a significant improvement over current tools and iptable GUIs.

---

### Post by Duncan Williams on 2011-03-27
skyting they call it in New Zealand. Bragging in the UK.
I know linux is safer than windows, but get in front and supply the tools, fools.

---

### Post by HermanAB on 2011-03-27
"The tools are out there Sculley".  

You just need to get off your lazy bum and learn how to use them.

---

### Post by Duncan Williams on 2011-03-27
I found some:
[http://my.opera.com/internetsecurity/archive/](http://my.opera.com/internetsecurity/archive/)

---

### Post by bodhi.zazen on 2011-03-27
> **Duncan Williams said:**
> skyting they call it in New Zealand. Bragging in the UK.
I know linux is safer than windows, but get in front and supply the tools, fools.

The tools are listed and referenced in the security sticky. The security stick also contains a number of links to additional material.

If you have a question, please start a support thread.

---

### Post by uRock on 2011-03-27
This thread has deteriorated into an argument that nobody here can settle.

Feel free to present ideas at [Ubuntu Brainstorm]("http://brainstorm.ubuntu.com/") and maybe someone will write such an app.

Thread Closed.

---

