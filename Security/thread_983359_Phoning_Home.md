---
title: "Phoning Home"
date: 2008-11-15
forum: Security
---

### Post by fuio on 2008-11-15
What i dont understand about linux firewalls is that they are not application controlled. Whats to stop that silly game i just installed from phoning home using port 80?

---

### Post by randy78 on 2008-11-15
Well, nothing is going to stop it... 
If you installed a legit game, you really have nothing to worry about. The most it would do is check for updates, and if you had any doubts about what it was doing, you could read the source code or run Wireshark to sniff the wire.

Open source software isn't known for spying on users.

This is why it's important to only install software from trusted sources (Repos, SourceForge, Official sites, etc.).

Of course, if you're really worried about it, you could: 'sudo ifconfig eth0 down' before playing the game ;)

---

### Post by fuio on 2008-11-15
Id then consider this a major security flaw. Any firewall writers want to take up the challenge and make their firewall application controlled? Id say it would eat firestarter for users.

---

### Post by lisati on 2008-11-15
I'd rather have the firewall control being controlled by the firewall, without the security risk of any old application being able to tinker with the settings. Unless of course you mean having permissions based on the current application, as does Zonealarm....

---

### Post by randy78 on 2008-11-15
Why would you consider this a security flaw? If you aren't sure what a program does before installing it, you shouldn't install it.

And there already is a firewall app that eats Firestarter's lunch... it's called UFW.

You should read [THIS]("http://ubuntuforums.org/showthread.php?t=510812") to help clarify how security on Linux differs from Windows.

---

### Post by Kinstonian on 2008-11-15
Honestly, it's a good question for which I don't know the answer.  I'm sure there has to be a good reason why there isn't a commonly used application aware firewall for Linux like there is for Windows.  Hmmmm....

---

### Post by fuio on 2008-11-15
Im a migrating windows user and all firewalls had port restrictions based on what program was trying to access the internet. When i was looking into linux firewalls i could not find any that would act like say zonealarm or eset. Not sure why, as i use firestarter and its telling me that firefox is access port 80. I cant see why firestarter could not look at what program is trying to access port 80 and block it or allow it.

---

### Post by Kinstonian on 2008-11-15
While this isn't as good as Windows firewalls, I've found a work around.  You can create a user named say *nonet*, and make that user the owner of the program you want to run.  Then using an IPTables rule that contains -m owner --uid-owner nonet -j DROP you can make it so that, and other programs owned by nonet don't have internet access.

---

### Post by lovinglinux on 2008-11-15
> **Kinstonian said:**
> While this isn't as good as Windows firewalls, I've found a work around.  You can create a user named say *nonet*, and make that user the owner of the program you want to run.  Then using an IPTables rule that contains -m owner --uid-owner nonet -j DROP you can make it so that, and other programs owned by nonet don't have internet access.

Interesting trick, but I guess this would create other issues, like the application not being able to write files to your home directory.

Another alternative is to block the IP of the software developer with a simple iptables rule or using [[COLOR="DarkRed"]**moblock**[/COLOR]]("http://moblock-deb.sourceforge.net/").

> **fuio said:**
> Im a migrating windows user and all firewalls had port restrictions based on what program was trying to access the internet. When i was looking into linux firewalls i could not find any that would act like say zonealarm or eset.

I was a big fan o Comodo Firewall when I was a Windows user (3 months ago) and it beats ZoneAlarm with the eyes closed. Nevertheless, I'm very comfortable with Linux firewall now. My initial concern about not being able to block specific programs was basically Windows paranoia. If you only run software from trusted and legal sources, then you don't have to worry about it. But if you don't, then it's not Linux firewall fault.

> **fuio said:**
> Not sure why, as i use firestarter and its telling me that firefox is access port 80. I cant see why firestarter could not look at what program is trying to access port 80 and block it or allow it.

Firestarter is not aware of which program is connecting to the network. What it does is detect the destination port and guess the application based on it, to create real-time log that is easy to read. So basically, it will tell you that Firefox is connecting to the network every time any application connects using port 80 as destination.

I'm not sure, but I remember reading somewhere in the Ubuntu documentation that ufw has plans to implement integration with applications.

