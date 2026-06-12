---
title: "Bind &amp; Dynamic DNS"
date: 2007-07-14
forum: Server Platforms
---

### Post by jleiss on 2007-07-14
Just a quick question.. I had bind9 and dhcp3 server passing information back and forth to each other fine when i had a single NIC in the machine. Today I added the second NIC so i could start reouting my internet traffic through this box and it stopped working.. I made no to either of those files regarding updates or the authorization key.. I'm stumped as to why it stopped.

[named.conf]

include "/etc/bind/named.conf.options";

// prime the server with knowledge of the root servers
zone "." {
        type hint;
        file "/etc/bind/db.root";
};

// be authoritative for the localhost forward and reverse zones, and for
// broadcast zones as per RFC 1912

// added on 7/8/07 - update for Dynamic DNS: begin -

key dhcpupdate {
  algorithm hmac-md5;
  secret "j414ooX7bAPnX4m9ToXMsw==";
};

zone "netional.org" {
  type master;
  file "/etc/bind/db.netional.org";
  allow-update { key dhcpupdate; };
};

zone "0.168.192.in-addr.arpa" {
  type master;
  file "/etc/bind/rev.0.168.192.in-addr.arpa";
  allow-update { key dhcpupdate; };
};

// end

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

include "/etc/bind/named.conf.local";

[dhcpd.conf]


ddns-update-style interim;
ignore client-updates;

key dhcpupdate {
  algorithm hmac-md5;
  secret j414ooX7bAPnX4m9ToXMsw==;
};

zone 0.168.192.in-addr.arpa {
  primary dns;
  key dhcpupdate;
}

zone 10.168.192.in-addr.arpa {
  primary dns;
  key dhcpupdate;
}

zone netional.org {
  primary dns;
  key dhcpupdate;
}

---

### Post by Mr. C. on 2007-07-14
You said "it stopped working".  What is "it" ?  Please provide more detail as to what commands work and fail.

Are both NICs configured?
Can each machine ping each other, and a remote host?

You might want to change your now not-so-secret secret.

MrC

---

### Post by jleiss on 2007-07-14
i get unable to forward, connection refused. Both DNS & DHCP are only configured to talk over eth0 which is a local subnet of 192.168.0.0/24. Both NIC's work fine, and all machine's in the house have no problems using the machine as a gateway, just their DHCP addresses aren't being posted to DNS anymore.

---

### Post by Mr. C. on 2007-07-15
I do not see any subnet declarations in your dhcpd.conf file.  You need to declare which subnets the server will provide address for, or it will ignore those networks.

Also, set the authoritative option for your server as well.

dhcpd.conf:
```
...
authoritative;
...
subnet 192.168.0.0 netmask 255.255.255.0 {
   range 192.168.1.10 192.168.1.100;
   ...
}
...
```

MrC

---

### Post by jleiss on 2007-07-15
it's there, just looks like it got cut off with the copy of paste.. here is the whole file again

ignore client-updates;
 
key dhcpupdate {
  algorithm hmac-md5;
  secret j414ooX7bAPnX4m9ToXMsw==;
};

zone 0.168.192.in-addr.arpa {
  primary 127.0.0.1;
  key dhcpupdate;
}

zone netional.org {
  primary 127.0.0.1;
  key dhcpupdate;
}
   
subnet 192.168.0.0 netmask 255.255.255.0 {

   # The range of IP addresses the server
   # will issue to DHCP enabled PC clients
   # booting up on the network
 
   range 192.168.0.100 192.168.0.200;
 
   # Set the amount of time in seconds that
   # a client may keep the IP address

  default-lease-time 86400;
  max-lease-time 86400;
  authoritative;
 
   # Set the default gateway to be used by
   # the PC clients
 
   option routers 192.168.0.1;
   
   # Don't forward DHCP requests from this
   # NIC interface to any other NIC
   # interfaces
 
   option ip-forwarding off;
 
   # Set the broadcast address and subnet mask
   # to be used by the DHCP clients

  option broadcast-address 192.168.0.255;
  option subnet-mask 255.255.255.0;
 
   # Set the DNS server to be used by the
   # DHCP clients
  
  option domain-name "netional.org";
  option domain-name-servers 192.168.0.1;
 
   # Set the NTP server to be used by the
   # DHCP clients
 
   option nntp-server 192.168.0.1;
 
   # If you specify a WINS server for your Windows clients,
   # you need to include the following option in the dhcpd.conf file:

  option netbios-name-servers 192.168.0.254;

---

### Post by Mr. C. on 2007-07-15
Ah, ok good.

How about enable debugging output.  See the -d option in man dhcpd.

MrC

---

### Post by jleiss on 2007-07-17
I was able to resolve my issue. I needed to allow it to listen on local host, as well as add controls back in. Now on to othe fish to fry such as ftp, and getting it to work and respond as a NAT. Thank you for your help.

---

### Post by Mr. C. on 2007-07-17
Excellent.  Best of luck!

MrC

---

