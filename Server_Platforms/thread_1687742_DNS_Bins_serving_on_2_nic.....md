---
title: "DNS Bins serving on 2 nic...."
date: 2011-02-14
forum: Server Platforms
---

### Post by yield_ on 2011-02-14
Hi There,

I have a brand new Bind server with many zones and revere lookup that goes with it....
It all work fine...

However, on the host mahine for that BIND9, I have 2 NIC in 2 different subnet:
- One for ''servers''
- One for workstations....

If only one NIC is enable, the DNS resolution in that Subnet works great. 
However, if the 2 NIC are enabled, it does not work correctly, time out or does not work at all..... Is there any thing I need to tell my BIND9 to answer DNS request from one subnet to a specefic NIC and other Request from the other subnet to be answered to the other NIC ??

---

### Post by SeijiSensei on 2011-02-15
In the options{} section of named.conf, add a "listen-on" directive with the IP addresses of both interfaces like this:

```

options {
         [...]
         listen-on { 127.0.0.1; 192.168.1.1; 192.168.2.1; };
         [...]
}

```

This tells named to listen on the localhost interface and two other IPs at 192.168.1.1 and 192.168.2.1.

---

### Post by yield_ on 2011-02-16
Yeah... I did that.

Also try with { any; } ..... and didn't fixed the issue....

---

### Post by yield_ on 2011-02-16
Never mind... I am just blind today...... ;-)

Thanks again ! :-)

---

### Post by confusedstingray on 2011-02-20
could i ask what solved the issue, going to be setting up a bind server to serve dns to 3 subnets

---

