---
title: "Am I being hacked? I really think so."
date: 2013-03-13
forum: Security
---

### Post by SONIC Life on 2013-03-13
[SIZE=3]Hello Everyone![/SIZE]

i\ve consulted the forum often but i just registered now, i really hope someone could give me advices, i had to install like 15 times all kinds of OS, now im on TRY ubutnu 12.10, because suddenly and as always my password changed itself when the 12.10 version was installed, so does passwords for firewall and antivirus when i used win 7 thats why i changed to ubuntu but even with linux i have really weirds thinks going on like my gmail account saying my account is open on more than one device when i only have one device, and that like i have like 5 browsers using it, it never happened before, it always told me its was open on 1 device and used 1 browser *mozilla! now i even have safari and other weird browsers.

i have dowloaded Firestarter, but it says that the log doesnt work so no adresses appears anymore, so i downloaded Gufgw to be able to confirgure the firewall, i do have the Icon but i could click a thousand times it wont open itselfs, i have no printer so when i remove a printer or scan apps on the ubuntu software center then it get shady and refuse to delete simple stuff or says that it depends on my drum machin !! hydrogen, like the scan depends on a drum machine !! and then the app center disappear most of the time and plenty of other things like that, been trying to protect my connection and pc for months now since the 24 of december in fact, im getting really annoyed bored of all this, i think my PC is corrupted and someone has acces to all the file systems and can change applications behaviours and/or sabotage them. All this happened to me with lubuntu, ubuntu 12.04 and ubuntu 12.10 and win 7. i think they have corrupted the initrg or intramfs or something but im a noob and powerless.

when i try to install the 12.10 with erase everything it refuses like a part of my PC is locked and secured FROM me, i cannot format the disk and install any OS,


when i type **who** on the terminal i get this

```
ubuntu   tty6         2013-03-13 09:55
ubuntu   tty5         2013-03-13 09:55
ubuntu   tty2         2013-03-13 09:55
ubuntu   tty4         2013-03-13 09:55
ubuntu   tty3         2013-03-13 09:55
ubuntu   tty1         2013-03-13 09:55
ubuntu   tty7         2013-03-13 09:59 (:0)
ubuntu   pts/2        2013-03-13 10:55 (:0.0)
```

also iv dowled

**netstat:**
```
roto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        1      0 192.168.1.2:57790       barbadine.canonica:http CLOSE_WAIT 
tcp        0      0 192.168.1.2:51054       64.209.77.25:http       ESTABLISHED
tcp        0      0 192.168.1.2:51059       64.209.77.25:http       ESTABLISHED
tcp        1      0 192.168.1.2:58414       barbadine.canonica:http CLOSE_WAIT 
tcp        1      0 192.168.1.2:57889       barbadine.canonica:http CLOSE_WAIT 
tcp        1      0 192.168.1.2:58365       barbadine.canonica:http CLOSE_WAIT 
tcp        1      0 192.168.1.2:58415       barbadine.canonica:http CLOSE_WAIT 
tcp        0      0 192.168.1.2:51055       64.209.77.25:http       ESTABLISHED
```



if this can help 


```
sudo apt-get install** ethtool**
Reading package lists... Done
Building dependency tree       
Reading state information... Donefrom
The following NEW packages will be installed:
  ethtool
0 upgraded, 1 newly installed, 0 to remove and 304 not upgraded.
Need to get 97.6 kB of archives.
After this operation, 305 kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/main ethtool i386 1:3.4.1-1 [97.6 kB]
Fetched 97.6 kB in 0s (154 kB/s) 
Selecting previously unselected package ethtool.
(Reading database ... 160331 files and directories currently installed.)
Unpacking ethtool (from .../ethtool_1%3a3.4.1-1_i386.deb) ...
Processing triggers for man-db ...
Setting up ethtool (1:3.4.1-1) ...
ubuntu@ubuntu:~$ sudo ethtool eth0
Settings for eth0:
    Supported ports: [ TP MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Advertised pause frame use: Symmetric Receive-only
    Advertised auto-negotiation: Yes
    Link partner advertised link modes:  10baseT/Half 10baseT/Full 
                                         100baseT/Half 100baseT/Full 
    Link partner advertised pause frame use: Symmetric
    Link partner advertised auto-negotiation: Yes
    Speed: 100Mb/s
    Duplex: Full
    Port: MII
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: on
    Supports Wake-on: pumbg
    Wake-on: g
    Current message level: 0x00000033 (51)
                   drv probe ifdown ifup
    Link detected: yes
```

My PC is a small asus made for XBMC which i dont use Eb 150 or something like that.

if someone could help me i would be very very very greatful !

Thank you for your time and good day:)

