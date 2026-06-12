---
title: "Help Networking with VMWare"
date: 2008-01-17
forum: Virtualisation
---

### Post by satimis on 2008-01-17
Hi bodhi.zazen,


Ubuntu 7.04 server amd64 (Host OS) (IP addr 192.168.0.10)
CentOS 5 (Guest OS) (IP addr 192.168.0.20)
VMWare (bridge connection)
One NIC (eth0)
Gateway 192.168.0.1


Happy to find this tutorial.  I have been stuck for several days unable to make Internet contact Guest OS.  Guest OS can connect Internet w/o problem.  Internet can't get in Guest OS.


Could you please shed me some light on following points;

1)
On Ubuntu, Host OS
I shall edit /etc/network/interfaces as follow;```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
# auto eth0
# iface eth0 inet static
#        address 192.168.0.10
#        netmask 255.255.255.0
#        network 192.168.0.0
#        broadcast  192.168.0.255
#        gateway 192.168.0.1
brctl addbr br0
auto br0
iface br0 inet static
        address 192.168.0.10
        netmask 255.255.255.0
        broadcast  192.168.0.255
        gateway 192.168.0.1
bridge_ports eth0

```


2)
regarding
> 
Configure your guest. Again I am using 101 in this example, substitute your VE # as necessary.

```
sudo vzctl set 101 --netif_add eth0 --save

# The VE must be running to add the interface to the bridge
sudo  brctl addif br0 veth101.0
sudo vzctl exec 101 dhclient eth0
```

What shall I substitute "101" here.  Guest OS IP addr is "192.168.0.20"


3)
regarding your sample iptables rules.  Whether I need to copy it to both Host OS annd Guest OS identically.


Please advise.  TIA


B.R.
satimis

---

### Post by bodhi.zazen on 2008-01-21
satimis: sorry to be so late getting back to you.

> **satimis said:**
> What shall I substitute "101" here. Guest OS IP addr is "192.168.0.20"

Well, when you started the machine you used :

```
vzctl create xxx --ostemplate <ostmeplate>
```

where xxx = a number (ie 101) ... so use the same number you used to create the VE.

You first start the VE, then you can use :

```
sudo -i

# Create a VE :
 
root@GutsyVZ:~vzctl create 303 --ostemplate debian-4.0-i386-minimal
Creating VE private area (debian-4.0-i386-minimal)
Performing postcreate actions
VE private area was created
root@GutsyVZ:~ #

#Assign an IP :
root@GutsyVZ:~ #vzctl set 303 --ip 192.168.1.33 --hostname Debian.test --nameserver 192.168.1.1 --save

Adding IP address(es): 192.168.1.33
Configure meminfo: 49152
Set hostname: Debian.test
File resolv.conf was modified
Saved parameters for VE 303

#Doneroot@GutsyVZ:~ #ping 192.168.1.33
PING 192.168.1.33 (192.168.1.33) 56(84) bytes of data.
64 bytes from 192.168.1.33: icmp_seq=1 ttl=64 time=0.069 ms
64 bytes from 192.168.1.33: icmp_seq=2 ttl=64 time=0.058 ms

--- 192.168.1.33 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1000ms
rtt min/avg/max/mdev = 0.058/0.063/0.069/0.009 ms
root@GutsyVZ:~ #vzctrl exec 303 ping google.com
-bash: vzctrl: command not found
root@GutsyVZ:~ #vzctl exec 303 ping google.com
PING google.com (64.233.187.99) 56(84) bytes of data.
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=1 ttl=241 time=109 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=2 ttl=241 time=108 ms
```

again xxx is the number you assigned to you VE.

You can :

```
sudo vzlist -a
``` to list your VE

[QUOTE=satimis;4153810]regarding your sample iptables rules. Whether I need to copy it to both Host OS annd Guest OS identically.[/code]

Just the host.

HTH

---

### Post by satimis on 2008-01-22
Hi bodhi.zazen,


Thanks for your advice.


Sorry I made a mistake on my previous posting.  I'm running VMWare on "Ubuntu 7.10 server amd64" NOT OpenVZ.  So I don't have "vzctl" installed.


What I'm trying to fix on sharing your tutorial is "there is only one NIC on this box.  Ubuntu and CentOS (guest OS) on VE are sharing the NIC.  Now CentOS can connect Internet but Internet can't get in CentOS".  Your assistance would be much appreciated.  TIA


B.R.
satimis

---

### Post by bodhi.zazen on 2008-01-22
OK, first I moved your posts out of the OpenVZ thread as it seems to do with VMWare and not OpenVZ.

