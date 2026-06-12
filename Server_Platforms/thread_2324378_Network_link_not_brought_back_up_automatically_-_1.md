---
title: "Network link not brought back up automatically - 14.04 Server"
date: 2016-05-13
forum: Server Platforms
---

### Post by Roy_Kleefman on 2016-05-13
I am seeing a rather peculiar issue with regards to my servers network interfaces.
When I have an active network connection on interface em1, and I remove the network cable, I see the following message in /var/log/syslog:
```
kernel: [  194.433266] tg3 0000:01:00.0 em1: Link is down
```
When I then re-insert the cable, the connection is not brought back up again, it stays down.

I've seen this happen with with bonding as well as non-bonded interfaces, and with static & DHCP address configurations.
My current interfaces file has:
```

# Loopback device
auto lo
iface lo inet loopback

# Device em1
auto em1
iface em1 inet dhcp

# Device em2
auto em2
iface em2 inet dhcp

```

My bonding config looks like this:
```

# Loopback device
auto lo
iface lo inet loopback

# Bonding device bond0
auto bond0
iface bond0 inet static
address 172.16.216.51
network 172.16.0.0
netmask 255.255.0.0
broadcast 172.16.255.255
gateway 172.16.10.254
dns-nameservers 192.168.10.1
bond-mode active-backup
bond-miimon 100
bond-slaves none

# Device em1
auto em1
iface em1 inet manual
bond-master bond0
bond-primary em1
bond-primary_reselect failure

# Device em2
auto em2
iface em2 inet manual
bond-master bond0

```

Both produce the same result: I remove the cable, wait for a few seconds, the link is disabled, I re-insert the cable, but the link is not brought back up.

I can't figure out if this is a network driver issue, a mis-match with the network chip, or a general hardware failure. :(

---

### Post by Roy_Kleefman on 2016-05-13
The server I am working with is a Dell R220.

---

### Post by houstonbofh on 2016-05-15
That is odd, and it should be working.  Try booting a Live-CD and see if it works in a normal configuration without bonding.

---

### Post by Roy_Kleefman on 2016-05-17
I just made a live-cd & will try it today.

---

### Post by Roy_Kleefman on 2016-05-17
Using the latest 16.04 live-cd I get the same result on my server; the link is brought down when the cable is removed (apparently there is some kind of timeout before the interface is brought down?) & the link is not being brought back up when the cable is re-inserted.

---

### Post by Roy_Kleefman on 2016-05-17
I found [this]("http://ubuntuforums.org/showthread.php?t=1905244") thread which seems to have the same problem (but was never solved and was about Ubuntu 11.10). I've tried adding the allow-hotplug stanza to my config, but it doesn't seem to work in 14.04.

---

### Post by Roy_Kleefman on 2016-05-17
I also found an inconsistency between executing ifconfig & ip address.
Executing ifconfig lists the network interface em1 as UP, while executing ip address lists the network interface as being down.

---

### Post by Roy_Kleefman on 2016-05-17
I have the same installation running in a VM (VirtualBox) & I see that the link is re-established there (I de-activated the network adapter from the VM settings while it was running & then re-enabled it).
Though there is a difference in the VM environment: in my VM the NIC is of type e1000 whereas in my physical server it is of type tg3...

---

