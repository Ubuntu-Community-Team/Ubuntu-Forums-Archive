---
title: "Should I use bind or is there an easier way?"
date: 2005-11-18
forum: Server Platforms
---

### Post by senectus on 2005-11-18
I have a DNS problem with my home network
The network looks like this :
[IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=3679&stc=1&d=1132308936[/IMG]

The problem I'm having is that inside my network the domain name modmeup.net resolves to the router.. and that's it.. 
It will only do the port forwarding (NAPT) if the connection comes from outside the network.. it doesn't seem bright enough to forward internally.

that wouldn't be a big problem except that the php scrips in WordPress keep pointing to 192.168.254.2 (the server internal address), If I change them to modmeup.net then it breaks the templates because it resolves that to the gateway device.. and the gateway device doesn't forward those requests back inside.

So what is the best solution for this sort of problem?

---

### Post by pingswept on 2005-11-18
Nice diagram.

There are two standard solutions that I know of:

1. Distribute /etc/hosts files to each of the computers on the network. The hosts file simply lists known hosts. When you add a machine to the network, you update all of the /etc/hosts files with the new name. This is a great solution for a small network that won't grow.

2. The DNS system is designed to solve exactly the same situation when the network grows enough that distributing hosts files is tedious. You can install BIND and add a file called db.intranet in /etc/bind. You then configure all the machines on the network to use the local DNS server first (which will also cache lookups for you, by default, which is a nice bonus). When you need to add a new host, you just add it to the db.intranet file.

I manage a small network of around 35 machines and a few servers. Whenever anyone wants a website, I add a new Apache virtual host, add a new entry to db.intranet, reload, and I'm done. Setting up BIND is not trivial, but you don't have to be Paul Vixie to succeed.

---

### Post by senectus on 2005-11-18
Ok.. sounds like BIND might be what I want.. as I'm really not a big fan of the hosts file solution.. it'll bite me on the arse later.

I've also been suggested pdns and dnsmasq do you know if they'd be a good idea?

btw.. who is Paul Vixie? :confused:

---

### Post by pingswept on 2005-11-18
I have only used BIND. It's what ~70% of DNS servers on the public web are running. Here's a survey from last summer: [http://mydns.bboy.net/survey/](http://mydns.bboy.net/survey/)

On the other hand, maybe configuring pdns or dnsmasq is easier. Myself, I stick with BIND because so many other people know how to configure it. Earlier versions of BIND have had security problems, but I think BIND 9 is believed to be more secure. If you are a security nut, you might look at djbdns, an ultra-secure DNS server written by Daniel J. Bernstein, the slightly neurotic author of qmail.

Paul Vixie is the guy who wrote BIND. He regularly posts on the NANOG list; his posts tend to be funny and extremely correct.

---

### Post by senectus on 2005-11-18
yeah.. I guess I really need to learn BIND anyhow :-P

Thanks mate..
uh, any suggestions for good Ubuntu package related howto's on BIND9 ?

---

### Post by pingswept on 2005-11-18
Here are some sample files from my server:


/etc/bind/db.intranet
---------------------------------------------------
; BIND data file called db.intranet
;
$ORIGIN yourdomain.org.
$TTL    604800
@       IN      SOA     ns1.yourdomain.org. you.yourdomain.org. (
                              1         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
        IN      NS      ns1.yourdomain.org.
ns1     IN      A       192.168.1.2
ns2     IN      A       192.168.1.3
calendar        IN      A       192.168.1.2
database        IN      A       192.168.1.40
help    IN      A       192.168.1.2
www     IN      A       65.217.206.23
@       IN      A       65.217.206.23

/etc/bind/named.conf
----------------------------------------------
// This is the primary configuration file for the BIND DNS server named.
//
// Please read /usr/share/doc/bind9/README.Debian.gz for information on the
// structure of BIND configuration files in Debian, *BEFORE* you customize
// this configuration file.
//
// If you are just adding zones, please do that in /etc/bind/named.conf.local
key "rndc-key" {
      algorithm hmac-md5;
      secret "your_rndc_key_goes_here";
};
controls {
      inet 127.0.0.1 port 953
      allow { 127.0.0.1; } keys { "rndc-key"; };
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

zone "yourdomain.org" {
        type master;
        file "/etc/bind/db.intranet";
};

I think that *might* be the only files I changed from the default Breezy install. I had to screw around with the rndc.key file a little, but I don't recall the details.

Useful commands:
rndc status
rndc reload
/etc/init.d/bind9 restart
ps -A | grep named


Good luck.

---

### Post by squirrelyosis on 2005-11-18
Bind can seem overwhelming at first but it's not that difficult to setup.  I just got done setting up bind yesterday.  You have to install BIND, then put the DNS servers of your ISP as forwarders.  Also open up port 53 if you have a firewall.  At this point it can resolve and cache DNS requests on it's own.  Then you have to make BIND the master for your internal zone as you see in ping's .conf file. Then you have to setup static mappings as you see in pingswept's db.intranet file.  To resolve say linuxbox1 to 192.168.1.x It gets kinda tricky.  This link helped me get started.  It will setup BIND9 in a chroot environment [http://www.howtoforge.com/perfect_setup_ubuntu_5.10_p3](http://www.howtoforge.com/perfect_setup_ubuntu_5.10_p3)
Good site BTW. 

Your files will be different, don't just copy/paste.  This is from my SUSE 10 server.  Ubuntu desktop, SUSE server.  I try to keep it fresh!

Here's my named.conf
# Copyright (c) 2001-2004 SuSE Linux AG, Nuernberg, Germany.
# All rights reserved.
#
# Author: Frank Bodammer, Lars Mueller <lmuelle@suse.de>
#
# /etc/named.conf
#
# This is a sample configuration file for the name server BIND 9.  It works as
# a caching only name server without modification.
#
# A sample configuration for setting up your own domain can be found in
# /usr/share/doc/packages/bind/sample-config.
#
# A description of all available options can be found in
# /usr/share/doc/packages/bind/misc/options.

options {

        # The directory statement defines the name server's working directory

        directory "/var/lib/named";

        # Write dump and statistics file to the log subdirectory.  The
        # pathenames are relative to the chroot jail.

        dump-file "/var/log/named_dump.db";
        statistics-file "/var/log/named.stats";

        # The forwarders record contains a list of servers to which queries
        # should be forwarded.  Enable this line and modify the IP address to
        # your provider's name server.  Up to three servers may be listed.

        #forwarders { 68.87.64.146; 68.87.75.194; };

        # Enable the next entry to prefer usage of the name server declared in
        # the forwarders section.

        #forward first;

        # The listen-on record contains a list of local network interfaces to
        # listen on.  Optionally the port can be specified.  Default is to
        # listen on all interfaces found on your system.  The default port is
        # 53.

        #listen-on port 53 { 127.0.0.1; };

        # The listen-on-v6 record enables or disables listening on IPv6
        # interfaces.  Allowed values are 'any' and 'none' or a list of
        # addresses.

        listen-on-v6 { any; };

        # The next three statements may be needed if a firewall stands between
        # the local server and the internet.

        #query-source address * port 53;
        #transfer-source * port 53;
        #notify-source * port 53;

        # The allow-query record contains a list of networks or IP addresses
        # to accept and deny queries from. The default is to allow queries
        # from all hosts.

        #allow-query { 127.0.0.1; };

        # If notify is set to yes (default), notify messages are sent to other
        # name servers when the the zone data is changed.  Instead of setting
        # a global 'notify' statement in the 'options' section, a separate
        # 'notify' can be added to each zone definition.

        notify no;
        include "/etc/named.d/forwarders.conf";
};

# To configure named's logging remove the leading '#' characters of the
# following examples.
#logging {
#       # Log queries to a file limited to a size of 100 MB.
#       channel query_logging {
#               file "/var/log/named_querylog"
#                       versions 3 size 100M;
#               print-time yes;                 // timestamp log entries
#       };
#       category queries {
#               query_logging;
#       };
#
#       # Or log this kind alternatively to syslog.
#       channel syslog_queries {
#               syslog user;
#               severity info;
#       };
#       category queries { syslog_queries; };
#
#       # Log general name server errors to syslog.
#       channel syslog_errors {
#               syslog user;
#               severity error;
#       };
#       category default { syslog_errors;  };
#
#       # Don't log lame server messages.
#       category lame-servers { null; };
#};

# The following zone definitions don't need any modification.  The first one
# is the definition of the root name servers.  The second one defines
# localhost while the third defines the reverse lookup for localhost.

zone "." in {
        type hint;
        file "root.hint";
};

zone "localhost" in {
        type master;
        file "localhost.zone";
};

zone "0.0.127.in-addr.arpa" in {
        type master;
        file "127.0.0.zone";
};

# Include the meta include file generated by createNamedConfInclude.  This
# includes all files as configured in NAMED_CONF_INCLUDE_FILES from
# /etc/sysconfig/named

include "/etc/named.conf.include";
logging {
        category default { log_syslog; };
        channel log_syslog { syslog; };
};
zone "yourdomain.com" in {
        file "master/yourdomain.com";
        type master;
};
zone "1.168.192.in-addr.arpa" in {
        file "master/1.168.192.in-addr.arpa";
        type master;
};

# You can insert further zone records for your own domains below or create
# single files in /etc/named.d/ and add the file names to
# NAMED_CONF_INCLUDE_FILES.
# See /usr/share/doc/packages/bind/README.SUSE for more details.


*Note: 
        zone "yourdomain.com" in {
        file "master/yourdomain.com";
        type master;

That part specifies that BIND is the master for that domain, the zone after is the reverse lookup of it.  That will create a the folder /var/lib/named/master  This is where ping's db.intranet could have been.  Either way these are the 2 files in the "master" folder
- 1.168.192.in-addr.arpa
- yourdomain.com

First is the reverse lookup zone, second is the forward.  
Here is my yourdomain.com file 
$TTL 2D
@               IN SOA          yourbindserver.yourdomain.com.     root.yourbindserver.yourdomain.com. (
                                2005111700      ; serial
                                3H              ; refresh
                                1H              ; retry
                                1W              ; expiry
                                1D )            ; minimum
                NS      homeserv
localhost       A       127.0.0.1
homeserv        A       192.168.1.101
linuxbox        A       192.168.1.103
router          A       192.168.1.102

This is the reverse zone file 
$TTL 2D
@               IN SOA          yourbindserver.yourdomain.com.      root.yourbindserver.yourdomain.com. (
                                2005111700      ; serial
                                3H              ; refresh
                                1H              ; retry
                                1W              ; expiry
                                1D )            ; minimum
                NS      homeserv.trevors.no-ip.org.
1               PTR     homeserv.trevors.no-ip.org.
2               PTR     linuxbox.trevors.no-ip.org.
3               PTR     router.trevors.no-ip.org.

Give it a go!

---

### Post by sect2k on 2005-11-19
I've been using djbdns for over two years, and I have nothing but praise for it.

It's easy to administer, unlike bind, and also very secure. Setting it up might be a bit tricky, but it's all smooth sailing afterwards.

For more info check out [http://cr.yp.to/djbdns.html](http://cr.yp.to/djbdns.html).

Cheers,
/me

---

