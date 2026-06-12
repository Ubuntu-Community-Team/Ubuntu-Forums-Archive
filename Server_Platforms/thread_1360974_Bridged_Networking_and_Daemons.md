---
title: "Bridged Networking and Daemons"
date: 2009-12-21
forum: Server Platforms
---

### Post by super_sport on 2009-12-21
Everyone,
I'm trying to get an odd issue solved when using bridged networking.  I am trying to configure br0 to bridge my eth0 and tap0, for use with openvpn.  Everything seems to work fine, until I restart the server.

It appears that during startup, the bridging doesn't occur immediately, and that the system may take a while to "settle".  During that time, various daemons are starting, but they seem to all fail (to greater or lesser degrees) because there is no valid device/address.

Services that fail include:
 openvpn
 samba
 dhcpd
 
Has anyone dealt with this behavior before?  I can post configs if they'll be helpful, just let me know what you'd like to see.  

Any thoughts y'all can offer would be great,
Stu

---

### Post by BkkBonanza on 2009-12-21
How or at what point in the boot process is the bridge getting configured?
For example, do you have it in /etc/rc.local ?
I believe that gets called last during boot so you would need the bridge to be configured early on before the dependent daemons get started.

---

### Post by super_sport on 2009-12-21
> **BkkBonaza said:**
> How or at what point in the boot process is the bridge getting configured?
For example, do you have it in /etc/rc.local ?
I believe that gets called last during boot so you would need the bridge to be configured early on before the dependent daemons get started.

I haven't changed anything about how the system boots, so whenever the networking starts out of the box is where it's starting now.

I presume that the excerpt (from /etc/init.d/openvpn) below means that openvpn is not supposed to start until after networking is enabled, but I need to dig further into the ubuntu init system to better understand this.

```
### BEGIN INIT INFO
# Provides:          vpn
# Required-Start:    **$network** $local_fs
# Required-Stop:     **$network** $local_fs
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Openvpn VPN service
### END INIT INFO
```

---

### Post by BkkBonanza on 2009-12-21
Are you sure the bridge gets started? 
I thought you had to manually add an "ifup br0" in the boot process to get it to start.
I may be wrong - it's a long since I setup a bridged config.

Regarding order of boot process. Look in /etc/rcN.d/ where N is the runlevel number you are using. Typically 2 on desktop or 3 on server. In there are numeric ordered links to /etc/init.d/ and the order is determined by the numbers, low to high.

---

### Post by super_sport on 2009-12-21
> **BkkBonaza said:**
> Are you sure the bridge gets started? 
I thought you had to manually add an "ifup br0" in the boot process to get it to start.

I am sure that br0 is starting up automatically.  I don't know of anything in particular that I've done to get that to work.  I did have to add some configs to get tap0 to be created.  This is my /etc/network/interfaces file:

