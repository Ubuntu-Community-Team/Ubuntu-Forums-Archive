---
title: "Email on hard drive errors"
date: 2015-04-06
forum: Server Platforms
---

### Post by lykwydchykyn on 2015-04-06
I have an Ubuntu server VM which occasionally has problems with its main partition disconnecting, possibly due to our VM backup software.

While I wait for the VM admin to deal with the underlying problem, I'd really like to be alerted when this happens.  The drive is set to remount read-only when it detects errors, but I'd also like it to email me at the same time.   Is there a simple, clean way to accomplish this?

---

### Post by tgalati4 on 2015-04-06
For bare metal, smartmontools will automatically send an email for a failing disk.  Not sure how well it works under a VM.

> tgalati4@Mint17 /etc/smartmontools/run.d $ cat 10mail
#!/bin/bash -e

# Send mail if /usr/bin/mail exists
if ! [ -x /usr/bin/mail ]; then
	echo "Your system does not have /usr/bin/mail.  Install the mailx or mailutils package" 
	exit 1
fi

input=$1
shift

/usr/bin/mail "$@" < $input



Mount errors get written to /var/log/syslog, so perhaps a script that scans for the remount every 5 minutes?

Grep your syslog for an appropriate and specific error that you are looking for.  I don't have any mount failures but I do have some smartd errors:

> tgalati4@Mint17 ~ $ grep smartd /var/log/syslog
Apr  6 07:16:30 Mint17 smartd[1369]: Device: /dev/sda [SAT], 10 Currently unreadable (pending) sectors
Apr  6 07:16:30 Mint17 smartd[1369]: Device: /dev/sda [SAT], SMART Usage Attribute: 190 Airflow_Temperature_Cel changed from 67 to 60
Apr  6 08:40:26 Mint17 smartd[1369]: Device: /dev/sda [SAT], 10 Currently unreadable (pending) sectors
Apr  6 08:40:26 Mint17 smartd[1369]: Device: /dev/sda [SAT], SMART Usage Attribute: 187 Reported_Uncorrect changed from 253 to 100
Apr  6 08:40:26 Mint17 smartd[1369]: Device: /dev/sda [SAT], SMART Usage Attribute: 188 Command_Timeout changed from 253 to 100
Apr  6 08:40:26 Mint17 smartd[1369]: Device: /dev/sda [SAT], SMART Usage Attribute: 190 Airflow_Temperature_Cel changed from 60 to 63

---

### Post by lykwydchykyn on 2015-04-06
Yeah, I was trying to avoid the "grep syslog" route, seems like this is a problem that should have an elegant solution out there already (I can't be the first admin to want to get alerted to disk failures).

I'll check into smartmontools.

---

### Post by lykwydchykyn on 2015-04-06
Well, no such luck. SMART doesn't work on VMware guests, which I guess makes sense since it's a hardware-monitoring thing and this is emulated hardware.

There's got to be a better way to do this than grepping syslog every X minutes.

---

### Post by tgalati4 on 2015-04-06
I didn't think so.  Anyway, you would need some sort of daemon or script running continuously to detect such a failure.  So you can check every 5 minutes:

```
cat /proc/mounts
```

or grep it for your particular drive.  If the drive is missing, then send a notification.

You can (again every 5 minutes) try an automatic mount:

```
sudo mount -av
```

And if nothing gets mounted then you are status quo.

> tgalati4@Mint17 ~ $ sudo mount -va
nothing was mounted

If you get errors mounting a partition, then it will show up and you can send a notification.

I think the reason such a framework is not available is because linux expects perfect hardware (and software), so losing a mount is a rare instance, unless you have a specific hardware or software problem.  Losing a wireless network connection is a frequent event, so there are frameworks that try to re-establish the wireless network connection automatically.

What is the host OS?

---

### Post by lykwydchykyn on 2015-04-06
The host OS is vmware ESX.  

My thinking is that there is already an event which is being responded to with an action (errors=remount-ro).  What I'd really like is a way to hook into that action directly and add another action.  Maybe that's not possible.

I do have a nagios setup that I stumbled through a few months ago, but it only pings right now.  I guess I need to figure out how to make SNMP work with it so I can monitor these things properly.

---

### Post by tgalati4 on 2015-04-06
There are lots of polling monitors available, but they consume a lot of CPU cycles and generally do just what I am suggesting.  Perhaps there is a *dbus* command that can be executed when a mount fails.  That one you will have to research.

```
man dbus
```

Some scripts to play with in the meantime:

[http://unix.stackexchange.com/questions/90426/shell-script-to-validate-mount-point-status-in-the-linux-server](http://unix.stackexchange.com/questions/90426/shell-script-to-validate-mount-point-status-in-the-linux-server)

[http://www.linux.org/threads/looking-for-a-way-to-check-mount-point-is-mounted-and-is-writable.484/](http://www.linux.org/threads/looking-for-a-way-to-check-mount-point-is-mounted-and-is-writable.484/)

I learned of the *mountpoint* command:  [http://stackoverflow.com/questions/9422461/check-if-directory-mounted-with-bash](http://stackoverflow.com/questions/9422461/check-if-directory-mounted-with-bash)

---

