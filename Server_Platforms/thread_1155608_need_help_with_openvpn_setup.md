---
title: "need help with openvpn setup"
date: 2009-05-11
forum: Server Platforms
---

### Post by Elsven on 2009-05-11
Ok, I am trying to set up an openvpn server so i can have full access to my network while I am away from home.  The tutorial I am using is found at [https://help.ubuntu.com/community/OpenVPN](https://help.ubuntu.com/community/OpenVPN) on the Ubuntu doc site.  Currently I am stuck on step three which involves generating the CA and server certificates.  Located below I have included a capture of my terminal, it seems that something is fundamentally wrong since this wont work regardless of whether I am using sudo or not. 

```
sysadmin@UbuntuServer:/etc/openvpn/easy-rsa$ ./pkitool --initca ## creates ca cert and key
Using CA Common Name: Richard CA
Generating a 1024 bit RSA private key
...............................................
writing new private key to 'ca.key'
ca.key: Permission denied
11478:error:0200100D:system library:fopen:Permission denied:bss_file.c:352:fopen('ca.key','w')
11478:error:20074002:BIO routines:FILE_CTRL:system lib:bss_file.c:354:
sysadmin@UbuntuServer:/etc/openvpn/easy-rsa$ ./pkitool --server server ## creates a server cert and key
pkitool: Need a readable ca.crt and ca.key in /etc/openvpn/easy-rsa/keys
Try pkitool --initca to build a root certificate/key.
sysadmin@UbuntuServer:/etc/openvpn/easy-rsa$ cd keys
sysadmin@UbuntuServer:/etc/openvpn/easy-rsa/keys$ openvpn --genkey --secret ta.key  ## Build a TLS key
Sun May 10 21:48:52 2009 Cannot open shared secret file 'ta.key' for write: Permission denied (errno=13)
Sun May 10 21:48:52 2009 Exiting
sysadmin@UbuntuServer:/etc/openvpn/easy-rsa/keys$ cp server.crt server.key ca.crt dh1024.pem ta.key ../../
cp: cannot stat `server.crt': No such file or directory
cp: cannot stat `server.key': No such file or directory
cp: cannot stat `ca.crt': No such file or directory
cp: cannot stat `dh1024.pem': No such file or directory
cp: cannot stat `ta.key': No such file or directory
sysadmin@UbuntuServer:/etc/openvpn/easy-rsa/keys$
```

Any help with this problem would be greatly appreciated my knowledge of Ubuntu and linux is descent however I relatively new to linux and Ubuntu.  I am currently trying to switch over from windows systems and this would allow me to get rid of my windows VPN server.

Regards

---

### Post by gombadi on 2009-05-11
> 
Located below I have included a capture of my terminal, it seems that something is fundamentally wrong since this wont work regardless of whether I am using sudo or not.

and
writing new private key to 'ca.key'
ca.key: Permission denied
11478:error:0200100D:system library:fopen: Permission denied:bss_file.c:352:fopen('ca.key','w')


By the looks of things you are trying to create a file in a directory that you do not have write permission to. You mention that you have also tried with sudo - did you get the same write permission error?

When I created the keys for my system I created a directory and the keys in my home directory and then used root to copy the files to the final location.

---

### Post by Elsven on 2009-05-11
Yes I tried it with sudo and it still did not generate them.  Here is the rest of it, I for got to paste everything.

```
sysadmin@UbuntuServer:/etc/openvpn/easy-rsa$ sudo chown -R root:admin .  ## make this directory writable by the system administrators
cd keys
openvpn --genkey --secret ta.key  ## Build a TLS key
cp server.crt server.key ca.crt dh1024.pem ta.key ../../
sysadmin@UbuntuServer:/etc/openvpn/easy-rsa$ source ./vars ## execute your new vars file
NOTE: If you run ./clean-all, I will be doing a rm -rf on /etc/openvpn/easy-rsa/keys
sysadmin@UbuntuServer:/etc/openvpn/easy-rsa$ ./clean-all  ## Setup the easy-rsa directory (Deletes all keys)
rm: cannot remove directory `/etc/openvpn/easy-rsa/keys': Permission denied
mkdir: cannot create directory `/etc/openvpn/easy-rsa/keys': File exists
sysadmin@UbuntuServer:/etc/openvpn/easy-rsa$ ./build-dh  ## takes a while consider backgrounding
Generating DH parameters, 1024 bit long safe prime, generator 2
This is going to take a long time
.............................................
/etc/openvpn/easy-rsa/keys/dh1024.pem: Permission denied
```

If you look the first command was a chmod, that command should have made that folder accessible by administrators right?  If this is so I should not have needed to use sudo.  The next segment will sho the commands be executed with sudo.

```
sysadmin@UbuntuServer:/etc/openvpn/easy-rsa$ source ./vars ## execute your new vars file
NOTE: If you run ./clean-all, I will be doing a rm -rf on /etc/openvpn/easy-rsa/keys
sysadmin@UbuntuServer:/etc/openvpn/easy-rsa$ sudo ./clean-all  ## Setup the easy-rsa directory (Deletes all keys)
[sudo] password for sysadmin:
Please source the vars script first (i.e. "source ./vars")
Make sure you have edited it to reflect your configuration.
sysadmin@UbuntuServer:/etc/openvpn/easy-rsa$ sudo ./build-dh  ## takes a while consider backgrounding
Please source the vars script first (i.e. "source ./vars")
Make sure you have edited it to reflect your configuration.
sysadmin@UbuntuServer:/etc/openvpn/easy-rsa$ sudo ./pkitool --initca ## creates ca cert and key
  Please edit the vars script to reflect your configuration,
  then source it with "source ./vars".
  Next, to start with a fresh PKI configuration and to delete any
  previous certificates and keys, run "./clean-all".
  Finally, you can run this tool (pkitool) to build certificates/keys.
```

It seems as if the vars file is not doing it s job, so here is my vars configuration.

```
# easy-rsa parameter settings

# NOTE: If you installed from an RPM,
# don't edit this file in place in
# /usr/share/openvpn/easy-rsa --
# instead, you should copy the whole
# easy-rsa directory to another location
# (such as /etc/openvpn) so that your
# edits will not be wiped out by a future
# OpenVPN package upgrade.

# This variable should point to
# the top level of the easy-rsa
# tree.
export EASY_RSA="/etc/openvpn/easy-rsa"

#
# This variable should point to
# the requested executables
#
export OPENSSL="openssl"
export PKCS11TOOL="pkcs11-tool"
export GREP="grep"


# This variable should point to
# the openssl.cnf file included
# with easy-rsa.
export KEY_CONFIG=`$EASY_RSA/whichopensslcnf $EASY_RSA`

# Edit this variable to point to
# your soon-to-be-created key
# directory.
#
# WARNING: clean-all will do
# a rm -rf on this directory
# so make sure you define
# it correctly!
export KEY_DIR="$EASY_RSA/keys"

# Issue rm -rf warning
echo NOTE: If you run ./clean-all, I will be doing a rm -rf on $KEY_DIR

# PKCS11 fixes
export PKCS11_MODULE_PATH="dummy"
export PKCS11_PIN="dummy"

# Increase this to 2048 if you
# are paranoid.  This will slow
# down TLS negotiation performance
# as well as the one-time DH parms
# generation process.
export KEY_SIZE=1024

# In how many days should the root CA key expire?
export CA_EXPIRE=3650

# In how many days should certificates expire?
export KEY_EXPIRE=3650

# These are the default values for fields
# which will be placed in the certificate.
# Don't leave any of these fields blank.
export KEY_COUNTRY="CA"
export KEY_PROVINCE="AB"
export KEY_CITY="Calgary"
export KEY_ORG="Richard"
export KEY_EMAIL="email@address.here"
```

---

### Post by gombadi on 2009-05-11
> 
It seems as if the vars file is not doing it s job, so here is my vars configuration.


It is not a problem with the vars file (may want to remove the email address from the var file you posted) but the fact that the scripts can not find the information.

You are sourcing the vars file into your current environment but then using sudo which changes your environment so the scripts can not fine the variables that you previously sourced.

Your choices as I see it are either make the keys in your own home directory - no need for sudo - or change to root and run all commands in a root environment.
```

sudo su -

```

---

### Post by Elsven on 2009-05-11
Thank you the sudo thing seems to be working, now I can continue on the step four.  Just a quick question, is "sudo su" the same as "su" was in the old systems?  After that point you are working as a super user?

---

### Post by gombadi on 2009-05-11
> 
Just a quick question, is "sudo su" the same as "su" was in the old systems? After that point you are working as a super user? 


If you have set a root password then you can use su to switch user with the password of root.
If you have not set a root password then you use sudo to give you permissions to switch user to root, using your own password.

Same result but a different way of getting there.

---

### Post by Elsven on 2009-05-11
Ok thanks for the info on sudo.  No I am on to configuring the server.conf file however the documentation on this file is very poor.  The setup I have is two Ethernet cards, eth1 is setup DHCP and that will be getting an internet IP address form my ISP.  This one will be the car I want to service my VPN connections on.  The other network card Eth0 will be connected to my internal network and will be bridged to my VPN computers.  With this said I am unsure how to modify this config file to suite my needs.

```
mode server
tls-server

local <your ip address> ## ip/hostname of server
port 1194 ## default openvpn port
proto udp



#bridging directive
dev tap0 ## If you need multiple tap devices, add them here
up "/etc/openvpn/up.sh br0"
down "/etc/openvpn/down.sh br0"

persist-key
persist-tun

#certificates and encryption
ca ca.crt
cert server.crt
key server.key  # This file should be kept secret
dh dh1024.pem
tls-auth ta.key 0 # This file is secret

cipher BF-CBC        # Blowfish (default)
comp-lzo

#DHCP Information
ifconfig-pool-persist ipp.txt
server-bridge 192.168.1.10 255.255.255.0 192.168.1.100 192.168.1.110
push "dhcp-option DNS your.dns.ip.here"
push "dhcp-option DOMAIN yourdomain.com"
max-clients 10 ## set this to the max number of clients that should be connected at a time

#log and security
user nobody
group nogroup
keepalive 10 120
status openvpn-status.log
verb 3
```

As far as I understand it 
```
server-bridge 192.168.1.10 255.255.255.0 192.168.1.100 192.168.1.110
```
should be the same IP as Eth0 but how do i get it to automatically determine the ip and stuff if this information is coming from another DHCP server?

---

