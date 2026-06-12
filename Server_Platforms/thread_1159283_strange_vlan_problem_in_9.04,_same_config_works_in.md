---
title: "strange vlan problem in 9.04, same config works in 8.10"
date: 2009-05-14
forum: Server Platforms
---

### Post by Gourgi on 2009-05-14
ok here is the interesting situtation i'm stuck with :

we have several ubuntu servers(8.04 and 8.10) in our internal network that are in 192.168.0.x subnet.
We also use 192.168.1.x and 192.168.2.x subnets for our clients. We also administer our server using ssh from subnet 192.168.2.x. An layer-3 switch does routing between subnets.
All servers have vlans active and working and use samba for their services.
Recently we purchased another server, i installed 9.04 on it and first thing to do was to copy the /etc/network/interfaces and smb.conf from another server to the newest (changed the ip addresses of course :) ) and installed vlan package.
so let's see the problem :
```
$sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...
 * if-up.d/mountnfs[eth0]: waiting for interface vlan2 before doing NFS mounts
 * if-up.d/mountnfs[eth0]: waiting for interface vlan1 before doing NFS mounts
Set name-type for VLAN subsystem. Should be visible in /proc/net/vlan/config
Added VLAN with VID == 3 to IF -:eth0:-
 * if-up.d/mountnfs[vlan2]: waiting for interface vlan1 before doing NFS mounts
Set name-type for VLAN subsystem. Should be visible in /proc/net/vlan/config
Added VLAN with VID == 2 to IF -:eth0:-
   ...done.

```
 after that i loose connection from any other location except 192.168.0.x subnet. while networking restarts correctly and all vlans are up
```
$cat /proc/net/vlan/config 
VLAN Dev name    | VLAN ID
Name-Type: VLAN_NAME_TYPE_PLUS_VID_NO_PAD
vlan2          | 3  | eth0
vlan1          | 2  | eth0
```

so my clients (samba) or even me (ssh) **can't connect **to the 9.04 server **unless** i physically go and **bring the vlans down** :
```
$ ifdown vlan1
$ ifdown vlan2

```
route -n is as expected.
/etc/network/interfaces is the same as in the other ubuntu machines.
i don't have any network mount point in my fstab (as networking thinks ...)


modules are different (maybe the problem is there ??) 

in 9.04
```
$lsmod |grep 8021
8021q                  31776  0 
garp                   17792  1 8021q

```

in 8.04 or 8.10
```
$lsmod |grep 8021
8021q                  31776  0 

```

i tried to remove garp but obvisouly i can't.

also the if-up.d/mountnfs script is different :

