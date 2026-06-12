---
title: "Setting up BIND9 trouble"
date: 2010-12-25
forum: Server Platforms
---

### Post by twister666 on 2010-12-25
Hello Everyone!
I am having trouble with setting up BIND9 for 6 virtual servers that use ubuntu x64 v10.10. 
I have main server running ubuntu as well. host name is xeonserver

I would like to explain my setup first.

my router ip: 192.168.1.1/24
host server for VMs ip: 192.168.1.2/24

Then on qemu my virtual machines are in 10.0.0.0/24 network, gateway to my router is 10.0.0.1
1. kerberos.xeonserver (not configured yet) 10.0.0.2 
2. dns.xeonserver (the one I have trouble with) 10.0.0.3
3. mysql.xeonserver (not configured yet) 10.0.0.4
4. apache.xeonserver (not configured yet) 10.0.0.5
5. ftp.xeonserver (not configured yet) 10.0.0.6
6. mail.xeonserver (not configured yet) 10.0.0.7

To configure it I followed instructions found on [http://www.ubuntugeek.com/dns-server-setup-using-bind-in-ubuntu.html](http://www.ubuntugeek.com/dns-server-setup-using-bind-in-ubuntu.html)

my **/etc/bind/named.conf.local **looks like this

        zone "aquapuffin.com"{
type master;
file "/etc/bind/zones/aquapuffin.com.db";
};

        zone "0.0.10.in-addr.arpa" {
type master;
file "/etc/bind/zones/rev.0.0.10.in-addr.arpa";
};

my** /etc/bind/named.conf.options** looks like this

options {
        directory "/var/cache/bind";

        forwarders {
192.168.1.1;
};
        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
};

my **/etc/bind/zones/aquapuffin.com.db** looks like this

aquapuffin.com.                         IN      SOA     dns.xeonserver.aquapuff$
        2010122500
        28800
        3600
        604800
        38400
)
aquapuffin.com.                         IN      NS      dns.xeonserver.aquapuff$
kerberos.xeonserver.aquapuffin.com.     IN      A       10.0.0.2
dns.xeonserver.aquapuffin.com.          IN      A       10.0.0.3
mysql.xeonserver.aquapuffin.com.        IN      A       10.0.0.4
apache.xeonserver.aquapuffin.com.       IN      A       10.0.0.5
ftp.xeonserver.aquapuffin.com.          IN      A       10.0.0.6
mail.xeonserver.aquapuffin.com.         IN      A       10.0.0.7

my** /etc/bind/zones/rev.0.0.10.in-addr.arpa** looks like this

@                       IN      SOA     dns.xeonserver.aquapuffin.com.  root.aq$
        2010122500;
        28800;
        604800;
        604800;
        86400 )
                        IN      NS      dsn.xeonserver.aquapuffin.com.
2.0.0.10.in-addr.arpa   IN      PTR     kerberos.xeonserver.aquapuffin.com.
3.0.0.10.in-addr.arpa   IN      PTR     dns.xeonserver.aquapuffin.com.
4.0.0.10.in-addr.arpa   IN      PTR     mysql.xeonserver.aquapuffin.com.
5.0.0.10.in-addr.arpa   IN      PTR     apache.xeonserver.aquapuffin.com.
6.0.0.10.in-addr.arpa   IN      PTR     ftp.xeonserver.aquapuffin.com.
7.0.0.10.in-addr.arpa   IN      PTR     mail.xeonserver.aquapuffin.com.

my **/etc/resolv.conf** looks like this 

nameserver 10.0.0.1

Could someone help me out to verify if I did everything correct here. I already pointed all my machines to dns server. but it can't find my machines. Any help will be appreciated

---

### Post by furlabs on 2010-12-26
I've never seen those dollar signs before, looks like a syntax error to me. eg "dns.xeonserver.aquapuff$". Take another look at the link you are following for the right syntax.

Also, tail /var/log/syslog when you start bind, it should let you know what is going wrong.

---

