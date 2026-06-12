---
title: "please help! (/etc/network/interfaces)"
date: 2005-11-10
forum: Server Platforms
---

### Post by tsumi on 2005-11-10
OK. so i have a server install which i set up to do dhcp (maybe it happened magicly, i dont know). I need to have the machine on a static ip. i found threads refering to this and ended up with an interfaces file that looks like this:

tsumi@sentry:~$ cat /etc/network/interfaces
 This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface

auto eth0
iface eth0 inet static
address 192.168.100.31
netmask 255.255.255.0
broadcast 192.168.100.255
gateway 192.168.100.1

#iface eth0 inet dhcp
tsumi@sentry:~$


problem is when the machine boots, it does not automagicly start the network connection... i am able to start it by using:

ifconfig eth0 192.168.100.31
route add default gw 192.168.100.1
ifconfig eth0 up

but i have to do that by hand which wont fly as this machine is running nagios as a network monitor. please let me know what im doing wrong here. thanks in advance!

---

### Post by LordHunter317 on 2005-11-10
The interface should be coming up at boot, no problems.  I don't see anything wrong in your stanzas that would prevent that.  You did edit the file as root and save it, right?

---

### Post by tsumi on 2005-11-10
Yupyup:

tsumi@sentry:/etc/network$ ls -la
total 36
drwxr-xr-x   7 root root 4096 2005-11-10 12:40 .
drwxr-xr-x  63 root root 4096 2005-11-10 12:41 ..
drwxr-xr-x   2 root root 4096 2005-10-04 08:50 if-down.d
drwxr-xr-x   2 root root 4096 2005-04-05 06:08 if-post-down.d
drwxr-xr-x   2 root root 4096 2005-10-04 08:49 if-pre-up.d
lrwxrwxrwx   1 root root   11 2005-10-04 08:49 ifstate -> run/ifstate
drwxr-xr-x   2 root root 4096 2005-10-04 08:50 if-up.d
-rw-r--r--   1 root root  544 2005-11-10 12:40 interfaces
-rw-r--r--   1 root root   45 2005-10-04 08:48 options
drwxr-xr-x   2 root root 4096 2005-11-10 12:41 run
tsumi@sentry:/etc/network$


Anything wrong with the permissions? What else could I look at?

---

### Post by ssam on 2005-11-10
the permissions match mine

if it is set up in /etc/network/interfaces you shoudl only need to run
```
sudo ifup eth0
```
to bring the interface up.

i think the init scrips effectively run that command to bring the interfaces up. so if you try it (after a boot, but before your method) and get an error message that could be a clue.

---

### Post by tsumi on 2005-11-10
tried that, i got something to the effect of

"/etc/network/interfaces:1: misplaced option"
"ifup could not read the file /etc/network/interfaces" 

(sorry for the lack of the cut/paste, the server is in a server room and that was typed fromt he console)

so it sounds like a permission error, no? or perhaps a problem with the stanzas.. hrmm. i have looked at this file so many times im pretty sure i did not fat finger anything..

---

### Post by ssam on 2005-11-10
ah ha.

you need a # on the first line of

```
/etc/network/interfaces
```

its not commented out so ifup trys to read it, and it cant understand it. prehaps.

otherwise we need to pool ideas with this thread. [http://www.ubuntuforums.org/showthread.php?p=481916&posted=1#post481916](http://www.ubuntuforums.org/showthread.php?p=481916&posted=1#post481916)

---

### Post by tsumi on 2005-11-10
GAAAAAAH.. I read over that freaking file so many times today.. I was so worried about the auctual stanzas that i did not notice my big fat fingers decided to delete a hash. GUH...

Thank you. Oddly, I was talking to my buddy who is a Gentoo head and he noticed the same thing.

THANK YOU EVERYONE!! :) Sorry for the PEBKAC issue.

PS: (just so you can share in the victory with me a bit...)

root@sentry:/etc/network # reboot

Broadcast message from root (pts/0) (Thu Nov 10 15:05:31 2005):

The system is going down for reboot NOW!
root@sentry:/etc/network # Connection to 192.168.100.31 closed by remote host.
Connection to 192.168.100.31 closed.
tsumi@itgimp:~$ ping 192.168.100.31
PING 192.168.100.31 (192.168.100.31) 56(84) bytes of data.
64 bytes from 192.168.100.31: icmp_seq=1 ttl=64 time=1.24 ms
64 bytes from 192.168.100.31: icmp_seq=2 ttl=64 time=0.185 ms

--- 192.168.100.31 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1000ms
rtt min/avg/max/mdev = 0.185/0.716/1.247/0.531 ms
tsumi@itgimp:~$

:D

---

### Post by tsumi on 2005-11-10
PPS: Seriously ssam and LordHunter317. I REALLY do appricate what yall do here. If you are ever in Austin, hit me up and I'll buy ya a beer.

---

### Post by ssam on 2005-11-10
:-)

glad to help. i get just as much of a buzz out of fixing something.

austin, texas? i am in manchester, england, so even if i [dig a hole]("http://grad.icmc.usp.br/~cipriani/bighole.php?lang=en") i dont come out anywhere close :-(

sam

ps. a fun thing for you to try next. on each computer install libnss-mdns and all the avahi packages. edit the host line of 
```
/etc/nsswitch.conf
```
to look like
```
hosts:          files  dns mdns4
```
now you should be able to refere to the computers by their hostname on the command line.
ie
```
tsumi@itgimp:~$ ping sentry.local
```

---