Just to clarify, Firestarter and UFW are not firewalls. Ubuntu firewall is called iptables, which is part of the distro. Firestarter and UFW are just firewall managers, which basically means a GUI for creating iptables rules without complication. What you can do with Firestarter and UFW you can do by creating your own iptables rules. But what you can do with iptables rules you do not necessarily can with Firestarter or UFW, because they are simple and limited firewall managers.

> **Kinstonian said:**
> Honestly, it's a good question for which I don't know the answer.  I'm sure there has to be a good reason why there isn't a commonly used application aware firewall for Linux like there is for Windows.  Hmmmm....

1 - Because Linux do not suffer from the same threats as Windows does. For instance, there are no virus for Linux on the wild that could phone home. 

2 - Most Linux applications are open source, so if an application contains spyware it is easily spotted and removed from repositories.

3 - Since most Linux applications are free and there are a lot of them, people are less inclined to install pirated software, thus there is no fear of applications phoning home and giving you up.

---

### Post by Kinstonian on 2008-11-15
> **lovinglinux said:**
> Interesting trick, but I guess this would create other issues, like the application not being able to write files to your home directory.

Good thinking... What about creating a nonet group instead of a user and using --**g**id-owner?

> **lovinglinux said:**
> 
1 - Because Linux do not suffer from the same threats as Windows does. For instance, there are no virus for Linux on the wild that could phone home. 

2 - Most Linux applications are open source, so if an application contains spyware it is easily spotted and removed from repositories.

3 - Since most Linux applications are free and there are a lot of them, people are less inclined to install pirated software, thus there is no fear of applications phoning home and giving you up.

That's probably true to some extent.  I agree, there isn't near as much need for this on *nix as there is on Windows, but there are things like bots on Linux that would make outbound connections.  Personally I would still want to know when a process tries to connect to an IRC server, send spam, or starts doing port scans.

---

### Post by lovinglinux on 2008-11-16
> **Kinstonian said:**
> Good thinking... What about creating a nonet group instead of a user and using --**g**id-owner?

This could work, but I'm not experienced enough to know if other problems could arise.

> **Kinstonian said:**
> That's probably true to some extent.  I agree, there isn't near as much need for this on *nix as there is on Windows, but there are things like bots on Linux that would make outbound connections.  Personally I would still want to know when a process tries to connect to an IRC server, send spam, or starts doing port scans.

I would like to know too, but like Rolling Stones says "You Can't Always Get What You Want" :D

Now seriously, if you are worried about bots you could use [[COLOR="DarkRed"]**moblock**[/COLOR]]("http://moblock-deb.sourceforge.net/") and the [[COLOR="DarkRed"]**spyware blocklist**[/COLOR]]("http://iblocklist.com/list.php?list=bt_spyware").

Is not a perfect solution, but I'm very happy using moblock with iptable rules. I don't even use Firestarer anymore, because moblock run custom iptables scripts whenever I turn it on/off. When I turn it off, my iptables rules script block all network traffic and when I turn it on, it allow only the traffic on ports that I need, but still blocks IPs from several blocklists like spyware, hackers and hijacked. I also configure moblock to run at startup, so I'm always protected.

If you want to monitor blocked connections you can track moblock's log with the following command or use [[COLOR="DarkRed"]**mobloquer**[/COLOR]]("http://mobloquer.foutrelis.com/").

```
tail -f /var/log/moblock.log
```

This will show blocked IPs only. If you want to monitor blocked connections from iptables, then you have to create some additional rules. Let me know if you are interested on this and I will explain.

If you want a simple monitoring program that can display active connections like Firestarter, you can use IPTState.

```
sudo apt-get install iptstate

```

It doesn't show the application which is connecting to the network, but what Firestarter shows is just a guess anyway.

---

### Post by Kinstonian on 2008-11-16
moblock seems pretty cool.  I've heard it mentioned a lot but haven't really checked it out until now.  Looks like it can help keep the script kiddies away. :)

---

### Post by cariboo on 2008-11-16
Your windows mindsets are showing. As previously mentioned if you download programs from trusted sources, you have nothing to worry about. Open sources programs are subject to peer review, there are lots of eyes looking at programs and if anything strange is found with a program, it will either be fixed within a day or two of the problem being found, or it will not be available for download.

