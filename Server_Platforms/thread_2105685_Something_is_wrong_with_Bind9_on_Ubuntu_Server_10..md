---
title: "Something is wrong with Bind9 on Ubuntu Server 10.04 LTS"
date: 2013-01-16
forum: Server Platforms
---

### Post by salientdigital on 2013-01-16
I should preface this by saying I don't really know that much about bind, networking or Ubuntu server; I'm a PHP/MySQL dev who inherited this server administration task. It's a Dell quad xeon with 16GB of RAM and a RAID config on 5 drives.

Well I had the idea to install MongoDB and Redis on it.

During the install of one of those, I got this problem:

```
/etc/resolv.conf must be a symlink
```

So I googled that and found that indeed, an ex-co-worker had set up Bind9 wrong. From what I gathered on this and [other forums]("http://askubuntu.com/questions/54888/resolvconf-u-gives-the-error-resolvconf-error-etc-resolv-conf-must-be-a-sym"), that static file should be a symlink to ../run/resolvconf/resolv.conf

Okay so I inspect the incorrectly set up /etc/resolve.conf file and there's just this:

```
domain companydev.com
search companydev.com
nameserver 192.168.2.205
#nameserver 8.8.8.8
nameserver 208.67.222.222
nameserver 208.67.222.220
```

So I read on [another forum post]("http://fixunix.com/mandriva/350979-how-get-three-nameserver-entries-etc-resolv-conf.html"), that the correct place for static DNS entries is /etc/resolvconf/resolv.conf.d/tail  -- which I have now done, and recreated the symlink...

I restart bind like so
```
/etc/init.d/bind9 restart
```

And it gives no errors, and I continue installing MongoDB & Redis. 

Now a day or two later, and I'm not sure what I've done but every request to the machine is taking an extra 2-5 seconds and I have to believe it's DNS related, as I haven't started MongoDB or Redis and nothing else has changed.

Specific example: I run phpMyAdmin on my local box (a Mac Mini), pointed to the dev server's MySQL databases. A super simple query takes 4 seconds for the page to load, but MySQL reports that the query took 0.0016sec. Last week this would've returned in 25ms. Both my box and the dev server are on gigabit lan. The same query, local database, takes 150ms on my Mac Mini.

 Any assistance on how to troubleshoot this would be appreciated immensely!

---

### Post by Doug S on 2013-01-17
I don't understand why you think it is a bind9 issue. Is 192.168.2.205 the same computer as your resolv.conf file?
 
Anyway, maybe continue with separting the variables. You already know that the database lookup takes 0.0016 seconds, so how about DNS lookups and network traffic? Maybe use dig to note DNS lookup times. Example:```
doug@s15:~$ dig s10.smythies.com
; <<>> DiG 9.8.1-P1 <<>> s10.smythies.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 12867
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 1
;; QUESTION SECTION:
;s10.smythies.com.              IN      A
;; ANSWER SECTION:
s10.smythies.com.       604800  IN      A       192.168.111.102
;; AUTHORITY SECTION:
smythies.com.           604800  IN      NS      ns1.smythies.com.
;; ADDITIONAL SECTION:
ns1.smythies.com.       604800  IN      A       192.168.111.1
;; [COLOR=red]Query time: 0 msec[/COLOR]
;; SERVER: 192.168.111.1#53(192.168.111.1)
;; WHEN: Wed Jan 16 21:26:40 2013
;; MSG SIZE  rcvd: 84

```And ping for transit times:```
doug@s15:~$ ping 192.168.111.1
PING 192.168.111.1 (192.168.111.1) 56(84) bytes of data.
64 bytes from 192.168.111.1: icmp_req=1 ttl=64 [COLOR=red]time=0.178 ms[/COLOR]
64 bytes from 192.168.111.1: icmp_req=2 ttl=64 time=0.143 ms
64 bytes from 192.168.111.1: icmp_req=3 ttl=64 time=0.136 ms
```Otherwise we might want to start looking at the bind files in /etc/bind

---

