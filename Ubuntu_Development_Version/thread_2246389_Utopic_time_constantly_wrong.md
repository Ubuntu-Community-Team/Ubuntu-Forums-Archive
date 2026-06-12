---
title: "Utopic time constantly wrong"
date: 2014-09-30
forum: Ubuntu Development Version
---

### Post by Cavsfan on 2014-09-30
My time on Utopic is usually 4 hours or so off. So I thought i'd try to fix it since the ability to set the time from the internet in Time & Date is greyed out.

I am in the US in Eastern Time however even this gets it wrong.

```
cavsfan@cavsfan-MS-7529:~$ sudo dpkg-reconfigure tzdata

Current default time zone: 'America/New_York'
Local time is now:      Tue Sep 30 08:09:32 EDT 2014.
Universal Time is now:  Tue Sep 30 12:09:32 UTC 2014.
```

The clock stated 08:09 AM and it was actually 12:09 PM when I did this and it is still wrong. Am I missing something?

---

### Post by QIII on 2014-09-30
Did you set 

```
 UTC=no 
```

In /etc/default/rcS?

I think Eastern time may be UTC -4.

---

### Post by Cavsfan on 2014-09-30
> **QIII said:**
> Did you set 

```
 UTC=no 
```

In /etc/default/rcS?

I think Eastern time may be UTC -4.

I'll check that. I booted into Utopic Mate and it's good as far as the time goes. I've had fewer problems with Mate although somethings are harder to accomplish.

Thanks!

---

### Post by Cavsfan on 2014-09-30
It's set to no. What should it be yes? The time is correct for the moment 

```
# assume that the BIOS clock is set to UTC time (recommended)
UTC=no
```

---

### Post by Cavsfan on 2014-09-30
Tried reading the rcS man page but can't really tell what's going on. But, I did notice that Eastern is symlinked which seems weird:
```
cavsfan@cavsfan-MS-7529:~$ cd /usr/share/zoneinfo/US/
cavsfan@cavsfan-MS-7529:/usr/share/zoneinfo/US$ ls -l
total 32
-rw-r--r-- 1 root root 2358 Aug 31 15:20 Alaska
-rw-r--r-- 1 root root 2353 Aug 31 15:20 Aleutian
-rw-r--r-- 1 root root  327 Aug 31 15:20 Arizona
-rw-r--r-- 1 root root 3559 Aug 31 15:20 Central
lrwxrwxrwx 1 root root   13 Aug 31 15:20 [COLOR=#3366ff]Eastern[/COLOR] -> ../posixrules
-rw-r--r-- 1 root root 1649 Aug 31 15:20 East-Indiana
lrwxrwxrwx 1 root root   19 Aug 31 15:20 [COLOR=#3366ff]Hawaii[/COLOR] -> ../Pacific/Johnston
-rw-r--r-- 1 root root 2411 Aug 31 15:20 Indiana-Starke
-rw-r--r-- 1 root root 2202 Aug 31 15:20 Michigan
lrwxrwxrwx 1 root root    9 Aug 31 15:20 [COLOR=#3366ff]Mountain[/COLOR] -> ../Navajo
-rw-r--r-- 1 root root 2819 Aug 31 15:20 Pacific
lrwxrwxrwx 1 root root    7 Aug 31 15:20 [COLOR=#3366ff]Pacific-New[/COLOR] -> Pacific
lrwxrwxrwx 1 root root   16 Aug 31 15:20 [COLOR=#3366ff]Samoa[/COLOR] -> ../Pacific/Samoa

```

---

### Post by Cavsfan on 2014-09-30
I see on all of my installs: 
UTC=no in /etc/default/rcS

So that must be standard with a multi boot system including windows. Most be a glitch as it usally works itself out.

My windows 7 os I'd swear is jealous from me being in Ubuntu 99% of the day.
Because when I boot into windows at the end of the day the time is off there too. I have to find another server for it to get the time off of. :p

If it weren't for my wife who gets on windows in the morning I'd leave it in Ubuntu most of the time.

---

### Post by Bashing-om on 2014-09-30
Cavsfan; Hello ,

How bout this for a thought ?
To tell your Ubuntu system that the hardware clock is set to 'local' time:

edit /etc/default/rcS
add or change the following section # Set UTC=yes if your hardware clock is set to UTC (GMT)
UTC=no

 Windows defaults to considering the hardware clock to being local time. Ubuntu (and pretty much all *NIX systems) defaults to considering the hardware clock to be UTC. So every time you boot Windows it's "fixing" the hardware clock, and setting it back 4 hours from UTC to your local time.

[INDENT][INDENT]out of my small bag of knowledge
[/INDENT][/INDENT]

---

### Post by Cavsfan on 2014-09-30
> **Bashing-om said:**
> Cavsfan; Hello ,

How bout this for a thought ?
To tell your Ubuntu system that the hardware clock is set to 'local' time:

