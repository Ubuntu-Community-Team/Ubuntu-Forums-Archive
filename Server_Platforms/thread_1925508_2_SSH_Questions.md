---
title: "2 SSH Questions"
date: 2012-02-14
forum: Server Platforms
---

### Post by d4m1r on 2012-02-14
Hey guys, I have a Ubuntu 11.04 VPS and I am wondering 2 things:


1) How do I disable telnet connections to it? (so you have to connect to it over SSH)

2) How do I change the default SSH port and does the new one have to be within a specific range?


On the port issue, will I have to change it anywhere else or for any other program (ex: apache2) or will changing the default SSH port not affect anything else apart from the port needed to connect directly to the VPS? 

Thanks in advance guys :D

---

### Post by koenn on 2012-02-14
1) don't have telnetd

2) in the sshd conf file, somewhere in /etc. You can pick any port, AFAIK - except those already in use by other daemons 

```

     Port    Specifies the port number that sshd(8) listens on.  The default
             is 22.  Multiple options of this type are permitted.  See also
             ListenAddress.


     ListenAddress
             Specifies the local addresses sshd(8) should listen on.  The fol-
             lowing forms may be used:

                   ListenAddress host|IPv4_addr|IPv6_addr
                   ListenAddress host|IPv4_addr:port
                   ListenAddress [host|IPv6_addr]:port

             If port is not specified, sshd will listen on the address and all
             prior Port options specified.  The default is to listen on all
             local addresses.  Multiple ListenAddress options are permitted.
             Additionally, any Port options must precede this option for non-
             port qualified addresses.


```

---

### Post by ruffEdgz on 2012-02-14
To go off @koenn on the 'port selection' part, I wouldn't use a port that is already reserved for another service (even if you aren't going to use it).

I would consult the good old /etc/services file to see what ports are already reserved and don't use those for a new SSH port if you want to move away from port 22.
```

less /etc/services

```

But I agree with what @koenn said 100% ;)

---

### Post by d4m1r on 2012-02-14
Should I just remove the "telnetd" package then = telnet disabled?

As for SSH port, does it have to be under a certain number? I read something about "privileged ports" so does it have to within a certain range or can I pick a number like 3xxx?

---

### Post by bjmerino on 2012-02-14
From - Step by step guide to setting up Ubuntu 11.10 server for Newbies!
[http://ubuntuforums.org/showthread.php?t=1895084](http://ubuntuforums.org/showthread.php?t=1895084)

"...from this you can deduce that only port 22 is currently open and in use (look for the number after the first colon). That means *most* any of the other ports in the range 1-65000 (roughly) are available. That said, ports below 1024 are reserved and should not be used. I have also read that ports over 40,000 should be left alone (I have no idea why). So I generally stay in the 15,000 - 30,000 range. That's still a lot of ports!"

Hope this helps!

---