### Post by jdthood on 2013-01-17
> **salientdigital said:**
> From what I gathered on this and [other forums]("http://askubuntu.com/questions/54888/resolvconf-u-gives-the-error-resolvconf-error-etc-resolv-conf-must-be-a-sym"), that static file should be a symlink to ../run/resolvconf/resolv.conf

That's right.

> So I read on [another forum post]("http://fixunix.com/mandriva/350979-how-get-three-nameserver-entries-etc-resolv-conf.html"), that the correct place for static DNS entries is /etc/resolvconf/resolv.conf.d/tail  -- which I have now done, and recreated the symlink.

That's not right. Only in very exceptional circumstances should any nameserver addresses be added to any files in /etc/resolvconf/resolv.conf.d/.

If an interface is configured by DHCP then normally the admin doesn't have to do anything extra; the nameserver address is furnished by the DHCP server and registered with resolvconf which puts the address in resolv.conf.

If an interface is statically configured using ifup then the admin has to put the nameserver address on a "dns-nameservers" line in the appropriate stanza in /etc/network/interfaces.

If an interface is statically configured using NetworkManager then the admin has to enter the nameserver address into the "Additional DNS servers" field for that interface in the Connection Editor.

> Okay so I inspect the incorrectly set up /etc/resolv.conf file and there's just this:

```
domain companydev.com
search companydev.com
nameserver 192.168.2.205
#nameserver 8.8.8.8
nameserver 208.67.222.222
nameserver 208.67.222.220
```

[...]

Now a day or two later, and I'm not sure what I've done but every request to the machine is taking an extra 2-5 seconds and I have to believe it's DNS related, as I haven't started MongoDB or Redis and nothing else has changed.


Probably the first nameserver is not responding.

The first question that needs to be answered is whether or not you really need the BIND nameserver (i.e., named) running locally. If so, second, does the local BIND nameserver provide general domain name service that should also be used on the local machine?  If so then named should be configured to listen on interface "lo" at address 127.0.0.1 and /etc/default/bind9 should contain ```
RESOLVCONF=yes
```
If not then named should be configured not to listen on interface lo at address 127.0.0.1 and /etc/default/bind9 should contain ```
RESOLVCONF=no
```

After this run ```
sudo dpkg-reconfigure resolvconf
```
Make sure /etc/resolv.conf is a symbolic link to ../run/resolvconf/resolv.conf.
Next eliminate all "nameserver" lines from files in /etc/resolvconf/resolv.conf.d/.
Then reboot.

After rebooting, ```
cat /etc/resolv.conf
``` should contain ```
nameserver 127.0.0.1
``` if you have configured the system to use the localling running named. Otherwise it should contain ```
nameserver 127.0.1.1
``` if you have the NetworkManager-controlled instance of dnsmasq enabled. Otherwise it should contain the address of some upstream nameserver. If it doesn't then you need to figure out why it doesn't and fix that. See above for instructions on where to enter nameserver addresses if you need to do that.

---

### Post by salientdigital on 2013-01-17
Thanks a lot guys for the detailed replies and assistance...

> **Doug S said:**
> I don't understand why you think it is a bind9 issue.

It may not be; mainly because I had got the impression that Bind9 was never really properly configured, and after I changed /etc/resolv.conf to a proper symlink as I described above, it seemed to be taking noticably longer to respond to internal requests from my local Mac to that server when they were instantaneous before. 

> **Doug S said:**
> Is 192.168.2.205 the same computer as your resolv.conf file?

Yes, 192.168.2.205 is the IP of the server. 

Ping and dig seem fast if I'm ssh'd into the box. 

> **jdthood said:**
> The first question that needs to be answered is whether or not you really need the BIND nameserver (i.e., named) running locally.

I'm not convinced that we do actually. The guy that set it up (who no longer works here) claimed we were insane for not running internal DNS, bought a Bind9 book and thought he set it up right (he meant well), but it may not be necessary. Our Cisco SA is handling DHCP but our computers are all un-named and we have no internal DNS otherwise. We have 10 people in our office, some of us web devs hack names into /etc/hosts manually.

> **jdthood said:**
> If so, second, does the local BIND nameserver provide general domain name service that should also be used on the local machine?

No. Well, our plan was to use it, but our plan was never fully implemented. If it's close to working, I'd like to learn to use it. This thread has helped.

