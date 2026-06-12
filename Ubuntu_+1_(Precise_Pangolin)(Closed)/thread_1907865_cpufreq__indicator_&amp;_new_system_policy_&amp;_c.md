---
title: "cpufreq / indicator &amp; new system policy &amp; crash on boot"
date: 2012-01-12
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by effenberg0x0 on 2012-01-12
This is a fresh PP install, no VM. As soon as I boot, I have a dialog asking for my root password in order for cpufreq to switch from performance to ondemand. No matter how fast I try to enter my root password, cpufreq indicator crashes first. See screenshot.

[attach]210685[/attach]

**EDIT:** It started happening 3 days ago. I have waited for some more updates until today, but the problem persists.

---

### Post by zika on 2012-01-12
> **effenberg0x0 said:**
> This is a fresh PP install, no VM. As soon as I boot, I have a dialog asking for my root password in order for cpufreq to switch from performance to ondemand. No matter how fast I try to enter my root password, cpufreq indicator crashes first. See screenshot.

[attach]210685[/attach]

**EDIT:** It started happening 3 days ago. I have waited for some more updates until today, but the problem persists.
If You're aware of stuff below disregard it...
You can (always) use CLI to acomplish what You want...

---

### Post by effenberg0x0 on 2012-01-12
Hi Zika, 

Yes, sure. Actually the crash is secondary for me. 

I was just wondering the causes for the policy issue. I think cpufreqd, as a service started by root, should have the freedom to adjust cpu state with no user intervention, it has been like that. But I'm not sure if I'm seeing a bug or a real new system policy (fruit of a decision in the lines of "no, cpufreq *should* need user auth").

---

### Post by mc4man on 2012-01-12
You should be given that thru /var/lib/polkit-1/localauthority/10-vendor.d/com.ubuntu.desktop.pkla
Though possibly the running of ondemand is something separate from above?
(you could try flip flopping admin & sudo in the above .pkla section

Am going to modify ondemand tonight to provide a little better performance response, (set the upscale threshold to 75, lower the sleep to 30),  will see if there are any issues with it running (haven't seen the message you're getting

---

### Post by effenberg0x0 on 2012-01-12
> **mc4man said:**
> You should be given that thru /var/lib/polkit-1/localauthority/10-vendor.d/com.ubuntu.desktop.pkla
Though possibly the running of ondemand is something separate from above?
(you could try flip flopping admin & sudo in the above .pkla section

Am going to modify ondemand tonight to provide a little better performance response, (set the upscale threshold to 75, lower the sleep to 30),  will see if there are any issues with it running (haven't seen the message you're getting


Hey, 
No luck with admin/sudo changes to the Identity of the "[Change CPU Frequency scaling]" section. Here's how it it's set, by default.
[05:28 PM][ahsl:AL-DESK:~/dev/java-manager]
$ sudo cat /var/lib/polkit-1/localauthority/10-vendor.d/com.ubuntu.desktop.pkla
```
[Mounting, checking, etc. of internal drives]
Identity=unix-group:admin;unix-group:sudo
Action=org.freedesktop.udisks.filesystem-*;org.freedesktop.udisks.drive-ata-smart*
ResultActive=yes

[Change CPU Frequency scaling]
Identity=unix-group:admin;unix-group:sudo
Action=org.gnome.cpufreqselector
ResultActive=yes

[Setting the clock]
Identity=unix-group:admin;unix-group:sudo
Action=org.gnome.clockapplet.mechanism.*;org.gnome.settingsdaemon.datetimemechanism.*;org.kde.kcontrol.kcmclock.save
ResultActive=yes

[Adding or changing system-wide NetworkManager connections]
Identity=unix-group:admin;unix-group:sudo
Action=org.freedesktop.NetworkManager.settings.modify.system
ResultActive=yes

[Update already installed software]
Identity=unix-group:admin;unix-group:sudo
Action=org.debian.apt.upgrade-packages
ResultActive=yes

[usb-creator]
Identity=unix-group:admin;unix-group:sudo
Action=com.ubuntu.usbcreator.mount;com.ubuntu.usbcreator.image
ResultActive=yes

[Printer administration]
Identity=unix-group:lpadmin;unix-group:admin;unix-group:sudo
Action=org.opensuse.cupspkhelper.mechanism.*
ResultActive=yes

[Disable hibernate by default]
Identity=unix-user:*
Action=org.freedesktop.upower.hibernate
ResultActive=no


```/etc/init.d/ondemand looks ok to me too. Not sure, haven't really messed with it ever. ```

[05:28 PM][ahsl:AL-DESK:~/dev/java-manager]
$ sudo cat /etc/init.d/ondemand 
#! /bin/sh
### BEGIN INIT INFO
# Provides:          ondemand
# Required-Start:    $remote_fs $all
# Required-Stop:
# Default-Start:     2 3 4 5
# Default-Stop:
# Short-Description: Set the CPU Frequency Scaling governor to "ondemand"
### END INIT INFO


PATH=/sbin:/usr/sbin:/bin:/usr/bin

. /lib/init/vars.sh
. /lib/lsb/init-functions

case "$1" in
    start)
        start-stop-daemon --start --background --exec /etc/init.d/ondemand -- background
        ;;
    background)
    sleep 60 # probably enough time for desktop login

    for CPUFREQ in /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
    do
        [ -f $CPUFREQ ] || continue
        echo -n ondemand > $CPUFREQ
    done
    ;;
    restart|reload|force-reload)
        echo "Error: argument '$1' not supported" >&2
        exit 3
        ;;
    stop)
        ;;
    *)
        echo "Usage: $0 start|stop" >&2
        exit 3
        ;;
