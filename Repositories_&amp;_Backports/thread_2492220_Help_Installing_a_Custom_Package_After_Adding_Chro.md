---
title: "Help Installing a Custom Package After Adding Chrony Dependency"
date: 2023-11-03
forum: Repositories &amp; Backports
---

### Post by 1hada on 2023-11-03
[COLOR=#3b3b3b][FONT=Droid Sans Mono][COLOR=#3b3b3b]We are running into an issue where we have a package being held back from an automated call to [/COLOR][COLOR=#800000]`apt-get dist-upgrade`[/COLOR][COLOR=#3b3b3b] that we do on boot, it breaks upon simply adding the dependency of [/COLOR][COLOR=#800000]`chrony`[/COLOR][COLOR=#3b3b3b].[/COLOR]

[LIST]
[*]How can we fix the issue across the fleet with the automated install? 
[/LIST]

[COLOR=#3b3b3b]The package we’re installing is a custom meta package which we host on our aptly server.[/COLOR]

[LIST]
[*][COLOR=#3b3b3b]Its sole purpose is to provide a list of other utility and tooling packages to install for our application. Examples include: bolt, can-utils, cpufrequtils, crda, cron, , and several others, etc. This has worked fine for years.[/COLOR] 
[*][COLOR=#3b3b3b]We usually never have an issue with installing new utility or any packages by adding them to the Depends portion of the debian/control file, but we are running into this issue when adding [/COLOR][COLOR=#800000]`chrony`[/COLOR][COLOR=#3b3b3b] as a Depends.[/COLOR] 
[/LIST]


[COLOR=#3b3b3b]This is a similar issue:[/COLOR]

[LIST]
[*][COLOR=#3b3b3b]https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/2016141
[/COLOR] 
[*][COLOR=#3b3b3b]In the linked bug they describe the issue being an upgrade to 245.4-4ubuntu3.21 / 245.4-4ubuntu3.20
[/COLOR] 
[*][COLOR=#3b3b3b]We believe our problem is slightly different than theirs simply because we use systemd/focal,now 245.4-4ubuntu3.15 amd64 [installed,automatic]
[/COLOR] 
[*][COLOR=#3b3b3b]We also believe we have a slightly nuanced requirement to ideally avoid updating systemd or any other packages aside from chrony; reason for this is that we have many servers in production which are controlling safety critical robots and would like to minimize unforeseen library interactions if possible.[/COLOR] 
[/LIST]


[COLOR=#3b3b3b]We think the issue has to do with the fact that chrony replaces/conflicts/provides time-daemon services:[/COLOR]


[COLOR=#3b3b3b]```
Conflicts: ntp, time-daemon
```[/COLOR]```


[COLOR=#3b3b3b] Replaces: time-daemon[/COLOR]

[COLOR=#3b3b3b] Provides: time-daemon[/COLOR]
```

[COLOR=#3b3b3b]And that time-daemon is currently provided by systemd-timesyncd. Which is where our problems start.[/COLOR]

[COLOR=#3b3b3b]These might also provide some relevant information:[/COLOR]

[LIST]
[*][COLOR=#3b3b3b]https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=902026
[/COLOR] 
[*][COLOR=#3b3b3b]https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=895821[/COLOR] 
[/LIST]
[COLOR=#3b3b3b]
[SIZE=5]Output of Solutions we've tried :[/SIZE][/COLOR]
[COLOR=#3b3b3b]When we only have the debian/control file set the Priority field set to required and add chrony as a Depends we see :[/COLOR]

[COLOR=#3b3b3b]```
server@server:~$ sudo apt-get -o Debug::pkgProblemResolver=yes dist-upgrade --dry-run
```[/COLOR]```

[COLOR=#3b3b3b]Reading package lists... Done[/COLOR]
[COLOR=#3b3b3b]Building dependency tree      [/COLOR]
[COLOR=#3b3b3b]Reading state information... Done[/COLOR]
[COLOR=#3b3b3b]Starting pkgProblemResolver with broken count: 2[/COLOR]
[COLOR=#3b3b3b]Starting 2 pkgProblemResolver with broken count: 2[/COLOR]
[COLOR=#3b3b3b]Investigating (0) systemd-timesyncd:amd64 < 245.4-4ubuntu3.15 @ii mK Ib >[/COLOR]
[COLOR=#3b3b3b]Broken systemd-timesyncd:amd64 Conflicts on time-daemon:amd64 < none @un H >[/COLOR]
[COLOR=#3b3b3b]  Conflicts//Breaks against version 1:6.2p3-4 for openntpd but that is not InstVer, ignoring[/COLOR]
[COLOR=#3b3b3b]  Conflicts//Breaks against version 1.1.8+dfsg1-4build1 for ntpsec but that is not InstVer, ignoring[/COLOR]
[COLOR=#3b3b3b]  Conflicts//Breaks against version 1:4.2.8p12+dfsg-3ubuntu4.20.04.1 for ntp but that is not InstVer, ignoring[/COLOR]
[COLOR=#3b3b3b]  Considering chrony:amd64 3 as a solution to systemd-timesyncd:amd64 17[/COLOR]
[COLOR=#3b3b3b]  Added chrony:amd64 to the remove list[/COLOR]
[COLOR=#3b3b3b]  Conflicts//Breaks against version 2.1.8-focal.20231103.154153 for CUSTOM-meta but that is not InstVer, ignoring[/COLOR]
[COLOR=#3b3b3b]  Fixing systemd-timesyncd:amd64 via keep of chrony:amd64[/COLOR]
[COLOR=#3b3b3b]Investigating (0) CUSTOM-meta:amd64 < 2.1.7-focal.20231025.184228 -> 2.1.8-focal.20231103.194012 @ii umU Ib >[/COLOR]
[COLOR=#3b3b3b]Broken CUSTOM-meta:amd64 Depends on chrony:amd64 < none | 3.5-6ubuntu6.2 @un uH >[/COLOR]
[COLOR=#3b3b3b]  Considering chrony:amd64 3 as a solution to CUSTOM-meta:amd64 4[/COLOR]
[COLOR=#3b3b3b]  Holding Back CUSTOM-meta:amd64 rather than change chrony:amd64[/COLOR]
[COLOR=#3b3b3b] Try to Re-Instate (1) CUSTOM-meta:amd64[/COLOR]
[COLOR=#3b3b3b]Done[/COLOR]
[COLOR=#3b3b3b]Calculating upgrade... Done[/COLOR]
[COLOR=#3b3b3b]The following packages have been kept back:[/COLOR]
[COLOR=#3b3b3b]  CUSTOM-meta[/COLOR]
[COLOR=#3b3b3b]0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.[/COLOR]
```


[COLOR=#3b3b3b]We tried copying the provides/conflicts statements to our CUSTOM-meta:[/COLOR]
[COLOR=#3b3b3b]And then installing. Also does not work. Here is the relevant debug output:[/COLOR]

[COLOR=#3b3b3b]```
server@server:~$ sudo apt-get -o Debug::pkgProblemResolver=yes dist-upgrade --dry-run
```[/COLOR]```

[COLOR=#3b3b3b]Reading package lists... Done[/COLOR]
[COLOR=#3b3b3b]Building dependency tree      [/COLOR]
[COLOR=#3b3b3b]Reading state information... Done[/COLOR]
[COLOR=#3b3b3b]Starting pkgProblemResolver with broken count: 2[/COLOR]
[COLOR=#3b3b3b]Starting 2 pkgProblemResolver with broken count: 2[/COLOR]
[COLOR=#3b3b3b]Investigating (0) systemd-timesyncd:amd64 < 245.4-4ubuntu3.15 @ii mK Ib >[/COLOR]
[COLOR=#3b3b3b]Broken systemd-timesyncd:amd64 Conflicts on time-daemon:amd64 < none @un H >[/COLOR]
[COLOR=#3b3b3b]  Conflicts//Breaks against version 1:6.2p3-4 for openntpd but that is not InstVer, ignoring[/COLOR]
[COLOR=#3b3b3b]  Conflicts//Breaks against version 1.1.8+dfsg1-4build1 for ntpsec but that is not InstVer, ignoring[/COLOR]
[COLOR=#3b3b3b]  Conflicts//Breaks against version 1:4.2.8p12+dfsg-3ubuntu4.20.04.1 for ntp but that is not InstVer, ignoring[/COLOR]
[COLOR=#3b3b3b]  Conflicts//Breaks against version 3.5-6ubuntu6.2 for chrony but that is not InstVer, ignoring[/COLOR]
[COLOR=#3b3b3b]  Considering CUSTOM-meta:amd64 4 as a solution to systemd-timesyncd:amd64 17[/COLOR]
[COLOR=#3b3b3b]  Added CUSTOM-meta:amd64 to the remove list[/COLOR]
[COLOR=#3b3b3b]  Fixing systemd-timesyncd:amd64 via keep of CUSTOM-meta:amd64[/COLOR]
[COLOR=#3b3b3b] Try to Re-Instate (0) CUSTOM-meta:amd64[/COLOR]
[COLOR=#3b3b3b]Done[/COLOR]
[COLOR=#3b3b3b]Calculating upgrade... Done[/COLOR]
[COLOR=#3b3b3b]The following packages have been kept back:[/COLOR]
[COLOR=#3b3b3b]  CUSTOM-meta[/COLOR]
[COLOR=#3b3b3b]0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.[/COLOR]
```





[SIZE=5][COLOR=#3b3b3b]Background :[/COLOR][/SIZE]


[COLOR=#3b3b3b]We maintain a fleet of Ubuntu 20.04 servers which uses a custom script to update download and then in a separate step install packages.[/COLOR]
[COLOR=#3b3b3b]The command we use to perform installation of the updated is :[/COLOR]

[COLOR=#3b3b3b]```
apt-get -y dist-upgrade --no-download
```[/COLOR]

[COLOR=#3b3b3b]Note: the reason for the [/COLOR][COLOR=#800000]`--no-download`[/COLOR][COLOR=#3b3b3b] is we already download them to speed up the installation process.[/COLOR]

[COLOR=#3b3b3b]From the debian/control file the package in question is currently installed as[/COLOR]

[COLOR=#3b3b3b]```
Section: embedded
```[/COLOR]```

[COLOR=#3b3b3b]Priority: optional[/COLOR]
```



[COLOR=#3b3b3b]Our hypothesis is that the issue is stemming from the fact that we are adding [/COLOR][COLOR=#800000]`chrony`[/COLOR][COLOR=#3b3b3b] as a new [/COLOR][COLOR=#800000]`Depends`[/COLOR][COLOR=#3b3b3b] and during the install process [/COLOR][COLOR=#800000]`chrony`[/COLOR][COLOR=#3b3b3b] will replace [/COLOR][COLOR=#800000]`systemd-timesyncd`[/COLOR]


[SIZE=5][COLOR=#3b3b3b]What we’ve tried :[/COLOR][/SIZE]



[COLOR=#3b3b3b]In order to test the above hypothesis we have tried updating the debian/control file for our custom package to look like :[/COLOR]

```


[COLOR=#3b3b3b]...[/COLOR]
[COLOR=#3b3b3b]Section: embedded[/COLOR]
[COLOR=#3b3b3b]Priority: required[/COLOR]
[COLOR=#3b3b3b]…[/COLOR]
[COLOR=#3b3b3b]Depends:[/COLOR]
[COLOR=#3b3b3b]…[/COLOR]
[COLOR=#3b3b3b]Chrony,[/COLOR]
[COLOR=#3b3b3b]…[/COLOR]
[COLOR=#3b3b3b]# We tried to match Chrony’s debian control fields for Conflicts, Provides, and Replaces https://salsa.debian.org/debian/chrony/-/blob/debian/latest/debian/control#L37[/COLOR]
[COLOR=#3b3b3b]Conflicts: time-daemon[/COLOR]
[COLOR=#3b3b3b]Provides: time-daemon[/COLOR]
[COLOR=#3b3b3b]Replaces: time-daemon[/COLOR]

```

[COLOR=#3b3b3b]Regardless of whether we match chrony's [/COLOR][COLOR=#800000]`Conflicts, Provides, Replaces`[/COLOR][COLOR=#3b3b3b] -- If we install the packages manually then we see that chrony and the custom package are installed without issue.[/COLOR]

[COLOR=#3b3b3b]Here we demonstrate it with a dry-run command[/COLOR]

[COLOR=#3b3b3b]```
chomper@GZDEV22:~$ sudo apt-get install -oDebug::pkgProblemResolver=1 CUSTOM-meta --dry-run
```[/COLOR]```

[COLOR=#3b3b3b]Reading package lists... Done[/COLOR]
[COLOR=#3b3b3b]Building dependency tree      [/COLOR]
[COLOR=#3b3b3b]Reading state information... Done[/COLOR]
[COLOR=#3b3b3b]Starting pkgProblemResolver with broken count: 1[/COLOR]
[COLOR=#3b3b3b]Starting 2 pkgProblemResolver with broken count: 1[/COLOR]
[COLOR=#3b3b3b]Investigating (0) CUSTOM-meta:amd64 < 2.1.7-focal.20231030.141854 -> 2.1.8-focal.20231103.154153 @ii pumU Ib >[/COLOR]
[COLOR=#3b3b3b]Broken CUSTOM-meta:amd64 Depends on chrony:amd64 < none | 3.5-6ubuntu6.2 @un uH >[/COLOR]
[COLOR=#3b3b3b]  Considering chrony:amd64 1 as a solution to CUSTOM-meta:amd64 10004[/COLOR]
[COLOR=#3b3b3b]  Re-Instated chrony:amd64[/COLOR]
[COLOR=#3b3b3b]Broken CUSTOM-meta:amd64 Conflicts on time-daemon:amd64 < none @un H >[/COLOR]
[COLOR=#3b3b3b]  Conflicts//Breaks against version 245.4-4ubuntu3.15 for systemd-timesyncd but that is not InstVer, ignoring[/COLOR]
[COLOR=#3b3b3b]  Conflicts//Breaks against version 1:6.2p3-4 for openntpd but that is not InstVer, ignoring[/COLOR]
[COLOR=#3b3b3b]  Conflicts//Breaks against version 1.1.8+dfsg1-4build1 for ntpsec but that is not InstVer, ignoring[/COLOR]
[COLOR=#3b3b3b]  Conflicts//Breaks against version 1:4.2.8p12+dfsg-3ubuntu4.20.04.1 for ntp but that is not InstVer, ignoring[/COLOR]
[COLOR=#3b3b3b]  Considering chrony:amd64 1 as a solution to CUSTOM-meta:amd64 10004[/COLOR]
[COLOR=#3b3b3b]  Added chrony:amd64 to the remove list[/COLOR]
[COLOR=#3b3b3b]  Fixing CUSTOM-meta:amd64 via remove of chrony:amd64[/COLOR]
[COLOR=#3b3b3b]Investigating (1) CUSTOM-meta:amd64 < 2.1.7-focal.20231030.141854 -> 2.1.8-focal.20231103.154153 @ii pumU Ib >[/COLOR]
[COLOR=#3b3b3b]Broken CUSTOM-meta:amd64 Depends on chrony:amd64 < none | 3.5-6ubuntu6.2 @un uH >[/COLOR]
[COLOR=#3b3b3b]  Considering chrony:amd64 1 as a solution to CUSTOM-meta:amd64 10004[/COLOR]
[COLOR=#3b3b3b]  Considering maas:amd64 0 as a solution to CUSTOM-meta:amd64 10004[/COLOR]
[COLOR=#3b3b3b]  Re-Instated squashfs-tools:amd64[/COLOR]
[COLOR=#3b3b3b]  Re-Instated snapd:amd64[/COLOR]
[COLOR=#3b3b3b]  Re-Instated maas:amd64[/COLOR]
[COLOR=#3b3b3b]Done[/COLOR]
[COLOR=#3b3b3b]The following additional packages will be installed:[/COLOR]
[COLOR=#3b3b3b]  maas snapd squashfs-tools[/COLOR]
[COLOR=#3b3b3b]Suggested packages:[/COLOR]
[COLOR=#3b3b3b]  zenity | kdialog[/COLOR]
[COLOR=#3b3b3b]The following packages will be REMOVED:[/COLOR]
[COLOR=#3b3b3b]  systemd-timesyncd[/COLOR]
[COLOR=#3b3b3b]The following NEW packages will be installed:[/COLOR]
[COLOR=#3b3b3b]  maas snapd squashfs-tools[/COLOR]
[COLOR=#3b3b3b]The following packages will be upgraded:[/COLOR]
[COLOR=#3b3b3b]  CUSTOM-meta[/COLOR]
[COLOR=#3b3b3b]1 upgraded, 3 newly installed, 1 to remove and 0 not upgraded.[/COLOR]
[COLOR=#3b3b3b]Inst squashfs-tools (1:4.4-1ubuntu0.3 ubuntu-experimental focal:focal [amd64])[/COLOR]
[COLOR=#3b3b3b]Inst snapd (2.51.1+20.04ubuntu2 ubuntu-experimental focal:focal [amd64])[/COLOR]
[COLOR=#3b3b3b]Conf squashfs-tools (1:4.4-1ubuntu0.3 ubuntu-experimental focal:focal [amd64])[/COLOR]
[COLOR=#3b3b3b]Conf snapd (2.51.1+20.04ubuntu2 ubuntu-experimental focal:focal [amd64])[/COLOR]

[COLOR=#3b3b3b]Inst maas (1:0.7 ubuntu-experimental focal:focal [all])[/COLOR]
[COLOR=#3b3b3b]Remv systemd-timesyncd [245.4-4ubuntu3.15] [systemd:amd64 ][/COLOR]
[COLOR=#3b3b3b]Inst CUSTOM-meta [2.1.7-focal.20231030.141854] (2.1.8-focal.20231103.154153 CUSTOM-experimental focal:focal [amd64])[/COLOR]
[COLOR=#3b3b3b]Conf maas (1:0.7 ubuntu-experimental focal:focal [all])[/COLOR]

[COLOR=#3b3b3b]Conf CUSTOM-meta (2.1.8-focal.20231103.154153 CUSTOM-experimental focal:focal [amd64])[/COLOR]
```

[/FONT][/COLOR]

---

