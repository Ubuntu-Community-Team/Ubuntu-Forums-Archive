---
title: "Problems with '/etc/networking/interfaces'"
date: 2006-04-11
forum: Server Platforms
---

### Post by jsteidl on 2006-04-11
Hello all,

finally i managed to switch my fileserver from Gentoo to Ubuntu and (too bad) ran into some problems. I haven't used a Debian-System before (at least not as a server) so i am not common with the configuration-files.

I am feeling really stupid by asking this here :-/

My installation is Ubuntu Server 6.04 (flight 6) and i want the Server to use a certain ip (who guessed? ;))

This is what i want:

IP:192.168.0.100
Gateway: 192.168.0.1
Netmask: 255.255.255.0
Nameserver: 217.237.151.161

So i tried to configure this in '/etc/network/interfaces' and this is what it looks like:

```
iface eth0 inet static
        adress 192.168.0.100
        netmask 255.255.255.0
        gateway 192.168.0.1
```

but i get an unconfigured eth0 after restarting and that is not really what i wanted. ;)

Sorry, but i am only used to the Gentoo-Configure-Scripts and that seems to be a bit more complicated.

I am thankfull for any advice you can give me!

---

### Post by audax321 on 2006-04-11
Does the end of the file have a line saying:

```
auto eth0
```

I believe that will cause the card to auto-configure at boot. Also, during runtime, you can bring the card up and down using:

```
sudo ifup eth0
```
and
```
sudo ifdown eth0
```

Hope this helps.

---

### Post by jsteidl on 2006-04-11
Okay, thanks for the reply in the first place!
i checked for "auto eth0" and its there... a line above the config part.

i tried to bring it up manually with "ifup eth0" but i got this message:
```

root@hive:~# ifup eth0
Don't seem to be have all the variables for eth0/inet.
Failed to bring up eth0.
```


Any ideas?

P.S.: I also wanted to ask if this is even the right place to do this or if there is another possibility to configure the NIC at startup.

---

### Post by s7eam on 2006-04-11
Well here's mine network configuration. Copy/Paste here so I hope this will help you.

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth1

iface eth1 inet static
  address 192.168.0.100
  netmask 255.255.255.0
  gateway 192.168.0.1


auto eth1

```

---

### Post by s7eam on 2006-04-11
[QUOTE=jsteidl]Hello all,

finally i managed to switch my fileserver from Gentoo to Ubuntu and (too bad) ran into some problems. I haven't used a Debian-System before (at least not as a server) so i am not common with the configuration-files.

I am feeling really stupid by asking this here :-/

My installation is Ubuntu Server 6.04 (flight 6) and i want the Server to use a certain ip (who guessed? ;))

This is what i want:

IP:192.168.0.100
Gateway: 192.168.0.1
Netmask: 255.255.255.0
Nameserver: 217.237.151.161

So i tried to configure this in '/etc/network/interfaces' and this is what it looks like:

```
iface eth0 inet static
        adress 192.168.0.100
        netmask 255.255.255.0
        gateway 192.168.0.1
```

but i get an unconfigured eth0 after restarting and that is not really what i wanted. ;)

Sorry, but i am only used to the Gentoo-Configure-Scripts and that seems to be a bit more complicated.

I am thankfull for any advice you can give me![/QUOTE]

I now see that you've misspelled your **address** and not **adress** as you wrote.

---

### Post by jsteidl on 2006-04-11
euuuw!

thanks a lot! That will probably do the trick. I'll try when i've got access to the machine again.

thanks again, jsteidl

EDIT: it worked, thanks for the help. :-)

---

