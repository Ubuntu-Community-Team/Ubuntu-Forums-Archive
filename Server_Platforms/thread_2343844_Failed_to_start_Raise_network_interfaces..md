---
title: "Failed to start Raise network interfaces."
date: 2016-11-19
forum: Server Platforms
---

### Post by Heeter on 2016-11-19
Hi All,

Doing a fresh Server Install with 16.04 and already hitting a wall. I am trying to change my network interface to Static from dhcp:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

source /etc/network/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto enp0s25
iface enp0s25 inet static
        address 192.168.1.9
        netmask 255.255.255.0
        gateway 192.168.1.1
        dns-nameservers 192.168.1.1

```

And then I hit networking restart:
```

root@mail:/etc/mysql# service networking restart
Job for networking.service failed because the control process exited with error code. See "systemctl status networking.service" and "journalctl -xe" for details.

```

So I do this "systemctl status networking.service" and this comes up.
```

root@mail:/etc/mysql# systemctl status networking.service
&#9679; networking.service - Raise network interfaces
   Loaded: loaded (/lib/systemd/system/networking.service; enabled; vendor preset: enabled)
  Drop-In: /run/systemd/generator/networking.service.d
           &#9492;&#9472;50-insserv.conf-$network.conf
   Active: failed (Result: exit-code) since Sat 2016-11-19 14:55:28 MST; 1min 37s ago
     Docs: man:interfaces(5)
  Process: 2327 ExecStop=/sbin/ifdown -a --read-environment (code=exited, status=0/SUCCESS)
  Process: 3854 ExecStart=/sbin/ifup -a --read-environment (code=exited, status=1/FAILURE)
  Process: 3848 ExecStartPre=/bin/sh -c [ "$CONFIGURE_INTERFACES" != "no" ] && [ -n "$(ifquery --read-environment --list --exclude=lo)" ] && udevadm se
 Main PID: 3854 (code=exited, status=1/FAILURE)

Nov 19 14:55:28 server1 systemd[1]: Starting Raise network interfaces...
Nov 19 14:55:28 server1 ifup[3854]: RTNETLINK answers: File exists
Nov 19 14:55:28 server1 ifup[3854]: Failed to bring up enp0s25.
Nov 19 14:55:28 server1 postfix/sendmail[3904]: fatal: /etc/postfix/main.cf, line 213: missing '=' after attribute name: "smtps     inet  n       -    
Nov 19 14:55:28 server1 ifup[3854]: run-parts: /etc/network/if-up.d/postfix exited with return code 75
Nov 19 14:55:28 server1 ifup[3854]: /sbin/ifup: post-up script failed.
Nov 19 14:55:28 server1 systemd[1]: networking.service: Main process exited, code=exited, status=1/FAILURE
Nov 19 14:55:28 server1 systemd[1]: Failed to start Raise network interfaces.
Nov 19 14:55:28 server1 systemd[1]: networking.service: Unit entered failed state.
Nov 19 14:55:28 server1 systemd[1]: networking.service: Failed with result 'exit-code'.
lines 1-21/21 (END)

```

What am I doing wrong?

Regards

---

### Post by darkod on 2016-11-19
Nothing. I have seen the same that sometimes trying to restart the networking service doesn't work. Reboot the machine and it will have the static IP after reboot (it should...).

Alternatively for the restart service command try (sudo in front if not running as root):
```
sudo /etc/init.d/networking restart
```

It should be the same as what you tried, but this way sometimes works better.

---

### Post by Heeter on 2016-11-19
Now having issues with this

```

root@server1:/home/adminpc# service hostname start
Failed to start hostname.service: Unit hostname.service is masked.
root@server1:/home/adminpc# 

