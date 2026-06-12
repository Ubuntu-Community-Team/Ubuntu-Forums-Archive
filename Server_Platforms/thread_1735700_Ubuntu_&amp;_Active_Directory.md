---
title: "Ubuntu &amp; Active Directory ???"
date: 2011-04-21
forum: Server Platforms
---

### Post by fbifido on 2011-04-21
Can i make a active directory using ubuntu+samba+ldap+dns

---

### Post by JonRohan on 2011-04-21
Yes you can. Care to elaborate any further? :p

---

### Post by arrrghhh on 2011-04-21
I wouldn't say it's exactly like AD - it really depends on your requirements.

You can certainly setup an 'AD-like' environment with that, and perhaps with some tweaking it can be pretty much identical to AD.

I'm far from an expert on this matter, but like the previous poster inquired - we need moar info :D.

---

### Post by headvampyre@hotmail.co.uk on 2011-04-22
You can use a different setup before, google is your best friend tbh. There is Samba4, which is in experimental stages atm. I run it off a Mint 10 machine with only some minor issues :D basically, the only one i have found is that when using:

hosts deny = 0.0.0.0/0

the network slows to a crawl, and group policy tends to freeze.
heres the link:

[http://wiki.samba.org/index.php/Samba4](http://wiki.samba.org/index.php/Samba4) :)
if ya decide to go with that, PM me an ill help ya set it up :)

---

### Post by fbifido on 2011-04-26
> **JonRohan said:**
> Yes you can. Care to elaborate any further? :p

I have:
   50 windows xp pro worksation.
   40 ubuntu 804lts workstation, will upgrade to 10 lts later.

1 redhat 2.1 AS server ruuning oracle 8i (equinox account software).
1 ubuntu server running samba 3 as file-server.
1 windows sbs 2003 as terminal server (not active directory)
1 windows 2003 server running accpac 5.x (not sure if there is a linux ver.out there)
1 clearos 5.1 (firewall) (set in block-everything except this: mode)
1 centos 5.6 as zimbra email server. (might go back to Kerio, zimbra is a pain in the hasssssssssss).

plan to virtualize  all ther except z firewall with
2 blade-server with xen-server 5.x
and then replace the windows pc with think-client or zero-client box.
for the terminal-server it will be windows 2008 r2 ent server with xen-desktop from citrix.
the firewall will be untable 8.x
the equinux server will be ubuntu server with oracle 11gr2 database server

but i was told by citrix that we will need a active directory, that will not be virtualize, for user access, password and rights.

How do i get the linux servers connect to this AD?
How do i go about setting up a linux AD, to replace windows AD?
How to connect windows/linux/think-client to this linux AD?

---

### Post by AllGamer on 2011-04-26
may i ask you setup and configured all the previous ubuntu + redhat servers?

because, having gone through all those, there should have been a write up or a KB article in the company archive already for the procedures followed.

Anyways... you do not really get an AD with Linux

You get an LDAP server which is what AD was based on, just tweated by MS so they can say it's "better" than your average LDAP (BS IMO)

there are many guides on how to setup LDAP+SAMBA

Once you configure OpenLDAP just join it as part of the LDAP forest (using MS terms), then you can pick, as in configure which LDAP server will be the main LDAP server, and the rest will become just the fail over LDAP servers (think back to the NT4 times PDC 7 BDC)

once you have that established you can configure all your other servers to talk to this new LDAP server that you have configured and assigned as the PDC

the rest is straight forward, specially the SAMBA portion.

The tricky part is if you plan to import all the users from the existing windows AD to LDAP

now that is a super heavy tedious job

Google up some good scripts and that will save you some time

---

### Post by headvampyre@hotmail.co.uk on 2011-04-27
Also, could you please elaborate on how much locking down the Clients need? and how secure the environment needs to be.
Thanks

---

### Post by yvovandoorn on 2011-04-28
I'd say go to [www.likewiseopen.org](www.likewiseopen.org) and download the Ubuntu version for your computer. Install and join. That's it. 

No need to follow long guides or anything like that.

---

### Post by AllGamer on 2011-04-28
hmm.. i don't think that is what the [OP] wants

after reading the likewise open paid OS, it seems to suggest the OS is only a BDC or secondary DC, it doesn't appear to offer the option to replace windows AD completely, as it requires an actual windows AD to be running side by side.

the [OP] seems to be trying to completely break free from windows AD and have openLDAP replace AD

---

