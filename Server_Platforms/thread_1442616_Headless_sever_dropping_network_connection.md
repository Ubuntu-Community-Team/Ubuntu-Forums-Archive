---
title: "Headless sever dropping network connection"
date: 2010-03-30
forum: Server Platforms
---

### Post by jdeal on 2010-03-30
Hello All.  I have a Dell Dimension 2350 with very unreliable video that I am trying to setup as a headless build/test server.  I was able to install Ubuntu Server 9.10, DHCP to a router that always returns the same address to the server.  I added ssh, LAMP, etc. support during install.

I was able to connect via ssh and add packages, download source, etc.  The problem is the server just disconnects itself from the router after about 10 minutes or so.  At first I thought it was an ssh timeout but I was unable to establish any ssh connections and upon investigating the router, I discovered that the connection was gone.  I have rebooted the server several times, increasing the ssh timeout to 3 hours, and the same thing happens.  Have great ssh service for about 10 minutes or so then it disconnects.  BTW when I had this as a Ubuntu 9.10 desktop system I did not have network disconnect issues.

Looking at syslog, the last entry was something like "IPV6 network not found" or something like that.  The server will not boot up now so I can't look at the log.  I don't remember specifying IP6 support during install but maybe it is the default and I did not catch it.  I have other systems on this network with both IP4 and IP6 network support and they do not have network issues.

I am going to try to get the video to work again long enough to see what the problem is (why it won't reboot) or do a reinstall.  I was just wondering if someone has any idea why my Ubuntu 9.10 server can not maintain a network connection.  Thanks!

---

### Post by Iowan on 2010-03-30
First thing that comes to mind is a BIOS setting for power saving that may disable the NIC. It may not be an issue on a machine with a keyboard, but couldn't recover on a headless machine. (Solution? - sorry...)

---

### Post by jdeal on 2010-03-30
Hello Iowan.  Could be.  Right now it is working but I have a monitor attached.  Been able to have an ssh session for an hour or so now.  It has been a busy connection so maybe that is preventing it from dropping out.

The next time I reboot and the video holds together I will check the firmware settings.  Good suggestion.  Thanks.

---

### Post by jdeal on 2010-04-04
Looked into the ACPI issue.  On the Dell 2350 the ACPI options are S1 and S3.  Both claim to shut down the monitor (I assume they mean the video circuits) and hard drive.  There is not any firmware option to turn it completely off.

Ran this server with the monitor attached but not on for hours yesterday.  Some of this time it was idle for say 30 minutes or so a few times.  No problems.

This morning, disconnected monitor, keyboard, and mouse (experimented with just keyboard and mouse before but no effect) and booted server.  Got ssh connections which died within 10 minutes.  

Last syslog entries are:

Apr  4 05:25:48 server dhclient: DHCPOFFER of 192.168.1.2 from 192.168.1.1
Apr  4 05:25:48 server dhclient: DHCPREQUEST of 192.168.1.2 on eth0 to 255.255.255.255 port 67
Apr  4 05:25:50 server dhclient: DHCPACK of 192.168.1.2 from 192.168.1.1
Apr  4 05:25:50 server dhclient: bound to 192.168.1.2 -- renewal in 877110497 seconds.
Apr  4 05:25:48 server ntpdate[1239]: step time server 91.189.94.4 offset -2.285350 sec
Apr  4 05:25:54 server kernel: [   23.885102] eth0: no IPv6 routers present
Apr  4 05:31:22 server mountd[1144]: authenticated mount request from 192.168.1.3:788 for /home/jdeal (/home/jdeal)
Apr  4 05:41:25 server kernel: imklog 4.2.0, log source = /var/run/rsyslog/kmsg started.
Apr  4 05:41:25 server rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="711" x-info="http://www.rsyslog.com"] (re)start


The NFS mount was successful and I was working on this server and the connections just dropped.

Anyway I can live with this situation.  It is just a signifiant inconvience because I have a large 19" CRT monitor sitting on a small desk next to this server, making the desk somewhat useless.  Thanks to all for looking at this.

---

### Post by Iowan on 2010-04-04
[Similar]("http://ubuntuforums.org/showthread.php?t=1397722") thread - any help?

---

### Post by jrssystemsnet on 2010-04-05
Try running a shell script in the background that just pings your router once per second - it's negligible load on the box or the router, but it should be sufficient activity to keep the NIC alive.

Ugly, but it ought to work.

---

### Post by jdeal on 2010-04-08
Humm.  Worth a try.  Thanks for the suggestion.  But still, with no network activity on my part but with a monitor plugged in, it will stay reachable on the net.  With a keyboard and mouse plugged in but no monitor, it will not.  The problem seems independent of network traffic.

I just forced acpi=off in the grub boot options and it did not make a difference.

---

### Post by liamf on 2010-04-08
Hmm. Sound like I have exactly the same issue.

Dell (something fairly old. Optiplex I think ... sorry ... it's up in the attic now ... headless dontcha know), was working fine during setup as normal GUI workstation.

Converted to headless yesterday to use as MythTV backend, removed gdm and grub splash etc. On boot it works fine for 5-10 minutes (I use VNC to remotely log into it) then drops off the network so it might as well be dead.

Can't be recovered except by power cycling ... when the whole sorry tale begins again.

I had high hopes for acpi=off but looks like that won't work from what you say.

Will keep looking ...

---

### Post by liamf on 2010-04-08
Alrighty: looks like encouraging news for me (if not for you :-( )

Changing the GRUB_CMDLINE_LINUX_DEFAULT in /etc/default/grub to

```

GRUB_CMDLINE_LINUX_DEFAULT="text acpi=off"

```

followed by a grub config rebuild seems to have fixed this for me. At least I am typing this over VNC to that machine a good half-hour after the reboot and it's still alive.

---

### Post by jdeal on 2010-04-24
Thanks for the tip liamf.  I will give it a try.  My system seems to be having hardware issues (does not seem to reset the CD on reset) but will see if I can fix that and give your idea a go.  Thanks!

---

### Post by bootkast on 2010-05-31
I had a similar problem with a Dell GX260.  I made three small changes, but I suspect, it was leaving a keyboard plugged in that fixed everything.

1) plug keyboard in
2) change bios setting to ignore keyboard errors
3) change power settings to S1 (sleep mode).  This probably did nothing.
4) Boot with monitor plug in (more for checking errors because I couldn't ssh in anymore!).  --- Later removed monitor, still running fine.

best of luck.  keep us informed!

---