edit /etc/default/rcS
add or change the following section # Set UTC=yes if your hardware clock is set to UTC (GMT)
UTC=no

 Windows defaults to considering the hardware clock to being local time. Ubuntu (and pretty much all *NIX systems) defaults to considering the hardware clock to be UTC. So every time you boot Windows it's "fixing" the hardware clock, and setting it back 4 hours from UTC to your local time.[INDENT][INDENT]out of my small bag of knowledge
[/INDENT]
[/INDENT]


So, you are saying change UTC=no to UTC=yes in /etc/default/rcS ? I just want to be clear. As you can see from my signature I've got 6 Linux systems on here and I looked at some of the other /etc/default/rcS files and they all had UTC=no.

My Windows setup every night about this time when I get on it to play NFSMW :lol: (I only play games where you use the arrow keys lol) the clock is always wrong.
I open up clock and click on internet time and have to change the server to a different one. Sometimes the first one I choose works and sometimes the 2nd one works.

When my wife gets up in the morning (too early for me) she says the time is always good and when I look at it in the morning it's good.
I changed the battery on the mobo about a year ago thinking that had something to do with the clock but it didn't change anything. Also this pc is about 5 or so years old.

Thanks!

---

### Post by Bashing-om on 2014-09-30
Cavsfan; Welp;

The default:
> 
# assume that the BIOS clock is set to UTC time (recommended)
UTC=yes


In most cases dual booting with Windows - from what little I have observed - one would set that to "no", BUT that depends on what Windows is doing to the hardware clock.

Won't hurt a thing to test with the alternate option in the file " /etc/default/rcS " and see what results.

[INDENT][INDENT]just a suggestion
[/INDENT][/INDENT]

---

### Post by Sophont on 2014-10-01
The 4 hour difference between UTC and US east cost ist correct (NYC is -5 from UTC, modified by 1 hour for DST).

So the problem seems to be that your desktop shows UTC instead of your local time.

When you click on the upper right corner on the time, what place does the menu item mention - NYC or UTC.

Under upper right clock menu -> Time & Date Settings -> Clock you can select the locations that are displayed.

---

### Post by Cavsfan on 2014-10-01
> **Bashing-om said:**
> Cavsfan; Welp;

The default:


In most cases dual booting with Windows - from what little I have observed - one would set that to "no", BUT that depends on what Windows is doing to the hardware clock.

Won't hurt a thing to test with the alternate option in the file " /etc/default/rcS " and see what results.[INDENT][INDENT]just a suggestion
[/INDENT]
[/INDENT]


I may have to try that. Yesterday eve when I got into Windows the time was correct for the first time in a long time. It is set to get the time from the internet.
 I just booted into Trusty and the time was correct there.


> **Sophont said:**
> The 4 hour difference between UTC and US east cost ist correct (NYC is -5 from UTC, modified by 1 hour for DST).

So the problem seems to be that your desktop shows UTC instead of your local time.

When you click on the upper right corner on the time, what place does the menu item mention - NYC or UTC.

Under upper right clock menu -> Time & Date Settings -> Clock you can select the locations that are displayed.

When I click on the time and date settings they are exactly 4 hours off although it thinks I am in New York.

[ATTACH=CONFIG]256866[/ATTACH]

This is getting old. :confused:

---

