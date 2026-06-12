---
title: "[SOLVED] name instead of IP"
date: 2008-09-30
forum: Server Platforms
---

### Post by TreeFinger on 2008-09-30
I have a few servers on my LAN. I would like to be able to SSH to them without typing their IP, instead using a more human readable name. How is this done?

---

### Post by skunkbad on 2008-09-30
It should be done through DNS on your machine. Probably by editing the hosts file.

---

### Post by MrFSL on 2008-09-30
I agree edit you hosts file.

This can be found in /etc/hosts

You will see some default examples. It should be as easy as:

IP Address     Hostname

**NOTE** you will have to edit this file as root.

---

### Post by jms1989 on 2008-09-30
I have this setup on all my computers, just edit your host file with the root user.

Linux: sudo nano /etc/hosts
Windows: wordpad.exe "C:\WINDOWS\system32\drivers\etc\hosts"

Insert your info with the ip of the computer first, followed by a space or a tab, followed by the name or domain you want to use. It would be ideal if you setup static ip addresses on the computers you want to access with a name instead of the ip because if the ip changes, your computer could point you to a different computer that has "stolen" another computers' ip.

You can add multiple names or domains for a specific computer by separating them with a space, no commas. Handy if you are running a server with multiple domains.

Btw, windows only support about six domains or names per line so if you have more than six like I do with my pc, you should add another line with the same ip. As far as I can tell, linux doesn't care how many names on ip may have.

Hope this answers your question, cheers!

---

### Post by kpatz on 2008-09-30
If you're running BIND on one of your servers, you could set up an in-house DNS server and assign your host names there.  If you're already using BIND as a caching nameserver, you can use that as well for internal DNS.

That way, you don't have to update the hosts file on each and every machine.

---

### Post by TreeFinger on 2008-09-30
> **kpatz said:**
> If you're running BIND on one of your servers, you could set up an in-house DNS server and assign your host names there.  If you're already using BIND as a caching nameserver, you can use that as well for internal DNS.

That way, you don't have to update the hosts file on each and every machine.


This is what I would like to do. I find it kind of stupid to have to do it on every machine. 

Could you point me to a HOW TO? Would setting this information up on my router/firewall be smart?

---

### Post by lykwydchykyn on 2008-09-30
> **TreeFinger said:**
> This is what I would like to do. I find it kind of stupid to have to do it on every machine. 

Could you point me to a HOW TO? Would setting this information up on my router/firewall be smart?

[http://ubuntuforums.org/showthread.php?t=236093](http://ubuntuforums.org/showthread.php?t=236093)

You need to edit your DHCP settings (on the router, or on the server if it's doing DHCP) to point DHCP clients to your internal DNS first.  Since most OS's let you specify at least two DNS servers, I'd make the second one your ISP's DNS, just so you can still use the internet if your server goes down.

---

### Post by TreeFinger on 2008-09-30
> **lykwydchykyn said:**
> [http://ubuntuforums.org/showthread.php?t=236093](http://ubuntuforums.org/showthread.php?t=236093)

You need to edit your DHCP settings (on the router, or on the server if it's doing DHCP) to point DHCP clients to your internal DNS first.  Since most OS's let you specify at least two DNS servers, I'd make the second one your ISP's DNS, just so you can still use the internet if your server goes down.

thanks for the replies all.


I would just like my DNS server to handle intranet and have my ISP's DNS handle internet. I'm planning on having my DNS server running on my router/firewall/proxy server. Is this OK?

---

### Post by doas777 on 2008-09-30
> **kpatz said:**
> If you're running BIND on one of your servers, you could set up an in-house DNS server and assign your host names there.  If you're already using BIND as a caching nameserver, you can use that as well for internal DNS.

That way, you don't have to update the hosts file on each and every machine.

+1 for Bind. I first seriously tried ubuntu as a dns server (and my upstairs A/V box) so i could address my lan. Learning to  write the zones was my first real challenge in linux.

good luck and have fun,
Franklin

---

### Post by doas777 on 2008-09-30
> **TreeFinger said:**
> thanks for the replies all.


I would just like my DNS server to handle intranet and have my ISP's DNS handle internet. I'm planning on having my DNS server running on my router/firewall/proxy server. Is this OK?

I've heard that you should be a little careful about using dns servers on comercial routers. if your using a *nix box as a router, disregard this post. there are several [upnp exploits]("http://www.gnucitizen.org/blog/hacking-the-interwebs/") that can allow xssers to poison your lookups.

the vulnerability is a touch esoteric, so if you disable upnp or just don't care, the router dns is probably easier to configure than bind, though adding "Forwarders", or isp dns servers is easy. just be sure to disable zone transfers, or restrict them to your local domain.

here is a tutorial on [bind]("http://ubuntuforums.org/showthread.php?t=236093"). here is [another]("http://www.ubuntugeek.com/dns-server-setup-using-bind-in-ubuntu.html").

now keep in mind, you do not need to do this on every box. all you have to do is set up bind on one server. then on each of your statically addressed machines, just set the dns server address to point to your bind server. for your dynamically assigned boxes (dhcp clients), just change your dhcp server to push down your bind servers address. keep in mind that if you want to use dhcp and still assign names to those hosts, you will need to set up static leases, or use dynamic dns.

good luck,
Franklin

---

### Post by TreeFinger on 2008-09-30
> **doas777 said:**
> I've heard that you should be a little careful about using dns servers on comercial routers. if your using a *nix box as a router, disregard this post. there are several [upnp exploits]("http://www.gnucitizen.org/blog/hacking-the-interwebs/") that can allow xssers to poison your lookups.

the vulnerability is a touch esoteric, so if you disable upnp or just don't care, the router dns is probably easier to configure than bind, though adding "Forwarders", or isp dns servers is easy. just be sure to disable zone transfers, or restrict them to your local domain.

here is a tutorial on [bind]("http://ubuntuforums.org/showthread.php?t=236093"). here is [another]("http://www.ubuntugeek.com/dns-server-setup-using-bind-in-ubuntu.html").

now keep in mind, you do not need to do this on every box. all you have to do is set up bind on one server. then on each of your statically addressed machines, just set the dns server address to point to your bind server. for your dynamically assigned boxes (dhcp clients), just change your dhcp server to push down your bind servers address. keep in mind that if you want to use dhcp and still assign names to those hosts, you will need to set up static leases, or use dynamic dns.

good luck,
Franklin

I am using a gentoo linux install as my router/firewall/proxy.

I am using dnsmasq and I just had to simply edit my /etc/hosts file on that box and now I can access my static IP LAN servers by a name :) I don't believe I have a need for BIND.

Thank you, marking as solved.

---

