---
title: "dhcpd update dns?"
date: 2005-07-19
forum: Server Platforms
---

### Post by akshoslaa on 2005-07-19
Alrighty, been working on this for days now and I've finally run out of steam.
I'm trying to set up a box to do dhcp and dns for my lan...

It's now _mostly_ working... dhcp assigns ip's to the correct subnets, the routes all work, pinging external and static-internal hosts by name and ip works fine, with domain resolution.. its all good.

My problem: getting dchp to add the leases to the dns...

ie static: I can "ping router" which resolves to "router.akshoslaa.local"
but dhcp: "ping test" gives unknown host.

I've gone through more howto's and man pages than I can remember atm, and as far as I can tell... it's configured properly... it's just not doing anything with dhcp hostnames...

**config file time:**:P

$ cat /etc/bind/named.conf #Yes I Know this should be split into .local, I'll get it _working_ first :P Also dhcp is only on eth2 and eth3
```
include "/etc/bind/named.conf.options";

key DHCP_UPDATER {
    algorithm HMAC-MD5.SIG-ALG.REG.INT;
    secret "hqrdTgBWjSpCJShdLR4g9g==";
};

// reduce log verbosity on issues outside our control
logging {
        category lame-servers { null; };
        category cname { null; };
};

// prime the server with knowledge of the root servers
zone "." {
        type hint;
        file "/etc/bind/db.root";
};

// be authoritative for the localhost forward and reverse zones, and for
// broadcast zones as per RFC 1912

zone "localhost" {
        type master;
        file "/etc/bind/db.local";
};

zone "127.in-addr.arpa" {
        type master;
        file "/etc/bind/db.127";
};

zone "0.in-addr.arpa" {
        type master;
        file "/etc/bind/db.0";
};

zone "255.in-addr.arpa" {
        type master;
        file "/etc/bind/db.255";
};

zone "0.168.192.in-addr.arpa" {
        type master;
        file "/etc/bind/db.0.168.192";
};

zone "1.168.192.in-addr.arpa" {
        type master;
        file "/etc/bind/db.1.168.192";
};

zone "2.168.192.in-addr.arpa" {
        type master;
        notify yes;
        file "/etc/bind/db.2.168.192";
        allow-update { key DHCP_UPDATER; };
};

zone "3.168.192.in-addr.arpa" {
        type master;
        notify yes;
        file "/etc/bind/db.3.168.192";
        allow-update { key DHCP_UPDATER; };
};

zone "akshoslaa.local" {
        type master;
        notify yes;
        allow-update { key DHCP_UPDATER; };
        file "/etc/bind/db.akshoslaa.local";
};

// add local zone definitions here
include "/etc/bind/named.conf.local";
```

$ cat /etc/dhcp3/dhcpd.conf #Comments removed for berivity
```
authoritative;

key DHCP_UPDATER {
         algorithm HMAC-MD5.SIG-ALG.REG.INT;
         secret hqrdTgBWjSpCJShdLR4g9g==;
};

ddns-domainname "akshoslaa.local.";
ddns-rev-domainname "in-addre.arpa.";
ddns-update-style interim;
ddns-updates on;
allow client-updates;

log-facility local7;

default-lease-time 600; #set low for testing
max-lease-time 600;


subnet 192.168.2.0 netmask 255.255.255.0 {
        range 192.168.2.100 192.168.2.199;
        option domain-name-servers 192.168.2.250, 203.30.44.23;
        option domain-name "akshoslaa.local";
        option routers 192.168.2.250;
}

subnet 192.168.3.0 netmask 255.255.255.0 {
        range 192.168.3.100 192.168.3.199;
        option domain-name-servers 192.168.3.250, 203.30.44.23;
        option domain-name "akshoslaa.local";
        option routers 192.168.3.250;
}

zone akshoslaa.local. {
        primary 127.0.0.1;
        key DHCP_UPDATER;
}

zone 2.168.192.in-addr.arpa. {
        primary 127.0.0.1;
        key DHCP_UPDATER;
}

zone 3.168.192.in-addr.arpa. {
         primary 127.0.0.1;
         key DHCP_UPDATER;
}
```

Starting the servers shows no errors... it all _looks_ fine... but the problem persists...
Reading the forums showed a few people with the same problem, but no (documented) solutions...

anyone care to shed some light?

---

### Post by ape on 2005-07-19
akshoslaa,

  The only thing I don't see in the configs above is the dhcp client machines dhclient.conf file.  I have the following lines in my /etc/dhcp3/dhclient.conf file:

   send fqdn.fqdn "<hostname.>";
   send fqdn.encoded on;
   send fqdn.server-update on;

 Make sure to replace the <hostname.> above with your fully qualified hostname followed by a period (i.e. somehost.foo.org.)

This has worked for me.

---

### Post by akshoslaa on 2005-07-19
[QUOTE=ape]akshoslaa,

  The only thing I don't see in the configs above is the dhcp client machines dhclient.conf file.  I have the following lines in my /etc/dhcp3/dhclient.conf file:

   send fqdn.fqdn "<hostname.>";
   send fqdn.encoded on;
   send fqdn.server-update on;

 Make sure to replace the <hostname.> above with your fully qualified hostname followed by a period (i.e. somehost.foo.org.)

This has worked for me.[/QUOTE]
 Brilliant... that's worked.

Now to figure out how to get windows clients to send that... :P
(not that I particularly care, I doubt I'll ever need to refer to them by name... it'd just be nice *shrugs*)

Thanks

[UPDATE]
it appears that windows(xp at least) sends the right info so all is good there...
curious as to why ubuntu's not doing this by default... I assume windows it just tacking it's hostname onto the dns name it's being told by the server... it'd be nice if ubuntu did this (or whatever) aswell...
The whole point of dchp is centeralised network configuration... having to manually set each client kinda defeats the purpose... *shrugs*

---

### Post by souki on 2005-07-19
windows clients send that by default (when configured in dhcp mode)

---

### Post by LordHunter317 on 2005-07-19
You can do it without updating the clients I believe, least I think have it working that way at home.  I'll have to check when I get there.

---

### Post by ermannobonifazi on 2006-08-16
I want just update the DDNS (running on Windows 2003 server) from my ubuntu client (that get DHCP from an hardware appliace (WLAN)). Is that possible?
I tried to se the fqdn setting in dhcp.conf (since I do not run the dhcp server I will not set the rest) but it seems is not sufficent.

---

### Post by ermannobonifazi on 2006-08-17
I was able to get the client update the Windows server (the DHCP server run on an hw appliance) setting:

send fqdn.fqdn "<hostname.>";
send fqdn.encoded off;
send fqdn.server-update off;

---