With VMWare, VMWare should handle networking for you, 

Go under VM -> Settings -> Internet tab

What application are you trying to connect with ? My guess is you need to configure your router to forward apps to your Centos Guest.

---

### Post by satimis on 2008-01-22
> **bodhi.zazen said:**
> With VMWare, VMWare should handle networking for you, 

Go under VM -> Settings -> Internet tab

I suppose "bridged" connection is the answer.  If NO please advise where can I find it.  I selected "bridged" on "vmware-server-console".


> 
What application are you trying to connect with ? My guess is you need to configure your router to forward apps to your Centos Guest.
Apache 2

Port 8080 is now forward to "192.168.0.20" (CentOS IP).  I made this request to ISP because the router is on loan from ISP.  I can't touch it except ISP.  I did reconfirm afterwards my request with ISP to make sure it "correct".

On Ubuntu running "192.168.0.20" can connect Apache 2 Test Page.  But running;

[https://satimis.com:8080](https://satimis.com:8080)
[https://220.232.213.178:8080](https://220.232.213.178:8080) (public IP)
etc.
including "http://....", w/o 8080

unable to connect "Apache 2 Test Page".

(remark: Apache 2 on CentOS is running.  Aparche 2 on Ubuntu stops running)


Edit:


Do I need "bridge-utils" ?  I have it installed already.



B.R.
satimis

---

### Post by bodhi.zazen on 2008-01-22
when you run the (VMWare) installer it sets up a bridged network interface for you, see this link :

[http://www.cyberciti.biz/tips/vmware-on-centos5-rhel5-64-bit-version.html](http://www.cyberciti.biz/tips/vmware-on-centos5-rhel5-64-bit-version.html)

Your server is not responding to a ping, so either your routed is not configured properly or your connection may be fire walled.

Start on your Centos install and start with a ping. If you have a public IP there is no need to block a ping.

---

### Post by satimis on 2008-01-22
> **bodhi.zazen said:**
> when you run the (VMWare) installer it sets up a bridged network interface for you, see this link :

[http://www.cyberciti.biz/tips/vmware-on-centos5-rhel5-64-bit-version.html](http://www.cyberciti.biz/tips/vmware-on-centos5-rhel5-64-bit-version.html)

Hereunder is the notes taken down on running;

$ sudo /usr/bin/vmware-config.pl ```

Making sure services for VMware Server are stopped.

Stopping VMware services:
   Virtual machine monitor done

Configuring fallback GTK+ 2.4 libraries.

In which directory do you want to install the mime type icons? 
[/usr/share/icons] [Enter]

What directory contains your desktop menu entry files? These files have a 
.desktop file extension. [/usr/share/applications] [Enter]

In which directory do you want to install the application's icon? 
[/usr/share/pixmaps] [Enter]

Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] [Enter]

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.20-15-generic/build/include] [Enter]

The module loads perfectly in the running kernel.

Do you want networking for your virtual machines? (yes/no/help) [yes] [Enter]

Configuring a bridged network for vmnet0.

The following bridged networks have been defined:

. vmnet0 is bridged to eth0

All your ethernet interfaces are already bridged.

Do you want to be able to use NAT networking in your virtual machines? (yes/no)
[yes] [Enter]

Configuring a NAT network for vmnet8.

Do you want this program to probe for an unused private subnet? (yes/no/help) 
[yes] [Enter]

Probing for an unused private subnet (this can take some time)...

The subnet 192.168.213.0/255.255.255.0 appears to be unused.

The following NAT networks have been defined:

. vmnet8 is a NAT network on private subnet 192.168.213.0.

Do you wish to configure another NAT network? (yes/no) [no] [Enter]

Do you want to be able to use host-only networking in your virtual machines? 
[yes] [Enter]

Configuring a host-only network for vmnet1.

Do you want this program to probe for an unused private subnet? (yes/no/help) 
[yes] [Enter]

Probing for an unused private subnet (this can take some time)...

The subnet 172.16.77.0/255.255.255.0 appears to be unused.

The following host-only networks have been defined:

. vmnet1 is a host-only network on private subnet 172.16.77.0.

Do you wish to configure another host-only network? (yes/no) [no] [enter]

......
The module loads perfectly in the running kernel.

Please specify a port for remote console connections to use [902] [Enter]

....
Generating SSL Server Certificate

In which directory do you want to keep your virtual machine files? 
[/var/lib/vmware/Virtual Machines] [Enter]

The path "/var/lib/vmware/Virtual Machines" does not exist currently. This 
program is going to create it, including needed parent directories. Is this 
what you want? [yes] [Enter]

Please enter your 20-character serial number.
....
.....

```
I selected NAT.  Later I changed Bridged connection on "vmware-server-console"


> 
Your server is not responding to a ping, so either your routed is not configured properly or your connection may be fire walled.

Oh sorry, the server has been turned off before.  I just restarted it.  This server is for testing.


> 
Start on your Centos install and start with a ping. If you have a public IP there is no need to block a ping.
Performed following test on Ubuntu (Host)


On console-1 (xterm)

$ ssh 192.168.0.20 (CentOS-guest IP addr)```

satimis@192.168.0.20's password: 
Last login: Mon Jan 21 08:42:56 2008

```

[satimis@centos ~]$ ping -c3 192.168.0.20```

PING 192.168.0.20 (192.168.0.20) 56(84) bytes of data.
64 bytes from 192.168.0.20: icmp_seq=1 ttl=64 time=0.020 ms
64 bytes from 192.168.0.20: icmp_seq=2 ttl=64 time=0.293 ms
64 bytes from 192.168.0.20: icmp_seq=3 ttl=64 time=0.078 ms

--- 192.168.0.20 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2001ms
rtt min/avg/max/mdev = 0.020/0.130/0.293/0.117 ms

```

[satimis@centos ~]$ ping -c3 192.168.0.1 (gateway/router IP)```

PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=150 time=0.246 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=150 time=0.003 ms
64 bytes from 192.168.0.1: icmp_seq=3 ttl=150 time=0.202 ms

--- 192.168.0.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2000ms
rtt min/avg/max/mdev = 0.003/0.150/0.246/0.106 ms

```

[satimis@centos ~]$ ping -c3 220.232.213.178(public IP)```

PING 220.232.213.178 (220.232.213.178) 56(84) bytes of data.
64 bytes from 220.232.213.178: icmp_seq=1 ttl=150 time=0.139 ms
64 bytes from 220.232.213.178: icmp_seq=2 ttl=150 time=0.000 ms
64 bytes from 220.232.213.178: icmp_seq=3 ttl=150 time=0.000 ms

--- 220.232.213.178 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 0.000/0.046/0.139/0.065 ms

```

[satimis@centos ~]$ ping -c3 yahoo.com```

PING yahoo.com (216.109.112.135) 56(84) bytes of data.
64 bytes from w2.rc.vip.dcn.yahoo.com (216.109.112.135): icmp_seq=1 ttl=50 time=
46.5 ms
64 bytes from w2.rc.vip.dcn.yahoo.com (216.109.112.135): icmp_seq=2 ttl=50 time=
54.9 ms
64 bytes from w2.rc.vip.dcn.yahoo.com (216.109.112.135): icmp_seq=3 ttl=50 time=
52.5 ms

--- yahoo.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1998ms
rtt min/avg/max/mdev = 46.588/51.357/54.938/3.515 ms

```

[satimis@centos ~]$ ping -c3 192.168.0.10 (Ubuntu IP addr) ```

PING 192.168.0.10 (192.168.0.10) 56(84) bytes of data.
64 bytes from 192.168.0.10: icmp_seq=1 ttl=64 time=0.295 ms
64 bytes from 192.168.0.10: icmp_seq=2 ttl=64 time=0.508 ms
64 bytes from 192.168.0.10: icmp_seq=3 ttl=64 time=0.540 ms

--- 192.168.0.10 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2001ms
rtt min/avg/max/mdev = 0.295/0.447/0.540/0.111 ms

```


Console-2 (xterm)

$ ping -c3 192.168.0.20 (CentOS IP addr)```

PING 192.168.0.20 (192.168.0.20) 56(84) bytes of data.
64 bytes from 192.168.0.20: icmp_seq=1 ttl=64 time=0.627 ms
64 bytes from 192.168.0.20: icmp_seq=2 ttl=64 time=0.139 ms
64 bytes from 192.168.0.20: icmp_seq=3 ttl=64 time=0.150 ms

--- 192.168.0.20 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2004ms
rtt min/avg/max/mdev = 0.139/0.305/0.627/0.227 ms

```

satimis@mail:~$ ping -c3 192.168.0.1(gateway)```

PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=150 time=0.772 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=150 time=0.741 ms
64 bytes from 192.168.0.1: icmp_seq=3 ttl=150 time=0.711 ms

--- 192.168.0.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2000ms
rtt min/avg/max/mdev = 0.711/0.741/0.772/0.033 ms

```

ping works both way


satimis

---

