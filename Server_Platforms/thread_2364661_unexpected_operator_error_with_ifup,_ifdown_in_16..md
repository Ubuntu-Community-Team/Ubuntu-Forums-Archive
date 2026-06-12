---
title: "unexpected operator error with ifup, ifdown in 16.04"
date: 2017-06-26
forum: Server Platforms
---

### Post by erik5678 on 2017-06-26
Hi!

I just upgraded another one of my VMs to 16.04, and I have solved most of the issues post upgrade, but there's one I can't figure out.

When using ifup and ifdown I get an error message, "/sbin/dhclient-script: 7: [: =: unexpected operator". I don't get this error on any other machine running 16.04. I have one with static IP, and 3 with DHCP assigned "static" IP. This is the only one that give me this error. Anyone else experiences this, and more importantly, does anyone have a solution?


Output from running "ifdown ens33 && ifup ens33" (MAC-address masked)
```
Killed old client processInternet Systems Consortium DHCP Client 4.3.3
Copyright 2004-2015 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/


Listening on LPF/ens33/xx:xx:xx:xx:xx:xx
Sending on   LPF/ens33/xx:xx:xx:xx:xx:xx
Sending on   Socket/fallback
DHCPRELEASE on ens33 to 192.168.0.1 port 67 (xid=0x5291f2ed)
/sbin/dhclient-script: 7: [: =: unexpected operator
Internet Systems Consortium DHCP Client 4.3.3
Copyright 2004-2015 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/


/sbin/dhclient-script: 7: [: =: unexpected operator
Listening on LPF/ens33/xx:xx:xx:xx:xx:xx
Sending on   LPF/ens33/xx:xx:xx:xx:xx:xx
Sending on   Socket/fallback
DHCPDISCOVER on ens33 to 255.255.255.255 port 67 interval 3 (xid=0x8eed6f2d)
DHCPREQUEST of 192.168.0.133 on ens33 to 255.255.255.255 port 67 (xid=0x2d6fed8e)
DHCPOFFER of 192.168.0.133 from 192.168.0.1
DHCPACK of 192.168.0.133 from 192.168.0.1
/sbin/dhclient-script: 7: [: =: unexpected operator
bound to 192.168.0.133 -- renewal in 39858 seconds.
```

/etc/network/interfaces
```
# This file describes the network interfaces available on your system# and how to activate them. For more information, see interfaces(5).


source /etc/network/interfaces.d/*


# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto ens33
iface ens33 inet dhcp
```


systemctl status networking.service
```
&#9679; networking.service - Raise network interfaces   Loaded: loaded (/lib/systemd/system/networking.service; enabled; vendor preset: enabled)
  Drop-In: /run/systemd/generator/networking.service.d
           &#9492;&#9472;50-insserv.conf-$network.conf
   Active: active (exited) since Mon 2017-06-26 13:53:10 CEST; 1h 1min ago
     Docs: man:interfaces(5)
  Process: 528 ExecStart=/sbin/ifup -a --read-environment (code=exited, status=0/SUCCESS)
  Process: 518 ExecStartPre=/bin/sh -c [ "$CONFIGURE_INTERFACES" != "no" ] && [ -n "$(ifquer
 Main PID: 528 (code=exited, status=0/SUCCESS)
   CGroup: /system.slice/networking.service


Jun 26 13:53:07 server systemd[1]: Starting Raise network interfaces...
Jun 26 13:53:08 server ifup[528]: /sbin/ifup: waiting for lock on /run/network/ifstate.ens33
Jun 26 13:53:10 server systemd[1]: Started Raise network interfaces.
```

---

### Post by steeldriver on 2017-06-26
What DHCP client are you using - what does 

```

dpkg -S /sbin/dhclient-script

```

say? can you post the first few lines of the script e.g.

```

head /sbin/dhclient-script

```

FWIW on my 16.04 system (running isc-dhcp-client) line 7 is simply a comment. 

