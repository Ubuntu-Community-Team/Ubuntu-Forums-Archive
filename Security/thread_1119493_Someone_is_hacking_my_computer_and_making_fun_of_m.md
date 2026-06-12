---
title: "Someone is hacking my computer and making fun of me."
date: 2009-04-08
forum: Security
---

### Post by ubuntu27 on 2009-04-08
Some-one is pulling a serious prank on me.
He or she keeps hacking to my computer.

Over the past two weeks I am seeing that my IM's nick get shortened or changed.

For example, when my nick was something like "I am so happy today!! yoohoo", it became "I am so"

Today my nickname was "I am going to study Kong Fu" and my nick was changed to "I am going to study C"

I am getting tired of this. At first I though it was an accident, that maybe I am the one who deleted it. But there is no chance, in no way I am going to put that I am going to study C. I am not interested in C.

Somehow the culprit has access to my computer laptop.

I know it is not someone from my home, since they are all computer novices and I never leave my computer without locking it.
And besides, they don't know anything about programming languages. They don't even know that there is one called "C"


**********

I am using Ubuntu 8.10 32-bit
My IM client is [emesene]("http://www.emesene.org/")
The Internet connection is wireless.

---

### Post by lisati on 2009-04-08
Suggestion: change your password(s) and check your wireless security a.s.a.p.

---

### Post by TBerk on 2009-04-08
How are you connecting to the Internet?  Is your laptop running over a wire, via wireless (wifi)? If wifi, then what form of security are you applying to the connection?

I agree it's high Time you change all your passwords, and not to the name of your pet or favourite colour or something. A good eight characters or more, including some capitals in strange places and a few numbers is the least you should be working with.

Here are  the 1st three Google links I ran across just to have something to read; 