in 9.04
```

#! /bin/sh
# Description:       Now that TCP/IP is configured, mount the NFS file
#                    systems in /etc/fstab if needed. If possible,
#                    start the portmapper before mounting (this is needed for
#                    Linux 2.1.x and up).
#
#                    Also mounts SMB filesystems now, so the name of
#                    this script is getting increasingly inaccurate.

PATH=/sbin:/bin
. /lib/init/vars.sh

. /lib/lsb/init-functions
. /lib/init/mount-functions.sh

do_start() {
	[ -f /etc/fstab ] || return
	#
	# Read through fstab line by line. If it is NFS, set the flag
	# for mounting NFS file systems. If any NFS partition is found and it
	# not mounted with the nolock option, we start the portmapper.
	# 
	# If any sec={krb5,krb5i,krb5p} option is given, or any of the file
	# systems are nfs4, we'll need to start rpc.gssd and/or rpc.idmapd too;
	# we'll leave that to nfs-common.
	#

	exec 9<&0 </etc/fstab

	start_nfs=no
	NETFS=""
	NETDEV=""
	while read DEV MTPT FSTYPE OPTS REST
	do
		case "$DEV" in
		  ""|\#*)
			continue
			;;
		esac
		case "$OPTS" in
		  noauto|*,noauto|noauto,*|*,noauto,*)
			continue
			;;
		  _netdev|*,_netdev|_netdev,*|*,_netdev,*)
			NETDEV=yes
			;;
		esac
		case "$FSTYPE" in
		  nfs)
		  	# NFS filsystems normally require statd and portmap. However,
			# if nolock is set, portmap and statd are not required for this
			# file system.
			case "$OPTS" in
			  nolock|*,nolock|nolock,*|*,nolock,*)
			  	# no action
				;;
			  *)
				start_nfs=yes
				;;
			esac

			# However, Kerberos requires gssd, so start nfs-common anyway.
			case "$OPTS" in
			  sec=krb5|*,sec=krb5|sec=krb5,*|*,sec=krb5,*|sec=krb5i|*,sec=krb5i|sec=krb5i,*|*,sec=krb5i,*|sec=krb5p|*,sec=krb5p|sec=krb5p,*|*,sec=krb5p,*)

			  	start_nfs=yes
				;;
			esac
			;;
		  nfs4)
			# NFSv4 requires idmapd, so start nfs-common no matter what the options are.
			start_nfs=yes
			;;
		  smbfs|cifs|coda|ncp|ncpfs|ocfs2|gfs)
			;;
		  *)
			FSTYPE=
			;;
		esac
		if [ "$FSTYPE" ]
		then
			case "$NETFS" in
			  $FSTYPE|*,$FSTYPE|$FSTYPE,*|*,$FSTYPE,*)
				;;
			  *)
				NETFS="$NETFS${NETFS:+,}$FSTYPE"
				;;
			esac
		fi
	done

	exec 0<&9 9<&-

	#
	# Initialize nfs-common (which starts rpc.statd, rpc.gssd
	# and/or rpc.idmapd, and loads the right kernel modules if
	# applicable) if we use Kerberos and/or NFSv4 mounts.
	#
	if [ "$start_nfs" = yes ] && [ -x /etc/init.d/portmap ] && [ -x /etc/init.d/nfs-common ]
	then
		/etc/init.d/portmap start
		/etc/init.d/nfs-common start
	fi

	pre_mountall
	if [ "$NETFS" ]
	then
		mount -a -t$NETFS
	fi
	if [ "$NETDEV" ]; then
		mount -a -O _netdev
	fi
	post_mountall
}

exit_unless_last_interface() {
    grep "^[:space:]*auto" /etc/network/interfaces  | \
	sed -e 's/[ \t]*auto[ \t]*//;s/[ \t]*$//;s/[ \t]/\n/g' | \
	while read i; do
	if [ `grep -c $i /var/run/network/ifstate` -eq "0" ]; then
	    msg="if-up.d/mountnfs[$IFACE]: waiting for interface $i before doing NFS mounts"
	    log_warning_msg "$msg"
	    # Can not pass this as a variable because of the while subshell
	    mkdir /var/run/network/mountnfs_earlyexit 2> /dev/null
	fi
    done
    if [ -d /var/run/network/mountnfs_earlyexit ]; then
	rmdir /var/run/network/mountnfs_earlyexit 2>/dev/null
	exit 0
    fi
}

# Using 'no !=' instead of 'yes =' to make sure async nfs mounting is
# the default even without a value in /etc/default/rcS
if [ no != "$ASYNCMOUNTNFS" ]; then
    # Not for loopback!
    [ "$IFACE" != "lo" ] || exit 0

    # Lock around this otherwise insanity may occur
    mkdir /var/run/network          2>/dev/null || true

    # Wait until all auto interfaces are up before attemting to mount
    # network file systems.
    exit_unless_last_interface

    if mkdir /var/run/network/mountnfs 2>/dev/null ; then
	:
    else
	msg="if-up.d/mountnfs[$IFACE]: lock /var/run/network/mountnfs exist, not mounting"
	log_failure_msg "$msg"
	# Log if /usr/ is mounted
	[ -x /usr/bin/logger ] && /usr/bin/logger -t "if-up.d/mountnfs[$IFACE]" "$msg"
	exit 0
    fi

    on_exit() {
        # Clean up lock when script exits, even if it is interrupted
	rmdir /var/run/network/mountnfs 2>/dev/null || exit 0
    }
    trap on_exit EXIT # Enable emergency handler
    do_start
elif [ yes = "$FROMINITD" ] ; then
    do_start
fi

```
while in 8.10 points in this script in lib
```

#! /bin/sh
# Description:       Mount all networked filesystems defined in /etc/fstab
#                    Start the portmapper before mounting (this is needed for
#                    Linux 2.1.x and up) if necessary.

PATH=/sbin:/bin
. /lib/init/vars.sh

. /lib/lsb/init-functions
. /lib/init/mount-functions.sh

# Some simple locking to ensure we never have two parallel instances
# running, but that each one called will eventually execute serially.

LOCKNAME=/var/run/mountall-net-fs.lock
trap "rm -rf $LOCKNAME" 0
while [ -d $LOCKNAME ] || [ -d /dev/shm/var.run ] || ! mkdir $LOCKNAME 2>/dev/null; do
  sleep 1
done

do_start() {
	[ -f /etc/fstab ] || return
	#
	# Read through fstab line by line. If it is a networked file system,
	# set the flag for mounting networked file systems; 
	# if any NFS are found and are not mounted with the
	# nolock option, we start the portmapper.
	# 
	# If any sec={krb5,krb5i,krb5p} option is given, or any of the file
	# systems are nfs4, we'll need to start rpc.gssd and/or rpc.idmapd 
	# too; we'll leave that to nfs-common.
	#

	exec 9<&0 </etc/fstab

	start_nfs=no
	while read DEV MTPT FSTYPE OPTS REST
	do
		case "$DEV" in
		  ""|\#*)
			continue
			;;
		esac
		case "$OPTS" in
		  noauto|*,noauto|noauto,*|*,noauto,*)
			continue
			;;
		esac
		case "$FSTYPE" in
		  nfs)
		  	# NFS filsystems normally require statd and portmap. 
			# However, if nolock is set, portmap and statd are not 
			# required for this file system.
			case "$OPTS" in
			  nolock|*,nolock|nolock,*|*,nolock,*)
			  	# no action
				;;
			  *)
				start_nfs=yes
				;;
			esac

			# However, Kerberos requires gssd, so start nfs-common 
			# anyway.
			case "$OPTS" in
			  sec=krb5|*,sec=krb5|sec=krb5,*|*,sec=krb5i,*|sec=krb5i|*,sec=krb5i|sec=krb5i,*|*,sec=krb5i,*|sec=krb5p|*,sec=krb5p|sec=krb5p,*|*,sec=krb5p,*)
			  	start_nfs=yes
				;;
			esac
			;;
		  nfs4)
			# NFSv4 requires idmapd, so start nfs-common no matter 
			# what the options are.
			start_nfs=yes
			;;
		  smbfs|cifs|coda|ncp|ncpfs|ocfs2|gfs)
			;;
		  *)
			FSTYPE=
			;;
		esac
		if [ "$FSTYPE" ]
		then
			case "$NETFS" in
			  $FSTYPE|*,$FSTYPE|$FSTYPE,*|*,$FSTYPE,*)
				;;
			  *)
				NETFS="$NETFS${NETFS:+,}$FSTYPE"
				;;
			esac
		fi
	done

	exec 0<&9 9<&-

	#
	# Initialize nfs-common (which starts rpc.statd, rpc.gssd
	# and/or rpc.idmapd, and loads the right kernel modules if
 	# applicable) if we use Kerberos and/or NFSv4 mounts.
	#
	if [ "$start_nfs" = yes ] && [ -x /etc/init.d/portmap ] && [ -x /etc/init.d/nfs-common ]
	then
		/etc/init.d/portmap start
		/etc/init.d/nfs-common start
	fi

	if [ "$NETFS" ]
	then
		pre_mountall
		mount -a -t$NETFS 
		post_mountall
	fi
}

do_start

:

```

