---
title: "Misc security questions"
date: 2008-08-13
forum: Security
---

### Post by Rakanishu on 2008-08-13
To begin with, I've read the interesting and informative FAQ on the site.

I would like to use Ubuntu for the following:
   Finance (accessing bank, paypal, ebay, my stocks and using VISA)
   Forum usage
   Instant messaging
   Downloading music and videos from private trackers

[edit by OldSoldier: removed reference to illegal activity]

What I want to know, is:

1. If I dual-boot Linux and Windows, will the Linux partition maybe be made insecure if the Windows partition is infected with something or hacked? Can I safely have a shared NTFS partition so that I can access media files in both Windows and Linux?

2. Is uTorrent and GAIM safe default, or do I have to make adjustments to the firewall? I mean, they open up ports and they query, which sniffers and hackers then can use to access the computer. When using Windows I always get attacks when using torrents for example.

3. What are the firewall settings I should use for this configuration?


Thanks in advance

---

### Post by HermanAB on 2008-08-13
No, yes, yes, no, none.
;)

Relax and enjoy your new system!

Herman

---

### Post by Rakanishu on 2008-08-13
> **HermanAB said:**
> No, yes, yes, no, none.
;)

Relax and enjoy your new system!

Herman

I appreciate your reply, and I don't want to be rude, but I don't think that yes or no are informative answers. It's never as simple as that, and even if it is I am interested in knowing why. 
I won't relax until I know.

Please. :-P

---

### Post by wyliecoyoteuk on 2008-08-13
He has answered your questions 100%.
[edit by OldSoldier: removed references to illegal activity]
If you want security, either dump windows and use Ubuntu, or pay for a windows license.

---

### Post by Rakanishu on 2008-08-13
> **wyliecoyoteuk said:**
> He has answered your questions 100%.

Depends on how you see it. While he is surely right, I ask because I am curious and want to know more.
And as I said, it's never as simple as yes or no.
A friend tells me for example that malware could theoretically access a UNIX system from Windows partition.

[QUOTE=wyliecoyoteuk][edit by OldSoldier: removed references to illegal activty]
If you want security, either dump windows and use Ubuntu, or pay for a windows license.[/QUOTE]

Apparently, your view is that forums are not meant for users sharing information and help with each other. I haven't managed to get this information with google or from the FAQ, that's why I turn here.
Unofficial is by the way an ironic expression.

And please, if you have nothing to contribute, then don't.

---

### Post by cdenley on 2008-08-13
If you install wine, then open an infected windows executable, it could do damage. Windows can't write to the linux partition unless you install a driver. It is very, very unlikely you will get a virus using linux unless you run it in wine.

Torrents don't usually work well if you block the ports they listen to. Those "attacks" you mention were probably just peers trying to establish a connection to you. I don't think services like gaim listen for connections, since they establish the connection to an external server.

Firewalls are only meant to block network servers that the user never intended to run (trojans, microsoft file sharing), or sometimes advanced filtering/routing. Firewalls aren't necessary in Linux and aren't used by default, but certainly are available. You are always vulnerable to someone sniffing your traffic, which is why encryption is important.

---

### Post by Rakanishu on 2008-08-13
> **cdenley said:**
> If you install wine, then open an infected windows executable, it could do damage. Windows can't write to the linux partition unless you install a driver. It is very, very unlikely you will get a virus using linux unless you run it in wine.

Torrents don't usually work well if you block the ports they listen to. Those "attacks" you mention were probably just peers trying to establish a connection to you. I don't think services like gaim listen for connections, since they establish the connection to an external server.

Firewalls are only meant to block network servers that the user never intended to run (trojans, microsoft file sharing), or sometimes advanced filtering/routing. Firewalls aren't necessary in Linux and aren't used by default, but certainly are available. You are always vulnerable to someone sniffing your traffic, which is why encryption is important.

Thanks for your answer!

So a hacker would have to install a driver to be able to access the Linux partition?
And not only that, but also know that there is a Linux partition at all?

But wouldn't a shared Windows/Linux partition pose a slightly bigger risk then, since you can write to it from Windows too?

Regarding the firewall: from what I understand, the firewall by default blocks all traffic that isn't initiated from an application on the system?
But using a program that listens for a connection, like utorrent, can theoretically cause the ports involved to be breached?

