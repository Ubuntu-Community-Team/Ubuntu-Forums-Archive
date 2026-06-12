---
title: "How to set up DNS"
date: 2009-12-28
forum: Server Platforms
---

### Post by vamega on 2009-12-28
Hello.

I just installed a DNS server using the command

```
sudo tasksel dns-server
```

I would like to now configure it. I'm trying to set it up for only the local machine, as a way for me to be able to redirect calls to [www.test1.com](www.test1.com) to localhost.

Although I know that this can more easily be achieved by editing the hosts file, I'd like to learn how to do it this way so that when I move over to a larger network, I can use the same set-up.

Does anyone know what I need to edit in order to get the desired results?

Thanks a lot

Vamega

---

### Post by BkkBonanza on 2009-12-28
I'm not familiar with this method for installing nor with the package "dns-server". Do you know what actual server software that installs? I couldn't find that name in the repos. Usually installs are done with apt-get or aptitude.

By far the most popular dns server out there is Bind. I'm not a fan of it at all as I think it's a pig. I have been using djbdns for years and like it a lot because it uses very little memory and is easy to configure (although perhaps a bit cryptic to some users). There is now a couple ubuntu packages for djbdns, the second one having patches and called dbndns. I haven't tried them as I have always built from source. Last I heard the djbdns ubuntu package had some install problems, although I think it was fairly easy to fix afterwards.

If you google you will find many tutorials on djbdns and on bind and finding a good one for ubuntu would be a good start.

---

### Post by msw on 2009-12-28
sudo tasksel dns-server will install BIND. I agree with your comments that the OP should look at using djbdns instead.

---

### Post by slakkie on 2009-12-28
Read a manual. There are plenty of examples to setup bind9 on Debian/Ubuntu on the web.

---

### Post by BkkBonanza on 2009-12-28
Here's a useful article about djbdns vs Bind.

[http://www.linuxjournal.com/article/10112](http://www.linuxjournal.com/article/10112)

I don't think this is the easiest way to install but I found the history and feature details interesting. When I first used djbdns I used the djbdnsrock.org tutorial.

---

### Post by Xiuh on 2009-12-28
I had a rough time getting Bind setup and even more problems having DHCP update my records. It's definitely not needed for a small business local LAN network. However, I'll agree that it's a good learning experience. I started out doing server administration with Win2k3. It's amazing how many concepts I never understood using Microsoft's DNS server for years and how fast I picked them up after only a few days working with Bind.

---

### Post by vamega on 2009-12-28
Bkk Bonanza, thanks a lot for telling me about djbdns, I read up the article on Linux Journal, and it seems like a great program. However it did mention that I need to use two different ip addresses to run the two components.

Perhaps I can move over to djbdns later, but for the time being I'm running everything off a single machine, and I may be mistaken, but I believe that limits me to a single ip address. 

Therefore I think I'll stick with BIND. Anyone have any idea how I can configure it to map [www.localtest.com](www.localtest.com) to 127.0.0.1?

Thanks a lot

---

### Post by slakkie on 2009-12-28
[http://www.debianhelp.co.uk/dnsrecords.htm](http://www.debianhelp.co.uk/dnsrecords.htm)
[http://ubuntuforums.org/showthread.php?t=236093](http://ubuntuforums.org/showthread.php?t=236093) for Dapper, but the instructions are valid for Ubuntu/Debian.

---

### Post by Xiuh on 2009-12-28
Documentation to setup DNS for Ubuntu 9.10

[https://help.ubuntu.com/9.10/serverguide/C/dns.html](https://help.ubuntu.com/9.10/serverguide/C/dns.html)

A few things in it I eventually ended up doing a bit different. However, it's short and to the point. The "DNS HOWTO" link listed in the references in the link above also did a nice job of keeping things straight forward while digging a bit deeper into Bind.

---

### Post by noway2 on 2009-12-28
Vamega,  depending on what you are trying to do, and based on your description I think this applies, the two IP / two server system isn't necessary.  That setup is necessary when one is making a publicly authoritative DNS system.

Bind9 is quite easy to setup and there are several excellent how to documents that will get you started.  My personal favorite is: [http://lani78.wordpress.com/2008/08/09/setting-up-a-dns-for-the-local-network/](http://lani78.wordpress.com/2008/08/09/setting-up-a-dns-for-the-local-network/).  You might also find this one of interest: [http://lani78.wordpress.com/2008/08/12/dhcp-server-update-dns-records/](http://lani78.wordpress.com/2008/08/12/dhcp-server-update-dns-records/).

When I first setup my home server, within the first couple of hours, knowing little about Ubuntu, I was able to get a DHCP-DNS co-ordinated system going in about 30 minutes using these two guides.

---

### Post by BkkBonanza on 2009-12-29
@vamega,
I know you're on your way with Bind now, but I'm adding a bit more info here just for clarity in future.

djbdns does run the recursive and authoritative dns as separate programs, so needs two ip addresses to run both on one machine. However, it is easy to add a second ip to a server, and due to the nature of the two types of dns it isn't a problem. A second ip just requires a few extra statements in the interfaces file creating a new virtual interface, for example, eth0:1.

Usually your local lookups would be sent to the recursive dns (dnscache), and the authoritative dns (tinydns) would handle name lookups from the public (and local ones  via dnscache). So the authoritative dns would be on the public facing port. 

The recommended way to run Bind (or any DNS) is to keep the authoritative and recursive servers on separate ips. A lot of people still run them on one port though.

---

### Post by vamega on 2010-01-07
Thanks BkkBonanza.
I'll keep that in mind for the future.
Where can i learn about creating virtual interfaces.
I used to use VMWare, and I remember it creating a bunch of virtual interfaces that showed up in the output of ifconfig, but I don't know how to create one of my own.

---

### Post by noway2 on 2010-01-07
I think what BkkBonanza is referring to is commonly called an alias eth0 interface.  Your ethernet card can be assigned and respond to multiple IP addresses.  To do this you need to modify the /etc/network/interfaces file.  Here is an example:

auto eth0:0
iface eth0:0 inet static
address 192.168.1.2
netmask 255.255.255.0
broadcast 192.168.1.255
network 192.168.1.0

If you notice, the declaration is eth0:0, where the :0 designates this adapter as a virtual (alias) of the eth0 port.

---

