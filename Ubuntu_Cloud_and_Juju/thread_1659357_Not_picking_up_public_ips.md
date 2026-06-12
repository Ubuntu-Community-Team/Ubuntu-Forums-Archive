---
title: "Not picking up public ips"
date: 2011-01-03
forum: Ubuntu Cloud and Juju
---

### Post by oldhoot on 2011-01-03
In spite of the eucalyptus.local.conf file appearing correct, my instances are launching with the public ip equal to the local ip.  Any suggestions as to where to look as to why?

---

### Post by raymdt on 2011-01-04
What VNET_MODE do you use?
can you post your eucalyptus.conf , eucalyptus.localconf and /var/run/eucalyptus/net/euca-dhcp.conf ?

If you are sure that the available public's Ip range is unused then override the 
VNET_PUBLICIPS in eucalyptus.conf and restart with CLEAN=1 (may be the Node too).

---

### Post by oldhoot on 2011-01-04
hoot@cloud-master:/etc/eucalyptus$ cat eucalyptus.local.conf
# /etc/eucalyptus/eucalyptus.local.conf

# This file is read and written by euca_conf(8)
# WARNING: You should *never* edit this file directly.

# To modify Eucalyptus parameters, either use euca_conf(8), or
# edit /etc/eucalyptus/eucalyptus.conf according to eucalyptus.conf(5).


# network configuration from the input configuration file
VNET_MODE="MANAGED-NOVLAN"
VNET_SUBNET="172.19.0.0"
VNET_NETMASK="255.255.0.0"
VNET_DNS="169.154.151.130"
VNET_ADDRSPERNET="32"
VNET_PUBLICIPS="172.16.230.201-172.16.230.210"
hoot@cloud-master:/etc/eucalyptus$ cat eucalyptus.conf 
# /etc/eucalyptus/eucalyptus.conf
#
# These are the Ubuntu Enterprise Cloud's default Eucalyptus parameters.

# Affects: All
# See: **NOTE** below
EUCALYPTUS="/"
EUCA_USER="eucalyptus"

# Affects: CLC, Walrus, SC
DISABLE_DNS="Y"
CLOUD_OPTS="-Xmx512m"

# Affects: SC
DISABLE_EBS="N"
DISABLE_ISCSI="N"

# Affects: CC, NC
# See: **NOTE** below
ENABLE_WS_SECURITY="Y"
LOGLEVEL="DEBUG"
VNET_PUBINTERFACE="eth0"
VNET_PRIVINTERFACE="eth1"
VNET_MODE="MANAGED-NOVLAN"

# Affects: CC
# See: **NOTE** below
CC_PORT="8774"
SCHEDPOLICY="ROUNDROBIN"
POWER_IDLETHRESH="300"
POWER_WAKETHRESH="300"
NC_SERVICE="axis2/services/EucalyptusNC"
VNET_DHCPDAEMON="/usr/sbin/dhcpd3"
VNET_DHCPUSER="dhcpd"
DISABLE_TUNNELLING="N"
NODES=""
VNET_ADDRSPERNET="32"
VNET_SUBNET="172.1.0.0"
VNET_NETMASK="255.255.255.0"
VNET_DNS="172.16.230.115"
VNET_PUBLICIPS="172.16.230.201-172.16.230.210"

# Affects: NC
NC_PORT="8775"
HYPERVISOR="kvm"
MANUAL_INSTANCES_CLEANUP=0
VNET_BRIDGE="br0"
INSTANCE_PATH="/var/lib/eucalyptus/instances/"
USE_VIRTIO_NET="0"
USE_VIRTIO_DISK="1"
USE_VIRTIO_ROOT="0"
#MAX_MEM=2048
#MAX_CORES="2"
#MAX_DISK="100"

##########################################################################
#
# Administrative overrides and customizations may go below, in accordance
# with the manpage for eucalyptus.conf(5).
#
# However, to modify Eucalyptus parameters, you are advised to use
# euca_conf(8), which will update eucalyptus.local.conf(5) and ensure
# smooth package upgrades.
#
# **NOTE**: To activate changes of these parameters on a CC, you must:
#           sudo restart eucalyptus-cc CLEAN=1
#           HOWEVER, if you do this, all currently running virtual
#           machines in this cluster will lose network connectivity.
#
##########################################################################


hoot@cloud-master:/etc/eucalyptus$ cat /var/run/eucalyptus/net/euca-dhcp.conf
# automatically generated config file for DHCP server
default-lease-time 1200;
max-lease-time 1200;
ddns-update-style none;

shared-network euca {
subnet 172.19.1.0 netmask 255.255.255.224 {
  option subnet-mask 255.255.255.224;
  option broadcast-address 172.19.1.31;
  option domain-name-servers 169.154.151.130, 172.19.1.1;
  option routers 172.19.1.1;
}

host node-172.19.1.2 {
  hardware ethernet D0:0D:31:64:06:9D;
  fixed-address 172.19.1.2;
}
}

---