```

auto lo br0
iface lo inet loopback

iface br0 inet static 
        pre-up tunctl -t tap0
        post-down tunctl -d tap0
        address 192.168.100.10
        netmask 255.255.255.0
        gateway 192.168.100.1
        bridge_ports eth0 tap0

```Now that I'm in cut and paste mode, here is an example of what I believe to be the delay between "br0 is initially starting", and "br0 is finished with it's startup (dmesg:
```

$ dmesg | grep br0
[   11.302859] br0: port 2(tap0) entering learning state
[   12.812573] br0: port 1(eth0) entering learning state
[   21.550008] br0: no IPv6 routers present
[   26.300011] br0: port 2(tap0) entering forwarding state
[   27.810009] br0: port 1(eth0) entering forwarding state

```If I understand dmesg's output format, then that's 16 seconds between "starting" and "started".  Plenty of time for various daemons to try to start and fail.

---

### Post by super_sport on 2009-12-24
Just wanted to follow up on this:

[LIST]
[*]Does anyone know if the above dmesg output (specifically the numbers in brackets) corresponds to "seconds since some event"
[*]If so, does anyone know why bridging takes so long to "finish"?
[*]Even if you don't, does anyone know how to make services try to start up only *after* bridging is *fully* finished?
[/LIST]

---

### Post by super_sport on 2010-01-04
Hey everyone.  I hope that everybody had a great Christmas and New Year's.  I'm hoping that the lack of answers is just because everyone was spending time with friends and family.

Anyhow, just wanted to bump this thread again and see if there are any "clean" ways to address this issue.  In the meantime, I've written a shell script that is called from rc.local and will attempt to start the failing services until they successfully start.  If that's my only recourse, please let me know, and I'll post the script for everyone's benefit.

---

### Post by BkkBonanza on 2010-01-04
I don't another method. But could be someone who really knows bridge stuff in depth might. I would guess that a script in rc.local could loop with a brief delay and just check the interface with something like "ifconfig br0 | grep up" until it validates and then start the services. This seems efficient enough even if not so "nice". 

Maybe it's possible to hook into udev with a rule to trigger the services startup. I have written udev rules before to trigger on device events. There may be an event tied to the network interface coming up.

If you wanted to explore that then the "udevadm monitor" command while downing/uping the interface (in another terminal) should list any events emitted.

---

### Post by super_sport on 2010-01-04
> **BkkBonaza said:**
> I would guess that a script in rc.local could loop with a brief delay and just check the interface with something like "ifconfig br0 | grep up" until it validates and then start the services. This seems efficient enough even if not so "nice".

This is almost precisely what I've done.  I'll go ahead and post my script(s) for future generations (though I'd still like a "nice" solution, if there is one).

```
cat /etc/rc.local 
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

/usr/local/bin/check.sh
exit 0
``````
cat /usr/local/bin/check.sh
#!/bin/sh

SERVICES="apache2 openvpn dhcp3-server"

for SERVICE in ${SERVICES} ; do
        STATUS="1"

        while [ "${STATUS}" -ne 0 ] ; do 
                SERVICE_SCRIPT="/etc/init.d/${SERVICE}"

                ${SERVICE_SCRIPT} status > /dev/null 2>&1
                STATUS="${?}"

                if [ "${STATUS}" -eq 0 ] ; then
                        echo "The service ${SERVICE} is running."
                else
                        echo "The service ${SERVICE} is NOT running."
                        ${SERVICE_SCRIPT} start
                        sleep 5
                fi

        done
done
```

---

### Post by BkkBonanza on 2010-01-04
I think I know the right way to do this now. I was digging around in upstart for some other reason and it dawned on me this should work for your problem.

Upstart is the system that Ubuntu uses for controlling the init sequence and starts the scripts that bring up services in the traditional sysvinit process, but also supports more sophisticated events as well. There is events for when an interface is up and I think this can be used.

The docs for Upstart are here,
[http://upstart.ubuntu.com/getting-started.html](http://upstart.ubuntu.com/getting-started.html)
[http://upstart.ubuntu.com/wiki/](http://upstart.ubuntu.com/wiki/)

The normal upstart scripts are in /etc/init directory. Normally /etc/init/rc.conf is responsible for starting all the /etc/init.d scripts according to runlevel. But that script doesn't have "interface-up br0" as a condition. I think the idea is to add another script here that uses this condition to trigger the services you want to start.

eg. /etc/init/bridgeup.conf
```

description "Post Bridge Services"

start on interface-up br0

script
  /etc/init.d/apache2 start
  /etc/init.d/openvpn start
  /etc/init.d/dhcp3-server start
end script

```
This could be used to stop them on shutdown too but that isn't likely a problem with the default scripts.

---

### Post by schmud on 2010-05-10
I've got a very similar issue with my WiFi - Ethernet bridge. My server is not starting mpd, postfix and some other services binding to the IP address of br0. 
Is the proposed "bridgeup.conf" really the best way to fix the problem? How does upstart handle all the processes, started by the old-style init scripts? In other words, can upstart handle this case correctly on shutdown? Do I have to remove the runlevel links?

---

### Post by schmud on 2010-05-10
OK. I did another hack seeming a little bit less dirty to me.

changed in /etc/init/rc-sysinit.conf

start on filesystem and net-device-up IFACE=lo
to:
start on filesystem and net-device-up IFACE=lo and net-device-up IFACE=br0

I'm open to better ideas.

---

