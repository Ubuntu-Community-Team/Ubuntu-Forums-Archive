---
title: "How do I make a publically accessible machine safe?"
date: 2008-04-17
forum: Security Discussions
---

### Post by J0ris on 2008-04-17
Hi,

My situation is the following: I have a pc hooked up to a local network. This pc is the only publically accessible machine (physical access) on the LAN. I've got gutsy installed on it and the intention is that anybody who walks in can do limited browing (whitelist), has read access to certain parts of the hdd with multimedia content and has access to certain apps (e.g. firefox, openoffice...).
My question is multifold:
1. How do I best establish an internet browsing whitelist (on what level)?
2. How do I shield off the other machines on the LAN?
3. How do I restrict access to certain apps (whitelist)?
4. Am I right to think that allowing cd's, usb sticks and the like to mount is a bad idea?

I don't have much experience in these things and my main interest is to find out what the best overall approach to the situation would be.


Thanks!

---

### Post by The Tronyx on 2008-04-17
Hi J0ris,

Your post brings up a lot of good points.  I have some suggestions but I am not comfortable with them until I know a bit more about the system.

How is it networked?  Is it a small homebrew setup with one router, one gateway IP and a few machines hooked into this router?

Do you need to be concerned about remote access?

If remote, what services will be forwarded to the internet, e.g., web server, ssh server, ftp, etc.?

Is the mounting of external media essential to what people will need the machine for?  You mentioned Openoffice and a lot of times, if isn't someone's personal machine they will carry their documents and files with them on a USB drive which makes mount permissions essential if that is to be the purpose of your machine.

What is this machine's main purpose to be and what services is it essential be provided?  

Knowing these things will help myself and others on this thread better assist you to make sure your system is taken care of.

---

### Post by J0ris on 2008-04-18
Thanks for the reply 2point0! To answer your questions:
This is a 'homebrew' network with one router, one gateway ip with about four machines, a NAS device and a printer hooked up to it. Remote access is not a issue at this moment, although ssh may come in handy.
This machine's functions will include (essential):
- online research (saving documents, I suppose, would be a good thing but if mounting a usb storage device presents a security risk, I prefer not to allow it. emailing it may be an alternative then)
- Looking through video material on a specific partition.
- searching a small database on the local machine.
I hope this is sufficient information to work with. Please let me know if I have forgotten something.


Thanks again!

---

### Post by The Tronyx on 2008-04-18
One major thing you can do is to configure IPTables to disallow any traffic from that machine's LAN IP.  THis may impose some limitations but we could work out the best rules when the time comes.

If people will need to save documents, you should probably allow the mounting of external media.  I am not sure if your machine would meet it's needs or the needs of others if it wasn't allowed.  Perhaps you could set up an S/FTP server on it and allow users to upload the documents they need for later retrieval?

As far as limiting partition access, I would need to do some research on that.  I am at work now and I don't have a lot of time to dig up information but I can check for you later.

For the database, depending on what you use, e.g.,Oracle XE,MySQL, PostgreSQL, you will need to specifically allow or disallow the user's access rights.  This thread,[http://forums.mysql.com/read.php?35,182130,182130](http://forums.mysql.com/read.php?35,182130,182130) looks like it might offer a suggestion as to how you would want to set this up based on your description.  If not, it will hopefully give you a push in the right direction.

---

### Post by p_quarles on 2008-04-18
Physical access = root privileges, end of story. 

The only way to secure a publicly accessible machine from tampering would be to lock the computer itself away in a secure area, and allow users access only to the mouse, keyboard, and monitor.

---

### Post by The Tronyx on 2008-04-19
> **p_quarles said:**
> Physical access = root privileges, end of story. 

The only way to secure a publicly accessible machine from tampering would be to lock the computer itself away in a secure area, and allow users access only to the mouse, keyboard, and monitor.

Right...but that defeats the purpose of the machine, at least from what I gather.  

I think it is a given that with any rights and permissions you give a user, you leave yourself more open to security risks.  How risky is another question.  If the machine is to be accessed by 3rd graders, low risk.  If it is to be accessed by college freshmen, larger risk and so on.

I mean, to say, "Physical access = root privileges, end of story," doesn't mean anything.  In theory, any kind of access, local or remote can mean 'end of story' depending on the level of skill and dedication the attacker has.  

The question is not how can this machine be totally secured but rather, given the existing criteria and the services this box needs to provide, what are the best preventative measures to put in place while still having this sytem serve its function.

---

### Post by p_quarles on 2008-04-19
> **2point0 said:**
> I think it is a given that with any rights and permissions you give a user, you leave yourself more open to security risks.  How risky is another question.  If the machine is to be accessed by 3rd graders, low risk.  If it is to be accessed by college freshmen, larger risk and so on.
True, but the term "public" implies a pretty wide range of potential users. If this is in a restricted physical area, then it's a different story, and not really public.

