---
title: "DHCP default setting"
date: 2011-12-15
forum: Server Platforms
---

### Post by philkscar on 2011-12-15
Hi Guys,

I run our school moodle on an Ubuntu 10.10 server on a windows network. I was wondering if Ubuntu enables its own dhcp server after a default installation. Our dhcp server is the windows server and I don't want any conflict from the ubuntu server. If I run ps -ax | grep dhcp it shows that dchpd is running. does this mean that the ubuntu server will be giving out ip's? I have checked /etc/dhcp3 but there is no config file. In fact, there doesn't seem to an config file anywhere.
I have searched on the net to try and find out how to turn off the dhcp server but there does not seem to be a lot of info out there.
Is there a way to disable the dhcp server if it is running?

Thanks in advance for any advice.

PhilK

---

### Post by jonobr on 2011-12-15
Hi there


It sounds from your description that you don't have DHCP server installed.

Even if it was you have to define a scope in your config file for the address range to be allocated.

The grep response your seeing is most likely from the grep itself.

Below is a response from me ps'ing junk and all thats returned is the grep

```

lumpy@jabba:~$ ps ax | grep junkyjunkjunk

 1879 pts/0    S+     0:00 grep --color=auto junkyjunkjunk
lumpy@jabba:~$

```

If I were to grep something there and you can see it in the return along with the grep

here is my dhcp 

```

lumpy@jabba:~$ ps -ax | grep dhcp

 1387 ?        Ss     0:00 dhclient3 -e IF_METRIC=100 -pf /var/run/dhclient.eth0.pid -lf /var/lib/dhcp3/dhclient.eth0.leases eth0
 1486 ?        Ss     0:00 /usr/sbin/ntpd -p /var/run/ntpd.pid -g -c /var/lib/ntp/ntp.conf.dhcp -u 108:117
 1937 pts/0    S+     0:00 grep --color=auto dhcp
lumpy@jabba:~$

```

a few other things,

if you go to /etc/init.d
you can look at whats in there, most likely jsut dhclient, but see if there is anything else in there along the dhcp scrips/

You could also try the which command

You can start it by typing 
```
which dhcp
```
hit tab to see if it auto fills, 

here is the result of mine

```

lumpy@jabba:~$ which dhcpd3
/usr/sbin/dhcpd3
lumpy@jabba:~$

```

---

### Post by philkscar on 2011-12-16
Thanks for your quick reply Jon.
I'll have a look today

Phil

---

### Post by HugoSerrano on 2011-12-16
hello!

You can stop the service with:
> sudo /etc/init.d/dhcp3-server stop

But like Jonor said, it's look like u don't have any dhcp server running.

And by default, theres no dhcp server installations, unless you choose it. 

Regards!

---