[http://compnetworking.about.com/od/wirelesssecurity/tp/wifisecurity.htm](http://compnetworking.about.com/od/wirelesssecurity/tp/wifisecurity.htm)

[http://news.cnet.com/Worried-about-Wi-Fi-security/2100-7347_3-5540969.html](http://news.cnet.com/Worried-about-Wi-Fi-security/2100-7347_3-5540969.html)

[http://www.securityfocus.com/columnists/385](http://www.securityfocus.com/columnists/385)


TBerk
I suppose I'll go read them myself...

---

### Post by HermanAB on 2009-04-08
The default install of Ubuntu has NO servers running.  Therefore it is impossible to hack it remotely.  

So if you have a hackable service, then it must be something you installed yourself eg, Apache or FTP.  Use 'top' and 'nmap' to see what you got running and stop it.

---

### Post by shad0w_crash on 2009-04-08
It's not impossible maby it's hacked from the inside out (by opening a malafide file wich trickers an un-updated application occurs a bufferoverflow and use a exploit).

Check your computer with rkhunter if anywone installed some nasty program.

You could also check ossec (a HIDS). For monitoring your information.

Is it only your IM wich is doing weird or do you have other signs that you've been hacked?

You could use firestarter to make sure everything gets blokked from outside. Or maby a re-install.

At last check your settings netstat for weird connection.

---

### Post by ubuntu27 on 2009-04-08
We have canceled our Internet connection since two months ago. I now connect to public WifFi from the library, stores, restaurants, etc.

Since it is not my internet, I cannot encrypt it.

I wonder if there is anything I can do.

For now, I have installed the GUI for UFW (Uncomplicated Firewall), and enabled the UFW. 
I have also change the passwords for my login, and for my e-mail account.

---

### Post by Volt9000 on 2009-04-08
> **ubuntu27 said:**
> We have canceled our Internet connection since two months ago. I now connect to public WifFi from the library, stores, restaurants, etc.

Since it is not my internet, I cannot encrypt it.

I wonder if there is anything I can do.

For now, I have installed the GUI for UFW (Uncomplicated Firewall), and enabled the UFW. 
I have also change the passwords for my login, and for my e-mail account.

Hm... this makes it sound like you're not getting hacked, but something else is going on in your system. If you're only connecting through public Wi-Fi at different locations, the odds of someone following you around just to screw with you like that seems very minimal.

Let's see what happens after you've changed your passwords. If the same stuff is still happening I suspect the problem isn't some annoying hacker, but something on your system.

---

### Post by PreviousN on 2009-04-08
I'm guessing its a friend or roomate pulling pranks on you. If you were a hacker, what would be the impitus to mess around with someone elses IM username? There is no real reason. If you do have a hacker problem, the hacker would be less likely to do stupid things like that (notifying you of the break-in), and more likely to do something malicious, like steal credit card information. 

I hope to god you aren't using public wireless to check on your bank information. That's like asking for your identity to be stolen. I told that to several friends last year, they didn't believe me, and one of them got their identity stolen. She's still picking up the pieces of her life...

So, I think its a roomate pulling a prank, not a hacker. Try locking your computer when you aren't using it.

---

### Post by hovzio on 2009-04-08
If your constantly using different internet connections you are not really using consistent ip's. This makes it quite hard to "attack" externally, unless you have some bogus program installed thats reporting outwords and creates a backdoor. An above post mentions rkhunter, this along with secure passwords is a good start. Watch outbound traffic and be restrictive with your firewall. See if any weird processes are running when connected.

---

### Post by Dougie187 on 2009-04-08
It doesn't really sound like someone is hacking you to me at least.

Why not check your logs to see if you are just being paranoid or not?

---

### Post by ubuntu27 on 2009-04-08
> **Volt9000 said:**
> Hm... this makes it sound like you're not getting hacked, but something else is going on in your system. If you're only connecting through public Wi-Fi at different locations, the odds of someone following you around just to screw with you like that seems very minimal.


Well, when I travel, I get to connect to varieties of WiFi.
But, most of the time I am at home in which I usually connect to some unknown neighbors net.

> **PreviousN said:**
> I'm guessing its a friend or roomate pulling pranks on you. If you were a hacker, what would be the impitus to mess around with someone elses IM username? There is no real reason. If you do have a hacker problem, the hacker would be less likely to do stupid things like that (notifying you of the break-in), and more likely to do something malicious, like steal credit card information. 


You don't need a good reason to do. Some people just do it for heck of it. Back when I was 14 I used to be a script kiddie and I will bother people around me in a Internet Cafe.

Also, I don't have any roommate. And none of my friends live near me. 
Well, it does not matter how far they are if they can have a remote connection..
But, they will not do that.

> **Volt9000 said:**
> Let's see what happens after you've changed your passwords. If the same stuff is still happening I suspect the problem isn't some annoying hacker, but something on your system.

I will be observant.
I guess it is a good time to install a Fresh Ubuntu Jaunty. I shall jump right to the Beta.

> **PreviousN said:**
>  
I hope to god you aren't using public wireless to check on your bank information. That's like asking for your identity to be stolen. I told that to several friends last year, they didn't believe me, and one of them got their identity stolen. She's still picking up the pieces of her life...


Don't worry. I am very aware of that. I never buy or visit a bank website when I am on a public wifi.

> **PreviousN said:**
> 
So, I think its a roomate pulling a prank, not a hacker. Try locking your computer when you aren't using it.

I always lock my computer when I am gone, even when I go to the bathroom/washroom/toilet

> **Dougie187 said:**
> 
Why not check your logs to see if you are just being paranoid or not?

Which Logs should I check?

> **hovzio said:**
> An above post mentions rkhunter, this along with secure passwords is a good start. Watch outbound traffic and be restrictive with your firewall. See if any weird processes are running when connected.

Ok. Run it. It displays 8 suspicious files.

I will attach the log and the terminal output of rkhunter.

---

### Post by Dr Small on 2009-04-08
A rather interesting situation. Most of the angles have already been covered for this. A few last questions:

1) Do you have remote desktop enabled?
  a) If so, is it password protected?
2) Are you using a 'secure' password (non-dictionary word/8+ character password)?
3) Are you running OpenSSH Server?

---

### Post by Stupendoussteve on 2009-04-08
Since it is only affecting IM, I would consider strongly the possibility that it is your IM account which has been hacked, or someone got your password.

---

### Post by cariboo on 2009-04-08
You stated you were leaching your wifi from your neighbour, how computer savvy is the neighbour? Just because the router is open, doesn't mean he doesn't know what he is doing.

Jim

---

### Post by Dr Small on 2009-04-08
> **cariboo907 said:**
> You stated you were leaching your wifi from your neighbour, how computer savvy is the neighbour? Just because the router is open, doesn't mean he doesn't know what he is doing.

