---
title: "bind9 question"
date: 2008-11-13
forum: Server Platforms
---

### Post by fouadk on 2008-11-13
hi everyone...

i am trying to install a secondary dns server to my windows server 2003 dns server...

the problem is that my secondary zone does not get updated

this is my configuration:

```
acl "BCCUpdaters"{
        192.168.100.111
};

zone "bcc.ndu.edu.lb"{
        type slave;
        file "/etc/bind/forward/bcc.ndu.edu.lb";
        masters { 192.168.100.111; };
        allow-update {any;};
};

```

this is the output of my syslog after a restart to the bind9 daemon:

```

Nov 14 05:08:12 rohan named[9100]: running
Nov 14 05:08:12 rohan named[9100]: zone bcc.ndu.edu.lb/IN: Transfer started.
Nov 14 05:08:12 rohan named[9100]: transfer of 'bcc.ndu.edu.lb/IN' from 192.168.100.111#53: connected using 192.168.100.111#47317
Nov 14 05:08:12 rohan named[9100]: dumping master file: /etc/bind/forward/tmp-08AeCnBn1s: open: permission denied
Nov 14 05:08:12 rohan named[9100]: transfer of 'bcc.lau.edu.lb/IN' from 172.16.50.12#53: failed while receiving responses: permission denied
Nov 14 05:08:12 rohan named[9100]: transfer of 'ndu.lau.edu.lb/IN' from 172.16.50.12#53: end of transfer

```

i have even tried to give chmoding the forward file to 777(which is a stupid thing to do....i did it for debugging purposes) 

please help

thanks in advance

---

### Post by oneloveamaru on 2008-11-13
You need to go onto the Windows Server, log into the DNS console, check the Name Servers tab and make sure this server is listed as a name server. THEN, you need to check the Zone Transfers tab and make sure it says to Allow zone transfers and another option below it. I usually check the "Only to servers listed on the Name Servers tab" for security.

---

### Post by fouadk on 2008-11-13
i did that....nothing

---

### Post by oneloveamaru on 2008-11-13
Permission denied means your slave does not have permissions. Easy as that. Windows sees the incoming zone request from the IP address, it tries to map it to an A record, then looks at it's security tab to see who can pull that zone down. If you have 5 zones, you need to do what I said to every single forward zone on your windows server. If your BIND slave server is going out on a different IP, then that will give you permission denied. Check your named.conf.options to make sure the transfer and notify source are using the IP that Windows has for that A record.

---

### Post by fouadk on 2008-11-13
this is my /etc/hosts

```

127.0.0.1       localhost
192.168.100.112    rohan.bcc.ndu.edu.lb    rohan
192.168.100.111    hippy.bcc.ndu.edu.lb    hippy

```

this is my named.conf.options

```

options {
        directory "/var/cache/bind";

        // If there is a firewall between you and nameservers you want
        // to talk to, you might need to uncomment the query-source
        // directive below.  Previous versions of BIND always asked
        // questions using port 53, but BIND 8.1 and later use an unprivileged
        // port by default.

        // query-source address * port 53;

        // If your ISP provided one or more IP addresses for stable
        // nameservers, you probably want to use them as forwarders.
        // Uncomment the following block, and insert the addresses replacing
        // the all-0's placeholder.

        forwarders {
                192.168.104.208;
                192.168.5.35;
        };

        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
};

```

this is my /etc/network/interface

```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.100.112
        netmask 255.255.255.0
        network 192.168.100.0
        broadcast 172.16.50.255
        gateway 192.168.100.254
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 192.168.100.111
        dns-search bcc.ndu.edu.lb
~

```


i have added the ubuntu server to the windows dns server

what could be possibly wrong

---

### Post by oneloveamaru on 2008-11-13
Add these into named.conf.options under the directory line...

        listen-on { 127.0.0.1; };
        listen-on { 192.168.100.112; };

then add these lines under the query-source address that is commented out.

        transfer-source 192.168.100.112 port 53;
        notify-source 192.168.100.112 port 53;

That will make it a little nicer but I still think your config is wrong on the Windows side too.

Let me see a screen shot of the A record for this BIND server in windows, a screen shot of the Name Servers tab for the "bcc.ndu.edu.lb" zone and then a screen shot of the Zone Transfers tab for the same zone.

---

