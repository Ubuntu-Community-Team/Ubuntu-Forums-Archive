---
title: "Troubleshooting bind9 problem"
date: 2013-02-05
forum: Server Platforms
---

### Post by JKyleOKC on 2013-02-05
For several years I ran my own DNS in place of using the servers provided by my ISP, and had no problems with it. Then the machine hosting it crashed, and I didn't bother to install bind9 on the replacement machine for a while; I just used the AT&T-provided servers. Eventually I had to replace my router/DSL modem, when AT&T changed my true static IP block to a "sticky static" block requiring PPPoE login, and that seems to have made it impossible to use a locally-maintained DNS.

However I've now been trying for several days to get bind9 going for my private LAN, with no success. I've copied existing forward and reverse files, editing them to refer to my LAN machines, running the named-checkzones and named-checkconf programs with no reported errors, and restarting the bind9 service. Both dig and nslookup, however, when invoked to check another machine on my LAN, return no answer. Instead, they report under the AUTHORITY heading a single root server.

In /var/log/daemon.log I find this:

```
Feb  5 10:08:38 mehitabel named[1612]: zone 0.in-addr.arpa/IN: loaded serial 1
Feb  5 10:08:38 mehitabel named[1612]: zone 127.in-addr.arpa/IN: loaded serial 1
Feb  5 10:08:38 mehitabel named[1612]: zone 0.192.168.in-addr.arpa/IN: loaded serial 2
Feb  5 10:08:38 mehitabel named[1612]: zone 255.in-addr.arpa/IN: loaded serial 1
[COLOR="Red"]Feb  5 10:08:38 mehitabel named[1612]: /etc/bind/db.jk.local:14: ignoring out-of-zone data (mehitabel)
Feb  5 10:08:38 mehitabel named[1612]: /etc/bind/db.jk.local:15: ignoring out-of-zone data (xubuntu2)[/COLOR]
Feb  5 10:08:38 mehitabel named[1612]: zone jk.local/IN: loaded serial 4
Feb  5 10:08:38 mehitabel named[1612]: zone localhost/IN: loaded serial 2
Feb  5 10:08:38 mehitabel named[1612]: zone jk.local/IN: sending notifies (serial 4)
Feb  5 10:08:38 mehitabel named[1612]: zone 0.192.168.in-addr.arpa/IN: sending notifies (serial 2)
Feb  5 10:08:38 mehitabel named[1612]: running

```However, here's the **/etc/bind/db.jk.local** file:```
;
; BIND data file for jk.local interface
;
$TTL	1d
@	IN	SOA	jk.local. root.localhost. (
			      4		; Serial
			 604800		; Refresh
			  86400		; Retry
			2419200		; Expire
			 604800 )	; Negative Cache TTL
;
@	IN	NS	localhost.
@	IN	A	192.168.0.2
mehitabel.	IN	A	192.168.0.2
xubuntu2.	IN	A	192.168.0.5
;@	IN	AAAA	::1

```I fail to see anything wrong in lines 14 and 15. So what am I doing wrong? I've searched the forums but find nothing...

Perhaps I ought to purge the existing copy of bind9 and reinstall, since I've tried so many different ways to test this. The machine running bind9, incidentally, is running Xubuntu 10.04 LTS with all updates applied.

---

### Post by Doug S on 2013-02-05
Hi Jim,
 
When I ran your file, db.jk.local under named-checkzone, it gives the same errors that you listed.```
doug@doug-64:~/config/bind/temp8$ nano db.jk.local_o
doug@doug-64:~/config/bind/temp8$ named-checkzone jk.local db.jk.local_o
db.jk.local_o:14: ignoring out-of-zone data (mehitabel)
db.jk.local_o:15: ignoring out-of-zone data (xubuntu2)
zone jk.local/IN: loaded serial 4
OK

```If I take out the "." (period) at the end of the names, then I get:```
doug@doug-64:~/config/bind/temp8$ nano db.jk.local_o
doug@doug-64:~/config/bind/temp8$ named-checkzone jk.local db.jk.local_o
zone jk.local/IN: loaded serial 4
OK

