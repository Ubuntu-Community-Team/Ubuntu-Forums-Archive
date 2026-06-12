---
title: "Need your help making an ubuntu firewall"
date: 2008-06-08
forum: Security
---

### Post by mechanicalmetal on 2008-06-08
Hey guys,

I am new to ubuntu and have been playing around with it for about 3 months now. I have alot down but not everything. I have ubuntu installed on my laptop (desktop edition) and I have a nice extra dell computer that I want to throw in a few NIC cards in to create a linux firewall. Can you guys let me know if ubuntu would be a good distro for a firewall for my home network? And if not, please tell me what I should use. I was looking at ubuntu server edition, so please advise. And settings for firewalls and stuff would be helpfull too!! Im a noob!!!

Thanks guys!!!

-Brandon

---

### Post by ibutho on 2008-06-08
Any distro will work fine as a firewall as long as its configured correctly. Ubuntu server is a good choice and you can use [Shorewall]("http://www.shorewall.net") as a frontend to iptables and netfilter, if you wish. Another option is to use Ubuntus own frontend called ufw. I've never tried ufw, but shorewall is well documented and you can have your firewall configured in not time.

---

### Post by mechanicalmetal on 2008-06-08
Thank you sir!

I will download Ubuntu Server edition now to install. 

Cant thank you enough!

---

### Post by hyper_ch on 2008-06-09
I'd rather go for debian server - but that's my personal opinion.

---

### Post by The Cog on 2008-06-09
I was going to suggest guarddog as a firewall. I haven't looked at shorewall, but I don't think firestarter (which is is another popular firewall) has the flexibility for handling lots of NICs. I know guarddog is quite capable in this area.

All these firewalls are GUI wrappers round the command-line iptables utility whcih configures the firewall in the Linux kernel. Using iptables directly is a bit of a challenge.

This brings me to the next point - all these firewalls are GUIs, and Ubuntu server comes without a GUI. You would have to install a GUI after installing the basic server if you want to use the GUI firewall wrappers. I think firestarter and shorewall are designed for the gnome desktop, but I know guarddog is designed for KDE. In practice, any of those firewall GUIs will work in any GUI desktop environment though.

You can install a GUI onto the server with one of these commands:
sudo apt-get install ubuntu-desktop
sudo apt-get install kubuntu-desktop
sudo apt-get install xubuntu-desktop

You will need to enable IP forwarding. The best place to do this is by adding this line to /etc/sysctl.conf :
**net.ipv4.ip_forward=1**
which will take effect after a reboot, or the command:
**sudo /etc/init.d/networking restart**

---

### Post by cdenley on 2008-06-09
If you're trying to make a dedicated firewall, I would suggest using pfsense. Especially if the hardware you're using is old. It runs on freebsd and uses openbsd's packet filter.

---

### Post by mechanicalmetal on 2008-06-12
> **cdenley said:**
> If you're trying to make a dedicated firewall, I would suggest using pfsense. Especially if the hardware you're using is old. It runs on freebsd and uses openbsd's packet filter.


