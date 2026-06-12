---
title: "Where are the tools and commands!!"
date: 2008-12-10
forum: Server Platforms
---

### Post by ecsd on 2008-12-10
I'm very used to FreeBSD. I cannot believe that I could install an OS that calls itself a "server" and it would not have GCC or MAKE already there! Not only that but it seems NOTHING is installed - for example I cannot even locate "if-up"!!!! (Ubuntu Server 8.10.)

Will someone please tell me what (few or many) commands I have to issue, to get the BASIC BREAD AND BUTTER ADMINISTRATOR ENVIRONMENT so that the BASIC SYSADMIN COMMANDS are just there?

I know about "apt-get" but I see nothing that will give me a LIST of WHAT I COULD GET. I'm not running a GUI on the server and can't use adept therefore.

Finally is there any place that just SAYS WHAT TO DO for people like me - sysadmins/hacks who are not stupid, but just not used to the Ubuntu methodologies?

Thanks. Sorry for being agitated.

---

### Post by hictio on 2008-12-10
Wow.
Breathe. Slow. Breathe again. Good.
You are among friends, this is a safe place :D


For gcc, make, etc, install:

```

sudo aptitude  install build-essential

```

Also, perhaps you might want to check these:

[https://help.ubuntu.com/community/SwitchingToUbuntu/FromLinux](https://help.ubuntu.com/community/SwitchingToUbuntu/FromLinux)
[https://help.ubuntu.com/community/Servers](https://help.ubuntu.com/community/Servers)
[https://help.ubuntu.com/community/SystemAdministration](https://help.ubuntu.com/community/SystemAdministration)

---

### Post by ecsd on 2008-12-10
Thanks for your advice, will use it and see how much further ...

A rhetorical question perhaps, but doesn't it strike anyone as odd that one has to issue a command to INSTALL ESSENTIAL COMMANDS? And having a one-page writeup in some obvious place (like /etc/README) that refers to "next steps" would just be really nice.

I have bitched about this before, but during setup I would really really really really really appreciate it if they would ask ONE MORE QUESTION, which is "Shall I also dump in all the stuff an admin or develop would PRESUME UPON?" so I can say Yes and not have to search kingdom-come for basic tools.

What blows my mind is I never ever find anything (quickly in any obvious place) written by a new user or an old hand that ACKNOWLEDGES these basic questions immediately. Like "step 1.01 after you've installed from the CD, 'in order to provide the basic commands documented in every book on earth, do the following thing.'

If if-up was not installed, how did the system bring the network to begin with?

---

### Post by Dr Small on 2008-12-10
> **ecsd said:**
> If if-up was not installed, how did the system bring the network to begin with?

The networking daemon?
/etc/init.d/networking

By the way, all your network profiles are in:
/etc/network/interfaces

---

### Post by kaldrenon on 2008-12-10
> **ecsd said:**
> I know about "apt-get" but I see nothing that will give me a LIST of WHAT I COULD GET. I'm not running a GUI on the server and can't use adept therefore.

Don't know if you've found this on your own yet, but running "aptitude" (as root, or with sudo) will give you a package manager that's all text - perfect for terminal sessions and GUI-less setups. Takes just a minute or two to get oriented the first time it loads, but it'll let you install all kinds of software with just a few commands.

---

### Post by wirelessmonkey on 2008-12-11
if-up in bsd is equivalent to ifconfig <interface> up ;)

---

### Post by hyper_ch on 2008-12-11
> **ecsd said:**
> I know about "apt-get" but I see nothing that will give me a LIST of WHAT I COULD GET. I'm not running a GUI on the server and can't use adept therefore.
did you have a look at the man pages? You can easily search with apt-get...

> **ecsd said:**
> Finally is there any place that just SAYS WHAT TO DO for people like me - sysadmins/hacks who are not stupid, but just not used to the Ubuntu methodologies?
For people who are not stupid I generally recommend consulting the man pages :)

> **ecsd said:**
> A rhetorical question perhaps, but doesn't it strike anyone as odd that one has to issue a command to INSTALL ESSENTIAL COMMANDS? And having a one-page writeup in some obvious place (like /etc/README) that refers to "next steps" would just be really nice.
Why? You have APT which should give you, let's say, 99% of all software you need and presents it to you easily... I don't think it's odd.

---

### Post by bluefrog on 2008-12-11
ifup eth0 would work fine if really needed.

in build-essential there is essential indeed but more important there is build. so if you are using a server as a programmer workstations I understand you concern but if you use it as a "normal" server, I don't see the point of installing development tools as 99% of programs can be installed without compiling.

info coreutils is a good way to start otherwise in a terminal.

---

### Post by Dr Small on 2008-12-11
> **hyper_ch said:**
> You can easily search with apt-get...

That's funny. I can't. I search with apt-cache ;)

---

### Post by koenn on 2008-12-11
> **bluefrog said:**
> ifup eth0 would work fine if really needed.

in build-essential there is essential indeed but more important there is build. so if you are using a server as a programmer workstations I understand you concern but if you use it as a "normal" server, I don't see the point of installing development tools as 99% of programs can be installed without compiling.

info coreutils is a good way to start otherwise in a terminal.

yes, that's the idea behind it, i think;
that, + the desire to save space so that ubuntu can remain a 1 cd distro (more so for desktop releases), and the fact that some unix/linux exploits count on the fact that there's alwyay a compiler present so as as soon as you can produce text, your good to go. 

But If you're used to the old school "software is to be distributed as source and to be compiled it to match your system and the sysadmin's preferences" paradigm, I can understand not having a compiler by default is unexpected.

---

### Post by koenn on 2008-12-11
> **ecsd said:**
> I'm very used to FreeBSD. I cannot believe that I could install an OS that calls itself a "server" and it would not have GCC or MAKE already there! Not only that but it seems NOTHING is installed - for example I cannot even locate "if-up"!!!! (Ubuntu Server 8.10.)
...
Finally is there any place that just SAYS WHAT TO DO for people like me - sysadmins/hacks who are not stupid, but just not used to the Ubuntu methodologies?

Thanks. Sorry for being agitated.

```

x:~$ which ifup
/sbin/ifup
```
That's on Ubuntu desktop, I imagine server has it too. 
'which' is to find out which executable will run if you call a command that's in the PATH, but can obviously also be used to find where executables are located.

Ubuntu documentation is rather fragmented. To get your bearings, reading Debian manuals may be a good start. Ubuntu as largely based on Debian, so Debian documentation will help finding out about major differences between *BSD and Debian/Ubuntu/Linux.
Usually, important differences between Debian and Ubuntu *are* well documented. The root/su/sudo issue is notorious. [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Scanning the Ubuntu Server Guide ( [https://help.ubuntu.com/ubuntu/serverguide/C/index.html](https://help.ubuntu.com/ubuntu/serverguide/C/index.html) ) might give you some info, but more importantly, give you a feel for or insight in how Ubuntu looks at things and what it's target audience is; that helps in understanding why things are the way they are

As Suse (used to) say: Have a lot of fun !

---

