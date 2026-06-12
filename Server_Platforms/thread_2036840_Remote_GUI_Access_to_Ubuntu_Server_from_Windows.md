---
title: "Remote GUI Access to Ubuntu Server from Windows"
date: 2012-08-03
forum: Server Platforms
---

### Post by wakary on 2012-08-03
I have a Ubuntu 12.04 server hosted in another country.
I'm using Windows and I connect to it using Putty, but I only see a terminal window.

I installed Xfce on my server with 'sudo apt-get install xubuntu-desktop --no-install-recommends' through Putty.

How can I connect to the server and see the desktop environment?
If you could answer in detail it would be great, because there are a lot of guides on the net but they are outdated or very brief.

EDIT: Absolutes an suggested I use Xming but it only lets me 'stream' programs individually, I want to see the full desktop environment.

---

### Post by Absolutes an on 2012-08-03
Install xming on your windows box then enable x11 in putty
[http://sourceforge.net/projects/xming/](http://sourceforge.net/projects/xming/)

---

### Post by wakary on 2012-08-03
> **Absolutes an said:**
> Install xming on your windows box then enable x11 in putty
[http://sourceforge.net/projects/xming/](http://sourceforge.net/projects/xming/)

I installed Xming and enabled X11 forwarding ([http://i.imgur.com/u742s.jpg](http://i.imgur.com/u742s.jpg))

What's next? I connected with Putty and it's the same terminal.

EDIT: Xming only lets me 'stream' programs individually, I want to see the full desktop environment.


* If the link doesn't work: [http://imgur.com/u742s](http://imgur.com/u742s)

---

### Post by 510carl on 2012-08-03
Sorry, off topic. How do I post on this forum. I need support, and I can not figure out how to post a question. sorry for my ignorance. Please help me

---

### Post by spynappels on 2012-08-03
> **wakary said:**
> I installed Xming and enabled X11 forwarding ([http://i.imgur.com/u742s.jpg](http://i.imgur.com/u742s.jpg))

What's next? I connected with Putty and it's the same terminal.

EDIT: Xming only lets me 'stream' programs individually, I want to see the full desktop environment.


* If the link doesn't work: [http://imgur.com/u742s](http://imgur.com/u742s)

In the open terminal window, type the following command:
```
startx
```
This should open the graphical desktop in Xming.

---

### Post by spynappels on 2012-08-03
> **510carl said:**
> Sorry, off topic. How do I post on this forum. I need support, and I can not figure out how to post a question. sorry for my ignorance. Please help me

You click on the New Thread button at the top of each forum or sub-forum. This lets you start a new thread to ask your question in.

---

### Post by wakary on 2012-08-03
> **spynappels said:**
> In the open terminal window, type the following command:
```
startx
```
This should open the graphical desktop in Xming.

This is the response I get: file /root/.Xauthority does not exist
(plus a lot of information about the server).

And the username:~# doesn't appear anymore, so I guess it's doing something.

---

### Post by spynappels on 2012-08-03
Is there a specific reason you are trying to startx as root? can you try as your normal user?

---

### Post by wakary on 2012-08-03
> **spynappels said:**
> Is there a specific reason you are trying to startx as root? can you try as your normal user?

I don't know any other user, these are the instructions I've been given to connect:

hostname: username.asd.asd 
login as: root
password: ***

---

### Post by Absolutes an on 2012-08-03
startxfce4
 
if you need help configuring putty and xming theres a short guide at
[http://qiu.bioweb.hunter.cuny.edu/index.php?option=com_content&view=article&id=110/](http://qiu.bioweb.hunter.cuny.edu/index.php?option=com_content&view=article&id=110/)
I use xlaunch (part of xming in the programs group) to use the full screen option over multiple windows (default)

---

### Post by arrrghhh on 2012-08-03
> **wakary said:**
> I don't know any other user, these are the instructions I've been given to connect:

hostname: username.asd.asd 
login as: root
password: ***

No offense, but why are you installing XFCE on a server?

If you want cli, you want Ubuntu Server.

If you want gui, you want Ubuntu Desktop, in your case XUbuntu.  Please install XUbuntu, it will make your life MUCH easier.  No need to try to fit a square peg into a round hole mate :)

---

### Post by CharlesA on 2012-08-03
> **arrrghhh said:**
> No offense, but why are you installing XFCE on a server?

If you want cli, you want Ubuntu Server.

If you want gui, you want Ubuntu Desktop, in your case XUbuntu.  Please install XUbuntu, it will make your life MUCH easier.  No need to try to fit a square peg into a round hole mate :)
+1. I'm guessing this is a VPS judging by them having a root password set.

@OP: Why do you want a GUI in the first place?

---

### Post by vasukinv on 2012-09-23
It can be either - or both - of these two reasons
-he isn't familiar with Linux commands and his server has Ubuntu installed. As you already know, Linux servers save significant amount of money over Windows servers.
-(virtual) dedicated server company doesn't offer Xubuntu

---

### Post by CharlesA on 2012-09-24
> **vasukinv said:**
> It can be either - or both - of these two reasons
-he isn't familiar with Linux commands and his server has Ubuntu installed. As you already know, Linux servers save significant amount of money over Windows servers.
-(virtual) dedicated server company doesn't offer Xubuntu
Taking the time to learn the command line is an immense help. What happens if the GUI breaks and you need to fix it from a terminal?

---

### Post by vasukinv on 2012-09-24
> **CharlesA said:**
> Taking the time to learn the command line is an immense help. What happens if the GUI breaks and you need to fix it from a terminal?
No doubt I agree with your point. Commandline is more fun, although I'm not too deep into it.

---

### Post by markbl on 2012-09-24
> **wakary said:**
> I have a Ubuntu 12.04 server hosted in another country.


Trying to run a full X environment over the internet will never work very well. But you are managing a linux server anyhow, so even sitting at the console you will only get a terminal window. That's all you need to manage a linux server.

---

### Post by jacekk015 on 2012-09-30
I was always curious why all you guys are against GUI.
I want GUI and server kernel - not the desktop one.

Because of that all against GUI in Ubuntu Server I've installed Linux Mint12 and I've changed the kernel settings for server version.
There is a 8 hdd with 2 for RAID1 and rest for RAID10 - with MDADM
He is serving:
- Samba
- Virtualization through KVM [mostly Windows with Virtio]
Besides I have Windows Server with SQL, DNS and DHCP for business apps.

I'm administering it with NoMachine NX through VPN from my home LinuxMint or Windows7 at work - for example for Virtual Machine Manager.

I was using a 6 months before Ubuntu desktop.
Someone tell me why I must killing myself with virsh??

Now after login I'm using mostly terminal for APT or other stuff - to not forget if something goes wrong.

My spec is XEON E-1230 with 8 cores and 8GB of RAM on SuperMicro motherboard.
The system doesn't feel GNOME as a ballast.

So you guys should consider that if you want more users to use Ubuntu please not answer on second post the old time question: "Why you want GUI? - CLI gives you everything!"
In that way you are sending people away or even worse to Windows !

My 5 cents.

---

### Post by CharlesA on 2012-09-30
> **jacekk015 said:**
> I was always curious why all you guys are against GUI.
I want GUI and server kernel - not the desktop one.

......

My spec is XEON E-1230 with 8 cores and 8GB of RAM on SuperMicro motherboard.
The system doesn't feel GNOME as a ballast.

There is no difference between the 12.04 kernels between server and desktop releases. If you are using Mint now, and it works, stick with it.

As a general rule, the more packages installed equals an increase in the number of packages that may have security flaws in them. Not to mention running a GUI on a box that is sitting in the corner is a waste of resources that could be used for something else.


> So you guys should consider that if you want more users to use Ubuntu please not answer on second post the old time question: "Why you want GUI? - CLI gives you everything!"
In that way you are sending people away or even worse to Windows !

My 5 cents.

If you want a GUI, install the desktop edition of Ubuntu, not the server edition and then learn the secure it properly. I would not run a GUI on a production machine, period, but I do all my administration via SSH, and there is no need for a GUI for that. The other alternative to a GUI is a web frontend, such as Webmin for administrative tasks.

*If the machine is for home use, do whatever you want with it.*

---

### Post by jacekk015 on 2012-10-06
> **CharlesA said:**
> There is no difference between the 12.04 kernels between server and desktop releases. If you are using Mint now, and it works, stick with it.

As a general rule, the more packages installed equals an increase in the number of packages that may have security flaws in them. Not to mention running a GUI on a box that is sitting in the corner is a waste of resources that could be used for something else.


If you want a GUI, install the desktop edition of Ubuntu, not the server edition and then learn the secure it properly. I would not run a GUI on a production machine, period, but I do all my administration via SSH, and there is no need for a GUI for that. The other alternative to a GUI is a web frontend, such as Webmin for administrative tasks.

*If the machine is for home use, do whatever you want with it.*

The machine is for production.
What is a difference for managing it through GUI with SSH or plain SSH terminal.
Try to manage KVM with virsh. That's horrible.
That machine isn't directly connected to Internet - only through VPN. It's secured enough.

"waste of resources" - it has 8 logical cores and 2 are for KVM virtual machine with 2 of 8 GB of RAM.
That server mostly "sleep" - even mdadm RAID10 cannot saturate it with speed of over 500MB/s.

"There is no difference between the 12.04 kernels between server and desktop releases"
That's not true !!! Please check the config of kernel settings.
What kind of IO scheduler you have ? Are you proposing CFQ for server use instead of DEADLINE ? PREEMPT and etc. ??

My GUI server has the same number of wakeups in the powertop as a non-gui.
I've removed all unneeded stuff like Bluetooth, NetworkManager or avahi...

"WEBMIN"
You are saying that we shouldn't use GUI because of something and then you are proposing Webmin which hasn't Ubuntu support from some time[because of security issues]?

---

### Post by CharlesA on 2012-10-07
> **jacekk015 said:**
> The machine is for production.
What is a difference for managing it through GUI with SSH or plain SSH terminal.

There is no difference between using ssh from another box and using something like VNC to get to the desktop of the server, opening a terminal and then running ssh from there. It sounds inefficient, but there is no difference between the two.

> Try to manage KVM with virsh. That's horrible.
That machine isn't directly connected to Internet - only through VPN. It's secured enough.

X over SSH ftw? Run Virtual Manager via SSH should work fine.

A complete list of tools is available here:
[http://www.linux-kvm.org/page/Management_Tools](http://www.linux-kvm.org/page/Management_Tools)


> "waste of resources" - it has 8 logical cores and 2 are for KVM virtual machine with 2 of 8 GB of RAM.
That server mostly "sleep" - even mdadm RAID10 cannot saturate it with speed of over 500MB/s.

I meant the GUI uses resources that could be used for something else. You have a beefy machine that can handle it, stick with what works for you.

> "There is no difference between the 12.04 kernels between server and desktop releases"
That's not true !!! Please check the config of kernel settings.
What kind of IO scheduler you have ? Are you proposing CFQ for server use instead of DEADLINE ? PREEMPT and etc. ??

I have no idea. I do not dig into the guts of the kernel. I am going off the note from the Precise beta that said they were merging the generic and server kernels into the same branch:

[https://wiki.ubuntu.com/PrecisePangolin/TechnicalOverview/Beta2#Ubuntu_Kernel](https://wiki.ubuntu.com/PrecisePangolin/TechnicalOverview/Beta2#Ubuntu_Kernel)

> My GUI server has the same number of wakeups in the powertop as a non-gui.
I've removed all unneeded stuff like Bluetooth, NetworkManager or avahi...

Does that even matter? If a box is idle, and running off the mains, the only reason to limit its power consumption is to save the environment and save on your electrical bill. I can see this as a big deal if you are running on a laptop, but on a server that is running 24/7 and doesn't go to sleep.

> "WEBMIN"
You are saying that we shouldn't use GUI because of something and then you are proposing Webmin which hasn't Ubuntu support from some time[because of security issues]?

Security reasons? From what I remember Webmin was removed from the Debian/Ubuntu repos because of the way it handled packages back in 2006 (or 2008, who knows).

See here:
[https://answers.launchpad.net/ubuntu/+question/2873](https://answers.launchpad.net/ubuntu/+question/2873)
[https://www.virtualmin.com/node/21110](https://www.virtualmin.com/node/21110)

I've run it fine on a 10.04 box (and a 8.04, 9.04, 9.10 box) before moving to just SSH with 10.04.1 and 12.04. To each their own.

If you do use webmin, Make sure it is not accessible to the internet - if you do need to access it from outside the local network, tunnel it over SSH, just like you would tunnel VNC or whatever.

---

