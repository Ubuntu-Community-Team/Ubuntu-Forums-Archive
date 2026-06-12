---
title: "Strange services and closed ports."
date: 2013-03-29
forum: Security
---

### Post by kleenex on 2013-03-29
Hi. Firstly; today I noticed, that four ports (135-139) are closed instead of stealth. I was doing a test on the grc.com website and check all common ports. That's pretty strange, because I do not have any service enabled on this system - no cups, no samba etc. Some time ago, these ports were stealth. No changes were made (I mean changes in services, iptables etc. area). This is a typical Desktop for music listening, movie watching etc. Can someone tell me why this is happening?

Secondly; I noticed two strange services: **-n** and **-f**. Yes! When I'm running e.g. [COLOR=#008000]update-rc.d [tab]_button[/COLOR] command I'm seeing this two services, except, of course, other services. Strange is that they are not in the **/etc/init.d/** directory! Someone knows something about this? I'm afraid a little.

---

### Post by Soul-Sing on 2013-03-30
'stealth' is an invention of mark G. It doesn't exist in the world of IT science. More relevant is the drop/reject discours in firewall discussions.
So the FAILED outcome on the website of mark G. gives you no indication if you'r system is doing fine.
All those ping related questions here also comes from this website. If you'r 'pingable', you'r system is in danger.!! (no way)

---

### Post by kleenex on 2013-03-30
Hi, have you written it with irony, right? I mean "system is in danger.!! (no way)" etc. things. OK. And what about this two, strange services; **-n **and **-f**? Both are visible via [COLOR=#008000]update-rc.d[/COLOR] command, but there is no such files in the **/etc/init.d/** directory.

---

### Post by CharlesA on 2013-03-30
Post the terminal output here so you will know for sure.

What Soul-Sing says it true, there is no difference between "stealth" and "closed" ports. Both settings drop traffic, but having your firewall silently drop packets can cause issues, which is why I use reject instead of drop in iptables.

---

### Post by Soul-Sing on 2013-03-30
I would suggest running:
sudo lsof -i -n -P
I post the outcome here. Services with portsnr. Would be interesting to see if the 135-139range is present.

---

### Post by kleenex on 2013-03-30
Hi guys. **CharlesA**; What output do you mean? Result of the [COLOR=#008000]update-rc.d[/COLOR] command? OK this issue with port is... pretty strange, because a couple of weeks ago, all ports were identified as stealth. Now, ports 135-139 are closed. This is strange, because I do not use Samba or something related to Windows.

**Soul-Sing**; here is the output of the **lsof** command;

```
[COLOR=#ff0000][~]$[/COLOR] [COLOR=#008000]sudo lsof -i -n -P[/COLOR]
[sudo] password for kleenex: 
COMMAND   PID  USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
dhclient 3317  root    6u  IPv4  18272     0t0  UDP *:port_number
firefox  4019 kleenex   22u  IPv4  20646   0t0  TCP 192.168.5.200:46212->173.194.70.120:443 (ESTABLISHED)
firefox  4019 kleenex   45u  IPv4  20644   0t0  TCP 192.168.5.200:58168->173.194.44.50:443 (ESTABLISHED)
firefox  4019 kleenex   53u  IPv4  19314   0t0  TCP 192.168.5.200:43974->173.194.65.100:443 (ESTABLISHED)
firefox  4019 kleenex   56u  IPv4  20656   0t0  TCP 192.168.5.200:43361->173.194.65.95:443 (ESTABLISHED)
``` Do you have some conclusions about this result?

---

### Post by Soul-Sing on 2013-03-30
google ip's. afaik nothing to worry about. very nice "empty" lsof.

---

### Post by kleenex on 2013-03-30
Hi **Soul**. Thank you for calming me down. But there is still the issue of these two services; **-n** and **-f** and closed (always were stealth) 135-139 ports (as I already mentioned, I do not use Samba etc.). Of course, thanks to you, I already know what is the difference between closed and stealth, but why suddenly these ports were marked as closed, while always have been stealth? I did not do anything related to [FONT=Verdana,Arial,Helvetica,Sans-Serif,MS Sans Serif][SIZE=-1][COLOR=#000066][FONT=Verdana,Arial,Helvetica,Sans-Serif,MS Sans Serif][SIZE=2][COLOR=#000066]dcom-scm [/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][COLOR=#000000][FONT=Verdana,Arial,Helvetica,Sans-Serif,MS Sans Serif][SIZE=-1][FONT=Verdana,Arial,Helvetica,Sans-Serif,MS Sans Serif][SIZE=2](port 135)[/SIZE][/FONT][/SIZE][/FONT][/COLOR], [FONT=Verdana,Arial,Helvetica,Sans-Serif,MS Sans Serif][SIZE=-1][COLOR=#000066][FONT=Verdana,Arial,Helvetica,Sans-Serif,MS Sans Serif][SIZE=2][COLOR=#000066]profile[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT] (port 136), [FONT=Verdana,Arial,Helvetica,Sans-Serif,MS Sans Serif][SIZE=-1][COLOR=#000066][FONT=Verdana,Arial,Helvetica,Sans-Serif,MS Sans Serif][SIZE=2][COLOR=#000066]netbios-ns[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT] (port 137) or [FONT=Verdana,Arial,Helvetica,Sans-Serif,MS Sans Serif][SIZE=-1][COLOR=#000066][FONT=Verdana,Arial,Helvetica,Sans-Serif,MS Sans Serif][SIZE=2][COLOR=#000066]netbios-dgm [/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][COLOR=#000000][FONT=Verdana,Arial,Helvetica,Sans-Serif,MS Sans Serif][SIZE=-1][FONT=Verdana,Arial,Helvetica,Sans-Serif,MS Sans Serif][SIZE=2](port 138) etc[/SIZE][/FONT][/SIZE][/FONT][/COLOR][FONT=Verdana,Arial,Helvetica,Sans-Serif,MS Sans Serif][SIZE=-1][COLOR=#000066][FONT=Verdana,Arial,Helvetica,Sans-Serif,MS Sans Serif][SIZE=2][COLOR=#000066].
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][TABLE]
[TR]
[TD][FONT=Verdana,Arial,Helvetica,Sans-Serif,MS Sans Serif][SIZE=2][COLOR=#000066][IMG]https://www.grc.com/image/transpixel.gif[/IMG]
[/COLOR][/SIZE][/FONT]
[/TD]
[/TR]
[/TABLE]

[TABLE]
[TR]
[TD="align: right"][/TD]
[TD][FONT=Verdana,Arial,Helvetica,Sans-Serif,MS Sans Serif][SIZE=2][COLOR=#000066][/COLOR][/SIZE][/FONT]
[/TD]
[/TR]
[/TABLE]

---

### Post by CharlesA on 2013-03-30
Looks like those are normal:

```
charles@Precise:~$ update-rc.d
acpid                        boinc-client                 friendly-recovery            mysql                        plymouth                     reboot                       skeleton                     ufw
acpi-support                 bootlogd                     grub-common                  [COLOR="#FF0000"]-n[/COLOR]                           plymouth-log                 resolvconf                   speech-dispatcher            umountfs
alsa-restore                 brltty                       halt                         networking                   plymouth-splash              rfkill-restore               ssh                          umountroot
alsa-store                   console-setup                hostname                     network-interface            plymouth-stop                rfkill-store                 stop-bootlogd                unattended-upgrades
anacron                      cron                         hwclock                      network-interface-container  plymouth-upstart-bridge      rsync                        stop-bootlogd-single         urandom
apache2                      cups                         hwclock-save                 network-interface-security   pppd-dns                     rsyslog                      sudo                         virtualbox-guest-utils
apparmor                     dbus                         irqbalance                   network-manager              procps                       saned                        udev                         whoopsie
apport                       dmesg                        kerneloops                   nxsensor                     pulseaudio                   screen-cleanup               udev-fallback-graphics       x11-common
atd                          dns-clean                    killprocs                    nxserver                     rc                           sendsigs                     udev-finish
avahi-daemon                 [COLOR="#FF0000"]-f[/COLOR]                           lightdm                      ondemand                     rc.local                     setvtrgb                     udevmonitor
bluetooth                    failsafe-x                   module-init-tools            passwd                       rcS                          single                       udevtrigger

```

As far as "Shields Up!" goes, if you are behind a router, it will scan the router not the PC. I wouldn't worry about ports showing up as closed vs stealth tbh.

FWIW, I ran the same lsof command on the box I have and it returned this:
```
charles@Precise:~$ sudo lsof -i -n -P
COMMAND    PID     USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
sshd       673     root    3r  IPv6   7624      0t0  TCP *:22 (LISTEN)
sshd       673     root    4u  IPv4   7626      0t0  TCP *:22 (LISTEN)
avahi-dae  783    avahi   12u  IPv4   7756      0t0  UDP *:5353
avahi-dae  783    avahi   13u  IPv6   7757      0t0  UDP *:5353
avahi-dae  783    avahi   14u  IPv4   7758      0t0  UDP *:48010
avahi-dae  783    avahi   15u  IPv6   7759      0t0  UDP *:42197
cupsd      810     root    8u  IPv4   7766      0t0  TCP 127.0.0.1:631 (LISTEN)
dhclient   987     root    6u  IPv4   7057      0t0  UDP *:68
mysqld    1108    mysql   10u  IPv4   9129      0t0  TCP 127.0.0.1:3306 (LISTEN)
apache2   1211     root    3u  IPv4   9707      0t0  TCP *:80 (LISTEN)
apache2   1226 www-data    3u  IPv4   9707      0t0  TCP *:80 (LISTEN)
apache2   1227 www-data    3u  IPv4   9707      0t0  TCP *:80 (LISTEN)
apache2   1228 www-data    3u  IPv4   9707      0t0  TCP *:80 (LISTEN)
apache2   1229 www-data    3u  IPv4   9707      0t0  TCP *:80 (LISTEN)
apache2   1230 www-data    3u  IPv4   9707      0t0  TCP *:80 (LISTEN)
dnsmasq   1616   nobody    4w  IPv4  10895      0t0  UDP 127.0.0.1:53
dnsmasq   1616   nobody    5u  IPv4  10896      0t0  TCP 127.0.0.1:53 (LISTEN)
ubuntu-ge 1733  lightdm    7u  IPv4   9163      0t0  TCP 192.168.1.30:58332->91.189.94.25:80 (CLOSE_WAIT)
sshd      2010     root    3r  IPv4  12349      0t0  TCP 192.168.1.30:22->192.168.1.15:56282 (ESTABLISHED)
sshd      2145  charles    3u  IPv4  12349      0t0  TCP 192.168.1.30:22->192.168.1.15:56282 (ESTABLISHED)

```

Of course, I am running Apache, MySQL, SSH, and Unity on that box.

---

### Post by Soul-Sing on 2013-03-30
CharlesA do you need that avahi? I just disable it with each install. Is it related with Apache, etc?

---

### Post by CharlesA on 2013-03-30
> **Soul-Sing said:**
> CharlesA do you need that avahi? I just disable it with each install. Is it related with Apache, etc?

Nah, it's probably leftover from the default install of 12.04. That box is running Vanilla 12.04 desktop with a few services added because I was using as my web development machine.

I checked my server box and avahi is nowhere to be seen (dnsmasq is gone too, but that's cuz network manager isn't installed.)

EDIT: Maybe I should move to Nginx instead of Apache. ;)

```
apache2    1553      root    3u  IPv4  14422      0t0  TCP *:80 (LISTEN)
apache2    1553      root    4u  IPv4  14425      0t0  TCP *:443 (LISTEN)
apache2    1578  www-data    3u  IPv4  14422      0t0  TCP *:80 (LISTEN)
apache2    1578  www-data    4u  IPv4  14425      0t0  TCP *:443 (LISTEN)
apache2    1579  www-data    3u  IPv4  14422      0t0  TCP *:80 (LISTEN)
apache2    1579  www-data    4u  IPv4  14425      0t0  TCP *:443 (LISTEN)
apache2    1583  www-data    3u  IPv4  14422      0t0  TCP *:80 (LISTEN)
apache2    1583  www-data    4u  IPv4  14425      0t0  TCP *:443 (LISTEN)
apache2    1586  www-data    3u  IPv4  14422      0t0  TCP *:80 (LISTEN)
apache2    1586  www-data    4u  IPv4  14425      0t0  TCP *:443 (LISTEN)
apache2    5044  www-data    3u  IPv4  14422      0t0  TCP *:80 (LISTEN)
apache2    5044  www-data    4u  IPv4  14425      0t0  TCP *:443 (LISTEN)
apache2    5047  www-data    3u  IPv4  14422      0t0  TCP *:80 (LISTEN)
apache2    5047  www-data    4u  IPv4  14425      0t0  TCP *:443 (LISTEN)
apache2    5048  www-data    3u  IPv4  14422      0t0  TCP *:80 (LISTEN)
apache2    5048  www-data    4u  IPv4  14425      0t0  TCP *:443 (LISTEN)
apache2    5049  www-data    3u  IPv4  14422      0t0  TCP *:80 (LISTEN)
apache2    5049  www-data    4u  IPv4  14425      0t0  TCP *:443 (LISTEN)
apache2    5050  www-data    3u  IPv4  14422      0t0  TCP *:80 (LISTEN)
apache2    5050  www-data    4u  IPv4  14425      0t0  TCP *:443 (LISTEN)
apache2   10745  www-data    3u  IPv4  14422      0t0  TCP *:80 (LISTEN)
apache2   10745  www-data    4u  IPv4  14425      0t0  TCP *:443 (LISTEN)

```

---

### Post by kleenex on 2013-03-31
Hi. **CharlesA** thank you very, very much. What do you think about these services; **-n** and **-f**? What is the purpose of these services? Yes, I'm behind a router. I will check security options and settings.
[B]
Soul-Sing[/B]; could you also check [COLOR=#008000]update-rc.d[/COLOR] command for **-n** and **-f** service? I would like to confirm that these services are available in *ubuntu by default. Thanks

---

### Post by CharlesA on 2013-03-31
They are not services, they are options.

Check out the man page when you get a chance.
[http://www.tin.org/bin/man.cgi?section=8&topic=update-rc.d](http://www.tin.org/bin/man.cgi?section=8&topic=update-rc.d)

---

### Post by kleenex on 2013-03-31
OK, that's interesting. But I'm still wonder why [COLOR=#008000]update-rc.d[/COLOR] command showed this. If they are options, it seems that we should see them for example by running [COLOR=#008000]update-rc.d --help[/COLOR] command etc. Solved. Thanks.

---

### Post by CharlesA on 2013-03-31
Could be a bug, I dunno though because Debian Squeeze does the same thing.

*shrugs*

---

