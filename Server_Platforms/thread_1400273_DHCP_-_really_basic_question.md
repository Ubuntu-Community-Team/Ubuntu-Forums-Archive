---
title: "DHCP - really basic question"
date: 2010-02-06
forum: Server Platforms
---

### Post by BarryDocks on 2010-02-06
I have successfully configured several dhcp servers, but I fail to see the need for a "shared network".:oops:

Please could someone kindly explain to me what a shared network is in linux dhcp server terms and its advantage?

Thankyou

---

### Post by capscrew on 2010-02-06
> **BarryDocks said:**
> I have successfully configured several dhcp servers, but I fail to see the need for a "shared network".:oops:

Please could someone kindly explain to me what a shared network is in linux dhcp server terms and its advantage?

Thankyou

In simple terms your DHCP server is capable of serving IP addresses for separate IP subnets that live on the same physical infrastructure.

If you had an IP network of 192.168.0.0/16 you would be able to subnet this to 255 separate 192.168.0.0/24 networks (e.g 192.168.1.0/24 and 192.168.2.0 etc.).  These *separate subnets *can be declared in the dhcp.conf file.  The DHCP server would now be able service those subnets.

In typical home or SOHO use these is not the case, but you need to declare at least the one subnet that you are using.

The advantage is flexibility.  If you found your network had more than 254 hosts you could add a subnet of IP addresses for increased capacity.

In short it is a tool for the network engineer to design or compensate for Ethernet topology.  See this from the man page of dhcp.conf

```

       Some  installations  have  physical  networks on which more than one IP
       subnet operates.   For example, if there  is  a  site-wide  requirement
       that  8-bit subnet masks be used, but a department with a single physi-
       cal ethernet network expands to the point where it has  more  than  254
       nodes,  it may be necessary to run two 8-bit subnets on the same ether-
       net until such time as a new physical network can be added.    In  this
       case,  the  subnet declarations for these two networks must be enclosed
       in a shared-network declaration.

       Some sites may have departments which have clients  on  more  than  one
       subnet, but it may be desirable to offer those clients a uniform set of
       parameters which are different than what would be  offered  to  clients
       from  other departments on the same subnet.   For clients which will be
       declared explicitly with host declarations, these declarations  can  be
       enclosed  in  a  group  declaration along with the parameters which are
       common to that department.   For clients whose addresses will be dynam-
       ically assigned, class declarations and conditional declarations may be
       used to group parameter assignments based  on  information  the  client
       sends.

```

---