i also tried removing /etc/network/if-up.d/mountnfs but nothing changes ...

here is my /etc/network/interfaces:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
        iface eth0 inet static
        address 192.168.0.17
        netmask 255.255.240.0
        broadcast 192.168.15.255
        gateway 192.168.0.1
### vlans
auto vlan2
        iface vlan2 inet static
        address 192.168.2.17
        netmask 255.255.255.0
        broadcast 192.168.2.255
        vlan_raw_device eth0

auto vlan1
        iface vlan1 inet static
        address 192.168.1.17
        netmask 255.255.255.0
        broadcast 192.168.1.255
        vlan_raw_device eth0

```

and i also here is my testparm for smb.conf
```

[global]
        unix charset = iso8859-7
        workgroup = SERVERS
        server string = New server
        interfaces = 127.0.0.0/8, eth0
        bind interfaces only = Yes
        security = SHARE
        obey pam restrictions = Yes
        passdb backend = tdbsam
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
        unix password sync = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        name resolve order = wins host bcast
        socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
        load printers = No
        printcap name = /dev/null
        disable spoolss = Yes
        show add printer wizard = No
        domain master = No
        dns proxy = No
        wins server = 192.168.0.1
        panic action = /usr/share/samba/panic-action %d
        printing = bsd
        print command = lpr -r -P'%p' %s
        lpq command = lpq -P'%p'
        lprm command = lprm -P'%p' %j