---

### Post by cdenley on 2008-08-13
> **Rakanishu said:**
> Thanks for your answer!

So a hacker would have to install a driver to be able to access the Linux partition?
And not only that, but also know that there is a Linux partition at all?

But wouldn't a shared Windows/Linux partition pose a slightly bigger risk then, since you can write to it from Windows too?

Regarding the firewall: from what I understand, the firewall by default blocks all traffic that isn't initiated from an application on the system?
But using a program that listens for a connection, like utorrent, can theoretically cause the ports involved to be breached?

Yes.

A virus can be written from windows, but it couldn't do any damage in linux unless you run it.

If you don't have anything listening for traffic on that port, then it is rejected. That has nothing to do with the firewall, there is simply nothing for the system to do with it so it rejects it. When you have an application like utorrent listening, the security depends on how well utorrent handles it's connections.

---

### Post by lisati on 2008-08-13
With a firewall (and other tools to protect your system) an approach based on a combination of techniques can sometimes be helpful. Many routers these days come with some kind of firewall-style options, which can be used in conjunction with whatever you choose for your OS.

---

### Post by Rakanishu on 2008-08-13
> **cdenley said:**
> Yes.

A virus can be written from windows, but it couldn't do any damage in linux unless you run it.

If you don't have anything listening for traffic on that port, then it is rejected. That has nothing to do with the firewall, there is simply nothing for the system to do with it so it rejects it. When you have an application like utorrent listening, the security depends on how well utorrent handles it's connections.

That's interesting.
In Windows, it's enough to have malware on your computer to have it do harm, from what I know.
But it has to be actively opened in UNIX systems?

So the security when it comes to listening applications, doesn't have anything to do with the firewall?

> **lisati said:**
> With a firewall (and other tools to protect your system) an approach based on a combination of techniques can sometimes be helpful. Many routers these days come with some kind of firewall-style options, which can be used in conjunction with whatever you choose for your OS.

But you still have to open up the ports for the programs you want to use.
So why would several layers of firewalls make any difference, when there must always be some port open?

Is there any good book in this subject? Not specifically UNIX but general internet security knowledge?

---

### Post by brian_p on 2008-08-13
> **Rakanishu said:**
> 

So the security when it comes to listening applications, doesn't have anything to do with the firewall?

Correct. The application either does its job securely or it doesn't. If it doesn't a firewall will not provide whatever security is lacking.

> But you still have to open up the ports for the programs you want to use.

Yes, but it is really the other way round. You run the service and that opens the port on the machine. Stop the service and the port is closed.

> So why would several layers of firewalls make any difference, when there must always be some port open?

You have the correct idea. It doesn't make any difference to the fundamental security of the service.

---

### Post by Rakanishu on 2008-08-13
So what's a firewall for if the security largely hangs on the applications themselves, and when all ports are blocked anyway unless requested by an application?

---

### Post by cdenley on 2008-08-13
> **Rakanishu said:**
> So what's a firewall for if the security largely hangs on the applications themselves, and when all ports are blocked anyway unless requested by an application?

Exactly. The only reason to run a firewall is to protect you from a server you foolishly enabled without realizing it, or to provide advanced filtering such as blocking/allowing certain hosts or limiting connections. It is recommended on Windows because it has file-sharing enabled by default (or at least used to), and people install all kinds of software from unreliable sources without knowing what it does.

For a desktop ubuntu user, if you pay attention to what you install, configure servers correctly, and install from reliable sources (ubuntu repository), there is no need for a firewall.

---

### Post by brian_p on 2008-08-13
> **Rakanishu said:**
> So what's a firewall for if the security largely hangs on the applications themselves, and when all ports are blocked anyway unless requested by an application? 

Firewalls filter packets based on port, protocol and IP. So you might want to restrict who you serve based on the IP. The BBC does this with its iplayer material. Or it could be desirable to filter outgoing packets. For example, force all traffic destined for port 25 through your own mail server rather than being sent directly. I'll leave you to think of reasons why either of these two techniques might be used but neither is a response to some inherent insecurity in the service.

A firewall can also be useful if you have no control over a machine, which is not the case with Linux. The widespread belief a firewall is a necessity arises in the Windows world because control of the OS is difficult or impossible.

---

