---
title: "I need to stop whatever is using port 443"
date: 2006-05-28
forum: Server Platforms
---

### Post by T313C0mun1s7 on 2006-05-28
I have a need to use port 443 for running a remote support application, however I can not start the service as it seem that something else is using the port. I have Dapper installed and am running it as a fully installed desktop. (Ubuntu 6.06 LTS - the Dapper Drake). My asumption is that it would be a webserver serving https, but looking at Synaptic Package Manager it does not look as if Apache is installed.

Does anyone know what might be using this port and how to stop it? My assumptions on the port being in use are because when I try to start the program I get an error that is indicitive of the port already being in use, but if I change the port it works ok.

Thank you in advance.

---

### Post by adwait on 2006-05-28
Try going to Services in the menu to find out the services running on your pc. Also try running
```
nmap localhost
```

This will show if the port is indeed being used. If you find out which service is using that port in the services app, you can simply stop. If not run this command
```
ls /etc/init.d/
```

It will give a list of files. If you see apache or apache2 in it, you can stop it using
```
sudo /etc/init.d/apache(or apache2) stop
```

---

### Post by fdoving on 2006-05-29
To list all open ports and their processes:
```

sudo netstat -lpAinet

```
To get ips without hostnames:
```

sudo netstat -lpnAinet

```

To list only what's using tcp port 443
```

sudo fuser -v 443/tcp

```

You can also use fuser to kill the process at once like this:
```

sudo fuser -vk 443/tcp

```

fuser can also be used for files, as an example:
```

sudo fuser -v /dev/dsp

```
this will list the application using /dev/dsp.


Hope this helps.

- Frode

---

### Post by T313C0mun1s7 on 2006-05-29
I had checked services prior and found nothing of interest.

nmap was not installed, so after installing it I got this:
```
Starting Nmap 4.03 ( http://www.insecure.org/nmap/ ) at 2006-05-29 10:37 MDT
Interesting ports on localhost.localdomain (127.0.0.1):
(The 1672 ports scanned but not shown below are in state: closed)
PORT    STATE SERVICE
25/tcp  open  smtp
631/tcp open  ipp

``` 
The listing of init.d did not show Apache or Apache2, but here is the listing just in case there is something else running that might grap the port.
```

acpid              ifrename                         rc.local
acpi-support       initrd-tools.sh                  rcS
alsa-utils         keymap.sh                        readahead
anacron            klogd                            readahead-desktop
apmd               laptop-mode                      README
atd                linux-restricted-modules-common  reboot
bittorrent         local                            rmnologin
bluez-utils        loopback                         rsync
bootclean.sh       lvm                              screen
bootlogd           makedev                          screen-cleanup
bootmisc.sh        mdadm                            sendsigs
brltty             mdadm-raid                       single
checkfs.sh         module-init-tools                skeleton
checkroot.sh       modutils                         stop-bootlogd
console-screen.sh  mountall.sh                      stop-readahead
cron               mountdevsubfs                    sudo
cupsys             mountnfs.sh                      sysklogd
dbus               mountvirtfs                      udev
dns-clean          mtab                             umountfs
evms               networking                       umountnfs.sh
festival           nvidia-kernel                    umountroot
fetchmail          pcmcia                           urandom
gdm                pcmciautils                      usplash
glibc.sh           postfix                          vbesave
halt               powernowd                        vmware
hostname.sh        powernowd.early                  waitnfs.sh
hotkey-setup       ppp                              x11-common
hplip              pppd-dns                         xorg-common
hwclockfirst.sh    procps.sh
hwclock.sh         rc

``` 
Here is my netstat ports:
```

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State PID/Program name
tcp        0      0 localhost.localdoma:ipp *:*                     LISTEN     5828/cupsd
tcp        0      0 localhost.localdom:smtp *:*                     LISTEN     4893/master
raw        0      0 *:icmp                  *:*                     7          5084/vmnet-natd

``` and IPs:
```

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State PID/Program name
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     5828/cupsd
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN     4893/master
raw        0      0 0.0.0.0:1               0.0.0.0:*               7          5084/vmnet-natd

``` 
It does not look like anything is actually using port 443 then. The problem for me being that I have a older version of the software where I can not change my port, nor do I have $100 for an upgrade. Another user in these forums with the same software had an identical problem to mine and got around it by changing ports. This is not an option for me.

Is it posible that something could be preventing me from opening a listening connection on that port even if a daemon is not currently using it?

---

### Post by fdoving on 2006-05-29
That is not likely. Though binding to ports below 1024 can only be done with root privileges.

---

### Post by T313C0mun1s7 on 2006-05-29
That must be it then. How might I get around this? The program is a Winders program and installed via Crossover Office 5.0.1.  The icons in the application window and desktop point to Crossover Office containers for items such as the desktop and startmenu, with the actual launcher being a script that contains this:
```

#!/bin/sh
exec "/opt/cxoffice/bin/wine" --bottle "win98"  --start "c:/Windows/Desktop/Help Desk VNC Wait for Connection.lnk" "$@"

``` 
It there a way to add sudo to this so it will ask for a password then launch the server?

Thank you.

---

### Post by garyng on 2006-05-30
visudo is the way to modify sudo behaviour.

But if you are sure the program is safe, it is IMO easier just chown root.root for the shell script you have then set the uid bit so anyone can run it as it will automatically escalate to root. "man chmod" for detail.

---

### Post by T313C0mun1s7 on 2006-05-30
Thank you, that is what I needed to hear. I had tried adding sudo and gsudo to the beginning of the exec line hoping it would ask for a password and then run. I also tried using the scripts that come preinstalled for root-nautilus-here and gedit-root as examples to no avail.

I will try this and see what happens. Currently I have it working in Windows under VMWare, but I would really rather not have to go into VMWare any more than needed. Eventually I would like to eliminate it, if just for one reason alone; I don't want to have to keep repointing to new header files everytime I change the kernel. That is more maintainace than any userspace program deserves in my opinion.

Thank you again.

---

### Post by squidward_tentacles on 2006-06-02
OK, Im sure this is a total noob question, but I cannot dissconnect whatever is connected at port 443 myself. Ive tried,
sudo fuser -v 443/tcp <no result> &
sudo fuser -vk 443/tcp <also with no results>
My understanding is that these and <another connection I cant seem to get rid of  running on 9001>, are all associated with tor. My questionable firewall connections are listed as;
192.168.1.100  18.244.0.144  443  HTTPS
192.168.1.100  222.94.11.129 443 HTTPS
192.168.1.100  213.113.27.69 9001 Unknown

none of these connections are listed as tor, in the program colum of firestarter, and despite everything Ive tried I cant get rid of the....Ive tried sudo killall tor, locking the firewall, rebooting and even editing iptables; sudo iptables -A INPUT -s 213.113.27.69 -j DROP for each of the connects, and STILL they are there glaring at me with unspoken menance....can anyone confirm this is normal, or how to close these connections, and what they might be doing there? It would be a great burden off my mind, Thanks!

---

