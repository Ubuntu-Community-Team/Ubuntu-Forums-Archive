---
title: "network time server"
date: 2008-08-18
forum: Server Platforms
---

### Post by rosv on 2008-08-18
Hi,
How does one set the clock properly in ubuntu? When I set it manually my systems shows the correct time for a while. After a few days it goes back to showing something completely crazy like the year 2214. The date and time are usually correct.

---

### Post by Krupski on 2008-08-18
> **rosv said:**
> Hi,
How does one set the clock properly in ubuntu? When I set it manually my systems shows the correct time for a while. After a few days it goes back to showing something completely crazy like the year 2214. The date and time are usually correct.

Install the ntp client like this:

```

sudo apt-get install ntp

```

It should just work as-is. If you want, you can add a few more NTP time servers to your /etc/ntp.conf file... like this:

```

sudo nano /etc/ntp.conf

```

About 1/2 screen from the top, you will see this:

```

# You do need to talk to an NTP server or two (or three).
server ntp.ubuntu.com

```

You can add a few more if you like... type this in:

```

# You do need to talk to an NTP server or two (or three).
server time-a.nist.gov **<- note the new one**
server time-b.nist.gov **<- note the new one**
server ntp.ubuntu.com

```

Obviously, leave out the '**<- note the new one**' part!  :)

Good luck!

-- Roger

---

### Post by Robstarusa on 2008-08-18
Speaking of a time server...has anyone setup ubuntu to be a network timeserver with a GPS based clock?

I'd like to use this for a lan which will not always have internet.

---

### Post by davidshere on 2008-09-09
Two questions:

1.  Is there a way to verify that this service is running?  (Other than "ps ax | grep ntp")

2.  Is there a way to "force" an update?

3.  Is there a way to restart the service without a reboot?

Oops.  That's three questions.  Monty Python moment there.

---