SL

---

### Post by coldraven on 2013-03-13
Are you using a wifi router?
One of your "friends" may have copied the wifi password which is usually on a sticker on the router.

If so I would log into the router change the router's password and then disable the wifi.
Then using a network cable go to [https://www.grc.com/](https://www.grc.com/) and use the ShiedsUp to see if you have any ports open.
Your problems may be just caused by bad memory so it would be worth running memcheck from a Live CD
It takes a long time so let it run overnight.

---

### Post by varunendra on 2013-03-13
*Thread moved to **Security Discussions**.*

---

### Post by SONIC Life on 2013-03-13
i am using a wifi router but not the wifi itself i use a cable: modem, then router (wifi router but with a cable directly connected) then PC, i disabled wifi in the bios. i\ll try that thanks a lot.

---

### Post by CharlesA on 2013-03-13
I don't see anything wrong from either who, netstat or ethtool.

---

### Post by JLeon85 on 2013-03-13
> **SONIC Life said:**
> what is impossible to believe precisely?


You're telling us you have Safari on Ubuntu.

---

### Post by CharlesA on 2013-03-13
> **JLeon85 said:**
> You're telling us you have Safari on Ubuntu.

Wow, I totally missed that. The only way I found to have Safari installed was to run it in WINE or PlayOnLinux.

---

### Post by Soul-Sing on 2013-03-13
barbadine.canonical.com is geo-ip which synchronize date/time on your computer. It isn't wise to turn it off.

---

### Post by coldraven on 2013-03-14
> **SONIC Life said:**
> i am using a wifi router but not the wifi itself i use a cable: modem, then router (wifi router but with a cable directly connected) then PC, i disabled wifi in the bios. i\ll try that thanks a lot.

Turning off wifi on your own machine is not what I meant.

You need to log in to your router and switch it off there so that no-one can use or abuse your network.
I log into mine using Firefox, the address is [http://192.168.2.1/](http://192.168.2.1/) but yours may be different.
 
You will need to know the router's password and if you are worried then it would be best to change it.
Make the new password at least 15 characters long and make a note of it somewhere.

When logged in check your router's firewall status, make sure that it is set to maximum.
Read the instructions that came with your router or Google for it.

---

### Post by SONIC Life on 2013-03-15
no thats what gmail says im using when i log on to it. i never said i had safari on my computer. its says im logged with: firefox, gecko etc + **safari and apple web kit**, when i click on the last ten connections and that it is open on three different devices when i only have one even my phone isnt synced to anything and is turned off., thats is why in my INSANE mind, like you immeidiatly said, i start to think my connection might be hacked, corrupted or whatever, but that there is something wrong since i dont use any apple product, doesnt it seem weird to you?

---

### Post by SONIC Life on 2013-03-15
> **coldraven said:**
> Turning off wifi on your own machine is not what I meant.

You need to log in to your router and switch it off there so that no-one can use or abuse your network.
I log into mine using Firefox, the address is [http://192.168.2.1/](http://192.168.2.1/) but yours may be different.
 
You will need to know the router's password and if you are worried then it would be best to change it.
Make the new password at least 15 characters long and make a note of it somewhere.

When logged in check your router's firewall status, make sure that it is set to maximum.
Read the instructions that came with your router or Google for it.

i think i had already done that, and made the password quite difficult using letters numbers big letters etc, but i guess ill try it again, took a break from my PC yesterday because i was really annoyed seeing the gmail security report. thanks again.

---

### Post by conquerorodueko on 2013-03-15
First things first buddie... firestarter??? - bad choice!
Secondly... your online accounts yes are possibly hacked {I have had my share of that on UBUNTU as well}
Ubuntu 12.10??? - buggie... very buggie.... 12.04.2 better for you to go on that one {12.10 is being fixed now on 13.04daily build}
Finally... by default UBUNTU firewall in the UFW is designed to give a false sense of security {YOU HAVE TO MANUALLY BUILD YOUR FIREWALL}
The default firewall allows every connection you have initiated back into your computer including everything in its path to your chosen destination
This is where you have to filter out {UFW is using a filter table} what you dont want to get into your computer {requires knowledge of the internet}

---

### Post by CharlesA on 2013-03-15
> **conquerorodueko said:**
> First things first buddie... firestarter??? - bad choice!

First things first, I didn't think firestarter was even in the Ubuntu repositories anymore, as it hasn't been maintained in a long while and conflicts with ufw/gufw. Uninstall it and start using ufw or guf.

> **conquerorodueko said:**
> Secondly... your online accounts yes are possibly hacked {I have had my share of that on UBUNTU as well}

This is possible, and it is usually a good idea to change ***all*** your passwords if you suspect one service is compromised. This applies to any service, but especially email because it is likely tied to your other accounts - Bank, Paypal, Online Stores, etc.

> **conquerorodueko said:**
> Ubuntu 12.10??? - buggie... very buggie.... 12.04.2 better for you to go on that one {12.10 is being fixed now on 13.04daily build}

Plenty of people are using 12.10 without any problems. All software has bugs and each user's environment is different.

> **conquerorodueko said:**
> Finally... by default UBUNTU firewall in the UFW is designed to give a false sense of security {YOU HAVE TO MANUALLY BUILD YOUR FIREWALL}
The default firewall allows every connection you have initiated back into your computer including everything in its path to your chosen destination
This is where you have to filter out {UFW is using a filter table} what you dont want to get into your computer {requires knowledge of the internet}

The only thing you need to do with ufw is enable it and the default configuration (incoming connections blocked, outgoing connections allowed) is suitable for most users.

Unless you are super paranoid about something on your PC making an outgoing connection, the default rules are fine.

Ubuntu still ships with "no open ports" by default, which means there is no remote access software installed by default, so the user would have had to either visited a compromised website (unlikely) or downloaded random stuff off the internet if their PC is being accessed without their knowledge.

@OP: If you want to confirm this is not the case, you would have to run this:

```
netstat -nlp
```

Check out the basic security guide I have linked in my signature for more info.

---

### Post by conquerorodueko on 2013-03-15
I do agree with CharlesA that: {All software has bugs and each user's environment is different.}
But i cannot say i entirely agree with this: {Unless you are super paranoid about something on your PC making an outgoing connection, the default rules are fine.}
But taking CharlesA's statement as the only condition, is it not - The more reason why it is difficult to ascertain the security level of the network used?
If i might ask, how would the "something" on his PC with 15 clean installations get into the PC again and again and again for 15 times????
By the way, with regards to CharlesA's comment:  {All software has bugs and each user's environment is different.}
I would like to refer CharlesA back to the complaint: {because suddenly and as always my password changed itself when the 12.10 version was installed}

Mind you: If CharlesA is correct that it [BLOCKS ALL IN] AND [ALLOWS ALL OUT], then when you are chatting on the internet, you send a message to who you are chatting with but the person's message back to you would not come back for you to see because the firewall will block it from getting back to you. It would also mean that every website you visit is actually locally on your computer which would mean you are not truly on the internet.

THE BLOCK ALL IN really blocks any connection that YOU HAVE NOT INITIATED. [If you dont say "hello", the other end will be blocked from saying "hello" back to you]
But once you say "Hello", then the person replies back with "Hello", however, the default means that anyone around at the time you say "Hello" is also permitted to say "Hello" back to you. [Makes sense???]

ALL THIS POINTS OUT THAT UBUNTU IS STILL VERY BUGGY AND NEEDS SOME SECURITY WORK.

---

### Post by SeijiSensei on 2013-03-15
Nothing the OP posted suggests there was "something" on his PC of a malevolent nature.  If you see something to the contrary, point it out.

I don't use firewalls on machines behind firewalls.  I have no problem avoiding any sort of security compromise.

---

### Post by Soul-Sing on 2013-03-15
> Mind you: If CharlesA is correct that it [BLOCKS ALL IN] AND [ALLOWS ALL OUT], then when you are chatting on the internet, you send a message to who you are chatting with but the person's message back to you would not come back for you to see because the firewall will block it from getting back to you. It would also mean that every website you visit is actually locally on your computer which would mean you are not truly on the internet.

No way, default ufw policy is yhe above policy: sudo ufw enable. This doesn't lock you out of the internet.
block all outbound traffic does. Except if you have outbound rules, which I have. For the xchat/chat example: freenode, allow port 7000/7070 for freenode via SSL cq SASL

---

### Post by Ms. Daisy on 2013-03-16
> **conquerorodueko said:**
> Mind you: If CharlesA is correct that it [BLOCKS ALL IN] AND [ALLOWS ALL OUT], then when you are chatting on the internet, you send a message to who you are chatting with but the person's message back to you would not come back for you to see because the firewall will block it from getting back to you. It would also mean that every website you visit is actually locally on your computer which would mean you are not truly on the internet.

THE BLOCK ALL IN really blocks any connection that YOU HAVE NOT INITIATED. [If you dont say "hello", the other end will be blocked from saying "hello" back to you]
But once you say "Hello", then the person replies back with "Hello", however, the default means that anyone around at the time you say "Hello" is also permitted to say "Hello" back to you. [Makes sense???]

ALL THIS POINTS OUT THAT UBUNTU IS STILL VERY BUGGY AND NEEDS SOME SECURITY WORK.What? No. The default ufw rules will deny all incoming except for those specifically related to traffic you initiated. 

Let's not argue facts, though...
[http://manpages.ubuntu.com/manpages/precise/en/man8/ufw.8.html#contenttoc10](http://manpages.ubuntu.com/manpages/precise/en/man8/ufw.8.html#contenttoc10)

---

### Post by OpSecShellshock on 2013-03-17
If you're getting reports of a mail account being accessed from another browser on another system that isn't yours, then it's the account that has been compromised, not the computer. Usually this occurs due to weak passwords and/or password re-use. You can implement firewall changes all day long and it won't solve that problem.

---

### Post by SeijiSensei on 2013-03-17
Some free mail services like Yahoo's are so vulnerable you can watch tutorial videos at YouTube that show you how to hijack an account.

---

### Post by CharlesA on 2013-03-17
> **SeijiSensei said:**
> Some free mail services like Yahoo's are so vulnerable you can watch tutorial videos at YouTube that show you how to hijack an account.

Indeed. This is also why two factor authentication is quite handy.

I know Gmail offers it, but  I am not sure about yahoo as I hardly use their email services.

---

### Post by SONIC Life on 2013-03-23
If someone has the time to check into this, these are the process running right now. see if there is anything wrong, i`de be grateful thanks.
have a nice day:)
```
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.1   3628  2108 ?        Ss   11:08   0:01 /sbin/init
root         2  0.0  0.0      0     0 ?        S    11:08   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S    11:08   0:02 [ksoftirqd/0]
root         6  0.0  0.0      0     0 ?        S    11:08   0:02 [migration/0]
root         7  0.0  0.0      0     0 ?        S    11:08   0:00 [watchdog/0]
root         8  0.0  0.0      0     0 ?        S    11:08   0:02 [migration/1]
root        10  0.0  0.0      0     0 ?        S    11:08   0:02 [ksoftirqd/1]
root        11  0.0  0.0      0     0 ?        S    11:08   0:00 [watchdog/1]
root        12  0.0  0.0      0     0 ?        S<   11:08   0:00 [cpuset]
root        13  0.0  0.0      0     0 ?        S<   11:08   0:00 [khelper]
root        14  0.0  0.0      0     0 ?        S    11:08   0:00 [kdevtmpfs]
root        15  0.0  0.0      0     0 ?        S<   11:08   0:00 [netns]
root        17  0.0  0.0      0     0 ?        S    11:08   0:00 [sync_supers]
root        18  0.0  0.0      0     0 ?        S    11:08   0:00 [bdi-default]
root        19  0.0  0.0      0     0 ?        S<   11:08   0:00 [kintegrityd]
root        20  0.0  0.0      0     0 ?        S<   11:08   0:00 [kblockd]
root        21  0.0  0.0      0     0 ?        S<   11:08   0:00 [ata_sff]
root        22  0.0  0.0      0     0 ?        S    11:08   0:00 [khubd]
root        23  0.0  0.0      0     0 ?        S<   11:08   0:00 [md]
root        25  0.0  0.0      0     0 ?        R    11:08   0:00 [kworker/1:1]
root        26  0.0  0.0      0     0 ?        S    11:08   0:00 [khungtaskd]
root        27  0.0  0.0      0     0 ?        S    11:08   0:00 [kswapd0]
root        28  0.0  0.0      0     0 ?        SN   11:08   0:00 [ksmd]
root        29  0.0  0.0      0     0 ?        SN   11:08   0:00 [khugepaged]
root        30  0.0  0.0      0     0 ?        S    11:08   0:00 [fsnotify_mark]
root        31  0.0  0.0      0     0 ?        S    11:08   0:00 [ecryptfs-kthrea]
root        32  0.0  0.0      0     0 ?        S<   11:08   0:00 [crypto]
root        41  0.0  0.0      0     0 ?        S<   11:08   0:00 [kthrotld]
root        42  0.0  0.0      0     0 ?        S    11:08   0:00 [scsi_eh_0]
root        43  0.0  0.0      0     0 ?        S    11:08   0:00 [scsi_eh_1]
root        44  0.0  0.0      0     0 ?        S    11:08   0:00 [scsi_eh_2]
root        45  0.0  0.0      0     0 ?        S    11:08   0:00 [scsi_eh_3]
root        46  0.0  0.0      0     0 ?        S    11:08   0:00 [scsi_eh_4]
root        47  0.0  0.0      0     0 ?        S    11:08   0:00 [scsi_eh_5]
root        51  0.0  0.0      0     0 ?        S    11:08   0:00 [kworker/u:5]
root        52  0.0  0.0      0     0 ?        S    11:08   0:00 [kworker/u:6]
root        54  0.0  0.0      0     0 ?        S<   11:08   0:00 [binder]
root        63  0.0  0.0      0     0 ?        S    11:08   0:00 [scsi_eh_6]
root        64  0.0  0.0      0     0 ?        S    11:08   0:00 [usb-storage]
root        79  0.0  0.0      0     0 ?        S<   11:08   0:00 [deferwq]
root        80  0.0  0.0      0     0 ?        S<   11:08   0:00 [charger_manager]
root        81  0.0  0.0      0     0 ?        S<   11:08   0:00 [devfreq_wq]
root       268  0.0  0.0      0     0 ?        S<   11:09   0:00 [ttm_swap]
root       374  0.0  0.0      0     0 ?        S<   11:09   0:02 [loop0]
root      1156  0.0  0.0   2820   876 ?        S    11:10   0:00 upstart-udev-bridge --daemon
root      1179  0.0  0.1   3540  1820 ?        Ss   11:10   0:00 /sbin/udevd --daemon
syslog    1191  0.0  0.0  31072  1508 ?        Sl   11:10   0:01 rsyslogd -c5
102       1194  0.0  0.1   4220  2232 ?        Ss   11:10   0:04 dbus-daemon --system --fork
avahi     1406  0.0  0.0   3448  1476 ?        S    11:10   0:00 avahi-daemon: running [ubuntu.local]
avahi     1409  0.0  0.0   3448   436 ?        S    11:10   0:00 avahi-daemon: chroot helper
root      1412  0.0  0.0   2816   600 ?        S    11:10   0:00 upstart-socket-bridge --daemon
root      1484  0.0  0.1   7416  2868 ?        Ss   11:10   0:00 /usr/sbin/modem-manager
root      1491  0.0  0.0      0     0 ?        S<   11:10   0:00 [kmpathd]
root      1492  0.0  0.0      0     0 ?        S<   11:10   0:00 [kmpath_handlerd]
root      1498  0.0  0.0      0     0 ?        S<   11:10   0:00 [led_workqueue]
root      1523  0.0  0.0      0     0 ?        S    11:10   0:00 [kworker/1:2]
root      1587  0.0  0.0      0     0 ?        S<   11:10   0:00 [kpsmoused]
root      1595  0.0  0.1   5268  2168 tty4     Ss   11:10   0:00 /bin/login -f       
root      1599  0.0  0.1   5268  2168 tty5     Ss   11:10   0:00 /bin/login -f       
root      1604  0.0  0.0      0     0 ?        S    11:10   0:00 [rc0]
root      1608  0.0  0.0      0     0 ?        S<   11:10   0:00 [krfcommd]
root      1622  0.0  0.1   5268  2156 tty2     Ss   11:10   0:00 /bin/login -f       
root      1623  0.0  0.1   5268  2164 tty3     Ss   11:10   0:00 /bin/login -f       
root      1625  0.0  0.1   5268  2168 tty6     Ss   11:10   0:00 /bin/login -f       
root      1647  0.0  0.0   2176   684 ?        Ss   11:10   0:00 acpid -c /etc/acpi/events -s /var/run/acpid.socket
root      1685  0.0  0.0   2620   892 ?        Ss   11:11   0:00 cron
daemon    1686  0.0  0.0   2476   120 ?        Ss   11:11   0:00 atd
root      1833  0.0  0.3  33144  5304 ?        Ssl  11:11   0:00 NetworkManager
root      1842  0.0  0.0   3820   636 ?        Ss   11:11   0:00 /usr/sbin/irqbalance
root      1927  0.0  0.2  30436  3500 ?        Sl   11:11   0:00 /usr/sbin/console-kit-daemon --no-daemon
root      1937  0.0  0.0      0     0 ?        S<   11:11   0:00 [hd-audio0]
ubuntu    2080  0.0  0.1   6588  2800 tty6     S+   11:11   0:00 -bash
ubuntu    2081  0.0  0.1   6588  2804 tty2     S+   11:11   0:00 -bash
ubuntu    2082  0.0  0.1   6588  2800 tty5     S+   11:11   0:00 -bash
ubuntu    2083  0.0  0.1   6588  2800 tty4     S+   11:11   0:00 -bash
ubuntu    2084  0.0  0.1   6588  2804 tty3     S+   11:11   0:00 -bash
whoopsie  2100  0.0  0.2  26068  4528 ?        Ssl  11:11   0:00 whoopsie
root      2388  0.0  0.1   5268  2168 tty1     Ss   11:11   0:00 /bin/login -f       
ubuntu    2522  0.0  0.1   6588  2800 tty1     S+   11:11   0:00 -bash
root      2851  0.0  0.2  28652  3844 ?        Sl   11:11   0:00 /usr/lib/upower/upowerd
root      3001  0.0  0.2  24728  3224 ?        Sl   11:12   0:00 /usr/lib/accountsservice/accounts-daemon
ubuntu    3014  0.0  0.3  99788  5528 ?        S<l  11:12   0:00 /usr/bin/pulseaudio --start --log-target=syslog
rtkit     3016  0.0  0.0  21336  1252 ?        SNl  11:12   0:00 /usr/lib/rtkit/rtkit-daemon
ubuntu    3027  0.0  0.1  14248  2508 ?        S    11:12   0:00 /usr/lib/pulseaudio/pulse/gconf-helper
colord    3049  0.0  0.2  35512  4300 ?        Sl   11:12   0:00 /usr/lib/i386-linux-gnu/colord/colord
root      4564  0.0  0.0   3236  1128 ?        S    11:14   0:00 /sbin/udevd --daemon
root      4565  0.0  0.0   3236  1108 ?        S    11:14   0:00 /sbin/udevd --daemon
root      4689  0.0  2.0  34120 31164 ?        SLsl 11:14   0:00 lightdm
root      4701  3.7  2.2  63832 34240 tty7     Ds+  11:14   5:01 /usr/bin/X :0 -core -auth /var/run/lightdm/root/:0 -
root      4705  0.0  0.2  18084  3532 ?        Sl   11:14   0:00 lightdm --session-child 12 15
root      4718  0.0  0.2  25832  4376 ?        Sl   11:14   0:02 /usr/lib/policykit-1/polkitd --no-debug
ubuntu    4739  0.0  0.6  50900  9352 ?        Ssl  11:14   0:01 gnome-session --session=ubuntu
ubuntu    4775  0.0  0.0   4096   204 ?        Ss   11:14   0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-
ubuntu    4778  0.0  0.0   3844   532 ?        S    11:14   0:00 /usr/bin/dbus-launch --exit-with-session gnome-sessi
ubuntu    4779  0.0  0.1   5816  2888 ?        Ss   11:14   0:06 //bin/dbus-daemon --fork --print-pid 5 --print-addre
ubuntu    4781  0.0  0.2  43508  3176 ?        Sl   11:14   0:00 /usr/lib/at-spi2-core/at-spi-bus-launcher
ubuntu    4785  0.0  0.1   3488  1684 ?        S    11:14   0:00 /bin/dbus-daemon --config-file=/etc/at-spi2/accessib
ubuntu    4788  0.0  0.1  17088  3032 ?        Sl   11:14   0:01 /usr/lib/at-spi2-core/at-spi2-registryd --use-gnome-
ubuntu    4799  0.0  0.2  34448  3308 ?        Sl   11:14   0:01 /usr/lib/dconf/dconf-service
ubuntu    4808  0.0  0.1   9344  2840 ?        S    11:14   0:00 /usr/lib/i386-linux-gnu/gconf/gconfd-2
ubuntu    4820  0.0  1.1 165644 17400 ?        Sl   11:14   0:05 /usr/lib/gnome-settings-daemon/gnome-settings-daemon
ubuntu    4827  0.0  0.2  71468  3692 ?        Sl   11:14   0:00 /usr/bin/gnome-keyring-daemon --start --components=g
ubuntu    4833  0.0  0.1  36232  2960 ?        Sl   11:14   0:01 /usr/lib/gvfs/gvfsd
ubuntu    4837  0.0  0.1  42764  3008 ?        Sl   11:14   0:00 /usr/lib/gvfs//gvfsd-fuse -f /run/user/ubuntu/gvfs
ubuntu    4844  2.4  5.5 239628 85756 ?        Sl   11:14   3:16 compiz
ubuntu    4855  0.0  1.5 153168 23784 ?        Sl   11:14   0:07 nautilus -n
ubuntu    4856  0.0  0.9 109148 15132 ?        Sl   11:14   0:01 nm-applet
ubuntu    4857  0.0  0.5  40912  8148 ?        Sl   11:14   0:00 /usr/lib/policykit-1-gnome/polkit-gnome-authenticati
ubuntu    4861  0.0  0.7  79612 11148 ?        Sl   11:14   0:00 bluetooth-applet
ubuntu    4863  0.0  0.5  58304  8408 ?        Sl   11:14   0:00 /usr/lib/gnome-settings-daemon/gnome-fallback-mount-
ubuntu    4872  0.0  0.2  28560  3816 ?        Sl   11:14   0:00 /usr/lib/gvfs/gvfs-udisks2-volume-monitor
root      4875  0.0  0.2  42932  3848 ?        Sl   11:14   0:00 /usr/lib/udisks2/udisksd --no-debug
ubuntu    4882  0.0  0.8  71204 13900 ?        Sl   11:14   0:01 /usr/lib/notify-osd/notify-osd
ubuntu    4893  0.0  0.1  27364  2628 ?        Sl   11:14   0:00 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
ubuntu    4901  0.0  0.1  38796  2648 ?        Sl   11:14   0:00 /usr/lib/gvfs/gvfs-afc-volume-monitor
ubuntu    4903  0.0  0.5  41408  8760 ?        Sl   11:14   0:00 /usr/bin/gnome-screensaver --no-daemon
ubuntu    4912  0.0  0.2  36392  3168 ?        Sl   11:15   0:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.17 /org/gtk/g
ubuntu    4920  0.0  0.1  35864  2420 ?        Sl   11:15   0:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.17 /org/gtk/gv
ubuntu    4927  0.0  0.6  75912 10264 ?        Sl   11:15   0:00 telepathy-indicator
ubuntu    4936  0.0  0.1  17244  2464 ?        Sl   11:15   0:00 /usr/lib/gvfs/gvfsd-metadata
ubuntu    4940  0.0  0.4  43400  6244 ?        Sl   11:15   0:00 /usr/lib/telepathy/mission-control-5
ubuntu    4947  0.0  1.2 109824 18952 ?        Sl   11:15   0:01 /usr/bin/signon-ui
ubuntu    4948  0.0  0.2  53472  4544 ?        Sl   11:15   0:00 zeitgeist-datahub
ubuntu    4954  0.0  0.2  43804  4340 ?        Sl   11:15   0:00 /usr/bin/zeitgeist-daemon
ubuntu    4960  0.0  0.5  51400  7784 ?        Sl   11:15   0:00 /usr/lib/zeitgeist/zeitgeist-fts
ubuntu    4970  0.1  0.6  51440  9692 ?        Sl   11:15   0:09 /usr/lib/bamf/bamfdaemon
ubuntu    4972  0.0  0.0   4228   280 ?        S    11:15   0:00 /bin/cat
ubuntu    4981  0.0  0.0   2232   536 ?        Ss   11:15   0:00 /bin/sh -c /usr/bin/gtk-window-decorator
ubuntu    4982  0.0  0.6  41388 10456 ?        Sl   11:15   0:05 /usr/bin/gtk-window-decorator
ubuntu    4992  0.1  1.1  91668 18152 ?        Sl   11:15   0:10 /usr/lib/unity/unity-panel-service
ubuntu    4994  0.0  0.3  62696  4724 ?        Sl   11:15   0:03 /usr/lib/indicator-appmenu/hud-service
ubuntu    5007  0.0  0.2  54256  4388 ?        Sl   11:15   0:00 /usr/lib/i386-linux-gnu/indicator-application-servic
ubuntu    5010  0.0  0.5  75788  8052 ?        Sl   11:15   0:00 /usr/lib/indicator-datetime/indicator-datetime-servi
ubuntu    5014  0.0  0.6  61748  9400 ?        Sl   11:15   0:00 /usr/lib/indicator-printers/indicator-printers-servi
ubuntu    5015  0.0  0.2  64720  4528 ?        Sl   11:15   0:00 /usr/lib/indicator-session/indicator-session-service
ubuntu    5048  0.0  0.3  48604  5776 ?        Sl   11:15   0:00 /usr/lib/evolution/evolution-source-registry
ubuntu    5051  0.0  0.2  64376  4240 ?        Sl   11:15   0:00 /usr/lib/indicator-messages/indicator-messages-servi
ubuntu    5052  0.0  0.3 127776  5944 ?        Sl   11:15   0:00 /usr/lib/indicator-sound/indicator-sound-service
ubuntu    5066  0.0  0.3  30556  4640 ?        Sl   11:15   0:00 /usr/lib/geoclue/geoclue-master
ubuntu    5078  0.0  0.3  40516  5536 ?        Sl   11:15   0:00 /usr/lib/ubuntu-geoip/ubuntu-geoip-provider
ubuntu    5081  0.0  0.7  51760 11780 ?        Sl   11:15   0:01 update-notifier
ubuntu    5100  0.0  0.6  90852 10556 ?        Sl   11:16   0:04 /usr/lib/unity-lens-applications/unity-applications-
ubuntu    5102  0.0  0.4  85564  6468 ?        Sl   11:16   0:01 /usr/lib/unity-lens-files/unity-files-daemon
ubuntu    5104  0.0  0.3  88076  5912 ?        Sl   11:16   0:00 /usr/lib/gwibber/unity-gwibber-daemon
ubuntu    5106  0.0  0.4  77908  7532 ?        Sl   11:16   0:00 /usr/lib/i386-linux-gnu/unity-music-daemon
ubuntu    5108  0.0  1.3 114124 20768 ?        Sl   11:16   0:01 /usr/bin/python3 /usr/lib/unity-lens-photos/unity-le
ubuntu    5110  0.0  0.5  91612  8060 ?        Sl   11:16   0:00 /usr/lib/i386-linux-gnu/unity-shopping-daemon
ubuntu    5112  0.0  1.0  88852 15904 ?        Sl   11:16   0:01 /usr/bin/python /usr/lib/unity-lens-video/unity-lens
ubuntu    5189  0.0  0.9 107400 15064 ?        Sl   11:16   0:00 /usr/bin/python3 /usr/lib/unity-lens-files/unity-sco
ubuntu    5190  0.0  0.2  84560  4188 ?        Sl   11:16   0:00 /usr/lib/i386-linux-gnu/unity-musicstore-daemon
ubuntu    5228  0.0  0.9 100048 14216 ?        Sl   11:16   0:02 /usr/bin/python /usr/lib/unity-scope-video-remote/un
ubuntu    5249  0.0  0.2  44744  3868 ?        Sl   11:16   0:00 /usr/lib/i386-linux-gnu/deja-dup/deja-dup-monitor
ubuntu    5253  0.0  0.9  24204 14428 ?        S    11:16   0:01 /usr/bin/python /usr/lib/ubuntuone-client/ubuntuone-
ubuntu    5336 10.3  9.3 425788 144316 ?       Sl   11:19  13:17 /usr/bin/python /usr/bin/software-center
ubuntu    5380  0.0  0.9  43992 14840 ?        Sl   11:20   0:01 /usr/bin/python /usr/share/oneconf/oneconf-service
ubuntu    8022  0.0  0.3  67276  5912 ?        Sl   11:26   0:01 /usr/lib/gvfs/gvfsd-http --spawner :1.17 /org/gtk/gv
root      8734  0.0  1.1  27316 18364 ?        S    11:29   0:01 python3 /usr/lib/software-properties/software-proper
ubuntu   12248  0.0  1.5 264580 23836 ?        Sl   11:45   0:05 gnome-control-center --overview
root     15547  0.0  0.0      0     0 ?        S    12:06   0:00 [kworker/0:2]
ubuntu   15920  0.0  0.0      0     0 ?        Z    12:09   0:03 [debconf-communi] <defunct>
ubuntu   17892  0.2  2.2 126916 34744 ?        Sl   13:08   0:03 /usr/bin/python3 /usr/bin/update-manager
root     17939  0.0  0.0      0     0 ?        S    13:11   0:00 [kworker/0:1]
ubuntu   17952  0.0  0.0   2232   544 ?        Ss   13:12   0:00 /bin/sh -c gnome-terminal
ubuntu   17953  1.2  1.0  90776 16140 ?        Sl   13:12   0:11 gnome-terminal
ubuntu   17959  0.0  0.0   2404   728 ?        S    13:12   0:00 gnome-pty-helper
ubuntu   17960  0.0  0.1   6220  2628 pts/1    Ss   13:12   0:00 bash
root     18107  0.7  1.3  42136 21008 ?        SNl  13:17   0:04 /usr/bin/python3.2 /usr/sbin/aptd
root     18108  0.0  0.2   5492  3124 ?        S    13:17   0:00 /sbin/dhclient -d -4 -sf /usr/lib/NetworkManager/nm-
nobody   18120  0.0  0.0   5468  1412 ?        S    13:17   0:00 /usr/sbin/dnsmasq --no-resolv --keep-in-foreground -
ubuntu   18251 16.5  6.6 467624 103508 ?       Sl   13:18   1:40 /usr/lib/firefox/firefox
root     18456  0.0  0.0      0     0 ?        S    13:23   0:00 [kworker/0:0]
ubuntu   18635  1.0  0.0   5208  1208 pts/1    R+   13:28   0:00 ps -aux
```

---

### Post by CharlesA on 2013-03-23
That looks fine.

---

### Post by SONIC Life on 2013-03-23
just to say i dont have a USB storage on my PC and dont have an account on unbutuone or any other accounts related to ubuntu beside this one, i dont backup my files, dont a printer, dont use gwibber,, twitter and these social networks, and i know there are servers, X11, and evolution, but i dont know what they do and if i should use them etc... its, a Live cd here, thx

---

### Post by CharlesA on 2013-03-23
> **SONIC Life said:**
> ... its, a Live cd here, thx

The username of "ubuntu" sorta gave that away... :)

---

