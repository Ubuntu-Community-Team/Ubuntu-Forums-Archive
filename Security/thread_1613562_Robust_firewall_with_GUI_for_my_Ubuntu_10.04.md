---
title: "Robust firewall with GUI for my Ubuntu 10.04"
date: 2010-11-04
forum: Security
---

### Post by agentfortyseven on 2010-11-04
Hey there fellas,
I've been using Windows for quite a few years now. I loved the way how I used to set incoming/outgoing rules for my applications. But I'm having hard time doing that in Ubuntu. I tried searching for a good GUI for iptables but I need your help selecting the best. I might learn iptables someday but for the time being I will be using a nice GUI. I'm currently using GUFW, I've tried Firestarter. All I need is a firewall that would allow me to configure rules for my applications. Please suggest me some.
Thanks :)

---

### Post by CandidMan on 2010-11-04
Hi there

From what I've read GUFW and UFW are recommended the most because Firestarter's not been developed for a few years

---

### Post by FuturePilot on 2010-11-04
Please read the Ubuntu Security sticky. There's a link in my sig.

Short answer: you probably don't need one.

---

### Post by arapaho on 2010-11-05
Read this:
[http://ubuntuforums.org/showthread.php?t=1591340](http://ubuntuforums.org/showthread.php?t=1591340)
As every newbee you have the same request :P 

There is no firewall with application block feature for linux. I use firestarter because at least it can block all inbound and outbound traffic with exceptions for outbound (Restrictive by default whitelist traffic).
Gufw works differently. You can't block all outbound and make exception, because the general rule next to the shield picture seems to be more important. In Gufw you can have all inbound blocked with all outbound open and then block chosen outbound ports. 
You may also want to have a look at this:
[http://ubuntuforums.org/showthread.php?t=990311](http://ubuntuforums.org/showthread.php?t=990311)
[http://ubuntuforums.org/showthread.php?t=1188099](http://ubuntuforums.org/showthread.php?t=1188099)
But it is rather complicated and it work in a different way, blocking users or IP addresses.

---

### Post by CharlesA on 2010-11-05
Note: All GUI "firewalls" are just frontends for iptables.

Sometimes it's just easier to write the rule straight into iptables.

---

### Post by uRock on 2010-11-05
I use GUFW when using insecure LANs. (Any LAN I am not in control of.)

---

### Post by Enigmapond on 2010-11-05
+1 for GUFW....this is really the best front-end for iptables..IMHO..:)

---

### Post by arapaho on 2010-11-05
> **CharlesA said:**
> Note: All GUI "firewalls" are just frontends for iptables.

Sometimes it's just easier to write the rule straight into iptables.

You can't create an iptable rule for application. Only for IP address or port. And the author wrote:
"All I need is a firewall that would allow me to configure **rules for my applications**."
The answer is: impossible.

---

### Post by uRock on 2010-11-05
> **arapaho said:**
> You can't create an iptable rule for application. Only for IP address or port. And the author wrote:
"All I need is a firewall that would allow me to configure **rules for my applications**."
The answer is: impossible.
Different applications use different default ports, so it is possible.

---

### Post by CharlesA on 2010-11-05
> **arapaho said:**
> You can't create an iptable rule for application. Only for IP address or port. And the author wrote:
"All I need is a firewall that would allow me to configure **rules for my applications**."
The answer is: impossible.

Why not just use your Tux Guardian application then?

[http://ubuntuforums.org/showthread.php?t=1591340](http://ubuntuforums.org/showthread.php?t=1591340)

---

### Post by arapaho on 2010-11-05
> **uRock said:**
> Different applications use different default ports, so it is possible.

Of course this is possible to block ports, but this is something different then just block _application_ or process itself. The problem is when you want one application to use specific port for example 80, and simultaneously block it for another application or when one application use the other like web browser to access the Internet. But the discussion repeats itself...

Tuxguardian would do the job but unfortunately it is not developed anymore. I wish Ubuntu developers would do similar application.

---

### Post by CharlesA on 2010-11-05
You can filter traffic based on the PID with iptables.

Keep in mind that Linux is not Windows and you really don't need an active "application" firewall.

---

### Post by uRock on 2010-11-05
> **arapaho said:**
> Of course this is possible to block ports, but this is something different then just block _application_ or process itself. The problem is when you want one application to use specific port for example 80, and simultaneously block it for another application or when one application use the other like web browser to access the Internet. But the discussion repeats itself...
It only repeats itself when people deny the truth. Every application has its own designated default ports. An understanding of the seven layer OSI model or even the TCP/IP model will show how this works.

---

### Post by arapaho on 2010-11-05
> **CharlesA said:**
> You can filter traffic based on the PID with iptables.
What is PID?

---

### Post by CharlesA on 2010-11-05
> **arapaho said:**
> What is PID?

Process ID.

[http://linux.die.net/man/8/iptables](http://linux.die.net/man/8/iptables)

---

### Post by arapaho on 2010-11-05
I can see in system monitor some ID's for processes like for example 15515 for Opera.
Could you please give me an example of an iptable rule to block this process?
Lecture of this man page is rather complicated to me.

> "An understanding of the seven layer OSI model or even the TCP/IP model will show how this works."
I'm sure it is a great thing to understand but having simple application like working like tuxguardian would make live more easy and enjoyable.:P Don't you agree?

---

### Post by CharlesA on 2010-11-05
[http://www.frozentux.net/iptables-tutorial/chunkyhtml/x2702.html](http://www.frozentux.net/iptables-tutorial/chunkyhtml/x2702.html)

I think it should look like this:

```
sudo iptables -A OUTPUT -m owner --pid-owner 78
```

---

### Post by arapaho on 2010-11-05
I've found this 
[http://ubuntuforums.org/showthread.php?t=1591433](http://ubuntuforums.org/showthread.php?t=1591433)

---

### Post by uRock on 2010-11-05
> **arapaho said:**
> I'm sure it is a great thing to understand but having simple application like working like tuxguardian would make live more easy and enjoyable.:P Don't you agree?
Yes and no. Personally, if there is a program on my system that I do not want connecting, then I completely remove the program.

---

### Post by CharlesA on 2010-11-05
> **uRock said:**
> Yes and no. Personally, if there is a program on my system that I do not want connecting, then I completely remove the program.

I do the same.

---

### Post by cariboo on 2010-11-05
Blocking programs by pid only works if your computer is on 24/7, every time you restart a program, it gets a different pid.

I really fail to see how this is an issue, if you don't want a program to connect to the internet, don't start it.

---

### Post by CharlesA on 2010-11-05
> **cariboo907 said:**
> Blocking programs by pid only works if your computer is on 24/7, every time you restart a program, it gets a different pid.

I really fail to see how this is an issue, if you don't want a program to connect to the internet, don't start it.

That makes sense then, thanks.

---

### Post by arapaho on 2010-11-05
> **cariboo907 said:**
> I really fail to see how this is an issue,
I'd like to use programs from different sources like for example from this site
[http://www.linuxlinks.com/Software/](http://www.linuxlinks.com/Software/)
not only from repositories. And I'm not sure if they are safe and if they can contain a spyware or a keylogger. So, just in case I'd like to block them right at the installation process.

---

### Post by CharlesA on 2010-11-05
> **arapaho said:**
> I'd like to use programs from different sources like for example from this site
[http://www.linuxlinks.com/Software/](http://www.linuxlinks.com/Software/)
not only from repositories. And I'm not sure if they are safe and if they can contain a spyware or a keylogger. So, just in case I'd like to block them right at the installation process.

If you run unverified code, you are opening an entirely new set of worms. There really isn't anything that a firewall can do if you install something that has a keylogger or whatever in it.

---

### Post by janpol on 2010-11-05
> **CharlesA said:**
> If you run unverified code, you are opening an entirely new set of worms. There really isn't anything that a firewall can do if you install something that has a keylogger or whatever in it.
True, and that's true for firewalls in any OS. Also, spyware in Open Source, and for Linux is really really unlikely (ofc not impossible, but really unlikely).

@arapaho: Please, read the thread FuturePilot recommended: [http://ubuntuforums.org/showthread.php?t=510812]("http://ubuntuforums.org/showthread.php?t=510812")

---

### Post by The Cog on 2010-11-05
> **uRock said:**
> It only repeats itself when people deny the truth. Every application has its own designated default ports. An understanding of the seven layer OSI model or even the TCP/IP model will show how this works.

Sorry but that's not right. An application that listens for incoming connections (a server application) must listen on a "well known port" number, or its clients won't know which port number to try to connect to. So for instance, web servers generally listen on port 80, and SSH servers on port 22. 

But for applications that only make outgoing connections, there is no particular port number for them. They generally just ask the OS to open a socket and they get the next available (often starting from port 1024 and working up from there). So you can't easily distinguish between applications on the basis of port numbers. You might be able to identify web browsers on the basis that they connect to port 80, but you can't tell between firefox, chromium, lynx or apt-get. The server port is 80, but the client port is essentially random.

I also happen to think there's not that much value in trying to block particular applications anyway. I gather it's not that hard for an application to masquerade as a different one although I don't understand the details - maybe just run a different program in the background? And it is generally standard practice for malware to disable the firewall.

---

### Post by OpSecShellshock on 2010-11-05
Haven't used Firestarter in a while, but as I recall, when you set it to allow an application, what's really happening is that it sets iptables up to allow outgoing connections to the default server-side port generally associated with that application's service. In other words, I don't think it's actually going by process name even then. It also means that a theoretical malicious application, even with a different process name, would still be able to make a connection provided it used one of the allowed services.

---

### Post by cariboo on 2010-11-05
> **arapaho said:**
> I'd like to use programs from different sources like for example from this site
[http://www.linuxlinks.com/Software/](http://www.linuxlinks.com/Software/)
not only from repositories. And I'm not sure if they are safe and if they can contain a spyware or a keylogger. So, just in case I'd like to block them right at the installation process.

I just had a quick look, and every program I saw was already in the repositories. You'd be much better off staying with the repositories, as at least the packages are signed by the dev/maintainer. There should be a really compelling reason to go outside of the repos, like a new feature that isn't available in the repo version.

I would suggest if you need a newer version of something in the repositories, check the ppas (personal package archives) on [https://lauchpad.net](https://lauchpad.net), as many of the newer packages show up there before they hit the repositories.

---

### Post by tkoco on 2010-11-05
> **agentfortyseven said:**
> Hey there fellas,
I've been using Windows for quite a few years now. I loved the way how I used to set incoming/outgoing rules for my applications. But I'm having hard time doing that in Ubuntu. I tried searching for a good GUI for iptables but I need your help selecting the best. I might learn iptables someday but for the time being I will be using a nice GUI. I'm currently using GUFW, I've tried Firestarter. All I need is a firewall that would allow me to configure rules for my applications. Please suggest me some.
Thanks :)

I'm not sure that your question was answered. An inherent problem with any GUI based interface is that should you want to do something which the programmer failed to consider, then you are automatically blocked from doing it through the GUI.

The whole purpose of a firewall is control of the data flow between the computer and the outside world. It is not for the control of applications. That is your job - you control the applications. So, you need to be thinking in terms of data flow.

So, the question here is "What do you want the data flow to do or not do?"

I use Shorewall to set up the IPtables. Why? It is well documented and as flexible as doing it by hand with iptables. Think of iptables/Shorewall in terms of programming.  (writing a program in assembly code vs writing it in C or C++) If you had to write a program, which method would you use? Both methods will get the job done.

Back to data flow considerations, the simplist firewall blocks all inbound connections and passes all outbound connections (no services presented to the Internet, and no control of clients connecting to the Internet). Any of the GUI front ends can do this type of firewall.

If you want to set up holes in the firewall (like allowing connections to a web server as an example), then the situation gets a bit more complicated.

And can get even more complicated when you block outbound data going to known security risks. An example of this is to block data headed for any address on TCP ports 445, 5554 and 9996. (Net-Worm:W32/Sasser infection on a Windows based system). Now before anyone says something about "windows" based infections, I respectfully remind everyone that WINE can potentially get infected by windows based malware.

Does this help?

---

### Post by A_M_S on 2010-11-05
You can use this tutorial to prevent applications to access the Internet. (Its CLI solution)

[http://ubuntuforums.org/showthread.php?t=1188099](http://ubuntuforums.org/showthread.php?t=1188099)

---

### Post by agentfortyseven on 2010-11-06
> **tkoco said:**
> I'm not sure that your question was answered. An inherent problem with any GUI based interface is that should you want to do something which the programmer failed to consider, then you are automatically blocked from doing it through the GUI.

The whole purpose of a firewall is control of the data flow between the computer and the outside world. It is not for the control of applications. That is your job - you control the applications. So, you need to be thinking in terms of data flow.

So, the question here is "What do you want the data flow to do or not do?"

I use Shorewall to set up the IPtables. Why? It is well documented and as flexible as doing it by hand with iptables. Think of iptables/Shorewall in terms of programming.  (writing a program in assembly code vs writing it in C or C++) If you had to write a program, which method would you use? Both methods will get the job done.

Back to data flow considerations, the simplist firewall blocks all inbound connections and passes all outbound connections (no services presented to the Internet, and no control of clients connecting to the Internet). Any of the GUI front ends can do this type of firewall.

If you want to set up holes in the firewall (like allowing connections to a web server as an example), then the situation gets a bit more complicated.

And can get even more complicated when you block outbound data going to known security risks. An example of this is to block data headed for any address on TCP ports 445, 5554 and 9996. (Net-Worm:W32/Sasser infection on a Windows based system). Now before anyone says something about "windows" based infections, I respectfully remind everyone that WINE can potentially get infected by windows based malware.

Does this help?

Sure it does, to some extent:)

---

### Post by agentfortyseven on 2010-11-06
Hey everone,
Thanks for all those replies.
From what I've figured out from your comments is that there's no such GUI that would enable me to set rules for each of my application.
But I honestly feel that there should be a Windows-like firewall application that would make the Windows migrants feel at home here in Linux (Ubuntu ;)). That's because the laborous ordeal involved in setting up IPTABLES is a turn off for most of the windows users. I know there's GUFW and Firestarter, but in terms of configurability they don't stand out. And I as an advance windows user would love to see my system/application behaviour on Ubuntu too.
I can bet the number of windows migrants to Ubuntu would double or even quadruple once nice GUIs for firewall and other stuff are developed.
The bigger the community, the better it gets:cool:
CHEERS EVERYONE.

---

### Post by arapaho on 2010-11-06
> **tkoco said:**
> And can get even more complicated when you block outbound data going to known security risks. An example of this is to block data headed for any address on TCP ports 445, 5554 and 9996. (Net-Worm:W32/Sasser infection on a Windows based system). Now before anyone says something about "windows" based infections, I respectfully remind everyone that WINE can potentially get infected by windows based malware.

Does this help?

Good to know that WINE can be infected by windows based malware. I use WINE because some widows applications are better than linux applications, and some can't be replaced.

In reference to ports, that's why I prefer to use Firestarter because it can block all outbound, but allow for exceptions. I have only 80, 443 and 8000 opened for outbound and eventually open another if necessary. This is impossible with Gufw because when it blocks outbound all outbound traffic is blocked. You can't make exemptions in outbound whitelist. I checked it and they are blocked even when exception rule is added. Although I know that both are only GUI for the same iptables, I think Firestarter gives more control than Gufw and it should be default firewall for Ubuntu.

---

### Post by agentfortyseven on 2010-11-06
> **arapaho said:**
>  Although I know that both are only GUI for the same iptables, I think Firestarter gives more control than Gufw and it should be default firewall for Ubuntu.
Yeah same here buddy. I pretty much like the internet locking feature in Firestarter.

---

### Post by CharlesA on 2010-11-06
> **arapaho said:**
> Although I know that both are only GUI for the same iptables, I think Firestarter gives more control than Gufw and it should be default firewall for Ubuntu.

The reason firestarter isn't the default frontend in Ubuntu is because it's no longer in development.

Old software tends to be out-of-date.

---

### Post by agentfortyseven on 2010-11-06
> **CharlesA said:**
> The reason firestarter isn't the default frontend in Ubuntu is because it's no longer in development.

Old software tends to be out-of-date.

I see. Can you suggest me one good firewall my friend other than GUFW.

---

### Post by agentfortyseven on 2010-11-06
How does fwbuilder(firewall builder) compare with shorewall?
I've heard fwbuilder's got a nice GUI but some people had issues configuring it.

---

### Post by CharlesA on 2010-11-06
> **agentfortyseven said:**
> I see. Can you suggest me one good firewall my friend other than GUFW.

There are a ton of front-ends, but I don't use them, so I can't suggest any.

I usually just use plain iptables to set rules.

---

### Post by agentfortyseven on 2010-11-06
Alrighty

---

### Post by janpol on 2010-11-06
> **agentfortyseven said:**
> I honestly feel that there should be a Windows-like firewall application that would make the Windows migrants feel at home here in Linux (Ubuntu ;)). That's because the laborous ordeal involved in setting up IPTABLES is a turn off for most of the windows users. I know there's GUFW and Firestarter, but in terms of configurability they don't stand out. And I as an advance windows user would love to see my system/application behaviour on Ubuntu too.

I think is better to explain to new users "the linux way of doing things". Regular users don't need to set up iptables in Ubuntu in order to be secure (that's easier than needing to configure a firewall in Windows right?). You only need to mess up with it when you install a service that opens a port to access your computer (if you install something like that, is because you want people to be able to access that service from the outside, and you can easily block this with GUI tools). And even your default cheap router with NAT will block that unless you configure it. 

If you buy a Mac with OSX, you don't expect it to be just like Windows right?, the same is with Ubuntu.

Easy of use is not the same as "doing things exactly like Windows". Windows does some great things, is easy to use and you might get some ideas that you can implement in Ubuntu. But that's not the case of the Windows firewall (security in general in both operative systems is different).

Please read: [Ubuntu Security]("http://ubuntuforums.org/showthread.php?t=510812")

Also, read a little bit about AppArmor if you want to restrict applications.

Regards

---

### Post by agentfortyseven on 2010-11-06
> **janpol said:**
> I think is better to explain to new users "the linux way of doing things". Regular users don't need to set up iptables in Ubuntu in order to be secure (that's easier than needing to configure a firewall in Windows right?). You only need to mess up with it when you install a service that opens a port to access your computer (if you install something like that, is because you want people to be able to access that service from the outside, and you can easily block this with GUI tools). And even your default cheap router with NAT will block that unless you configure it. 

If you buy a Mac with OSX, you don't expect it to be just like Windows right?, the same is with Ubuntu.

Easy of use is not the same as "doing things exactly like Windows". Windows does some great things, is easy to use and you might get some ideas that you can implement in Ubuntu. But that's not the case of the Windows firewall (security in general in both operative systems is different).

Regards
Well I wrote that comment keeping in mind 'windows users' who intend to switch on to Ubuntu.

> **janpol said:**
> (if you install something like that, is because you want people to be  able to access that service from the outside, and you can easily block  this with GUI tools)

Now that you've mentioned the magic word GUI tools, I'm gonna shoot you with the same question. Suggest me one good GUI tool.

---

### Post by janpol on 2010-11-06
Never used one, I configure IPTables from the terminal, and I needed to configure it to OPEN a port, not to close it xD.

In another thread, a guy was saying he liked [Gufw]("http://gufw.tuxfamily.org/"). 

But the main point is that **_you don't need to configure a firewall_**, unless you are installing a service that needs to be accessed from the outside, that's what I wanted you to understand. New Windows users shouldn't worry about a firewall, I think that brings more users to Ubuntu :). 

Configuring IPTables (using whatever GUI) is useful for restricting traffic or allowing/restricting a service to be contacted from the outside (and a service that is programmed to be accessed from the outside, like a web server), but, from a security stand point, a regular user doesn't need to touch iptables. And, if you don't want amule to eat up your bandwidth, just close it xD (I don't think that windows users go and close their firewall port, they just close the program). 

Get rid of your Windows firewall fears ;) If you want paranoid Security in Linux, take a look at AppArmor and SELinux.

Maybe if you could explain your situation better, we can show you if you need or you don't need to touch iptables and why.

---

### Post by NadirPoint on 2010-11-06
> **uRock said:**
> It only repeats itself when people deny the truth. Every application has its own designated default ports. An understanding of the seven layer OSI model or even the TCP/IP model will show how this works.
Unfortunately cyber n'er-do-wells cannot be depended upon to follow the rules.  As was stated:
> **The Cog said:**
> ...it's not that hard for an application to masquerade as a different one although I don't understand the 
details - maybe just run a different program in the background? And it is generally standard practice for malware to disable the firewall.
Among other things.  Likely things nobody in the general population or anyone playing with FW development is even aware of.  A traditional-type firewall is the last thing you are worried about if you truly are a serious target.  If not, the basics will do fine.  Keep your system patched/updated, don't run unnecessary services, use strong passwords, etc.  No worries.  Because:
> **janpol said:**
> Regular users don't need to set up iptables in Ubuntu in order to be secure (that's easier than needing to configure a firewall in Windows right?).
Enabled upon installation, assuming you accept the default, nothing else to worry about.  I think the problem is this crossover with the Windows security paradigm.  That must be an oxymoron.  

Otherwise, I agree with tkoco and for Linux I like Shorewall: 

[http://www.shorewall.net/index.htm](http://www.shorewall.net/index.htm)

1st line on that home page says it all.

---

### Post by janpol on 2010-11-06
> **NadirPoint said:**
> 
Enabled upon installation, assuming you accept the default, nothing else to worry about.  I think the problem is this crossover with the Windows security paradigm.

Exactly, that's what I meant, you don't need to set up or worry about anything, just be happy :D

But I'll wait for agentfortyseven to explain his particular situation and why he is worried about firewalls, maybe he needs to set up a web server or something like that.

---

### Post by agentfortyseven on 2010-11-06
Yeah guys, I'm quite a paranoid about my security. 
I have no doubt in accepting that IPTABLES is much superior than those in Windows.
I always thought that Ubuntu was impervious to network attacks and  hacking but I was wrong. Few months ago, I came across this article on  internet that was discussing about various ways of breaking into Ubuntu.  A friend of mine confirmed that its possible, but the probability is  low. This, I guess is probably the main reason for apprehensions  regarding security.
In this age of Paypals and Alertpays, we cannot afford to be callous.  Maybe applications like apparmor, angryIPscanner, snort etc could add  that extra bit of security.

---

### Post by The Cog on 2010-11-06
Yabbut...

You don't need to install/configure a firewall just because you install a web server. All the firewall will do is to block all your incoming connections to the server until you configure it to let them through again, after which you're in the same place you were before you messed with the firewall in the first place. If you don't want anybody connecting to a service, don't install the service. 

If you want everybody to be able to connect to your service, you don't need a firewall blocking them. You don't need a firewall unless you want to be **selective** about what you block. In that case, it's obvious that you need a firewall, and you can state exactly what you want it to do - what to permit and what to deny. If you can't explain exactly what you want the firewall to do but just feel you should have one because windows needs one, then you don't need it.

The one exception to that is that it does seem reasonable to me to want a firewall to allow "proper" apps to access the network but to deny malware. The problem there is, as has been said, once malware is inside, it can do pretty much what it likes and the firewall will be one of the first things it re-adjusts / subverts. There is a good reason that there's not much of a market for door locks designed to prevent burglars from getting back out again, and it really surprises me how many windows users want to rely on that kind of approach.

---

### Post by janpol on 2010-11-06
> **agentfortyseven said:**
> Yeah guys, I'm quite a paranoid about my security. 
I have no doubt in accepting that IPTABLES is much superior than those in Windows.
I always thought that Ubuntu was impervious to network attacks and  hacking but I was wrong. Few months ago, I came across this article on  internet that was discussing about various ways of breaking into Ubuntu.  A friend of mine confirmed that its possible, but the probability is  low. This, I guess is probably the main reason for apprehensions  regarding security.
In this age of Paypals and Alertpays, we cannot afford to be callous.  Maybe applications like apparmor, angryIPscanner, snort etc could add  that extra bit of security.
If you wanna do online banking safely, boot from a livecd, and do all your online transactions from there ;)

Still, from what you are saying it seems that you don't need to touch your firewall.

---

### Post by agentfortyseven on 2010-11-07
> **janpol said:**
> If you wanna do online banking safely, boot from a livecd, an do all your online transactions from there ;)

Still, from what you are saying it seems that you don't need to touch your firewall.

Alright that seems to be a good alternative, thanks:)

---

### Post by HermanAB on 2010-11-07
Howdy,

Look at it this way: Underneath every home Windows machine lies a dinky little Linux firewall router thingy amongst the dust bunnies.  That dinky little machine doesn't have a firewall to hide behind - it is right on the wild wild web and it does perfectly fine thanks.

Now you are running a Linux desktop/laptop machine and just like that dinky little machine on the floor, it doesn't need to have a firewall to hide behind.  Ditto for the tens of thousands of Linux servers in the Amazon/Akamai/Google/Yahoo/Rackspace data centres.

Relax and enjoy your Linux system and forget about firewalls.  Just make sure that if you run a program, that you are sure that you really want to run it and know what it is supposed to do.

---

### Post by DaveVM on 2010-11-07
Folks,

As a recent NuBee to ubuntu from the Windows world, I too have been concerned about security. Yes I've read that nix boxes are inherently more secure but like most folks, prove it to me, and I believe that is what was being asked.

Those of us from Windows know we have to use AntiVirus, Firewalls and other malware tools to keep our system hopefully clean. Think of it as keeping all of our homes windows and doors locked, along with a security system if needed. So when we move to nix boxes and we're told oh this neighborhood is safe no need for locks and so forth, we go "Ya, Right!"

So anyway a site I use to check firewalls for open/accessible ports is [www.grc.com](www.grc.com) and their check called Shields Up!! Because if a port responds to a probe then in my thinking the computer might be at risk. There may be other port scanners/probers out there, this is just the one I use.

So I checked LTS 10.04 with Shields Up!! and it passed all tests! The check gave me the proof I needed.

All this being said it would still be nice to know when the first time you launch/start an app and it's dependencies if they are going to access the net and if so for what purpose? Let's face it, if we start a little text editor there should be no reason for it to access the web and if it were most Windows firewalls would tell us, though this is something I have yet to to see in Ubuntu. Call it paranoid but I don't want something accessing the web I'm not aware of. Think of it as people accessing your home.

Just my three cents.

Dave

---

### Post by uRock on 2010-11-07
When running the shields up test it is best to connect directly to the modem or else you are just scanning the router.

---

### Post by CharlesA on 2010-11-07
> **uRock said:**
> When running the shields up test it is best to connect directly to the modem or else you are just scanning the router.

Yep.

I find it easier to just run nmap against the machine I want to test to find any open ports.

---

### Post by WeAreLinux on 2010-11-08
> **DaveVM said:**
> All this being said it would still be nice to know when the first time you launch/start an app and it's dependencies if they are going to access the net and if so for what purpose? 

Thats one of the few things I miss from using Windows FW's and/or HIPS programs (felt like I had more control what to run, what to allow to connect online,etc.) but like I keep reading on here over & over...it's really not needed on a Ubuntu system. Do I know for sure? No, because I don't have the knowledge but I trust the community here to provide correct information. I've been using the "basic" UFW to configure the complicated iptables & I have no complaints.

One thing I would like to see with UFW, is the logging of which programs are establishing connections but maybe this is already possible?? I don't know. I'm still learning. :)

---

### Post by uRock on 2010-11-08
> **WeAreLinux said:**
> Thats one of the few things I miss from using Windows FW's and/or HIPS programs (felt like I had more control what to run, what to allow to connect online,etc.) but like I keep reading on here over & over...it's really not needed on a Ubuntu system. Do I know for sure? No, because I don't have the knowledge but I trust the community here to provide correct information. I've been using the "basic" UFW to configure the complicated iptables & I have no complaints.

One thing I would like to see with UFW, is the logging of which programs are establishing connections but maybe this is already possible?? I don't know. I'm still learning. :)

I have heard that ntop is good for showing what is connecting and via which ports.

---

### Post by WeAreLinux on 2010-11-08
> **uRock said:**
> I have heard that ntop is good for showing what is connecting and via which ports.

Thanks, I'll look into that.

---

### Post by DaveVM on 2010-11-08
Will try both ntop and nmap to see what is going on, thanks for those pointers. Now to find them.

And yes I too would like to believe what I read here as well, though some of us migrating from Windows would like to and need to be able to verify for ourselves that the system is secure. To that end I would think there should be some utilities/web sites available to ease our minds. Even if they were only used by those migrating from Windows. So be it. I do like to verify things I'm told, particularly when there is such polar opposites in play. 

It's like when we were kids, Mom told us not to touch because it was HOT! What did we do?

---

### Post by OpSecShellshock on 2010-11-08
> **DaveVM said:**
> Will try both ntop and nmap to see what is going on, thanks for those pointers. Now to find them.

And yes I too would like to believe what I read here as well, though some of us migrating from Windows would like to and need to be able to verify for ourselves that the system is secure. To that end I would think there should be some utilities/web sites available to ease our minds. Even if they were only used by those migrating from Windows. So be it. I do like to verify things I'm told, particularly when there is such polar opposites in play. 

It's like when we were kids, Mom told us not to touch because it was HOT! What did we do?

Ah, I think I see. Well, look at it this way: if Linux desktops had the same susceptibility to web-based threats as Windows (not even necessarily in the same ways, since the threat models are so different), then I'd expect it to have what you might call "time-to-pwnage parity" with an unprotected Windows desktop. That is, we've all seen or heard about reports that say an unprotected new Windows machine has x-number of minutes to be stood up on a network open to the web before it gets owned. However, despite the fact that most Linux desktops get set out without any additional "protections" aside from the ones which derive from the structure of the OS itself, there aren't even similar statistics to compare it to. There are certainly enough Linux desktop users out there who are also statistic-nerds to a degree that would justify making that information available, regardless of comparative marketplace penetration.

---

### Post by cariboo on 2010-11-08
Most households have at least two computers these days and are connected to the internet via a router. it is fairly simple to install a port scanner on a second system, and check for your self on your internal network.

---

### Post by uRock on 2010-11-08
I have never run it on Windows, but Zenmap is available for Windows and it is in the Ubuntu repos. Zenmap is a GUI version of nmap, which I use often.

---

### Post by agentfortyseven on 2010-11-15
I figure the discussion has drifted away from a 'good firewall with GUI' to something else=P~
But good to see you guys discussing about other security applications.

---

### Post by cariboo on 2010-11-15
> **DaveVM said:**
> Will try both ntop and nmap to see what is going on, thanks for those pointers. Now to find them.

And yes I too would like to believe what I read here as well, though some of us migrating from Windows would like to and need to be able to verify for ourselves that the system is secure. To that end I would think there should be some utilities/web sites available to ease our minds. Even if they were only used by those migrating from Windows. So be it. I do like to verify things I'm told, particularly when there is such polar opposites in play. 

It's like when we were kids, Mom told us not to touch because it was HOT! What did we do?

There are services out there that you can check the integrity of your firewall, again if you are connected to a router, you have to connect directly to your modem for these tests to do any good.

[list]
[*] [Nmap -Online/]("http://nmap-online.com/")
[*] [Canyouseeme]("http://www.canyouseeme.org/")
[/list]

are two that I use regularly.

---

