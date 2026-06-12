---
title: "Ubuntu Server, Precise 12.04 How to admin? I am very confused."
date: 2012-05-26
forum: Server Platforms
---

### Post by doctortonic on 2012-05-26
[CENTER]**_[SIZE="3"]I humbly ask you to post only if you know exactly what is about and you have experienced on your own skin. (Example: I have received some advices in the past regarding boot-splash manager which broken the system up. They where good but maybe for another ubuntu version)[/SIZE]_**[/CENTER]


[SIZE="3"][CENTER][B]This is what I did in general
[/B][/CENTER][/SIZE]

[CENTER][B]Hello! I've managed to install Ubuntu server 12.04 Precise into a laptop which is a 
Toshiba Tecra 8200 
 Pentium III @ 877 or 900 Mhz
256 SDRAM 
74 Gb Hdd[/B]
:confused:[/CENTER]

I am working with my tiny box with ssh (I have changed the port to another number like 61980), and putty but I have also installed grafical interface.):P

At the command free -m was showing that it is using only ~89 Mb right after I finished the install, but in time I added more software/other stuff with 

```
sudo tasksel
``` like xubuntu desktop, lubuntu desktop, ubuntu desktop, lamp server, znc, and other little goodies as "fortune-mod, mc etc."

Now the problem is that is using more ram ~203 mb, and I guess that some stuff start automatically after reboot.


[CENTER]++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++[/CENTER]
 

[CENTER][SIZE="3"]**Questions / What I wish to do**[/SIZE][/CENTER]


1) 
  How can I tune up and optimize the system to use the smalles ammount of ram possible?


2) I wish to disable some services (I do not need printing, I don't have bluetooth and all that other stuff), I have read some documentation and google after 

some tutorials but I can not find something to explain VERY clear and that really works, at least from the command line.

**sudo rcconf is buggy**, Example: It show's that the ssh is disabled but the fact is that ssh is enabled, I change the xdm /lightdm to start but after reboot 

dosen't start, same with ufw. Buggy, not good.

sudo sysv-rc-conf show's up runlevels but I have read and people say that runlevels have no importance in the new ubuntu
init and telinit (aka sudo telinit) dosne't show me in what runlevel is the machine, so now I am really confused, Do the runlevels exist or not? If they do 

then how can be they configured? Ex. in what runlevel should machine start.
 

3)
 I have found webmin with google but I have read that is not supported in ubuntu because of incompatibility and it is a security breach as is very hackable 

and vulnerable, so
 
Is there free program to change settings to the system, services, etc. and manage it with a brownser like Webmin?

 I am currently unemployed and I am not making money with this machine, but I learn how to manage, configure and use linux so 

[https://landscape.canonical.com/](https://landscape.canonical.com/) is out of the question being a paid service and I wish to manage only a machine not a milion of servers/machines.

 Anyway I wish a program webmin-like to use on the system without the need of creating an account to some webpage, I am happy by connecting to the machine 

with a [http://192.168.2.4:portnumber](http://192.168.2.4:portnumber), **machine username and password** rather than using a [http://www.somewebpage.com](http://www.somewebpage.com) and [B]make 

there a username which could be taken by someone else before me.[/B] 

4)
 I have changed settings in /etc/defalut/grub with these ones:

```
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=3
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="text"
GRUB_CMDLINE_LINUX=""
GRUB_GFXMODE=1024x576x32

```

 But I wish to see more text when It is booting up like is in freebsd, slackware, gentoo or when I choose "recovery mode" but at the same normal resolution. 

What and where do I need to change to make the boot sequence to be more verbose? What do I need to run after editing the file, sudo update-grub or sudo 

update-grub2?

5)
 Can I manage the Power management settings (profiles) only from command line? The system is starting up and it shows only a text console with "login" but I 

use ssh anyway, and I wish to power off the LCD screen not only standby. 
 I assume that If I will change the power options from xfce, lxde, unity, gnome-shell etc. they will NOT gonna be system wide they will gonna be for the 

