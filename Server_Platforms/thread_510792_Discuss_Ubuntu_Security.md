---
title: "Discuss Ubuntu Security"
date: 2007-07-27
forum: Server Platforms
---

### Post by bodhi.zazen on 2007-07-27
This thread is to discuss [This Guide](http://ubuntuforums.org/showthread.php?t=510812) as an introduction to Ubuntu Security.  Any suggestions/comments are welcome.

_**Edit**_: Thank you to everyone for reading my sticky and taking the time to reply in this thread. I should have added more information here I see ...

The guide is intended as an introduction to security issues for users new to Ubuntu, including the how and why of a default Ubuntu Desktop installation, and more specifically the default firewall settings (for example as this is the most controversial area followed shortly by anti-virus) ...

It is up to each user to determine what s/he feels is most relevant and important from there ... For example, Firewalls. The default install settings and logistics were explained. If users feel they want to install a firewall despite a default install with no open ports, well it is a snap to install and configure Firestarter ... 

Any additional suggestions from the community are appreciated and as information is presented it can be added to the sticky.

A comprehensive guide to security with all the options and configurations, pros / cons would as you can imagine take quite some time to write, let alone read. Hopefully this sticky serves :

[list=number][*]An introduction to Ubuntu Security for new users.
[*]A road map for further learning.
[*]A healthy starting point for discussing security.[/list]

Some clarification :

The "_Windows Mindset_" is intended as exactly that. I assume most new users are coming from Windows and the issues under this section are both most familiar to them and areas of FAQ on the forums (how often do we see questions from the "Ubuntu Mindset" on ABT?).

The "_Ubuntu Mindset_" is thus likely new information for most new users.

Those divisions/titles are not intended to convey more or less importance to any particular issue, those decisions I leave for "self determination".

---

### Post by Ek0nomik on 2007-07-27
As always, nice work Bodhi.  A lot of good information there.  :)

---

### Post by Jolly-Swagman on 2007-07-27
Very well organised and well put and interesting reading, as for my security measures our whole home office network of 2 x XP pro and 2x linxux + ubutu server are all protected by a hardware firewall, SmoothWall.
See signature for more details to Smoothwall

Thank you and regards

Jolly Swagman

---

