---
title: "dealing with arrays in bash files"
date: 2013-08-23
forum: Server Platforms
---

### Post by sophie_horner on 2013-08-23
How do you basically manipulate arrays ? I'm aiming to make a list of names, Macs, and IPs in three arrays that I can rewrite arptables and dhcpd.conf with in one go.
basically I need to know the syntax so I can  insert the data in each array into a echo type instruction to create both the arptables and DHCPd.conf, I imagine with a "for" loop.
any examples ?
pleeeease....

---

### Post by prodigy_ on 2013-08-23
List:
```
$ a[0]="foo"
$ a[1]="bar"
$ echo "${a[@]}"
foo bar
```

Associative array:
```
$ declare -A a
$ a["foo"]="b"
$ a["bar"]="c"
$ echo "${a[@]}"
c b
```

But from your explanation I can't really understand what you're trying to achieve.

---

### Post by 1clue on 2013-08-23
Maybe this is a n00b question, but why are you trying to write to arp tables?  The arp should be handled directly by the networking stack when a device contacts your computer.

---

### Post by sophie_horner on 2013-08-23
Thanks !!
good question, I'm trying to find a way to impose a fixed IP to each client and in case they choose a fixed IP themselves, deny access to a mac address that has any other IP than the one I assigned assigned in dhcpd.conf, hence with arptable rules...
so as not to have to write each IP + mac address twice seeing as I would have to make a rule for each client in arptables too. Also client addresses are going to be changing often
...
I have done some research and haven't found a better way to get IPs imposed. If someone has a better idea, I'm all ears.... Or rather eyes ;)

---

### Post by 1clue on 2013-08-23
I'm not a trained network admin but I served in that capacity for a few years.  You don't want to do it like that.

Falsely writing arp tables is a bad idea IMO.  I don't know exactly what will happen, but arp just a cache of hosts which have recently contacted your host.  I'm pretty sure that adding false entries will cause some sort of error, even if that is simply more network traffic.  Besides, I think that arp will automatically re-map the mac address to whatever they have changed it to the next time the host contacts it.  This isn't a security device, it's a communications enabler.

You need to configure the domain (or whatever is appropriate for your client OS) such that a normal user can't change the network configuration.

You need to set up your DHCP such that in most VLANs the DHCP server won't accept unknown MAC addresses.  This will keep people from plugging in a USB network card or similar and getting around whatever restrictions you have in place.

You might consider some sort of tool that greps the dhcpd.conf file every so often for expected ip's and expected mac addresses, and make sure that the arp table matches.  Or vice versa.

You need some sort of firewall to prevent unknown hosts from accessing anything at all.

---

### Post by prodigy_ on 2013-08-23
> **sophie_horner said:**
> I'm trying to find a way to impose a fixed IP to each client
Why? Generally you want to use static IPs for servers and make workstation register themselves in DNS. Anyway, you can define MAC addresses reservations in dhcpd.conf:
```

host myhost {
  hardware ethernet 00:11:22:33:44:55;
  fixed-address 192.168.1.2;
}
```

As for the rest, if you need to control what host/interface is "authorized" to use a particular IP, you need a managed switch.

---

### Post by 1clue on 2013-08-23
Back when I was doing this sort of thing for my office, I used to put that entire host structure on a single line.  That way I could see the name, mac address and ip address with grep.

---

### Post by sophie_horner on 2013-08-23
Thanks for feedback and advice... but I'm still a bit confused :
> [COLOR=#000000]Falsely writing arp tables is a bad idea IMO[/COLOR]
I thought "arptables" was just like a MAC firewall - I didn't mean a set of arp instructions... at least I thought they were different things ?!
> [COLOR=#000000]You need some sort of firewall to prevent unknown hosts from accessing anything at all.[/COLOR]
That's exactly what I want - I'd like to go about solving the issue without setting up domains or client authentication ? starting to wonder whether it'll be possible :|

I guess I'll have to start looking at "Samba", Winbind and stuff like that (most of clients are on Windows)... grrr...
LOL - realizing I still have a stack of work to do ;)
Thanks a lot anyhow :) It cheers one up to get some help with all this ](*,) hehe...

---

### Post by 1clue on 2013-08-23
Most of this has nothing to do with Windows.  It's networking.

It's just that you're trying to use the wrong tool for the job.  And yes, if you're starting here then you have a stack of work to do.

