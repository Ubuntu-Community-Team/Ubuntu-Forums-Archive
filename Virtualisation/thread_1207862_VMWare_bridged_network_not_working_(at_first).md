---
title: "VMWare bridged network not working (at first)"
date: 2009-07-08
forum: Virtualisation
---

### Post by arch0njw on 2009-07-08
After I log into KDE (4.2.2), if I start VMware Workstation and try to start a VM, I get a message that the bridged network is disabled.

If I go to the CLI and type "[FONT=Courier New]sudo vmware-networks --stop[/FONT]" and then "[FONT=Courier New]sudo vmware-networks --start[/FONT]" I can get it working.

**However**, upon executing both commands, it crashes KDE.  Thankfully, KDE recovers.

This is more of an "how ugly", rather than a complete breakage.  Though, perhaps obviously, it would be nice if it didn't do this.

Kubuntu 9.04 amd64
Dual NIC -- both DHCP   ... (is that the problem?)

I thought I'd start here because I'm 99.999 (ad infinitum) % sure that posting on the VMWare groups is going to get me hit with "workstation ain't supported on that kernel yet, bubba".  Since "we all" like to be a little ahead of the curve, I'm hoping someone else has experienced this and can help.

---

### Post by dcstar on 2009-07-11
> **arch0njw said:**
> After I log into KDE (4.2.2), if I start VMware Workstation and try to start a VM, I get a message that the bridged network is disabled.

If I go to the CLI and type "[FONT=Courier New]sudo vmware-networks --stop[/FONT]" and then "[FONT=Courier New]sudo vmware-networks --start[/FONT]" I can get it working.

**However**, upon executing both commands, it crashes KDE.  Thankfully, KDE recovers.

This is more of an "how ugly", rather than a complete breakage.  Though, perhaps obviously, it would be nice if it didn't do this.

Kubuntu 9.04 amd64
**Dual NIC -- both DHCP   ... (is that the problem?)**
.......

Quite possible, it may be that VMWare networking is trying to start before the DHCP has configured.

Set a Static IP and see what happens.

---

### Post by arch0njw on 2009-07-11
> **dcstar said:**
> Quite possible, it may be that VMWare networking is trying to start before the DHCP has configured.

Set a Static IP and see what happens.

And there arises my second issue KDE 4 in Jaunty removed the nice graphical interface for setting up a static IP.  Is there a *clear* How To for doing this?  I usually like to think I know what I'm doing, but I always seem to really mess things up when I start editing my networking files.

---

### Post by arch0njw on 2009-08-04
I tried changing some services so the startup order would be different.

```
K08vmware@
README 
S01policykit@
S10acpid@
S10sysklogd@ 
S11klogd@
S12dbus@ 
S16ssh@
S20apport@ 
S20dkms_autoinstaller@
S20hotkey-setup@
S20libchipcard-tools@
S20samba@
S24hal@
S25bluetooth@
S30kdm@
S50avahi-daemon@
S50cups@
S50NetworkManager@
S50pulseaudio@
S50rsync@
S50saned@
S70bootlogs.sh@
S70dns-clean@
S70pppd-dns@
S89anacron@
S89atd@
S89cron@
S90vmware@
S91apache2@
S98usplash@
S99acpi-support@
S99laptop-mode@
S99ondemand@
S99rc.local@
S99rmnologin@
S99stop-readahead@
```Unfortunately, that did not seem to help.

I will be trying the static IP when I can get a chance to figure out how it works through a manual (CLI) configuration.  I could find where to do it in KDE3, but either I can't find it in KDE4 or it cannot (yet) be set in KDE4.

---

### Post by arch0njw on 2009-08-10
> **dcstar said:**
> Quite possible, it may be that VMWare networking is trying to start before the DHCP has configured.

Set a Static IP and see what happens.

Bingo.  A Static IP appears to be the trick.  I finally found how to set that up in KDE4.  In KDE3 it was pretty easy, but KDE4 required going straight to /etc/network/interfaces and me learning a few new things.

Thanks!

---

### Post by jocampo on 2009-08-10
Learning how to config and edit your network interfaces via console (instead of GUI) can save you from a lot of troubles :-)

Here some quick tips

IP configuration is on /etc/network/interfaces

An DHCP configuration should look like:

```

auto eth0
iface eth0 inet dhcp

```

A static IP configuration should look like

```

auto eth0
iface eth0 inet static
address 192.168.1.100
gateway 192.168.1.1
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255

```

You can edit files via console using vi. Some useful vi commands are:

Open new line (above current one)
[ESC]+O
Open new line (below)
[ESC]+o
Undo
[ESC]+U

Inserting
a or i

Deleting X or x

Quit without saving
[ESC]+:q!

Saving
[ESC]+:w!

You check your network with

```
ifconfig
```
or
```
iwconfig
```

You restart your network service this way
```
>sudo /etc/init.d/networking restart
```

Finally, please read the man for each command and practice a lot! no matter what X environment you have. I did not know this 1 or 2 months ago ... now I don't depend of a GUI in order to fix or troubleshoot my network interfaces ;-)

---

