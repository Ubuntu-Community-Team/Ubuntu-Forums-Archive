---
title: "squid with ldap_auth and squid_ldap_group... help needed"
date: 2006-09-30
forum: Server Platforms
---

### Post by rextor on 2006-09-30
I am trying to configure squid with Active directory authentication. The final aim is to have dansguardian with squid for web filtering. The user would authenticate with ADS and internet would be provided to the user depending on the group (on ADS) to which she belongs. I am doing this on Ubuntu Server 6.06

I have successfully configured ntlm authentication by using ntlm_auth helper (winbind + samba + squid). But i cant figure out how to read the groups of these users.

I have been now trying to use ldap_auth instead of ntlm_auth, but this does not seem to work.
The below command does not work on command line:
> 
/usr/lib/squid/ldap_auth -b "dc=corp,dc=mycompany,dc=com" -h mydomain.corp.mycompany.com -D "cn=Administrator,ou=dept,dc=corp,dc=mycompany,dc=com" -w <admin-password> -f ""sAMAccountName=%s
It return me "ERR" for both username or DOMAIN\username.

Are there any more packages to be installed or configured?
Currently i have Kerberos, Samba, Winbind, Squid.

Thanks.

edit: do i need to configure /etc/libnss-ldap.conf first?

---

### Post by munwin on 2006-10-03
Here's where I am at with my Squid project.
The end goal is to have the Ubuntu Server authenticate via AD, and log all access. It will then run a .php command line script every hour to input the logs into a database. There will be a web front end to generate usage reports. I actually have this all working, although it's on a Windows box. My Ubuntu box can verify users, and log the data to the DB - just got the (tidied up) web interface to go.
Below is how I setup the Ubuntu Server 6.06 to verify users against AD...

Hope it helps.



These instructions assume your domain information is DOMAIN (old style domain name) and the DNS resolvable one is DOMAIN.INTERNAL. Our Active Directory environment is running on Windows 2000.
SERVER1 and SERVER2 are Active Directory Domain Controllers.

Install Ubuntu 6.06 Lamp Server

Setup Networking
- At my work we have a firewall, that restricts access to the net to only certain PCs. Hence, I need to setup a static IPAddress for the Ubuntu-Proxy. When using this in production, you would need a static IPAddress, as well (how else will your client PCs know where the proxy is ?).

sudo vi /etc/network/interfaces
--------------------------------

auto      eth0

iface     eth0 inet static

address   192.168.10.29

netmask   255.255.255.0

broadcast 192.168.10.255

gateway   192.168.10.5
--------------------------------

Restart networking
sudo /etc/init.d/networking restart

Edit sources 
- uncomment all relevant lines
- comment our CDRom
sudo vi /etc/apt/sources.list

Run update
sudo apt-get update

Run Upgrade
sudo apt-get upgrade

Install SSH (optional)
sudo apt-get install openssh-server

Install Kerberos, Samba, and Winbind
Note: Enter Y when asked if you want to install the additional packages
sudo apt-get install krb5-user winbind samba

Edit the /etc/krb5.conf File
--------------------------------
[logging]
    default = FILE10000:/var/log/krb5lib.log
[libdefaults]
    ticket_lifetime = 24000
    default_realm = DOMAIN.INTERNAL
    dns_lookup_realm = true
    dns_lookup_kdc = true
    default_tkt_enctypes = des3-hmac-sha1 des-cbc-crc
    default_tgs_enctypes = des3-hmac-sha1 des-cbc-crc
[realms]
    HO.QPCU.ORG.AU = {
        kdc = SERVER1
        kdc = SERVER1
        admin_server = SERVER1
        default_domain = DOMAIN.INTERNAL
}
[domain_realm]
    .domain.internal = DOMAIN.INTERNAL
    domain.internal = DOMAIN.INTERNAL
-------------------------------


Edit /etc/samba/smb.conf 
Notes: Change the 
       - netbios name 
       - realm
       - password server
       - workgroup
       parameters to be correct for the server. Make a backup copy of the original file!!!
-------------------------------
[global]
        security = ads
        netbios name = ubuntu-squid
        realm = DOMAIN.INTERNAL
        password server = SERVER1.DOMAIN.INTERNAL
        workgroup = DOMAIN
        idmap uid = 500-10000000
        idmap gid = 500-10000000
        winbind separator = +
        winbind enum users = no
        winbind enum groups = no
        winbind use default domain = yes
        template homedir = /home/%D/%U
        template shell = /bin/bash
        client use spnego = yes
        domain master = no
-------------------------------


Test the configuration with the testparm command

Edit /etc/nsswitch.conf
***NOTE - Do NOT rename & copy this file.
        - Once you rename is sudo is borked....
-------------------------------
passwd:         compat winbind
group:          compat winbind
shadow:         compat
hosts:          files dns wins
networks:       files
protocols:      db files
services:       db files
ethers:         db files
rpc:            db files
netgroup:       nis
-------------------------------


Edit /etc/pam.d/common-account so it contains ONLY the following
-------------------------------
account sufficient	pam_winbind.so
account required	pam_unix.so
-------------------------------


Edit /etc/pam.d/common-auth so it contains ONLY the following
-------------------------------
auth    sufficient      pam_winbind.so
auth    required        pam_unix.so nullok_secure use_first_pass
-------------------------------

Modify the /etc/pam.d/common-password file, so the max parameter is set to 50, similar to the one shown below
-------------------------------
password   required   pam_unix.so nullok obscure min=4 max=50 md5
-------------------------------

Make sure the /etc/pam.d/common-session file contains the following line
-------------------------------
session required        pam_mkhomedir.so umask=0022 skel=/etc/skel
-------------------------------

Make a directory to hold domain user home directories
Note: Use the value you put in the WORKGROUP tag of the /etc/samba/smb.conf file
mkdir /home/DOMAIN

Initialize Kerberos
kinit [email]administrator@DOMAIN.INTE[/email]RNAL

Check to be sure you got a ticket from the domain controller
klist

Join the system to the domain
sudo net ads join -U [email]administrator@DOMAIN.INTE[/email]RNAL


Restart Samba-related Services (Or reboot the server)
Note: The order is important
/etc/init.d/samba stop
/etc/init.d/winbind stop
/etc/init.d/samba start
/etc/init.d/winbind start


Attempt to login via SSH as a domain administrator

Install Squid
sudo apt-get install squid

sudo chgrp proxy /var/run/samba/winbindd_privileged
sudo chmod g+rx /var/run/samba/winbindd_privileged

sudo /etc/init.d/squid restart


To reset permissions on above at logon.
[http://ubuntuforums.org/showthread.php?t=205978](http://ubuntuforums.org/showthread.php?t=205978)


sudo vi /etc/init.d/winbind-ch.sh
-------------------------------
#!/bin/sh
#set -x
WINBINDD_PRIVILEGED=/var/run/samba/winbindd_privileged

chmodgrp() {
chgrp proxy $WINBINDD_PRIVILEGED || return 1
chmod g+w $WINBINDD_PRIVILEGED || return 1
}

case "$1" in
start)
chmodgrp
;;
restart|reload|force-reload)
echo "Error: argument '$1' not supported" >&2
exit 3
;;
stop)
;;
*)
echo "Usage: $0 start|stop" >&2
exit 3
;;
esac
#EOF
-------------------------------

Have the script run after startup
sudo update-rc.d winbind-ch.sh start 21 2 3 4 5 .

---

