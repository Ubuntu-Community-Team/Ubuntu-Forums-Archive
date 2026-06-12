---
title: "General security"
date: 2010-10-25
forum: Security
---

### Post by Mirrorboy on 2010-10-25
Because of certain system incompatibilities among the computers in my house, my dad has been paying for 2 different anti virus suites for some time now (Kaspersky and Zonealarm). Well, the Zonealarm just ran out on my dad's desktop and the Kaspersky is incompatible with it since it's really old and not worth it to upgrade. I presented the idea of switching from Windows XP to Xubuntu since it runs lightly and doesn't require an anti virus program. He brought up the question that he does a lot of banking and stuff on his desktop and would want that traffic to be protected. I know that Ubuntu has a built in firewall, but I can't imagine it being the great wall of china. I was wondering if there were more secure programs available or if one was even needed given the existing stability of Linux.

---

### Post by nerdleturtle on 2010-10-25
[http://www.fs-security.com/](http://www.fs-security.com/)
 
A nice suggestion. Honestly, if your network is encrypted, it should be fine. Best of luck! Trust me, Linux makes you forget what a virus is! :)

---

### Post by cstudent on 2010-10-25
I think he would be much better off if he could convert to Linux. Virtually no fear of attracting a virus and as long as he's sure the bank site is using a secure connection (https) he should be OK. If his computer is behind a router, even better.

---

### Post by kreggz on 2010-10-26
You should take into consideration what applications he requires. If he is heavily dependent on Windows programs it will present a challenge in migrating to Linux.

