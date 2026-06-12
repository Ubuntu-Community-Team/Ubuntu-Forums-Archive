---
title: "bind9 not starting on boot (Trying Again)"
date: 2011-03-01
forum: Server Platforms
---

### Post by hawkmage on 2011-03-01
Since I have not gotten anything on the "General Help" I am posting this here:

When a Ubuntu 10.10 I have starts up apache2, MySQL and postfix start properly but bind9 doesn't. Once booted is I run 'sudo /etc/init.d/bind9 start' it starts.

The only thing odd on this system is I have a "inet6 v4tunnel" interface defined in my /etc/network/interfaces.

From booting in the syslog there is:
```
/var/log/syslog:Feb 28 19:02:42 ubuntu named[1029]: starting BIND 9.7.1-P2 -u bind -d 9
/var/log/syslog:Feb 28 19:02:42 ubuntu named[1029]: built with '--prefix=/usr' '--mandir=/usr/share/man' '--infodir=/usr/share/info' '--sysconfdir=/etc/bind' '--localstatedir=/var' '--enable-threads' '--enable-largefile' '--with-libtool' '--enable-shared' '--enable-static' '--with-openssl=/usr' '--with-gssapi=/usr' '--with-gnu-ld' '--with-dlz-postgres=no' '--with-dlz-mysql=no' '--with-dlz-bdb=yes' '--with-dlz-filesystem=yes' '--with-dlz-ldap=yes' '--with-dlz-stub=yes' '--with-geoip=/usr' '--enable-ipv6' 'CFLAGS=-fno-strict-aliasing -DDIG_SIGCHASE -O2' 'LDFLAGS=-Wl,-Bsymbolic-functions' 'CPPFLAGS='
/var/log/syslog:Feb 28 19:02:42 ubuntu named[1029]: adjusted limit on open files from 1024 to 1048576
/var/log/syslog:Feb 28 19:02:42 ubuntu named[1029]: found 2 CPUs, using 2 worker threads
/var/log/syslog:Feb 28 19:02:42 ubuntu named[1029]: using up to 4096 sockets
```Where as running 'sudo /etc/init.d/bind9 start' once booted I get:
```
/var/log/syslog:Feb 28 19:14:51 ubuntu named[2792]: starting BIND 9.7.1-P2 -u bind -d 9
/var/log/syslog:Feb 28 19:14:51 ubuntu named[2792]: built with '--prefix=/usr' '--mandir=/usr/share/man' '--infodir=/usr/share/info' '--sysconfdir=/etc/bind' '--localstatedir=/var' '--enable-threads' '--enable-largefile' '--with-libtool' '--enable-shared' '--enable-static' '--with-openssl=/usr' '--with-gssapi=/usr' '--with-gnu-ld' '--with-dlz-postgres=no' '--with-dlz-mysql=no' '--with-dlz-bdb=yes' '--with-dlz-filesystem=yes' '--with-dlz-ldap=yes' '--with-dlz-stub=yes' '--with-geoip=/usr' '--enable-ipv6' 'CFLAGS=-fno-strict-aliasing -DDIG_SIGCHASE -O2' 'LDFLAGS=-Wl,-Bsymbolic-functions' 'CPPFLAGS='
/var/log/syslog:Feb 28 19:14:51 ubuntu named[2792]: adjusted limit on open files from 1024 to 1048576
/var/log/syslog:Feb 28 19:14:51 ubuntu named[2792]: found 2 CPUs, using 2 worker threads
/var/log/syslog:Feb 28 19:14:51 ubuntu named[2792]: using up to 4096 sockets
/var/log/syslog:Feb 28 19:14:51 ubuntu named[2792]: loading configuration from '/etc/bind/named.conf'
/var/log/syslog:Feb 28 19:14:51 ubuntu named[2792]: reading built-in trusted keys from file '/etc/bind/bind.keys'
/var/log/syslog:Feb 28 19:14:51 ubuntu named[2792]: using default UDP/IPv4 port range: [1024, 65535]
/var/log/syslog:Feb 28 19:14:51 ubuntu named[2792]: using default UDP/IPv6 port range: [1024, 65535]
/var/log/syslog:Feb 28 19:14:51 ubuntu named[2792]: listening on IPv6 interfaces, port 53
/var/log/syslog:Feb 28 19:14:51 ubuntu named[2792]: listening on IPv4 interface lo, 127.0.0.1#53
/var/log/syslog:Feb 28 19:14:51 ubuntu named[2792]: listening on IPv4 interface eth0, XXX.XXX.XXX.XXX#53
/var/log/syslog:Feb 28 19:14:51 ubuntu named[2792]: generating session key for dynamic DNS
/var/log/syslog:Feb 28 19:14:51 ubuntu named[2792]: set up managed keys zone for view _default, file 'managed-keys.bind'
/var/log/syslog:Feb 28 19:14:51 ubuntu named[2792]: automatic empty zone: 254.169.IN-ADDR.ARPA
/var/log/syslog:Feb 28 19:14:51 ubuntu named[2792]: automatic empty zone: 2.0.192.IN-ADDR.ARPA
/var/log/syslog:Feb 28 19:14:51 ubuntu named[2792]: automatic empty zone: XXX.XXX.XXX.IN-ADDR.ARPA
/var/log/syslog:Feb 28 19:14:51 ubuntu named[2792]: automatic empty zone: 113.0.203.IN-ADDR.ARPA
/var/log/syslog:Feb 28 19:14:51 ubuntu named[2792]: automatic empty zone: 255.255.255.255.IN-ADDR.ARPA
/var/log/syslog:Feb 28 19:14:51 ubuntu named[2792]: automatic empty zone: X.X.X.X.X.X.X.X.X.X.X.X.X.X.X.X.X.X.X.X.X.X.X.X.X.X.X.X.X.X.X.X.IP6.ARPA
/var/log/syslog:Feb 28 19:14:51 ubuntu named[2792]: automatic empty zone: X.X.X.X.X.X.X.X.X.X.X.X.X.X.X.X.X.X.X.X.X.X.X.X.X.X.X.X.X.X.X.X.IP6.ARPA
/var/log/syslog:Feb 28 19:14:51 ubuntu named[2792]: automatic empty zone: D.F.IP6.ARPA
/var/log/syslog:Feb 28 19:14:51 ubuntu named[2792]: automatic empty zone: 8.E.F.IP6.ARPA
/var/log/syslog:Feb 28 19:14:51 ubuntu named[2792]: automatic empty zone: 9.E.F.IP6.ARPA
/var/log/syslog:Feb 28 19:14:51 ubuntu named[2792]: automatic empty zone: A.E.F.IP6.ARPA
/var/log/syslog:Feb 28 19:14:51 ubuntu named[2792]: automatic empty zone: B.E.F.IP6.ARPA
/var/log/syslog:Feb 28 19:14:51 ubuntu named[2792]: automatic empty zone: 8.B.D.0.1.0.0.2.IP6.ARPA
/var/log/syslog:Feb 28 19:14:51 ubuntu named[2792]: automatic empty zone: 0.1.1.0.0.2.IP6.ARPA
/var/log/syslog:Feb 28 19:14:51 ubuntu named[2792]: command channel listening on 127.0.0.1#953
/var/log/syslog:Feb 28 19:14:51 ubuntu named[2792]: zone 0.in-addr.arpa/IN: loaded serial 1
/var/log/syslog:Feb 28 19:14:51 ubuntu named[2792]: zone 127.in-addr.arpa/IN: loaded serial 1
/var/log/syslog:Feb 28 19:14:51 ubuntu named[2792]: zone XXX.XXX.XXX.in-addr.arpa/IN: loaded serial 110113000
/var/log/syslog:Feb 28 19:14:51 ubuntu named[2792]: zone XXX.XXX.XXX.in-addr.arpa/IN: loaded serial 109030502
/var/log/syslog:Feb 28 19:14:51 ubuntu named[2792]: zone 255.in-addr.arpa/IN: loaded serial 1
/var/log/syslog:Feb 28 19:14:51 ubuntu named[2792]: zone X.X.X.X.X.X.X.X.X.X.X.X.X.X.X.X.ip6.arpa/IN: loaded serial 110128000
/var/log/syslog:Feb 28 19:14:51 ubuntu named[2792]: zone mydomain.com.com/IN: loaded serial 110127002
/var/log/syslog:Feb 28 19:14:51 ubuntu named[2792]: zone localhost/IN: loaded serial 1
/var/log/syslog:Feb 28 19:14:51 ubuntu named[2792]: zone myotherdomain.com/IN: loaded serial 110127002
/var/log/syslog:Feb 28 19:14:51 ubuntu named[2792]: managed-keys-zone ./IN: loading from master file managed-keys.bind failed: file not found
/var/log/syslog:Feb 28 19:14:51 ubuntu named[2792]: managed-keys-zone ./IN: loaded serial 0
/var/log/syslog:Feb 28 19:14:51 ubuntu named[2792]: zone X.X.X.X.X.X.X.X.X.X.X.X.X.X.X.X.ip6.arpa/IN: sending notifies (serial 110128000)
/var/log/syslog:Feb 28 19:14:51 ubuntu named[2792]: zone XXX.XXX.XXX.in-addr.arpa/IN: sending notifies (serial 110113000)
/var/log/syslog:Feb 28 19:14:51 ubuntu named[2792]: zone mydomain.com/IN: sending notifies (serial 110127002)
/var/log/syslog:Feb 28 19:14:51 ubuntu named[2792]: zone myotherdomain.com/IN: sending notifies (serial 110127002)
/var/log/syslog:Feb 28 19:14:51 ubuntu named[2792]: running
```Even with the bind debug level at set at 90 I do not get any more in the logs that what I posted before. The lack of errors in the logs is giving me no idea where to start.

