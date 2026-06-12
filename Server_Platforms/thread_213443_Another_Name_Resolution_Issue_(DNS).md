---
title: "Another Name Resolution Issue (DNS)"
date: 2006-07-11
forum: Server Platforms
---

### Post by Martin.Snyder on 2006-07-11
I've searched through the forums, and I don't think I've seen this exact issue elsewhere (yet).  I have seen some very similar stuff though, so maybe my problem might shed some light on the underlying issue.

To summarize:
  On a new installation of Ubuntu 6.0.6 Server, all DNS lookups fail for me.  I was able to resolve this by setting my network to use a static IP instead of DHCP.  What makes this issue slightly different than the others that I've seen is that my /etc/resolv.conf correctly lists the name server entry.


The machine in question is a P4 3.0Ghz Dell box (4700 series).  It's connected as follows

Dell 4700
  Netgear 10/100 switch
    Linksys WRT54G Router - 192.168.0.1
      Westell DSL Modem (Verizon DSL) - 192.168.1.1

The DSL modem is the DNS server for the network.  Other machines on the network include:
  Mandrake Linux 10.1 (server) (static IP)
  Powerbook OSX 10.3 - DHCP
  Windows XP SP 2 - DHCP

After the clean install, the ubuntu box cannot reach anything by DNS name.  dig, host, nslookup all fail with no information, even with debug and verbose flags set.  They just timout after 30 seconds or so and then report a generic failure.

As I mentioned before, /etc/resolv.conf correctly lists the name server.  This file matches the file on my other linux box and the DNS server reported there (192.168.1.1) matches what all my other machines report.  In addition, when I switch to static IP, name resolution is fine with the exact same resolv.conf file.

The machine can successfully reach local and external machines by IP address.  This was confirmed with ping and wget.

This machine is supposed to have a static IP, so there's no issue that I'm personally looking to resolve.  I would be happy to run any tests or diagnostics if it would help the experts here.

- Martin

---

### Post by MonkeyNet on 2006-07-11
Have you tried setting the DNS in resolv.conf to an external DNS server?

Have a look on the Verizon Support Page to see what your dns settings should be.

I am in Australia and the Netgear router that I use sometimes has issues doing DNS lookups, so I just use my ISPs DNS servers instead which means that  I never have any issues. That would be the first thing that I would check.


Cheers,

Andrew

---

### Post by Martin.Snyder on 2006-07-11
No, I did not try that.  It was on my list of things to try, but since moving to a static IP "solved" it I did not need to go any further.

I would note though, that with a static IP, I can resolve names against the same DNS server set by the DHCP server (192.168.1.1).  The resolve.conf file was correctly updated by the DHCP client when I first logged on, and I was able to resolve names without modifying that file after I switched to a static IP.

At one point, I did attempt to at least identify the Verizon DNS servers in case I needed them later.  This proved to be harder than I expected.  I did find this alternative that might save people time who want to pursue this.

[http://www.opendns.com/](http://www.opendns.com/) (ISP Agnostic DNS service with other benefits).

---

### Post by LordHunter317 on 2006-07-11
This is an issue with the way the dhclient-script works in dhcp3-client.  If you install the 'resolvconf' package and reboot, it will work.  

Basically, your working DNS is getting plowed by the second connection.

---

### Post by Martin.Snyder on 2006-07-11
LordHunter,

  Can you provide a link so that I might read more about the issue (to satisfy my curiosity).  What do you mean by "second connection?"

- Martin

---

### Post by LordHunter317 on 2006-07-11
Your machine has two NICs and is hooked up to two networks, correct?

Anyway, this can cause issues with the default dhclient-script.  Basically, it prefers overwriting /etc/resolv.conf to preserving the information already there.

---

### Post by Martin.Snyder on 2006-07-11
> **LordHunter317 said:**
> Your machine has two NICs and is hooked up to two networks, correct?

Anyway, this can cause issues with the default dhclient-script.  Basically, it prefers overwriting /etc/resolv.conf to preserving the information already there.

No, that would be a pretty important detail for me to have omitted from the original post, don't you think?

One nic, one connection to the single network as mentioned in the first post.

There is nothing exceptional about this setup (and like I said above, I have things working).  It's just a stock Dell box with a fresh ubuntu install.  With the (default) DHCP setup, I get no DNS resolution.  When I switch to static IP (and make no other changes) then I do get DNS resolution.  Everything else works fine either way.  /etc/resolv.conf is the same in both cases.

- Martin

---

### Post by LordHunter317 on 2006-07-11
WEll, I'm confused.  You have two IP networks on the same physical segment?

If so, that's bad, and it's no wonder things aren't working.

---

### Post by Martin.Snyder on 2006-07-11
Ok, I understand what's confusing you.

1. The DSL modem acts as a gateway and DHCP server.

2. The router is a DHCP client to the DSL modem.  It uses 192.168.1.1 as it's gateway and receives a 192.168.1.x IP address from the modem.

3. The router then acts as a gateway and DHCP server to the 192.168.0.x network (all routers have two IP addresses, one for the internal network and one for the external network).

4. The Ubuntu box makes a DHCP request to the router and receives a 192.168.0.x IP address.  It's gateway is 192.168.0.1.

5. The DNS server is 192.168.1.1.  This information is given to the router in step 2 (when it gets an IP address from the modem).  When the Ubuntu box (or any other machine on the network) fetches a new IP address from the DHCP pool, it also gets the DNS information (192.168.1.1).

There's nothing wrong with the setup.  Every machine on the network behaves fine (a mix of linux, windows and OSX machines).    The ubuntu box, as I mentioned, can interact with the network fine in both cases.  The only issue is that when it fetches a dynamic IP address via DHCP, it can't do DNS resolution (even though it knows the correct DNS server of 192.168.1.1).  With static IP and the exact same DNS server information, it works fine.

- Martin

---