### Post by Rakanishu on 2008-08-13
Thanks for the clarification guys.

So basically, entirely broken down, if I just use Mozilla Firefox and GAIM, I won't need a firewall at all since they are safe and don't listen to queries? Yet if they were unsafe, theoretically, I should try to control their behaviour with a firewall?


Some others security related questions came up too. Help with them could be nice. :P

1. I understand that a Linux partition is entirely safe even if it shares the same HDD as an "infected" Windows system. But my Windows XP runs some program after installation, during boot. Is it possible that an "altered" Windows XP installation can install stuff into the boot sector or something like that, which then poses a threat to the privacy and safety of the Linux partition?

2. When I installed Ubuntu, after removing the disc when the computer was shutting down, the computer didn't shut down it turned out. I just was at a "DOS-like" prompt, like: "$Ubuntu: _____"
And when I pressed Ctrl-Alt-Del, the system froze after showing the message about "Ctrl-Alt-Delete Pressed".

Were there any important things related to the installation or security that should have happened during shutdown after first installation, or was it perfectly safe to turn off the PC?

---

### Post by cariboo on 2008-08-14
never mind

---

### Post by Oldsoldier2003 on 2008-08-14
> **Rakanishu said:**
> 
Apparently, your view is that forums are not meant for users sharing information and help with each other. I haven't managed to get this information with google or from the FAQ, that's why I turn here.
Unofficial is by the way an ironic expression.

And please, if you have nothing to contribute, then don't.

The forums are not meant for discussing illegal activities. Although in must cases I would agree with, "And please, if you have nothing to contribute, then don't." - right now you don't have a leg to stand on. 

Consider this a learning experience, you could very easily have formulated your question without violating the forum rules and getting the responses you have received.

---

### Post by Rakanishu on 2008-08-14
> **Oldsoldier2003 said:**
> The forums are not meant for discussing illegal activities. Although in must cases I would agree with, "And please, if you have nothing to contribute, then don't." - right now you don't have a leg to stand on. 

Consider this a learning experience, you could very easily have formulated your question without violating the forum rules and getting the responses you have received.

Since I didn't discuss piracy or how to use pirated software, but rather the effects an insecure Windows could have on Ubuntu, I thought it was okay. If not, I'm sorry, it won't happen again. Sergeant!

I think the responses in this thread have been very good and helpful though up to this point.

---

### Post by Oldsoldier2003 on 2008-08-14
> **Rakanishu said:**
> Since I didn't discuss piracy or how to use pirated software, but rather the effects an insecure Windows could have on Ubuntu, I thought it was okay. If not, I'm sorry.

I think the responses in this thread have been very good and helpful though.

I agree that most of the responses in this thread have been very good replies. however the warning stands. It was very clear from the original post what you meant. We cannot allow this behavior on the Ubuntu forums because it could lead to legal action against the Forum. These forums are a great community asset and it would be a shame for the community to lose access to the forum over some perceived illegal activities. This is why we are not very tolerant with discussions of illegal software or  links to hacked/copyright infringed/pirated material.

---

### Post by lisati on 2008-08-14
> **Rakanishu said:**
> 
But you still have to open up the ports for the programs you want to use.
So why would several layers of firewalls make any difference, when there must always be some port open?

A lot of it boils down to well-informed choice. I don't run a server, so other than setting up some basic protection for the wireless portion of my home network to keep the neighbours out, together with a bit of good sense when checking emails, the default settings in my hardware and software are sufficient to keep out intruders.

---

### Post by Rakanishu on 2008-08-14
> **Oldsoldier2003 said:**
> I agree that most of the responses in this thread have been very good replies. however the warning stands. It was very clear from the original post what you meant. We cannot allow this behavior on the Ubuntu forums because it could lead to legal action against the Forum. These forums are a great community asset and it would be a shame for the community to lose access to the forum over some perceived illegal activities. This is why we are not very tolerant with discussions of illegal software or  links to hacked/copyright infringed/pirated material.

Warning duly noted. Ubuntu clearly relies very much on the forums.

---

### Post by hyper_ch on 2008-08-14
> **cdenley said:**
> Windows can't write to the linux partition unless you install a driver. It is very, very unlikely you will get a virus using linux unless you run it in wine.
However windows malware could remove the whole linux partition. So it doesn't really matter that Windows can't by default alter stuff within the files contained when you can erase the whole thing.