I commented out the IPv6 tunnel interface and rebooted and still no help. bind still is not starting at boot.

OK, it is not a permissions issue, I have changed the config and zone files to be owned by bind:bind, root:bind, root:root and bind:root and it has made no difference.

Doing a fresh install on a Virtual Box VM and configure it in a similar manner bind9 starts normally. (I am almost to the point where I will rebuild the box)

---

### Post by elico on 2011-03-02
well you dont need to disable the IPV6 tunnel just enable the ipv4 mask for usage on the bind.conf file using 
this lines(at the begining of the file):
> #allow local usage and lan usage:
acl lan {
        127.0.0.0/8;
        192.168.0.0/16;
        };



and change the 192 subnet to your lan subnet .

i didnt see if you had a post on int before but it is so simple to use bind so you will get it right.

---

### Post by headvampyre@hotmail.co.uk on 2011-03-02
Please could you post your configuration file for Bind9, this could seriously help in sorting the issue :)

---

### Post by hawkmage on 2011-03-02
elico:
bind is working just fine if I start it manually.  

[EMAIL="headvampyre@hotmail.co.uk"]headvampyre@hotmail.co.uk[/EMAIL]:
I don't think is the a config issue, I installed a new instance of Ubuntu 10.10 in a VM and copied the config over and bind starts properly on boot but here they are:

