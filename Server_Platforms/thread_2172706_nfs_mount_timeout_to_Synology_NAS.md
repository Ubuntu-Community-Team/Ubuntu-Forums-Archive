---
title: "nfs mount timeout to Synology NAS"
date: 2013-09-06
forum: Server Platforms
---

### Post by gizmojunkee on 2013-09-06
Hi all,

I have been google'g now for a few days and searched this forum for some Jedi power to enlighten me but I have been unsuccessful in my search for wisdom. Now I hope dearly one of the Jedi Masters here can point me in the right direction.
I have installed several versions of ubuntu up to 13.x (server edition) in a Virtual Machine using parallels and virtualbox. Now my aim is to connect to a nfs - share I have created on my Synology NAS, currently installed the latest version of DSM 4.3 that is supporting nfs4 and fixed a few bugs.

1. Pre Installation Ubuntu Client
nfs-common
portmap
nfs-kernel-server (because I read somewhere that would fix my issue)
and of course I create a local mount point, for this example:
```
sudo mkdir /mnt/asterix
```

2. Configuration on my NAS
I just give you the /etc/export infos from the NAS created out of the GUI setup

```
Asterix> cat exports
/volume1/TEST    192.168.12.*(rw,async,no_wdelay,insecure,no_root_squash,insecure_locks,sec=sys,anonuid=1025,anongid=100)

```

3. Checking Ports and visible mounts
So I am logged into my Ubuntu Server and execute the command: 
```
showmounts -e 192.168.12.23
```

**output:**
```
frontrow@hubble:~$ showmount -e 192.168.12.23
Export list for 192.168.12.23:
/volume1/TEST           192.168.12.*
/volume1/frontrow       192.168.12.*
/volume1/plex_downloads 192.168.12.*
frontrow@hubble:~$

```

Next I check the ports locally and remotely just to be sure I have nfs3/4 support
**locally:**
```
rontrow@hubble:~$ rpcinfo
   program version netid     address                service    owner
    100000    4    tcp6      ::.0.111               portmapper superuser
    100000    3    tcp6      ::.0.111               portmapper superuser
    100000    4    udp6      ::.0.111               portmapper superuser
    100000    3    udp6      ::.0.111               portmapper superuser
    100000    4    tcp       0.0.0.0.0.111          portmapper superuser
    100000    3    tcp       0.0.0.0.0.111          portmapper superuser
    100000    2    tcp       0.0.0.0.0.111          portmapper superuser
    100000    4    udp       0.0.0.0.0.111          portmapper superuser
    100000    3    udp       0.0.0.0.0.111          portmapper superuser
    100000    2    udp       0.0.0.0.0.111          portmapper superuser
    100000    4    local     /run/rpcbind.sock      portmapper superuser
    100000    3    local     /run/rpcbind.sock      portmapper superuser
    100024    1    udp       0.0.0.0.157.223        status     106
    100024    1    tcp       0.0.0.0.193.100        status     106
    100024    1    udp6      ::.230.82              status     106
    100024    1    tcp6      ::.184.9               status     106
    100021    1    udp       0.0.0.0.171.117        nlockmgr   superuser
    100021    3    udp       0.0.0.0.171.117        nlockmgr   superuser
    100021    4    udp       0.0.0.0.171.117        nlockmgr   superuser
    100021    1    tcp       0.0.0.0.231.52         nlockmgr   superuser
    100021    3    tcp       0.0.0.0.231.52         nlockmgr   superuser
    100021    4    tcp       0.0.0.0.231.52         nlockmgr   superuser
    100021    1    udp6      ::.235.123             nlockmgr   superuser
    100021    3    udp6      ::.235.123             nlockmgr   superuser
    100021    4    udp6      ::.235.123             nlockmgr   superuser
    100021    1    tcp6      ::.225.206             nlockmgr   superuser
    100021    3    tcp6      ::.225.206             nlockmgr   superuser
    100021    4    tcp6      ::.225.206             nlockmgr   superuser
frontrow@hubble:~$

```

[B]remotely:
[/B]```
frontrow@hubble:~$ rpcinfo -p 192.168.12.23
   program vers proto   port  service
    100000    4   tcp    111  portmapper
    100000    3   tcp    111  portmapper
    100000    2   tcp    111  portmapper
    100000    4   udp    111  portmapper
    100000    3   udp    111  portmapper
    100000    2   udp    111  portmapper
    100005    1   udp    892  mountd
    100005    1   tcp    892  mountd
    100005    2   udp    892  mountd
    100005    2   tcp    892  mountd
    100005    3   udp    892  mountd
    100005    3   tcp    892  mountd
    100021    1   udp  54322  nlockmgr
    100021    3   udp  54322  nlockmgr
    100021    4   udp  54322  nlockmgr
    100021    1   tcp  60625  nlockmgr
    100021    3   tcp  60625  nlockmgr
    100021    4   tcp  60625  nlockmgr
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100024    1   udp  52085  status
    100024    1   tcp  45308  status
frontrow@hubble:~$

```

4. Now that looks all good to me, so I try to mount my nfs share manually:
```
sudo mount -v -t nfs 192.168.12.23:/volume1/TEST /mnt/asterix
```