So, linux partitions/drives are not really safe when running Windows as windows malware could format them.

> **cdenley said:**
> Firewalls are only meant to block network servers that the user never intended to run (trojans, microsoft file sharing), or sometimes advanced filtering/routing.
Firewalls on windows have also a different purpose that does not (yet) exist on linux. In windows with all the proprietary products you often have products calling home. Or if you got your software from "dubious" sources it might be infected with malware that spies on you and phones home. Due to the nature of open source such behaviour is not common in linux and hence linux basically only cares at who is trying to connect me and not also preventing "who is phoning home".

---

### Post by cariboo on 2008-08-14
> However windows malware could remove the whole linux partition. So it doesn't really matter that Windows can't by default alter stuff within the files contained when you can erase the whole thing.

So, linux partitions/drives are not really safe when running Windows as windows malware could format them.

hyper_ch your concept intrigues me, windows can't really tell what a partition is formatted as, except for its own format fat32, ntfs etc. So it wouldn't matter if it was Linux, Solaris or BSD, malicious software, would only have to know there is a different type of partition and then know how to delete it, is this what you are getting at?

Jim

---

### Post by Camilia on 2008-08-15
I am beginning to wonder if I have a virus on my computer. For at times the cursor gets stuck and doesn't move. Sometimes typing gets blocked. One time could not log in to a forum. I was not able to click the log in button

If I do the problem started in windows xp. 

In windows had 3 trojan viruses get in. I think I wiped them out with superantispyware. Then downloaded SysSafety (System Safety Monitor) 30 day trial security. It was trying to make changes to my register. Thus turned of the computer at the tower, turned it on and put ubuntu disk in. Download ubuntu disk in full form making permanent changes to computer.

How do I download a program, to check my computer?

---

### Post by cariboo on 2008-08-15
I would say that you more then likely don't have an infection of any sort, as a virus has to be run as root to install it self. It more then likely is some sort of misconfiguration somewhere.

Jim

---

### Post by Rakanishu on 2008-08-17
I understand that a Linux partition is entirely safe even if it shares the same HDD as a malware-infected hacker-attended Windows system.

But is there any possibility of going through alternate ways, like the boot sector or something like that, that doesn't run directly under Windows? Maybe by running some program when Windows installs and reboots that puts the malware there.

Just want to know, last question.

---

### Post by hyper_ch on 2008-08-17
> **Rakanishu said:**
> I understand that a Linux partition is entirely safe even if it shares the same HDD as a malware-infected hacker-attended Windows system.

If the hacker gains access he could just decided to erase the whole linux partition....

---

### Post by Rakanishu on 2008-08-17
Yeah, I understand that. I'm not asking from a hacker perspective.
Rather if it's possible to make the Linux system insecure by installing something in the boot sector or something like that, for example during Windows installation, something that doesn't run directly under Windows but still poses a security threat to Linux.

---

### Post by hyper_ch on 2008-08-17
well, if a hacker has access he can install the ext2/3 drivers and read the data also...

---

### Post by theduffman on 2008-08-18
> **cariboo907 said:**
> I would say that you more then likely don't have an infection of any sort, as a virus has to be **_run as root to install it self._** It more then likely is some sort of misconfiguration somewhere.

Jim

Ive just thought of something.. I run something as root, say i wanna edit sources.list and i type in the password, and it caches it so i dont have to keep typing for so long.. couldnt something use this?  the fact its cached could pose a security risk (?)

---

### Post by cdenley on 2008-08-18
> **theduffman said:**
> Ive just thought of something.. I run something as root, say i wanna edit sources.list and i type in the password, and it caches it so i dont have to keep typing for so long.. couldnt something use this?  the fact its cached could pose a security risk (?)

I think so, IF someone gains shell access as your admin user then continually try over and over until you use sudo on the matching tty. Of course if they have shell access as your admin user, they can also create aliases for programs like sudo to trick you into logging your password or sending it over the net. To prevent sudo from "caching" your password, you can add this using "sudo visudo".
```

Defaults env_reset**,timestamp_timeout 0**

```
To prevent someone with shell admin access from creating aliases for you
```

sudo chattr +i ~/.bashrc

```

---

