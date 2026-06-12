---
title: "static ip problems: ubuntu reverts back to DHCP on its own"
date: 2008-05-20
forum: Server Platforms
---

### Post by davidshere on 2008-05-20
I've faithfully followed the instructions on changing my server to a static IP address here:
[http://www.howtoforge.com/perfect-server-ubuntu8.04-lts-p3](http://www.howtoforge.com/perfect-server-ubuntu8.04-lts-p3)
and it works fine.  I get a static IP and have internet access. I can access the machine remotely.  The problem I'm having is that after a certain amount of time (about 20 minutes) the computer changes itself back to DCHP.  I can run "sudo /etc/init.d/networking restart" and get the static IP back, but 20 mintues later it changes back to DHCP again.  It happens quite consistently -- I've seen it happen three times now.  Here is my configuration file: (with my IP address starred out)

```
david@nighthawk:~$ more /etc/network/interfaces 
#This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address ***.***.***.104
        netmask 255.255.255.0
        network ***.***.***.0
        gateway ***.***.***.1
        broadcast ***.***.***.255

```

I'm having a problem similar to the one described here:
[http://ubuntuforums.org/showthread.php?t=560064&highlight=goes+back+to+DHCP](http://ubuntuforums.org/showthread.php?t=560064&highlight=goes+back+to+DHCP)
Mine is slightly different, though -- his IP changes back to DHCP after he resets the computer; mine goes back to DHCP after about 20 minutes without a reset.

Any suggestions would be greatly appreciated.

---

### Post by compgeek83 on 2008-05-20
I had a similar problem, I could use dhcp and get online/share files just fine, but when I setup my static address I couldn't get online at all (or share files).  After several times of going back and fourth trying things it finally started working on it's own for no apparent reason....

---

### Post by davidshere on 2008-05-20
I gave it a while to make sure...

rebooting the machine seems to have solved this problem.

---

### Post by Iowan on 2008-05-20
If it hadn't already fixed itself, you could uncomment this section of **/etc/dhcp3/dhclient.conf** and embed your information:
```
#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}
```

---