and this is what I get:
```
frontrow@hubble:~$ sudo mount -v -t nfs 192.168.12.23:/volume1/TEST /mnt/asterix
[sudo] password for frontrow:
mount.nfs: timeout set for Fri Sep  6 10:27:26 2013
mount.nfs: trying text-based options 'vers=4,addr=192.168.12.23,clientaddr=192.168.12.90'
mount.nfs: mount(2): Connection timed out
mount.nfs: Connection timed out
frontrow@hubble:~$

```
Now the real odd thing is if I execute the exact same line on my Macbook it works within a few seconds.
I have tried this now with several linux distributions, (Redhat, Fedora, Mint) in a VM and as well full install on a PC. All show the same issue.
I would appreciate some advice, I am hitting a wall here.

PS: just in case, I am not interested in SMB (CIFS) mounts that is not feasible for my requirements. Save your beans.

---

### Post by gizmojunkee on 2013-09-07
Hi again,

so I added the -vvv flag and here is a bit more comprehensive output.
Hope that triggers anyone's Memory. Thanks in advance.

```

sudo mount -vvv -t nfs4 192.168.12.23:/volume1/TEST /mnt/asterix/
mount: fstab path: "/etc/fstab"
mount: mtab path:  "/etc/mtab"
mount: lock path:  "/etc/mtab~"
mount: temp path:  "/etc/mtab.tmp"
mount: UID:        0
mount: eUID:       0
mount: spec:  "192.168.12.23:/volume1/TEST"
mount: node:  "/mnt/asterix/"
mount: types: "nfs4"
mount: opts:  "(null)"
mount: external mount: argv[0] = "/sbin/mount.nfs4"
mount: external mount: argv[1] = "192.168.12.23:/volume1/TEST"
mount: external mount: argv[2] = "/mnt/asterix/"
mount: external mount: argv[3] = "-v"
mount: external mount: argv[4] = "-o"
mount: external mount: argv[5] = "rw"
mount.nfs4: timeout set for Sat Sep  7 16:42:14 2013
mount.nfs4: trying text-based options 'addr=192.168.12.23,clientaddr=192.168.12.90'
mount.nfs4: mount(2): Connection timed out
mount.nfs4: Connection timed out
frontrow@hubble:~$

```

---

### Post by Bucky Ball on 2013-09-07
*Thread moved to **Server Platforms**.*

You might have more luck here.

---

### Post by Bucky Ball on 2013-09-07
*Thread moved to **Server Platforms**.*

You might have more luck here.

---

### Post by M!K3_$ on 2013-09-08
Have you tried paring back your export options to a bare minimum? Those export options should all be valid, but it's worth a shot. 
Also, any firewall which might be blocking this connection (iptables)? I have a feeling this isn't the issue though because rpcbind can connect.

---

### Post by gizmojunkee on 2013-09-08
Hi,

first of all, many thanks that you took the time to answer. Much appreciated. I did actually check the firewall and for me it looked good. If I do a nmap from the Server I get the following output:

```
frontrow@hubble:~$ sudo nmap -PO 192.168.12.23
[sudo] password for frontrow: 


Starting Nmap 6.00 ( http://nmap.org ) at 2013-09-08 14:38 CEST
Nmap scan report for Asterix (192.168.12.23)
Host is up (0.00022s latency).
Not shown: 986 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
80/tcp   open  http
111/tcp  open  rpcbind
139/tcp  open  netbios-ssn
161/tcp  open  snmp
445/tcp  open  microsoft-ds
515/tcp  open  printer
548/tcp  open  afp
631/tcp  open  ipp
873/tcp  open  rsync
2049/tcp open  nfs
3260/tcp open  iscsi
5000/tcp open  upnp
5432/tcp open  postgresql
MAC Address: 00:11:32:18:A8:D7 (Synology Incorporated)


Nmap done: 1 IP address (1 host up) scanned in 0.06 seconds
frontrow@hubble:~$ 

```

For the export, I have not tried anything as "normally" you would not SSH into the NAS but use the GUI.
Also bear in mind that with the same settings it works like a charm from my mac.

I will make a quick change to the export and test it tho. I really am stumped here, something must cause the timeout.
I actually tried out autofs as someone suggested it works well with Synology NAS, however I get the same issue... timeout.

---

### Post by gizmojunkee on 2013-09-08
I got it working now, well I don't understand it yet but I will do some research to get on the bottom of it. So what I did was thinking out of the box and changing all the Network settings on the Virtual Machine (Parallels). I chose a different Network interface I was provided (Realtek RTL8029AS) with Type Shared Network. I then changed the Network Settings of the Ubuntu Server from Static IP to DHCP. After the reboot it connected in a couple of seconds just fine. When I checked the Network Settings I find that I am on a different Subnet... which is one of the parts I still don't get. I will update when I find some answers.

*may the force be with you*

---

### Post by papibe on 2013-09-08
Hi gizmojunkee.

Latest Ubuntu versions try to mount an NFS export first using version 4, before defaulting to version 3. My guess is the Synology box is still using v3.

You may reduce the mounting time by forcing to use version3 (either option nfsvers or vers)
```
sudo mount -v -t nfs 192.168.12.23:/volume1/TEST /mnt/asterix **-onfsvers=3**
```
Hope it helps.
Regards.

---

### Post by krichter722 on 2014-03-23
> **gizmojunkee said:**
> I chose a different Network interface I was provided (Realtek RTL8029AS) with Type Shared Network. 

Hi gizmojunkee,
Can you maybe point out what type of network a Shared Network is (bridge, NAT, host-only, etc.)?

---

### Post by krichter722 on 2014-03-28
I figured it out by solving another issue. I forgot to forward port 111 besides 2049. This is also a good explanation for the timeouts. This should make things work in a NAT network (in VirtualBox I use NAT-Network (which is different from NAT - which should work, too)).

---

