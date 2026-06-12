---
title: "[ubuntu]Has my server been infected?"
date: 2014-04-05
forum: Security
---

### Post by jos7 on 2014-04-05
My server got listed on "The CBL" ([http://cbl.abuseat.org](http://cbl.abuseat.org)):
> This IP is infected (or NATting for a computer that is infected) with a spam-sending infection.  In other words, it's participating in a botnet. If you simply remove the listing without ensuring that the infection is removed (or the NAT secured), it will probably relist again.

 I ran both rkhunter and chkrootkit. Chkrootkit tells me my server is infected:
```
...
Searching for Romanian rootkit...                           nothing found
Searching for Suckit rootkit...                             Warning: /sbin/init INFECTED
Searching for Volc rootkit...                               nothing found
...
Checking `asp'...                                           not infected
Checking `bindshell'...                                     INFECTED (PORTS:  60001)
Checking `lkm'...                                           chkproc: nothing detected
...
```

while rkhunter says the server is not infected:
```
...
[14:28:57]   /usr/bin/whoami                                 [ OK ]
[14:28:57]   /usr/bin/unhide.rb                              [ Warning ]
[14:28:57] Warning: The command '/usr/bin/unhide.rb' has been replaced by a script: /usr/bin/unhide.rb: Ruby script, ASCII text
[14:28:58]   /usr/bin/gawk                                   [ OK ]
...
[14:32:38] Info: Starting test name 'filesystem'
[14:32:38] Performing filesystem checks
[14:32:38] Info: SCAN_MODE_DEV set to 'THOROUGH'
[14:32:38]   Checking /dev for suspicious file types         [ Warning ]
[14:32:38] Warning: Suspicious file types found in /dev:
[14:32:38]          /dev/.udev/rules.d/root.rules: ASCII text
[14:32:38]   Checking for hidden files and directories       [ Warning ]
[14:32:38] Warning: Hidden directory found: /dev/.udev
[14:32:38] Warning: Hidden file found: /dev/.initramfs: symbolic link to `/run/initramfs'
...
[14:30:08]
[14:30:08] Checking for Suckit Rootkit...
[14:30:08]   Checking for file '/sbin/initsk12'              [ Not found ]
[14:30:08]   Checking for file '/sbin/initxrk'               [ Not found ]
[14:30:08]   Checking for file '/usr/bin/null'               [ Not found ]
[14:30:09]   Checking for file '/usr/share/locale/sk/.sk12/sk' [ Not found ]
[14:30:09]   Checking for file '/etc/rc.d/rc0.d/S23kmdac'    [ Not found ]
[14:30:09]   Checking for file '/etc/rc.d/rc1.d/S23kmdac'    [ Not found ]
[14:30:09]   Checking for file '/etc/rc.d/rc2.d/S23kmdac'    [ Not found ]
[14:30:09]   Checking for file '/etc/rc.d/rc3.d/S23kmdac'    [ Not found ]
[14:30:09]   Checking for file '/etc/rc.d/rc4.d/S23kmdac'    [ Not found ]
[14:30:09]   Checking for file '/etc/rc.d/rc5.d/S23kmdac'    [ Not found ]
[14:30:09]   Checking for file '/etc/rc.d/rc6.d/S23kmdac'    [ Not found ]
[14:30:09]   Checking for directory '/dev/sdhu0/tehdrakg'    [ Not found ]
[14:30:09]   Checking for directory '/etc/.MG'               [ Not found ]
[14:30:09]   Checking for directory '/usr/share/locale/sk/.sk12' [ Not found ]
[14:30:09]   Checking for directory '/usr/lib/perl5/site_perl/i386-linux/auto/TimeDate/.packlist' [ Not found ]
[14:30:09] Suckit Rootkit                                    [ Not found ]
[14:30:09]
...
[14:31:55]   Performing Suckit Rookit additional checks
[14:31:55]     Checking hard link count on '/sbin/init'      [ OK ]
[14:31:55]     Checking for hidden file extensions           [ None found ]
[14:31:55]     Running skdet command                         [ Skipped ]
[14:31:55] Info: Unable to find the 'skdet' command
[14:31:55]   Suckit Rookit additional checks                 [ OK ]
...
```

I ran netstat, but there were no connections on port 25.

What do I do? Assume nothing is wrong? Surely there must be a reason for why the IP got blacklisted?

---

### Post by HermanAB on 2014-04-05
Use tcpdump to see whether there is anything untoward going on.  If you are connecting over SSH, exclude port 22 from the check.

---

### Post by bashiergui on 2014-04-05
If you want to quickly get back up and you don't really care how it happened then just reinstall the server and restore from backup. Then look at the stickies in this forum for ways to better secure the serer so it doesn't happen again.

If you want to figure out what happened, then look at your auth logs and sys logs for odd events and connections, and for chunks of missing time. Use wireshark or tcpdump on another computer on the same LAN to look for connections out to the internet. I'd watch it over several hours to see if it sleeps for a while.

---

### Post by Habitual on 2014-04-06
If you're listed at [http://cbl.abuseat.org/](http://cbl.abuseat.org/), the first thing to "do" is read their page on getting de-listed.

chkrootkit is **useless**, IMO...
What's **"[New]("http://chkrootkit.org/#new")**"?

chkrootkit 0.49 is now available! (Release Date: **[COLOR=#ff0000]Thu Jul 30 2009[/COLOR]**)
Re-installing will not help as CBLs usually block portions of netblocks for some networks. (dynamic IP assignment)

```
sudo lsof -i :60001
``` and see what's listed as listening on that port.

---

### Post by lisati on 2014-04-06
If you're looking at mail logs, pay particular attention to outgoing mail that was rejected around the time that the CBL people last detected a problem.

---

### Post by untrustytahr on 2014-04-06
> **Habitual said:**
> Tools every shell scripter should have, [explainshell]("http://explainshell.com/"), [shellcheck]("http://www.shellcheck.net/"), and [crontab sandbox]("http://www.dataphyx.com/cronsandbox/cronsandboxgui.php").

I'd be alot smarter today if these existed 30 years ago.  :lolflag:

---

### Post by Habitual on 2014-04-07
> **untrustytahr said:**
> I'd be alot smarter today if these existed 30 years ago.  :lolflag:
You and me both!

---

### Post by 23dornot23d on 2014-04-07
I get warnings on these - are they standard hidden files in Linux to have here ..... checked after running rootkit hunter
in the development version 14.04

```

[18:02:26] Info: Start date is Mon Apr  7 18:02:26 CEST 2014
[18:02:26]
[18:02:26] Checking configuration file and command-line options...
[18:02:26] Info: Detected operating system is 'Linux'
[18:02:26] Info: Found O/S name: Ubuntu Trusty Tahr (development branch)
[18:02:26] Info: Command line is /usr/bin/rkhunter -c

.
.
.

[18:04:20] Info: Starting test name 'filesystem'
[18:04:20] Performing filesystem checks
[18:04:20] Info: SCAN_MODE_DEV set to 'THOROUGH'
[18:04:20]   Checking /dev for suspicious file types         [ Warning ]
[18:04:20] Warning: Suspicious file types found in /dev:
[18:04:20]          /dev/.udev/rules.d/root.rules: ASCII text
[18:04:21]   Checking for hidden files and directories       [ Warning ]
[18:04:21] Warning: Hidden directory found: '/etc/.java: directory '
[18:04:21] Warning: Hidden directory found: '/dev/.udev: directory '
[18:04:21] Warning: Hidden file found: /dev/.blkid.tab: ASCII text
[18:04:21] Warning: Hidden file found: /dev/.blkid.tab.old: ASCII text
[18:04:21] Warning: Hidden file found: /dev/.initramfs: symbolic link to `/run/initramfs' 
[18:04:21] Warning: Hidden file found: /usr/bin/.vglrun.vars32: ASCII text



```

$ less /usr/bin/.vglrun.vars32

# Copyright (C)2013 D. R. Commander
#
# This library is free software and may be redistributed and/or modified under
# the terms of the wxWindows Library License, Version 3.1 or (at your option)
# any later version.  The full license is in the LICENSE.txt file included
# with this distribution.
#
# This library is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# wxWindows Library License for more details.

# If the faker libraries are packaged in a non-system directory, then this
# script adds that directory to VGL_LIBRARY_PATH, which is later added to
# LD_LIBRARY_PATH so that LD_PRELOAD can find the libraries.

VGL_LIBDIR=/usr/lib/i386-linux-gnu

if [ -d "$VGL_LIBDIR" -a -f "$VGL_LIBDIR/librrfaker.so" ] && \
        [ $__VGL_DL -eq 0 -o -f "$VGL_LIBDIR/libdlfaker.so" ] && \
        [ $__VGL_GE -eq 0 -o -f "$VGL_LIBDIR/libgefaker.so" ]; then
        if [ -z "$VGL_LIBRARY_PATH" ]; then
                VGL_LIBRARY_PATH=$VGL_LIBDIR
/usr/bin/.vglrun.vars32


$ less /dev/.blkid.tab
$ less /dev/.udev/rules.d/root.rules

---

### Post by jos7 on 2014-04-07
> **Habitual said:**
> If you're listed at [http://cbl.abuseat.org/](http://cbl.abuseat.org/), the first thing to "do" is read their page on getting de-listed.

chkrootkit is **useless**, IMO...
What's **"[New]("http://chkrootkit.org/#new")**"?

chkrootkit 0.49 is now available! (Release Date: **[COLOR=#ff0000]Thu Jul 30 2009[/COLOR]**)
Re-installing will not help as CBLs usually block portions of netblocks for some networks. (dynamic IP assignment)

```
sudo lsof -i :60001
``` and see what's listed as listening on that port.

Yeah. So I decided to install a fresh copy of Ubuntu server in a VM, and... /sbin/init is infected right after a clean install. It turns out port 60001 is opened by the software I run on the server, but you cannot connect to it from the outside. That means neither rkhunter nor chkrootkit actually detected anything.

I tried de-listing, but the IP got listed once again, which made me worry that the server might still be infected.

> **lisati said:**
> If you're looking at mail logs, pay  particular  attention to outgoing mail that was rejected around the time that the  CBL people last detected a problem.Curiously enough, there were  no mails rejected or sent when the CBL last detected a problem...

After looking at the mail logs and establishing when the IP got blacklisted, I realised I may have actually caused the listing myself. So I changed a few things back to how they were before, and I just de-listed the IP again...

---

### Post by bashiergui on 2014-04-07
> **jos7 said:**
> 
After looking at the mail logs and establishing when the IP got blacklisted, I realised I may have actually caused the listing myself. So I changed a few things back to how they were before, and I just de-listed the IP again...
What do you think you did to cause it yourself out of curiosity?

---

