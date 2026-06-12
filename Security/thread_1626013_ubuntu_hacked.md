---
title: "ubuntu hacked ?"
date: 2010-11-19
forum: Security
---

### Post by AM_SOS on 2010-11-19
hello all,
i recently heard about firestarter, a firewall facility that ubuntu is equipped with.
one of my friends mentioned that he had seen a mac getting hacked, and even his ubuntu has been attacked. he advised me to install firestarter.
now all along i was under the impression that given the small market share of linux, no one is interested in hacking linux. second, linux is inherently much more secure than windows.
now both of my beliefs are sort of being called into question, and i am sort of wondering how secure ubuntu is !
you see, neither have i installed any anti virus, nor have i used any firewall. and so far for the past 3 years or so, i have had no problems of any kind.
so does this mean that i dont even know and my computer has been hacked ? !
thanks!

---

### Post by uRock on 2010-11-19
Even without a firewall installed your system still has IPTables by default. If you run **sudo ufw enable** in a terminal, it will activate the firewall.

You only truly need to activate the Ubuntu firewall if you are running any server applications, which ubuntu has none that are active unless you install them, and if you do not have a router with its own firewall, which most have running by default.

Please read this thread on [Ubuntu Security]("http://ubuntuforums.org/showthread.php?t=510812") to better understand how Ubuntu's security works.

Regards,
uRock

---

### Post by Hippytaff on 2010-11-19
This is a discussion that continues in the world of Linux...

The main difference between windows and linux in security terms is that windows security is a bolt on feature and linux was designed with security in mind.

my penneth worth :-)

---

### Post by wilee-nilee on 2010-11-19
> **Hippytaff said:**
> This is a discussion that continues in the world of Linux...

The main difference between windows and linux in security terms is that windows security is a bolt on feature and linux was designed with security in mind.

my penneth worth :-)

+1 and the MS users are not informed of this by the OS provider information=power. ;)

---

### Post by sisco311 on 2010-11-19
> **urock said:**
> 

please read this thread on [ubuntu security]("http://ubuntuforums.org/showthread.php?t=510812") to better understand how ubuntu's security works.


+1 

> security is an ongoing process and, like an onion, it has layers and stinks. The best defense you have is to read and learn how to secure your os.

---

### Post by holiday on 2010-11-19
If you don't have a router, get one. Even the cheap ones are good enough unless you have exceptional requirements - you want to run an internet service, for example. 

If you do have a router, and you haven't forwarded any ports, then you're good. There's danger everywhere, of course, but even the most secure systems have been hacked. 

Unless you're hosting information marketable enough to warrant a heavily-funded attack, a locked-down router will keep you safe. 

A firewall is interesting for its logs. You want to look for outbound requests that you have not requested.

---

### Post by d3v1150m471c on 2010-11-19
The only %100 secure operating system is one that has absolutely no internet connection, no power source, and no user :). I use firestarter, and I think it's great. A lot of people take issues with it because it's no longer being developed. To the best of my knowledge this isn't a security issue unless of course you download and execute some program that happens to exploit firestarter. Though, you shouldn't be using code you don't trust in the first place. A remote buffer overflow, or remote attacks in general, should be your largest concern. Given that firestarter is a front-end to iptables, unless a hacker gets through iptables, which is constantly developed and upgraded, you have nothing to worry about. Also, make sure you're updating programs that listen on open ports: samba, ssh, etc. These should be in your security updates and you can check it off with your update manager or synaptic. I think that about covers it. Using a router is also a good idea. Be careful what you give root privileges to. Hmm...what else, use apparmor or selinux if you can set it up. Apparmor is easier to learn. gufw and ufw are available for ubuntu but i hated them. good luck and i hope that helps.

---

### Post by HermanAB on 2010-11-20
> given the small market share of linux, no one is interested in hacking linux

That is MS marketing bulldust. Linux is the most popular OS ever, with billions of systems in operation and every year hundreds of millions new Linux devices are manufactured.  MS is the most popular *desktop* system, which is only a small market segment.  Linux is king of everything else: Embedded systems, Cell phones, Routers, Firewalls, Servers, Super computers... and since Linux systems usually sit on high speed network backbones, it makes a very attractive target indeed.

Anyhoo, a system is only as secure as the software you run on it. A default Ubuntu system is secure.  However, if you install VNC, FTP, and what not and use k3wl four character passwords, then you machine will get hacked pretty soon and no amount of firewalling will protect you against it.

Your best defense if to always use looooong passwords of 9 characters or more, for all accounts.

---

### Post by holiday on 2010-11-20
I like HostsDeny. My ssh log used to packed with pages of hits from some robot reading from a Baby Name book. Now I don't. Instead I've got a huge hosts.deny file. I'll top it down sometime, sure, but I like looking at all those ips that can't even try anymore.

For the truly paranoid we have TripWire, and of course WireShark can offer hours of entertainment. 

And anyone serious should run chkrootkit. 

At work, we have people working 24 hours a day monitoring these things. But at work we're protecting the private information of millions of citizens, information that bad people will pay big money for. And that information is not on Ubuntu Desktop systems, it is on hardened Solaris systems.

Most of us don't have information assets worth the effort to crack through basic protections. The script kiddies and robots are combing the beach for the happy-go-lucky soul who leaves his wallet on his towel while he takes a swim. 

Security concerns for the Ubuntu user are way over-hyped. I've been reading these forums for years, and I have yet to see a case of genuine intrusion. I may have missed one, sure, but if security was a concern for Ubuntu users we'd be seeing a lot more.

---

### Post by wilee-nilee on 2010-11-20
> **HermanAB said:**
> That is MS marketing bulldust. Linux is the most popular OS ever, with billions of systems in operation and every year hundreds of millions new Linux devices are manufactured.  MS is the most popular *desktop* system, which is only a small market segment.  Linux is king of everything else: Embedded systems, Cell phones, Routers, Firewalls, Servers, Super computers... and since Linux systems usually sit on high speed network backbones, it makes a very attractive target indeed.

Anyhoo, a system is only as secure as the software you run on it. A default Ubuntu system is secure.  However, if you install VNC, FTP, and what not and use k3wl four character passwords, then you machine will get hacked pretty soon and no amount of firewalling will protect you against it.

Your best defense if to always use looooong passwords of 9 characters or more, for all accounts.

Thats the truth, I just use pwgen and string together a bunch of them.;) But I have other methods as well.

---

### Post by Soul-Sing on 2010-11-21
> **Hippytaff said:**
> This is a discussion that continues in the world of Linux...

The main difference between windows and linux in security terms is that windows security is a bolt on feature and linux was designed with security in mind.

my penneth worth :-)

There is a difference between linux as an -op system and the linux kernel.
The decision to increase the amount of code to expand without any limits isn't a decision based on security imho.(leaving the MINIX concept to limit code) Is the amount of code related to security? Yes, very much.
Uncompromised security is found via BSD projects.

---