If you use Windows programs on Linux, then it is up to you to keep track of what it is doing.

Jim

---

### Post by Kinstonian on 2008-11-16
> **cariboo907 said:**
> Your windows mindsets are showing. As previously mentioned if you download programs from trusted sources, you have nothing to worry about. Open sources programs are subject to peer review, there are lots of eyes looking at programs and if anything strange is found with a program, it will either be fixed within a day or two of the problem being found, or it will not be available for download.

If you use Windows programs on Linux, then it is up to you to keep track of what it is doing.

Jim

I'm not as worried about the programs I download and execute as I am the programs an attacker downloads and executes.  How could being alerted to a process you don't recognize out of nowhere wanting to communicate with an IRC server, SMTP server, SSH server, Web server, FTP server, etc., and then be given the option of blocking or allowing it be a bad thing?  I think more control over what happens on your computer, as well as more visibility into what is happening is a good thing.

---

### Post by randy78 on 2008-11-16
Linux is not Windows... programs don't auto-execute.

If you are running services and daemons on your machine, you should be more concerned with securing those services instead of relying on a simple pop-up to guide you.

Most servers do not even have a GUI, so how would a pop-up notice help there?

The point is, is that there are ways to deal with intruders, such as tripwire, snort, fwsnort, fwknop, hardened kernels, patches and etc...but it's really hard to grasp for those used to things like ZoneAlarm, Norton360, Kaspersky, etc... Things that do all of the thinking for you.
We don't have many security threats in Linux... the weakest link is the person in front of the monitor.

If you're really worried, do a full pen-test of your network and network connected machines, then write a security policy based off of those results.

You are putting all of your eggs in one basket by basing your security policies on the output of a simple pop-up.

---

### Post by stimpack on 2008-11-16
I liked the per-application aspect of Windows firewalls. for example stopping skype sending too much info back to base.

Also this linux mindset of 'use only trusted sources', makes me wonder just how fragile Linux is. I dont see how you can trust anybody... I love google earth, I have to trust it, But I do not want to give up my right to block certain google IPs it talks too.

Surely in an ideal world an application starts with zero permissions and the user chooses what it can do, including its networking capabilties, down to the specific IPs it can and cant talk too.

---

### Post by Kinstonian on 2008-11-16
As the saying goes-- *prevention is ideal, detection is a must*.  I gave an example of a common situation that happens when preventative controls fail, and how an application aware firewall can help with detection.  Of course there are other tools that can be used to detect incidents, but just as you use layers of preventative measures to prevent incidents, you should use layers of detective measures to detect incidents when prevention fails.

I don't see how anyone could argue against a more aware firewall.  Something that gives the user more control over what happens on their computer, more information about happens on their computer, something that can help quickly detect intrusions, and something that can help mitigate the impact of an intrusion.  I guess everyone has their own opinions though...

---

### Post by needhelpplease on 2008-11-16
> **Kinstonian said:**
> Honestly, it's a good question for which I don't know the answer.  I'm sure there has to be a good reason why there isn't a commonly used application aware firewall for Linux like there is for Windows.  Hmmmm....

It's a good question, and there is a good answer.

The question is, "isn't it a major problem that any random app that I run, that I may or may not trust, can access the net and do stuff that I don't know what it's doing and I don't want it to do?"  Stuff like phoning home to say "I'm running", or worse stuff like sending data from your computer.

Those are bad things.

But it's not the job of the firewall to prevent those from happening.  Those aren't "network security problems".  Those are "application capability problems".

Ideally, you would like to be able to define a set of capabilities the application has, before it even starts running.  A list for OpenOffice might be:

[LIST=1]
[*]Access the screen, keyboard, and mouse
[*]Load and save files; could be further restricted by file type
[*]Go over the net once a day, to one particular site, to look for updates
[*]Run with a defined limit of CPU and memory use
[/LIST]

Something else, like Skype, which is a closed-source untrusted program many of us run, would have a different set of permissions:

[LIST=1]
[*]Access to screen, keyboard, mouse, webcam, microphone
[*]Load and save only its own configuration files
[*]Talk to computers over the net on certain ports it uses
[*]Listen on certain ports
[*]Consume a limited amount of network bandwidth
[*]Consume a limited amount of CPU and memory
[/LIST]

