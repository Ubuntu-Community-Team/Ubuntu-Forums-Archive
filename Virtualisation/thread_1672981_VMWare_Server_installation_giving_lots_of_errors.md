---
title: "VMWare Server installation giving lots of errors"
date: 2011-01-21
forum: Virtualisation
---

### Post by Wamiduku on 2011-01-21
I've followed the instructions at [https://help.ubuntu.com/community/VMware/Server](https://help.ubuntu.com/community/VMware/Server) to install VMWare Server 2.0.2 on Ubuntu Server 10.04 (64-bit). I get these error messages:

insserv: warning: script 'network-interface' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0 6) of script `networking' overwrites defaults (empty).
insserv: warning: current start runlevel(s) (0) of script `halt' overwrites defaults (empty).
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'hostname' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'plymouth-log' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'apport' missing LSB tags and overrides
insserv: script vmware-autostart: service VMware already provided!
insserv: script vmware-mgmt: service VMware already provided!
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'smbd' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'ufw' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'udev' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'network-interface-security' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0 6) of script `umountfs' overwrites defaults (empty).
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'udev-finish' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'module-init-tools' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0 6) of script `umountroot' overwrites defaults (empty).
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'plymouth-stop' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'udevmonitor' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'atd' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'rsyslog' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'udevtrigger' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'hwclock' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'plymouth-splash' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'console-setup' missing LSB tags and overrides
insserv: There is a loop between service rsyslog and winbind if stopped
insserv:  loop involving service winbind at depth 3
insserv:  loop involving service rsyslog at depth 2
insserv:  loop involving service udev at depth 1
insserv: There is a loop between service winbind and rsyslog if stopped
insserv: exiting now without changing boot order!

The VMWare Server web service (https://<server name>:8333) starts, but doesn't let me add any VMs. After a reboot, the web service doesn't even start anymore.

---

### Post by CharlesA on 2011-01-21
VMWare server is pretty much garbage. Use VMWare workstation or VMWare Player.

You could even use VirtualBox.

---

### Post by Wamiduku on 2011-01-21
> **CharlesA said:**
> VMWare server is pretty much garbage. Use VMWare workstation or VMWare Player.

You could even use VirtualBox.

VMWare Workstation/Player doesn't start VMs automatically after boot, and won't shut them down automatically before system shutdown either. 

I don't have a problem with VMWare Server on the Windows boxes I use where it, so it's not garbage to me.

---

### Post by CharlesA on 2011-01-21
I've gotten VMware server to work once, Take a look here:

[http://ubuntuforums.org/showthread.php?t=1581439](http://ubuntuforums.org/showthread.php?t=1581439)

---

### Post by Wamiduku on 2011-01-21
Ok, I checked out the thread and tried the procedure. Ran into some errors, trouble shot and got a bit further, but at this point I realize that I've spent more than 5 hours on something that takes 5 minutes in Windows, so it's time to quit trying and change to something that works.

I'm not blaming Linux here, but the combination of VMWare and Linux is just not worth the time and trouble, so I'm installing Windows on the VM host. Shame about the waste of memory though.

I'm sure Linux is great for VM hosts if you run Xen or something else with installation ready packages, but right now I need to be compatible with both VMWare Server and VMWare Workstation (frequently moving VMs between machines) and that limits my options.

---

### Post by CharlesA on 2011-01-21
Yep. That happens, I had a guy I know go thru hell trying to set up Nagious on a Linux box, only to find out after messing with it for a month that they released a Windows version that was way easier to deal with.

Use what works best. :)

---

### Post by HermanAB on 2011-01-23
Unless you want to pay for VMware Workstation, your options are VMware Player and Virtualbox.

I just compiled Virtualbox from source, since I'm running a Beta kernel - rather painful, but now it works.

---

### Post by Wamiduku on 2011-01-23
> **HermanAB said:**
> Unless you want to pay for VMware Workstation, your options are VMware Player and Virtualbox.

> **Wamiduku said:**
> VMWare Workstation/Player doesn't start VMs automatically after boot, and won't shut them down automatically before system shutdown either. 

...and neither will VirtualBox.

---

### Post by CharlesA on 2011-01-23
> **Wamiduku said:**
> ...and neither will VirtualBox.

It will if you write up a script to do so. That's how I have mine set up.

---

### Post by Wamiduku on 2011-01-23
Yes, I suppose you could fix it with scripting. I actually tried VirtualBox on an Intel D510MO board running Ubuntu 9.10, because the disk files are compatible with VMWare disk files, so I thought I'd be able to move VMs between the computers running VMWare and those running VBox. Unfortunately, networking wasn't compatible and I would have had to rename all my disk files too, because VBox doesn't allow 2 VMs to have disk files with the same name, although the disk files are in different directories.

Also, performance was terrible compared to VMWare on the D510MO. Strange, because on a Q9550, I didn't notice any difference between VMWare and VBox. Running VBox's remote desktop didn't work very well either, because the mouse pointer was out of sync with where the guest OS thought it was.

Anyway, the problem is solved, because the D510MO is up and running VMWare under Windows since yesterday, with 2 virtualized Ubuntu servers inside. I can freely move the VMs unmodified back and forth between desktops, running VMWare Workstn, and the server, running VMWare Server. Mission accomplished :).

---