``` 

i tried adding the vlans at interfaces in smb.conf but that didn't help also.

the most annoying thing is that the same setup works great in 8.04 and 8.10!

so what can possibly be the issue here ?

---

### Post by Gourgi on 2009-05-16
i'm sorry for bumping this, but i haven't reached to a solution yet :(

can someone with working vlans please tell me if this is supposed to happen in 9.04
```
$lsmod |grep 8021
8021q                  31776  0 
garp                   17792  1 8021q
```

---

### Post by netztier on 2009-05-16
> **Gourgi said:**
> An layer-3 switch does routing between subnets.


I know that this probably won't help to solve the given problem - I just want to add some comments, since some things in your post struck me as odd.

If the L3-Switch actually does the routing job between the three subnets, there is no need to have VLANs on the server(s). Just put them into one of the VLANs (best create a VLAN for the servers), and the switch's routing function will forward packets between client VLAN(s) and the server VLAN.

On a server, having multiple IP interfaces into different subnets drags all kinds of complexity and difficulty along:

For every problem that occurs, having to look at the local routing table (regardless if ip forwarding on the box is active or not) is just the start.  

It does not stop at a lot of head-scratching when it comes to side effects for forward and reverse name resolution: How many DNS names/entries are there for a given server, how many IPs to a name? one, two, three? How do you make sure that clients on subnet "A" always get the "A" IP-address for the server? 

What if they get the "B" address - will the traffic flow be asymmetrical? Requests from client to server through the router/L3-Switch, replies from server to client directly out of the server's "B" interface? Now asymmetric traffic flow or split-path routing is not bad as such - but the day someone comes and demands that there be firewalls between clients and servers, you'll curse it.

If you *actually are* in the comfortable situation to have a proper L3-switch, I strongly suggest to remove VLANs from the servers and connect them to untagged switch ports belonging only to one VLAN* ("the server VLAN") - unless you have a very specific reason to run the servers with multiple IP interfaces.



regards

Marc



[SIZE="1"]* an example for a single-VLAN port for an IOS based switch
```
interface gig0/10
 description * Samba Server 2*
 switchport mode access
 switchport access vlan 2
 spanning-tree portfast