### Post by raymdt on 2011-01-04
Hi your config is a bit tricky,
you should first try to make your UEC work before dealing with complex network settings.

What ist the right DNS Address? ( 172.16.230.115 or 169.154.151.130)
Can you use another ip range for public ip's ? (ex. 10.xxx.xxx.xxx or 192.168.xxx.xxx) So you can better see the difference between privates an public ip's.

Edit the  local.conf ( if it still not works ) then make a clean restart.

Please read  this ( The section about MANAGED_VLAN )

[http://open.eucalyptus.com/wiki/EucalyptusNetworking_v1.6](http://open.eucalyptus.com/wiki/EucalyptusNetworking_v1.6)

---

### Post by oldhoot on 2011-01-04
At this stage my intent is not to be tricky and my cloud is working, meaning I can log into instances I create (assuming I use the private IP).  I will draw a picture of where I'm heading and get back to you.

---

### Post by oldhoot on 2011-01-04
Didn't answer your question.....

DNS should be 172.16.230.115.  And am I reading correctly in that I should try editing the .local.conf file directly?  But I guess I remain confused.  The local.conf file has the right public IP range, why isn't it being used and passed to the instances?  And where did the dhcp configuration get the 172.19.1.0 subnet from?

---

### Post by oldhoot on 2011-01-04
Here's a picture of what I'm trying to assemble.  All addresses shown are the actual physical addresses of the connections (no virtual).  I really don't care what the virtual subnet is just so I can manage instances from the client computer over the 172.16.230.0 subnet.  The 10.10.10.0 subnet is the very private 10GigE link I ultimately want to test.

---

### Post by raymdt on 2011-01-04
> And am I reading correctly in that I should try editing the .local.conf file directlyI tried it today on my both "Test-clouds" then made a clean restart and there was no problem. I did it because i was curious to know what would happen ( I experience a lot with my Test-clouds , so i can  learn more about UEC )

So, do it only if you know what you do -:)

Did you tried to use another ip range (10.xxx.xxx.xxx or 192.168.xxx.xxx) for public IP?

---

### Post by raymdt on 2011-01-04
Now i understand what you mean :guitar:

So, try to use subnetz 192.168.0.0 for your private Ips (Eucalyptus will configure a 192.168.1.1 route on your frontend) Just activate IP FORWARDING AND MASQUERADE on your Frontend

172.16.230.201 -....... 210 for public ips

Also, put this in you eucalyptus.local.conf and eucalyptus.conf file 
```

VNET_ADDRSPERNET="32"
VNET_SUBNET="192.168.0.0"
VNET_NETMASK="255.255.255.0"
VNET_DNS="172.16.230.115"
VNET_PUBLICIPS="172.16.230.201-172.16.230.210"


```

do  stop eucalyptus-cc CLEAN=1 then start eucalyptus CLEAN=1
and it should work.

---

### Post by oldhoot on 2011-01-04
Thanks for the help.  I'll be back with results.

Hoot

---

### Post by oldhoot on 2011-01-05
I have fixed part of the problem but have created a new one.  The IPs now look right as seen here...

[email]hoot@cloud-master:~/.euca[/email]$ euca-describe-instances 
RESERVATION    r-325B064D    admin    default
INSTANCE    i-433B0758    emi-DF13106C    172.16.230.201    172.19.1.2    running    wednew    0        c1.medium    2011-01-05T20:33:20.575Z    crux    eki-F56110EC    eri-09E6115D

And here's what I did to accomplish it ....

[email]hoot@cloud-master:~/.euca[/email]$ cat /etc/eucalyptus/eucalyptus.conf
# /etc/eucalyptus/eucalyptus.conf
#
# These are the Ubuntu Enterprise Cloud's default Eucalyptus parameters.

# Affects: All
# See: **NOTE** below
EUCALYPTUS="/"
EUCA_USER="eucalyptus"

# Affects: CLC, Walrus, SC
DISABLE_DNS="Y"
CLOUD_OPTS="-Xmx512m"

# Affects: SC
DISABLE_EBS="N"
DISABLE_ISCSI="N"

# Affects: CC, NC
# See: **NOTE** below
ENABLE_WS_SECURITY="Y"
LOGLEVEL="DEBUG"
VNET_PUBINTERFACE="eth0"
VNET_PRIVINTERFACE="eth1"
VNET_MODE="MANAGED-NOVLAN"

# Affects: CC
# See: **NOTE** below
CC_PORT="8774"
SCHEDPOLICY="ROUNDROBIN"
POWER_IDLETHRESH="300"
POWER_WAKETHRESH="300"
NC_SERVICE="axis2/services/EucalyptusNC"
VNET_DHCPDAEMON="/usr/sbin/dhcpd3"
VNET_DHCPUSER="dhcpd"
DISABLE_TUNNELLING="N"
NODES=""
VNET_ADDRSPERNET="32"
#VNET_SUBNET=""
#VNET_NETMASK=""
#VNET_DNS=""
#VNET_PUBLICIPS=""

