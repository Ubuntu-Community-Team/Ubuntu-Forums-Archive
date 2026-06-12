---
title: "Ubuntu Server 13.10 keeps falling asleep"
date: 2014-01-04
forum: Server Platforms
---

### Post by thishalll on 2014-01-04
I installed Ubuntu Server 13.10 (32bit) on my old laptop, AVERATEC 6100, to build web server.  The Ubuntu Server has been updated to the latest version.

The laptop has the [SIZE=3]rt2500pci[/SIZE] network card, and it's using wifi (not a physical cable).

When I finished setting it up, everything seemed working well, but around half minutes later, it started [SIZE=3]driving me crazy[/SIZE].


First, it gives me an error message: *ieee80211 phy0: rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16)* over and over again.

I thought the problem was caused by _power management_, so I added following lines in '*/etc/systemd/logind.conf*'

```

HandlePowerKey=ignore
HandleSuspendKey=ignore
HandleHibernateKey=ignore
HandleLidSwitch=ignore

```

Above codes prevented from falling asleep when I close the lid of the laptop.

Also I entered this command:

```
sudo iwconfig wlan0 power off
```

Then, the error messages didn't show up anymore.  I also added the above command in */etc/rc.local *to start it up automatically.


[SIZE=5]HOWEVER,[/SIZE]


_The network drive keeps falling asleep_. When I try to connect to the FTP server or other server (SSH, APACHE2, or etc.) from other computer, the server doesn't respond.  I HAVE TO run the code '*ping google.com*' on my ubuntu server(the laptop) to wake up the network card.  After typing the above code, it wakes up around 2~3 seconds later.  Then, I can connect to my server.

So I have tried these methods (yeah, I worked hard).[INDENT]
1. Added the line *SUSPEND_MODULES="rt2500pci"* in */etc/pm/config.d/config* -> Doesn't work

[/INDENT]
[INDENT]2. Installed network-manager (by *sudo apt-get install network-manager*) and run the code: *sudo nmcil nm sleep false* -> Doesn't work

[/INDENT]
[INDENT]3. Tried to disable ACPI function, but in the BIOS setup, there is no ACPI configure section (BIOS: American Megatrends 02.54).  So I added '*acpi=off' *at GRUB menu ([http://askubuntu.com/questions/160036/how-do-i-disable-acpi-when-booting](http://askubuntu.com/questions/160036/how-do-i-disable-acpi-when-booting)).  -> Doesn't work.[/INDENT]



I have been stuck at this problem for a week!  I have tried every solutions I could find, and nothing worked.

**[SIZE=2]Please PLEASE help me out[/SIZE]**. If any information you need, please let me know (and sorry for my incorrect English grammar, I'm a foreign student in the US).
[SIZE=4]
I will check this thread every. single. hour.
[SIZE=2]
Also, the interesting is the monitor of the laptop keeps falling asleep as well.  I'm pretty sure the problem is causing by power management..


[/SIZE]
[/SIZE]

---

### Post by nerdtron on 2014-01-05
Not really a workaround since you are in a hurry.
Write a cron job that will ping google.com every 10 minutes just to wake up the server.
Why 13.10 and why put a server on laptop?

---

### Post by tgalati4 on 2014-01-05
I would look for an updated BIOS for the computer and check for any power management settings (in BIOS) that you have overlooked.  Also, look into the laptop framework:

```
apropos laptop
man laptop-detect
cat /etc/default/acpi-support
```

There are several ways to put a machine to sleep.  If the OS thinks you have a laptop (and you do) then one of those methods will eventually put your machine to sleep.

> # Please specify a space separated list of options. The recommended value is
# "dbus pm-utils"
#
SUSPEND_METHODS="**dbus-pm dbus-hal pm-utils**"

Why 13.10?  Why are you using a laptop as a server?

---

### Post by thishalll on 2014-01-05
Oh, the cron job idea is pretty good. But is there real solution for my program?

And what about 13.10? Is it really bad? should I install 12.04?

The laptop is the only computer that I can use as a server.. :P

---

### Post by thishalll on 2014-01-05
> **tgalati4 said:**
> I would look for an updated BIOS for the computer and check for any power management settings (in BIOS) that you have overlooked.  Also, look into the laptop framework:

```
apropos laptop
man laptop-detect
cat /etc/default/acpi-support
```

There are several ways to put a machine to sleep.  If the OS thinks you have a laptop (and you do) then one of those methods will eventually put your machine to sleep.



Why 13.10?  Why are you using a laptop as a server?


Thanks for replying!

```
apropos laptop
RESULT: laptop-detect (8) - attempt to detect a laptop

```


```
cat /etc/default/acpi-support
RESULT: No such file or directory

```

and I think the laptop is so old so probably I can't update BIOS (but I will try).

The laptop is the only computer that I can use as a server haha.

---

### Post by nerdtron on 2014-01-05
If you're testing for a web server and going to deploy it on a production server, you wouldn't use 13.10 right? Ubuntu 12.04 is LTS supported until 2017, 13.10 is a normal release with only 18 month support, you can't install/update any software on a release that is no longer supported.

Can you look again on the BIOS of the computer, maybe there could be setting in there about power saving, try disabling them and see if there are any difference.

---

### Post by SeijiSensei on 2014-01-07
A simple alternative to a cron job for pinging remotes is to use the -n, -c and -i parameters to ping like this:

```
ping -i 60 -c 5 -n 9999999999 8.8.8.8 &
```

That will ping Google's DNS server five times every sixty seconds for a very long time.  The "&" puts the job into the background so it will continue to run after you log out.

---

### Post by tgalati4 on 2014-01-07
I don't know why you don't have /etc/default/acpi-support since it is in 12.10, perhaps the acpi framework changed in 13.10.

Since you have *laptop-detect* on your system, there is probably a script somewhere that uses it and sets power management features.

You can install *ethtool* to query the network card and to set certain features (like turn off network card sleep).

---