Jim
An open router still doesn't mean a compromised computer. Yes, it can lead to that, but just the inital fact does not mean that.

---

### Post by Stupendoussteve on 2009-04-08
An open router can mean a traffic sniffer. Most IM protocols are not encrypted and extremely easy to parse.

---

### Post by ubuntu27 on 2009-04-09
> **Dr Small said:**
> A rather interesting situation. Most of the angles have already been covered for this. A few last questions:

1) Do you have remote desktop enabled?
  a) If so, is it password protected?
2) Are you using a 'secure' password (non-dictionary word/8+ character password)?
3) Are you running OpenSSH Server?

Hi Dr. Small.

1) I have disabled it,
2) my login passwords are over 10 characters long for the IM, and over 15 character for my Ubuntu log-in.

3) I am not running any server.

```
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0   3056  1896 ?        Ss   14:57   0:01 /sbin/init
root         2  0.0  0.0      0     0 ?        S<   14:57   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S<   14:57   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        S<   14:57   0:08 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S<   14:57   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S<   14:57   0:00 [migration/1]
root         7  0.0  0.0      0     0 ?        S<   14:57   0:02 [ksoftirqd/1]
root         8  0.0  0.0      0     0 ?        S<   14:57   0:00 [watchdog/1]
root         9  0.0  0.0      0     0 ?        S<   14:57   0:00 [events/0]
root        10  0.0  0.0      0     0 ?        S<   14:57   0:00 [events/1]
root        11  0.0  0.0      0     0 ?        S<   14:57   0:00 [khelper]
root        51  0.0  0.0      0     0 ?        S<   14:57   0:00 [kintegrityd/0]
root        52  0.0  0.0      0     0 ?        S<   14:57   0:00 [kintegrityd/1]
root        54  0.0  0.0      0     0 ?        S<   14:57   0:00 [kblockd/0]
root        55  0.0  0.0      0     0 ?        S<   14:57   0:00 [kblockd/1]
root        57  0.0  0.0      0     0 ?        S<   14:57   0:00 [kacpid]
root        58  0.0  0.0      0     0 ?        S<   14:57   0:00 [kacpi_notify]
root       152  0.0  0.0      0     0 ?        S<   14:57   0:00 [cqueue]
root       156  0.0  0.0      0     0 ?        S<   14:57   0:00 [kseriod]
root       201  0.0  0.0      0     0 ?        S    14:57   0:00 [pdflush]
root       202  0.0  0.0      0     0 ?        S    14:57   0:00 [pdflush]
root       203  0.0  0.0      0     0 ?        S<   14:57   0:00 [kswapd0]
root       245  0.0  0.0      0     0 ?        S<   14:57   0:00 [aio/0]
root       246  0.0  0.0      0     0 ?        S<   14:57   0:00 [aio/1]
ubuntu     333  0.0  0.0   5556  2204 ?        S    21:15   0:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.5 /org/gtk/gvfs/exec_spaw/1
ubuntu     343  0.0  0.0  23040  2004 ?        S    21:15   0:00 scim-bridge
root       346  0.0  0.0   2252   948 ?        S    21:15   0:00 /sbin/dhclient -d -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /var/run/dhclient-eth1.pid -lf /var/run/dhclient-eth1.lease -cf /var/run/
nm-dhclient-eth1.conf eth1
ubuntu     349  0.8  1.6 151904 49972 ?        Sl   21:15   0:04 python /usr/share/emesene/Controller.py
ubuntu     371  1.0  0.5  57696 17032 ?        S    21:15   0:05 /usr/lib/notification-daemon/notification-daemon
root       455  0.2  0.5  22472 15824 ?        S    21:16   0:01 /usr/bin/python /usr/share/jockey/jockey-backend
ubuntu     518  9.7  2.5 206668 78024 ?        Sl   21:16   0:45 /usr/lib/firefox-3.0.8/firefox
ubuntu     654  2.4  0.8 108800 25980 ?        Sl   21:24   0:00 gnome-terminal
ubuntu     658  0.0  0.0   2912   756 ?        S    21:24   0:00 gnome-pty-helper
ubuntu     659  0.7  0.1   5800  3116 pts/0    Ss   21:24   0:00 bash
ubuntu     678  0.0  0.0   2744  1008 pts/0    R+   21:24   0:00 ps aux
ubuntu     679  0.0  0.0   5800  1736 pts/0    R+   21:24   0:00 bash
root      1338  0.0  0.0      0     0 ?        S<   14:57   0:00 [ksuspend_usbd]
root      1339  0.0  0.0      0     0 ?        S<   14:57   0:00 [khubd]
root      1398  0.0  0.0      0     0 ?        S<   14:57   0:04 [ata/0]
root      1403  0.0  0.0      0     0 ?        S<   14:57   0:00 [ata/1]
root      1408  0.0  0.0      0     0 ?        S<   14:57   0:00 [ata_aux]
root      1409  0.0  0.0      0     0 ?        S<   14:57   0:00 [khpsbpkt]
root      2186  0.0  0.0      0     0 ?        S<   14:58   0:00 [scsi_eh_0]
root      2187  0.0  0.0      0     0 ?        S<   14:58   0:00 [scsi_eh_1]
root      2190  0.0  0.0      0     0 ?        S<   14:58   0:00 [scsi_eh_2]
root      2302  0.0  0.0      0     0 ?        S<   14:58   0:00 [knodemgrd_0]
root      2311  0.0  0.0      0     0 ?        S<   14:58   0:08 [scsi_eh_3]
root      2312  0.0  0.0      0     0 ?        S<   14:58   0:00 [scsi_eh_4]
root      2525  0.0  0.0      0     0 ?        S<   14:58   0:00 [kjournald]
root      2997  0.0  0.0   2536  1028 ?        S<s  14:58   0:00 /sbin/udevd --daemon
root      3393  0.0  0.0      0     0 ?        S<   14:58   0:00 [kmmcd]
root      3438  0.0  0.0      0     0 ?        S<   14:58   0:00 [btaddconn]
root      3439  0.0  0.0      0     0 ?        S<   14:58   0:00 [btdelconn]
root      3596  0.0  0.0      0     0 ?        S<   14:58   0:00 [kpsmoused]
root      5462  0.0  0.0   1780   528 tty4     Ss+  14:58   0:00 /sbin/getty 38400 tty4
root      5463  0.0  0.0   1780   524 tty5     Ss+  14:58   0:00 /sbin/getty 38400 tty5
root      5468  0.0  0.0   1780   520 tty2     Ss+  14:58   0:00 /sbin/getty 38400 tty2
root      5469  0.0  0.0   1780   520 tty3     Ss+  14:58   0:00 /sbin/getty 38400 tty3
root      5470  0.0  0.0   1780   528 tty6     Ss+  14:58   0:00 /sbin/getty 38400 tty6
root      5677  0.0  0.0   2440  1324 ?        Ss   14:58   0:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
root      5741  0.0  0.0      0     0 ?        S<   14:58   0:07 [kondemand/0]
root      5743  0.0  0.0      0     0 ?        S<   14:58   0:00 [kondemand/1]
syslog    5816  0.0  0.0   2012   676 ?        Ss   14:58   0:00 /sbin/syslogd -u syslog
root      5869  0.0  0.0   1940   536 ?        S    14:58   0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
klog      5877  0.0  0.0   3636  2488 ?        Ss   14:58   0:00 /sbin/klogd -P /var/run/klogd/kmsg
108       5912  0.0  0.0   3148  1380 ?        Ss   14:58   0:01 /bin/dbus-daemon --system
avahi     5934  0.0  0.0   2888  1492 ?        Ss   14:58   0:00 avahi-daemon: running [tensai.local]
avahi     5935  0.0  0.0   2888   492 ?        Ss   14:58   0:00 avahi-daemon: chroot helper
root      6000  0.0  0.0   6572  2504 ?        Ss   14:58   0:00 /usr/sbin/cupsd
113       6414  0.0  0.0   6340   956 ?        Ss   14:58   0:00 /usr/sbin/exim4 -bd -q30m
root      6575  0.0  0.0   9216  1428 ?        Ss   14:58   0:00 /usr/sbin/winbindd
root      6593  0.0  0.0   9216  1136 ?        S    14:58   0:00 /usr/sbin/winbindd
111       6601  0.0  0.1   6456  4440 ?        Ss   14:58   0:02 /usr/sbin/hald
root      6608  0.0  0.0  17480  2596 ?        Ssl  14:58   0:00 /usr/sbin/console-kit-daemon
root      6673  0.0  0.0   3364  1120 ?        S    14:58   0:00 hald-runner
root      6711  0.0  0.0   3436  1084 ?        S    14:58   0:02 hald-addon-input: Listening on /dev/input/event4 /dev/input/event8 /dev/input/event5 /dev/input/event7 /dev/input/event6 /dev/input/event2 /dev/input/event3 /dev/input/event10 /dev/input/event1
root      6722  0.0  0.0   3448  1036 ?        S    14:58   0:00 /usr/lib/hal/hald-addon-cpufreq
111       6724  0.0  0.0   2296   940 ?        S    14:58   0:00 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
root      6766  0.0  0.0   3440  1060 ?        S    14:58   0:09 hald-addon-storage: polling /dev/scd0 (every 2 sec)
root      6828  0.0  0.0   3488  1712 ?        Ss   14:58   0:00 /usr/sbin/bluetoothd
root      6864  0.0  0.0      0     0 ?        S<   14:58   0:00 [krfcommd]
root      6901  0.0  0.0  14764  2732 ?        Ssl  14:58   0:02 /usr/sbin/NetworkManager
root      6918  0.0  0.0   4244  1872 ?        S    14:58   0:01 /sbin/wpa_supplicant -u -f /var/log/wpa_supplicant.log
root      6924  0.0  0.0   6776  2960 ?        S    14:58   0:00 /usr/sbin/nm-system-settings --config /etc/NetworkManager/nm-system-settings.conf
root      7000  0.0  0.0  14240  1792 ?        Ss   14:58   0:00 /usr/sbin/gdm
root      7003  0.0  0.1  14776  3320 ?        S    14:58   0:00 /usr/sbin/gdm
root      7068  0.0  0.0   4336  1148 ?        Ss   14:58   0:00 /usr/bin/system-tools-backends
daemon    7106  0.0  0.0   2068   460 ?        Ss   14:58   0:00 /usr/sbin/atd
root      7140  0.0  0.0   3412  1028 ?        Ss   14:58   0:00 /usr/sbin/cron
root      7338  0.0  0.0   1780   524 tty1     Ss+  14:58   0:00 /sbin/getty 38400 tty1
1001     30988  0.0  0.2  45168  7156 ?        Sl   16:16   0:00 /usr/lib/evolution/evolution-data-server-2.24 --oaf-activate-iid=OAFIID:GNOME_Evolution_DataServer_CalFactory:1.2 --oaf-ior-fd=29
root     32371  6.9  1.6  78436 51804 tty7     Ss+  21:14   0:40 /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
ubuntu   32397  0.0  0.0  14700  2072 ?        S    21:14   0:00 /usr/bin/gnome-keyring-daemon -d --login
ubuntu   32407  0.0  0.2  26196  7104 ?        Ssl  21:14   0:00 x-session-manager
ubuntu   32496  0.0  0.0  21432  1444 ?        Ss   21:14   0:00 /usr/lib/scim-1.0/scim-launcher -d -c simple -e all -f socket --no-stay
ubuntu   32511  0.0  0.0   3040  1180 ?        Ss   21:14   0:00 //bin/dbus-daemon --fork --print-pid 6 --print-address 9 --session
ubuntu   32513  0.0  0.0   3124   672 ?        S    21:14   0:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-session /usr/bin/seahorse-agent --execute x-session-manager
ubuntu   32520  0.0  0.1  28964  4168 ?        Ssl  21:14   0:00 /usr/bin/pulseaudio -D --log-target=syslog
ubuntu   32535  0.0  0.0   7532  2536 ?        S    21:14   0:00 /usr/lib/pulseaudio/pulse/gconf-helper
ubuntu   32537  0.1  0.1   7996  4960 ?        S    21:14   0:00 /usr/lib/libgconf2-4/gconfd-2
ubuntu   32539  0.0  0.0   4176   800 ?        Ss   21:14   0:00 /usr/lib/scim-1.0/scim-helper-manager
ubuntu   32540  0.0  0.3  30020 10560 ?        Ssl  21:14   0:00 /usr/lib/scim-1.0/scim-panel-gtk --display :0.0 -c socket -d --no-stay
ubuntu   32542  0.0  0.0   6240   872 ?        Ss   21:14   0:00 /usr/lib/scim-1.0/scim-launcher -d -c socket -e socket -f x11
ubuntu   32548  0.0  0.2  18788  7156 ?        Ss   21:14   0:00 /usr/bin/seahorse-agent --execute x-session-manager
ubuntu   32551  0.0  0.0   5556  2148 ?        S    21:14   0:00 /usr/lib/gvfs/gvfsd
ubuntu   32558  0.0  0.0  29196  2032 ?        Ssl  21:14   0:00 /usr/lib/gvfs//gvfs-fuse-daemon /home/ubuntu/.gvfs
ubuntu   32562  0.0  0.1  13916  3632 ?        S    21:14   0:00 /usr/lib/gnome-session/helpers/gnome-keyring-daemon-wrapper
ubuntu   32567  0.1  0.5  47356 16872 ?        Ssl  21:14   0:01 /usr/lib/gnome-settings-daemon/gnome-settings-daemon
ubuntu   32569  0.3  0.1  13784  4660 ?        S    21:14   0:01 /usr/lib/at-spi/at-spi-registryd
ubuntu   32571  0.0  0.1  33456  3560 ?        Ssl  21:14   0:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=13
ubuntu   32575  0.0  0.0   1844   552 ?        S    21:14   0:00 /bin/sh /usr/bin/compiz
ubuntu   32639  1.4  0.4  22056 14208 ?        S    21:15   0:08 /usr/bin/compiz.real --ignore-desktop-hints --replace --indirect-rendering core ccp
ubuntu   32651  0.2  0.1  22008  3276 ?        Ss   21:15   0:01 gnome-screensaver
ubuntu   32652  0.0  0.0   1844   492 ?        Ss   21:15   0:00 /bin/sh -c emerald --replace
ubuntu   32653  0.2  0.5  47952 15592 ?        S    21:15   0:01 emerald --replace
ubuntu   32654  0.5  0.8 105388 27708 ?        Sl   21:15   0:03 gnome-panel
ubuntu   32655  0.1  0.8  59776 25312 ?        S    21:15   0:01 nautilus --no-desktop --browser
ubuntu   32658  0.0  0.4  27476 14484 ?        S    21:15   0:00 python /usr/share/system-config-printer/applet.py
ubuntu   32663  0.0  0.3  57884 11220 ?        Sl   21:15   0:00 /usr/lib/evolution/2.24/evolution-alarm-notify
ubuntu   32667  0.0  0.0   1844   496 ?        S    21:15   0:00 /bin/sh /usr/bin/blueproximity
ubuntu   32668  1.7  0.6  48056 21052 ?        Sl   21:15   0:09 python /usr/share/blueproximity/proximity.py
ubuntu   32670  0.0  0.5  41320 17304 ?        S    21:15   0:00 nm-applet --sm-disable
ubuntu   32671  0.0  0.2  24420  8368 ?        S    21:15   0:00 bluetooth-applet
ubuntu   32673  0.0  0.4  34720 15460 ?        S    21:15   0:00 update-notifier
ubuntu   32678  0.0  0.0   5872  2712 ?        S    21:15   0:00 /usr/lib/gvfs/gvfs-hal-volume-monitor
ubuntu   32681  0.0  0.0   5536  2180 ?        S    21:15   0:00 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
ubuntu   32682  0.0  0.3  41376 10828 ?        Sl   21:15   0:00 /usr/lib/evolution/2.24/evolution-exchange-storage --oaf-activate-iid=OAFIID:GNOME_Evolution_Exchange_Connector_CalFactory:1.2 --oaf-ior-fd=24
ubuntu   32683  0.0  0.2  24908  9252 ?        Ss   21:15   0:00 gnome-power-manager
ubuntu   32690  0.0  0.5  52568 16296 ?        Sl   21:15   0:00 /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-iid=OAFIID:GNOME_MixerApplet_Factory --oaf-ior-fd=27
ubuntu   32723  0.0  0.2  53544  7732 ?        Sl   21:15   0:00 /usr/lib/evolution/evolution-data-server-2.24 --oaf-activate-iid=OAFIID:GNOME_Evolution_DataServer_CalFactory:1.2 --oaf-ior-fd=25
ubuntu   32748  0.0  0.0  22192  2740 ?        S    21:15   0:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.5 /org/gtk/gvfs/exec_spaw/0


```