arp is nothing to do with security.  It's just how a normal TCP/IP stack works, it maps an IP address with a Mac address, but as soon as a packet comes along with a mac address and a TCP address the arp table is updated, no security and an old one with different values is going to be overwritten.  It's a cache.  Writing your own table over the one the operating system is not going to give you anything but grief.

What was said by prodigy_ is true, most offices would use a managed switch to limit what can happen on a specific network interface.  I said 'some sort of firewall' because that's how I think most people unfamiliar with managed switches would think of it.

You'll need:
[LIST=1]
[*]dhcpd to deny automatic addresses to unknown mac addresses.
[*]Untrusted clients (workstations) to disallow network configuration or system renaming to normal users.
[*]A dynamic DNS setup linked with dhcpd so you have a human-understandable reference for the boxes.
[*]Name each box, put its IP address and name on a non-removable sticker that can be seen over the shoulder of the users.
[*]Some way to do what the point of your original post was really about.
[/LIST]

How many people are you dealing with here?  A managed switch is usually a four digit number of dollars, and not necessarily at the bottom of that range.  Setting it up can be arduous, but once you get it done they're amazing.

If it were me, here's what I would get on the network switch end of things:
[LIST=1]
[*]A real firewall from a reputable manufacturer, and pay a real professional to set it up for you initially.  These guys will spend more time figuring out what you actually want than they will setting things up, and it'll be done right.  Most small or medium businesses do this sort of thing.
[*]One or more managed switches, from a reputable manufacturer, and get that same guy to set them up initially.
[*]You might want to keep that guy on call.
[*]Set up VLANs that make sense for your business.  This is a software-enforced group of physical networks.
[*]Set up a bad-boy time-out VLAN to put miscreants in, with no access to anything they shouldn't get.
[*]A conference room VLAN that will actually allow unknown computers to connect, but only access outside access, not inside.  This lets the visitors do presentations but not get at your stuff.  You could have a presenter port that has full access.
[/LIST]

VLANs for workstations would not allow unknown network cards.  I would scan the arp table from the switch or the dhcp server to see if somebody has an incorrect IP address for the mac address.  That means they're cheating somehow.

---

### Post by 1clue on 2013-08-23
By the way, either samba or a real domain controller is definitely in the cards here.  If you've got a bunch of Windows users and your network doesn't work the way they expect, you'll get unending grief for it.

---

### Post by Brian_Murray on 2013-08-23
+1 to what 1clue said.  Also if the environment is fairly static with the workstations to network ports you can also enforce port security that will tie each port to a specific MAC.  Violations can also be setup to down the port if needed.  Additionally a real managed switch with vlans and layer 3 routing opens up tons of other options that are well worth the price in most cases.  You can even implement network access control which allows you to authenticate hosts and verify that they are running the correct versions of AV or whatever else prior to allowing them access to your more important vlans.

I'm not entirely clear on what you're trying to accomplish, but if by "deny access" you mean internet access, then you could possibly just add static arp entries into your firewall.  This is VERY easy to do on a Cisco ASA or PIX.  By forcing your the network resource to only map a specific MAC to a specific IP in the arp table you effectively break communications between it and the gateway.  This same logic could likely be used on other network resources but would be far too labor intensive to be practical.

---

### Post by 1clue on 2013-08-24
> **Brian_Murray said:**
> I'm not entirely clear on what you're trying to accomplish, but if by "deny access" you mean internet access, then you could possibly just add static arp entries into your firewall.  This is VERY easy to do on a Cisco ASA or PIX.  By forcing your the network resource to only map a specific MAC to a specific IP in the arp table you effectively break communications between it and the gateway.  This same logic could likely be used on other network resources but would be far too labor intensive to be practical.

OK this is what the OP was talking about at first, but I thought arp was only a cache.  I've never heard of somebody rewriting arp as a security measure.

Are you saying that there's a Cisco command to only accept a packet if the mac address matches the IP, or are they really writing entries to arp?

I used Cisco managed switches, but it was a long time ago and we never tried to control things quite so much as this guy is doing, so it's either new or I never knew about the feature.

---

### Post by Brian_Murray on 2013-08-31
It's more of a "hack" to do something it's not designed to do.  ARP is a cache but you can force a static entry into the table.

On the Cisco ASA from configure mode it's the arp command:

[http://www9.cisco.com/en/US/docs/security/asa/command-reference/a3.html#wp1716126](http://www9.cisco.com/en/US/docs/security/asa/command-reference/a3.html#wp1716126)

Keep in mind I'm not recommending it, it's really not the right way to do things, but in a pinch it could come in handy.

---