/etc/bind/named.conf
```
// This is the primary configuration file for the BIND DNS server named.
//
// Please read /usr/share/doc/bind/README.Debian for information on the 
// structure of BIND configuration files in Debian for BIND versions 8.2.1 
// and later, *BEFORE* you customize this configuration file.
//
include "/etc/bind/rndc.key";

controls {
    inet 127.0.0.1 port 953
    allow { 127.0.0.1; } keys { "rndc-key"; };
};

include "/etc/bind/named.conf.options";

// reduce log verbosity on issues outside our control
logging {
    category lame-servers { null; };
//    category cname { null; };
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
        file "/etc/bind/db.localhost";
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

// add local zone definitions here
include "/etc/bind/named.conf.local";
```/etc/bind/named.conf.options
```
options {
    directory "/var/cache/bind";

    // If there is a firewall between you and nameservers you want
    // to talk to, you may need to fix the firewall to allow multiple
    // ports to talk.  See http://www.kb.cert.org/vuls/id/800113

    // If your ISP provided one or more IP addresses for stable 
    // nameservers, you probably want to use them as forwarders.  
    // Uncomment the following block, and insert the addresses replacing 
    // the all-0's placeholder.

     forwarders { 208.67.222.222; 208.67.220.220; };

    auth-nxdomain no;    # conform to RFC1035
    listen-on-v6 { any; };

    };
};
```/etc/bind/named.conf.local 
```
//
// Add local zone definitions here.
zone "mydomain.com" {
        type master;
        file "/etc/bind/db.mydomain";
    allow-transfer { 192.168.XXX.0/24 ; 192.168.YYY.0/24 ; 216.218.130.2/32 ; };
};

zone "myotherdomain.com" {
        type master;
        file "/etc/bind/db.myotherdomain";
    allow-transfer { 192.168.XXX.0/24 ; 192.168.YYY.0/24 ; 216.218.130.2/32 ; };
};

zone "XXX.168.192.in-addr.arpa" in {
        type master;
        file "/etc/bind/db.XXX.168.192";
    allow-transfer { 192.168.XXX.0/24 ; 192.168.YYY.0/24 ; };
};

zone "YYY.168.192.in-addr.arpa" in {
        type master;
        file "/etc/bind/db.YYY.168.192";
    allow-transfer { 192.168.XXX.0/24 ; 192.168.YYY.0/24 ; };
};

zone "Z.Z.Z.Z.Z.Z.Z.Z.Z.Z.Z.Z.Z.Z.Z.Z.ip6.arpa" {
        type master;
        file "/etc/bind/db.Z.Z.Z.Z.Z.Z.Z.Z.Z.Z.Z.Z.Z.Z.Z.Z";
};
```

---

### Post by hawkmage on 2011-03-04
No more thought or suggestions.  I am almost to the point of throwing annother drive in the box and doing a clean install and set things up again starting with BIND and see if there is a point in the configuration where BIND starting breaks.

---

### Post by headvampyre@hotmail.co.uk on 2011-03-04
Hmm :/ try a clean install of bind (backup your config files for it first). Does /etc/bind/rndc.key exist? i find that occasionally ubuntu will just dump it in /etc, so i copy to /etc/bind aswell.