> **cariboo907 said:**
> You stated you were leaching your wifi from your neighbour, how computer savvy is the neighbour? Just because the router is open, doesn't mean he doesn't know what he is doing.

Jim

I do not even know who's wifi it is. I just happened to find it ><:

---

### Post by shad0w_crash on 2009-04-09
Check your ARP cache (arp -a).

Also maby your pc isn't hacked but only your IM account. If somebody is connecting from a other remote computer to you IM account do you get kicked then or can he also IM on the same account? You did change All your passwords (IM, mail, pc) or only a couple?

if you're really affraid for a hacker, you should also compare the filehash of rkhunter to an excisting one, because if rkhunter is replaced by an evil version it'll ofcourse not notice the trojans etc.

---

### Post by frodon on 2009-04-09
> **Stupendoussteve said:**
> Since it is only affecting IM, I would consider strongly the possibility that it is your IM account which has been hacked, or someone got your password.Same analysis here, IM nick change is not evidence of computer hacking for me, however it may be evidence of IM account hacking which is all but rare.
It arrived to some of my friends and the IM account hacker even changed the password and sent strange message to her friend list. Act quick and get your account canceled or back with new password, having your IM account hacked is not safe for you and your friends.

---

### Post by spikoley on 2009-04-09
> **Stupendoussteve said:**
> Since it is only affecting IM, I would consider strongly the possibility that it is your IM account which has been hacked, or someone got your password.

