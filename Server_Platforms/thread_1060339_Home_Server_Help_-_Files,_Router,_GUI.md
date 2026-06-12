---
title: "Home Server Help - Files, Router, GUI"
date: 2009-02-04
forum: Server Platforms
---

### Post by quietas on 2009-02-04
Currently I have an aging Sonicwall as my home gateway and firewall. It really is overkill and is better suited to an enterprise environment, thus it is being donated to a new startup non-profit shortly. In the meantime I am looking to replace the Sonicwall, my HP NAS, and Ubuntu fileserver, all with one easy to administer GUI driven wonderboxen.

My needs:
[LIST]
[*]Firewall
[*]Gateway
[*]DNS
[*]DHCP
[*]Samba (multiple shares, guest readonly, user access, ...)
[*]GUI config (simple, quick, and wife enabled)
[*]Proxy (caching, transparent, reportable)
[*]Web Content Fitering (user or MAC/IP based to secure web for kids)
[*]Firefly Media Server
[/LIST]

Right now I have 3 boxes all drawing power 24/7 doing what I need and far more. I'd like to simplify this all back to one new box with a low-power system such as an Atom 330, Antec EarthWatt PUSm and some WD Green hard drives. Low power consumption is a key, but I also need this unit to be transparent 99% of the time and that 1% when I need to do something with it I would prefer a simple web based GUI. 

KEY FEATURE: Wife enabled. She's PC friendly and knows *nix a bit, but the GUI is essential. No CLI for day to day operation, I can do that just fine for setup (I run 4 Ubuntu 6-8 servers at work), but if it's blocking a site and she needs to get to it when I am not around, I need her to have at least basic understanding.

Any ideas? I thought Ubuntu first, but how to simplify the process is my stumbling block.

---

### Post by HermanAB on 2009-02-04
You can do all of that on an Ubuntu machine with two ethernet ports.  It will take you a while to set it all up, but it sure can do it all.

Cheers,

Herman

---

### Post by quietas on 2009-02-04
Any good web GUI's to replace Webmin yet and cover all those functions? I can manage to get it all set up I am sure, but I'd prefer to have a point and click interface.

---

### Post by HermanAB on 2009-02-05
Hmm, if you want to do point and click, then you should install Mandriva Linux.  It has wizards for everything.

Ubuntu is not the easiest Linux - it is kinda intermediate and its wizards still have a long way to go to catch up with Suse and Mandriva.

Cheers,

Herman

---

### Post by albinootje on 2009-02-05
> **quietas said:**
> 
[list]
[*]Firewall
[*]Samba (multiple shares, guest readonly, user access, ...)
[/list]


I just like to add that putting gateway and your data on just 1 machine might not be the best idea.
The moment an attacker manages to get in, then all of your data is also accessible.

Does your dsl-router or cable-modem not supply a firewall and dhcp and DNS ?

---

### Post by quietas on 2009-02-05
> **albinootje said:**
> Does your dsl-router or cable-modem not supply a firewall and dhcp and DNS ?

Nope, my cable modem feeds me the straight internet connection unfiltered along with my static IP. DNS is provided my my ISP and is what my Sonicwall provides via DHCP.

CLI Ubuntu is not a problem, I run 2 samba fileservers, an intranet webserver with Wordpress, GLPI and OSC NG, along with two Zimbra mail servers. All via Ubuntu Server 6.06 or 8.04, all CLI no X on those boxes.

At home though I'd prefer a simple straight forward web admin page of some sort, but again no need for X on a headless box which lives at the bottom of my rack. (Yes I have a full 7ft rack in a closet). 

**One requirement I forgot to add, Firefly Media Server.** I need my iTuna hookup with my many gigs of music throughout my house.

ClarkConnect comes close, but it really does far more than I need. It works, I played with it today and I see no problems with it in a small/medium office. Especially the paid version, the community version is a bit gimped for my tastes. Also CC seems to have issues getting Firefly to work well.

PFsense or IPcop, even Ebox, seem to be great firewall/router/gateway systems, but they stop there. Yes, that is all they were made to do and they do it well, but there is then the need for more boxes again. For the Home environment, I see no need for multiple systems with firewalls and storage.

Hold the train there.... Multiple physical boxes is exactly what I don't want to do, too much wasted power and actual space. 

How about something like VMware ESXi?  PFSense, IPCop, or Smoothwall for the gateway virtual machine. Then create a second virtual machine to run Ubuntu Server 8.10 and feed it all my terabytes of storage drives to share out via Samba and firefly. At this point I could add more machines or add on to the seconf vm for Apache or whatever. Webmin would work fine to manage the fileserver, though it's frowned on still by the Ubuntu devs.

Any ideas on a Webmin replacement?

---

### Post by Go_Big_Blue on 2009-02-06
eBox seems to be a pretty good web-based gui for and Ubuntu Server setup.

Try [http://www.howtoforge.com/running-a-file-and-print-server-with-ebox-on-ubuntu8.04-server](http://www.howtoforge.com/running-a-file-and-print-server-with-ebox-on-ubuntu8.04-server)

---

### Post by quietas on 2009-02-06
> **Go_Big_Blue said:**
> eBox seems to be a pretty good web-based gui for and Ubuntu Server setup.


Reading through the Ebox site it looks like the web GUI will work for most of the management functions. It also deals with the proxy and content filtering. Samba seems to be added in and with a normal Ubuntu server install I will be able to run Firefly unlike PFsense, IPCop, ClarkConnect, or others.

I'll be working on it tonight after I locate a decent fakeRAID card here in town to provide some SATA ports for my large drives.

---

