---
title: "New Virus For Ubuntu/Linux?"
date: 2009-01-27
forum: Security
---

### Post by Eagleon on 2009-01-27
Hi Guys,

Well here I was doing some research online for work, no apps open except the browser (FF3 or Epiphany, can't remember) and two terminals running htop. Suddenly I notice htop display CPU usage to 100% ... there is a process "whiptail" running, killing my CPU at 100% .. htop couldn't kill it (apparently invoked by root, right?), so I had to manually sudo kill it. There was also a --nocancel parameter I noticed, but can't remember what else I saw. Then after this process was dead my CPU immediately jumped to 100% again, but this time it was dpkg that started doing something. I didn't realize what it was doing at first -- I figured it was doing an automatic update and went back to work. Then suddenly I lost network connection while simultaneously realizing that I have auto-updates turned off (only notifications are on). Taking a closer look at the dpkg process in htop, I noticed that it was un-installing a whole bunch of programs. Before I knew it, half my system is gone and none of the icons on my desktop work. I quickly shut-down and rebooted the system, but everything was gone. No gnome, no nothing. startx does nothing too, says something about X being mis-configured. I went in recovery mode and tried a few things, but it was no use because everything was gone anyway. I am writing this from the Live CD. 

I have to work, so I am contemplating if I should reinstall everything or leave the system the way it is now so I can extract any useful info to post here.

---

### Post by cdenley on 2009-01-27
My first thought wouldn't be a virus. What kind of servers were you running? VNC or SSH? If you weren't running any servers, then my next guess would be your browser got exploited, but then that wouldn't explain how they got root. Have you enabled the root account?

Considering they did something as obvious and destructive as removing all your packages instead of quietly capturing data they can use for their own benefit or turning your system into a zombie, I suspect it was someone doing something simple. Either way, don't try to salvage your filesystem. You will never know for sure it is safe or what the attacker did.

If you want to figure out what happened, a good place to start looking is /var/log/auth.log.

---

### Post by Eagleon on 2009-01-27
Thanks for the reply cdenley!

I did have servers running, but they were firewalled. I had ssh, apache (for local dev), and mysql apart from whatever is pre-installed. I did a format and cleaned out my system a few days ago to install ubuntu 8.10 so there was nothing much on the system. I had put in the LAMP server using tasksel, so nothing manually there either. 

The only thing I had installed this morning was AllTray and mailnotify (mail-notification) this morning since I was trying to figure out the best way to keep evolution in the task bar (or get mail notifications). So apart from these two, nothing else.

I had a look at my auth.log as you suggested:

```

Jan 26 23:39:01 eagleon-laptop CRON[31725]: pam_unix(cron:session): session closed for user root
Jan 27 00:09:01 eagleon-laptop CRON[1548]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 27 00:09:01 eagleon-laptop CRON[1548]: pam_unix(cron:session): session closed for user root
Jan 27 00:17:01 eagleon-laptop CRON[2182]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 27 00:17:01 eagleon-laptop CRON[2182]: pam_unix(cron:session): session closed for user root

[..... a lot more cron here]

session opened for user root by (uid=0)
Jan 27 06:25:01 eagleon-laptop CRON[25319]: pam_unix(cron:session): session closed for user root
Jan 27 06:39:01 eagleon-laptop CRON[26487]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 27 06:39:01 eagleon-laptop CRON[26487]: pam_unix(cron:session): session closed for user root
Jan 27 06:45:44 eagleon-laptop sudo:  eagleon : TTY=unknown ; PWD=/home/eagleon ; USER=root ; COMMAND=/usr/sbin/synaptic
Jan 27 06:53:12 eagleon-laptop sudo:  eagleon : TTY=unknown ; PWD=/home/eagleon ; USER=root ; COMMAND=/usr/sbin/synaptic
Jan 27 07:09:01 eagleon-laptop CRON[29070]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 27 07:09:01 eagleon-laptop CRON[29070]: pam_unix(cron:session): session closed for user root
Jan 27 07:17:01 eagleon-laptop CRON[29735]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 27 07:17:01 eagleon-laptop CRON[29735]: pam_unix(cron:session): session closed for user root
Jan 27 07:27:46 eagleon-laptop sudo:  eagleon : TTY=unknown ; PWD=/home/eagleon ; USER=root ; COMMAND=/usr/sbin/synaptic --hide-main-window --non-interactive -o Synaptic::closeZvt=true --parent-window-id 54525955 --set-selections-file /tmp/tmp5QWvRO
Jan 27 07:30:01 eagleon-laptop CRON[30827]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 27 07:30:02 eagleon-laptop CRON[30827]: pam_unix(cron:session): session closed for user root
Jan 27 07:39:01 eagleon-laptop CRON[31741]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 27 07:39:01 eagleon-laptop CRON[31741]: pam_unix(cron:session): session closed for user root
Jan 27 07:47:03 eagleon-laptop sudo:  eagleon : TTY=unknown ; PWD=/home/eagleon ; USER=root ; COMMAND=/usr/sbin/synaptic
Jan 27 07:54:23 eagleon-laptop sudo:  eagleon : TTY=pts/3 ; PWD=/home/eagleon ; USER=root ; COMMAND=/usr/bin/tasksel
Jan 27 08:04:14 eagleon-laptop sudo:  eagleon : TTY=pts/1 ; PWD=/home/eagleon ; USER=root ; COMMAND=/bin/kill 584
Jan 27 08:04:18 eagleon-laptop sudo:  eagleon : TTY=pts/1 ; PWD=/home/eagleon ; USER=root ; COMMAND=/bin/kill 584
Jan 27 08:08:35 eagleon-laptop sudo:  eagleon : TTY=unknown ; PWD=/home/eagleon ; USER=root ; COMMAND=/usr/bin/software-properties-gtk
Jan 27 08:09:01 eagleon-laptop CRON[2939]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 27 08:09:01 eagleon-laptop CRON[2939]: pam_unix(cron:session): session closed for user root
Jan 27 08:12:12 eagleon-laptop gdm[5629]: pam_unix(gdm:session): session closed for user eagleon
Jan 27 08:13:44 eagleon-laptop login[5345]: pam_unix(login:session): session opened for user eagleon by LOGIN(uid=0)
Jan 27 08:14:11 eagleon-laptop sudo:  eagleon : TTY=tty1 ; PWD=/home/eagleon ; USER=root ; COMMAND=/usr/bin/tasksel
Jan 27 08:15:28 eagleon-laptop sudo:  eagleon : TTY=tty1 ; PWD=/home/eagleon ; USER=root ; COMMAND=/usr/bin/apt-get update
Jan 27 08:16:10 eagleon-laptop sudo:  eagleon : TTY=tty1 ; PWD=/home/eagleon ; USER=root ; COMMAND=/usr/bin/dpkg --configure -a
Jan 27 08:16:18 eagleon-laptop sudo:  eagleon : TTY=tty1 ; PWD=/home/eagleon ; USER=root ; COMMAND=/usr/bin/apt-get update
Jan 27 08:16:25 eagleon-laptop sudo:  eagleon : TTY=tty1 ; PWD=/home/eagleon ; USER=root ; COMMAND=/usr/bin/apt-get ugrade
Jan 27 08:17:01 eagleon-laptop CRON[5535]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 27 08:17:01 eagleon-laptop CRON[5535]: pam_unix(cron:session): session closed for user root
Jan 27 08:18:07 eagleon-laptop sudo:  eagleon : TTY=tty1 ; PWD=/usr/bin ; USER=root ; COMMAND=/usr/bin/apt-get install links2


```


The part where you start seeing "tasksel" is after I rebooted the system and I was trying to put ubuntu-desktop back... but that failed since there was no network connection. 

by the way, I also posted this question on linuxforums.org for those interested on seeing the replies there: #post662818

---

### Post by cdenley on 2009-01-27
So you open synaptic, then thirty minutes later install updates with the update manager and all your packages disappear? The fact that update manager installed and/or removed packages and within 20 minutes your desktop is gone can't be a coincidence. Are you sure you didn't accidentally unmark packages in synaptic or tasksel?

---

### Post by RaiCoss on 2009-01-27
Whiptail isn't a virus!

Just google it...

---

### Post by cdenley on 2009-01-27
> **RaiCoss said:**
> Whiptail isn't a virus!

Just google it...

Whiptail was probably opened by update manager while removing all his packages. However, someone or something had to select his packages to be removed. At the moment, I suspect user error.

---

### Post by Eagleon on 2009-01-27
I know its definitely not tasksel because I only ran tasksel after it all happened to tried and restore ubuntu-desktop. 

As for synaptic, I can be fairly certain that I did not deselect anything. I only used it to install AllTray and mailnotify. In fact, I think I used the Add/Remove feature in Application menu for AllTray or both -- I don't remember, but very unlikely that I deselected anything. Since the procedure was quick, and I continued with my work. I simply added "alltray evolution" command to my start up session, and left it as such to test it later. I didn't want to restart my session since I had work to do. So after working for a while (20 mins approx) with no activity on CPU, suddenly I see on htop that is "whiptail" eating the CPU at 100% -- then when I kill that dpkg uninstalls!

Crazy huh? :-S

---

### Post by Eagleon on 2009-01-27
> **RaiCoss said:**
> Whiptail isn't a virus!

Just google it...

 I know whiptail isnt a virus, never suggested it was :p -- i was just describing what happend! the first thing I actually did was lookup what whiptail was using the whatis command!

 whiptail (1)         - display dialog boxes from shell scripts

---

### Post by cdenley on 2009-01-27
So at 7:27, is that when you installed alltray? Then, at 7:47, you ran synaptic? Was that before or after you were having problems? Try these commands to see when those packages were removed.
```

grep -e -installed /var/log/dpkg.log
cat /var/log/aptitude
zcat /var/log/aptitude.1.gz

```

---

### Post by Eagleon on 2009-01-27
Alright, the aptitude log, nor the log archive for apt eixist. Could it be somewhere else?

I had to scan here: /media/disk-1/var/log

Since I am on the LiveCD, and /media/disk is "HOME", /media/disk-1 is "/"

for grep -e -installed /media/disk-1/var/log/dpkg.log, I get a long list...


```

2009-01-26 09:46:37 status half-installed vlc 0.9.4-1ubuntu3
2009-01-26 09:46:37 status half-installed vlc 0.9.4-1ubuntu3
2009-01-27 06:48:51 status half-installed libytnef0 1.5-1
2009-01-27 06:48:51 status half-installed evolution-plugins-experimental 2.24.2-0ubuntu1
2009-01-27 06:48:51 status half-installed evolution-rss 0.1.0-1ubuntu2
2009-01-27 06:48:51 status half-installed evolution-rss 0.1.0-1ubuntu2
2009-01-27 06:48:51 status half-installed mail-notification 5.4.dfsg.1-1build1
2009-01-27 06:48:51 status half-installed mail-notification 5.4.dfsg.1-1build1
2009-01-27 06:48:52 status half-installed mail-notification-evolution 5.4.dfsg.1-1build1
2009-01-27 07:27:51 status half-installed alltray 0.69-1ubuntu2
2009-01-27 07:27:51 status half-installed alltray 0.69-1ubuntu2
2009-01-27 08:04:19 status half-installed pulseaudio-module-hal 0.9.10-2ubuntu9.2
2009-01-27 08:04:19 status not-installed pulseaudio-module-hal <none>
2009-01-27 08:04:19 status half-installed network-manager-gnome 0.7~~svn20081020t000444-0ubuntu1.8.10.1
2009-01-27 08:04:20 status half-installed network-manager 0.7~~svn20081018t105859-0ubuntu1.8.10.1
2009-01-27 08:04:20 status half-installed network-manager 0.7~~svn20081018t105859-0ubuntu1.8.10.1
2009-01-27 08:04:20 status half-installed ubuntu-desktop 1.124
2009-01-27 08:04:20 status not-installed ubuntu-desktop <none>
2009-01-27 08:04:30 status half-installed gnome-power-manager 2.24.0-0ubuntu8.1
2009-01-27 08:04:31 status half-installed gnome-power-manager 2.24.0-0ubuntu8.1
2009-01-27 08:04:31 status half-installed lxde 0.3.2.1+svn20080509-2
2009-01-27 08:04:31 status not-installed lxde <none>
2009-01-27 08:04:31 status half-installed pcmanfm 0.5-3
2009-01-27 08:04:31 status half-installed pcmanfm 0.5-3
2009-01-27 08:04:40 status half-installed update-notifier 0.71.8
2009-01-27 08:04:41 status half-installed hal-cups-utils 0.6.17+git20080728-0ubuntu2
2009-01-27 08:04:41 status half-installed hal-cups-utils 0.6.17+git20080728-0ubuntu2
2009-01-27 08:04:41 status not-installed hal-cups-utils <none>
2009-01-27 08:04:49 status half-installed gnome-mount 0.8-1ubuntu1
2009-01-27 08:04:50 status half-installed gnome-mount 0.8-1ubuntu1
2009-01-27 08:04:50 status half-installed hal 0.5.11-4ubuntu4
2009-01-27 08:04:50 status half-installed hal 0.5.11-4ubuntu4
2009-01-27 08:04:50 status half-installed acl 2.2.47-2
2009-01-27 08:04:50 status half-installed acl 2.2.47-2
2009-01-27 08:04:50 status not-installed acl <none>
2009-01-27 08:04:50 status half-installed acpi 1.1-1ubuntu1
2009-01-27 08:04:50 status half-installed acpi 1.1-1ubuntu1
2009-01-27 08:04:50 status not-installed acpi <none>
2009-01-27 08:04:50 status half-installed powermanagement-interface 0.3.18
2009-01-27 08:04:50 status half-installed acpi-support 0.114-0intrepid2
2009-01-27 08:04:50 status half-installed acpi-support 0.114-0intrepid2
2009-01-27 08:04:50 status half-installed acpid 1.0.6-9ubuntu4
2009-01-27 08:04:50 status half-installed acpid 1.0.6-9ubuntu4
2009-01-27 08:04:51 status half-installed adobe-flashplugin 10.0.15.3-1hardy1
2009-01-27 08:04:51 status not-installed adobe-flashplugin <none>
2009-01-27 08:04:51 status half-installed alacarte 0.11.6-0ubuntu2
2009-01-27 08:04:51 status half-installed alacarte 0.11.6-0ubuntu2
2009-01-27 08:04:52 status half-installed alltray 0.69-1ubuntu2
2009-01-27 08:04:52 status half-installed alltray 0.69-1ubuntu2
2009-01-27 08:04:52 status half-installed alsa-base 1.0.17.dfsg-2ubuntu1
2009-01-27 08:04:52 status half-installed gdm-guest-session 0.6.1
2009-01-27 08:05:00 status half-installed fast-user-switch-applet 2.24.0-0ubuntu6
2009-01-27 08:05:01 status half-installed gdm 2.20.8-0ubuntu3
2009-01-27 08:05:01 status half-installed gdm 2.20.8-0ubuntu3
2009-01-27 08:05:01 status half-installed alsa-utils 1.0.17-0ubuntu3
2009-01-27 08:05:01 status half-installed alsa-utils 1.0.17-0ubuntu3
2009-01-27 08:05:01 status half-installed anacron 2.3-13.1ubuntu6
2009-01-27 08:05:01 status half-installed anacron 2.3-13.1ubuntu6
2009-01-27 08:05:01 status half-installed apache2 2.2.9-7ubuntu3
2009-01-27 08:05:01 status not-installed apache2 <none>
2009-01-27 08:05:01 status half-installed php5-mysql 5.2.6-2ubuntu4
2009-01-27 08:05:02 status half-installed libapache2-mod-php5 5.2.6-2ubuntu4
2009-01-27 08:05:05 status half-installed apache2-mpm-prefork 2.2.9-7ubuntu3
2009-01-27 08:05:05 status not-installed apache2-mpm-prefork <none>
2009-01-27 08:05:05 status half-installed apache2.2-common 2.2.9-7ubuntu3
2009-01-27 08:05:05 status half-installed apache2.2-common 2.2.9-7ubuntu3
2009-01-27 08:05:05 status half-installed apache2.2-common 2.2.9-7ubuntu3
2009-01-27 08:05:05 status half-installed apache2-utils 2.2.9-7ubuntu3
2009-01-27 08:05:05 status half-installed apache2-utils 2.2.9-7ubuntu3
2009-01-27 08:05:05 status not-installed apache2-utils <none>
2009-01-27 08:05:06 status half-installed apmd 3.2.2-10ubuntu1
2009-01-27 08:05:06 status half-installed apmd 3.2.2-10ubuntu1
2009-01-27 08:05:06 status half-installed ubufox 0.6-0ubuntu1.8.10.1
2009-01-27 08:05:14 status half-installed apturl 0.2.7ubuntu1
2009-01-27 08:05:14 status half-installed apturl 0.2.7ubuntu1
2009-01-27 08:05:22 status half-installed gnome-app-install 0.5.12-0ubuntu1
2009-01-27 08:05:23 status half-installed gnome-app-install 0.5.12-0ubuntu1
2009-01-27 08:05:23 status half-installed app-install-data 0.6.10.1
2009-01-27 08:05:24 status half-installed app-install-data-commercial 10
2009-01-27 08:05:24 status not-installed app-install-data-commercial <none>
2009-01-27 08:05:24 status half-installed apport-gtk 0.119
2009-01-27 08:05:24 status half-installed apport 0.119
2009-01-27 08:05:24 status half-installed apport 0.119
2009-01-27 08:05:26 status half-installed apt-xapian-index 0.15
2009-01-27 08:05:26 status half-installed apt-xapian-index 0.15
2009-01-27 08:05:26 status half-installed gnome-spell 1.0.8-0ubuntu1
2009-01-27 08:05:26 status not-installed gnome-spell <none>
2009-01-27 08:05:26 status half-installed aspell-en 6.0-0-5.1
2009-01-27 08:05:27 status half-installed aspell 0.60.6-1
2009-01-27 08:05:27 status half-installed aspell 0.60.6-1
2009-01-27 08:05:27 status not-installed aspell <none>
2009-01-27 08:05:27 status half-installed gnome-orca 2.24.1-0ubuntu1
2009-01-27 08:05:27 status half-installed gnome-orca 2.24.1-0ubuntu1
2009-01-27 08:05:28 status half-installed python-pyatspi 1.24.0-0ubuntu3
2009-01-27 08:05:28 status not-installed python-pyatspi <none>
2009-01-27 08:05:36 status half-installed at-spi 1.24.0-0ubuntu3
2009-01-27 08:05:37 status half-installed avahi-autoipd 0.6.23-2ubuntu2.1
2009-01-27 08:05:37 status half-installed avahi-autoipd 0.6.23-2ubuntu2.1
2009-01-27 08:05:37 status half-installed avahi-utils 0.6.23-2ubuntu2.1
2009-01-27 08:05:37 status half-installed avahi-utils 0.6.23-2ubuntu2.1
2009-01-27 08:05:37 status not-installed avahi-utils <none>
2009-01-27 08:05:37 status half-installed libnss-mdns 0.10-3ubuntu2
2009-01-27 08:05:38 status half-installed avahi-daemon 0.6.23-2ubuntu2.1
2009-01-27 08:05:38 status half-installed avahi-daemon 0.6.23-2ubuntu2.1
2009-01-27 08:05:38 status half-installed foomatic-db-hpijs 20080915-0ubuntu1
2009-01-27 08:05:38 status not-installed foomatic-db-hpijs <none>
2009-01-27 08:05:38 status half-installed hpijs 2.8.7-0ubuntu6
2009-01-27 08:05:38 status half-installed hpijs 2.8.7-0ubuntu6
2009-01-27 08:05:38 status not-installed hpijs <none>
2009-01-27 08:05:38 status half-installed hplip 2.8.7-0ubuntu6
2009-01-27 08:05:38 status half-installed cups-driver-gutenprint 5.2.0~rc1-0ubuntu1
2009-01-27 08:05:38 status half-installed cups-driver-gutenprint 5.2.0~rc1-0ubuntu1
2009-01-27 08:05:38 status half-installed bluez-cups 4.12-0ubuntu5
2009-01-27 08:05:39 status not-installed bluez-cups <none>
2009-01-27 08:05:39 status half-installed cups 1.3.9-2ubuntu6.1
2009-01-27 08:05:39 status half-installed cups 1.3.9-2ubuntu6.1
2009-01-27 08:05:39 status half-installed cups 1.3.9-2ubuntu6.1
2009-01-27 08:05:39 status half-installed cups 1.3.9-2ubuntu6.1
2009-01-27 08:05:39 status half-installed bc 1.06.94-3ubuntu1
2009-01-27 08:05:39 status half-installed bc 1.06.94-3ubuntu1
2009-01-27 08:05:39 status half-installed wine 1.1.13~winehq0~ubuntu~8.10-0ubuntu1
2009-01-27 08:05:40 status half-installed wine 1.1.13~winehq0~ubuntu~8.10-0ubuntu1
2009-01-27 08:05:40 status half-installed binfmt-support 1.2.11
2009-01-27 08:05:40 status half-installed binfmt-support 1.2.11
2009-01-27 08:05:40 status half-installed gcc 4:4.3.1-1ubuntu2
2009-01-27 08:05:40 status half-installed gcc 4:4.3.1-1ubuntu2
2009-01-27 08:05:40 status not-installed gcc <none>
2009-01-27 08:05:40 status half-installed gcc-4.3 4.3.2-1ubuntu11
2009-01-27 08:05:41 status half-installed gcc-4.3 4.3.2-1ubuntu11
2009-01-27 08:05:41 status not-installed gcc-4.3 <none>
2009-01-27 08:05:41 status half-installed binutils 2.18.93.20081009-0ubuntu1
2009-01-27 08:05:41 status half-installed binutils 2.18.93.20081009-0ubuntu1
2009-01-27 08:05:41 status half-installed bluez-utils 4.12-0ubuntu5
2009-01-27 08:05:41 status half-installed bluetooth 4.12-0ubuntu5
2009-01-27 08:05:41 status not-installed bluetooth <none>
2009-01-27 08:05:41 status half-installed bluez 4.12-0ubuntu5
2009-01-27 08:05:41 status half-installed bluez 4.12-0ubuntu5
2009-01-27 08:05:41 status half-installed bluez-alsa 4.12-0ubuntu5
2009-01-27 08:05:41 status not-installed bluez-alsa <none>
2009-01-27 08:05:41 status half-installed libmbca0 0.0.3~bzr42-0ubuntu2
2009-01-27 08:05:49 status half-installed bluez-gnome 1.8-0ubuntu1
2009-01-27 08:05:50 status half-installed bluez-gnome 1.8-0ubuntu1
2009-01-27 08:05:52 status half-installed bluez-gstreamer 4.12-0ubuntu5
2009-01-27 08:05:52 status not-installed bluez-gstreamer <none>
2009-01-27 08:05:52 status half-installed bogofilter 1.1.7-1ubuntu1
2009-01-27 08:05:52 status not-installed bogofilter <none>
2009-01-27 08:05:52 status half-installed bogofilter-bdb 1.1.7-1ubuntu1
2009-01-27 08:05:52 status not-installed bogofilter-bdb <none>
2009-01-27 08:05:52 status half-installed bogofilter-common 1.1.7-1ubuntu1
2009-01-27 08:05:52 status half-installed bogofilter-common 1.1.7-1ubuntu1
2009-01-27 08:06:00 status half-installed brasero 0.8.2-0ubuntu1
2009-01-27 08:06:01 status half-installed brasero 0.8.2-0ubuntu1
2009-01-27 08:06:01 status half-installed brltty-x11 3.10-0ubuntu2
2009-01-27 08:06:01 status half-installed brltty-x11 3.10-0ubuntu2
2009-01-27 08:06:02 status half-installed brltty 3.10-0ubuntu2
2009-01-27 08:06:02 status half-installed brltty 3.10-0ubuntu2
2009-01-27 08:06:02 status half-installed gnome-applets 2.24.1-0ubuntu1
2009-01-27 08:06:02 status half-installed gnome-applets 2.24.1-0ubuntu1
2009-01-27 08:06:02 status half-installed gnome-panel 1:2.24.1-0ubuntu2.1
2009-01-27 08:06:02 status half-installed gnome-panel 1:2.24.1-0ubuntu2.1
2009-01-27 08:06:02 status half-installed nautilus-share 0.7.2-0ubuntu7
2009-01-27 08:06:02 status not-installed nautilus-share <none>
2009-01-27 08:06:11 status half-installed nautilus-cd-burner 2.24.0-0ubuntu1
2009-01-27 08:06:11 status half-installed nautilus 1:2.24.1-0ubuntu1
2009-01-27 08:06:11 status half-installed nautilus 1:2.24.1-0ubuntu1
2009-01-27 08:06:19 status half-installed gnome-session 2.24.1-0ubuntu1
2009-01-27 08:06:20 status half-installed gnome-session 2.24.1-0ubuntu1
2009-01-27 08:06:20 status half-installed gnome-control-center 1:2.24.0.1-0ubuntu7.1
2009-01-27 08:06:20 status half-installed gnome-control-center 1:2.24.0.1-0ubuntu7.1
2009-01-27 08:06:30 status half-installed capplets-data 1:2.24.0.1-0ubuntu7.1
2009-01-27 08:06:32 status half-installed cdparanoia 3.10.0+debian-1
2009-01-27 08:06:32 status half-installed cdparanoia 3.10.0+debian-1
2009-01-27 08:06:32 status not-installed cdparanoia <none>
2009-01-27 08:06:32 status half-installed cdrdao 1:1.2.2-16
2009-01-27 08:06:32 status half-installed cdrdao 1:1.2.2-16
2009-01-27 08:06:32 status not-installed cdrdao <none>
2009-01-27 08:06:32 status half-installed checkgmail 1.13-3ubuntu1
2009-01-27 08:06:32 status half-installed checkgmail 1.13-3ubuntu1
2009-01-27 08:06:32 status half-installed f-spot 0.5.0.3-0ubuntu4
2009-01-27 08:06:32 status half-installed f-spot 0.5.0.3-0ubuntu4
2009-01-27 08:06:42 status half-installed tomboy 0.12.0-0ubuntu1
2009-01-27 08:06:42 status half-installed tomboy 0.12.0-0ubuntu1
2009-01-27 08:06:43 status half-installed libndesk-dbus-glib1.0-cil 0.4.1-1
2009-01-27 08:06:43 status not-installed libndesk-dbus-glib1.0-cil <none>
2009-01-27 08:06:43 status half-installed libgnome-keyring1.0-cil 1.0.0~svn.r87622-1
2009-01-27 08:06:43 status not-installed libgnome-keyring1.0-cil <none>
2009-01-27 08:06:44 status half-installed libndesk-dbus1.0-cil 0.6.0-1
2009-01-27 08:06:44 status not-installed libndesk-dbus1.0-cil <none>
2009-01-27 08:06:44 status half-installed libmono-addins-gui0.2-cil 0.3.1-5
2009-01-27 08:06:44 status not-installed libmono-addins-gui0.2-cil <none>
2009-01-27 08:06:45 status half-installed libmono-addins0.2-cil 0.3.1-5
2009-01-27 08:06:45 status not-installed libmono-addins0.2-cil <none>
2009-01-27 08:06:45 status half-installed libgmime2.2-cil 2.2.21-1
2009-01-27 08:06:45 status not-installed libgmime2.2-cil <none>
2009-01-27 08:06:46 status half-installed libflickrnet2.1.5-cil 25277-6build1
2009-01-27 08:06:46 status half-installed cli-common 0.5.7
2009-01-27 08:06:46 status not-installed cli-common <none>
2009-01-27 08:06:46 status half-installed compiz 1:0.7.8-0ubuntu4.1
2009-01-27 08:06:46 status not-installed compiz <none>
2009-01-27 08:06:54 status half-installed compiz-gnome 1:0.7.8-0ubuntu4.1
2009-01-27 08:06:54 status half-installed compiz-gnome 1:0.7.8-0ubuntu4.1
2009-01-27 08:06:55 status half-installed compiz-plugins 1:0.7.8-0ubuntu4.1
2009-01-27 08:06:55 status not-installed compiz-plugins <none>
2009-01-27 08:07:03 status half-installed compiz-fusion-plugins-main 0.7.8-0ubuntu2.2
2009-01-27 08:07:11 status half-installed compiz-fusion-plugins-extra 0.7.8-0ubuntu2
2009-01-27 08:07:11 status half-installed compiz-core 1:0.7.8-0ubuntu4.1
2009-01-27 08:07:11 status half-installed compiz-core 1:0.7.8-0ubuntu4.1
2009-01-27 08:07:11 status half-installed compiz-wrapper 1:0.7.8-0ubuntu4.1
2009-01-27 08:07:12 status not-installed compiz-wrapper <none>
2009-01-27 08:07:12 status half-installed compizconfig-backend-gconf 0.7.8-0ubuntu1
2009-01-27 08:07:12 status not-installed compizconfig-backend-gconf <none>
2009-01-27 08:07:12 status half-installed conky 1.6.1-0ubuntu3
2009-01-27 08:07:12 status half-installed conky 1.6.1-0ubuntu3
2009-01-27 08:07:12 status half-installed jockey-gtk 0.5~beta3-0ubuntu6.1
2009-01-27 08:07:12 status half-installed jockey-common 0.5~beta3-0ubuntu6.1
2009-01-27 08:07:12 status half-installed ubuntu-system-service 0.1.10
2009-01-27 08:07:12 status half-installed policykit-gnome 0.9-1ubuntu1
2009-01-27 08:07:13 status not-installed policykit-gnome <none>
2009-01-27 08:07:13 status half-installed policykit 0.9-1ubuntu3
2009-01-27 08:07:13 status half-installed policykit 0.9-1ubuntu3
2009-01-27 08:07:13 status half-installed tracker-utils 0.6.6-1ubuntu5.1
2009-01-27 08:07:13 status half-installed tracker-utils 0.6.6-1ubuntu5.1
2009-01-27 08:07:13 status not-installed tracker-utils <none>
2009-01-27 08:07:13 status half-installed tracker-search-tool 0.6.6-1ubuntu5.1
2009-01-27 08:07:13 status half-installed tracker-search-tool 0.6.6-1ubuntu5.1
2009-01-27 08:07:13 status half-installed libdeskbar-tracker 0.6.6-1ubuntu5.1
2009-01-27 08:07:13 status not-installed libdeskbar-tracker <none>
2009-01-27 08:07:13 status half-installed tracker 0.6.6-1ubuntu5.1
2009-01-27 08:07:13 status half-installed tracker 0.6.6-1ubuntu5.1
2009-01-27 08:07:13 status half-installed totem-mozilla 2.24.3-0ubuntu1
2009-01-27 08:07:14 status not-installed totem-mozilla <none>
2009-01-27 08:07:22 status half-installed rhythmbox 0.11.6svn20081008-0ubuntu4.2
2009-01-27 08:07:22 status half-installed rhythmbox 0.11.6svn20081008-0ubuntu4.2
2009-01-27 08:07:22 status half-installed evolution-plugins-experimental 2.24.2-0ubuntu1
2009-01-27 08:07:22 status not-installed evolution-plugins-experimental <none>
2009-01-27 08:07:22 status half-installed evolution-plugins 2.24.2-0ubuntu1
2009-01-27 08:07:22 status not-installed evolution-plugins <none>
2009-01-27 08:07:30 status half-installed evolution-exchange 2.24.2-0ubuntu1
2009-01-27 08:07:30 status half-installed evolution-exchange 2.24.2-0ubuntu1
2009-01-27 08:07:30 status half-installed mail-notification-evolution 5.4.dfsg.1-1build1
2009-01-27 08:07:30 status not-installed mail-notification-evolution <none>
2009-01-27 08:07:37 status half-installed evolution 2.24.2-0ubuntu1
2009-01-27 08:07:37 status half-installed evolution 2.24.2-0ubuntu1
2009-01-27 08:07:37 status half-installed firefox-gnome-support 3.0.5+nobinonly-0ubuntu0.8.10.1
2009-01-27 08:07:37 status not-installed firefox-gnome-support <none>
2009-01-27 08:07:37 status half-installed firefox-3.0-gnome-support 3.0.5+nobinonly-0ubuntu0.8.10.1
2009-01-27 08:07:37 status not-installed firefox-3.0-gnome-support <none>
2009-01-27 08:07:44 status half-installed epiphany-extensions 2.24.1-0ubuntu1
2009-01-27 08:07:44 status half-installed epiphany-browser 2.24.1-0ubuntu1
2009-01-27 08:07:44 status half-installed epiphany-browser 2.24.1-0ubuntu1
2009-01-27 08:07:44 status not-installed epiphany-browser <none>
2009-01-27 08:07:44 status half-installed epiphany-gecko 2.24.1-0ubuntu1
2009-01-27 08:07:44 status half-installed xulrunner-1.9-gnome-support 1.9.0.5+nobinonly-0ubuntu0.8.10.1
2009-01-27 08:07:44 status not-installed xulrunner-1.9-gnome-support <none>
2009-01-27 08:07:44 status half-installed totem 2.24.3-0ubuntu1
2009-01-27 08:07:44 status not-installed totem <none>
2009-01-27 08:07:44 status half-installed totem-plugins 2.24.3-0ubuntu1
2009-01-27 08:07:45 status not-installed totem-plugins <none>
2009-01-27 08:07:45 status half-installed totem-gstreamer 2.24.3-0ubuntu1
2009-01-27 08:07:45 status half-installed openoffice.org-gnome 1:2.4.1-11ubuntu2.1
2009-01-27 08:07:45 status not-installed openoffice.org-gnome <none>
2009-01-27 08:07:45 status half-installed libgtkhtml-editor0 1:3.24.1.1-0ubuntu1
2009-01-27 08:07:45 status half-installed libgtkhtml3.14-19 1:3.24.1.1-0ubuntu1
2009-01-27 08:07:45 status half-installed libgnome-window-settings1 1:2.24.0.1-0ubuntu7.1
2009-01-27 08:07:53 status half-installed gnome-settings-daemon 2.24.0-0ubuntu3.3
2009-01-27 08:07:53 status half-installed gnome-pilot-conduits 2.0.15-1.2
2009-01-27 08:07:53 status half-installed gnome-pilot-conduits 2.0.15-1.2
2009-01-27 08:07:53 status not-installed gnome-pilot-conduits <none>
2009-01-27 08:07:59 status half-installed gnome-pilot 2.0.15-2ubuntu4
2009-01-27 08:08:00 status half-installed gnome-pilot 2.0.15-2ubuntu4
2009-01-27 08:08:00 status half-installed gnome-games 1:2.24.1.1-0ubuntu1
2009-01-27 08:08:00 status half-installed gnome-games 1:2.24.1.1-0ubuntu1
2009-01-27 08:08:00 status half-installed seamonkey-gnome-support 1.1.12+nobinonly-0ubuntu1
2009-01-27 08:08:06 status half-installed mail-notification 5.4.dfsg.1-1build1
2009-01-27 08:08:07 status half-installed mail-notification 5.4.dfsg.1-1build1
2009-01-27 08:08:07 status half-installed galeon 2.0.6-2
2009-01-27 08:08:13 status half-installed seahorse-plugins 2.24.1-0ubuntu1
2009-01-27 08:08:14 status half-installed seahorse-plugins 2.24.1-0ubuntu1
2009-01-27 08:08:20 status half-installed deskbar-applet 2.24.1-0ubuntu1
2009-01-27 08:08:21 status half-installed python-gnome2-desktop 2.24.0-0ubuntu1
2009-01-27 08:08:21 status not-installed python-gnome2-desktop <none>
2009-01-27 08:08:22 status half-installed system-config-printer-gnome 1.0.5+git20080819-0ubuntu6
2009-01-27 08:08:22 status half-installed system-config-printer-gnome 1.0.5+git20080819-0ubuntu6
2009-01-27 08:08:22 status half-installed gnome-about 1:2.24.1-0ubuntu1
2009-01-27 08:08:22 status half-installed gnome-about 1:2.24.1-0ubuntu1
2009-01-27 08:08:22 status not-installed gnome-about <none>
2009-01-27 08:08:22 status half-installed python-gnome2 2.22.3-0ubuntu1
2009-01-27 08:08:22 status not-installed python-gnome2 <none>
2009-01-27 08:08:29 status half-installed mousetweaks 2.24.1-0ubuntu1
2009-01-27 08:08:29 status half-installed mousetweaks 2.24.1-0ubuntu1
2009-01-27 08:08:29 status half-installed libgnomevfs2-extra 1:2.24.0-0ubuntu1
2009-01-27 08:08:29 status half-installed libgnomevfs2-bin 1:2.24.0-0ubuntu1
2009-01-27 08:08:29 status not-installed libgnomevfs2-bin <none>
2009-01-27 08:08:36 status half-installed vinagre 2.24.1-0ubuntu1.1
2009-01-27 08:08:36 status half-installed vinagre 2.24.1-0ubuntu1.1
2009-01-27 08:08:37 status half-installed gnome-terminal 2.24.1.1-0ubuntu1
2009-01-27 08:08:37 status half-installed gnome-terminal 2.24.1.1-0ubuntu1
2009-01-27 08:08:37 status not-installed gnome-terminal <none>
2009-01-27 08:08:38 status half-installed ubuntu-docs 8.10.2
2009-01-27 08:08:38 status half-installed gnome-user-guide 2.24.0+svn20080922ubuntu1
2009-01-27 08:08:45 status half-installed yelp 2.24.0-0ubuntu2
2009-01-27 08:08:45 status half-installed yelp 2.24.0-0ubuntu2
2009-01-27 08:08:51 status half-installed vino 2.24.1-0ubuntu1
2009-01-27 08:08:51 status half-installed tsclient 0.150-1ubuntu3
2009-01-27 08:08:51 status half-installed tsclient 0.150-1ubuntu3
2009-01-27 08:08:52 status half-installed libgnome2.0-cil 2.20.1-1ubuntu1
2009-01-27 08:08:52 status not-installed libgnome2.0-cil <none>
2009-01-27 08:08:52 status half-installed libgnome2-perl 1.042-1build2
2009-01-27 08:08:52 status half-installed libgnome2-perl 1.042-1build2
2009-01-27 08:08:52 status not-installed libgnome2-perl <none>
2009-01-27 08:08:52 status half-installed gnome-media 2.24.0.1-0ubuntu1
2009-01-27 08:08:52 status half-installed gnome-media 2.24.0.1-0ubuntu1
2009-01-27 08:08:52 status half-installed libgnome-media0 2.24.0.1-0ubuntu1
2009-01-27 08:08:52 status half-installed libeel2-2 2.24.1-0ubuntu1
2009-01-27 08:08:58 status half-installed gnome-utils 2.24.1-0ubuntu1
2009-01-27 08:08:58 status half-installed gnome-utils 2.24.1-0ubuntu1
2009-01-27 08:09:04 status half-installed gnome-screensaver 2.24.0-0ubuntu2
2009-01-27 08:09:05 status half-installed gnome-screensaver 2.24.0-0ubuntu2
2009-01-27 08:09:10 status half-installed eog 2.24.1-0ubuntu1
2009-01-27 08:09:10 status half-installed eog 2.24.1-0ubuntu1
2009-01-27 08:09:11 status half-installed libgnome-desktop-2-7 1:2.24.1-0ubuntu1
2009-01-27 08:09:11 status half-installed libgail-gnome-module 1.20.0-1ubuntu1
2009-01-27 08:09:16 status half-installed gnome-netstatus-applet 2.12.2-0ubuntu1
2009-01-27 08:09:22 status half-installed gconf-editor 2.24.1-0ubuntu1
2009-01-27 08:09:22 status half-installed gconf-editor 2.24.1-0ubuntu1
2009-01-27 08:09:27 status half-installed file-roller 2.24.1-0ubuntu2
2009-01-27 08:09:27 status half-installed file-roller 2.24.1-0ubuntu2
2009-01-27 08:09:33 status half-installed evolution-webcal 2.24.0-0ubuntu1
2009-01-27 08:09:41 status half-installed ekiga 2.0.12-0ubuntu5
2009-01-27 08:09:41 status half-installed ekiga 2.0.12-0ubuntu5
2009-01-27 08:09:41 status half-installed contact-lookup-applet 0.16-1build1
2009-01-27 08:09:41 status not-installed contact-lookup-applet <none>
2009-01-27 08:09:41 status half-installed libgnomeui-0 2.24.0-0ubuntu1
2009-01-27 08:09:42 status half-installed libgnome2-vfs-perl 1.080-1build2
2009-01-27 08:09:42 status half-installed libgnome2-vfs-perl 1.080-1build2
2009-01-27 08:09:42 status not-installed libgnome2-vfs-perl <none>
2009-01-27 08:09:42 status half-installed libexchange-storage1.2-3 2.24.2-0ubuntu1
2009-01-27 08:09:42 status half-installed libedataserverui1.2-8 2.24.2-0ubuntu1
2009-01-27 08:09:42 status half-installed evolution-data-server 2.24.2-0ubuntu1
2009-01-27 08:09:42 status not-installed evolution-data-server <none>
2009-01-27 08:09:42 status half-installed libedata-cal1.2-6 2.24.2-0ubuntu1
2009-01-27 08:09:42 status half-installed libedata-book1.2-2 2.24.2-0ubuntu1
2009-01-27 08:09:42 status half-installed libecal1.2-7 2.24.2-0ubuntu1
2009-01-27 08:09:42 status half-installed libebook1.2-9 2.24.2-0ubuntu1
2009-01-27 08:09:42 status half-installed liblpint-bonobo0 0.1.21
2009-01-27 08:09:42 status half-installed libpanel-applet2-0 1:2.24.1-0ubuntu2.1
2009-01-27 08:09:42 status half-installed libbonoboui2-0 2.24.0-0ubuntu1
2009-01-27 08:09:43 status half-installed libgnome2-0 2.24.1-0ubuntu4
2009-01-27 08:09:43 status half-installed libgnome-vfs2.0-cil 2.20.1-1ubuntu1
2009-01-27 08:09:43 status not-installed libgnome-vfs2.0-cil <none>
2009-01-27 08:09:43 status half-installed gstreamer0.10-gnomevfs 0.10.21-3
2009-01-27 08:09:43 status not-installed gstreamer0.10-gnomevfs <none>
2009-01-27 08:09:43 status half-installed libgnomevfs2-0 1:2.24.0-0ubuntu1
2009-01-27 08:09:43 status half-installed dbus-x11 1.2.4-0ubuntu1
2009-01-27 08:09:43 status half-installed dbus-x11 1.2.4-0ubuntu1
2009-01-27 08:09:43 status half-installed cups-bsd 1.3.9-2ubuntu6.1
2009-01-27 08:09:44 status half-installed cups-bsd 1.3.9-2ubuntu6.1
2009-01-27 08:09:44 status half-installed cups-client 1.3.9-2ubuntu6.1
2009-01-27 08:09:44 status half-installed cups-client 1.3.9-2ubuntu6.1
2009-01-27 08:09:44 status not-installed cups-client <none>
2009-01-27 08:09:44 status half-installed cups-common 1.3.9-2ubuntu6.1
2009-01-27 08:09:44 status not-installed cups-common <none>
2009-01-27 08:09:44 status half-installed cupsddk 1.2.3-3
2009-01-27 08:09:44 status half-installed cupsddk 1.2.3-3
2009-01-27 08:09:44 status not-installed cupsddk <none>
2009-01-27 08:09:44 status half-installed cupsddk-drivers 1.2.3-3
2009-01-27 08:09:44 status half-installed cupsddk-drivers 1.2.3-3
2009-01-27 08:09:45 status not-installed cupsddk-drivers <none>
2009-01-27 08:09:45 status half-installed dc 1.06.94-3ubuntu1
2009-01-27 08:09:45 status half-installed dc 1.06.94-3ubuntu1
2009-01-27 08:09:45 status half-installed dc 1.06.94-3ubuntu1
2009-01-27 08:09:45 status half-installed dcraw 8.80-1
2009-01-27 08:09:45 status half-installed dcraw 8.80-1
2009-01-27 08:09:45 status not-installed dcraw <none>
2009-01-27 08:09:45 status half-installed lxappearance 0.2-4~lxde
2009-01-27 08:09:45 status half-installed lxappearance 0.2-4~lxde
2009-01-27 08:09:45 status not-installed lxappearance <none>
2009-01-27 08:09:45 status half-installed lxpanel 0.3.8.1-0.2ubuntu0.1
2009-01-27 08:09:45 status half-installed lxpanel 0.3.8.1-0.2ubuntu0.1
2009-01-27 08:09:45 status not-installed lxpanel <none>
2009-01-27 08:09:47 status half-installed flashplugin-nonfree 10.0.15.3ubuntu1~intrepid1
2009-01-27 08:09:47 status half-installed prism 0.8+svn20071115r8030-0ubuntu3
2009-01-27 08:09:47 status half-installed prism 0.8+svn20071115r8030-0ubuntu3
2009-01-27 08:09:49 status half-installed xulrunner-1.9-dom-inspector 1.9.0.5+nobinonly-0ubuntu0.8.10.1
2009-01-27 08:09:49 status not-installed xulrunner-1.9-dom-inspector <none>
2009-01-27 08:09:50 status half-installed firefox 3.0.5+nobinonly-0ubuntu0.8.10.1
2009-01-27 08:09:50 status not-installed firefox <none>
2009-01-27 08:09:55 status half-installed evolution-rss 0.1.0-1ubuntu2
2009-01-27 08:09:55 status half-installed evolution-rss 0.1.0-1ubuntu2
2009-01-27 08:09:55 status half-installed openoffice.org-gtk 1:2.4.1-11ubuntu2.1
2009-01-27 08:09:55 status not-installed openoffice.org-gtk <none>
2009-01-27 08:10:00 status half-installed openoffice.org-emailmerge 1:2.4.1-11ubuntu2.1
2009-01-27 08:10:00 status not-installed openoffice.org-emailmerge <none>
2009-01-27 08:10:00 status half-installed python-uno 1:2.4.1-11ubuntu2.1
2009-01-27 08:10:00 status not-installed python-uno <none>
2009-01-27 08:10:00 status half-installed openoffice.org-writer 1:2.4.1-11ubuntu2.1
2009-01-27 08:10:00 status half-installed openoffice.org-writer 1:2.4.1-11ubuntu2.1
2009-01-27 08:10:01 status half-installed openoffice.org-math 1:2.4.1-11ubuntu2.1
2009-01-27 08:10:01 status half-installed openoffice.org-math 1:2.4.1-11ubuntu2.1
2009-01-27 08:10:01 status half-installed openoffice.org-impress 1:2.4.1-11ubuntu2.1
2009-01-27 08:10:01 status half-installed openoffice.org-impress 1:2.4.1-11ubuntu2.1
2009-01-27 08:10:01 status half-installed openoffice.org-draw 1:2.4.1-11ubuntu2.1
2009-01-27 08:10:01 status half-installed openoffice.org-draw 1:2.4.1-11ubuntu2.1
2009-01-27 08:10:01 status half-installed openoffice.org-calc 1:2.4.1-11ubuntu2.1
2009-01-27 08:10:01 status half-installed openoffice.org-calc 1:2.4.1-11ubuntu2.1
2009-01-27 08:10:01 status half-installed language-support-en 1:8.10+20080703
2009-01-27 08:10:03 status not-installed language-support-en <none>
2009-01-27 08:10:03 status half-installed language-support-writing-en 1:8.10+20080904
2009-01-27 08:10:03 status half-installed openoffice.org-thesaurus-en-us 1:2.4.0-2ubuntu4
2009-01-27 08:10:03 status half-installed libtracker-gtk0 0.6.6-1ubuntu5.1
2009-01-27 08:10:04 status half-installed libtotem-plparser12 2.24.2-0ubuntu1
2009-01-27 08:10:04 status half-installed gimp 2.6.1-1ubuntu3
2009-01-27 08:10:04 status half-installed gimp 2.6.1-1ubuntu3
2009-01-27 08:10:09 status half-installed evince 2.24.1-0ubuntu1
2009-01-27 08:10:10 status half-installed evince 2.24.1-0ubuntu1
2009-01-27 08:10:10 status half-installed libpoppler-glib3 0.8.7-1ubuntu0.1
2009-01-27 08:10:16 status half-installed gedit 2.24.2-0ubuntu1
2009-01-27 08:10:17 status half-installed python-gtksourceview2 2.4.0-0ubuntu1
2009-01-27 08:10:17 status not-installed python-gtksourceview2 <none>
2009-01-27 08:10:17 status half-installed libgtksourceview2.0-0 2.4.1-0ubuntu1
2009-01-27 08:10:17 status half-installed zenity 2.24.0-0ubuntu1
2009-01-27 08:10:17 status half-installed zenity 2.24.0-0ubuntu1
2009-01-27 08:10:17 status half-installed python-gnomecanvas 2.22.3-0ubuntu1
2009-01-27 08:10:17 status not-installed python-gnomecanvas <none>
2009-01-27 08:10:17 status half-installed libgnomeprintui2.2-0 2.18.3-1
2009-01-27 08:10:17 status half-installed libgnome2-canvas-perl 1.002-1+b1ubuntu3
2009-01-27 08:10:17 status half-installed libgnome2-canvas-perl 1.002-1+b1ubuntu3
2009-01-27 08:10:17 status not-installed libgnome2-canvas-perl <none>
2009-01-27 08:10:17 status half-installed libgnomecanvas2-0 2.20.1.1-1ubuntu3
2009-01-27 08:10:17 status half-installed libavahi-ui0 0.6.23-2ubuntu2.1
2009-01-27 08:10:17 status half-installed mplayer 2:1.0~rc2-0ubuntu17
2009-01-27 08:10:17 status half-installed mplayer 2:1.0~rc2-0ubuntu17
2009-01-27 08:10:18 status half-installed xarchiver 0.4.6-8ubuntu1
2009-01-27 08:10:18 status half-installed xarchiver 0.4.6-8ubuntu1
2009-01-27 08:10:18 status half-installed seamonkey-browser 1.1.12+nobinonly-0ubuntu1
2009-01-27 08:10:18 status half-installed seamonkey-browser 1.1.12+nobinonly-0ubuntu1
2009-01-27 08:10:18 status half-installed openbox-themes 1.0.2
2009-01-27 08:10:18 status not-installed openbox-themes <none>
2009-01-27 08:10:19 status half-installed openbox 3.4.7.2-2
2009-01-27 08:10:19 status half-installed openbox 3.4.7.2-2
2009-01-27 08:10:19 status half-installed lxsession-lite 0.3.6-1
2009-01-27 08:10:19 status half-installed lxsession-lite 0.3.6-1
2009-01-27 08:10:19 status not-installed lxsession-lite <none>
2009-01-27 08:10:19 status half-installed lxrandr 0.1+svn20080716-1
2009-01-27 08:10:19 status half-installed lxrandr 0.1+svn20080716-1
2009-01-27 08:10:19 status not-installed lxrandr <none>
2009-01-27 08:10:19 status half-installed filezilla-locales 3.1.2-0ubuntu2
2009-01-27 08:10:19 status not-installed filezilla-locales <none>
2009-01-27 08:10:19 status half-installed filezilla 3.1.2-0ubuntu2
2009-01-27 08:10:19 status half-installed filezilla 3.1.2-0ubuntu2
2009-01-27 08:10:19 status half-installed libwxgtk2.8-0 2.8.8.0-0ubuntu2
2009-01-27 08:10:19 status half-installed libsexymm2 0.1.9-2
2009-01-27 08:10:19 status half-installed libobrender21 3.4.7.2-2
2009-01-27 08:10:19 status half-installed libgtk2-trayicon-perl 0.06-0ubuntu2
2009-01-27 08:10:19 status half-installed libgtk2-trayicon-perl 0.06-0ubuntu2
2009-01-27 08:10:19 status not-installed libgtk2-trayicon-perl <none>
2009-01-27 08:10:19 status half-installed leafpad 0.8.13-1
2009-01-27 08:10:19 status half-installed leafpad 0.8.13-1
2009-01-27 08:10:19 status half-installed kompozer 1:0.7.10-0ubuntu4
2009-01-27 08:10:19 status half-installed kompozer 1:0.7.10-0ubuntu4
2009-01-27 08:10:20 status not-installed kompozer <none>
2009-01-27 08:10:20 status half-installed gpicview 0.1.10-1
2009-01-27 08:10:20 status half-installed gpicview 0.1.10-1
2009-01-27 08:10:20 status not-installed gpicview <none>
2009-01-27 08:10:20 status half-installed xscreensaver 5.07-0ubuntu3
2009-01-27 08:10:20 status half-installed xscreensaver 5.07-0ubuntu3
2009-01-27 08:10:20 status half-installed xsane 0.995-3ubuntu2
2009-01-27 08:10:20 status half-installed xsane 0.995-3ubuntu2
2009-01-27 08:10:25 status half-installed update-manager 1:0.93.34
2009-01-27 08:10:25 status half-installed update-manager 1:0.93.34
2009-01-27 08:10:25 status half-installed software-properties-gtk 0.68.1
2009-01-27 08:10:26 status half-installed language-selector 0.3.17
2009-01-27 08:10:26 status not-installed language-selector <none>
2009-01-27 08:10:26 status half-installed synaptic 0.62.1ubuntu10
2009-01-27 08:10:26 status half-installed synaptic 0.62.1ubuntu10
2009-01-27 08:10:27 status half-installed ssh-askpass-gnome 1:5.1p1-3ubuntu1
2009-01-27 08:10:27 status half-installed ssh-askpass-gnome 1:5.1p1-3ubuntu1
2009-01-27 08:10:27 status not-installed ssh-askpass-gnome <none>
2009-01-27 08:10:31 status half-installed seahorse 2.24.1-0ubuntu1
2009-01-27 08:10:31 status half-installed seahorse 2.24.1-0ubuntu1
2009-01-27 08:10:32 status half-installed scim-bridge-client-gtk 0.4.14-2ubuntu5
2009-01-27 08:10:32 status not-installed scim-bridge-client-gtk <none>
2009-01-27 08:10:32 status half-installed scim-bridge-agent 0.4.14-2ubuntu5
2009-01-27 08:10:32 status half-installed scim-bridge-agent 0.4.14-2ubuntu5
2009-01-27 08:10:32 status half-installed gdebi 0.3.13
2009-01-27 08:10:32 status half-installed gdebi 0.3.13
2009-01-27 08:10:32 status not-installed gdebi <none>
2009-01-27 08:10:32 status half-installed python-vte 1:0.17.4-0ubuntu1
2009-01-27 08:10:32 status not-installed python-vte <none>
2009-01-27 08:10:32 status half-installed python-sexy 0.1.9-1ubuntu1
2009-01-27 08:10:33 status not-installed python-sexy <none>
2009-01-27 08:10:33 status half-installed python-notify 0.1.1-2build1
2009-01-27 08:10:33 status not-installed python-notify <none>
2009-01-27 08:10:33 status half-installed python-gtkhtml2 2.19.1-0ubuntu11
2009-01-27 08:10:33 status not-installed python-gtkhtml2 <none>
2009-01-27 08:10:33 status half-installed usb-creator 0.1.10
2009-01-27 08:10:33 status half-installed usb-creator 0.1.10
2009-01-27 08:10:33 status not-installed usb-creator <none>
2009-01-27 08:10:33 status half-installed gnome-menus 2.24.1-0ubuntu1
2009-01-27 08:10:33 status half-installed python-gmenu 2.24.1-0ubuntu1
2009-01-27 08:10:33 status not-installed python-gmenu <none>
2009-01-27 08:10:34 status half-installed onboard 0.91ubuntu2
2009-01-27 08:10:34 status half-installed hwtest-gtk 0.1-0ubuntu10
2009-01-27 08:10:34 status half-installed hwtest-gtk 0.1-0ubuntu10
2009-01-27 08:10:34 status half-installed python-glade2 2.13.0-0ubuntu8
2009-01-27 08:10:34 status not-installed python-glade2 <none>
2009-01-27 08:10:34 status half-installed python-beagle 0.3.5-1
2009-01-27 08:10:34 status not-installed python-beagle <none>
2009-01-27 08:10:34 status half-installed python-gtk2 2.13.0-0ubuntu8
2009-01-27 08:10:35 status not-installed python-gtk2 <none>
2009-01-27 08:10:35 status half-installed pidgin-otr 3.2.0-1
2009-01-27 08:10:35 status not-installed pidgin-otr <none>
2009-01-27 08:10:39 status half-installed pidgin 1:2.5.2-0ubuntu1
2009-01-27 08:10:39 status half-installed pidgin 1:2.5.2-0ubuntu1
2009-01-27 08:10:45 status half-installed notification-daemon 0.3.7-1ubuntu15
2009-01-27 08:10:52 status half-installed nautilus-sendto 1.1.0-0ubuntu1
2009-01-27 08:10:52 status half-installed nautilus-sendto 1.1.0-0ubuntu1
2009-01-27 08:10:53 status half-installed metacity 1:2.24.0-0ubuntu1
2009-01-27 08:10:53 status not-installed metacity <none>
2009-01-27 08:10:57 status half-installed gnome-system-monitor 2.24.1-0ubuntu1
2009-01-27 08:10:58 status half-installed gnome-system-monitor 2.24.1-0ubuntu1
2009-01-27 08:10:58 status half-installed libwnck22 2.24.1-0ubuntu1
2009-01-27 08:10:58 status half-installed libvte9 1:0.17.4-0ubuntu1
2009-01-27 08:10:58 status half-installed libsexy2 0.1.11-2
2009-01-27 08:10:59 status half-installed gnome-themes-extras 2.22.0-0ubuntu1
2009-01-27 08:11:01 status half-installed gnome-themes 2.24.1-0ubuntu1
2009-01-27 08:11:01 status half-installed tangerine-icon-theme 0.26.debian-1
2009-01-27 08:11:01 status half-installed gnome-icon-theme 2.24.0-0ubuntu1
2009-01-27 08:11:03 status half-installed gnome-accessibility-themes 2.24.1-0ubuntu1
2009-01-27 08:11:03 status half-installed librsvg2-common 2.22.3-0ubuntu1
2009-01-27 08:11:03 status not-installed librsvg2-common <none>
2009-01-27 08:11:03 status half-installed rss-glx 0.8.1-10ubuntu2
2009-01-27 08:11:03 status half-installed rss-glx 0.8.1-10ubuntu2
2009-01-27 08:11:03 status not-installed rss-glx <none>
2009-01-27 08:11:03 status half-installed obex-data-server 0.3.4+svn1951-0ubuntu1
2009-01-27 08:11:03 status half-installed obex-data-server 0.3.4+svn1951-0ubuntu1
2009-01-27 08:11:03 status half-installed libmagick10 7:6.3.7.9.dfsg1-2ubuntu3
2009-01-27 08:11:03 status half-installed librsvg2-2 2.22.3-0ubuntu1
2009-01-27 08:11:03 status half-installed libpolkit-gnome0 0.9-1ubuntu1
2009-01-27 08:11:03 status half-installed libgtkmm-2.4-1c2a 1:2.14.1-0ubuntu1
2009-01-27 08:11:03 status half-installed libpangomm-1.4-1 2.14.0-1
2009-01-27 08:11:04 status half-installed transmission-gtk 1.34-0ubuntu2.2
2009-01-27 08:11:04 status half-installed transmission-gtk 1.34-0ubuntu2.2
2009-01-27 08:11:04 status half-installed vlc 0.9.4-1ubuntu3
2009-01-27 08:11:04 status half-installed vlc 0.9.4-1ubuntu3
2009-01-27 08:11:04 status half-installed libnotify1 0.4.4-3build1
2009-01-27 08:11:04 status half-installed libmetacity0 1:2.24.0-0ubuntu1
2009-01-27 08:11:04 status half-installed python-launchpad-integration 0.1.21
2009-01-27 08:11:04 status not-installed python-launchpad-integration <none>
2009-01-27 08:11:08 status half-installed gucharmap 1:2.24.1-0ubuntu1
2009-01-27 08:11:09 status half-installed gucharmap 1:2.24.1-0ubuntu1
2009-01-27 08:11:09 status half-installed libgucharmap7 1:2.24.1-0ubuntu1
2009-01-27 08:11:09 status half-installed gnome-nettool 2.22.1-0ubuntu1
2009-01-27 08:11:13 status half-installed gcalctool 5.24.1-0ubuntu1
2009-01-27 08:11:14 status half-installed gcalctool 5.24.1-0ubuntu1
2009-01-27 08:11:14 status half-installed liblaunchpad-integration1 0.1.21
2009-01-27 08:11:14 status half-installed libgtkspell0 2.0.13-1
2009-01-27 08:11:14 status half-installed libgtksourceview1.0-0 1.8.5-1
2009-01-27 08:11:14 status half-installed libgtkhtml2-0 2.11.1-2ubuntu1
2009-01-27 08:11:14 status half-installed libgtk-vnc-1.0-0 0.3.7-0ubuntu2
2009-01-27 08:11:14 status half-installed libgtkglext1 1.2.0-1ubuntu1
2009-01-27 08:11:14 status half-installed libglade2.0-cil 2.12.1-1ubuntu2
2009-01-27 08:11:14 status not-installed libglade2.0-cil <none>
2009-01-27 08:11:14 status half-installed libgtk2.0-cil 2.12.1-1ubuntu2
2009-01-27 08:11:15 status not-installed libgtk2.0-cil <none>
2009-01-27 08:11:15 status half-installed xscreensaver-gl 5.07-0ubuntu3
2009-01-27 08:11:15 status half-installed xscreensaver-gl 5.07-0ubuntu3
2009-01-27 08:11:15 status half-installed screensaver-default-images 0.2-1
2009-01-27 08:11:15 status not-installed screensaver-default-images <none>
2009-01-27 08:11:15 status half-installed xscreensaver-data 5.07-0ubuntu3
2009-01-27 08:11:15 status half-installed xscreensaver-data 5.07-0ubuntu3
2009-01-27 08:11:15 status half-installed xdg-user-dirs-gtk 0.8-0ubuntu1
2009-01-27 08:11:15 status half-installed python-virtkey 0.50ubuntu1
2009-01-27 08:11:15 status not-installed python-virtkey <none>
2009-01-27 08:11:15 status half-installed libnautilus-extension1 1:2.24.1-0ubuntu1
2009-01-27 08:11:15 status half-installed libnautilus-burn4 2.24.0-0ubuntu1
2009-01-27 08:11:15 status half-installed libgweather1 2.24.1-0ubuntu1
2009-01-27 08:11:15 status half-installed libgtk2.0-bin 2.14.4-0ubuntu1
2009-01-27 08:11:15 status half-installed libgtk2.0-bin 2.14.4-0ubuntu1
2009-01-27 08:11:15 status not-installed libgtk2.0-bin <none>
2009-01-27 08:11:16 status half-installed libgtk2-perl 1:1.183-1
2009-01-27 08:11:16 status not-installed libgtk2-perl <none>
2009-01-27 08:11:16 status half-installed libgnomekbdui3 2.24.0-0ubuntu2
2009-01-27 08:11:16 status half-installed libgnomekbd3 2.24.0-0ubuntu2
2009-01-27 08:11:16 status half-installed gksu 2.0.0-5ubuntu3
2009-01-27 08:11:16 status half-installed gksu 2.0.0-5ubuntu3
2009-01-27 08:11:21 status half-installed libgksu2-0 2.0.7-1ubuntu3
2009-01-27 08:11:23 status half-installed libglade2-0 1:2.6.3-0ubuntu1
2009-01-27 08:11:23 status half-installed libgimp2.0 2.6.1-1ubuntu3
2009-01-27 08:11:23 status half-installed libgegl-0.0-0 0.0.18-1
2009-01-27 08:11:23 status half-installed libcryptui0 2.24.1-0ubuntu1
2009-01-27 08:11:23 status half-installed libcanberra-gtk-module 0.6-0ubuntu3
2009-01-27 08:11:23 status not-installed libcanberra-gtk-module <none>
2009-01-27 08:11:23 status half-installed libcanberra-gnome 0.6-0ubuntu3
2009-01-27 08:11:23 status not-installed libcanberra-gnome <none>
2009-01-27 08:11:23 status half-installed libcanberra-gtk0 0.6-0ubuntu3
2009-01-27 08:11:23 status half-installed gnome-mag 1:0.15.4-0ubuntu1
2009-01-27 08:11:23 status half-installed gnome-mag 1:0.15.4-0ubuntu1
2009-01-27 08:11:23 status not-installed gnome-mag <none>
2009-01-27 08:11:23 status half-installed libatspi1.0-0 1.24.0-0ubuntu3
2009-01-27 08:11:23 status half-installed gtk2-engines-pixbuf 2.14.4-0ubuntu1
2009-01-27 08:11:23 status not-installed gtk2-engines-pixbuf <none>
2009-01-27 08:11:23 status half-installed ubuntu-artwork 46.3
2009-01-27 08:11:24 status half-installed human-theme 0.28.6
2009-01-27 08:11:24 status not-installed human-theme <none>
2009-01-27 08:11:24 status half-installed gtk2-engines-murrine 0.60.1
2009-01-27 08:11:24 status not-installed gtk2-engines-murrine <none>
2009-01-27 08:11:24 status half-installed gtk2-engines 1:2.16.1-0ubuntu1
2009-01-27 08:11:24 status not-installed gtk2-engines <none>
2009-01-27 08:11:28 status half-installed gstreamer0.10-plugins-good 0.10.10.4-1ubuntu1
2009-01-27 08:11:34 status half-installed gnome-system-tools 2.22.1-0ubuntu1
2009-01-27 08:11:35 status half-installed gnome-system-tools 2.22.1-0ubuntu1
2009-01-27 08:11:40 status half-installed gnome-keyring 2.24.1-0ubuntu1
2009-01-27 08:11:40 status half-installed gnome-keyring 2.24.1-0ubuntu1
2009-01-27 08:11:40 status half-installed wv 1.2.4-2
2009-01-27 08:11:41 status half-installed wv 1.2.4-2
2009-01-27 08:11:41 status half-installed libwv-1.2-3 1.2.4-2
2009-01-27 08:11:41 status half-installed libwmf0.2-7 0.2.8.4-6
2009-01-27 08:11:41 status half-installed libgraphviz4 2.18-1ubuntu2
2009-01-27 08:11:41 status half-installed libgraphviz4 2.18-1ubuntu2
2009-01-27 08:11:42 status half-installed libgnomeprint2.2-0 2.18.5-1
2009-01-27 08:11:42 status half-installed gstreamer0.10-x 0.10.21-3
2009-01-27 08:11:42 status not-installed gstreamer0.10-x <none>
2009-01-27 08:11:42 status half-installed pnm2ppa 1.12-16.1ubuntu1
2009-01-27 08:11:42 status half-installed pnm2ppa 1.12-16.1ubuntu1
2009-01-27 08:11:42 status half-installed pnm2ppa 1.12-16.1ubuntu1
2009-01-27 08:11:42 status half-installed ghostscript-x 8.63.dfsg.1-0ubuntu6.1
2009-01-27 08:11:42 status not-installed ghostscript-x <none>
2009-01-27 08:11:50 status half-installed ghostscript 8.63.dfsg.1-0ubuntu6.1
2009-01-27 08:11:50 status half-installed ghostscript 8.63.dfsg.1-0ubuntu6.1
2009-01-27 08:12:02 status half-installed ttf-thai-tlwg 1:0.4.10-2
2009-01-27 08:12:03 status half-installed x-ttcidfont-conf 29
2009-01-27 08:12:12 status half-installed ttf-unfonts-core 1.0.1-7ubuntu1


```


What's strange is that I was working after 7:30 am ... I know because I looked at the time and noticed that I was behind on my project, so I stopped doing the evolution stuff for the time-being! Everything after 7:27 am is not me...

EDIT:


This was me too, I forgot about this:

```

2009-01-27 06:48:51 status half-installed evolution-plugins-experimental 2.24.2-0ubuntu1
2009-01-27 06:48:51 status half-installed evolution-rss 0.1.0-1ubuntu2
2009-01-27 06:48:51 status half-installed evolution-rss 0.1.0-1ubuntu2

```

---

### Post by Eagleon on 2009-01-27
...but looks like I did do something at 8:04 when all this happened! I killed whiptail! ....

---

### Post by cdenley on 2009-01-27
So someone else ran tasksel as your admin user at 7:54, then unchecked ubuntu-desktop, then selected OK? Did you run synaptic at 7:47?

---

### Post by Eagleon on 2009-01-27
It's very unlikely that I ran either tasksel or synaptic at that time, because I was already freaking out about being behind on my work. It was dark outside and didn't notice it was 7:30 am, (I was supposed to start work at 7:00)... so unless I had a blackout of some sort (unlikely), that was definitely not me!

EDIT: 

Although, even if tasksel was used to removed ubuntu-desktop by accident (let's just assume that was the case).. why did the network not work? Usually there is network access from the console without gnome or gnome netowkr manager. -- Hence why apt-get update or install failed!

EDIT2:

```

Jan 27 08:15:28 eagleon-laptop sudo:  eagleon : TTY=tty1 ; PWD=/home/eagleon ; USER=root ; COMMAND=/usr/bin/apt-get update
Jan 27 08:16:10 eagleon-laptop sudo:  eagleon : TTY=tty1 ; PWD=/home/eagleon ; USER=root ; COMMAND=/usr/bin/dpkg --configure -a
Jan 27 08:16:18 eagleon-laptop sudo:  eagleon : TTY=tty1 ; PWD=/home/eagleon ; USER=root ; COMMAND=/usr/bin/apt-get update
Jan 27 08:16:25 eagleon-laptop sudo:  eagleon : TTY=tty1 ; PWD=/home/eagleon ; USER=root ; COMMAND=/usr/bin/apt-get ugrade
Jan 27 08:17:01 eagleon-laptop CRON[5535]: pam_unix(cron:session): session opened for user root by (uid=0)
Jan 27 08:17:01 eagleon-laptop CRON[5535]: pam_unix(cron:session): session closed for user root
Jan 27 08:18:07 eagleon-laptop sudo:  eagleon : TTY=tty1 ; PWD=/usr/bin ; USER=root ; COMMAND=/usr/bin/apt-get install links2

```

see, I tried to update and it failed to fetch there. Also tried installing a text browser to test if there was a network connection (which also failed), and I remember confirming that I didn't have netowrk conn by trying something else afterwards. My other computer had internet on the same network just fine.

---

### Post by cdenley on 2009-01-27
> **Eagleon said:**
> Although, even if tasksel was used to removed ubuntu-desktop by accident (let's just assume that was the case).. why did the network not work? Usually there is network access from the console without gnome or gnome netowkr manager. -- Hence why apt-get update or install failed!
Network-manager was removed. Without network-manager and without a configured /etc/network/interfaces file, you have no network settings.

Someone removed ubuntu-desktop with tasksel as eagleon, whether it was locally, through a VNC/remote desktop session, or a remote terminal session such as SSH. Since they first ran synaptic on an unknown TTY, I suspect it was the graphical version, so a remote terminal session seems unlikely.

---

### Post by Eagleon on 2009-01-27
could it have been a remote terminal with X11 forwarding? 

I was wondering though, is network-manager a part of ubuntu-desktop package in tasksel? In the past, I remember once I removed ubuntu-desktop (using tasksel), used apt-get to install fluxbox (downloading over the internet) and the network was fine! 

I think this was probably/most-likely not a virus as I had assumed first, but rather an intrusion like you are saying.

One thing I noticed in the last few days that might be of interest is that my computer kept reaching 100% randomly for some process X11r6 ... with a lot of params attached to it, but I would kill it. Do you think someone was trying to evesdrop on my X11 session, and finally did this?


EDIT: 
Here is the proccess I mentioned, is it normal for this to run randomly causing 100% CPU?

```

/usr/x11r6/bin/x :0 -br -audit 0 -auth /var/lib/gdm:0.Xauth -nolisten tcp vt7

```

I found the string from my Firefox history in the home partiton, since I had been trying to figure out what that was, yesterday!

---

### Post by cdenley on 2009-01-27
I suppose it could be a forwarded x11 session through ssh. However, I didn't see any SSH authentications in /var/log/auth.log, but they could have been logged in for days or edited that log file.

Network-manager is part of ubuntu-desktop, and the output you posted indicated it was removed along with everything else. It is new, I think as of intrepid, or maybe hardy. Anyway, before that, the /etc/network/interfaces was always used, and removing the desktop would not have caused you to lose your network settings.

That process is normal. It is a regular X session. If you kill it, I would expect X, GDM, and gnome to crash and restart.

---

### Post by beyboo on 2009-01-27
cant help musing here. Looking at questions down to precision of minutes and seconds, t'is a classic case for Hercule Poirot !!

---

### Post by Eagleon on 2009-01-27
Oh, I see. I guess that explains it about the network manager. thanks again for your help, i appreciate it. By the way, i am on my wife's asus eee pc now so it's hrd to type, but i rebooted into the system again, looks like tasksel does not work anymore either. it just drops me back to prompt. I tried using the CD as a repo, but dosen't have ubuntu-desktop. ubuntu-standard and ubuntu-minimal is installed, but startx does not work.

looks like i am going to have to reinstall from scratch. probably going to keep this system as it is (just in case, for further analysis) and put a full installation in the home partition

---

### Post by Eagleon on 2009-01-27
> **beyboo said:**
> cant help musing here. Looking at questions down to precision of minutes and seconds, t'is a classic case for Hercule Poirot !!

lol

edit: 

i sure do appreciate the help tho, i managed to stay sane by talking to you!

edit2;

oops, just realized this comment was form beyboo and not cdenley lol, this eee pc screen is so small, cant see a thing! -- anyway, that thanks was meant for cdenley :)

---