Microsoft offer a free antivirus program which works quite well. [http://www.microsoft.com/security_essentials/](http://www.microsoft.com/security_essentials/)

---

### Post by eraker on 2010-10-26
If he uses Photoshop or Quicken software, those are generally two main areas where I've found it difficult to convince people to migrate. If he does all banking and taxes online (totally possible), then I would think it's no big deal.

Further, Linux is great for security assuming your system is set-up well and you're using a router, etc. As far as firewall suggestions go, I've been a fan of [ufw]("https://help.ubuntu.com/community/UFW") for a long time. It's very easy to use and understand and in this way is an ideal firewall program for someone (like me) who's not too great at reading/editing ipTables.

Anyway, with a router, good access controls on folders, excellent passwords, and finally with a simple firewall, most Linux systems should be pretty secure.

---

### Post by CharlesA on 2010-10-26
> **nerdleturtle said:**
> [http://www.fs-security.com/](http://www.fs-security.com/)
 
A nice suggestion. Honestly, if your network is encrypted, it should be fine. Best of luck! Trust me, Linux makes you forget what a virus is! :)

Please don't suggest firestarter. It's no longer under development and ufw/gufw are a better choice if you want to use something to configure a firewall.

> **eraker said:**
> If he uses Photoshop or Quicken software, those are generally two main areas where I've found it difficult to convince people to migrate. If he does all banking and taxes online (totally possible), then I would think it's no big deal.

Further, Linux is great for security assuming your system is set-up well and you're using a router, etc. As far as firewall suggestions go, I've been a fan of [ufw]("https://help.ubuntu.com/community/UFW") for a long time. It's very easy to use and understand and in this way is an ideal firewall program for someone (like me) who's not too great at reading/editing ipTables.

+1.

> Anyway, with a router, good access controls on folders, excellent passwords, and finally with a simple firewall, most Linux systems should be pretty secure.

Ubuntu desktop is secure out of the box, since it has no listening services that listen on external interfaces.

See [here]("https://wiki.ubuntu.com/SecurityTeam/Policies").

---

### Post by Mirrorboy on 2010-10-26
He only uses his desktop for banking and buying stuff. He has a laptop running Windows 7 64bit that he uses for his job (AutoCAD, Photoshop stuff like that). We have a 3-user subscription to Kaspersky that we wouldn't need anymore if he switched. I was planning on putting Xubuntu on his desktop and I would switch from Windows 7 to Ubuntu. Then all he would need would be a 1-user subscription for his laptop. Really the only Windows programs he'd need would be MS Office and that runs perfectly with Wine. We have a router that all the computers in my house connect to and all the banking sites are HTTPS. One thing I forgot to mention is that it needs to have a UI. My dad is sort of an old dog when it comes to these things and he knows absolutely nothing about Linux terminal (I'd be servicing it since I have more experience with the OS). So whatever firewall ends up being installed has to have some sort of UI that he can interface with. Or like I said, if Xubuntu even needs a firewall at all. I'm mainly looking for somebody to tell me if one is even needed and then suggest a good one if it is needed.

---

### Post by Chayak on 2010-10-26
I know Kaspersky comes in a 3 license pack so you might might as well get your money's worth for the subscription.

The setup that I'd suggest for banking is a live CD or USB.  You get a known good system every time you boot and you can carry it around.

What I use is a little more elaborate.  I have a stripped and locked down Ubuntu base on my workstation that runs VMware workstation.  There's a non-persistant VM that I use for banking, another for general use, and a few others for reverse engineering  I do work as a malware analyst so it's probably overkill for a regular user, but it fits my needs and works well.

---

### Post by CharlesA on 2010-10-26
One thing to note about the livecd thing: They aren't usually up-to-date with the latest security updates and patches.

Just wanted to throw that out there.

---

### Post by movieman on 2010-10-26
> **CharlesA said:**
> One thing to note about the livecd thing: They aren't usually up-to-date with the latest security updates and patches.

While that's true, it's not likely to be a problem if you just boot up, access your bank web site and shut down, since the bad guys can't install anything on the CD for the next time you run. But if you go to some dubious site beforehand that breaks into the web browser through an old exploit and then captures and sends out your banking password you'd be screwed.

I guess that's a good reason to ensure the live CD doesn't come with Flash installed.

---

### Post by CharlesA on 2010-10-26
> **movieman said:**
> While that's true, it's not likely to be a problem if you just boot up, access your bank web site and shut down, since the bad guys can't install anything on the CD for the next time you run. But if you go to some dubious site beforehand that breaks into the web browser through an old exploit and then captures and sends out your banking password you'd be screwed.

That's true. Personally, I'd rather use an up-to-date OS to do my banking. Using a VM with snapshots works for that.

> I guess that's a good reason to ensure the live CD doesn't come with Flash installed.

As for flash, I believe it's not included by default due to a different reason.

---

### Post by Mirrorboy on 2010-10-26
The LiveCD is a good idea, but my dad wouldn't go for it. In addition to banking, he uses it like a regular computer. I only highlighted the banking because he brought up a security question. It's also the only computer in the house with a printer hooked up, so we use it to print. What I'm gathering from this thread is that an additional firewall isn't needed because of the combination of Linux security, Ubuntu's built in firewall, and connecting through a router. Would that be a correct assumption?

---

### Post by CharlesA on 2010-10-26
Correct. you could always enable ufw in ubuntu:

```
sudo ufw enable
```

---

### Post by DodgeV83 on 2010-10-26
> **Mirrorboy said:**
> Because of certain system incompatibilities among the computers in my house, my dad has been paying for 2 different anti virus suites for some time now (Kaspersky and Zonealarm). Well, the Zonealarm just ran out on my dad's desktop and the Kaspersky is incompatible with it since it's really old and not worth it to upgrade. I presented the idea of switching from Windows XP to Xubuntu since it runs lightly and doesn't require an anti virus program. He brought up the question that he does a lot of banking and stuff on his desktop and would want that traffic to be protected. I know that Ubuntu has a built in firewall, but I can't imagine it being the great wall of china. I was wondering if there were more secure programs available or if one was even needed given the existing stability of Linux.

A few issues here:

1.  A firewall doesn't actually "protect" your traffic.  If you send out your username and password in the clear (read - a non "https" website), no firewall will protect you.

2.  Ubuntu's default installation does not require a firewall, because there is literally nothing for it to block.  No ports are open.

Now that that's out of the way, yes, running Xubuntu or Ubuntu on the laptop would be much more secure than Windows + Kaspersky and/or Zonealarm.  Even if you don't download anything with the Windows machine, you can still be infected by a worm, or by someone unknowingly sticking an infected USB stick in the machine...etc.  I recently got a virus on my Windows 7 x64 machine **simply by visiting a webpage, _without downloading anything_**.  This simply is not an issue with Linux.

Side Note:  How old is the computer exactly?  Running Ubuntu instead of Xubuntu might be easier for him, since most online guides and help documents were made for Ubuntu, they might not work correctly under Xubuntu.  Unless it's a really old machine, I would stick to Ubuntu.

---

### Post by bodhi.zazen on 2010-10-26
> **Mirrorboy said:**
> He brought up the question that he does a lot of banking and stuff on his desktop and would want that traffic to be protected. I know that Ubuntu has a built in firewall, but I can't imagine it being the great wall of china. I was wondering if there were more secure programs available or if one was even needed given the existing stability of Linux.

There are several considerations.

When performing online banking there are, in a nut shell, three considerations:

Your (client) computer.
"The internet"
The (server) bank's computer.

You can only control a few variables here, mainly on your client.

Client: 
[indent]Windows: There are a large number of potential security holes, thus it makes sense to add as much security as possible.[/indent]

[indent]Linux: There are much fewer, almost no security holes. How much more do you want to add?[/indent]

On the client side, you should read the security sticky. You can "add" several things.

[list][*]A firewall. by default there are no significant open ports, so not much gained.
[*]Use NoScript !!
[*]Apparmor/SELinux - I personally use NoScript and Apparmor or SELinux.[/list]

See also : [http://ubuntuforums.org/showthread.php?t=671604](http://ubuntuforums.org/showthread.php?t=671604)

BUT: Linux is not windows and you can not simply apply your windows mentality to Linux, you would need to learn Linux security (see the sticky).

"The internet" 
[list][*]Use https.[*]Avoid Phishing.[/list]

On the server side, you can not control the bank's server.

With all that in mind, what do you want to tighten?

---

### Post by Mirrorboy on 2010-10-27
> **DodgeV83 said:**
> Side Note:  How old is the computer exactly?  Running Ubuntu instead of Xubuntu might be easier for him, since most online guides and help documents were made for Ubuntu, they might not work correctly under Xubuntu.  Unless it's a really old machine, I would stick to Ubuntu.

The computer (it's the desktop I'm talking about btw) is from 2002 with 2000 specifications. It's got a 1.3GHz CPU and 640MB of **RDRAM** (I started laughing when I found out it had RDRAM lol). It just isn't worth it to upgrade any component since it's so old. I was thinking Xubuntu because it supposedly runs a lot lighter than Ubuntu. Don't get me wrong, Ubuntu runs great. I'm just looking to avoid lag however I can.

> **bodhi.zazen said:**
> Client: 
[indent]Windows: There are a large number of potential security holes, thus it makes sense to add as much security as possible.[/indent]

[indent]Linux: There are much fewer, almost no security holes. How much more do you want to add?[/indent]

BUT: Linux is not windows and you can not simply apply your windows mentality to Linux, you would need to learn Linux security (see the sticky).

"The internet" 
[list][*]Use https.[*]Avoid Phishing.[/list]

On the server side, you can not control the bank's server.

With all that in mind, what do you want to tighten?

That's true. It's hard to completely change your way of thinking after using Windows for so long. I definitely seem to have gotten an answer that there's no reason to add a firewall. The banking sites are all HTTPS anyway and nothing evil can get in because the OS is sealed up tight.

---

### Post by emarkay on 2010-10-27
Windows:  If the free AVG Windows antimalware program is not enough, then you are using sites you should not be using.

If you are using proper awareness and online security procedures then your online activities should be safe. This included knowing and doing registry tweaks, cache clearing, and a lot of Google research if you are using Windows (and, of course,) you fear more than just a lame-o "script kiddie" or the million to one chance that some Russian cracker gets your account number.

Linux:  While it may be "malware free" but if your network, password, ISP, or application is not secure by default/design, and you are not aware of the "crumbs" on your "HOME" directory, you are still vulnerable to someone with a reason to dig.

If you are going beyond common sense or common law, nothing stops a remote transmitting keylogger under the floorboard, or the appearance of a few extra wires in the junction box...

---