```

Any ideas?

Maybe I should go back to 14.04, not used to this stuff not working out of the box :(

Regards

---

### Post by darkod on 2016-11-19
Sorry, can't help with that. I have never used that service.

If all you want to do it set up hostname (FQDN) I always used only /etc/hostname and /etc/hosts. Or setting it up during installation which makes it right from the beginning.

---

### Post by drmatthes on 2016-11-28
I have seen this message (failed to raise network interfaces) in debian based systems very often (lately on debian stretch). Boot hangs for a while (or machine doesn't boot at all).

Follows a quick-and-dirty workaround:

(i) changed line in /etc/network/interfaces to

iface eth$ inet manual

[with $ being number of interface]

(ii) switched off systemd networking like so:

sudo systemctl stop networking.service
sudo systemctl disable networking.service

[ignoring complaints of console about this being not in accordance with runlevel LSBs]

(iii) appended the following line to crontab [code: sudo crontab -e]:

@reboot ifconfig eth$ X.X.X.X && ifup eth$ 

[with X.X.X.X being your static IP address] 

OR, for DHCP:

@reboot dhclient -r eth$ && dhclient eth$

Of course, this means taking away networking from systemd - for me this did the job apart from rendering the system darn slow @bootup or even useless.

Jesko

---

### Post by Heeter on 2016-11-29
Great, Thank you for this @Jesko

---

### Post by drmatthes on 2016-12-04
You're welcome, Heeter. As this was no real solution as far as networking control over systemd is concerned (got the idea from the Raspberry Pi folks, and there are many more solutions around like renumbering network connections or messing around with udev rules) - is there a way to mark this issue as [BUTCHERED] ;) ?

---

### Post by briancady413 on 2017-05-28
Thanks, @Jesko

---

### Post by nirolfciv on 2017-06-06
Hi guys,

Thought not to start a new thread so posting here.
Scenario details
 - Ubuntu 16.04
 - one NIC being used on DHCP

[I]root@ubuntu-laf:~# cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


source /etc/network/interfaces.d/*


# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto eth0
iface eth0 inet dhcp
dns-name servers 127.0.0.1
up route add -net 172.25.0.0/16 gw 172.17.35.1 dev eth0
up route add -net 172.17.40.0/24 gw 172.17.35.1 dev eth0

 - [/I] first of all I have this error going on

*root@ubuntu-laf:~# systemctl status networking.service **â— networking.service - Raise network interfaces*
*   Loaded: loaded (/lib/systemd/system/networking.service; enabled; vendor preset: enabled)*
*  Drop-In: /run/systemd/generator/networking.service.d*
*           â””â”€50-insserv.conf-$network.conf*
*   Active: failed (Result: exit-code) since Tue 2017-06-06 09:27:06 EEST; 8min ago*
*     Docs: man:interfaces(5)*
*  Process: 28964 ExecStart=/sbin/ifup -a --read-environment (code=exited, status=1/FAILURE)*
*  Process: 28958 ExecStartPre=/bin/sh -c [ "$CONFIGURE_INTERFACES" != "no" ] && [ -n "$(ifquery --read-environment --list --exclude=lo)" *
* Main PID: 28964 (code=exited, status=1/FAILURE)*

*Jun 06 09:27:06 ubuntu-laf.laf.ro ifup[28964]: DHCPDECLINE on eth0 to 255.255.255.255 port 67 (xid=0x7421aec5)*
*Jun 06 09:27:06 ubuntu-laf.laf.ro ifup[28964]: Unable to obtain a lease on first try (declined).  Exiting.*
*Jun 06 09:27:06 ubuntu-laf.laf.ro ifup[28964]: Failed to bring up eth0.*
*Jun 06 09:27:06 ubuntu-laf.laf.ro ifup[28964]: /etc/network/if-up.d/sendmail: 44: .: Can't open /usr/share/sendmail/dynamic*
*Jun 06 09:27:06 ubuntu-laf.laf.ro ifup[28964]: run-parts: /etc/network/if-up.d/sendmail exited with return code 2*
*Jun 06 09:27:06 ubuntu-laf.laf.ro ifup[28964]: /sbin/ifup: post-up script failed.*
*Jun 06 09:27:06 ubuntu-laf.laf.ro systemd[1]: networking.service: Main process exited, code=exited, status=1/FAILURE*
*Jun 06 09:27:06 ubuntu-laf.laf.ro systemd[1]: Failed to start Raise network interfaces.*
*Jun 06 09:27:06 ubuntu-laf.laf.ro systemd[1]: networking.service: Unit entered failed state.*
[I]Jun 06 09:27:06 ubuntu-laf.laf.ro systemd[1]: networking.service: Failed with result 'exit-code'.

  - [/I]last but not least, how can I add two static routes on startup
*up route add -net 172.25.0.0/16 gw 172.17.35.1 dev eth0*
*up route add -net 172.17.40.0/24 gw 172.17.35.1 dev eth0*

as routing table doesn't get them

*root@ubuntu-laf:~# ip r*
*default via 172.17.35.254 dev eth0 *
*172.17.35.0/24 dev eth0  proto kernel  scope link  src 172.17.35.107 *
*172.18.0.0/16 dev docker0  proto kernel  scope link  src 172.18.0.1 linkdown *



Thanks,
Florin.

---

### Post by darkod on 2017-06-06
1. Delete the 'dns-name servers' line. It doesn't work with dhcp. Plus you have a typo in it, it should be without space 'dns-nameservers'.

2. Delete the 'up route' also.

3. Check if dhcp works correctly and if you get an IP and have internet/network connectivity.

4. Add the route commands you want in /etc/rc.local above the 'exit 0' line. In that file you can put commands that will be run as root at the end of the boot process on each boot.

---

### Post by nirolfciv on 2017-06-06
Thanks for the reply! Here's current status:

*root@ubuntu-laf:~# cat /etc/network/interfaces*
*# This file describes the network interfaces available on your system*
*# and how to activate them. For more information, see interfaces(5).*

*source /etc/network/interfaces.d/**

*# The loopback network interface*
*auto lo*
*iface lo inet loopback*

*# The primary network interface*
*auto eth0*
*iface eth0 inet dhcp*
*#dns-name servers 127.0.0.1*
*#up route add -net 172.25.0.0/16 gw 172.17.35.1 dev eth0*
*#up route add -net 172.17.40.0/24 gw 172.17.35.1 dev eth0*

[I]#post-up route add -net 172.17.40.0 netmask 255.255.255.0 gw 172.17.35.1
[/I]
*root@ubuntu-laf:~# service networking restart *
*Job for networking.service failed because the control process exited with error code. See "systemctl status networking.service" and "journalctl -xe" for details.*
*root@ubuntu-laf:~# systemctl status networking.service*
*â&#8212; networking.service - Raise network interfaces*
*   Loaded: loaded (/lib/systemd/system/networking.service; enabled; vendor preset: enabled)*
*  Drop-In: /run/systemd/generator/networking.service.d*
*           â&#8221;&#8221;â&#8221;&#8364;50-insserv.conf-$network.conf*
*   Active: failed (Result: exit-code) since Tue 2017-06-06 13:03:39 EEST; 7s ago*
*     Docs: man:interfaces(5)*
*  Process: 2177 ExecStart=/sbin/ifup -a --read-environment (code=exited, status=1/FAILURE)*
*  Process: 2171 ExecStartPre=/bin/sh -c [ "$CONFIGURE_INTERFACES" != "no" ] && [ -n "$(ifquery --read-environment --list --exclude=lo)" ]*
* Main PID: 2177 (code=exited, status=1/FAILURE)*

*Jun 06 13:03:39 ubuntu-laf.laf.ro ifup[2177]: DHCPDECLINE on eth0 to 255.255.255.255 port 67 (xid=0x59cb874f)*
*Jun 06 13:03:39 ubuntu-laf.laf.ro ifup[2177]: Unable to obtain a lease on first try (declined).  Exiting.*
*Jun 06 13:03:39 ubuntu-laf.laf.ro ifup[2177]: Failed to bring up eth0.*
*Jun 06 13:03:39 ubuntu-laf.laf.ro ifup[2177]: /etc/network/if-up.d/sendmail: 44: .: Can't open /usr/share/sendmail/dynamic*
*Jun 06 13:03:39 ubuntu-laf.laf.ro ifup[2177]: run-parts: /etc/network/if-up.d/sendmail exited with return code 2*
*Jun 06 13:03:39 ubuntu-laf.laf.ro ifup[2177]: /sbin/ifup: post-up script failed.*
*Jun 06 13:03:39 ubuntu-laf.laf.ro systemd[1]: networking.service: Main process exited, code=exited, status=1/FAILURE*
*Jun 06 13:03:39 ubuntu-laf.laf.ro systemd[1]: Failed to start Raise network interfaces.*
*Jun 06 13:03:39 ubuntu-laf.laf.ro systemd[1]: networking.service: Unit entered failed state.*
[I]Jun 06 13:03:39 ubuntu-laf.laf.ro systemd[1]: networking.service: Failed with result 'exit-code'.

[/I]Last but not least, this VM is getting its IP address fine no matter I restart the service or reboot the machine.

---

### Post by darkod on 2017-06-06
If you reboot the machine, do you still get that error? Reboot it and then check the status of the networking service and the journal with the same commands as above, only after a reboot.

I have found cases where a restart of the networking service was failing but on reboot it was working OK.

---

### Post by nirolfciv on 2017-06-09
[I]root@ubuntu-laf:~# uptime
 13:13:25 up 1 min,  1 user,  load average: 0.72, 0.49, 0.19

root@ubuntu-laf:~# service networking restart
Job for networking.service failed because the control process exited with error code. See "systemctl status networking.service" and "journalctl -xe" for details.
root@ubuntu-laf:~# systemctl status networking.service
â— networking.service - Raise network interfaces
   Loaded: loaded (/lib/systemd/system/networking.service; enabled; vendor preset: enabled)
  Drop-In: /run/systemd/generator/networking.service.d
           â””â”€50-insserv.conf-$network.conf
   Active: failed (Result: exit-code) since Fri 2017-06-09 13:13:16 EEST; 2s ago
     Docs: man:interfaces(5)
  Process: 1785 ExecStart=/sbin/ifup -a --read-environment (code=exited, status=1/FAILURE)
  Process: 1780 ExecStartPre=/bin/sh -c [ "$CONFIGURE_INTERFACES" != "no" ] && [ -n "$(ifquery --read-environment --list --exclude=lo)" ]
 Main PID: 1785 (code=exited, status=1/FAILURE)


Jun 09 13:13:16 ubuntu-laf.laf.ro ifup[1785]: DHCPDECLINE on eth0 to 255.255.255.255 port 67 (xid=0x5e870913)
Jun 09 13:13:16 ubuntu-laf.laf.ro ifup[1785]: Unable to obtain a lease on first try (declined).  Exiting.
Jun 09 13:13:16 ubuntu-laf.laf.ro ifup[1785]: Failed to bring up eth0.
Jun 09 13:13:16 ubuntu-laf.laf.ro ifup[1785]: /etc/network/if-up.d/sendmail: 44: .: Can't open /usr/share/sendmail/dynamic
Jun 09 13:13:16 ubuntu-laf.laf.ro ifup[1785]: run-parts: /etc/network/if-up.d/sendmail exited with return code 2
Jun 09 13:13:16 ubuntu-laf.laf.ro ifup[1785]: /sbin/ifup: post-up script failed.
Jun 09 13:13:16 ubuntu-laf.laf.ro systemd[1]: networking.service: Main process exited, code=exited, status=1/FAILURE
Jun 09 13:13:16 ubuntu-laf.laf.ro systemd[1]: Failed to start Raise network interfaces.
Jun 09 13:13:16 ubuntu-laf.laf.ro systemd[1]: networking.service: Unit entered failed state.
Jun 09 13:13:16 ubuntu-laf.laf.ro systemd[1]: networking.service: Failed with result 'exit-code'.

[/I]Any thoughts now?

---

### Post by darkod on 2017-06-09
I didn't say to try restart the networking service, just to check it's status. It seems in latest editions the networking can't be restarted on purpose because that is not something you would need restarting often.

So, reboot the machine and check the service status with:
```
sudo systemctl status networking.service
```

Then compare it with the above output of the status.

---

### Post by nirolfciv on 2017-06-09
***I did that, but no luck:***[I]

root@ubuntu-laf:~# uptime
13:13:25 up 1 min, 1 user, load average: 0.72, 0.49, 0.19[/I]

---

### Post by darkod on 2017-06-09
No, luck with what? and you DID NOT do that.

What you did was:
1. Reboot the server.
2. Tried to restart the networking service.
3. Checked its status.

What I am suggesting is this:
1. Reboot the server.
2. Check the service status.

Notice the difference? What I am trying to say is that networking service restart failing is not necessarily an error. But it would be important to see if the networking service status is failed after a reboot. Do not restart the service after the reboot, just check its status.

I think you don't have a problem at all. You think you have a problem because the service restart fails but I have read somewhere that nowdays it is designed to fail. So you can try what I suggest or not, your choice...

---

### Post by nirolfciv on 2017-06-12
> **darkod said:**
> No, luck with what? and you DID NOT do that.

What you did was:
1. Reboot the server.
2. Tried to restart the networking service.
3. Checked its status.

What I am suggesting is this:
1. Reboot the server.
2. Check the service status.

Notice the difference? What I am trying to say is that networking service restart failing is not necessarily an error. But it would be important to see if the networking service status is failed after a reboot. Do not restart the service after the reboot, just check its status.

I think you don't have a problem at all. You think you have a problem because the service restart fails but I have read somewhere that nowdays it is designed to fail. So you can try what I suggest or not, your choice...

Hey,

Thanks for the stubbornness and your replies. Here's SSH session output:

[I]root@ubuntu-laf:~# uptime 13:16:20 up 3 days, 4 min,  1 user,  load average: 0.00, 0.00, 0.00
root@ubuntu-laf:~# systemctl status networking.service
â&#8212; networking.service - Raise network interfaces
   Loaded: loaded (/lib/systemd/system/networking.service; enabled; vendor preset: enabled)
  Drop-In: /run/systemd/generator/networking.service.d
           â&#8221;&#8221;â&#8221;&#8364;50-insserv.conf-$network.conf
   Active: failed (Result: exit-code) since Fri 2017-06-09 13:13:16 EEST; 3 days ago
     Docs: man:interfaces(5)
  Process: 1785 ExecStart=/sbin/ifup -a --read-environment (code=exited, status=1/FAILURE)
  Process: 1780 ExecStartPre=/bin/sh -c [ "$CONFIGURE_INTERFACES" != "no" ] && [ -n "$(ifquery --read-environment --list --exclude=lo)" ] && udevadm 
 Main PID: 1785 (code=exited, status=1/FAILURE)


Jun 09 13:13:16 ubuntu-laf.laf.ro ifup[1785]: DHCPDECLINE on eth0 to 255.255.255.255 port 67 (xid=0x5e870913)
Jun 09 13:13:16 ubuntu-laf.laf.ro ifup[1785]: Unable to obtain a lease on first try (declined).  Exiting.
Jun 09 13:13:16 ubuntu-laf.laf.ro ifup[1785]: Failed to bring up eth0.
Jun 09 13:13:16 ubuntu-laf.laf.ro ifup[1785]: /etc/network/if-up.d/sendmail: 44: .: Can't open /usr/share/sendmail/dynamic
Jun 09 13:13:16 ubuntu-laf.laf.ro ifup[1785]: run-parts: /etc/network/if-up.d/sendmail exited with return code 2
Jun 09 13:13:16 ubuntu-laf.laf.ro ifup[1785]: /sbin/ifup: post-up script failed.
Jun 09 13:13:16 ubuntu-laf.laf.ro systemd[1]: networking.service: Main process exited, code=exited, status=1/FAILURE
Jun 09 13:13:16 ubuntu-laf.laf.ro systemd[1]: Failed to start Raise network interfaces.
Jun 09 13:13:16 ubuntu-laf.laf.ro systemd[1]: networking.service: Unit entered failed state.
Jun 09 13:13:16 ubuntu-laf.laf.ro systemd[1]: networking.service: Failed with result 'exit-code'.

root@ubuntu-laf:~# reboot


Welcome to Ubuntu 16.04.2 LTS (GNU/Linux 4.4.0-78-generic x86_64)


 * Documentation:  [https://help.ubuntu.com](https://help.ubuntu.com)
 * Management:     [https://landscape.canonical.com](https://landscape.canonical.com)
 * Support:        [https://ubuntu.com/advantage](https://ubuntu.com/advantage)


16 packages can be updated.
11 updates are security updates.




Last login: Mon Jun 12 13:15:58 2017 from 172.17.35.71
root@ubuntu-laf:~#root@ubuntu-laf:~# systemctl status networking.service
â&#8212; networking.service - Raise network interfaces
   Loaded: loaded (/lib/systemd/system/networking.service; enabled; vendor preset: enabled)
  Drop-In: /run/systemd/generator/networking.service.d
           â&#8221;&#8221;â&#8221;&#8364;50-insserv.conf-$network.conf
   Active: failed (Result: exit-code) since Mon 2017-06-12 13:16:50 EEST; 45min ago
     Docs: man:interfaces(5)[/I]
  [I]Process: 946 ExecStart=/sbin/ifup -a --read-environment (code=exited, status=1/FAILURE)
  Process: 795 ExecStartPre=/bin/sh -c [ "$CONFIGURE_INTERFACES" != "no" ] && [ -n "$(ifquery --read-environment --list --exclude=lo)" ] && udevadm s
 Main PID: 946 (code=exited, status=1/FAILURE)


Jun 12 13:16:50 ubuntu-laf.laf.ro dhclient[1018]: Unable to obtain a lease on first try (declined).  Exiting.
Jun 12 13:16:50 ubuntu-laf.laf.ro ifup[946]: Unable to obtain a lease on first try (declined).  Exiting.
Jun 12 13:16:50 ubuntu-laf.laf.ro ifup[946]: Failed to bring up eth0.
Jun 12 13:16:50 ubuntu-laf.laf.ro ifup[946]: /etc/network/if-up.d/sendmail: 44: .: Can't open /usr/share/sendmail/dynamic
Jun 12 13:16:50 ubuntu-laf.laf.ro ifup[946]: run-parts: /etc/network/if-up.d/sendmail exited with return code 2
Jun 12 13:16:50 ubuntu-laf.laf.ro ifup[946]: /sbin/ifup: post-up script failed.
Jun 12 13:16:50 ubuntu-laf.laf.ro systemd[1]: networking.service: Main process exited, code=exited, status=1/FAILURE
Jun 12 13:16:50 ubuntu-laf.laf.ro systemd[1]: Failed to start Raise network interfaces.
Jun 12 13:16:50 ubuntu-laf.laf.ro systemd[1]: networking.service: Unit entered failed state.
Jun 12 13:16:50 ubuntu-laf.laf.ro systemd[1]: networking.service: Failed with result 'exit-code'.

[/I] So far, I have no "production error" still I'd like to get rid of that log error. Any chance of doing that?

L.E. where can I add two permanent static routes for this current DHCP config?

---