> **Stupendoussteve said:**
> An open router can mean a traffic sniffer. Most IM protocols are not encrypted and extremely easy to parse.

> **frodon said:**
> Same analysis here, IM nick change is not evidence of computer hacking for me, however it may be evidence of IM account hacking which is all but rare.
It arrived to some of my friends and the IM account hacker even changed the password and sent strange message to her friend list. Act quick and get your account canceled or back with new password, having your IM account hacked is not safe for you and your friends.

This sounds like the case to me.  Somebody sniffed your IM password and did not hack your computer.

If you have a remote server with ssh access you could tunnel all your traffic on it.  [SSH Tunnel HowTo]("http://ubuntuforums.org/showthread.php?t=723025&highlight=ssh"), but use it with System> Preferences> Network Proxy.  Make sure you change all your passwords.

---

### Post by Dougie187 on 2009-04-09
The main log I would check to see if someone indeed had access to your computer would be 

/var/log/auth.log

however there are others that might give you useful information. You can look in System->Administration->System Log
for more information.

---

### Post by Dr Small on 2009-04-09
Another thing to try (which I forgot, before), is to look for any listening services.
```
sudo netstat -tlp --numeric-ports
```

---

### Post by huwnet on 2009-04-09
Have you tried just using a different IM program before jumping to the conclusion that you're being hacked?