The key here is we want to define *capabilities* for the application to limit what it can do.  That includes limiting network access, file access, CPU access, and a whole ton of other things.  You can see in the above list, OpenOffice should *never* need to open a socket for listening, while Skype could.  Conversely, OpenOffice might need to access various files from the system, while Skype really should only access its own config files.

This type of capabilities system is far outside the scope of a firewall.  A firewall was created as a blunt instrument to secure things before capability restriction was available.

Now we have a lot more options.  If your application is a Java app, you can quite easily put in a security constraint that denies it outgoing network connections.  Java has had fine-grained security restrictions for apps for a long time.

Linux has it, too.  Two different capabilities systems have been released for Linux: the NSA's SELinux, which I believe was rolled into RedHat; and [AppArmor](http://en.wikipedia.org/wiki/AppArmor).  Both of them can do things like shut off an app's ability to phone home.

The difficulty with them is they have a reputation for being hard to configure.  Further,I'm not sure if AppArmor is still under active development.

Anyway, those are the tools to look at for doing what you want.  Obviously, such capabilities-based mandatory access control is the future of security, and with all the untrusted apps we occasionally want to run, we really need it.  I hope it can eventually come into more mainstream use.

---

### Post by needhelpplease on 2008-11-16
> **cariboo907 said:**
> Your windows mindsets are showing. As previously mentioned if you download programs from trusted sources, you have nothing to worry about. 

That itself is a very poor mindset.  The bad mindset is, "yeah, if it's a signed Ubuntu package from the repos, I trust whatever it's doing."  Wrong!  It's a certainty that programs in the repos have unintentional bugs in them, which could cause security problems.  For instance, there have been libpng versions which allow carefully-crafted images to start running code.  Some of these have, at various times, been officially shipped with Ubuntu etc.  Imagine someone is reading his mail with this "trusted" mail reader which links in libpng (nothing unusual about that).  He then receives and views a dangerous file that triggers this hole and starts "phoning home" including a bunch of private information.

Well, a mail reader should *never* silently contact a remote server except the designated mail server(s).  *But here we see, a "trusted" program from a "trusted" source is now taking unauthorized actions and causing a real security breach!*

This is why all programs should operate with capabilities-based access controls.  The capabilities list for a mail reader would look like:

[LIST=1]
[*]Can access a specified host for IMAP and SMTP
[*]Screen, keyboard, mouse interaction with the user
[*]Config file access
[*]Can make a request to the system to prompt the user for a one-time capability token to save a file or load a file for attachments
[*]Can make a request to the system prompt the user for one-time capabilities to open external content players
[/LIST]

"I only run trusted software" is *not* a viable mindset for security, unless the set of software you run is really really small and doesn't change.  Not realistic for any modern multi-use server or desktop.

---

### Post by cariboo on 2008-11-17
How is viewing a picture that needs libpng going to compromise the system without having root access?

Is this something you have run yourself, or just something you read on some security site?

I know how my system runs, even so I usually run a couple of ports scans every day just to see if there are any services I haven't installed running. I regularly run rootkit scanners, usually twice a day.

As far as trusted software goes, I've been using Debian or one of it's variants for about 8 years, in all that time the repositories have never been compromised. There was an incident where the Debian servers were hacked several years ago, it took them a couple of weeks to get up and running again, but nothing went back online until everything was checked for authenticity. 

Getting a package in the repositories is not something that John J. Cracker can do just out of the blue, he has to submit the source code, a prebuilt .deb won't be accepted. He would have to compromise the servers if he wanted to insert his malware package in the repositories. I admit that it is possible, but the chances are pretty slim, and usually if a security fault is found it is fixed within hours of the problem showing up.

Jim

---

### Post by loko on 2008-11-17
Well,

there are some programs that can act like application firewalls.

You can start reading about using apparmor as an application firewall:

