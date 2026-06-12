---
title: "allow only 1 (not specific) IP at a time on a port"
date: 2020-01-17
forum: Security
---

### Post by mikamikamika on 2020-01-17
Hello,

I'm looking to a UFW or IPTables rule in order to allow only One not specific IP at a time to a port.

There is plenty of exemples online about allowing 1 specfic IP which is not what I want.

I wish to Allow ANY IP to connect to a port, but only 1 IP at a time (which means that if two person on different location are trying to connect to that port, the later won't be allow, or better, both would be disconnected).

Anyone has an idea ?

Thanks a lot.

---

### Post by SeijiSensei on 2020-01-17
In the good old days, I would wrap the service with [xinetd]("https://www.linux.co.cr/distributions/review/2003/red-hat-9/rhl-rg/s1-tcpwrappers-xinetd-config.html") to limit it to one simultaneous connection. Apparently systemd now offers this ability, but someone else will have to explain that method.

After installation of xinetd, you'll have an /etc/xinetd.d/ directory. Create a configuration file for the service like the ones you'll see there. If it's a standard service that appears in the list in /etc/services, use that name, e.g., smtp, otherwise define a custom service in /etc/services by adding a line like 
```
myservice     62610/tcp
```
whish specifies that myservice listens on port 62610. Next, create the configuration file in /etc/xinetd.d/ like this:
```

service myservice
{
        disable         = no
        type            = INTERNAL
        socket_type     = stream
        server          = /path/to/some/executable
        protocol        = tcp
        user            = root
        wait            = no
        instances       = 1
}

```

After xinetd is started, it will listen on the port assigned to the server (62610 in this case) and pass incoming requests to the program at /path/to/some/executable. That last line will limit concurrent connections to one.

---

### Post by kevdog on 2020-01-19
Neat -- I had no idea you could do this.  Thanks for information.

---

### Post by SeijiSensei on 2020-01-20
Xinetd has a number of useful features. I use the redirect option to pass connections to an IMAP server running on a machine behind a public-facing server. The [man page for xinetd.conf]("https://linux.die.net/man/5/xinetd.conf") is quite extensive.

---

### Post by mikamikamika on 2020-01-21
Hello !

This solution will fit the job perfectly, i will dig into xinetd.

Thanks you very much !

---

### Post by Doug S on 2020-01-23
I think this iptables rule will also do what you want:

```
sudo iptables -A INPUT -p tcp --dport 22 -s 0.0.0.0/0 -m connlimit --connlimit-above 1 -j DROP
```

The rule will have to be placed properly within your existing rule set.
Yes, normally the connlimit-above is ip specific, but the rule specifies any IP address as an override.
**EDIT: Incorrect: see post [#8]("https://ubuntuforums.org/showthread.php?t=2435199&p=13927247#post13927247") below.**

Example use (port 22 SSH): I had one ssh session already going to the test server, added the iptables rule and all was fine. I attempted to open another ssh session, could not and also got dropped from my original session. Once the conntrack table entries were eventually closed, I was then able to re-connect to via ssh to the computer and repeat the process. I also did the test from two different computers on my LAN.

---

### Post by SeijiSensei on 2020-01-23
If you use REJECT instead of DROP, 
```
sudo iptables -A INPUT -p tcp --dport 22 -s 0.0.0.0/0 -m connlimit --connlimit-above 1 -j REJECT
```
the second connection will see
```
ssh: connect to host hostname port 22: Connection refused
```
Using DROP causes the second connection to hang with no error reply.

Unlike your experience, my first connection remained established after a second attempt was made. That was true with DROP and REJECT.

This works well and is much simpler than using xinetd. Thanks, Doug!

---

### Post by Doug S on 2020-01-24
@SeijiSensei : thanks for trying it and your additional information.

I played around some more and had difficulties getting repeatable good test results. I think my suggested iptables rule should have been this instead (at least my tests work better):

```
sudo iptables -A INPUT -p tcp --syn --dport 22 -i enp3s0 -m connlimit --connlimit-above 1 [COLOR="#FF0000"]--connlimit-mask 0[/COLOR] -j REJECT
```Because then the mask looks correct when I do this:

```
doug@s18:~$ [COLOR="#FF0000"]sudo iptables -v -x -n -L[/COLOR]
[sudo] password for doug:
Chain INPUT (policy ACCEPT 300 packets, 28907 bytes)
    pkts      bytes target     prot opt in     out     source               destination
       2      120 REJECT     tcp  --  enp3s0 *       0.0.0.0/0            0.0.0.0/0            tcp dpt:22 flags:0x17/0x02 #conn [COLOR="#FF0000"]src/0[/COLOR] > 1 reject-with icmp-port-unreachable
...

```Whereas, with my previous rule, the mask seemed wrong:
```

doug@s18:~$ sudo iptables -D INPUT -p tcp --syn --dport 22 -i enp3s0 -m connlimit --connlimit-above 1 --connlimit-mask 0 -j REJECT
doug@s18:~$ sudo iptables -A INPUT -p tcp --dport 22 -i enp3s0 -s 0.0.0.0/0 -m connlimit --connlimit-above 1 -j REJECT
doug@s18:~$ [COLOR="#FF0000"]sudo iptables -v -x -n -L[/COLOR]
Chain INPUT (policy ACCEPT 9 packets, 628 bytes)
    pkts      bytes target     prot opt in     out     source               destination
       0        0 REJECT     tcp  --  enp3s0 *       0.0.0.0/0            0.0.0.0/0            tcp dpt:22 #conn [COLOR="#FF0000"]src/32[/COLOR] > 1 reject-with icmp-port-unreachable
...

```Edit: Where "enp3s0" is the network interface name for my computer. Change as required.

---

### Post by kevdog on 2020-01-28
> **SeijiSensei said:**
> Xinetd has a number of useful features. I use the redirect option to pass connections to an IMAP server running on a machine behind a public-facing server. The [man page for xinetd.conf]("https://linux.die.net/man/5/xinetd.conf") is quite extensive.

I don't understand this method.  Don't you still have to open a port on the firewall to accomplish this?

---

### Post by SeijiSensei on 2020-01-28
Yes, just as you would need to do for any service that listens for incoming client requests. So, in the case I described above, I'd open port 62610/tcp on the firewall.

It's no different than opening port 25 to allow incoming mail or port 80 to allow HTTP requests.

---