emesene is fairly buggy.

---

### Post by jojo1224 on 2009-04-09
> **huwnet said:**
> Have you tried just using a different IM program before jumping to the conclusion that you're being hacked?

emesene is fairly buggy.

Thats what I was thinking, I was gonna post that but was makeing sure no one else did. To the OP try Pidgin.

---

### Post by kidux on 2009-04-09
I agree that if anything has been hacked it's IM account. Odds are it's someone you know who perhaps saw you enter your password and is messing with you. Change the IM password, use a different program like Pidgin.

Another possibility would be someone sniffed it while you were using public WiFi. We had a problem in my area where a hacker was sitting on public hotspots and attacking users who didn't have proper security setup when they connected. Then of course we had a guy setup an open router just to get access to users machines.

The moral is to be careful what net you connect to, and what information you transmit across it.

---

### Post by rajasekharan1 on 2009-04-09
You had mentioned that you access the web using a public wifi. When you connect to these public wifis, do you see a dialog for a security key? It is possible to listen and monitor wifi transmissions that are not secured. Ubuntu doesn't prominently label if the network is secure or not. 

Raj

---

### Post by Dougie187 on 2009-04-09
> **rajasekharan1 said:**
> You had mentioned that you access the web using a public wifi. When you connect to these public wifis, do you see a dialog for a security key? It is possible to listen and monitor wifi transmissions that are not secured. Ubuntu doesn't prominently label if the network is secure or not. 