> **jdthood said:**
> If so then named should be configured to listen on interface "lo" at address 127.0.0.1 

This is what I have /etc/network/interfaces 

```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.2.205
        netmask 255.255.255.0
        network 192.168.2.0
        broadcast 192.168.2.255
        gateway 192.168.2.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 192.168.2.1

auto eth0:1
iface eth1 inet static
        address 192.168.2.206
        netmask 255.255.255.0
        network 192.168.2.0
        broadcast 192.168.2.255
        gateway 192.168.2.1
```

> **jdthood said:**
> and /etc/default/bind9 should contain
Code:
RESOLVCONF=yes

It does. Here's that complete file:

```

# run resolvconf?
RESOLVCONF=yes

# startup options for the server
OPTIONS="-u bind"
```

> **jdthood said:**
> Make sure /etc/resolv.conf is a symbolic link to ../run/resolvconf/resolv.conf

Done. Next step...

> After this run
Code:
sudo dpkg-reconfigure resolvconf


When I try to reconfigure resolvconf I get:

```

sudo dpkg-reconfigure resolvconf
update-rc.d: warning: resolvconf stop runlevel arguments (none) do not match LSB Default-Stop values (0 6)
```

which appears to be [this bug](https://bugs.launchpad.net/ubuntu/+source/resolvconf/+bug/750423).

When I tried to ```
sudo add-apt-repository ppa:jdthood/resolvconf
``` I got 
```

Error: can't find signing_key_fingerprint at https://launchpad.net/api/1.0/~jdthood/+archive/resolvconf
```

I stopped there and have not rebooted, unsure how to get the patch for resolvconf.

---

### Post by jdthood on 2013-01-17
Hi

> 
This is what I have /etc/network/interfaces 

```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.2.205
        netmask 255.255.255.0
        network 192.168.2.0
        broadcast 192.168.2.255
        gateway 192.168.2.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 192.168.2.1

auto eth0:1
iface eth1 inet static
        address 192.168.2.206
        netmask 255.255.255.0
        network 192.168.2.0
        broadcast 192.168.2.255
        gateway 192.168.2.1
```


Make sure that the dns-nameservers line is correct, i.e., that there really is a nameserver available at 192.168.2.1.

> 
It does. Here's that complete file:

```

# run resolvconf?
RESOLVCONF=yes

# startup options for the server
OPTIONS="-u bind"

```


OK, so the locally running named registers its address, 127.0.0.1, with resolvconf which will put "nameserver 127.0.0.1" in resolv.conf.

> 
When I try to reconfigure resolvconf I get:

```

sudo dpkg-reconfigure resolvconf
update-rc.d: warning: resolvconf stop runlevel arguments (none) do not match LSB Default-Stop values (0 6)
```

which appears to be [this bug](https://bugs.launchpad.net/ubuntu/+source/resolvconf/+bug/750423).

When I tried to ```
sudo add-apt-repository ppa:jdthood/resolvconf
``` I got 
```

Error: can't find signing_key_fingerprint at https://launchpad.net/api/1.0/~jdthood/+archive/resolvconf
```

I stopped there and have not rebooted, unsure how to get the patch for resolvconf.

I just realized that you are not running 12.04 LTS but 10.04 LTS! In 12.04, resolvconf is part of the base install. Prior to 12.04, resolvconf was not standardly used in Ubuntu. The resolvconf package wasn't in the main archive; it was in Universe and it was broken because it had not been ported from sysvinit to upstart.

So my advice to you now is to purge the resolvconf package from your 10.04 system. 

Put a static file at /etc/resolv.conf with the following contents.
```

nameserver 127.0.0.1
search companydev.com

```

Make sure that /etc/resolv.conf is really a static file and not a symlink.

Make sure that BIND named is properly configured and is in fact listening at 127.0.0.1.

---

### Post by salientdigital on 2013-01-17
> **jdthood said:**
> Make sure that the dns-nameservers line is correct, i.e., that there really is a nameserver available at 192.168.2.1.

We actually do not have a name server running at 192.168.2.1 - that's our gateway (It's a Cisco SA 5500 I believe) - it's running DHCP but not DNS. Our plan was for the dev server (192.186.2.205 running 10.04 LTS) to be the primary and only DNS server on our LAN.

> **jdthood said:**
> OK, so the locally running named registers its address, 127.0.0.1, with resolvconf which will put "nameserver 127.0.0.1" in resolv.conf.

> **jdthood said:**
> I just realized that you are not running 12.04 LTS but 10.04 LTS! In 12.04, resolvconf is part of the base install. Prior to 12.04, resolvconf was not standardly used in Ubuntu. The resolvconf package wasn't in the main archive; it was in Universe and it was broken because it had not been ported from sysvinit to upstart.

So my advice to you now is to purge the resolvconf package from your 10.04 system. 

Put a static file at /etc/resolv.conf with the following contents.
```

nameserver 127.0.0.1
search companydev.com

```

Make sure that /etc/resolv.conf is really a static file and not a symlink.

Yeah, it's confusing due to being changed between 10 & 12. I did put 10.04LTS nice, big & bold in the subject line ;-) I suppose we ought to upgrade but I haven't gotten around to  it.

I ran ```
sudo apt-get purge resolvconf
``` and that succeeded. When I went to inspect /etc/resolv.conf it is a static file and now contains: ```
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
# nameserver 192.168.2.1
domain companydev.com
search companydev.com
nameserver 192.168.2.205
nameserver 8.8.8.8
nameserver 208.67.222.222
nameserver 208.67.222.220

nameserver 127.0.0.1
domain companydev.com
search companydev.com
nameserver 192.168.2.205
```

The fact that #nameserver 192.168.2.1 is commented out seems odd to me, although I'm kind of okay with it being that in fact no name server is running at that IP. I'm also confused why there's two copies of the info in this file (I didn't edit it this way, it was built by BIND/named, right? 

Should I just leave it or should I do what it says not to do (edit by hand) as you suggested? 

> **jdthood said:**
> Make sure that BIND named is properly configured and is in fact listening at 127.0.0.1.

I'm not sure if BIND is properly configured, however: ```
sudo netstat -tulpn | grep :53
tcp        0      0 192.168.2.205:53        0.0.0.0:*               LISTEN      28686/named     
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN      28686/named     
tcp6       0      0 :::53                   :::*                    LISTEN      28686/named     
udp        0      0 192.168.2.205:53        0.0.0.0:*                           28686/named     
udp        0      0 127.0.0.1:53            0.0.0.0:*                           28686/named     
udp6       0      0 :::53                   :::*                                28686/named     

```

---

### Post by Doug S on 2013-01-17
Bind seem to be listening properly.
I don't think bind builds the resolv.conf file. I run 12.04, and mine is:```
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1
search smythies.com
```If indeed your issues are DNS related, I still don't understand why no delay was observed using dig. It was done from the MAC computer, right? And the MAC computer uses 192.168.2.205 as the first DNS right?
 
I am interested in this part of the thread:> If so then named should be configured to listen on interface "lo" at address 127.0.0.1 and /etc/default/bind9 should contain 
Code:
RESOLVCONF=yes
If not then named should be configured not to listen on interface lo at address 127.0.0.1 and /etc/default/bind9 should contain 
Code:
RESOLVCONF=no
from the perspective of trying to help with the accuracy of the Ubuntu server guide, which makes no mention of such an edit. Indeed, my file is:```
# run resolvconf?
RESOLVCONF=no
# startup options for the server
OPTIONS="-u bind"

```And local DNS lookup work fine.

---

### Post by jdthood on 2013-01-18
> **salientdigital said:**
> We actually do not have a name server running at 192.168.2.1


In that case at least comment out the dns-nameservers line so it doesn't mislead anyone. 

> I ran ```
sudo apt-get purge resolvconf
``` and that succeeded. When I went to inspect /etc/resolv.conf it is a static file and now contains: ```
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
# nameserver 192.168.2.1
domain companydev.com
search companydev.com
nameserver 192.168.2.205
nameserver 8.8.8.8
nameserver 208.67.222.222
nameserver 208.67.222.220

nameserver 127.0.0.1
domain companydev.com
search companydev.com
nameserver 192.168.2.205
```


Now edit the file way down to what is valid. 

```
 
search companydev.com
nameserver 127.0.0.1

```

The rest is cruft.

---

### Post by confusedstingray on 2013-01-19
what is the final results you want. Do you want to have a dns server running 
the resolv.conf is machine based, it is used to configure a machine to point to a proper domain name server.
I would purge the contents of resolv.conf of the bind machine
for what you want you need to configure bind9 and it will do what you want.
from what you have posted the ip of your bind machine is 192.168.2.205.
so that is the ip of your nameserver(bind machine) you have to make this ip static on this machine
once that is set the following link should point you in the right direction, 
[http://www.howtoforge.com/installing-an-ubuntu8.04-dns-server-with-bind-p4](http://www.howtoforge.com/installing-an-ubuntu8.04-dns-server-with-bind-p4)
 it is for 8.04 but the setup is the same  for 10.04 lts
if you need help let me know i have a similar set-up

---

### Post by salientdigital on 2013-01-21
> **confusedstingray said:**
> what is the final results you want. Do you want to have a dns server running 

I'd like to know if we have Bind configured correctly or not. I think it is now, but I'm not 100% sure.

If so, I'd like to use it and learn it better. What's the best way to test if it's working?

If not, I guess we can remove it. What's the best way to do that? apt-get purge bind9?

Thanks for the help -

---

### Post by jdthood on 2013-01-21
> **salientdigital said:**
> I'd like to know if we have Bind configured correctly or not. I think it is now, but I'm not 100% sure.

If so, I'd like to use it and learn it better. What's the best way to test if it's working?

Well, see if it resolves the names that it ought to resolve. ;)

Out of the box the Ubuntu bind9 nameserver provides recursive DNS service: it resolves any given Internet domain name by doing iterative DNS queries starting at the root servers. It also caches answers to queries.

It can also be configured to forward (some) queries to other nameservers.

You can also configure it to act as an authoritative nameserver for your own zones. Having done that you can use it to resolve private domain names in a local network or register it with a DNS registrar so that the names in your zones can also be resolved by outsiders.

Run BIND or one of its alternatives if you need any of these features. If you just want to look up Internet domain names then you may not have to run a nameserver at all; or you can run a simple caching forwarding nameserver such as dnsmasq, either on a single server or on every machine on the LAN or both.

> If not, I guess we can remove it. What's the best way to do that? apt-get purge bind9?

Yes, that's a good way.

---

### Post by salientdigital on 2013-01-21
> **jdthood said:**
> Well, see if it resolves the names that it ought to resolve. ;)

I realize I can Google *How to use Bind* but as you know, it's super deep, and also I can buy a 900 page book on it. Say I wanted to skip all that. I'm an intermediate sysadmin at best, but I kind of understand DNS from doing years of web development. 

I just figure if I point my Mac Mini to that server's IP for name servers (removing any others) I should be able to go to some random domain name while tailing some log on the BIND server and see if it is actually doing the lookup and the caching, right?

Got a quick 5-step overview for me, JT? That'd be super sweet. If not I understand you're not here to give free Bind lessons ;-)

Ultimately, it would be nice to actually name all our internal PCs & Macs (stop hand editing hosts files all over everyone's machines) and provide internal DNS via this box - but that's pretty far beyond my skillset at the moment. Some tips on what that is actually called, for better google results, would be cool.

Thanks again & Cheers -

---

### Post by jdthood on 2013-01-22
> **salientdigital said:**
> I just figure if I point my Mac Mini to that server's IP for name servers (removing any others) I should be able to go to some random domain name

That should work. Does it?

> while tailing some log on the BIND server and see if it is actually doing the lookup and the caching, right?

The BIND nameserver program is called named. 

You can control named's logging and other behavior using the rndc command. 

> Ultimately, it would be nice to actually name all our internal PCs & Macs (stop hand editing hosts files all over everyone's machines) and provide internal DNS via this box - but that's pretty far beyond my skillset at the moment. Some tips on what that is actually called, for better google results, would be cool.

I'd also like to know if there are any utilities out there that make BIND configuration easier.

---

