---
title: "DHCP server won't start. Gives 'Not configured to listen on any interfaces!'"
date: 2014-10-13
forum: Server Platforms
---

### Post by THPubs on 2014-10-13
I have just setup isc-dhcp on my server. I even setup the correct interface. But still the dhcp server won't boot. Its says `Not configured to listen on any interfaces!` in the syslog. And when I try `dhcpd -t /etc/dhcp/dhcpd.conf` it gives this error : `/etc/dhcp/dhcpd.conf: interface name too long (is 20`


Here's my dhcpd.conf :


```
    ddns-update-style none;


    option domain-name "thpi";
    option domain-name-servers 208.67.222.222, 208.67.220.220;


    default-lease-time 86400;
    max-lease-time 604800;


    authoritative;


    # Use this to send dhcp log messages to a different log file (you also
    # have to hack syslog.conf to complete the redirection).
    log-facility local7;




    subnet 10.0.0.0 netmask 255.255.255.0 {
        ## dhcp start  and end IP range ##
        range 10.0.0.20 10.0.0.90;
        option subnet-mask 255.255.255.0;     ## subnet
        option broadcast-address 10.0.0.255; ## broadcast
        option routers 10.0.0.1; ## router IP




        host pc1 {
            hardware ethernet 60:a4:4c:3d:76:fa;
            fixed-address 10.0.0.100;
        }


        host lap1 {
            hardware ethernet 6c:71:d9:1e:f3:4f;
            fixed-address 10.0.0.150;
        }


        host thnote {
            hardware ethernet d0:22:be:d3:be:e1;
            fixed-address 10.0.0.200;
        }
    }

```

`/etc/default/isc-dhcp-server` file :


```
    # Defaults for isc-dhcp-server initscript
    # sourced by /etc/init.d/isc-dhcp-server
    # installed at /etc/default/isc-dhcp-server by the maintainer scripts


    #
    # This is a POSIX shell fragment
    #


    # Path to dhcpd's config file (default: /etc/dhcp/dhcpd.conf).
    #DHCPD_CONF=/etc/dhcp/dhcpd.conf


    # Path to dhcpd's PID file (default: /var/run/dhcpd.pid).
    #DHCPD_PID=/var/run/dhcpd.pid


    # Additional options to start dhcpd with.
    #       Don't use options -cf or -pf here; use DHCPD_CONF/ DHCPD_PID instead
    #OPTIONS=""


    # On what interfaces should the DHCP server (dhcpd) serve DHCP requests?
    #       Separate multiple interfaces with spaces, e.g. "eth0 eth1".
    INTERFACES="eth0:0"

```

Interfaces file :


```
    auto lo


    iface lo inet loopback


    auto eth0
    iface eth0 inet static
    address 192.168.1.10
    netmask 255.255.255.0
    network 192.168.1.0
    broadcast 192.168.1.255
    gateway 192.168.1.1


    auto eth0:0
    iface eth0:0 inet static
    name Lan
    address 10.0.0.1
    netmask 255.255.255.0
    network 10.0.0.0


    allow-hotplug wlan0
    iface wlan0 inet manual
    wpa-roam /etc/wpa_supplicant/wpa_supplicant.conf
    iface default inet dhcp

```

What might be the issue?

---

### Post by SeijiSensei on 2014-10-13
Virtual interfaces usually have addresses in the same subnet as the base interface.  So you can set eth0:0 to, say, 192.168.1.20, but not to an address in 10/8.

Perhaps you should explain to us what you are trying to accomplish with the arrangement you have now.

---

### Post by THPubs on 2014-10-13
Actually im trying to build a proxy. The 10.0.0.0 network is for the clients. It works well for the proxy. Isn't there a way to fix this without changing this?

---

### Post by Doug S on 2014-10-13
As a side note, I do not think that pc1 and thnote should be trying to get the same IP address.

---

### Post by THPubs on 2014-10-13
> **Doug S said:**
> As a side note, I do not think that pc1 and thnote should be trying to get the same IP address.


Thanks a lot. I fixed it but still the problem is there!

---

### Post by SeijiSensei on 2014-10-13
> **THPubs said:**
> Actually im trying to build a proxy. The 10.0.0.0 network is for the clients. It works well for the proxy. Isn't there a way to fix this without changing this?
You'd be much better off adding a second network card, assigning it to the 10 network, then binding the DHCP server to that interface.

---

### Post by THPubs on 2014-10-13
> **SeijiSensei said:**
> You'd be much better off adding a second network card, assigning it to the 10 network, then binding the DHCP server to that interface.

Adding another card is a bit difficult because this is a Raspberrypi :-)

---

### Post by THPubs on 2014-10-13
Any other way to fix this?

---

### Post by SeijiSensei on 2014-10-14
> **THPubs said:**
> Adding another card is a bit difficult because this is a Raspberrypi :-)

Use a [USB adapter]("http://www.newegg.com/Product/ProductList.aspx?Description=usb%20to%20ethernet%20adapter&Submit=ENE").

---