Raj

I don't know what version of ubuntu you are using, but with all of the wireless networks I can see it is very easy to tell which are secure and which aren't. On top of that, most public networks are not going to use any type of security because that would limit the number of people who could use it. I think the rule of thumb is something like, "If you are using a public network, you don't care who sees your crap". No offense to the OP, but if you really want security, you should just pay for your own internet instead of leeching off other peoples.

---

### Post by Godly on 2009-04-09
Why don't you get your own internet?

---

### Post by ComputerHermit on 2009-04-09
don't get your own Internet if you don't have to if you don't have the money due to a lay off or something we all have to do cut backs try to change all your passwords make them long and complex their is a good how to in these forums on making a stable iptables script run rkhunter or reinstall I work in a corporate environment you got to make end's meet anyway you can. ):P

---

### Post by ubuntu27 on 2009-04-09
Thank you everyone for your replies. 

Yes, I suppose it could be that my IM account has been compromised.
I have changed the password.
Is emesene really buggy? I never had any trouble wit it until recently.


As some of you guessed, we had to cut the Internet because of economic reasons.

*****

On a somewhat related note. The other laptop which belongs to my family (not mine) which runs Windows Vista has been compromised. I am fairly sure of this one.

They had an important software that occupied 1600 MB of HD space.
When they tried to use it last night, all the icons had disappeared. I search for the software and I saw that it was un-installed. All the shortcuts were gone from Start Menu and desktop.
I went to the Program Files folder and saw that software's folder was still there, but all the executables files and library files were gone.

