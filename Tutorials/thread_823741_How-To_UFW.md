---
title: "How-To: UFW"
date: 2008-06-09
forum: Tutorials
---

### Post by cprofitt on 2008-06-09
I looked for a current how-to for UFW and when I did not see one I wanted to add one.

(important note: UFW is not the firewall. UFW just configures your iptables)

in most cases I recommend doing the following immediately:

```

sudo ufw default deny
sudo ufw enable

```Then fine tuning can start:

**Some basic commands are:**
[B]
Turn on the firewall[/B]
```

sudo ufw enable

```**Turn off the firewall**
```

sudo ufw disable

```[B]

_To add deny rules:_[/B]
**blocking a port**
```

sudo ufw deny port <port number>

```[B]
blocking an ip address[/B]
```

sudo ufw deny from <ip address>

```**blocking a specific ip address and port**
```

sudo ufw deny from <ipaddress> to port <port number>

```**advanced deny example for denying access from an ip address range 10.120.0.1 - 10.120.0.255 for SSH port 22**
```

sudo ufw deny from 10.0.0.1/24 to any port 22

```[B]
[U]
To add allow rules:[/U][/B]
**to allow an ip address**
```

sudo ufw allow from <ip address>

```**to allow a port**
```

sudo ufw <port number>

```**allow a specific ip address and port**
```

sudo ufw allow from <ipaddress> to any port <port number>

```**advanced allow example for allowing access from an ip address range 10.120.0.1 - 10.120.0.255 to port 22**
```

sudo ufw allow from 10.0.0.0/24 to any port 22

```[B]
To get the current status of your UFW rules[/B]
```

sudo ufw status

```**To remove a deny or allow rule**
```

sudo ufw delete <rule type> from <ip address> to any port <port number>

```(note: you basically match the syntax for the creation of the rule and add 'delete')

You need to be careful with setting up allow and deny rules that 'intersect' because the first rule matched is applied and the remaining are ignored.
[B]
SECNARIO: [/B]
you want to block access to port 22 from 192.168.0.1 and 192.168.0.7 but allow all other 192.168.0.x IPs to have access to port 22

```

sudo ufw deny from 192.168.0.1 to any port 22
sudo ufw deny from 192.168.0.7 to any port 22
sudo ufw allow from 192.168.0.0/24 to any port 22

```if you do the allow statement before either of the deny statements it will be matched first and the deny will not be evaluated.

you can check this by checking ufw status
```

sudo ufw status
To                         Action  From
--                         ------  ----
22:tcp                     DENY    192.168.0.1
22:udp                     DENY    192.168.0.1
22:tcp                     DENY    192.168.0.7
22:udp                     DENY    192.168.0.7
22:tcp                     ALLOW   192.168.0.0/24
22:udp                     ALLOW   192.168.0.0/24

```the allow is at the bottom and will be the last command evaluated if it appeared above the deny rules the deny rules would not be evaluated.

I hope this helps you use ufw to secure your computer.
[URL="https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw?action=show"]
Link to the documentation wiki[/URL]

---

### Post by Bakon Jarser on 2008-06-30
Every time I restart my computer I have to restart ufw.  Is there a way to make it enabled at startup?

---

### Post by kevdog on 2008-07-01
Can you ICS with ufw as you can in iptables?

---

### Post by ugm6hr on 2008-07-06
> **Bakon Jarser said:**
> Every time I restart my computer I have to restart ufw.  Is there a way to make it enabled at startup?

I would like to understand this too.  I can't find any documentation that clarifies the situation.

I presume iptables boots at startup.  And ufw is a "frontend" for iptables.

So does ufw need to be running to enable the open ports that I have defined with ufw?

ufw does not boot at startup:
```
sudo ufw status
[sudo] password for xxxxx: 
Firewall not loaded

```