specific graphical enviroment. 

6) 
 Can I manage the WiFi only from command line? I assume that eth1 is the WiFi, I need to select the network and give the password to connect to the WiFi network.
How to make the WiFi to automatically connect if I will NOT start the graphical interface?


```
wolfy@tinybox:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:00:39:47:2e:8f
          inet addr:192.168.2.4  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::200:39ff:fe47:2e8f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:469 errors:0 dropped:0 overruns:0 frame:0
          TX packets:436 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:46162 (46.1 KB)  TX bytes:55713 (55.7 KB)

eth1      Link encap:Ethernet  HWaddr 00:02:2d:14:11:b3
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Base address:0xd100

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

```


7)
 How can be the Graphical interface forwarded to my windows machine trough ssh?

VIII)
 Do you guy's reccomand me a good Cpanel alternative which is free (not commercial)/not paid which supports php, email, mysql, apache and nginx?


9)
 When I login with ssh, there is no lag (and the connection it is pretty good being a lan connection), but at this particular step, after I input the 

username I have to wait about 10-15 seconds till I will be asked to input the password, why this is not instant? After this step, all commands are taken 

quick and instant with no lag.



10)
 When I start "sudo lightdm" the theme, artwork is like I have installed xubuntu, how can I start the login manager to look like I have installed ubuntu? I 

need to start sudo gdm/gdm2?

11) 
 I have noticed that the first time I have used sudo tasksel the screen was with PINK, in putty not with purple. The people from irc said that this is okay, I 

was assuming/scared that there are some putty settings, but after installing stuff now tasksel is blue. Why this behavior on changing colors?

---

### Post by spynappels on 2012-05-26
First question, why did you install Server Edition rather than a distro with a very small DE?

Using server edition on a laptop and expecting to use WiFi is not easy/standard, the answer to question 6 is not as simple as you may think, the wireless is normally wlan0 or something.

Answer 9) the SSH daemon is doing a reverse DNS lookup. You can stop this by adding the line ```
UseDNS no
``` to the /etc/ssh/sshd_config file and restarting SSH

---

### Post by doctortonic on 2012-05-27
> **spynappels said:**
> First question, why did you install Server Edition rather than a distro with a very small DE?


I installed ubuntu server for the following reasons:

1. I really need to learn how to work with it
2. Has a slighter better hardware support compared with debian
3. I can easy maintain system up to date
4. Having such a big success on desktop marked on being easy to use I believed and expected to be easy to use as a server also.
5. Is not such a big difference if is server or other official flavour as I installed also " apt-get install ubuntu-desktop && apt-get install xubuntu-desktop / fluxbox / icewm etc."


> **spynappels said:**
> Using server edition on a laptop and expecting to use WiFi is not easy/standard, the answer to question 6 is not as simple as you may think, the wireless is normally wlan0 or something.

I don't know exactly but my bad memory tell's me that I have done that once on gentoo or I have read something about it.

> **spynappels said:**
> Answer 9) the SSH daemon is doing a reverse DNS lookup. You can stop this by adding the line ```
UseDNS no
``` to the /etc/ssh/sshd_config file and restarting SSH

Worked like a charm! :)


I am still looking after something like this:
[IMG]http://oi48.tinypic.com/2ewz2nn.jpg[/IMG]

---

### Post by spynappels on 2012-05-29
> **doctortonic said:**
> 
5. Is not such a big difference if is server or other official flavour as I installed also " apt-get install ubuntu-desktop && apt-get install xubuntu-desktop / fluxbox / icewm etc."


If you have a DM installed, why not just use the Network Manager to manage the wireless connection?

Also, I'm not sure what you are trying to achieve with the screenshot. Is this what you have or is this what you are trying to get?

As a general suggestion, you may want to look at the run level conf files to start services at boot rather than using a GUI, especially as you said you wanted to learn...

---