```However, and with the disclaimer that I am, by far, not some bind authority, I suggest this (formatting always gets ruined when I copy and paste):```
;
; BIND data file for jk.local interface
;
$TTL    1d
@       IN      SOA     jk.local. root.jk.local. (
                              5         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
        IN      A       192.168.0.2
;
@       IN      NS      ns.jk.local.
ns              IN      A       192.168.0.2
mehitabel       IN      A       192.168.0.2
xubuntu2        IN      A       192.168.0.5

```Edit: which doesn't mean you can not set localhost as the name server for 192.168.0.2, if that was the intent. However, that is done somewhere else. Example (from my system):```
doug@doug-64:~/config/bind/temp8$ nslookup smythies.com
Server:         [COLOR=red]127.0.0.1[/COLOR]
Address:        127.0.0.1#53
Name:   smythies.com
Address: 192.168.111.1
doug@doug-64:~/config/bind/temp8$ nslookup s15.smythies.com
Server:         [COLOR=red]127.0.0.1[/COLOR]
Address:        127.0.0.1#53
Name:   s15.smythies.com
Address: 192.168.111.112

```

---

### Post by JKyleOKC on 2013-02-05
Thanks for the quick response. I got rid of the periods, changed all the "@" characters to "jk.local" instead, and commented out the first assignment to 192.168.0.2. These edits allowed the zone to load error-free, and I can now look up the other machine using its FQDN. However I've not found a way to have the private domain "jk.local" automagically added, so a lookup by hostname only still fails.

I can manually add a "search jk.local" line to resolv.conf, but it gets overwritten immediately at the next DHCP lease renewal. I'm still trying various ideas, though. My target is to get rid of all the cruft in my /etc/hosts files, and let it all be resolved by a local DNS. Also, of course, to learn more about the quirks of bind9...

---

### Post by Doug S on 2013-02-05
Hi Jim,
 
So you want something like this:```
doug@doug-64:~/config/bind/temp8$ nslookup [COLOR=red]s15[/COLOR]
Server:         127.0.0.1
Address:        127.0.0.1#53
Name:   s15.smythies.com
Address: 192.168.111.112
```where the smythies.com part is added automatically. There was a thread on this just recently, and I will try to find it. Give me a few minutes, but I also have to go out in a few minutes. In the mean time, please note that "dig", by default, does not automatically append the extention stuff. Example:```
doug@s15:~/temp1$ [COLOR=red]dig s10[/COLOR]
; <<>> DiG 9.8.1-P1 <<>> s10
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 25777
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0
;; QUESTION SECTION:
;s10.                           IN      A
;; AUTHORITY SECTION:
.                       10800   IN      SOA     a.root-servers.net. nstld.verisign-grs.com. 2013020501 1800 900 604800 86400
;; Query time: 176 msec
;; SERVER: 192.168.111.1#53(192.168.111.1)
;; WHEN: Tue Feb  5 10:59:54 2013
;; MSG SIZE  rcvd: 96
doug@s15:~/temp1$ [COLOR=red]nslookup s10[/COLOR]
Server:         192.168.111.1
Address:        192.168.111.1#53
Name:   s10.smythies.com
Address: 192.168.111.102

```

---

### Post by Doug S on 2013-02-05
Jim,
 
Have a look [here]("http://ubuntuforums.org/showpost.php?p=12289468&postcount=6"), and there are other links within that. Out of time, for now. and [here]("http://ubuntuforums.org/showpost.php?p=12414706&postcount=7").

---

### Post by JKyleOKC on 2013-02-05
Many thanks! I think I was being misled by using dig rather than nslookup; nslookup now works properly after I added "jk.local" to the search textbox in Network Manager and restarted the whole system.

---

### Post by Doug S on 2013-02-05
Just for completeness, to get dig to attach the extention to the DNS request use the +search option. Example:```
doug@s15:~/temp1$ [COLOR=red]dig +search s10[/COLOR]
; <<>> DiG 9.8.1-P1 <<>> +search s10
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 37528
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 1
;; QUESTION SECTION:
;s10.smythies.com.              IN      A
;; ANSWER SECTION:
[COLOR=red]s10.smythies.com.       604800  IN      A       192.168.111.102[/COLOR]
;; AUTHORITY SECTION:
smythies.com.           604800  IN      NS      ns1.smythies.com.
;; ADDITIONAL SECTION:
ns1.smythies.com.       604800  IN      A       192.168.111.1
;; Query time: 0 msec
;; SERVER: 192.168.111.1#53(192.168.111.1)
;; WHEN: Tue Feb  5 14:04:14 2013
;; MSG SIZE  rcvd: 84

```

---

### Post by SeijiSensei on 2013-02-05
To make the resolver append domain.name to an unqualified name requires a "search domain.name" entry in /etc/resolv.conf.  If you are using 12.04 or any later version of Ubuntu, you cannot simply edit resolv.conf and add the search line because the file is recreated anew each time the machine boots.  You can try adding the domain to the search list via NetworkManager, or add it manually to /etc/network/interfaces like this:

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
dns-nameservers 10.10.10.10 8.8.8.8
dns-search domain.name

```

The "dns-nameservers" line is optional; it lets you specify the nameservers statically and control the order in which they are tried.

---

### Post by Doug S on 2013-02-05
In the case of a static IP address, or a dhcp address where you don't control the server, I agree one can edit /etc/network/interfaces. However, it can also be done via the dhcp server if one is using dhcp. For example, on my s15 computer used in some examples above the /etc/interfaces file is:```
doug@s15:~/temp1$ [COLOR=red]cat /etc/network/interfaces[/COLOR]
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo
iface lo inet loopback
# The primary network interface
auto eth0
iface eth0 inet dhcp
# Local network interface
auto eth1
iface eth1 inet static
  address 192.168.222.1
  network 192.168.222.0
  netmask 255.255.255.0
  broadcast 192.168.222.255

```So how does it know to append "smythies.com" to the DNS request example a few postings up? It was done in the dhcp.conf file on the server, here:```
# option definitions common to all supported networks...
default-lease-time 86400;
max-lease-time 93000;
[COLOR=red]option domain-name "smythies.com";[/COLOR]
# option domain-name-servers 192.168.111.1, 75.154.133.68, 75.154.133.100;
[COLOR=red]option domain-name-servers 192.168.111.1;[/COLOR]
option subnet-mask 255.255.255.0;
option broadcast-address 192.168.111.255;
option routers 192.168.111.1;

```I also put in [COLOR=red]red[/COLOR] the dns servers lines, because I think we want our local dns to be first. (In my case I don't bother with the upstream servers because if my server is down, my whole LAN is down anyhow.)
The advantage is that I don't have to think about it or edit any client files, and the windows computers all work with abbreviated names also.

---

### Post by JKyleOKC on 2013-02-05
Will those dns-* lines in the stanza override the DHCP assignments in 10.04 as well as 12.04? One of my machines still runs Lucid while the other runs Precise; the man page for "interfaces" on the Lucid box (the one using DHCP from the router and serving as the internal router for my LAN) doesn't mention the "dns-*" options.

I'd like to have both boxes using the local DNS server since it's configured to go through the root servers if need be. I found this to be more responsive than using AT&T's DNS servers in my original setup. If the "interfaces" file will override the DHCP data then my problems should be completely solved.

Thanks much!

EDIT: The Lucid box uses the interfaces file, and its Network Manager is disabled by having a file in /etc/defaults containing the single word "exit" so that it quits without activating itself during boot. The Precise box, however, uses Network Manager and only has the loopback interface defined in /etc/network/interfaces.

---

### Post by SeijiSensei on 2013-02-05
I'd use a static resolv.conf on 10.04.  I prefer that anyway.  On 12.04, I sometimes end up creating a static resolv.conf and marking it immutable with chattr +i.  I think you can also simply remove the resolvconf package and get the same result, but I'm loathe to recommend that without some thorough testing.

However, if you have control of the router providing DHCP, the easiest solution is to configure the router to advertise your local DNS server as the first option in the list, followed by your secondary if you have one, and then some public server like Google's 8.8.8.8. I've been able to do that on pretty much all wifi routers I've tried.

---

### Post by JKyleOKC on 2013-02-05
> **SeijiSensei said:**
> However, if you have control of the router providing DHCP, the easiest solution is to configure the router to advertise your local DNS server as the first option in the list, followed by your secondary if you have one, and then some public server like Google's 8.8.8.8. I've been able to do that on pretty much all wifi routers I've tried.The router is a Motorola 3347, which is a step up from the usual SOHO units but nowhere near the level of the big Cisco gear. I do have full control of it, but am uncertain whether AT&T's "sticky static" connections are able to overwrite the DNS addresses that I enter, or whether these WAN-side addresses will even accept 192.168.0.0/24 IP values.

Guess I ought to just try it and see what happens. Meanwhile I've added the DNS-search line to my DHCP stanza in /etc/network/interfaces, but have not yet gone through the ifdown/sleep/ifup sequence to get things reloaded.

---

### Post by JKyleOKC on 2013-02-06
Well, I restarted the system this morning, but the "DNS-*" lines added to /etc/network/interfaces to force search with the local domain added, and use of the local nameserver, had no effect at all on /etc/resolv.conf. It still showed just a single line, the router's address.

I then edited the DNS settings on the router to show the local IP address as the primary, and to search the jk.local domain. I set an AT&T server address as secondary. After restarting the router to make the new settings active, I was still able to ping a test site on the web, but with a very long lookup delay before the first packet returned. However, nslookup still did not return any answer; I believe that the router was failing to access the primary DNS locally, and timing out before going to the secondary.

I then restored the original router settings, and performance returned to normal.

Looks like the next step is going to have to be making /etc/resolv.conf immutable and seeing what that does!

Thanks for all the ideas. At least we now know several things that **won't** work!

---

### Post by SeijiSensei on 2013-02-06
You could turn off the DHCP server on the router and install [isc-dhcp-server]("http://www.cyberciti.biz/faq/howto-ubuntu-debian-squeeze-dhcp-server-setup-tutorial/") on the box that has your DNS.  It has hooks into BIND so that it will create nameservice entries for the machines to which it gives addresses.  You can designate the nameservers in the dhcpd.conf file.

---

### Post by JKyleOKC on 2013-02-06
That would make it impossible for our NOOK devices to connect, and for my wife's machine at the other end of the house to get to the Internet. My setup is a bit strange; the 3347 includes a secured wireless AP served by its internal DHCP, while my LAN is wired and all-static but the Lucid box's second NIC connects to the router/modem via DHCP, as do all the wireless devices. The only wired connection to the router is the Lucid box, and the Lucid box neither has nor needs any wireless capability.

Making /etc/resolv.conf immutable seems to have solved all the problems. Nslookup now works as expected, and the Lucid box now uses the local DNS as primary with the router as secondary. If all is still working right in another 24 hours, I'll tag the thread as solved. Thanks again for all the ideas!

---

### Post by jdthood on 2013-02-06
> **SeijiSensei said:**
> I'd use a static resolv.conf on 10.04.

I agree.

> On 12.04, I sometimes end up creating a static resolv.conf and marking it immutable with chattr +i.  I think you can also simply remove the resolvconf package and get the same result, but I'm loathe to recommend that without some thorough testing.

Don't remove resolvconf. If /etc/resolv.conf isn't a symbolic link to ../run/resolvconf/resolv.conf then resolvconf has no effect on name resolving. 

The presence of the resolvconf package stops other packages from futzing with /etc/resolv.conf, which is beneficial.

> 
However, if you have control of the router providing DHCP, the easiest solution is to configure the router to advertise your local DNS server as the first option in the list, followed by your secondary if you have one

Yes.

> 
, and then some public server like Google's 8.8.8.8


No. The list of nameservers is supposed to be a list of equivalent nameservers. A public nameserver does not know about the local zones. 

If you include 8.8.8.8 in the list of nameservers then everyone on the LAN will have to disable dnsmasq which, unlike the glibc resolver, strongly assumes that all the nameservers are equivalent. If they aren't then dnsmasq will malfunction.

Ref: [https://bugs.launchpad.net/ubuntu/+source/dnsmasq/+bug/1003842](https://bugs.launchpad.net/ubuntu/+source/dnsmasq/+bug/1003842)

---

### Post by jdthood on 2013-02-06
> **JKyleOKC said:**
> I can manually add a "search jk.local" line to resolv.conf, but it gets overwritten immediately at the next DHCP lease renewal.

Don't add a "search" line directly to /etc/resolv.conf if you are using resolvconf. Instead (assuming that you are configuring network interfaces statically on the machine in question) add it to the configuration of whatever you use to configure the external network interface on that machine. If you use ifup then add a "dns-search" option to the relevant stanza in /etc/network/interfaces. If you use NetworkManager then add the domain name to the connection configuration using the Connection Editor. See resolvconf(8) for more information.

Better yet, if the machine's network interface is configured via DHCP, then configure the DHCP server to supply the search list.

---

### Post by jdthood on 2013-02-06
> **JKyleOKC said:**
> Well, I restarted the system this morning, but the "DNS-*" lines added to /etc/network/interfaces to force search with the local domain added, and use of the local nameserver, had no effect at all on /etc/resolv.conf.


That indicates that /etc/resolv.conf is no longer a symbolic link to ../run/resolvconf/resolv.conf, which it has to be if resolvconf is going to update its contents. (Resolvconf updates /run/resolvconf/resolv.conf, not /etc/resolv.conf directly.)

To restore the symlink you can run "sudo dpkg-reconfigure resolvconf".

---

### Post by jdthood on 2013-02-06
> **JKyleOKC said:**
> I then edited the DNS settings on the router to show the local IP address as the primary, and to search the jk.local domain.

The ".local" domain is reserved for multicast DNS (Zeronconf/Bonjour) which is implemented in Ubuntu by the avahi daemon. Although the avahi daemon will disable itself if it detects a unicast nameserver claiming authority over ".local", this doesn't always work well. Avoid problems and use some other private TLD such as ".private" or ".internal", if you can.

Ref: [http://avahi.org/wiki/AvahiAndUnicastDotLocal](http://avahi.org/wiki/AvahiAndUnicastDotLocal)

---

### Post by jdthood on 2013-02-06
> **JKyleOKC said:**
> Making /etc/resolv.conf immutable seems to have solved all the problems.

The immutability attribute makes no difference as far as resolvconf is concerned. You only need to make /etc/resolv.conf immutable if (1) it's a static file, and (2) some badly behaved third party program keeps trashing /etc/resolv.conf. The resolvconf program doesn't touch /etc/resolv.conf directly but relies for its effect upon /etc/resolv.conf being a symbolic link to the file that resolvconf does write to.

---

### Post by SeijiSensei on 2013-02-06
You seem to have a *lot* of strongly-held opinions, some of which are more controversial than you might think.  First, I don't want to have resolvconf manage my resolv.conf at all. In particular I do not want it funneling all my name service requests to dnsmasq as is now the Ubuntu standard. I have had this combination fail on a number of occasions and simply prefer a static file.  Unless you mark the file immutable, resolvconf will overwrite it, even if it is marked read-only.  (Trust me I've been down that road.)  

I don't run any so-called "badly-behaved third-party programs" that could affect the contents of resolv.conf. I've used static resolv.conf files on dozens of machines over two decades without problems.

As for the servers in resolv.conf itself, remember that they are consulted in order of appearance.  If you have a local primary and secondary followed by an external server, you can at least resolve public names in the event of a massive failure of both your local servers.  Also we're talking about a home network here, not an ISP or even a business.

I don't think you understood the original premise which is that resolvconf+dnsmasq is not always the correct solution.  On machines that I run, including my workstations, I routinely replace the symlink with a static file and mark it immutable so resolvconf won't be able to alter it.  That may not be what the Ubuntu developers want people to do, but they imposed this "solution" on us without much warning.  Right after 12.04 came out there was a surge of postings about how DNS resolution wasn't working right for some people.  Plus the [use-case]("https://blueprints.launchpad.net/ubuntu/+spec/foundations-p-dns-resolving") for resolvconf+dnsmasq is pretty small.  This is designed to handle situations where someone may have a number of different connections with different nameservers.  I have one network, with two local nameservers and two public servers I manage in the cloud.  Those are the only nameservers I want my machines to talk to.  I don't need dnsmasq trying to figure that out for me.

---

### Post by JKyleOKC on 2013-02-06
I appreciate your suggestions, but they don't apply to this box. It's running Lucid, 10.05 LTS, and does not have resolveconf installed at all. The other one, which does have resolveconf, isn't having any problem. The forum software here doesn't let me show that I am running two different versions of Xubuntu, so I show the most recent one. However I don't plan to replace Lucid until it reaches EOL this spring...

I do plan to change that local domain name to simply "mylan" although everything seems to be working properly at present. I'll be adding my bridged VMs to the local DNS and cleaning them out of all the hosts files at the same time.

---

### Post by JKyleOKC on 2013-02-06
> **jdthood said:**
> You only need to make /etc/resolv.conf immutable if (1) it's a static file, and (2) some badly behaved third party program keeps trashing /etc/resolv.conf.In this case, it is a static file, not a symlink, resolvconf does not exist on the machine, and the badly behaved program is the DHCP server of the Motorola 3347 which is forcing the router's address and in the process deleting the other two lines. The immutable attribute solves the problem completely.

---

### Post by jdthood on 2013-02-07
> **SeijiSensei said:**
> You seem to have a *lot* of strongly-held opinions, some of which are more controversial than you might think.

First, I don't want to have resolvconf manage my resolv.conf at all.

That's fine. Remove the symbolic link at /etc/resolv.conf and resolvconf will no longer have any effect on /etc/resolv.conf.

But if you want /etc/resolv.conf to be a static file, you are better off keeping the resolvconf package installed, since several other Ubuntu packages refrain from writing directly to /etc/resolv.conf so long as resolvconf is present. See below.

> In particular I do not want it funneling all my name service requests to dnsmasq as is now the Ubuntu standard. I have had this combination fail on a number of occasions and simply prefer a static file.

Resolvconf is not responsible for dnsmasq being used as a local forwarding nameserver. *NetworkManager* is responsible for this. In fact, if you remove resolvconf then NetworkManager will still start dnsmasq and will write "nameserver 127.0.1.1" directly to /etc/resolv.conf.

You are correct in saying that the use of a local forwarding nameserver sometimes gives rise to name service failure --- see bug report #1003842. It's a good idea to disable the NetworkManager-controlled local forwarding nameserver. To do this, comment out the line "dns=dnsmasq" in /etc/NetworkManager/NetworkManager.conf and then restart network-manager.

> Unless you mark the file immutable, resolvconf will overwrite it, even if it is marked read-only.  (Trust me I've been down that road.)

This is not true. The resolvconf program never touches /etc/resolv.conf. *Never.*

Now, on *initial* installation, the resolvconf *package* does make *one* attempt to create the symbolic link /etc/resolv.conf -> ../run/resolvconf/resolv.conf *if* you have given it permission to do so by answering (the default) "yes" to the "Linkify /etc/resolv.conf?" debconf question. But if you subsequently remove this symbolic link and replace it with a static file then the resolvconf package will not touch it, even when upgraded, unless you deliberately run "dpkg-reconfigure resolvconf".

You may have experienced something overwriting /etc/resolv.conf at run time but it wasn't resolvconf that was doing it.

> I don't run any so-called "badly-behaved third-party programs" that could affect the contents of resolv.conf. I've used static resolv.conf files on dozens of machines over two decades without problems.

Only badly behaved third-party programs overwrite /etc/resolv.conf when the resolvconf package is installed.

If the resolvconf package is deinstalled then there are programs in Ubuntu itself which will overwrite /etc/resolv.conf, including NetworkManager, as mentioned above.

So if you were experiencing something trashing your /etc/resolv.conf, the reason might have been that you chose to uninstall resolvconf.

If you want a static /etc/resolv.conf then there are two possible solutions. (1) Leave resolvconf installed, replace /etc/resolv.conf with a static file, and don't use badly behaved third-party programs; (2) Replace /etc/resolv.conf with a static file and make it immutable if your filesystem allows that.

> As for the servers in resolv.conf itself, remember that they are consulted in order of appearance.  If you have a local primary and secondary followed by an external server, you can at least resolve public names in the event of a massive failure of both your local servers.  Also we're talking about a home network here, not an ISP or even a business.

You can include external nameservers in the nameserver list, but if you do this then you should disable dnsmasq on all your clients, since dnsmasq assumes that all listed nameservers are equivalent.

> I don't think you understood the original premise which is that resolvconf+dnsmasq is not always the correct solution.  On machines that I run, including my workstations, I routinely replace the symlink with a static file and mark it immutable so resolvconf won't be able to alter it.

See above. Resolvconf does not touch /etc/resolv.conf.

But you are right in this sense: *NetworkManager* + dnsmasq is not always the correct solution.

> That may not be what the Ubuntu developers want people to do, but they imposed this "solution" on us without much warning.  Right after 12.04 came out there was a surge of postings about how DNS resolution wasn't working right for some people.

There were many postings by people who didn't understand what had happened. The Ubuntu developers should have communicated better.

> Plus the [use-case]("https://blueprints.launchpad.net/ubuntu/+spec/foundations-p-dns-resolving") for resolvconf+dnsmasq is pretty small.  This is designed to handle situations where someone may have a number of different connections with different nameservers.  I have one network, with two local nameservers and two public servers I manage in the cloud.  Those are the only nameservers I want my machines to talk to.  I don't need dnsmasq trying to figure that out for me.

The best resource resource is: [https://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/](https://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/)

---

### Post by jdthood on 2013-02-07
> **JKyleOKC said:**
> I appreciate your suggestions, but they don't apply to this box. It's running Lucid, 10.05 LTS

Ah, OK. My remarks about the immutability attribute applied only to Ubuntu 12.04.

For earlier Ubuntu releases it's not recommended to use resolvconf at all, unless you have a special need.

---

### Post by jdthood on 2013-02-07
For completeness I will now say how I think that things should be configured in a situation like the one described here. (I realize that this is not exactly the situation described by the OP, who is running Ubuntu 10.04 on one of the boxes, etc.)

Hardware: Modemrouter R has Ethernet and Wi-Fi interfaces; Ubuntu Server 12.04 machine S is connected to R by Ethernet; Ubuntu Client 12.04 machine C is connected to R by Wi-Fi.

R's wired interface has static address 192.168.0.1.

R runs a DHCP server which provides a random address in 192.168.0.[3-254] to C. The DHCP server is configured to tell clients that the nameserver address is 192.168.0.2 and that the search domain list is "mylan".

S's wired network interface is configured statically using ifup. Its /etc/network/interfaces contains
```

    iface eth0 inet static
        address 192.168.0.2
        gateway 192.168.0.1
        dns-search mylan

```
S runs BIND which is configured to answer recursive DNS queries on both lo and eth0. Its "forwarders" option is set to the address of the ISP nameserver and it has a local zone configured such that it  additionally resolves the name 's.mylan' to 192.168.0.2.

On both S and C resolvconf is installed and /etc/resolv.conf is a symbolic link to ../run/resolvconf/resolv.conf.

On S, /etc/default/bind9 contains "RESOLVCONF=yes" which causes BIND to register its local listen address 127.0.0.1 with resolvconf. Consequently, on S the content of resolv.conf is
```

    nameserver 127.0.0.1
    search mylan

```
C's Wi-Fi interface is configured using NetworkManager. The wireless connection has IPv4 Settings | Method set to "Automatic (DHCP)". Consequently, its resolv.conf contains
```

    nameserver 192.168.0.2
    search mylan

```

---

### Post by JKyleOKC on 2013-02-07
Looks fine to me, when all machines run Precise 12.04. However the problem I had wasn't connected to resolvconf at all -- it stems from the router's DHCP server and its inability to deal with a local DNS. It's complicated by the fact that I have to maintain a pinhole through the router to enable a private FTP server that my customers use to send me large database files for recovery, and the router firmware only permits this when connected through DHCP. The whole thing is definitely an "edge case" and unlikely to be replicated by anyone else!

---

### Post by Doug S on 2013-02-07
It is a task just to keep up with this one thread... Very informative.
 
> In this case, it is a static file, not a symlink, resolvconf does not exist on the machine, and the badly behaved program is the DHCP server of the Motorola 3347 which is forcing the router's address and in the process deleting the other two lines. The immutable attribute solves the problem completely.I had the same on my old 10.10 server (which is now a 12.04 server). Even though I have static external IP addresses, my ISP rules required that I get them via DHCP. Additionally, my ISP responds differently for every other lease request, even though the request is identical, resulting in sometimes abbreviated lookups working sometimes not. That took forever to figure out, but in the end I forced some stuff on my DHCP server.
 
jdthood: I have seen you mention that RESOLVCONF=yes should be the case in /etc/default/bind9 [before]("http://ubuntuforums.org/showthread.php?t=2105685&highlight=RESOLVCONF") . I do not have that and everything is working fine. My drive to understand, and as I mentioned in [post 7]("http://ubuntuforums.org/showpost.php?p=12460702&postcount=7") of the previous thread, is from the perspective of the Ubuntu server guide, which makes no mention of it. The server guide is just starting the 13.04 edit cycle, so if improvements are needed, now is the time.

---

### Post by SeijiSensei on 2013-02-07
> **Doug S said:**
> My drive to understand, and as I mentioned in [post 7]("http://ubuntuforums.org/showpost.php?p=12460702&postcount=7") of the previous thread, is from the perspective of the Ubuntu server guide, which makes no mention of it. The server guide is just starting the 13.04 edit cycle, so if improvements are needed, now it the time.

Since most servers use static addresses as defined in /etc/network/interfaces, add the "dns-nameservers" and "dns-search" directives there in the stanza for eth0.

---

### Post by Doug S on 2013-02-07
Seiji, thanks for your reply. However, it does not cover the point I was trying to get to. By the way, I agree with your reply, and even linked to the same way back on this same thread. More importantly, what you said is also detailed in the [name resolution ]("https://help.ubuntu.com/12.04/serverguide/network-configuration.html#name-resolution")section of the Ubuntu server guide.
 
What I am trying to determine is when the file /etc/default/bind9 (I typed the path wrong before, but will edit) needs to have the line "RESOLVCONF=yes" and when it has to have the line "RESOLVCONF=no". If required, I'll fix the server guide during this release cycle. I have seen jdthood mention that it needs to be "yes" at least twice now. However, mine says "no", but my server is running bind9 and it knows to use itself as the DNS, as detailed in dhclient.conf:```
...
#prepend domain-name-servers 192.168.111.1;
[COLOR=red]prepend domain-name-servers 127.0.0.1;[/COLOR]
supersede host-name "mail";
supersede domain-name "smythies.com";
supersede domain-search "smythies.com";
...

```Edit: The answer to my question seems to be [here]("http://askubuntu.com/questions/239169/how-to-edit-etc-resolv-conf-on-ubuntu-12-04") (answer 1, by jdthood), although I'm not sure why how I am doing it via dhclient.conf is considered wrong.

---

### Post by jdthood on 2013-02-08
> **Doug S said:**
> What I am trying to determine is when the file /etc/default/bind9 (I typed the path wrong before, but will edit) needs to have the line "RESOLVCONF=yes" and when it has to have the line "RESOLVCONF=no".


The general principle is that anything that configures an interface (sets its address, adjusts routing, etc.) simultaneously supplies information about DNS services available *via* that interface. For example, along with an IP address, netmask and possibly host name, a DHCP client obtains nameserver addresses and a DNS search list. After it configures the interface it registers this DNS information with resolvconf. It also de-registers the information before it deconfigures the interface. Likewise nameserver addresses, etc., are included in the interface configuration stanza in /etc/network/interfaces. Ifup sends this information to resolvconf after it configures the interface; ifdown deletes that information before it deconfigures the interface. NetworkManager, pppd, et al. also register this information with resolvconf and de-register it when they deconfigure the interfaces that they control. 

Each time it receives new information, resolvconf updates resolv.conf.

When a nameserver is started locally and it is configured to answer recursive Internet DNS queries coming in on 127.0.0.1 then 127.0.0.1 becomes another nameserver address, associated with interface lo. This needs to be registered with resolvconf after the nameserver starts. Once the nameserver has stopped, 127.0.0.1 ceases to be the address of a nameserver so that address needs to be de-registered. To obtain this biconditionality the nameserver itself, or its initscript, has to call resolvconf.

In the case of BIND this behavior is enabled by setting RESOLVCONF=yes. (The reason for having a variable to control this is that BIND is not always configured to provide general purpose DNS service.)

Now keep in mind (1) that nameserver information associated with interface "lo" is given top priority by resolvonf, and (2) no more nameserver addresses are listed in resolv.conf by resolvconf after any loopback address. As a result of (1) and (2), any system that is configured to start BIND at boot and leave it running all the time has a resolvconf-generated resolv.conf that has exactly one "nameserver" line, namely "nameserver 127.0.0.1".

For such a system it is under normal circumstances equally good to put "nameserver 127.0.0.1" in /etc/resolvconf/resolv.conf.d/base. Or to delete the symbolic link /etc/resolv.conf and put a static file there containing "nameserver 127.0.0.1".

On such a system you will only see a difference after BIND is stopped. When resolvconf is "correctly" configured what happens then is that the BIND initscript de-registers the address 127.0.0.1 and resolvconf writes a resolv.conf containing a nameserver line with the address of the next best available nameserver. If one of the static configuration approaches is adopted, this will not happen --- /etc/resolv.conf will still contain 127.0.0.1 which won't work because the local nameserver has been stopped.

> 
If required, I'll fix the server guide during this release cycle. I have seen jdthood mention that it needs to be "yes" at least twice now. However, mine says "no", but my server is running bind9 and it knows to use itself as the DNS, as detailed in dhclient.conf:```
...
#prepend domain-name-servers 192.168.111.1;
[COLOR=red]prepend domain-name-servers 127.0.0.1;[/COLOR]
supersede host-name "mail";
supersede domain-name "smythies.com";
supersede domain-search "smythies.com";
...

```Edit: The answer to my question seems to be [here]("http://askubuntu.com/questions/239169/how-to-edit-etc-resolv-conf-on-ubuntu-12-04") (answer 1, by jdthood), although I'm not sure why how I am doing it via dhclient.conf is considered wrong.

The reason it's less than ideal is that it associates the nameserver address 127.0.0.1 with an arbitrary *external* interface. If you deconfigure that external interface then the address 127.0.0.1 is de-registered from resolvconf even though the local nameserver is still running. On the other hand, if you stop bind9 and the external interface is still configured then 127.0.0.1 remains registered even though there is no longer a nameserver listening at 127.0.0.1.

---

### Post by Doug S on 2013-02-08
Thanks for your detailed reply, and the time you took to do it.

---

### Post by jdthood on 2013-02-09
> **Doug S said:**
> Thanks for your detailed reply, and the time you took to do it.

You're welcome. 

I just checked out the 12.04 version of the Ubuntu Server Guide. It does need some work. E.g., it shouldn't say things like "Simply edit /etc/resolv.conf and add the following" (§3.1.1) any more. :)

Regarding BIND and resolvconf, you might be interested in bug #1091602 ([https://bugs.launchpad.net/ubuntu/+source/bind9/+bug/1091602](https://bugs.launchpad.net/ubuntu/+source/bind9/+bug/1091602)).  It is my wish that a script be added to the bind9 package which will cause named to use nameserver addresses registered with resolvconf as forwarder addresses instead of a static list. Such a script was available for BIND 8 and that script just needs to be included in the bind9 package with some tweaks. Anyone who would like such a feature is encouraged to add their voice to bug #1091602.

---