Why do I arrive to this conclusion?
It is because I made every single account on that laptop as a limited account. They cannot remove or install programs unless they have my password. Think of it as Windows' sudo.

I have never gave them the password for my account. 

I don't know if anything else happened on that laptop. I did not have any time to look for it further.

But, all of this makes me think  it is not an accident.


Anyhow, thank you guys for all your help. 
I appreciate it a lot.

---

### Post by PreviousN on 2009-04-09
> **ComputerHermit said:**
> don't get your own Internet if you don't have to if you don't have the money due to a lay off or something we all have to do cut backs try to change all your passwords make them long and complex their is a good how to in these forums on making a stable iptables script run rkhunter or reinstall I work in a corporate environment you got to make end's meet anyway you can. ):P

Whoa. That was real skill, using only one period for the whole sentence like that. :-)

---

### Post by kidux on 2009-04-10
> **ubuntu27 said:**
> Thank you everyone for your replies. 

Yes, I suppose it could be that my IM account has been compromised.
I have changed the password.
Is emesene really buggy? I never had any trouble wit it until recently.


As some of you guessed, we had to cut the Internet because of economic reasons.

*****

On a somewhat related note. The other laptop which belongs to my family (not mine) which runs Windows Vista has been compromised. I am fairly sure of this one.

They had an important software that occupied 1600 MB of HD space.
When they tried to use it last night, all the icons had disappeared. I search for the software and I saw that it was un-installed. All the shortcuts were gone from Start Menu and desktop.
I went to the Program Files folder and saw that software's folder was still there, but all the executables files and library files were gone.

Why do I arrive to this conclusion?
It is because I made every single account on that laptop as a limited account. They cannot remove or install programs unless they have my password. Think of it as Windows' sudo.

I have never gave them the password for my account. 

I don't know if anything else happened on that laptop. I did not have any time to look for it further.

But, all of this makes me think  it is not an accident.


Anyhow, thank you guys for all your help. 
I appreciate it a lot.
Perhaps, but I recall hearing something about Vista uninstalling programs on it's own that aren't used enough.

---

### Post by MrBrandon on 2009-04-10
I'm thinking Ubuntu27 is a pot smoker :lolflag:

---

### Post by ubuntu27 on 2009-04-10
> **kidux said:**
> Perhaps, but I recall hearing something about Vista uninstalling programs on it's own that aren't used enough.

Really? I never heard of it. I will search for it. 

> **MrBrandon said:**
> I'm thinking Ubuntu27 is a pot smoker :lolflag:

Woah! Ok, I see. Some people might think like that.

*********************


Thank you guys again.

In a couple of weeks I am reinstalling the OS with the Ubuntu Jaunty and start new.

---