Please give me details, got ubuntu server installed.... it has no GUI. I have no idea what im doing :(

---

### Post by mechanicalmetal on 2008-06-13
> **The Cog said:**
> I was going to suggest guarddog as a firewall. I haven't looked at shorewall, but I don't think firestarter (which is is another popular firewall) has the flexibility for handling lots of NICs. I know guarddog is quite capable in this area.

All these firewalls are GUI wrappers round the command-line iptables utility whcih configures the firewall in the Linux kernel. Using iptables directly is a bit of a challenge.

This brings me to the next point - all these firewalls are GUIs, and Ubuntu server comes without a GUI. You would have to install a GUI after installing the basic server if you want to use the GUI firewall wrappers. I think firestarter and shorewall are designed for the gnome desktop, but I know guarddog is designed for KDE. In practice, any of those firewall GUIs will work in any GUI desktop environment though.

You can install a GUI onto the server with one of these commands:
sudo apt-get install ubuntu-desktop
sudo apt-get install kubuntu-desktop
sudo apt-get install xubuntu-desktop

You will need to enable IP forwarding. The best place to do this is by adding this line to /etc/sysctl.conf :
**net.ipv4.ip_forward=1**
which will take effect after a reboot, or the command:
**sudo /etc/init.d/networking restart**


My bad, figured out GUI.... lol

---

### Post by mechanicalmetal on 2008-06-13
> **mechanicalmetal said:**
> My bad, figured out GUI.... lol

Ehhhh when I type the command sudo apt-get install ubuntu-desktop I get a few "dones" and then E:Couldn'y find package ubuntu desktop

---

### Post by kevdog on 2008-06-13
Is your network connection up and working?  

Also update packages:
sudo aptitude update && sudo aptitude upgrade

---

### Post by cdenley on 2008-06-13
> **mechanicalmetal said:**
> Please give me details, got ubuntu server installed.... it has no GUI. I have no idea what im doing :(

PFSense is FreeBSD pre-configured as a firewall. FreeBSD is an alternate operating system to Linux, and is one of several BSD Unix flavors. Basically, if you choose to use it, you would install it over your linux install. It doesn't have a GUI, but it does have a web configuration. Instead of a shell, it has a basic configuration menu, in case you need to re-configure your networking in order to access the web front-end. It basically turns your computer into a hardware firewall, except with a lot more features.

[http://doc.pfsense.org/index.php/Tutorials](http://doc.pfsense.org/index.php/Tutorials)

---

### Post by mechanicalmetal on 2008-06-14
Nahh my network is not up and running becouse I don't know the commands to get it working. I am a total noob with linux. Can someone please give me step by step directions on what I need to do? Thanks so much

---

### Post by Margus81 on 2008-06-14
sudo pppoeconf

no need for a firewall.

Thats it!

---

### Post by rated727 on 2008-07-09
For ease of setup and use, look into some of the dedicated software firewalls.  I use SmoothWall on an old clone PC.  Smoothwall uses a hardened Linux base that has been striped down to provide ONLY the services it requires (no support for printers, sound cards etc.).  One more "selling point" for dedicated firewalls, is that the makers of the software have already configured the security, and they do update regularly.  

SmoothWall uses a text based installer (no mouse needed) and after you get passed the installation and initial configuration (installing NICs and setting up your network mapping and IP configuration) you can remove the CD drive (only used for installation) and the keyboard (if your BIOS will ignore keyboard error on startup) and the monitor.

Once installed, you access SmoothWall from one of your protected computers by using your Web-browser of choice (Graphic Interface).

Smoothwall is NOT your only choice.  There are at least 1/2 dozen dedicated firewall packages.  Check them our and install our preference.
[www.smoothwall.org](www.smoothwall.org)

Good Luck

---

### Post by bla on 2008-07-12
I'm an advocate of firewalls but I find Linux to really lack in this arena.

From what I know, iptables is a primitive, obsolete firewall.  Modern firewalls (seemingly not available for linux) inspect packets and can follow complex rules.  

For example, you can close every port and run in stealth mode.  No port is ever open.  All inbound & outbound traffic is blocked at all times.  Then you make rules based on application file crc checks to allow an application to use a port under very strict rules.  This does not open the port to other applications at the same time.  

As far as I understand this is not possible in Linux.  If you open a port is open to everything.  You can not controll outbound traffic based with such controll.

It makes no sense to have a dedicated firewall box, since you can not define what ports are open to what specific applications on what LAN boxes.  You do need this level of control.  If you close most of the ports and open ones you intend to use, you may as not even have a firewall because such a firewall will not stop a scanner.

---

### Post by cdenley on 2008-07-13
> **bla said:**
> I'm an advocate of firewalls but I find Linux to really lack in this arena.

From what I know, iptables is a primitive, obsolete firewall.  Modern firewalls (seemingly not available for linux) inspect packets and can follow complex rules.  

For example, you can close every port and run in stealth mode.  No port is ever open.  All inbound & outbound traffic is blocked at all times.  Then you make rules based on application file crc checks to allow an application to use a port under very strict rules.  This does not open the port to other applications at the same time.  

As far as I understand this is not possible in Linux.  If you open a port is open to everything.  You can not controll outbound traffic based with such controll.

It makes no sense to have a dedicated firewall box, since you can not define what ports are open to what specific applications on what LAN boxes.  You do need this level of control.  If you close most of the ports and open ones you intend to use, you may as not even have a firewall because such a firewall will not stop a scanner.

I think iptables is typically for servers, and ubuntu desktop users don't really need protection from malware. However, it sounds like you want TuxGuardian. I haven't tried it yet.

[http://tuxguardian.sourceforge.net/](http://tuxguardian.sourceforge.net/)

---

### Post by kevdog on 2008-07-13
> From what I know, iptables is a primitive, obsolete firewall. Modern firewalls (seemingly not available for linux) inspect packets and can follow complex rules.

This statement is FUD.  Everything you want your firewall to do iptables can do.  In fact, most of the so called modern firewalls in linux are really just frontends to iptables and netfilter.

---

### Post by cdenley on 2008-07-13
> **kevdog said:**
> This statement is FUD.  Everything you want your firewall to do iptables can do.  In fact, most of the so called modern firewalls in linux are really just frontends to iptables and netfilter.

Can iptables filter outgoing connections based on the application that owns the connection? If the "owner" module were fully functional, it might be able to do what tuxguardian does. The manpage for iptables warns that you probably have to recompile the kernel to use the "owner" module, and it is broken on SMP systems. Does tuxguardian use iptables?

---

### Post by kevdog on 2008-07-13
Can you do me a favor?  I don't know if the ipt_owner module is in your kernel(meaning I'm not sure if it was compiled in or not).  To see if you have the module compiled:

sudo updatedb
sudo locate ipt_owner

---

### Post by cdenley on 2008-07-14
> **kevdog said:**
> Can you do me a favor?  I don't know if the ipt_owner module is in your kernel(meaning I'm not sure if it was compiled in or not).  To see if you have the module compiled:

sudo updatedb
sudo locate ipt_owner

```

cdenley@ubuntu:~$ modprobe -l|grep ipt_owner
/lib/modules/2.6.24-19-generic/kernel/net/ipv4/netfilter/ipt_owner.ko

```
The module is in the kernel, but the warning is only for 3/5 options with the module.
```

cdenley@ubuntu:~$ sudo iptables -A OUTPUT -m owner --uid-owner 1000 -j DROP
cdenley@ubuntu:~$ sudo iptables -A OUTPUT -m owner --pid-owner 6734 -j DROP
iptables: Invalid argument

```
Also, I think multi-core processors would be used as multiple processors.
> 
NOTE: pid, sid and command matching are broken on SMP


---

### Post by kevdog on 2008-07-14
Lets see if I get your explanation just for clarity. 

The module is in the current kernel, but not all of the options work.  Specifically the pid, and the sid options?  Is this correct?

---

### Post by cdenley on 2008-07-14
> **kevdog said:**
> Lets see if I get your explanation just for clarity. 

The module is in the current kernel, but not all of the options work.  Specifically the pid, and the sid options?  Is this correct?

And probably cmd, yes. At least as far as I can tell. You can read the manpage for yourself. I didn't even know that module existed until I read this thread and looked at the manpage out of curiosity. I may be wrong.

---

### Post by Peterfc on 2008-07-14
Hi All

I run a Dell desktop with Ubuntu 8.4 for daily use and a AMD500 machine to run a openoffice Powerpoint type slide show. Both machines run without fault. 

Question do i need a firewall. Both machine are connected to the same router.

Thanks all for reading this.

---

### Post by Sneaky07 on 2008-07-14
>  Re: Need your help making an ubuntu firewall
Hi All

I run a Dell desktop with Ubuntu 8.4 for daily use and a AMD500 machine to run a openoffice Powerpoint type slide show. Both machines run without fault.

Question do i need a firewall. Both machine are connected to the same router.

Thanks all for reading this.


If your router has a good firewall already I don't think you would need much more.  If you wanted added security maybe a virtual firewall would help.  Anyone else agree?

---

### Post by bla on 2008-07-18
> cdenley:
I think iptables is typically for servers, and ubuntu desktop users don't really need protection from malware. However, it sounds like you want TuxGuardian. I haven't tried it yet.

thanks!

> kevdog:
This statement is FUD. Everything you want your firewall to do iptables can do.
If you say so.  I don't believe these features exist/work on iptables.  I've never seen anyone confirm them or use such features.  I don't want to spend months/years adding code to iptables to get such features.  

Open source doesn't mean unlimited features...just beacause you can add code.

I don't want to criticize anyone here but install XP (for testing purposes) with something like zonealarm(pop but perh not the best) and two things will become clear.

(1) Linux does need a firewall that does not require a masters in comp sci to operate.
(2) The firewalls on Windows are light years ahead of iptables (sorry).
Now, hate MS or not (MS does not make these firewalls), it appears that there is a sort of natural selection in operation here.  These things evolved from the abyss for Windows because there was a pressing need.  Being the choice of 90% of users, it is the OS targeted most.  Their evolution and transformation was shaped by the need for easy of use, minimal dependence on the OS, and consideration for the complete spectra of network vulnerability because Windows is insecure from every angle.  You can never be sure about anything.  No file can be trusted, nor is trusted on Windows.  Linux should apply(steal) this philosophy!!  This is the first rule of security.  At the end of the day, Windows is unhackable with such a firewall (without a backdoor-some have been caught with a backdoor), tests have shown this time after time.  These days Windows systems are the most secure systems and perty much the only way you can hack Windows with such a firewall is if the user downloads and installs malware or if the user uses an insecure web browser that does the same(down & inst code) behind the users back.  That is it.  There is no protection against that on Linux or Windows but at least on windows you can get firewalls that can give you a clue. In such a case they will warn you that a specific app(file) is trying to get on the net and give you the option to diag & trace.  They will also tell you if a file you gave permission to in the past has changed.  

You don't need a firewall on linux?  How do you know if you don't have such a firewall that monitors for unauthorized inbound and most importantly OUTBOUND axs?  That is like never scanning your computer for a virus and then claiming you never had a virus/malware infection.  Or having slept with thousands of people and then not getting checked but claiming that you don't have HIV.  Zero logic.  

Instead of making excuses for Linux, it should be made better.  With the few but important usability improvements UBUNTU has made in the Linux world, it is becoming more of a target as the user base grows.

> cdenley:
Can iptables filter outgoing connections based on the application that owns the connection?
Exactly.

---

### Post by cdenley on 2008-07-18
> 
You don't need a firewall on linux? How do you know if you don't have such a firewall that monitors for unauthorized inbound and most importantly OUTBOUND axs?


If you only install applications from the ubuntu repository, you don't need to worry about outgoing connections. Most desktop ubuntu users shouldn't need a firewall such as that, because they shouldn't be installing random stuff that can send data over the net without their knowledge.

Any traffic can be monitored. You just may not be able to match a connection to a process.

It would be nice to have something like tuxguardian available in the ubuntu repos, but I guess that won't happen unless there is more of a demand. Firewalls in Linux may be lacking in features for desktop users compared to Windows, but I think that's only because of the way the OS's are meant to be used.

---

### Post by brian_p on 2008-07-18
> **bla said:**
> 

. . . . and two things will become clear.

(1) Linux does need a firewall that does not require a masters in comp sci to operate.

ufw

> (2) The firewalls on Windows are light years ahead of iptables (sorry).

Netfilter filters packets based on source, destination and protocol and does it well. I expect you know that, so where does comparing pineapples and pumpkins get us?

> These days Windows systems are the most secure systems and perty much the only way you can hack Windows with such a firewall is if the user downloads and installs malware or if the user uses an insecure web browser that does the same(down & inst code) behind the users back.  That is it.  There is no protection against that on Linux . . . .

No protection! Permissions. User space. System space. Etc. And this is inbuilt into the OS and comes without a firewall in sight.

>  . . . . or Windows but at least on windows you can get firewalls that can give you a clue. In such a case they will warn you that a specific app(file) is trying to get on the net and give you the option to diag & trace.  They will also tell you if a file you gave permission to in the past has changed.

My machine does what I tell it to do and we trust each other. I don't need a toy piece of software (which you dignify with the name 'firewall') to question my intentions.

'Traceroute is trying to access the internet. Do you want it to?'. If I didn't I wouldn't have typed 'traceroute', would I?

> You don't need a firewall on linux?  How do you know if you don't have such a firewall that monitors for unauthorized inbound and most importantly OUTBOUND axs? 

By knowing how the system works and making a rational decision.

---

### Post by bla on 2008-07-18
> My machine does what I tell it to do and we trust each other.

Good for you.  Sounds rational to me.


> I guess that won't happen unless there is more of a demand. Firewalls in Linux may be lacking in features for desktop users compared to Windows, but I think that's only because of the way the OS's are meant to be used.

Right, I can agree with that.  I think it is a big mistake to assume that people will meet all their needs by limiting themselves to the official repos.

---