[http://www.linux.com/feature/58789]("http://www.linux.com/feature/58789")

and here:

[http://articles.techrepublic.com.com/5100-10878_11-6104800.html]("http://articles.techrepublic.com.com/5100-10878_11-6104800.html")

Another program is called TuxGuardian, but it seems that this is not developed anymore, but maybe it still works. you can checkout yourself:

[http://tuxguardian.sourceforge.net/]("http://tuxguardian.sourceforge.net/")

---

### Post by Kinstonian on 2008-11-17
Good post needhelpplease, thanks!  I didn't think that AppArmor could help in this situation but I guess it can.  However, could novice users easily create a profile for every program that will by default not allow access to the network, be notified of network access attempts, and make it easy to allow/block access?  Ease of use is important for people who only use a computer for web surfing, and it's important for me too because I don't want to spend 5 minutes everytime I want to allow a new program network access. :)

---

### Post by needhelpplease on 2008-11-17
> **Kinstonian said:**
> Good post needhelpplease, thanks!  I didn't think that AppArmor could help in this situation but I guess it can.  However, could novice users easily create a profile for every program that will by default not allow access to the network, be notified of network access attempts, and make it easy to allow/block access? 

I don't have experience with it myself, but it seems fairly easy to use.  You can run it in "training mode" where it logs all the capabilities the application uses, and generates a profile based on that.  Then you could use that profile as-is, or you could review it and edit.  Let's say that in training mode, your new "desktop calculator" app phones home, and that shows up in the auto-generated profile.  You would remove that from the profile before using it.

---

### Post by needhelpplease on 2008-11-17
> **cariboo907 said:**
> How is viewing a picture that needs libpng going to compromise the system without having root access?

Very easily.  There were in fact bugs in libpng and some other libs like that that are used all over the place which would allow code execution.

Sure, it's not running as root, but if it's running as me, it can scan my emails or wreak all kinds of havoc.  It doesn't need root access to do some very bad things.

> **cariboo907 said:**
> Is this something you have run yourself, or just something you read on some security site?

Have I had a machine hit with an exploit like that?  Not that I'm aware of, but this is solidly documented all over the place.  In a quick search I found something that says it's an exploit:

[http://securityvulns.ru/files/po.c](http://securityvulns.ru/files/po.c)

(I haven't tried it of course.)  And libpng is just one lib.  There were and probably still are exploits in the JPEG lib, XML libs, GIF libs, etc.

The point is, you need to use some type of capabilities restrictions to stop these things.  If an attacker can gain control of your user, that's enough to do plenty of harm, and it's an absolute fact that a whole bunch of programs and libraries for web browsing, mail reading, office tasks, etc, for various operating systems, have shipped with exploitable code in them.

---

### Post by Kinstonian on 2008-11-17
> **needhelpplease said:**
> I don't have experience with it myself, but it seems fairly easy to use.  You can run it in "training mode" where it logs all the capabilities the application uses, and generates a profile based on that.  Then you could use that profile as-is, or you could review it and edit.  Let's say that in training mode, your new "desktop calculator" app phones home, and that shows up in the auto-generated profile.  You would remove that from the profile before using it.

Sounds cool, I'll check it out.  Thanks!

---

### Post by needhelpplease on 2008-11-27
I just looked at AppArmor, and from what I can tell, all it can do is control which *files* the app can access.  That's lame!  It should be able to control which files *and* all the system calls it makes, and also the memory and CPU usage.  It's a start, but only a start.

---

### Post by Kinstonian on 2008-11-28
> **needhelpplease said:**
> I just looked at AppArmor, and from what I can tell, all it can do is control which *files* the app can access.  That's lame!  It should be able to control which files *and* all the system calls it makes, and also the memory and CPU usage.  It's a start, but only a start.

Yeah, I've been reading a little about it too..  It's still a pretty good defense for apps to have against attack (including 0day), but it would be nice if it could do more and at the same time be easier to use.

---

### Post by markharding557 on 2008-11-30
you need to stop being paranoid oday is a windows virus(won't work on linux)

---

### Post by Kinstonian on 2008-11-30
> **markharding557 said:**
> you need to stop being paranoid oday is a windows virus(won't work on linux)

Actually, [0day vulnerabilities](http://en.wikipedia.org/wiki/Zero_day_attack) that I was referring to are completely different from [viruses](http://en.wikipedia.org/wiki/Computer_virus)...

---