```[/SIZE]

---

### Post by gpredrag on 2009-05-17
Also, as far as I know, one shouldn't set an IP address on raw device used for vlans, i.e. you should not use eth0 as an layer 3 interface any more.
I suppose  that eth0 address is in vlan1. My guess you should create vlan1 interface, assign an address and use it.
I beleive that vconfig complains that vlan1 may not be compatible with some switches. I have vlans on my server (not Jaunty), but not vlan1, and raw devices do not have address (that was my understanding, I thought it would never work, but you said it actually did).
Also, I know for certainly that Windows NT (and probably samba) explicitly doesn't recomend multihomed domain controllers, there is problem with browsing.
Maybe you should really consider having separate server vlan, and setting samba to be WINS server.

---

### Post by Gourgi on 2009-05-17
> **netztier said:**
> 
regards

Marc

marc i'd like to thank you for your detailed approach.
i know our network scheme sounds bizarre (and maybe it makes you wonder) but indeed we have a very specific reason for doing this.

> **gpredrag said:**
> Also, as far as I know, one shouldn't set an IP address on raw device used for vlans, i.e. you should not use eth0 as an layer 3 interface any more.
I suppose  that eth0 address is in vlan1. My guess you should create vlan1 interface, assign an address and use it.
I beleive that vconfig complains that vlan1 may not be compatible with some switches. I have vlans on my server (not Jaunty), but not vlan1, and raw devices do not have address (that was my understanding, I thought it would never work, but you said it actually did).
actually both are correct [1] although i would like to take your approach too. sadly i cannot do that on a working network.also *man vlan-interfaces* suggests your way

[1] [http://www.edugeek.net/forums/nix/8907-howto-using-802-1q-vlans-directly-linux.html](http://www.edugeek.net/forums/nix/8907-howto-using-802-1q-vlans-directly-linux.html)


> **gpredrag said:**
> 
Also, I know for certainly that Windows NT (and probably samba) explicitly doesn't recomend multihomed domain controllers, there is problem with browsing.
Maybe you should really consider having separate server vlan, and setting samba to be WINS server.
you are also correct about this but we already solved that problem and it is working as i explained before for the others servers but not for the jaunty server :(

thank you both for reading my endless post above. no answer found so far.
i thinking that the problem is either the garp module or the if-up script.

---

### Post by wirelessmonkey on 2009-05-17
You have multiple vlans on your device, so you need to fix routing.
```
sudo -i
echo "0" > /proc/sys/net/ipv4/conf/all/rp_filter

```
If that doesn't work by itself, make sure your routing table is set properly, in your case I think that 192.168.0.1 should be the default route, and if it's not, you can set it win
```
 sudo route add default gw 192.168.0.1 
```

Now, I have to admit that I have only done this in Gentoo, not Ubuntu, but I have 2 servers that sit on multiple vlans, so hopefully my experience is helpful.

---

### Post by HermanAB on 2009-05-18
Hmm, you are trying to debug multiple things at the same time.  First get the VLANs and routing figured out, then worry about Samba.

---

### Post by netztier on 2009-05-18
> **gpredrag said:**
> I beleive that vconfig complains that vlan1 may not be compatible with some switches. 

It is common practice not to run end systems (i.e. Servers) in VLAN 1 at all in a 802.1q environment, and to use VLAN 1 as the default/native VLAN on a 802.1q link. You may choose to run the default/native VLAN with or without tags on a given 802.1q link between two devices, as long as both ends of the link have the same config in that regard.

Some inter-switch protocols such as CDP, VTP, DTP (in the Cisco world) and the likes run on the native VLAN, and by keeping the servers out of it, you can reduce the operational and security risk exposure for Ethernet-based attacks to your infrastructure [SIZE="1"](to properly secure your Layer 2, it will take a few more measures than just keeping servers out of the native VLAN, of course)[/SIZE]

There are (used to be?) switch products that do not support per-VLAN-spanning-tree; they run only a single spanning tree instance leading to one common topology for all VLANs - I would bet that this STP instance also uses the native VLAN by default to exchange BDPU packets between devices.

regards

Marc

---

### Post by Gourgi on 2009-05-21
> **wirelessmonkey said:**
> You have multiple vlans on your device, so you need to fix routing.
```
sudo -i
echo "0" > /proc/sys/net/ipv4/conf/all/rp_filter

```

although route -n seemed it was ok, and the gateway was configured correctly, when i added 0 > rp_filter magically everything started to work again. thanks for this wirelessmonkey.
to keep this setting among reboots should i use /etc/sysctrl.conf or the /etc/network/interfaces syntax ? 
*i copy from the *vlan-interfaces* manpage:
> ip-rp-filter 0|1|2
              Set the return path filter for this  specific  interface. This also works on plain ethernet like devices.


---

### Post by wirelessmonkey on 2009-05-22
The problem lies in the way routing works... with multiple VLANS on 1 physical interface, the machine doesn't know which interface to listen on. rp_filter forces it to listen on the default gateway interface to prevent accidental nastiness. 
I wrote an init script to make sure mine is set properly at startup.

---