---

### Post by hawkmage on 2011-03-04
Yes the /etc/bind/rndc.key exists.  I already have a backup of my BIND config having tested it on a VM.

I will do the removal and reinstall of BIND9 and see if that helps.  Luckily this is not the DNS server my systems query, I use slave DNS servers for that which get their zone info from this one.

---

### Post by headvampyre@hotmail.co.uk on 2011-03-04
yeah, usually a reinstall of bind9 will fix the issues. I've seen it happen lots of times before. It should sort the issues.

---

### Post by hawkmage on 2011-03-04
After running:
```
sudo apt-get purge bind9 bind9-doc bind9-host bind9utils
sudo apt-get autoclean
sudo rm -Rf /etc/bind
```

Then rebooting.  Then running:
```
sudo apt-get install bind9 bind9-doc bind9utils
sudo /etc/init.d/bind9 stop
```
and restoring my bind config and starting bind9 it ran and I could query it.

After rebooting it still did not start.  So a clean install of bind9 did not help either.

---

### Post by headvampyre@hotmail.co.uk on 2011-03-05
Hi, im thinking im stupid now... Have you tried running:

sudo update-rc.d bind9 defaults

This adds the init file to the rc.* folder in /etc and *should* cause the script to be run at boot.
Or, if that doesnt work, you could always add:

/etc/init.d/bind9 start

to /etc/rcS :)
hope this works :)

---

### Post by hawkmage on 2011-03-05
Running the command you gave gave me this:
```
hawkmage@ubuntu:~$ sudo update-rc.d bind9 defaults
 System start/stop links for /etc/init.d/bind9 already exist.
hawkmage@ubuntu:~$
```

Did not help.

There is no /etc/rcS file there is a /etc/rcS.d directory.

The thing is that the syslog shows that BIND is trying to start on boot but just stops with out giving an error.

---

### Post by headvampyre@hotmail.co.uk on 2011-03-05
Oh, sorry, i meant /etc/init.d/rcS :/ Try adding it to that.

---

### Post by hawkmage on 2011-03-05
Made no difference.  I still see that bind begins to start up and stops without an error or any indication of why.

---

### Post by headvampyre@hotmail.co.uk on 2011-03-05
Hmm :/ Is it running in a CHROOT'ed environment? That could potentially cause issues i guess :/ Ive never seen an issue like this before, normally if it had errors starting at boot you wouldnt be able to start it anyway :/ Try running a similar setup in a Virtual Machine and see if it runs fine then, it could be a brolen system :/

---

### Post by hawkmage on 2011-03-06
It is not a chroot environment.  I have taken the config and put it in a VM and it works I did not set up the IPv6 tunnel on the VM but I did remove the tunnel on the "broken" system and it didn't help.  

I was hoping to avoid rebuilding the box.

---

### Post by hawkmage on 2011-05-27
OK, I finally figured this out.  The root of this issue was the same as in my problem with sshd starting.  

It was being caused by a change I had made to my openssl.cnf to use the HOME environment variable.

I added the following line to the /etc/init.d/bind9  after the INIT Info section to fix this:
```
if [ "${HOME}" = "" ]; then export HOME="/var/cache/bind";fi
```

---

### Post by elico on 2011-05-28
and why the if?
just make the export HOME....
in any case it will not change...

---

### Post by hawkmage on 2011-05-28
True but I out of habit I was just setting it only if it is not already set.

I am thinking that it will be better for me to make a copy of the system openssl.cnf in my home directory and use the OPENSSL_CONF environment variable pointing to it.

---

### Post by elico on 2011-05-29
it's a good idea.
and also i recommend for you to make a daily or weekly "/etc/"  backup into a tar\gz file.

---

### Post by hawkmage on 2011-05-29
Having worked on Unix/Linux for many years I have never found a reason to make an automatic backup of /etc.  When I make a change I first make a copy of the file I am going to modify with a date/time stamp added to the name and once I have a working change I do make a tarball of the config.  

I have been using the updated openssl.cnf in Ubuntu, RedHat/CentOS for years and it is only recent updates that have started being affected.  A backup would not have made a difference.  

To me the biggest issue is that the services that have failed because of the openssl.cnf fail without any real error.  With sshd it worked on Ubuntu 10.04 but not 10.10 and I only got a cryptic error about "STR_COPY:variable has no value:conf_def.c" only after I turned on debuging.  With bind9 I never got an error.  From what I can find this all stems from changes made to how openssl loads its config which makes it harder to catch the error but to fail without anything makes things hard to troubleshoot.

---

### Post by elico on 2011-05-30
Well you have a good and nice working way!!
i always do some auto-backup cause i know i have loose mind some times.
it never costs money so... who cares for 1-3 MB of backup?

---