### Post by Roy_Kleefman on 2016-05-17
Upgrading from kernel 3.16.0-30 (which came with the default installation) to 3.16.0-71 (latest kernel available from the repo's) also did not resolve my issues.

---

### Post by Roy_Kleefman on 2016-05-17
I can force the link to get back up by executing
```
sudo ifdown em1 && sudo ifup em1
```
But this is a manual action...

---

### Post by papapig on 2016-05-18
I had a similar problem on an ubuntu 16.04 server.

I don't know why, but I solved by disabling IPv6:

open open /etc/sysctl.conf and add this:

```
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1
```

Then activate it:

```
sudo sysctl -p
```

or reboot.

Maybe you can give it a try...

---

### Post by Roy_Kleefman on 2016-05-19
Unfortunately, disabling IPv6 did not resolve the issue.
Unplugging the cable without IPv6 & then re-inserting the cable resulted in the same result; the link is not automatically brought back.

---

### Post by Roy_Kleefman on 2016-05-20
I've done some digging in the server itself (Dell R220) & found that the BIOS detects the IP link just fine. I can check the status of the NIC's in the BIOS' device settings which correctly shows if the NIC is connected or not.
This does lead me to believe that there is something going wrong in the OS rather than with the server hardware.

---

### Post by Roy_Kleefman on 2016-05-25
Over the last days, I tried a few other things to see if I can find the culprit of this issue:
[LIST]
[*]I tried to install a different OS (OpenSUSE 13.2) on the same server. This OS did not have this issue. 
[*]I've also investigated into trying the [netplugd]("http://manpages.ubuntu.com/manpages/trusty/man8/netplugd.8.html") daemon to see if that offers any help, but it also does not get any updates regarding the link state when the cable is re-inserted into the server. 
[/LIST]
I get the following ouput from netplugd:
```
[FONT=courier new]netplugd[13633]: em1: state ACTIVE flags 0x00011843  UP,BROADCAST,RUNNING,SLAVE,MULTICAST,10000 -> 0x00001803  UP,BROADCAST,SLAVE,MULTICAST[/FONT]
[LEFT][FONT=courier new]netplugd[15277]: /etc/netplug/netplug em1 out -> pid 15277
netplugd[13633]: em1: state OUTING flags 0x00001803 UP,BROADCAST,SLAVE,MULTICAST -> 0x00001802 BROADCAST,SLAVE,MULTICAST[/FONT][FONT=courier new]
netplugd[13633]: em1 state DOWNANDOUT pid 15277 exited status 0[/FONT]
[FONT=courier new]netplugd[15294]: /etc/netplug/netplug em1 probe -> pid 15294[/FONT][FONT=courier new]
netplugd[13633]: em1: state PROBING flags 0x00001002 BROADCAST,MULTICAST -> 0x00001003 UP,BROADCAST,MULTICAST[/FONT]
[/LEFT]
[FONT=courier new]netplugd[13633]: em1: state PROBING_UP pid 15294 exited status 0[/FONT]
```

From what I understand of netplugd is that the daemon listens to kernel events regarding the carrier detect signal on a network interface. Seeing as this daemon does not show the interface as back up, I suspect the kernel event is never raised.
Would this mean there is an issue/bug in the network driver for em1?

---

### Post by Roy_Kleefman on 2016-05-30
Somewhat of a bump.

I understand that this is a forum ran by volunteers in their own time, but I find it kind of hard to believe that nobody has time to help me with this issue over the timespan of two weeks.
This is a major issue for me & I would like to get to the root of it; but I can't do it on my own.

So please, if anybody has an idea, let me know.

---

### Post by houstonbofh on 2016-05-30
I think the reason is that it is a driver issue specific to that nic.  I do not spend much time on nic driver issues, because multi-port nics are cheap. [http://www.amazon.com/Intel-1000-Dual-Server-Adapter/dp/B000BMZHX2](http://www.amazon.com/Intel-1000-Dual-Server-Adapter/dp/B000BMZHX2)  Problem solved.

Now I am not saying that figuring this out is not worthwhile...  But I personally would not spend a lot of time on it.

---

### Post by Roy_Kleefman on 2016-05-31
Well that's the problem. It's certainly easier to get different NIC's  for new systems, but for existing systems at client locations it's not  so easy.

---

### Post by houstonbofh on 2016-05-31
That would also make troubleshooting a bit more difficult! :)

---

### Post by Roy_Kleefman on 2016-05-31
Exactly... Anyway, I have made somewhat of a work-around that we can install remotely; a cronjob that checks every minute if the network is still connected, and if it isn't it tries to bring all interfaces in the configured bond0 interface back up by executing
```

#! /bin/sh

RestoreInterface () {
    logger "Trying to bring $1 back up..."
    /sbin/ifdown $1
    /sbin/ifup $1
}

carrier=`/bin/cat /sys/class/net/bond0/carrier`
if [ $carrier -eq 0 ]; then
    for interface in `grep "Slave Interface" /proc/net/bonding/bond0 | awk {' print $3 '}`; do
        RestoreInterface $interface
    done
fi

```
All neatly packaged in a .deb file.

This is certainly not an ideal solution, but it gives us some breathing room...
I'll pick this issue up at a later time though.

---