I thought this was where the bootup setting was (default):
```
cat /etc/ufw/ufw.conf
# /etc/ufw/ufw.conf
# 

# set to yes to start on boot
ENABLED=yes

```

Any help?

---

### Post by glitch32 on 2008-07-13
I would also like to know, I'm a little confused with this.

---

### Post by kevdog on 2008-07-14
Im curious also -- I know for example iptables does not by default store settings between boots unless the settings are exported and then imported at boot, or a startup script is launched that re-enters the settings back into iptables.  (iptables-save, iptables-restore).  I thought Network Manager had the iptables-save, restore code calls built in, however if you are not using network manager, then that's another issue).  In theory however, since ufw uses iptables, it would be possible manually to save and restore the settings using the save/restore commands by calling iptables directly rather than ufw.

---

### Post by clio on 2008-07-16
> **Bakon Jarser said:**
> Every time I restart my computer I have to restart ufw.  Is there a way to make it enabled at startup?

i had the same problem before,when i find this gui -->> gufw link [http://gufw.tuxfamily.org/screenshots.html](http://gufw.tuxfamily.org/screenshots.html) 

works all time after reboot,and very easy to use

---

### Post by glitch32 on 2008-07-16
Finally a link that works!  I tried downloading that from ubuntu-unleashed, (and quite a few others), but I could never get the link to work.  Google always said forbidden.  Thank you for that!

---

### Post by bullgr on 2008-08-24
> **Bakon Jarser said:**
> Every time I restart my computer I have to restart ufw.  Is there a way to make it enabled at startup?
try this (from ubuntu wiki: [https://wiki.ubuntu.com/UbuntuFirewall](https://wiki.ubuntu.com/UbuntuFirewall))
```
Toggle logging:
# ufw logging on|off
```

---

### Post by nvteighen on 2008-08-30
Ehm... My ufw doesn't reset itself after reboot.

---

### Post by InfinityCircuit on 2008-08-31
If you are trying to print to a Windows printer shared over samba, you have to make the following changes:

1) Edit /etc/default/ufw and change the last line from:

```
IPT_MODULES="nf_conntrack_ftp nf_nat_ftp nf_conntrack_irc nf_nat_irc"
```

To:

```
IPT_MODULES="nf_conntrack_ftp nf_nat_ftp nf_conntrack_irc nf_nat_irc nf_conntrack_netbios_ns"
```

2) Create the following rules:

```
sudo ufw allow proto udp from 192.168.0.0/16 to any port 137
sudo ufw allow proto udp from 192.168.0.0/16 to any port 631
```

---

### Post by element_G on 2008-10-17
just want to say thanks for this, gufw has failed me and I had to go back to the always reliable cli :guitar:

---

### Post by DenKain on 2009-03-11
*I know the last post in this thread, before me, was in 2007 but I just want to point something out encase anyone ever finds this on google like I did while searching for ufw.*

If you want ufw to load on start up do the following:

System > Preferences > Sessions > Startup Programs > Click Add.

Then just type in ufw for the name and the command. (or gufw if you use that)

Then click "Okay" and then click "Close"

There, your finished, its on the startup.

---

### Post by hostilejosh on 2009-03-14
so if ufw (or any other firewall configuration tool) is not loaded you have no firewall?

---

### Post by ugm6hr on 2009-03-14
> **hostilejosh said:**
> so if ufw (or any other firewall configuration tool) is not loaded you have no firewall?

No.

iptables is enabled as default.  ufw is an optional simplified front-end for iptables.

If you use:`
```
sudo ufw enable
```

A reboot will leave ufw enabled.

---

### Post by edibanez on 2009-06-18
Hi, i'm confused about configuring ufw i'm using kubuntu jaunty, i got ssh deny rule on ufw, if i connect on ssh at localhost will the firewall drop my connection or will it still push thru?

---

### Post by yuli_capone on 2009-06-18
I need some help.
I'm trying to open ports for deluge for upload(it say "no incomming connection")
How can i do that?can you explain me step by step?
Thanks!

---

### Post by nick1 on 2009-07-10
> iptables is enabled as default. ufw is an optional simplified front-end for iptables.

I just installed Ubuntu 8.04.3 LTS desktop version and ran:

```
sudo iptables -L
```

which lists all rules in all chains in the default filter table ( [source]("http://www.opensource.com/docs/manuals/linux/RHL-9-Manual/ref-guide/s1-iptables-options.html") ). This was returned:

```
Chain INPUT (policy ACCEPT)
target  prot opt source  destination

Chain FORWARD (policy ACCEPT)
target  prot opt source  destination

Chain OUTPUT (policy ACCEPT)
target  prot opt source  destination
```

It appears that iptables is enabled by default, however, it appears the default firewall rules are allowing all inbound, forwarding, and outbound traffic. 

If that is the case, the operating system is wide open to vulnerabilities, especially when first plugging into a public network and proceeding to patch the operating system via ```
apt-get update
``` and then ```
apt-get upgrade
```.

But please educate me if I am incorrect.

Thanks,

---

### Post by memilanuk on 2009-07-12
Whether the system is 'wide open' probably depends on what all you have running (and listening to ports).

I believe the default firewall policy tends towards 'mostly allow'.  To change it to 'mostly deny', you probably would want to run something like:

```

sudo ufw default deny

```

(with the caveat that I'm not sitting in front of my Ubuntu box right now, so you would be well advised to double check the above via the man page)

---

### Post by frogotronic on 2009-07-14
Do I need to configure a specific port on ufw to enable last.fm using rhthymbox?

---

### Post by ssdt on 2009-07-24
Thank you for such a great post with UFW firewall.

---

### Post by oygle on 2009-08-21
I tend to close all incoming and only allow specific outgoing. It seems UFW does this with

```

sudo ufw default deny
sudo ufw enable

```

although all ports OUTGOING seem to be 'open', as I haven't had to define any rules via GUFW.

Oygle

---

### Post by lukjad on 2009-08-21
Thanks, this will be very useful. :)

---

### Post by Ubunt2u on 2009-10-28
I know this was posted well over a year ago, but i still wanted to say thanks.

---

### Post by Jordanwb on 2009-10-29
I use NFS to mount a remote share on my laptop. If I don't add any allow rules will it still work? I want to setup UFW on my laptop.

---

### Post by Marrkk on 2009-10-31
yup ... just easily install   gufw in synaptic :)

---

### Post by dacoman on 2009-11-12
Please help me understand this. The UFW official page states this:

[INDENT]#/etc/ufw/before[6].rules: rules in these files are evaluated before any rules added via the ufw command
#/etc/ufw/after[6].rules: rules in these files are evaluated after any rules added via the ufw command [/INDENT] 

Does this mean rules set in before.rules are over-written by rules set by the ufw command line?

For example I have http access open to everyone by running ufw command line:
ufw allow 80/tcp

Then I want to block access to the Web server to certain IP range so I added the following rule in the before.rules
-A ufw-before-input -m iprange --src-range xxx.xxx.xxx.xxx-xxx.xxx.xxx.255 -j DROP 

Is this futile, i.e. this last rule get canceled by the ufw command line to allow http access to everyone?

Should I add this last rule in the after.rules to make sure the rule is active, i.e. blocks the IP range?

Thank you for your time,
--D

After some more reading it seams that packets are dropped as soon as a matching rule is encountered so rules placed in before.rules take precedence. Please correct me if I'm wrong.

---

### Post by Andrew_P on 2009-11-19
> **Bakon Jarser said:**
> Every time I restart my computer I have to restart ufw.  Is there a way to make it enabled at startup?

Every time I restart my computer I have to *disable* ufw and restart Samba in order to get it to join the Windows network.  It didn't originally  act this way, until one day I typed "ufw enable" in a terminal window.  Now it seems to be permanently fouled up and there's no obvious way to reset it to the way it was after the clean install.  It would be OK if I could just set up a script that automatically runs as root during boot to perform this ufw disable/Samba restart task, but I haven't been able to find information on it in over six months of searching.  Is there any way we can just get rid of the blasted firewall on Ubuntu entirely?  My Netgear router has a far better firewall in it anyway that protects my entire LAN from the outside world.

---

### Post by Astrals on 2009-12-27
Thank you this has been a great help to me, than you everyone.

---

### Post by y_farkash on 2010-01-26
Is there a default state for ports? When I enable ufw, are all ports in deny or allow mode or do I need to state one or the other? I mean, if I do not state anything about port X, what is the default state?

Thanks!

---

### Post by peridot on 2010-03-16
> **y_farkash said:**
> Is there a default state for ports? When I enable ufw, are all ports in deny or allow mode or do I need to state one or the other? I mean, if I do not state anything about port X, what is the default state?

Thanks!

I know this is late, but I thought I'd reply for anyone searching. You can type ufw status to see the list of rules and whether or it is enabled (active) or disabled (inactive). You can do "ufw default deny", "ufw default allow" and "ufw default reject" to set its default behavior.

---

### Post by piju on 2010-07-07
any body tried firestarter before ?

---

### Post by kibrun on 2010-08-05
> **piju said:**
> any body tried firestarter before ?
i did have a go with firestarter. very easy in gui and for desktop user. not recommended for server use since i don't install gui in server. now i'm trying to learn ufw. in the mean time i'm using script for my iptables from : [http://ubuntuforums.org/showthread.php?t=159661](http://ubuntuforums.org/showthread.php?t=159661). Hope this help.

---

### Post by MaxVK on 2010-10-23
I believe that Gufw is advised over Firestarter because Firestarter is no longer maintained, which is not a good state for firewall software.

---

### Post by clapika on 2011-03-03
can ufw deny icmp from eth0(client) to eth1(server) if make topology of
SERVER<------->(eth1)UFW(eth0)<-------->CLIENT
can?

---

### Post by deesto on 2011-07-18
> **ugm6hr said:**
> No.

iptables is enabled as default.  ufw is an optional simplified front-end for iptables.

I'm really confused about all this: I am told that ufw is an optional, "simplified" interface to netfilter, and that iptables is still active in addition to ufw, but I don't know of a simple way in Ubuntu to use iptables *instead of* ufw.  In addition, the traditional iptables rules configuration files (in RH/Fedora, /etc/sysconfig/iptables) don't seem to exist, and instead rules are written directly into the kernel, and after that I don't know where they are saved.  Is this accurate?  

Are ufw created via CLI stored in a similar manner, e.g., not in config files and direct to the kernel?  I'm familiar with the files in /etc/ufw/*, but I don't see the ufw rules I create with "sudo ufw ..." being saved there.

---

### Post by xravenz on 2011-08-30
chkconfig --level 2345 ufw on

May or may not work for users.

You may need to install chkconfig first.

sudo apt-get install chkconfig

---

### Post by deesto on 2011-08-30
> **xravenz said:**
> chkconfig --level 2345 ufw on

May or may not work for users.

You may need to install chkconfig first.

sudo apt-get install chkconfig
Sorry: what?  If that was meant for me, thanks, but I don't understand how it applies to my questions about how applied ufw firewall rules are saved? how iptables can be used instead of ufw? etc.?

---

### Post by ryzingsrinivas on 2011-11-16
Hi ,

I am getting log messages in ubuntu server 10.10,

Nov 16 18:25:31 ubuntu kernel: [30373.102472] [UFW BLOCK] IN=eth0 OUT= MAC=e0:69:95:77:a7:30:00:25:5e:c9:23:95:08:00 SRC=122.175.35.121 DST=192.168.1.108 LEN=40 TOS=0x00 PREC=0x00 TTL=61 ID=0 DF PROTO=TCP SPT=19082 DPT=8088 WINDOW=0 RES=0x00 RST URGP=0 
Nov 16 18:25:52 ubuntu kernel: [30393.423502] [UFW BLOCK] IN=eth0 OUT= MAC=e0:69:95:77:a7:30:00:25:5e:c9:23:95:08:00 SRC=122.175.35.121 DST=192.168.1.108 LEN=40 TOS=0x00 PREC=0x00 TTL=61 ID=0 DF PROTO=TCP SPT=19097 DPT=8088 WINDOW=0 RES=0x00 RST URGP=0 
Nov 16 18:26:12 ubuntu kernel: [30413.723842] [UFW BLOCK] IN=eth0 OUT= MAC=e0:69:95:77:a7:30:00:25:5e:c9:23:95:08:00 SRC=122.175.35.121 DST=192.168.1.108 LEN=40 TOS=0x00 PREC=0x00 TTL=61 ID=0 DF PROTO=TCP SPT=19110 DPT=8088 WINDOW=0 RES=0x00 RST URGP=0 


How to resolve this problem .Please help me 

Thanks,
Srinivas

---

### Post by cintiaarosales on 2012-07-17
Hola guys,
Interesting thread, from its time-span to the various (related) issues that were raised. I’m looking for info about iptables frontend/GUI for ufw/firewall management for Ubuntu, etc. and thought maybe someone here can advise. But maybe I can also help a bit - in my searches I found this [wiki post]( https://wiki.archlinux.org/index.php/Firewalls), it has some good info as well as different methods/tools to manage iptables and ufw.
My issue is if I have several Ubuntu firewalls to manage on different servers, and I’m not sure what would be the best option. In the wiki post they mention something called firewall builder, and I also found this [Ubuntu firewall management tool]( http://www.dome9.com/security-challenges/ubuntu-firewall-management), and from what I understand, these seem like something that might be good. I’m wondering if anyone has any experience managing multiple Ubuntu firewall instance, or can consult about these management tools or would a frontend/gui be good enough, and which would give the best security?
Any input would be appreciated :) Cintia

---

### Post by teward on 2012-07-17
> **ryzingsrinivas said:**
> Hi ,
 
I am getting log messages in ubuntu server 10.10,
 
Nov 16 18:25:31 ubuntu kernel: [30373.102472] [UFW BLOCK] IN=eth0 OUT= MAC=e0:69:95:77:a7:30:00:25:5e:c9:23:95:08:00 SRC=122.175.35.121 DST=192.168.1.108 LEN=40 TOS=0x00 PREC=0x00 TTL=61 ID=0 DF PROTO=TCP SPT=19082 DPT=8088 WINDOW=0 RES=0x00 RST URGP=0 
Nov 16 18:25:52 ubuntu kernel: [30393.423502] [UFW BLOCK] IN=eth0 OUT= MAC=e0:69:95:77:a7:30:00:25:5e:c9:23:95:08:00 SRC=122.175.35.121 DST=192.168.1.108 LEN=40 TOS=0x00 PREC=0x00 TTL=61 ID=0 DF PROTO=TCP SPT=19097 DPT=8088 WINDOW=0 RES=0x00 RST URGP=0 
Nov 16 18:26:12 ubuntu kernel: [30413.723842] [UFW BLOCK] IN=eth0 OUT= MAC=e0:69:95:77:a7:30:00:25:5e:c9:23:95:08:00 SRC=122.175.35.121 DST=192.168.1.108 LEN=40 TOS=0x00 PREC=0x00 TTL=61 ID=0 DF PROTO=TCP SPT=19110 DPT=8088 WINDOW=0 RES=0x00 RST URGP=0 
 
 
How to resolve this problem .Please help me 
 
Thanks,
Srinivas
 
That is just your system logging what's blocked.  Unless you want port 8088 open, there's no issue here.

---