### Post by weth on 2007-07-27
Is there a log, except for the /var/log/*  (because they don't monitor everything) or a program that shows every event on the computer, well, I mean not any system or kernel activity but for example every file that has been opened, every picture, film, command typed in the shell, or everything a user has done let's say the last 24 hours...

---

### Post by Seisen on 2007-07-27
You can remove flashblock from Browser / Spyware : Java/Flash/Ad-ware/Trackers/Cookies
because Noscript blocks flash also. Other than that good job :)

---

### Post by koenn on 2007-07-27
Good job. However, I do have some comments - I'll leave it up to you to see whether theyfit r into your guide. I'm not a newbie anymore and deal primarily with servers and networks, so my point of view may be too far away from your target audience's. Still, I use Ubuntu at home, and care about security. So here goes ...


1/ re. viruses. 
The joke (that link) is funny, but misleading. It suggests linux/unix viruses would be spread as source code and that you'd have to comipile and configure it before it can do anything. Obviously, there are better ways - you hint at them in the intro : Do not install software from untrusted sources. Your claim that viruses are not or just a minor problem is imo correct, but the example does not really support you case. 

2/Firewalls. 
Ha, the passionate debates .. :) I've seen a few. 
minor detail : "However, many times installing various server software will cause ports to open" - the 'many times ..." sounds to me that you **repeatedly** need to install (the same?) software before it becomes dangerous. But that could just be me. 

"so some people like to use a firewall as a catch-all layer to find mistakes in their configuration."
You put this under the 'Windows" section so maybe you mean that firewalls are meant to be a safety net under a bad configuration (or a not-so-secure-by-design OS). Althoug that might be true, a firewall is important - also to a linux user.
A firewall is not only a safety net, it's a component of your layered security : it's the gatekeeper between your own private space (be it a single computer or a small home network), and the not-to-be-trusted outside world, usually the internet. 
Granted that a default Ubuntu install does not run any public services (so no listening ports), people will experiment with ssh, file sharing, their own (public!) web server, etc. and a firewall is your first line of defense : if those services are not to be accessed from the internet, access should be blocked. Your firewall is the first hurdle - but it can keep out 80% of the trouble. The remaining 20%, you deal with through other measures.


3/ servers ?
You may ague that most of my comments relate to servers, and that they are irrelevant to new users with just a desktop system. However, the distinction between servers and desktops  (or 'worksations, or whatever' is a false on. Any machine offering services to other systems is a server. If someone  implements filesharing on his PC to share music, pictures ar what not with a room mate or someone five rooms down the hall, or, god forbid, his sister in another part of town, that PC is a server and should be treated as one : under what account will the roommate access the server ?. Is there anything else that account can do ? If the shares should only be accessible on a local, private network, did you take precautions to make sure it's inaccessible from, say, the internet, or from the campus LAN ? ... same goes for any program that allows some sort of remore access. 

4/  layered security.
You're correct that security is an active process and that a secure environment uses layers of defense (a firewall being one of them - re. 2/ ). But you jump from basic (filesystem) security and (file system) to rootkits. The hard work is between those two : Do you allow other users to use your computer ? Do they all have their own account ? How do you enforce the use of strong passwords ? What sort of activity do you want to allow them, and how do you make sure the don't do stuff you don't want them to (by accident or on purpose. Is it OK for anyone to copy your passwd and shadow file on a USB stick and take it home to for a cracking exercise ? And if not, how do you prevent it ? 

 If those users also have remote access - how do you limit the acces to a selected group and keep the others out ? Do you rely solely on login credentials or do you implement additional measures (ACCEPT/DENY rules in your firewall, allowed users / hosts in the respective config files, public/private key pairs ? certificates ?  ...). 
At this pont, it becomes also important to see the bigger picture : what good are key pairs or deny statements in config files if a user can modify those files ? So your account/authentication policy should be seen in relation to other security aspects, such as file system security. Linux and most distro's have the tools and apply sane defaults so it's generally considered a good OS in terms of security. 
When users enter the equation, things change.

---

### Post by hggdh on 2007-07-27
* One should also consider running a chrooted environment, or a virtual machine (VMWare, xen, etc).

Potentially dangerous programmes should be executed from such an environment, not from the real machine. If using VMs, consider making the image static (so rebooting will revert to the saved image). Of course, maintenance of the images has to be performed carefully..

* make sure external media is always mounted noexec, nosuid, nodev. This apllies to all sort of external media. Usually there is no reason to mount them with any of the above flags unset.

---

### Post by bodhi.zazen on 2007-07-28
1. I would like to add two anonymous suggestions I received (by PM)

**First :**
> With the root password scrambled, there's NO reason that the default opensshd config (/etc/ssh/sshd_config) comes with this setting:

PermitRootLogin yes

If the user does set a password on root, it's bad practice to log in as root via SSH.  Also, lots of brute force ssh attacks happen, usually on a regular basis i'm hit with a hundred common passwords.

Might be worth adding.

Just to comment on this : I believe that with a default installation the root account is locked and that sudo is patched to allow this. Please feel free to correct me if this is inaccurate.


**Second :**
> You may also want to touch on honeypots a bit re: intrusion detection...

[http://en.wikipedia.org/wiki/Honeypot_%28computing%29](http://en.wikipedia.org/wiki/Honeypot_%28computing%29)

An interesting idea ...


===================


I am not sure of the implications of this, it is something I have followed.

My comments are that if you find what you feel is a vulnerability, please report it to Launchpad :

[Launchpad](http://www.lauchpad.net)

The thread is quite old (Started in 10/05) and I am reporting the more recent activity this thread now and will post an update if one becomes available.

[http://ubuntuforums.org/showthread.php?t=72598](http://ubuntuforums.org/showthread.php?t=72598)

A word on windows viruses:


In the past there *HAVE* been holes in the wine code that allowed viruses to run on wine, but these have been patched. In reviewing that thread :

[list=number][*]The command to run the virus was initiated by the user, ie wine did *NOT* spontaneously run the code.
[*]It appears to my review that only the home directory was affected so unless you ran the virus as root the system does not appear to be compromised.
[*]The offending worm was "Some Fool" and from here : [http://os.newsforge.com/article.pl?sid=05/01/25/1430222](http://os.newsforge.com/article.pl?sid=05/01/25/1430222)

> **SomeFool**

The SomeFool first-generation worm (Netsky.D according to some folks) actually installs its winlogon.exe file under Wine, and, as an added bonus, seems to get stuck in an endless loop, thus really having a negative performance impact on my Linux machine! I'll give this one 4/5 penguins for not only running and sort of doing what it was supposed to, but actually doing mildly bad things to Linux -- at least until I hit Control-C in the terminal from which I was running Wine to stop it dead.
[*]The thread became "active" again with a similar report posted in 1/07.
[*]Some users on that thread discuss modifying the wine environment to allow viruses to run on wine by adding missing windows .dll IMO this is akin to saying "windows viruses run on windows code" which is very different then windows viruses running on wine code.
[*]So if you modify the code be sure you understand the security implications.[/list]

IMO this falls under social engineering and/or the caution about running code from untrusted sources ...

[indent]He he he ... including windows .dll[/indent]

---

### Post by Gen2ly on 2007-07-29
With Security always changing its nice to read something that is new and thought about well.  After a little more research ( the recent security holes I've seen Firefox... ) it's best to treat cookies ( or javascript FTM ) like a firewall. Block EVERYTHING and allow trusted in. So I appreciate this being pointing out. It's, to be truthful, something I hadn't thought about that much.  I would like to add, that while blocking everything and entering in all your trusted sites is a laborious process there is a way to make it simpler. [Extended Cookie Manager]("https://addons.mozilla.org/en-US/firefox/addon/1243") will allow the users in a pop-up menu to allow what sites you want.  

Appreciate the help!

---

### Post by euler_fan on 2007-08-12
It looks like the ntop link is dead.

[This one looks good]("http://www.ntop.org/news.html").

Thanks.

P.S: I've already sent two or three people to the guide today.

---

### Post by bodhi.zazen on 2007-08-12
> **euler_fan said:**
> It looks like the ntop link is dead.

[This one looks good]("http://www.ntop.org/news.html").

Thanks.

P.S: I've already sent two or three people to the guide today.

Thanks, I fixed the links (I found another dead one)

---

### Post by euler_fan on 2007-08-13
I would like OSSEC-HIDS to start on boot, but . . . 

Is there still an issue with making OSSEC-HIDS do this?

I use a lappy and commute with it alot, so it is coming up and down 2-3 times per day.

When I run htop and manually start OSSEC, I get all the different monitoring processes coming up.

When I do a fresh reboot and don't manually start OSSEC, I don' t seem them in htop.

There is an ossec init.d script, and when I tried to set it to auto-run on startup I got a message kicked back that it was already configured for this.

I will post all the code, etc, when I get back to my laptop a little later today.

Thanks . . .

---

### Post by KevinM1 on 2007-08-13
Some general suggestions/questions for the big stickied security thread:

Mind putting up a section about iptables? :)

I tried installing apache2's mod_security, but it didn't work.  Is it available for 7.04?  Is the install syntax listed in the subsection correct?
```
sudo apt-get libapache2-mod-security
```

Mail server options/security concerns?

Thanks! :D

---

### Post by Seisen on 2007-08-13
> I tried installing apache2's mod_security, but it didn't work. Is it available for 7.04?
For some reason it was removed from the feisty repositories that is why you can't find it.

---

### Post by euler_fan on 2007-08-14
> **euler_fan said:**
> I would like OSSEC-HIDS to start on boot, but . . . 

Is there still an issue with making OSSEC-HIDS do this?

I use a lappy and commute with it alot, so it is coming up and down 2-3 times per day.

When I run htop and manually start OSSEC, I get all the different monitoring processes coming up.

When I do a fresh reboot and don't manually start OSSEC, I don' t seem them in htop.

There is an ossec init.d script, and when I tried to set it to auto-run on startup I got a message kicked back that it was already configured for this.

I will post all the code, etc, when I get back to my laptop a little later today.

Thanks . . .

It turns out that if you restart your machine and it automatically connects to the network then OSSEC-HIDS starts up during boot/reboot automatically like it should.

On the other hand, if your machine does not automatically connect at startup and must be manually connected (hidden SSID for wireless network for instance) then OSSEC-HIDS will fail to start at boot/reboot and must be started manually AFTER connecting to the network.

I think this has something to do with the automatic email notices. If turned on, it checks for network connectivity. If it does not find it then the entire program fails to load. This is based on what happens when trying to start OSSEC while my laptop was not connected to the network.

I think you can lose network connectivity and OSSEC will continue to run.

---

### Post by southernman on 2007-08-16
@bodhi.zazen

I appreciate the time and effort you took writing this Guide. Once I've gone through all the info thoroughly, expect to see me back with questions. <scared now aren't ya> ;)

Thank you too, to others that contributed either directly or incognito.

---

### Post by southernman on 2007-08-23
FWIW - if you'd like to add this to your sticky on Ubuntu Security it'd probably make a nice find for those in need:

It's a pdf of a book called Hardening Apache by Tony Mobily you can buy it in print form or download the pdf from [here]("http://www.apress.com/ApressCorporate/supplement/1/320/1590593782-1829.pdf")

If there is any question about the source [here]("http://www.google.com/search?q=Hardening+Apache&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a") is the Google search I ran to find the book.

I have another to add, but I can't find the link to it and I want to be certain it's ok to post here before doing so.

Enjoy... I did!

---

### Post by southernman on 2007-08-23
> **KevinM1 said:**
> Some general suggestions/questions for the big stickied security thread:

Mind putting up a section about iptables? :)

I tried installing apache2's mod_security, but it didn't work.  Is it available for 7.04?  Is the install syntax listed in the subsection correct?
```
sudo apt-get libapache2-mod-security
```

Mail server options/security concerns?

Thanks! :D
Kevin,

It shows for me when I do an apt-cache search mod_security. Do you have universe repos enabled?

---