> I mean, to say, "Physical access = root privileges, end of story," doesn't mean anything.  In theory, any kind of access, local or remote can mean 'end of story' depending on the level of skill and dedication the attacker has.  
It's true that no computer is perfectly secure, but giving someone physical access is like leaving the key to your safe hanging off the lock. Software vulnerabilities -- which are prerequisite for any kind of local or remote exploit -- are a completely different category than physical access. Again: leave a computer out in the open, and everyone has root access to that computer. The software could be bulletproof, but the user with physical access can still do anything they want. 

> The question is not how can this machine be totally secured but rather, given the existing criteria and the services this box needs to provide, what are the best preventative measures to put in place while still having this sytem serve its function.
And my point is that web browsing and application white lists, or attempting to set permissions on unencrypted disks, would be easily defeated by an Ubuntu live CD.

---

### Post by The Tronyx on 2008-04-19
I'm just saying that from an attack standpoint, it is impractical to approach a machine with malicious intent that for the most part is so...useless.  What would you do with one machine?  It is a homebrew setup, one router, one IP.  It is not like gaining access to a kiosk that is attached to the university or corporate network or something comparable (presumably).  Besides, if the other machines on the LAN are configured to dump incoming traffic from that box, rooting it via LiveCD is useless.  If someone wants to bypass a browsing by using a LiveCD, the joke is on them as they have some serious issues with the amount of spare time they have.  I think it is safe to say that this machine, while on the LAN, is isolated.  Make an image of the HD and the settings.  If it gets trashed, restore from the image.

If I were going to use a LiveCD to hijack a machine, it would be one far more important than something setup in such a simple manner.  For the sake of staying on track, perhaps J0ris can shed some light on these matters and the audience that will be using the machine to help us build a better threat profile.

---

### Post by p_quarles on 2008-04-19
> **2point0 said:**
> If I were going to use a LiveCD to hijack a machine, it would be one far more important than something setup in such a simple manner.  For the sake of staying on track, perhaps J0ris can shed some light on these matters and the audience that will be using the machine to help us build a better threat profile.
Well, again, my point is that giving all users physical access to the machine allows them to easily bypass the two main security features which were already specifically mentioned: whitelisting web sites and applications. Obviously we are not talking about a computer containing nuclear secrets here, but I have pointed out (and will maintain) that the goals laid out by the OP are not compatible with leaving the computer itself in a publicly accessible location. 

Again, a kiosk or thin-client setup could offer a much better solution here  If the "public" using this computer is actually a limited group that can be monitored frequently, this may not be necessary. The other option would be to lower one's expectations about what kinds of uses could be reasonably prevented.

---

### Post by lswest on 2008-04-19
well, to get around the problem presented by a liveCD, put a password on the BIOS setup, and set it so the hard drive is first to boot, and then disable (if possible) the boot menu/disable the CD drive as a bootable medium.  Then i'd set up the user so it's not in the sudoers file, install xnest (in case you need to admin something, login in a new window to admin it).  Then yeah, configuring IPtables is a good step, and (if possible) disallow booting from a USB stick.

Just my $0.02

*EDIT* Oh, and it might be smart to somehow protect your /etc/shadow file, otherwise any kid with a bit of time could crack your root/admin hash.

---

### Post by wannadumpwindows on 2008-04-21
Remove the menus, put shortcuts for the apps you want to offer on the desktop, and limit acces to everything else. Use a BIOS password. Don't allow booting from usb. Also, completely unplug and remove the cd-rom. There shouldn't be much need for a cd-rom in a machine like this. That's an easy way to solve that problem. Not a lot of help I'm sure, but the simplest start on your way, or so it seems to me. Or you could just boot it with a Damn Small Linux livecd or usb stick when you need to, and just run it straight from ram every time, then you don't need a hard drive at all, and every restart is a completely fresh system.

---

### Post by netlogic on 2008-04-21
I am sorry I am jumping on this thread too late. Some of my suggestions might be very redundant.  This is for someone who is super paranoid.

1. grub password. it is  a must.
2. bios password
3. pad lock for the pc case. prevent an user from opening up the case to change the jumper setting to boot from an external media.
4. NO booting from the optical media. 
5. USB pad locks. Few companies sell a physical pad lock tools
6. blacklist mass storage usb drives and optical drives in the kernel.
7. partitioning. <-- very important
a. i don't know your specific application needs. It is a good idea for /usr/local, /sbin, /lib, /boot, /usr and other partitions based on your need to be read-only. I have seen super paranoid people even mount /etc as a read-only.  Some people mount /var/log to the network and make replications few times a day. That way even hackers remove his trace of his/her existence, you will have a backup copy of the real log to examine. This also prevents trojans getting installed in your system. Only the root privilege user can mount the partitions with the write access for the further upgrade.

8. All management stations should encrypt /home, /root, /var, /tmp and /etc . You never want people to access your keys when the machines are turned off.  I don't know your network policies.

9. Force  swap to be erased during the shutdown.

10. If you implemented ssh public key, it is very easy to force iptables rules to all the machines with very simple shell scripts. Another option is if you maintain your own source install server, you can actually create different named deb files that contains configs. It is a good idea for workstations only talk to certain machines in the local network.

There are  more things you can do. I suggest check out the NSA guidelines. Actually, you can do a lot more than their suggestions.

---