### Post by davidshere on 2008-09-09
Answering my own question, from [https://help.ubuntu.com/community/UbuntuTime](https://help.ubuntu.com/community/UbuntuTime)

*Try sudo /etc/init.d/ntp status to check if NTP is running, and sudo /etc/init.d/ntp restart to restart it if necessary. *

That same page says to type *sudo ntpdate ntp.ubuntu.com* to force an update, but that doesn't work for me.  I get the following:

```
david@warthog:~$ sudo ntpdate ntp.ubuntu.com
 9 Sep 13:05:14 ntpdate[7076]: the NTP socket is in use, exiting

```

... not sure what's wrong there.  It seems to be updating anyway; I'm watching the logs:
```

david@raptor:~$ tail -F -n 1000 /var/log/syslog | grep ntpd
Sep  9 13:27:13 raptor ntpd[4066]: ntpd exiting on signal 15
Sep  9 13:27:15 raptor ntpd[22851]: ntpd 4.2.4p4@1.1520-o Fri Mar  7 20:24:07 UTC 2008 (1)
Sep  9 13:27:15 raptor ntpd[22852]: precision = 1.000 usec
...
Sep  9 13:27:15 raptor ntpd[22852]: kernel time sync status 0040
Sep  9 13:27:15 raptor ntpd[22852]: frequency initialized -16.063 PPM from /var/lib/ntp/ntp.drift
Sep  9 13:31:34 raptor ntpd[22852]: synchronized to 128.2.1.21, stratum 2
Sep  9 13:31:34 raptor ntpd[22852]: time reset +17.396120 s
Sep  9 13:31:34 raptor ntpd[22852]: kernel time sync status change 0001
Sep  9 13:36:15 raptor ntpd[22852]: synchronized to 128.2.1.21, stratum 2
```

---

### Post by erwall on 2008-09-09
Here's how I did it, as usual no guarantees!

On the machine you want to be the time server,

```
sudo aptitude remove ntpdate
sudo aptitude install ntp
```

set the following appropriately in /etc/ntp.conf

```

# You do need to talk to an NTP server or two (or three).
server nist1-dc.WiTime.net iburst
server ntp0.mcs.anl.gov
server 0.us.pool.ntp.org
server 1.us.pool.ntp.org
server 2.us.pool.ntp.org
server 3.us.pool.ntp.org

# If you want to provide time to your local subnet, change the next line.
# (Again, the address is an example only.)
broadcast 192.168.1.255

# Allow LAN machines to synchronize with this ntp server
restrict 192.168.1.0 mask 255.255.255.0 nomodify notrap
```

then

```
sudo /etc/init.d/ntp restart
```

on the machines you want to sych to your local time server, 

```
sudo aptitude remove ntpdate
sudo aptitude install ntp
```

set the following in their /etc/ntp.conf:
```

# You do need to talk to an NTP server or two (or three).
server serverip
```

then
```

sudo /etc/init.d/ntp restart
```

---

### Post by davidshere on 2008-09-09
thanks...

when I try to uninstall ntpdate I get this:

```
sudo aptitude remove ntpdate
[sudo] password for david: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages are BROKEN:
  ubuntu-minimal 
The following packages have been automatically kept back:
  evolution-common firefox-3.0 firefox-3.0-gnome-support gnome-cards-data gtk2-engines-murrine gtkhtml3.14 kcontrol kdebase-bin kdebase-data 
  kdebase-kio-plugins kdesktop kfind kicker konqueror konqueror-nsplugins konsole kwin libedataserver1.2-9 libegroupwise1.2-13 libexchange-storage1.2-3 
  libglibmm-2.4-1c2a libgtkhtml3.14-19 libgtksourceview2.0-0 libgtksourceview2.0-common libkonq4 libnspr4-0d libnss3-0d libpcre3 libpoppler-glib2 
  libpoppler2 libwnck22 linux-headers-2.6.24-19 linux-headers-2.6.24-19-generic linux-libc-dev linux-restricted-modules-common 
  openoffice.org-writer2latex python2.5 python2.5-minimal update-notifier-common xserver-xorg-video-intel xulrunner-1.9 xulrunner-1.9-gnome-support 
The following packages have been kept back:
  anacron app-install-data-commercial deskbar-applet eject eog evolution evolution-data-server evolution-data-server-common evolution-exchange 
  evolution-plugins firefox firefox-gnome-support gcalctool gdm gnome-about gnome-desktop-data gnome-games gnome-games-data gnome-panel gnome-panel-data 
  gnome-system-monitor gtk2-engines gtk2-engines-ubuntulooks gvfs gvfs-backends hal initramfs-tools iproute kdebase-bin-kde3 language-pack-en 
  language-pack-gnome-en libcamel1.2-11 libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserverui1.2-8 libgdata-google1.2-1 
  libgdata1.2-1 libgksu2-0 libglib2.0-0 libgnome-desktop-2 libgvfscommon0 libgweather-common libgweather1 libhal-storage1 libhal1 libldap-2.4-2 
  libnss3-1d libpanel-applet2-0 libpango1.0-0 libpango1.0-common libsmbclient libsmbios1 libsoup2.4-1 libtiff4 libwnck-common libxml2 libxml2-utils 
  libxslt1.1 linux-image-2.6.24-19-generic linux-restricted-modules-2.6.24-19-generic nautilus-sendto pciutils poppler-utils procps python-gobject 
  python-libxml2 python2.4 python2.4-minimal samba-common smbclient tzdata ufw update-manager update-manager-core update-notifier xsltproc yelp 
The following packages will be REMOVED:
  ntpdate 
0 packages upgraded, 0 newly installed, 1 to remove and 121 not upgraded.
Need to get 0B of archives. After unpacking 217kB will be freed.
The following packages have unmet dependencies:
  ubuntu-minimal: Depends: ntpdate but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
ubuntu-minimal

Score is 115

Accept this solution? [Y/n/q/?] q
Abandoning all efforts to resolve these dependencies.
Abort.

```

---

### Post by erwall on 2008-09-09
I just said yes to that and it worked out fine.

---

### Post by davidshere on 2008-09-10
Thanks for all your help folks.  I plowed through the "ubuntu minimal broken" problem, and I've made some progress.

My network time server appears to be working fine, even though it doesn't report to the syslog when it receives a request from a client.  When I first started it up, I got this:
```
Sep  9 13:27:15 raptor ntpd[22852]: frequency initialized -16.063 PPM from /var/lib/ntp/ntp.drift
Sep  9 13:31:34 raptor ntpd[22852]: synchronized to 128.2.1.21, stratum 2
Sep  9 13:31:34 raptor ntpd[22852]: time reset +17.396120 s
Sep  9 13:31:34 raptor ntpd[22852]: kernel time sync status change 0001

```
This is the ONLY time I've received the "time reset ** s" message.  Never again.  It would seem that it hasn't made any clock corrections since then, but it does stay that it is staying synchronized:
```
david@raptor:~$ tail -n 10000 /var/log/syslog | grep synch
Sep 10 08:41:27 raptor ntpd[1113]: synchronized to 75.144.70.35, stratum 2
Sep 10 08:46:48 raptor ntpd[1113]: synchronized to 91.189.94.4, stratum 2
Sep 10 09:02:59 raptor ntpd[1113]: synchronized to 75.144.70.35, stratum 2
Sep 10 09:22:23 raptor ntpd[1113]: synchronized to 91.189.94.4, stratum 2
Sep 10 09:37:25 raptor ntpd[1113]: synchronized to 75.144.70.35, stratum 2
Sep 10 09:50:18 raptor ntpd[1113]: synchronized to 91.189.94.4, stratum 2
Sep 10 10:57:47 raptor ntpd[7791]: synchronized to 209.237.247.192, stratum 3
Sep 10 11:05:16 raptor ntpd[7791]: synchronized to 91.189.94.4, stratum 2

```
These "synchronized to" messages are then followed by a line like this:
```
Sep 10 10:57:47 raptor ntpd[7791]: synchronized to 209.237.247.192, stratum 3
Sep 10 10:57:47 raptor ntpd[7791]: kernel time sync status change 0001

```
Does that mean that it reset the clock, or not?

The same appears to be happening on the client, and there I've done more experimentation.  My client is a virtual machine (virtual machine timekeeping problems is what prompted me to look into this), and reverting to a snapshot each time I want to start over and try again.  I can uninstall ntpdate, install ntp.  The ntp daemon, however, once it's running, (I'm monitoring in the syslog) doesn't reset the clock, unlike the server, which did so on its first startup.  I did some digging and found "ntpd -q" as a command to force an update.  I have to stop the running ntpd process before I can run this command.  The first time I run "ntpd -q", it complains (in the log, not from the command line):
```
Sep  9 14:24:47 texan ntpd[4503]: time correction of 74136 seconds exceeds sanity limit (1000); set clock manually to the correct UTC time.

```
That's fine and makes sense; the clock is still set to yesterday when I created the virtual machine snapshot.  I did more digging and found that "ntpq -qg" will override the sanity check, and my clock is reset.  Yay!
```
Sep  9 14:25:04 texan ntpd[4504]: time reset +74136.166099 s
```
I can run "ntpq -q" repeatedly from then on and clearly see that it's correcting 100ths of a second each time:
```
root@texan:/home/david# ntpd -q
ntpd: time slew +0.032597s
root@texan:/home/david# ntpd -q
ntpd: time slew +0.026639s
root@texan:/home/david# ntpd -q
ntpd: time slew -0.000343s

```
So clearly, each time an update is requested from the server, a reply is received, and a correction is necessary and possible.  Yet, when I start the ntp daemon back up:
```
Sep 10 11:23:13 texan ntpd[4594]: ntpd 4.2.4p4@1.1520-o Fri Mar  7 20:24:07 UTC 2008 (1)
Sep 10 11:23:13 texan ntpd[4595]: precision = 3.000 usec
Sep 10 11:23:13 texan ntpd[4595]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Sep 10 11:23:13 texan ntpd[4595]: Listening on interface #1 wildcard, ::#123 Disabled
Sep 10 11:23:13 texan ntpd[4595]: Listening on interface #2 lo, ::1#123 Enabled
Sep 10 11:23:13 texan ntpd[4595]: Listening on interface #3 eth0, (ipv6address)#123 Enabled
Sep 10 11:23:13 texan ntpd[4595]: Listening on interface #4 lo, 127.0.0.1#123 Enabled
Sep 10 11:23:13 texan ntpd[4595]: Listening on interface #5 eth0, ***.***.***.***#123 Enabled
Sep 10 11:23:13 texan ntpd[4595]: kernel time sync status 0040
Sep 10 11:23:13 texan ntpd[4595]: frequency initialized 0.000 PPM from /var/lib/ntp/ntp.drift

```
No synchronization.  As I was writing this post, I did see this in the log:
```
Sep 10 11:27:32 texan ntpd[4595]: synchronized to ***.***.***.***, stratum 3
Sep 10 11:27:32 texan ntpd[4595]: kernel time sync status change 0001

```
This says to me that no time reset was necessary, which I find hard to believe, since when I run the update manually, a time reset is always necessary.  Plus there's no way for me to find out if the automatic updates will work, because I have no idea what to expect the time between automatic updates to be.

What I need is:
1.  A way to force an update without stopping the ntp daemon process
2.  A way to force the daemon to update more frequently, at least temporarily, until I determine that its regular updates are working right
3.  An error message from the daemon if it isn't receiving a reply from the server, or if it cannot set the clock.
4.  Some clue of what I'm doing wrong.  
5.  Someone to tell me I'm worrying about nothing.

I've also tried running the cron job that I found at /etc/cron.daily/ntp -- however, that produces no output and no messages in the syslog.

Any further help would be greatly appreciated.

---

### Post by promodus on 2008-09-11
Something I learned, just to keep in mind for troubleshooting ntp.

It can take 5 minutes for the ntp daemon to start... 
So if your client keeps telling you "No server suitable for synchronization found" Just wait about 5 minutes.

From my desktop:
```
root@blackbox:~# ntpdate server
10 Sep 20:51:21 ntpdate[9372]: no server suitable for synchronization found
root@blackbox:~# ntpdate server
10 Sep 20:57:05 ntpdate[9465]: adjust time server 10.0.0.1 offset 0.062798 sec
```


and from my server:```

Sep 10 20:50:32 server ntpd[24172]: ntpd 4.2.4p4@1.1520-o Fri Mar  7 20:36:58 UTC 2008 (1)
Sep 10 20:50:32 server ntpd[24173]: precision = 1.000 usec
Sep 10 20:50:32 server ntpd[24173]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Sep 10 20:50:32 server ntpd[24173]: Listening on interface #1 wildcard, ::#123 Disabled
Sep 10 20:50:32 server ntpd[24173]: Listening on interface #2 lo, ::1#123 Enabled
Sep 10 20:50:32 server ntpd[24173]: Listening on interface #3 eth0, fe80::215:f2ff:fe55:38a0#123 Enabled
Sep 10 20:50:32 server ntpd[24173]: Listening on interface #4 lo, 127.0.0.1#123 Enabled
Sep 10 20:50:32 server ntpd[24173]: Listening on interface #5 eth0, 10.0.0.1#123 Enabled
Sep 10 20:50:32 server ntpd[24173]: kernel time sync status 0040
Sep 10 20:50:32 server ntpd[24173]: frequency initialized 0.539 PPM from /var/lib/ntp/ntp.drift
Sep 10 20:54:51 server ntpd[24173]: synchronized to 132.246.168.164, stratum 2
Sep 10 20:54:51 server ntpd[24173]: kernel time sync status change 0001
```

---

