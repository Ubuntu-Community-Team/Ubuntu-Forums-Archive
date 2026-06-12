---
title: "Can we safely remove ZeroConfig, AVAHI ???"
date: 2021-07-12
forum: Security
---

### Post by Rick St. George on 2021-07-12
Given the many security vulnerabilities inherent in ZERCONFIG, BONJOUR, AVAHI, What are the ramifications of removing this programs from an Ubuntu/Linux machine (not a server)? 

See BlackHat Vulneralbilities Slideshow (PDF) here [https://www.blackhat.com/docs/us-16/materials/us-16-Bai-Discovering-And-Exploiting-Novel-Security-Vulnerabilities-In-Apple-Zeroconf.pdf]("https://www.blackhat.com/docs/us-16/materials/us-16-Bai-Discovering-And-Exploiting-Novel-Security-Vulnerabilities-In-Apple-Zeroconf.pdf")

I could not find an answer in Post Search. And could not believe no one has posted this question before.
So, Thank you for your consideration and posting to this question!

---

### Post by &amp;KyT$0P# on 2021-07-13
You can find the ramifications yourself by checking the output from running this command in Terminal -
```
apt-get -s purge avahi*
```
(This is just a simulation.  It won't actually change anything.)

If the result would be unacceptable to you, you could instead stop+disable+mask avahi systemd service(s).

---

### Post by TheFu on 2021-07-13
I've been purging avahi for about a decade.  There are a few inconveniences, but nothing worth leaving it installed, IMHO.  A typical home user who wants their network printer and media players to "just work" would find the inconveniences bad.

---

### Post by Rick St. George on 2021-07-13
Thanks! Ran this;

```

sudo apt-get purge avahi*

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'avahi-ui-utils' for glob 'avahi*'
Note, selecting 'avahi-daemon' for glob 'avahi*'
Note, selecting 'avahi-dnsconfd' for glob 'avahi*'
Note, selecting 'avahi-autoipd' for glob 'avahi*'
Note, selecting 'avahi-utils' for glob 'avahi*'
Note, selecting 'avahi-discover' for glob 'avahi*'
Package 'avahi-discover' is not installed, so not removed
Package 'avahi-dnsconfd' is not installed, so not removed
Package 'avahi-ui-utils' is not installed, so not removed
The following packages will be REMOVED:
  avahi-autoipd* avahi-daemon* avahi-utils* libnss-mdns*
0 upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
After this operation, 662 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 425252 files and directories currently installed.)
Removing avahi-autoipd (0.7-3.1ubuntu1.3) ...
Missing interface name.
Removing avahi-utils (0.7-3.1ubuntu1.3) ...
Removing libnss-mdns:amd64 (0.10-8ubuntu1) ...
Removing avahi-daemon (0.7-3.1ubuntu1.3) ...
Created symlink /run/systemd/system/avahi-daemon.service &#8594; /dev/null.
Removed /run/systemd/system/avahi-daemon.service.
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
Processing triggers for dbus (1.12.2-1ubuntu1.2) ...
Processing triggers for libc-bin (2.27-3ubuntu1.4) ...
(Reading database ... 425176 files and directories currently installed.)
Purging configuration files for libnss-mdns:amd64 (0.10-8ubuntu1) ...
libnss-mdns.postrm: Checking NSS setup...
libnss-mdns.postrm: Removing mdns from NSS setup
Purging configuration files for avahi-daemon (0.7-3.1ubuntu1.3) ...
rmdir: failed to remove '/var/run/avahi-daemon': Directory not empty
Purging configuration files for avahi-autoipd (0.7-3.1ubuntu1.3) ...
Processing triggers for systemd (237-3ubuntu10.48) ...
Processing triggers for dbus (1.12.2-1ubuntu1.2) ...
Processing triggers for ureadahead (0.100.0-21) ...
ureadahead will be reprofiled on next reboot

```

NOTE: that failed to remove '/var/run/avahi-daemon': Directory not empty

So, didn't completely remove, and may restart on reboot!?!?  or Did the "symlink", that it created (line 24), fix that?
Looking in Dir: /etc/systemd/system/multi-user.target.wants the symbolic link for the service to enable avahi was removed.

Thanks!

---

### Post by TheFu on 2021-07-13
Stuff in /var/run/ is unimportant.  It is probably just a PID file.  That is a specifically named file, that just has a PID inside it.  /var/run is a tmpfs, so it is recreated at boot. No long term data is in there.

Relax.

Of course with mdns gone, any systems that were accessed using {hostname}.local previously won't work anymore.

---

### Post by Rick St. George on 2021-07-13
Thanks FU ... you always come through for me!

Closing Thread as SOLVED.

---

