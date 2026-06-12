---
title: "Dns providers that dont keep logs?"
date: 2011-03-01
forum: Security
---

### Post by asdfghjkl67 on 2011-03-01
Are there any dns providers that dont keep logs? 

Kind of like the way ixquick search engine dosents?

---

### Post by MechaMechanism on 2011-03-02
> **asdfghjkl67 said:**
> Are there any dns providers that dont keep logs? 

Kind of like the way ixquick search engine dosents?
Not that I know of.

If you want a DNS server that don't log, then run your own DNS server.

Do the following

```
sudo apt-get bind9
```Make the file as below.

```
sudo nano /etc/bind/named.conf.options
```> options {
        directory "/var/cache/bind";

        // If there is a firewall between you and nameservers you want
        // to talk to, you may need to fix the firewall to allow multiple
        // ports to talk.  See [http://www.kb.cert.org/vuls/id/800113](http://www.kb.cert.org/vuls/id/800113)

        // If your ISP provided one or more IP addresses for stable
        // nameservers, you probably want to use them as forwarders.
        // Uncomment the following block, and insert the addresses replacing
        // the all-0's placeholder.

        // forwarders {
        //      0.0.0.0;
        // };

        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { ::1; };
        listen-on { 127.0.0.1; };
};Make as below.

```
sudo nano /etc/bind/named.conf.local
```> //
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";
logging {
category lame-servers { null; };
};
Right click network icon and select edit connections.  Under wired tab select eth0 select edit.  Select ip4 setting.  By method select DHCP only.  In the DNS box enter 127.0.0.1

Congratulations you now have your own DNS server and you control the logs.

---

