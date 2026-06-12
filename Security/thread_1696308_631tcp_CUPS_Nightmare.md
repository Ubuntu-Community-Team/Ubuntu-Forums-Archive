---
title: "631/tcp CUPS Nightmare"
date: 2011-02-27
forum: Security
---

### Post by zzzorrander on 2011-02-27
Running: Ubuntu 10.10  

Hi everyone and thanks for the help. I'm in a bind and I don't know how to get what I want. Nmap shows ipp running cups on port 631. Great, simple enough I uninstall cups, along with its dependencies. A new portscan reveals that the port is closed SUCCESS, but... Ubuntu Update Manager nags me @ every restart about the "important security" updates. I can't lock the version of cups in Synaptic, because cups is not installed! So you see I'm in a bind. If I have cups installed I have an open port, and if I uninstall cups the update manager nags me. What do I do?  I've tried:


[LIST]
[*] - stopping the cups service and issuing the chkconfig cups off command...   (doesn't close the port)
[*]- uninstalling cups... (update manager nags)
[*] - fuser -k 631/tcp (great,  but @ reboot the port is still open)
[/LIST]
 Please teach me how to close this  port / stop this service / tell update manager to shove cups.....

---

### Post by coffee412 on 2011-02-27
> **zzzorrander said:**
> Running: Ubuntu 10.10  

Hi everyone and thanks for the help. I'm in a bind and I don't know how to get what I want. Nmap shows ipp running cups on port 631. Great, simple enough I uninstall cups, along with its dependencies. A new portscan reveals that the port is closed SUCCESS, but... Ubuntu Update Manager nags me @ every restart about the "important security" updates. I can't lock the version of cups in Synaptic, because cups is not installed! So you see I'm in a bind. If I have cups installed I have an open port, and if I uninstall cups the update manager nags me. What do I do?  I've tried:


[LIST]
[*] - stopping the cups service and issuing the chkconfig cups off command...   (doesn't close the port)
[*]- uninstalling cups... (update manager nags)
[*] - fuser -k 631/tcp (great,  but @ reboot the port is still open)
[/LIST]
 Please teach me how to close this  port / stop this service / tell update manager to shove cups.....


Two commands will stop cups and cause it to not start on reboot.

sudo service cups stop
sudo chkconfig cups off

Leave cups installed. If the above commands do not work then you have other problems most likely. Post the output of the two commands if they dont work or look at your /var/log/messages log file for any other info.

coffee

---

### Post by zzzorrander on 2011-02-27
Hi Coffee,

I took your advice and reinstalled cups with it's dependencies. As expected tcp port 631 opened up. I ran the two commands and did another portscan. Port 631 was closed. However... upon restarting the computer and doing another portscan the cups service port 631 was still open, and cups service was still running. Nothing was written to /var/log/messages during the inputting of those commands... I'll try this process again, do a reboot and fish through the logs to see if I can find anything interesting, although I've never looked in that log before.....

---

### Post by zzzorrander on 2011-02-27
Coffee,

I don't know if this is helpful... I looked through the logs from when I shutdown to when I reboot, and this is what I think is relevant...?

type=1400 audit(1298824482.920:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=971 comm="apparmor_parser"
type=1400 audit(1298824482.920:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=971 comm="apparmor_parser"


I have no idea...

---

### Post by zzzorrander on 2011-02-27
It just struck me that my attempts to uninstall cups-like packages may be the cause of those commands not working...

I opened up a program called Boot Up Manager and noticed that cups was unchecked... I checked it, tried the commands again, and this error came out:

```
sudo chkconfig cups off
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'K20cups' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'K20acpi-support' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'cups' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'irqbalance' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `irqbalance'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `irqbalance'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'network-manager' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `network-manager'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `network-manager'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'rsyslog' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `rsyslog'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `rsyslog'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'acpid' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `acpid'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `acpid'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'network-interface' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `network-interface'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `network-interface'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'ecryptfs-utils-save' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `ecryptfs-utils-save'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `ecryptfs-utils-save'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'anacron' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `anacron'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `anacron'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'ecryptfs-utils-restore' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `ecryptfs-utils-restore'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `ecryptfs-utils-restore'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'udevmonitor' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udevmonitor'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udevmonitor'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'cron' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cron'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cron'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'gdm' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `gdm'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `gdm'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'procps' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `procps'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `procps'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'plymouth-log' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `plymouth-log'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `plymouth-log'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'hostname' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `hostname'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `hostname'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'dmesg' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `dmesg'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `dmesg'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'cryptdisks-udev' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cryptdisks-udev'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cryptdisks-udev'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'udev-finish' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udev-finish'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udev-finish'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'atd' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `atd'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `atd'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'console-setup' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `console-setup'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `console-setup'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'hwclock' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `hwclock'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `hwclock'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'plymouth-stop' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `plymouth-stop'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `plymouth-stop'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'screen-cleanup' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `screen-cleanup'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `screen-cleanup'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'network-interface-security' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `network-interface-security'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `network-interface-security'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'cryptdisks-enable' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cryptdisks-enable'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cryptdisks-enable'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'plymouth-splash' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `plymouth-splash'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `plymouth-splash'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'udev' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udev'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udev'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'module-init-tools' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `module-init-tools'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `module-init-tools'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'failsafe-x' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `failsafe-x'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `failsafe-x'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'dbus' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `dbus'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `dbus'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'plymouth' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `plymouth'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `plymouth'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'apport' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `apport'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `apport'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'ufw' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `ufw'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `ufw'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'hwclock-save' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `hwclock-save'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `hwclock-save'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'alsa-mixer-save' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `alsa-mixer-save'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `alsa-mixer-save'
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'udevtrigger' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `udevtrigger'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `udevtrigger'
insserv: warning: script 'acpi-support' missing LSB tags and overrides
```

I'm looking through all of the packages that I uninstalled. I'll reinstall them, and try again.....

---

### Post by brian_p on 2011-02-27
> **zzzorrander said:**
> 

 Please teach me how to close this  port / stop this service / tell update manager to shove cups.....

If you are willing to be taught, grasshopper, you will learn.

Why are you bothered about an open port? Open ports are good. Port 631 being open means you can print.

But, by default, port 631 is accessible only from the machine you are sitting at and the only printer which can be used is one attached to that machine. Nobody else can get to it.

So stop being afraid of open ports. Understand what they are for how they are configured by default.

---

### Post by zzzorrander on 2011-02-27
Brian,

Point well taken, and I enjoyed the grasshopper part very much. :)

I'm currently spending every day learning everything that I can about Unix/Linux/Firewalls/Hacking/Etc. I want to close port 631 because although I have 3 printers in my room (lol) I'm not going to use any of them. Why have an open port if you're not going to use it. Plus, open ports do give me the creeps as I'm slowly getting up to speed on (in)security. When I watch videos on people opening up a netcat listener on port XX and shovelling what ever onto a compromised system, and I look at my nmap or netstat output and see

127.0.0.1::::* LISTENING...

or 

631/tcp Open Unknown

I do want to close it asap.

Yeah, what else can I say. I've briefly read about IPP/cups only being available on the loopback, but as I just got 2/3 of the way through my first book on TCP/IP I still don't trust anything.

Now I'm channeling my paranoia into reading an OpenBSD book. I can't wait to install it and read, break my system, cry from a lack of help, and fight harder to get all this stuff.

Thanks for the insight! I'll dig deeper into cups and figure out why I shouldn't crawl under my bed about it's open port 631.
'
Cheers!

---

### Post by cariboo on 2011-02-27
Cups only listens on 127.0.0.1, if you run nmap from another system on your network, you'll see that it's closed to the outside world.

---

### Post by zzzorrander on 2011-02-27
Thank you all for your feedback. I'll drop the neurosis and portscan my box from another computer to confirm this. Again, thanks!

---

### Post by francoise_peace on 2012-02-02
> **brian_p said:**
> If you are willing to be taught, grasshopper, you will learn.

Why are you bothered about an open port? Open ports are good. Port 631 being open means you can print.

But, by default, port 631 is accessible only from the machine you are sitting at and the only printer which can be used is one attached to that machine. Nobody else can get to it.

So stop being afraid of open ports. Understand what they are for how they are configured by default.

Thank you ! I have just deleted the port 631/tcp from FIREWALL because Facebook disconnected me alone wich gave me suspicions. So this was my printer !!! So just I'll just add again ALLOW IN TCP 631 inside my FIREWALL.

---

### Post by CharlesA on 2012-02-02
> **francoise_peace said:**
> Thank you ! I have just deleted the port 631/tcp from FIREWALL because Facebook disconnected me alone wich gave me suspicions. So this was my printer !!! So just I'll just add again ALLOW IN TCP 631 inside my FIREWALL.
That port has nothing to do with facebook.

It is only listening on the loopback address (127.0.0.1 or ::1), and as such it cannot accept connections from outside your local machine.

There is no need to firewall it.

---

### Post by Dangertux on 2012-02-02
Well my advice here is to walk before you run. You're worried about open ports but don't even understand how they work , or how a service or application is even exploited. 

Just because you have an open port does not mean there is a vulnerable or even an accessible service running on it.  

Hope this helps.

---