# Affects: NC
NC_PORT="8775"
HYPERVISOR="kvm"
MANUAL_INSTANCES_CLEANUP=0
VNET_BRIDGE="br0"
INSTANCE_PATH="/var/lib/eucalyptus/instances/"
USE_VIRTIO_NET="0"
USE_VIRTIO_DISK="1"
USE_VIRTIO_ROOT="0"
#MAX_MEM=2048
#MAX_CORES="2"
#MAX_DISK="100"

##########################################################################
#
# Administrative overrides and customizations may go below, in accordance
# with the manpage for eucalyptus.conf(5).
#
# However, to modify Eucalyptus parameters, you are advised to use
# euca_conf(8), which will update eucalyptus.local.conf(5) and ensure
# smooth package upgrades.
#
# **NOTE**: To activate changes of these parameters on a CC, you must:
#           sudo restart eucalyptus-cc CLEAN=1
#           HOWEVER, if you do this, all currently running virtual
#           machines in this cluster will lose network connectivity.
#
##########################################################################

[email]hoot@cloud-master:~/.euca[/email]$ cat /etc/eucalyptus/eucalyptus.local.conf
# /etc/eucalyptus/eucalyptus.local.conf

# This file is read and written by euca_conf(8)
# WARNING: You should *never* edit this file directly.

# To modify Eucalyptus parameters, either use euca_conf(8), or
# edit /etc/eucalyptus/eucalyptus.conf according to eucalyptus.conf(5).


# network configuration from the input configuration file
VNET_MODE="MANAGED-NOVLAN"
VNET_SUBNET="172.19.0.0"
VNET_NETMASK="255.255.0.0"
VNET_DNS="172.16.230.115"
VNET_ADDRSPERNET="32"
VNET_PUBLICIPS="172.16.230.201-172.16.230.210"


But now I can't log into the instance, I get an immediate key violation.  I've cleaned out known_hosts, rebuilt the cluster, etc. (all the usual tricks) and no luck...

[email]hoot@cloud-master:~/.euca[/email]$ ssh -vvv -i wednew.priv ubuntu@172.16.230.201
OpenSSH_5.5p1 Debian-4ubuntu4, OpenSSL 0.9.8o 01 Jun 2010
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 172.16.230.201 [172.16.230.201] port 22.
debug1: Connection established.
debug3: Not a RSA1 key file wednew.priv.
debug3: key_read: missing whitespace
debug2: key_type_from_name: unknown key type '-----BEGIN'
debug3: key_read: missing keytype
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug2: key_type_from_name: unknown key type '-----END'
debug3: key_read: missing keytype
debug1: identity file wednew.priv type -1
debug1: identity file wednew.priv-cert type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.1p1 Debian-6ubuntu2
debug1: match: OpenSSH_5.1p1 Debian-6ubuntu2 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.5p1 Debian-4ubuntu4
debug2: fd 3 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: [email]ssh-rsa-cert-v00@openssh.com,ssh-dss-cert-v00@openssh.com[/email],ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: mac_setup: found hmac-md5
debug1: kex: server->client aes128-ctr hmac-md5 none
debug2: mac_setup: found hmac-md5
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug2: dh_gen_key: priv key bits set: 122/256
debug2: bits set: 521/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug3: check_host_in_hostfile: host 172.16.230.201 filename /home/hoot/.ssh/known_hosts
debug3: check_host_in_hostfile: host 172.16.230.201 filename /home/hoot/.ssh/known_hosts
debug3: check_host_in_hostfile: match line 2
debug1: Host '172.16.230.201' is known and matches the RSA host key.
debug1: Found key in /home/hoot/.ssh/known_hosts:2
debug2: bits set: 515/1024
debug1: ssh_rsa_verify: signature correct
debug2: kex_derive_keys
debug2: set_newkeys: mode 1
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug2: set_newkeys: mode 0
debug1: SSH2_MSG_NEWKEYS received
debug1: Roaming not allowed by server
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug2: key: wednew.priv ((nil))
debug1: Authentications that can continue: publickey
debug3: start over, passed a different list publickey
debug3: preferred gssapi-keyex,gssapi-with-mic,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Trying private key: wednew.priv
debug1: read PEM private key done: type RSA
debug3: sign_and_send_pubkey
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey
debug2: we did not send a packet, disable method
debug1: No more authentication methods to try.
Permission denied (publickey).

---

### Post by oldhoot on 2011-01-05
I sure wish I understood the magic of all this but I went through and deregistered, re-registered everyting, did reboots, etc. and now I log into the instances again and there are the right IPs.

What is it that gets stuck that gives the publickey failure???  It's getting very frustrating.

---

### Post by oldhoot on 2011-01-05
And now my next IP related question, when log into my instance I can ping public IPs through the controller and the controller can ping the public IP assigned to instance.  However, other public IPs CAN NOT ping through the controller to the instance.  Any thoughts?  Is it a route problem?

---