esac

```I can see that manually changing the governor via echoing stuff to  /sys/devices/system/cpu/cpu0/cpufreq/* works without  creating this dialog/error (of course, as I'm already root when I echo  anything inside /sys).

---

### Post by mc4man on 2012-01-13
See no issues with the ondemand script, default or otherwise.

However the cpufreq indicator is using the wrong group, probably should file a bug on - [edit]("https://bugs.launchpad.net/ubuntu/+source/indicator-cpufreq/+bug/916360")


In the meantime, if desired - 

```
sudo gedit /var/lib/polkit-1/localauthority/10-vendor.d/indicator-cpufreq.pkla
```

change to Identity=unix-group:sudo


```
[Change CPU Frequency scaling]
Identity=unix-group:sudo
Action=com.ubuntu.indicatorcpufreqselector.setfrequencyscaling
ResultActive=yes
```

If for some reason you don't have that file then just create your own as above in /var/lib/polkit-1/localauthority/50-local.d, maybe with slight name change as in - 

sudo gedit /var/lib/polkit-1/localauthority/50-local.d/cpufreq.pkla

(.pkla's in 50-.. are not subject to be overwritten, I have a few that make dev use simpler

---

### Post by effenberg0x0 on 2012-01-13
> **mc4man said:**
> See no issues with the ondemand script, default or otherwise.

However the cpufreq indicator is using the wrong group, probably should file a bug on - [edit]("https://bugs.launchpad.net/ubuntu/+source/indicator-cpufreq/+bug/916360")


In the meantime, if desired - 

```
sudo gedit /var/lib/polkit-1/localauthority/10-vendor.d/indicator-cpufreq.pkla
```change to Identity=unix-group:sudo


```
[Change CPU Frequency scaling]
Identity=unix-group:sudo
Action=com.ubuntu.indicatorcpufreqselector.setfrequencyscaling
ResultActive=yes
```If for some reason you don't have that file then just create your own as above in /var/lib/polkit-1/localauthority/50-local.d, maybe with slight name change as in - 

sudo gedit /var/lib/polkit-1/localauthority/50-local.d/cpufreq.pkla

(.pkla's in 50-.. are not subject to be overwritten, I have a few that make dev use simpler

You nailed it, as usual :) I did had it set to the admin group. I'm a little confused about the change from admin to sudo group: My user is still part of admin and the admin group seems to be valid. I guess I haven't really considered the impact of such a change. Gotta study.

---

### Post by mc4man on 2012-01-13
Here's the main bug on where all the little ones end up on - 
[https://bugs.launchpad.net/ubuntu/+source/policykit-1/+bug/893842](https://bugs.launchpad.net/ubuntu/+source/policykit-1/+bug/893842)

Atm both sudo & admin are valid though the default for new installs should just be sudo

A curious new one is with command-not-found, been 'fixed' a couple of times though still not working here as released. 
I am only in the sudo group & still get the wrong terminal prompt. By reversing the order in the c-n-f script i then get the correct prompt
(it may be the "or" is being ignored

At least thru 12.04 there technically shouldn't be any issue if in admin or sudo or both, obviously that won't always be true, & currently isn't...

slightly ot - 
while in the past I saw more demonstrable advantage I still use this for ondemand & think it helps at times on this laptop - red edited, blue added


```
#! /bin/sh
### BEGIN INIT INFO
# Provides:          ondemand
# Required-Start:    $remote_fs $all
# Required-Stop:
# Default-Start:     2 3 4 5
# Default-Stop:
# Short-Description: Set the CPU Frequency Scaling governor to "ondemand"
### END INIT INFO


PATH=/sbin:/usr/sbin:/bin:/usr/bin

. /lib/init/vars.sh
. /lib/lsb/init-functions

case "$1" in
    start)
    	start-stop-daemon --start --background --exec /etc/init.d/ondemand -- background
        ;;
    background)
	sleep [COLOR="Red"]30[/COLOR] # probably enough time for desktop login

	for CPUFREQ in /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
	do
		[ -f $CPUFREQ ] || continue
		echo -n ondemand > $CPUFREQ
	done

	[COLOR="Blue"]for CPU_THRESHOLD in /sys/devices/system/cpu/cpufreq/ondemand/up_threshold
	do
		[ -f $CPU_THRESHOLD ] || continue
		echo -n 70 > $CPU_THRESHOLD
	done[/COLOR]
	;;
    restart|reload|force-reload)
        echo "Error: argument '$1' not supported" >&2
        exit 3
        ;;
    stop)
       ;;
    *)
        echo "Usage: $0 start|stop" >&2
        exit 3
        ;;
esac
```

---

### Post by zika on 2012-01-14
error

---

### Post by effenberg0x0 on 2012-01-14
> **zika said:**
> error
And this is the problem with programmers that don't like to print more helpful messages to stderr. :)

---

### Post by zika on 2012-01-14
> **effenberg0x0 said:**
> And this is the problem with programmers that don't like to print more helpful messages to stderr. :)
That was my error... ;)
That should have gone to nul... ;)

---

