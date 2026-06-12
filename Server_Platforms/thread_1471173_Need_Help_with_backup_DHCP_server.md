---
title: "Need Help with backup DHCP server"
date: 2010-05-03
forum: Server Platforms
---

### Post by onyxwolf on 2010-05-03
I have a DHCP server that I only mildly trust, but its nice because it is an eBox server (I use it for DNS, DHCP, and smtp relay for my internals). I want it to issue all addresses (simply because I like the way it displays its leases in the WebUI's dashboard), but I want a fail-safe too. I have another server that is strictly an Ubuntu Hardy server (I use it for openVPN and nothing else) so I would like it as my backup dhcp server. I figure I'll install all the dhcp stuff on it and just stop the service (to include a sudo crontab @reboot script to stop it when rebooted) and simple use a sudo crontab script to ping the eBox every 5 minutes to make sure its live, and if not then start the dhcp server.

My questions: If I put the entry in my sudo crontab will the script execute even if no session is currently running (its obviously a server so won't have anyone logged in except for administration)? Also since it is in the root crontab it will be able to start the init.d service without having to sudo it right (IE the script only needs to say "/etc/init.d/dhcp3-server start" not "sudo /etc/init.d/dhcp3-server start")?

---

### Post by onyxwolf on 2010-05-03
The script:

```
#!/bin/bash
ping -c 1 192.168.x.x
if [ $? -eq 1 ]
then
    /etc/init.d/dhcp3-server start
    logger "Primary is Down!!! Started DHCP on Second!"
else
if [ `ps aux | grep dhcp3-server | grep -c -v grep` -gt 0 ]
then
    /etc/init.d/dhcp3-server stop
    logger "Primary has returned to service. Stopped DHCP on Second."
else
    logger "Primary is up. Ping was good!"
fi
fi

```

and my Crontab entries:

```
@reboot /root/dhcpHA.sh
*/5 * * * * /root/dhcpHA.sh
```

---

### Post by KiLaHuRtZ on 2010-05-03
One major problem I see is individual lease databases.  If you look at ISC-DHCPD (Ubuntu's default -- dhcpd) you can setup redundant DHCP servers that communicate with each other at the DB level.  They both run simultaneously and if one goes down, the other continues to run.  When the failed server returns, they exchange DB info and synchronize.  Seamless to the end user.

Although, what you are trying to do should work, it is not the way it should be done.

---

### Post by onyxwolf on 2010-05-03
That's good to know, thank you. For this specific use (my home network, of which I can only stand the Mrs. yelling at me that I broke the internet, for up to 5 mins.) it doesn't need to be truely HA and after looking into the fail-over it seems more complicated then what I want to do for it, not to mention that my "server" is a 7 year old desktop, I don't really want dhcp to be constantly on for it. But I will keep that in mind if I need to use it in the future!

I'll mark as solved once I am able to test this semi-HA script.

---

### Post by KiLaHuRtZ on 2010-05-03
Try this script...

```
#!/bin/bash

# Set up the environment.
SHELL=/bin/bash
PATH=/usr/local/bin:/usr/local/sbin:/usr/bin:/usr/sbin:/bin:/sbin

# Get status of primary DHCP server.
priDhcp=`ping -c 1 192.168.x.x | grep "packets transmitted" | awk -F " " '{print $4}'`

# Get status of secondary DHCP server.
secDhcp="/var/run/dhcp3-server/dhcpd.pid"

# If primary is down, then...
if [[ "$priDhcp" == "0" ]]; then

  logger 'Primary DHCP: down'
  logger 'Secondary DHCP: enabling'
  /etc/init.d/dhcp3-server start

  # If secondary failed to start, then...
  if [[ -f "$secDhcp" ]]; then

    logger 'Secondary DHCP: up'
    exit 0;

  else

    logger 'Secondary DHCP: failed'
    exit 1;

  fi

# If primary and secondary are both up, then...
elif [[ ("$priDhcp" == "1") && (-f "$secDhcp") ]]; then

  logger 'Primary DHCP: up'
  logger 'Secondary DHCP: disabling'
  /etc/init.d/dhcp3-server stop

  # If secondary failed to stop, then...
  if [[ -f "$secDhcp" ]]; then

    logger 'Secondary DHCP: failed'
    exit 1;

  else

    logger 'Secondary DHCP: down'
    exit 0;

  fi

# If everything is OK, then...
else

  logger 'Primary DHCP: up'

fi

exit 0;

#eof
```

Add this to '/etc/crontab'...

```
*/5 * * * * root /root/dhcpHA.sh
```

And to stop the secondary server from ever starting at boot.  Simply rename these files...

```
/etc/rc2.d/[COLOR="Green"]S[/COLOR]40dhcp3-server
/etc/rc3.d/[COLOR="Green"]S[/COLOR]40dhcp3-server
/etc/rc4.d/[COLOR="Green"]S[/COLOR]40dhcp3-server
/etc/rc5.d/[COLOR="Green"]S[/COLOR]40dhcp3-server
```

To these names...

```
/etc/rc2.d/[COLOR="Red"]K[/COLOR]40dhcp3-server
/etc/rc3.d/[COLOR="Red"]K[/COLOR]40dhcp3-server
/etc/rc4.d/[COLOR="Red"]K[/COLOR]40dhcp3-server
/etc/rc5.d/[COLOR="Red"]K[/COLOR]40dhcp3-server
```

---

