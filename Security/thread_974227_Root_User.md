---
title: "Root User"
date: 2008-11-07
forum: Security
---

### Post by Quarkrad on 2008-11-07
Forgive basic question - I'm new to Ubuntu/Linux.  Read this on web in context of general surfing and cookies/mailware-

...the securities are better unless you're crazy and use the root user....

I think I know what he is talking about - is it the same as surfing in Windows with Administrator rights?   If it is I think I do have root user privilege - as I am the only user.  A couple of questions-

how do I know/find out?
what should I do to change and how?

Forgive me if I ask for not too many 'Linux code' type replies, or if not possible then please give me full list of codes.  As a newbie it is a bit daunting - but I'm learning!

---

### Post by psusi on 2008-11-07
You can't log in as root in Ubuntu by default, so you have nothing to worry about.  If you need to execute a command with root permission, you just prefix it with sudo.

---

### Post by SuperSonic4 on 2008-11-07
> **psusi said:**
> You can't log in as root in Ubuntu by default, so you have nothing to worry about.  If you need to execute a command with root permission, you just prefix it with sudo.

+1 root is disabled in ubuntu to stop newbies logging in as root and destroying the system. Using sudo gives temporary root privileges while being logged in as user and is thus safer since you can't accidentally delete system files. Logging in on your only account is still logging in as user

---

### Post by Quarkrad on 2008-11-07
Many thanks - sorry for obvious question.  Can't get use to not 100% concern about virus/spyware/mailware as per windows.   Should I install something(s) for piece of mind?   I dual boot and have other partitions on PC with winXP (until I find Linux appts that can do what windows appts can do).

---

### Post by m_duck on 2008-11-07
In terms of viruses etc you are pretty much safe in linux due to the way it is designed, so a virus scanner isn't really necessary. However, some people say that when dual booting with windows and sharing files between the two, that you should scan the shared files / partitions. I dual boot with windows, but do not run any virus scanner in linux. I do of course have one in windows and I have not yet had any problems with it set up this way (touch wood).

A couple of good resources in terms of security in ubuntu:
[Psychocats security](http://www.psychocats.net/ubuntu/security)
[Ubuntu community security page](https://help.ubuntu.com/community/Security)

---

### Post by psusi on 2008-11-07
> **Quarkrad said:**
> Many thanks - sorry for obvious question.  Can't get use to not 100% concern about virus/spyware/mailware as per windows.   Should I install something(s) for piece of mind?   I dual boot and have other partitions on PC with winXP (until I find Linux appts that can do what windows appts can do).

I know it is a bit of a shock to the system, but get used to it; you're perfectly safe ;)

---

### Post by SuperSonic4 on 2008-11-07
> **m_duck said:**
> In terms of viruses etc you are pretty much safe in linux due to the way it is designed, so a virus scanner isn't really necessary. However, some people say that when dual booting with windows and sharing files between the two, that you should scan the shared files / partitions. I dual boot with windows, but do not run any virus scanner in linux. I do of course have one in windows and I have not yet had any problems with it set up this way (touch wood).

A couple of good resources in terms of security in ubuntu:
[Psychocats security](http://www.psychocats.net/ubuntu/security)
[Ubuntu community security page](https://help.ubuntu.com/community/Security)

+1

I installed klamav (in ubuntu you'd want clamav) which are frontends to clamtk which is a virus scanner. I've set mine up to scan /media daily just to ease paranoia. It's wise to keep protection on windows and that will suffice on its own

---

### Post by Gizkaguy on 2008-11-07
> **Quarkrad said:**
> Forgive basic question - I'm new to Ubuntu/Linux.  Read this on web in context of general surfing and cookies/mailware-

...the securities are better unless you're crazy and use the root user....

I think I know what he is talking about - is it the same as surfing in Windows with Administrator rights?   If it is I think I do have root user privilege - as I am the only user.  A couple of questions-

how do I know/find out?
what should I do to change and how?

Forgive me if I ask for not too many 'Linux code' type replies, or if not possible then please give me full list of codes.  As a newbie it is a bit daunting - but I'm learning!

Unless something extraordinary happened, your not root. Ubuntu, by default, does not have a root user that can be logged into. Your current account uses *sudo* -- which gives temporary permissions with your password. While you are an administrator, you are not root.

For piece of mind, I would go to a terminal (If GNOME, Applications -> Accessories -> Terminal) and type *sudo apt-get install firestarter klamav*

Sudo I just explained.
Apt-Get is aptitude. It is the Ubuntu package manager, also known as synaptic.

Your already running a firewall (iptables), but Firestarter will help you configure it. It's menu entry should be Applications -> System Tools/Internet -> Firestarter

Klamav is the KDE frontend to ClamAV, an antivirus application. You can run it on Windows, too. Although, expect false positive on a Linux system.
And, you don't really need a virus scanner on Ubuntu.

Good luck!

SuperSonic4: ClamTK is a front end to ClamAV. And you can install Klamav in GNOME -- or any other graphical desktop environment. I personally recommend Klamav over ClamTK.

---

### Post by Hyper Tails on 2008-11-07
Yea I got clamav and firestarter I think It makes my system safer than ever

now Linux Is NOT perfectly safe but It's Pretty safe :)

---

### Post by cariboo on 2008-11-07
Nobody has mentioned that the av scanners for Linux only scan for Windows viruses. There are no known Linux viruses in the wild at the moment, and the only way they could affect you installation is if you install the malware as root.

Jim

---

### Post by bodhi.zazen on 2008-11-08
> **Quarkrad said:**
> I think I know what he is talking about - is it the same as surfing in Windows with Administrator rights?   If it is I think I do have root user privilege - as I am the only user.

You are asking good questions, nice to see.

Take a look at the security stickies in this section.

I would add, logging in as an administrator on Windows would be logging in as root in Ubuntu.

In Ubuntu if you are a member of the administrator group you can access administrative functions with sudo, gksu if you are using X (graphical) applications.

Some people make a second user, one who is not in the admin group, for daily use but in general this is not necessary.

See also : [uhelp]community/RootSudo[/uhelp]

---

### Post by Chayak on 2008-11-09
> **SuperSonic4 said:**
> +1

I installed klamav (in ubuntu you'd want clamav) which are frontends to clamtk which is a virus scanner. I've set mine up to scan /media daily just to ease paranoia. It's wise to keep protection on windows and that will suffice on its own

ClamAV is pretty much useless when it comes to malware detection.  It has the worst detection rates of any of the major AV scanners and only catches the old stuff that it has signatures for.  It's trivial to change a malware sample so it's not detected.  You can insert a single NOP \x90 ( a "no operation" instruction in assembly that simply gets skipped over when an executable runs ) instruction most of the time in the right place and it won't be detected at all.

If you want to transfer your files from Linux to windows and you have an executable run it through [Virustotal]("http://www.virustotal.com/") it'll put it through most of the AV scanners out there and give you a report back.  It's better than using a single scanner as sometimes certain vendors have signatures that others don't.  Even if it shows clean it doesn't mean it's safe as I see samples weekly that don't show up on anything and it's attributed to the simple fact that the malware author used a custom packer or armorer.  It can be a common piece of malware and it simply won't be detected.

To think people wonder why malware researchers use Linux...

---