### Post by Cavsfan on 2014-10-01
Changed UTC to yes, rebooted and still four hours off. Also got a lot of updates but still no beuno :-(

```
cavsfan@cavsfan-MS-7529:~$ sudo dpkg-reconfigure tzdata
[sudo] password for cavsfan: 

Current default time zone: 'America/New_York'
Local time is now:      Wed Oct  1 08:59:32 EDT 2014.
Universal Time is now:  Wed Oct  1 12:59:32 UTC 2014.

```

The UTC time is right for my location but I am in Eastern Time which is still wrong.

---

### Post by Cavsfan on 2014-10-01
This is the only thing that works.

**sudo ntpdate ntp.ubuntu.com**

I tried to setup a script to run at startup with root privileges and owned by root but that didn't work.

I fail to see the necessity to create a fix for something that should work.

So I guess I'll just execute that command when I boot into Utopic. :rolleyes:

---

### Post by zika on 2014-10-01
This is not a remedy but just an answer to Your question how to execute a command with root priviledges automatically.
1. /etc/rc.local
2. /usr/share/lightdm/lightdm.conf.d/
> 
If you need some special behaviour when X servers and  user sessions start/stop you can set commands to be run with the  following configuration: 

[SeatDefaults]
display-setup-script=command
display-stopped-script=command (Not in Ubuntu 12.04 LTS)
greeter-setup-script=command
session-setup-script=command
session-cleanup-script=command
session-wrapper=command
greeter-wrapper=command (Not in Ubuntu 12.04 LTS)**display-setup-script**  is run after the X server starts but before the user session / greeter  is run. Set this if you need to configure anything special in the X  server. It is run as root. If this command returns an error code the X  server is stopped. 
**display-stopped-script** is run after an X server exits. It is run as root. 
**greeter-setup-script**  is run before a greeter starts. It is run as root. If this command  returns an error code the greeter fails to start (which will cause  LightDM to stop). 
**session-setup-script**  is run before a user session starts. If this command returns an error  the session will not start (user is returned to a greeter). 
**session-cleanup-script** is run after a greeter or user session stops. It is run as root. 
**session-wrapper**  is a the command to run for a session. This command is run as the user  and needs to exec the command passed in the arguments to complete  running the session. Use this if you need to do special setup for a user  session. Note the default is 'lightdm-session' so you should chain to  this if you need to override this setting. 

**greeter-wrapper** is a the command to run a greeter. It is the equivalent of **session-wrapper** for greeters.
Pick one that You like, from ones that are run with root priviledges.
(from [https://wiki.ubuntu.com/LightDM#Configuration_and_Tweaks](https://wiki.ubuntu.com/LightDM#Configuration_and_Tweaks) )
Caveat: As far as I remember there is restriction that only one ntpd could be run so, I do fear, You will have to cope with that and that is what I suspect is preventing Your script from runnng successfully, You only do not see errors that are produced. I'd like to be mistaken here as I had a similar game played on one machine not so long ago.

---

### Post by Bashing-om on 2014-10-01
@zika; 

^^ In any event that is good to know ! 

[INDENT][INDENT]Thanks for the sharing
[/INDENT][/INDENT]

---

### Post by Cavsfan on 2014-10-01
> **zika said:**
> This is not a remedy but just an answer to Your question how to execute a command with root priviledges automatically.
1. /etc/rc.local
2. /usr/share/lightdm/lightdm.conf.d/

> If you need some special behaviour when X servers and  user sessions  start/stop you can set commands to be run with the  following  configuration: 

[SeatDefaults]
display-setup-script=command
display-stopped-script=command (Not in Ubuntu 12.04 LTS)
greeter-setup-script=command
session-setup-script=command
session-cleanup-script=command
session-wrapper=command
greeter-wrapper=command (Not in Ubuntu 12.04 LTS)**display-setup-script**   is run after the X server starts but before the user session / greeter   is run. Set this if you need to configure anything special in the X   server. It is run as root. If this command returns an error code the X   server is stopped. 
**display-stopped-script** is run after an X server exits. It is run as root. 
**greeter-setup-script**  is run before a greeter starts. It is run  as root. If this command  returns an error code the greeter fails to  start (which will cause  LightDM to stop). 
**session-setup-script**  is run before a user session starts. If  this command returns an error  the session will not start (user is  returned to a greeter). 
**session-cleanup-script** is run after a greeter or user session stops. It is run as root. 
**session-wrapper**  is a the command to run for a session. This  command is run as the user  and needs to exec the command passed in the  arguments to complete  running the session. Use this if you need to do  special setup for a user  session. Note the default is 'lightdm-session'  so you should chain to  this if you need to override this setting. 

**greeter-wrapper** is a the command to run a greeter. It is the equivalent of **session-wrapper** for greeters.

Pick one that You like, from ones that are run with root priviledges.
(from [https://wiki.ubuntu.com/LightDM#Configuration_and_Tweaks](https://wiki.ubuntu.com/LightDM#Configuration_and_Tweaks) )
Caveat: As far as I remember there is restriction that only one ntpd could be run so, I do fear, You will have to cope with that and that is what I suspect is preventing Your script from runnng successfully, You only do not see errors that are produced. I'd like to be mistaken here as I had a similar game played on one machine not so long ago.

Thanks for providing that information; it will be a good reference for running scripts with root privileges. Also thanks for sharing your immense knowledge about this stuff.
I just hope this problem goes away on it's own. If not I will do some more playing. It's strange that it just started happening on this one install; all of the other 5 have the correct time.
Thanks again zika! :)

---

### Post by zika on 2014-10-02
> **Cavsfan said:**
> It's strange that it just started happening on this one install; all of the other 5 have the correct time.Not uncommon thing. That happens a lot on dual boot due to UTC & etc.

---

### Post by sgage on 2014-10-02
I believe this is a bug in Utopic. The time is stored back to the BIOS at shutdown/reboot, and Utopic seems to be storing it as UTC, even though I have UTC=no. 

When I then boot into Windows, the clock is 4 hours fast (I'm in EDT), because Windows thinks the time stored in BIOS is local, and so does not subtract the 4 hours for my timezone. I set it to the correct time, reboot to Ubuntu, and the time is correct, because Ubuntu takes the BIOS time to be local time. It is at shutdown that Utopic stores the time back to BIOS as UTC, no matter what the UTC=(yes/no) setting is.

[Edit: Now I'm not so sure. If the scenario I outlined above was true (Utopic reads in as local, then writes out as UTC), then if you simply rebooted Ubuntu, the time would appear 4 hours fast on the clock. Which it does not. I'm not sure what-all is going on.]

---

### Post by Cavsfan on 2014-10-02
> **zika said:**
> Not uncommon thing. That happens a lot on dual boot due to UTC & etc.

It's odd that it's never happened to me before Utopic and that just started a week or two ago. I think I posted somewhere where the time and date settings were set to get the time from the internet.
The time was correct at that time but has since gone awry and it now set to get time manually (see below).

> **sgage said:**
> I believe this is a bug in Utopic. The time is stored back to the BIOS at shutdown/reboot, and Utopic seems to be storing it as UTC, even though I have UTC=no. 

When I then boot into Windows, the clock is 4 hours fast (I'm in EDT), because Windows thinks the time stored in BIOS is local, and so does not subtract the 4 hours for my timezone. I set it to the correct time, reboot to Ubuntu, and the time is correct, because Ubuntu takes the BIOS time to be local time. It is at shutdown that Utopic stores the time back to BIOS as UTC, no matter what the UTC=(yes/no) setting is.

[Edit: Now I'm not so sure. If the scenario I outlined above was true (Utopic reads in as local, then writes out as UTC), then if you simply rebooted Ubuntu, the time would appear 4 hours fast on the clock. Which it does not. I'm not sure what-all is going on.]

Well, it's nice to know it's not just me. I'm thinking it is just Utopic.  I am wondering how I can get this set to get the time from the internet like Trusty is set to do. Windows time has been correct for a while now.

[ATTACH=CONFIG]256903[/ATTACH]

---

### Post by P-I H on 2014-10-02
I saw this problem today.
On Utopic the time is +2 hours and "Automatically from the Internet" is grayed out.

I also saw that ntp was upgraded today to version "ntp (1:4.2.6.p5+dfsg-3ubuntu2)".

However, Ubuntu 14.04 has the correct time and it is possible to select "Automatically from the from the Internet"

---

### Post by zika on 2014-10-02
Got a spare couple of minutes to dwelve on this subject (because I do have couple of machines that show similar irregularities) and here is some insight:
```
$ cat /etc/default/ntpdate 
# The settings in this file are used by the program ntpdate-debian, but not
# by the upstream program ntpdate.

# Set to "yes" to take the server list from /etc/ntp.conf, from package ntp,
# so you only have to keep it in one place.
NTPDATE_USE_NTP_CONF=yes

# List of NTP servers to use  (Separate multiple servers with spaces.)
# Not used if NTPDATE_USE_NTP_CONF is yes.
NTPSERVERS="ntp.ubuntu.com"

# Additional options to pass to ntpdate
NTPOPTIONS=""
```
Did You try to change```
NTPDATE_USE_NTP_CONF
```to &#8222;no&#8220; in case You do not have (as default) ntp installed? Yes, there **are** two ntpdate and I'm not sure if some residue from Debian leaked so...
Just to make this post kind of complete:```
sudo hwclock -s
```should not be forgotten.

---

### Post by Bashing-om on 2014-10-02
@ zika, But, but but 

> 
# The settings in this file are used by the program ntpdate-debian, but not
# by the upstream program ntpdate.


Release 14.04 core:
```

sysop@1404mini:~$ dpkg -l ntpdate
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  ntpdate        1:4.2.6.p5+d amd64        client for setting system time fr
sysop@1404mini:~$

```
Do we not need to be following a different trail ?

[INDENT][INDENT]in that process of learning
[/INDENT][/INDENT]

---

### Post by zika on 2014-10-02
> **Bashing-om said:**
> @ zika, But, but but 



Release 14.04 core:
```

sysop@1404mini:~$ dpkg -l ntpdate
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  ntpdate        1:4.2.6.p5+d amd64        client for setting system time fr
sysop@1404mini:~$

```
Do we not need to be following a different trail ?[INDENT][INDENT]in that process of learning
[/INDENT]
[/INDENT]
...
> **zika said:**
> Yes, there **are** two ntpdate and I'm not sure if some residue from Debian leaked so...
```
$ dpkg -l|grep ntpdate
ii  ntpdate                                               1:4.2.6.p5+dfsg-3ubuntu2                            amd64        client for setting system time from NTP servers
$ whereis ntpdate-debian
ntpdate-debian: /usr/sbin/ntpdate-debian /usr/share/man/man8/ntpdate-debian.8.gz
$ ls -alt /usr/sbin/ntpdate*
-rwxr-xr-x 1 root root 102736 &#1086;&#1082;&#1090;  9  2013 /usr/sbin/ntpdate
-rwxr-xr-x 1 root root    593 &#1086;&#1082;&#1090;  9  2013 /usr/sbin/ntpdate-debian
```(not having Utopic machine in this room and no time to go to the other ;) but even this Trusty has the version You mention)

Update&#8321;: With that change I was able to complete successfully either of```
ntpdate ntp.ubuntu.com &
ntpdate-debian ntp.ubuntu.com &
```with```
hwclock -s
```on some of machines that refused to adjust time lately (just now (remotely)). I'm satisfied, for now.
Disclaimer: These machines are not dual-boot, those I'll tackle not sooner than tomorrow. I need to be by their keyboard to do that, reboot is needed.

---

### Post by Bashing-om on 2014-10-02
> **zika said:**
> ...

```
$ dpkg -l|grep ntpdate
ii  ntpdate                                               1:4.2.6.p5+dfsg-3ubuntu2                            amd64        client for setting system time from NTP servers
$ whereis ntpdate-debian
ntpdate-debian: /usr/sbin/ntpdate-debian /usr/share/man/man8/ntpdate-debian.8.gz
$ ls -alt /usr/sbin/ntpdate*
-rwxr-xr-x 1 root root 102736 &#1086;&#1082;&#1090;  9  2013 /usr/sbin/ntpdate
-rwxr-xr-x 1 root root    593 &#1086;&#1082;&#1090;  9  2013 /usr/sbin/ntpdate-debian
```(not having Utopic machine in this room and no time to go to the other ;) but even this Trusty has the version You mention)

Update&#8321;: With that change I was able to complete successfully either of```
ntpdate ntp.ubuntu.com &
ntpdate-debian ntp.ubuntu.com &
```with```
hwclock -s
```on some of machines that refused to adjust time lately (just now (remotely)). I'm satisfied, for now.


Not to throw another log on this fire: But just to "consider";
```

sysop@1404mini:~$ dpkg -l ntpdate-debian
dpkg-query: no packages found matching ntpdate-debian

sysop@1404mini:~$ whereis ntpdate-debian
ntpdate-debian: /usr/sbin/ntpdate-debian /usr/share/man/man8/ntpdate-debian.8.gz
sysop@1404mini:~$

```
So, 'ntpdate-debian' is available on the system but not installed.

Allowing us to have that option ?

EDIT: UUHH, I failed to follow through !
```

sysop@1404mini:~$ ls -alt /usr/sbin/ntpdate*
-rwxr-xr-x 1 root root 102736 Oct  9  2013 /usr/sbin/ntpdate
-rwxr-xr-x 1 root root    593 Oct  9  2013 /usr/sbin/ntpdate-debian
sysop@1404mini:~$ 

```
And now I am in a state of confusion, as 'dpkg' says 'ntpdate-debian'  is not installed. 'dpkg' being a pillar of my faith.

[INDENT][INDENT]the - who what where and why 
[/INDENT][/INDENT]

---

### Post by Cavsfan on 2014-10-02
> **P-I H said:**
> I saw this problem today.
On Utopic the time is +2 hours and "Automatically from the Internet" is grayed out.

I also saw that ntp was upgraded today to version "ntp (1:4.2.6.p5+dfsg-3ubuntu2)".

However, Ubuntu 14.04 has the correct time and it is possible to select "Automatically from the from the Internet"

Exact same thing here. Except mine's 4 hours off but once I fixed it this morning with **sudo ntpdate ntp.ubuntu.com** It stayed correct throughout 4-5 reboots.
It has to be on Utopic only and even Utopic Mate Remix does not have the same problem.

Just for giggles I looked in my bios and didn't find anywhere where you can select get time from internet. Windows has bee correct for the past couple of days and it is set to get the time from the internet.
The problem was there are 5 servers and the one selected didn't always work. I had to find one that worked.

This is probably just something that will work itself out like many other things we've seen in developmental versions.

Edit: sorry I didn't see the additional posts. I'll check back when I can.

---

### Post by Cavsfan on 2014-10-03
Ok after a gruelling morning.... I booted into Utopic and the time is still off by about 4 hours. 
I had to enter **sudo service ntp stop** and then **sudo ntpdate ntp.ubuntu.com** and then the clock is correct.
I cannot for the life of me get the option to set time from the internet selectable as it is greyed out like P-I H also noticed.

It's good to see I am not the only one with this problem and it is limited to Utopic Unicorn, Utopic Mate and the other OSs including windows 7 are good and have the correct time.

I'm going to see it this works I found on the wiki page for Ubuntu time:
[LIST]
[*]**gksudo leafpad /etc/cron.daily/ntpdate ** 
[/LIST]
I got tired of the error messages coming out of gedit. ):P

Added this to that file and saved it: 
```
#!/bin/sh
ntpdate ntp.ubuntu.com
```

[LIST]
[*]**sudo chmod 755 /etc/cron.daily/ntpdate** to make it executable. 
[/LIST]

Now I just have to wait until tomorrow to see if that works.

I got it from this which was just updated on May 14, 2014 [https://help.ubuntu.com/community/UbuntuTime](https://help.ubuntu.com/community/UbuntuTime)

I just opened a bug about this problem since I believe it is important [https://bugs.launchpad.net/ubuntu/+source/tzdata/+bug/1377258](https://bugs.launchpad.net/ubuntu/+source/tzdata/+bug/1377258)

---

### Post by Cavsfan on 2014-10-03
Annnnnnnd no sooner did I post that with the bug etc. I checked for updates and tzdata was in there. There was not much info in the changelog.

Let me know if if that fixes this problem for anyone else's time that is currently messed up. I don't think we'll be able to tell until tomorrow.

---

### Post by Cavsfan on 2014-10-04
Booted up and the time was 4 hours behind. After a little while I looked at the time and it was correct. Maybe it was that daily cron script that fixed it.
I guess that will suffice for a workaround until it's fixed.

---

### Post by Cavsfan on 2014-10-05
[QUOTE=Cavsfan]
Is no one else with this problem going to add themselves to this bug? [https://bugs.launchpad.net/ubuntu/+source/tzdata/+bug/1377258](https://bugs.launchpad.net/ubuntu/+source/tzdata/+bug/1377258)[/QUOTE]

It shows I'm the only one affected when there has to be more. I added that workaround which seems to work.

---

### Post by sgage on 2014-10-05
> **Cavsfan said:**
> It shows I'm the only one affected when there has to be more. I added that workaround which seems to work.

I didn't add myself to this bug report because I have a somewhat different issue from what others seem to be reporting. I dual-boot between Ubuntu Gnome and Windows. Whenever I boot into Windows, it is 4 hours fast. I reset the time in Windows. When I boot into UG, the time is correct.

Windows clearly expects the BIOS time that it picks up at boot to be local, and so does not subtract the 4 hours for EDT, making the clock 4 hrs. fast. When it shuts down, it stores the time back to the HW clock as local time, and if I boot right back into Windows, the time is correct.

It would appear that UG expects the BIOS time to be local as well, because when I boot to it after shutting down Windows, it shows the correct time. Aha! you say. It must be that UG sets the BIOS to UTC at shutdown! Except, if I simply reboot from UG to UG, the time is correct, and you'd expect it to be 4 hours fast in that case.

I can reboot from Windows to Windows, or UG to UG, or from Windows to UG, with no messing up of the time. Only going from UG to Windows does the time go 4 hours ahead.

If that weren't enough, if I reboot from UG to Windows, resulting in Windows showing the time 4 hours fast, then reboot to UG, UG shows the correct time!

Are there two different places where time is saved across boots? Even so, the facts on the ground still don't seem to make sense to me. No doubt I have an erroneous concept of what happens with time across boots...

---

### Post by mc4man on 2014-10-05
slightly different here also but 14.10 is somehow at fault (usa, eastern
boot to 14.10 > time correct
after that - 
boot to windows > off 4 hrs 
boot to 14.04 > greeter off 4 hrs., after login auto corrected to proper time

boot to 14.04 > time correct
after that - 
boot to windows > time correct

So 14.10 is doing something wrong...

---

### Post by sgage on 2014-10-05
[Addendum to #30]

Windows clearly sets the BIOS time to local time at shutdown.

UG clearly sets the BIOS time to UTC at shutdown.

Even though UTC=no is set.

Whether the BIOS time is set to local or UTC, UG shows the correct time at boot!

The only explanation that I can think of is that it gets the correct time over the Internet before it ever shows a clock. I will try setting a very off time and rebooting...

HAH! Correct time showing. It doesn't matter what's in the BIOS - the automatic time sync fixes it before a clock is ever displayed.

The bug is that even with UTC=no, Ubuntu stores time as UTC, but expects it as local. If I turn off automatic time sync, I'll bet I'll be 4 hours fast upon a reboot...

Yes. I had totally forgotten about the automatic time sync. I was beginning to think I'd lost it there.

I've added myself to your bug and left a post.

---

### Post by Cavsfan on 2014-10-05
My windows used to be off 4 hours only when I booted into it in the evening but for the past week or two has not once been wrong.
I initially just thought it was jealous because it wasn't getting as much love. :p

Since I added that daily cron script mentioned a few posts back when I boot into Utopic the time is off by -4 hours and after so many minutes corrects itself.

The problem is certainly in Utopic as none of the other 5 Linux system's time or even windows is ever off on this box.
But I don't have a clue beyond that.

---

### Post by Cavsfan on 2014-10-05
My windows used to be off 4 hours only when I booted into it in the evening but for the past week or two has not once been wrong.
I initially just thought it was jealous because it wasn't getting as much love. :p

Since I added that daily cron script mentioned a few posts back when I boot into Utopic the time is off by -4 hours and after so many minutes corrects itself.

The problem is certainly in Utopic as none of the other 5 Linux system's time or even windows is ever off on this box.
But I don't have a clue beyond that.

---

### Post by sgage on 2014-10-05
My workaround is to set UTC=yes (for when they fix the bug), and set Windows to use UTC with the HW clock using this registry key:

```
Windows Registry Editor Version 5.00
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\TimeZoneInformation]"RealTimeIsUniversal"=dword:00000001
```

Everything is fine now in both directions. I can't believe how long it took me to realize that the auto-time-sync was obfuscating my troubleshooting efforts. Oh well!  :KS

---

### Post by mc4man on 2014-10-05
Not too sure that tzdata is proper package to file against. Maybe sysvinit & or whatever 14.10 is using if /etc/default/rcS is ignored ... (systemd ?

---

### Post by sgage on 2014-10-05
> **mc4man said:**
> Not too sure that tzdata is proper package to file against. Maybe sysvinit & or whatever 14.10 is using if /etc/default/rcS is ignored ... (systemd ?

Good point. rcS is ignored on the shutdown, but not on boot. Not sure what package to 'blame'.

---

### Post by mc4man on 2014-10-05
> **sgage said:**
> Good point. rcS is ignored on the shutdown, but not on boot. Not sure what package to 'blame'.

What i've never figured out in launchpad is how to add 'whatever (Ubuntu)'  to a bug report (vs. adding 'whatever' which is easy
(- many times 'whatever' won't notify anyone where 'whatever (Ubuntu)' will

So started here even though the 2 reports are really the same issue  (not trying to step on Cavsfan.., just curious about a dev response, if any...
[https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/1377698](https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/1377698)

---

### Post by Cavsfan on 2014-10-06
Thanks          mc4man, you know more about what your doing than I do. I marked it as affecting me too.

I booted into Utopic and didn't get a chance to see the wrong time. I looked at it a few minutes later and I take it that cron script fixed it as it has been.

I didn't know that UTC=y would fix it because I thought I tried it and rebooted and it didn't work.

My windows 7 is consistently maintaining the right time now. Not sure what fixed that - just chock it up to microsoft I guess.

Off this topic for a sec: [start of off topic] mc4man did you ever get a chance to look into why my Trusty has no restart option in gnome flashback with compiz? 
I hate to just do a clean install because it's just sitting on a separate partition.
But, what does bother me is when I upgrade my Precise to Utopic in 2017. I upgraded Precise from Lucid at drs305's suggestion. I used to do clean installs but upgrading is better if it works.
[/back on topic] :)

---

### Post by Cavsfan on 2014-10-09
Now Utopic Mate is affected by this 4 hour behind ET problem. I put that cron script in place. It should do it's thing.

---

### Post by sgage on 2014-10-09
I haven't been paying proper attention to the masses of updates, but the problem seems to have been fixed as of late yesterday.

---

### Post by Cavsfan on 2014-10-09
> **sgage said:**
> I haven't been paying proper attention to the masses of updates, but the problem seems to have been fixed as of late yesterday.

My Utopic Mate install went awry yesterday or maybe the day before for the very first time and was off today. Also when I logged on to regular Utopic today the time was off. 
I did get a lot of updates and maybe it is fixed. I'll have to wait until tomorrow to see.
Thanks for the update.

---

### Post by mc4man on 2014-10-09
it was fixed in util-linux package - 

> This bug was fixed in the package util-linux - 2.25.1-3ubuntu2

---------------
util-linux (2.25.1-3ubuntu2) utopic; urgency=medium

  * Add debian/util-linux.hwclock.sh.upstart: Mask /etc/init.d/hwclock.sh, as
    we don't want to run this under upstart (we already have hwclock.conf for
    that). (LP: #1377698)
  * debian/util-linux.postinst: Remove /etc/adjtime again on upgrades to this
    version, we don't want it in Ubuntu. This can be removed after utopic, it
    only affects intra-utopic upgrades.
 -- Martin Pitt <martin.pitt@ubuntu.com> Tue, 07 Oct 2014 15:10:44 +0200


---

### Post by Cavsfan on 2014-10-10
Why then would I still have the problem?
I just booted into Utopic at 11:34AM CT while the system displayed 7:34AM (4 hours behind). I got an update to tzdata and when it installed it displayed this:
 ```
Current default time zone: 'America/New_York'
Local time is now:      Fri Oct 10 07:38:06 EDT 2014.
Universal Time is now:  Fri Oct 10 11:38:06 UTC 2014.
Run 'dpkg-reconfigure tzdata' if you wish to change it.

```

> util-linux (2.25.1-3ubuntu2) utopic; urgency=medium

  * Add debian/util-linux.hwclock.sh.upstart: Mask /etc/init.d/hwclock.sh, as
    we don't want to run this under [COLOR=#ff0000]upstart[/COLOR] (we already have hwclock.conf for
    that). (LP: #1377698)
  * debian/util-linux.postinst: Remove /etc/adjtime again on upgrades to this
    version, we don't want it in Ubuntu. This can be removed after utopic, it
    only affects intra-utopic upgrades.

 -- Martin Pitt <martin.pitt@ubuntu.com>  Tue, 07 Oct 2014 15:10:44 +0200

Could it be that is because I booted using systemd instead of upstart?

---

### Post by Cavsfan on 2014-10-10
I booted into Utopic Mate with systemd and it had the correct time. 
Maybe tomorrow regular Utopic will have the correct date.

I'm taking out that cron script I put in.

---

### Post by Cavsfan on 2014-10-11
I'm good now. The time is correct.

---

### Post by Cavsfan on 2014-10-13
Well I booted into Utopic and the time was 4 hours behind again. :rolleyes:
The ability to change get time from the internet is still greyed out.

Edit: this is the only way I could get the time right.
```
cavsfan@cavsfan-MS-7529:~$ sudo ntpdate ntp.ubuntu.com
13 Oct 16:38:28 ntpdate[19119]: step time server 91.189.94.4 offset 14399.735112 sec
```

---

### Post by Cavsfan on 2014-10-14
Am I the only one experiencing this?

Today I booted into Utopic via systemd and the time said 8:15am when it should have said 12:15pm.
Not sure how long it takes for that cron script to kick in but it did after several minutes. It definitely doesn't occur at bootup.

I got a lot of updates to gnome-flashback some nice menu corrections. So I figured I'd reboot and what do I see --- the thing is back to 8am again. 

I'm pretty sure that daily cron script will only run once or that is what the daily means I think. :p

So I guess it's **sudo ntpdate ntp.ubuntu.com** time again.

---

### Post by Cavsfan on 2014-10-14
The above problem was a first: the time was four hours behind on 2 consecutive boots even after it was fixed the first time.

I am in Utopic Mate Remix now and it has affected it as well - 4 hours behind.

---

### Post by Cavsfan on 2014-10-15
Same thing again today. What's up with the regression?

---

### Post by Cavsfan on 2014-10-16
Same thing again today. So it's just me?

---

### Post by mc4man on 2014-10-16
> **Cavsfan said:**
> Same thing again today. So it's just me?

Before I got rid of 14.10 it was fine. I guess if you're not using a default install then anything is possible

---

### Post by Cavsfan on 2014-10-16
> **mc4man said:**
> Before I got rid of 14.10 it was fine. I guess if you're not using a default install then anything is possible

I think I'm using the default install. This install was Trusty until final release and when the Utopic repositories became available I just changed the source names.

```
sudo sed -i 's/trusty/utopic/g' /etc/apt/sources.list 
```

But, I think I just found the culprit. I was booting with systemd and after getting some major updates to grub, etc. I booted into Utopic with Upstart and the time was correct.
I looked at the time and date settings and setting the time automatically from the internet is not greyed out and it is selected.

When I boot with systemd it is set to manual and setting the time automatically from the internet *is* greyed out and the time is wrong.
Should I worry about that? File a bug report on systemd or anything? I'm pretty sure it is repeatable.

---

### Post by Elfy on 2014-10-16
report it - systemd-boot tag it

---

### Post by mc4man on 2014-10-16
> I think I'm using the default install..
When I boot with systemd ..
Well I wouldn't call that a default install.
You could file a bug or wait until Ubuntu switches totally over which doesn't seem to be the case for 14.10 (if there is an issue then

---

### Post by Elfy on 2014-10-16
> **mc4man said:**
> Well I wouldn't call that a default install.
You could file a bug or wait until Ubuntu switches totally over which doesn't seem to be the case for 14.10 (if there is an issue then

There were specific requests from Martin Pitt for people to test with systemd if they could and/or wanted to and to report bugs with the systemd-boot tag, it might not be default but ...

---

### Post by Cavsfan on 2014-10-16
I'll do that. Glad I finally figured out that it was systemd and upstart works just fine. That's was driving me nuts!
I was in upstart and all was well. I read your posts and booted up with systemd and it was back 4 hours in time and update time via internet is greyed out.
So it's definitely repeatable. It will happen every time you boot with systemd.
I'll report it against util-linux since that is what mc4man reported the "good bug" against since tzdata isn't the right package.

Thanks! Lemme see...

---

### Post by Cavsfan on 2014-10-16
I'm not real good at this yet but here it is: [https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/1382208](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/1382208)

Could someone look at it and make sure it is correct?

Not sure why it says: "CurrentDesktop: Unity" when I am in Gnome Flashback (with compiz) or is that just the way it works?

Thanks

---

### Post by mc4man on 2014-10-16
That looks ok,  maybe could be on systemd?

---

### Post by Cavsfan on 2014-10-17
> **mc4man said:**
> That looks ok,  maybe could be on systemd?

It's tagged with systemd-boot. That is what they wanted for systemd bugs.

---