(The error you are seeing is the classic "unquoted empty shell variable in a test" e.g.

```

$ sh -c 'foo= ; [ $foo = bar ]'
sh: 1: [: =: unexpected operator

```
)

---

### Post by erik5678 on 2017-06-27
First one produces an error, second one is a comment on line 7. Weird.

dpkg -s /sbin/dhclient-script
```
dpkg-query: error: --status needs a valid package name but '/sbin/dhclient-script' is not: illegal package name in specifier '/sbin/dhclient-script': must start with an alphanumeric character

Use --help for help about querying packages.

```

head /sbin/dhclient-script
```
#!/bin/sh

# Explicitly set the PATH to that of ENV_SUPATH in /etc/login.defs and unset
# various other variables. We need to do this so /sbin/dhclient cannot abuse
# the environment to escape AppArmor confinement via this script
# (LP: #1045986). This can be removed once AppArmor supports environment
# filtering (LP: #1045985)
export PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
export ENV=
export BASH_ENV=

```

---

### Post by steeldriver on 2017-06-27
Please make sure you use an upper-case S in the dpkg command

```

dpkg [COLOR=#0000ff]**-S**[/COLOR] /sbin/dhclient-script

```

---

### Post by erik5678 on 2017-06-27
Oh yeah. Sorry! Didn't look hard enough apparently ](*,)

dpkg -S /sbin/dhclient-script
```
isc-dhcp-client: /sbin/dhclient-script
```

---

### Post by steeldriver on 2017-06-27
Hmm, so it looks like your system is running the isc-dhcp-client - but the /sbin/dhclient-script may be an older version?

And in any case, I don't see anything in line 7 that could explain the error

The only thing I can suggest is maybe reinstalling that package?

---

### Post by erik5678 on 2017-06-27
I reinstalled the package, still the same error.

There is a discussion about this error on the debian bug tracker ([https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=793064](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=793064)) but the real issue has not been found it seems.

It's weird that I get the error on just one of my VM's when I have several upgraded from 14.04.5 to 16.04.2. Of course, one VM failed the upgrade completely, twice, and had to be reinstalled fresh, so these upgrades doesn't seem to be too smooth all the time. This is however the only issue left with this machine (that I am currently aware of :tongue:).

---

### Post by dredkin on 2017-07-13
> **erik5678 said:**
> I reinstalled the package, still the same error.

There is a discussion about this error on the debian bug tracker ([https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=793064](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=793064)) but the real issue has not been found it seems.

It's weird that I get the error on just one of my VM's when I have several upgraded from 14.04.5 to 16.04.2. Of course, one VM failed the upgrade completely, twice, and had to be reinstalled fresh, so these upgrades doesn't seem to be too smooth all the time. This is however the only issue left with this machine (that I am currently aware of :tongue:).

Hello! I've just run into the same issue, and in my case that was an error in Dyn DNS client script, file ***/etc/dhcp/dhclient-exit-hooks.d/ddclient***
```
#!/bin/sh
# /etc/dhcp/dhclient-exit-hooks.d/ddclient - exit hook for dhclient

[ -x /usr/sbin/ddclient ] || exit 0
[ -f /etc/default/ddclient ] || exit 0
. /etc/default/ddclient
[ $run_dhclient = "true" ] || exit 0 <<< bug

case $reason in
    BOUND | RENEW | REBIND)
        /usr/bin/logger -t dhclient $reason, updating IP address with ddclient
        /usr/sbin/ddclient -daemon=0 -syslog > /dev/null 2>&1
        ;;
    *)
        ;;
esac


```
There is a bug in this script on line 7. You have set quotation marks around the variable so the line looks like this:
```
[ "$run_dhclient" = "true" ] || exit 0
```
After that the bug is gone!

---

### Post by erik5678 on 2017-07-13
Yep, that did it!

Thanks dredkin!

---

