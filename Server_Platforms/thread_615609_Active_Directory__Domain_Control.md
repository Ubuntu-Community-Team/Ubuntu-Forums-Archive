---
title: "Active Directory / Domain Control"
date: 2007-11-17
forum: Server Platforms
---

### Post by WIGGMPk on 2007-11-17
I have followed a few howto's and couldnt get this working. When running 'kadmin' or 'kinit' I get the following:

kinit(v5): Cannot contact any KDC for requested realm while getting initial credentials


Here are my config's

/etc/krb5.conf

[logging]
    default = FILE:/var/log/krb5.log
    kdc = FILE:/var/log/krb5kdc.log
    admin_server = FILE:/var/log/kadmind.log

[libdefaults]
    ticket_lifetime = 24000
    clock_skew = 300
    default_realm = LUGGS-BT.DYNDNS.ORG
    default_tkt_enctypes = des3-hmac-sha1 des-cbc-crc
    default_tgs_enctypes = des3-hmac-sha1 des-cbc-crc
#    dns_lookup_realm = false
#    dns_lookup_kdc = true
    forwardable = yes

[realms]
    LUGGS-BT.DYNDNS.ORG = {
        kdc = luggs-bt.luggs-bt.dyndns.org:88
        admin_server = luggs-bt.luggs-bt.dyndns.org:749
        default_domain = LUGGS-BT.DYNDNS.ORG
}

[domain_realm]
    .luggs-bt.dyndns.org = LUGGS-BT.DYNDNS.ORG
    luggs-bt.dyndns.org = LUGGS-BT.DYNDNS.ORG

[kdc]
    profile = /var/kerberos/krb5kdc/kdc.conf
-------------------------------------------------------------------------------------------------
/etc/bind/named.conf.local

//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization

include "/etc/bind/zones.rfc1918";

zone "luggs-bt.dyndns.org"{
        type master;
        file "/etc/bind/luggs-bt.org.db";
};

zone "0.168.192.in-addr.arpa"{
        type master;
        file "/etc/bind/zones/rev.0.168.192.in-addr.arpa";
};
--------------------------------------------------------------------------------------------------
/etc/bind/zones/luggs-bt.dyndns.org.db

@ IN SOA ns1.luggs-bt.dyndns.org. admin.luggs-bt.dyndns.org. (
        2007031001
        28800
        3600
        604800
        38400
);

luggs-bt.dyndns.org.    IN      NS              ns1.luggs-bt.dyndns.org.
#luggs-bt.dyndns.org.   IN      MX      10      mail.luggs-bt.dyndns.org.

www                     IN      A       192.168.0.1
#mta                    IN      A       192.168.0.1
ns1                     IN      A       192.168.0.1
gw                      IN      A       192.168.0.1
                                TXT     "Network Gateway"
--------------------------------------------------------------------------------------------------
/etc/krb5kdc/kdc.conf

[kdcdefaults]
    kdc_ports = 750,88

[realms]
   LUGGS-BT.DYNDNS.ORG  = {
        database_name = /var/lib/krb5kdc/principal
        admin_keytab = FILE:/etc/krb5kdc/kadm5.keytab
        acl_file = /etc/krb5kdc/kadm5.acl
        key_stash_file = /etc/krb5kdc/stash
        kdc_ports = 750,88
        max_life = 10h 0m 0s
        max_renewable_life = 7d 0h 0m 0s
        master_key_type = des3-hmac-sha1
        supported_enctypes = des3-hmac-sha1:normal des-cbc-crc:normal des:norma$
        default_principal_flags = +preauth
    }
-------------------------------------------------------------------------------------------------
/etc/hosts

#127.0.0.1      localhost
#127.0.0.1      LUGGS-BT.LUGGS-BT.DYNDNS.ORG    localhost       LUGGS-BT
192.168.0.1     LUGGS-BT.LUGGS-BT.DYNDNS.ORG    localhost       LUGGS-BT

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
--------------------------------------------------------------------------------------------------
/etc/samba/smb.conf

[global]
        realm = luggs-bt.dyndns.org
        security = ADS
        workgroup = LUGGS-BT
        netbios name = LUGGS-BT
        server string = %h server (Samba, Ubuntu)
        #interfaces = 192.168.0.1/eth1
        #bind interfaces only = Yes
        password server = 192.168.0.1
        idmap uid = 10000-20000
        idmap gid = 10000-20000
        winbind separator = +
        winbind enum users = Yes
        winbind enum groups = Yes
        winbind use default domain = Yes
        template homedir = /home/%D/%U
        template shell = /bin/bash
        client use spnego = Yes
        client ntlmv2 auth = Yes
        username map = /etc/samba/smbusers
        encrypt passwords = true
        #update encrypted = Yes
        restrict anonymous = 2
        log file = /var/log/samba/log.%m
        max log size = 50
        socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192$
        #printcap name = cups
        dns proxy = No
        #printing = cups
        os level = 65
        domain logons = Yes
        preferred master = Yes
-------------------------------------------------------------------------------------------------


I dont know what I did wrong.. The name of the server is 'LUGGS-BT' any help would be appreciated.

---

### Post by WIGGMPk on 2007-11-17
My setup is this

eth0 (attached to cable modem, getting IP via DHCP)

eth1 (attached to router (flashed with opensource firmware) configured as a switch/AP to serve DHCP requests using dhcp3-server)

eth1 IP address is 192.168.0.1

/etc/dhcp3/dhcpd.conf

# Custom DHCP Settings
# ETH1 = 192.168.0.1

ddns-update-style interim;
ignore client-updates;

subnet 192.168.0.0 netmask 255.255.255.0 {
        option routers 192.168.0.1;
        option subnet-mask 255.255.255.0;
        option domain-name-servers 204.186.0.201;
        option domain-name-servers 207.44.96.129;
        option domain-name-servers 204.186.0.203;
        option ip-forwarding off;
        range dynamic-bootp 192.168.0.100 192.168.0.254;
        default-lease-time 21600;
        max-lease-time 43200;
}


/etc/rc.local

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

# eth1 Static Script
sudo ifconfig eth1 192.168.0.1
sudo iptables -A FORWARD -i eth1 -o eth0 -s 192.168.0.0/24 -m state --state NEW$
sudo iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
sudo iptables -A POSTROUTING -t nat -j MASQUERADE

sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"

sudo /etc/init.d/dhcp3-server restart

sudo mount /dev/sda1 /media/LUGGS-BT

exit 0

---

### Post by andb on 2008-02-23
Do you still have the problem? I found I could fix the problem by editing /etc/hosts on the kerberos machine and remark out the 127.0.1.1 line, which has my FQDN.

#127.0.1.1 kerberosserver.example.net 

So it was clearly a DNS issue in my case.

---

