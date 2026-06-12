---
title: "bind not restarting"
date: 2010-12-27
forum: Server Platforms
---

### Post by fast_eddie on 2010-12-27
Hi,

Completely new to Ubuntu and Linux, but learning fast.

I've just installed a control panel (Parallels Plesk 10) and couldn't change the administrator password because I was getting a bind restart error.  I then realised that the static WAN IP address hadn't been configured and so I've edited the rndc.conf and named.conf files as follows:
> # Start of rndc.conf
key "rndc-key" {
    algorithm hmac-md5;
    secret "CeNgS23y0oME20njv0x40Q==";
};

options {
    default-key "rndc-key";
    default-server 8x.xx.x4.158;
#    default-port 953;
};
# End of rndc.conf

> // $Id: named.conf,v 1.1.1.1 2001/10/15 07:44:36 kap Exp $
//
// Refer to the named(8) man page for details.  If you are ever going
// to setup a primary server, make sure you've understood the hairy
// details of how DNS is working.  Even with simple mistakes, you can
// break connectivity for affected parties, or cause huge amount of
// useless Internet traffic.

options {
    allow-recursion {
        localnets;
    };
    version "none";
    directory "/var";
    auth-nxdomain no;
    pid-file "/var/run/named/named.pid";

// In addition to the "forwarders" clause, you can force your name
// server to never initiate queries of its own, but always ask its
// forwarders only, by enabling the following line:
//
//      forward only;

// If you've got a DNS server around at your upstream provider, enter
// its IP address here, and enable the line below.  This will make you
// benefit from its cache, thus reduce overall DNS traffic in the Internet.
/*
    forwarders {
        82.197.83.198;
        84.45.112.20;
    };
*/
    /*
     * If there is a firewall between you and nameservers you want
     * to talk to, you might need to uncomment the query-source
     * directive below.  Previous versions of BIND always asked
     * questions using port 53, but BIND 8.1 uses an unprivileged
     * port by default.
     */
    // query-source address * port 53;

    /*
     * If running in a sandbox, you may have to specify a different
     * location for the dumpfile.
     */
    // dump-file "s/named_dump.db";
};

//sync with rndc.conf, adjusting the allow list as needed:

key "rndc-key" {
    algorithm hmac-md5;
    secret "CeNgS23y0oME20njv0x40Q==";
};

controls {
    inet 8x.xx.x4.158 port 953
        allow { 8x.xx.x4.158; } keys { "rndc-key"; };
};


I'm not sure that these are correct, as the server is not acting as a name server I've specified a subdomain pointing at this vmware Ubuntu server. Do I need a local zone to be configured even though I have a FQDN on another NS pointing to this WAN IP?

However when I'm now trying to upload these files they are being written to a different location and I can't move them?  This had been working ok previously but has since changed!

> psftp> cd /etc/
Remote directory is now /etc
psftp> lcd c:\z-ftp
New local directory is c:\z-ftp
psftp> put named.conf
local:named.conf => remote:/var/named/run-root/etc/named.conf

So two aspects to this thread.
1) Are the named.conf and rndc.conf files correct, is there anything else that needs to be edited before I restart bind service
2) Why can I no longer upload these config files to /etc/ ?

Many thanks!

---

### Post by fast_eddie on 2010-12-27
Hi

This is the error message I get when trying to restart bind service


> Ubuntu 10.04.1 LTS

Welcome to the Ubuntu Server!
 * Documentation:  [http://www.ubuntu.com/server/doc](http://www.ubuntu.com/server/doc)
Last login: Mon Dec 27 23:08:27 2010 from xx.xx.xx.xx
root@crm:~#
root@crm:~# /etc/init.d/bind9 restart
 * Stopping domain name service... bind9                                               WARNING: key file (/etc/bind/rndc.key) exists, but using default configuration file (/etc/bind/rndc.conf)
rndc: connect failed: 8x.xx.x4.158#953: connection refused
named: no process found
                                                                         [ OK ]
 * Starting domain name service... bind9                                 [fail]
root@crm:~#

---

### Post by Vegan on 2010-12-27
BIND is designed for mechanized configuration from other tools such as an ISP package or Webmin

---

### Post by fast_eddie on 2010-12-29
Ok so you're saying I shouldn't be editting the rndc.conf and named.conf files manually?

---

