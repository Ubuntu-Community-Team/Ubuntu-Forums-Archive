---
title: "To sun or Not to Sun"
date: 2007-06-29
forum: Sun Sparc Users
---

### Post by Cwelle on 2007-06-29
Hello, 

I have come into possession of quite a bit of equipment. Some of it includes several Sun computers and Servers. 

Enterprise 220R
Enterprise 250
Sun Fire 280R
Storedge A1000 Full HD's unknown size
Storedge D1000 Full HD's unknown size
3 x Netra T1 105
Sparc 20
SparcServ1000
3 x Ultra 5

I was wondering if any of this equipment would be worth trying to get Ubuntu to work on. It would be a Apache, SQL SMTP Services on it. 

Any responses are greatly appreciated. 

Chris

---

### Post by hardyn on 2007-06-29
im not a sun guy, but i did some googling; the sun fire, looks reasonable hot... 1200mhz machine.
might be fun if you were looking for a project.

---

### Post by netztier on 2007-07-01
> **Cwelle said:**
> 
Enterprise 220R
Enterprise 250
Sun Fire 280R
Storedge A1000 Full HD's unknown size
Storedge D1000 Full HD's unknown size
3 x Netra T1 105
Sparc 20
SparcServ1000
3 x Ultra 5

I was wondering if any of this equipment would be worth trying to get Ubuntu to work on. It would be a Apache, SQL SMTP Services on it. 


Impressive :-) Will cost you an arm and a leg in terms of electrictiy and cooling if you want to run them all, but hey.. that's your choice ;-)

The **Enterprise 220R** is similar to the Ultra60, that should run nicely, same for the Enterprise 250, which I believe is similar to the Ultra2 family (correct me if I'm wrong!).

The **StorEdge** boxes might be tricky, since they have HVD-SCSI (High Voltage Differential) connectors that require special SCSI HBAs in the systems you want to connect them to. Check if any of your boxes have one of these - I don't know any of them, so I can't tell you if they're supported by the Penguin. 

The A1000 and D1000 are similar, but have one major difference: the A1000 contains a hardware RAID controller, the D1000 is "just a bunch of disks". I have no information if the RAID controller can be configured via OBP alone or only via some configuration tool that is certainly available for Solaris, but probably not for Linux.

The **Ultra5**s are straightforward to use, but might turn out somewhat tricky if you want them to run X.org - but the forum holds quite a few hints about this. Running ubuntu-desktop on a SPARC is a story for itself anyway - consider sticking to 6.06 LTS for that purpose (and disable any use of OpenGL - it crashes X.org everytime).

Speaking of X.org: If any of the machines contains a card based on a Permedia Chip (such as the PGX32, AFAICR), don't expect to get it to run X.org - reports here in the forum suggest that the glint driver doesn't work with these. ATI chips as in the U5/10 and on the PGX64 (I believe..) should work, and the Creator/Creator3D and Elite3D as well - the latter only with the **afbinit** package

About the T1 systems: I don't know any of these - can't help you there -  but I think I've seen posts about these here on the forums.

The **Fire 280R** is most interesting, of course - please find out what FC-AL controller it has. I believe it is supported in Linux  -  after all it's similar to the Blade1000 and there were reports about Linux on the Blade 1000. The tricky step might be in how to get it going; possibly you'll have to configure your own initrd.img to include the correct module.

The other systems seem to be from the pre-sparc64 era. AFAIK, Ubuntu currently does not support these, other distros however might.

best regards

Marc

---

### Post by Blood Fluke on 2007-07-01
> **Cwelle said:**
> Hello, 

I have come into possession of quite a bit of equipment. Some of it includes several Sun computers and Servers. 

Enterprise 220R
Enterprise 250
Sun Fire 280R
Storedge A1000 Full HD's unknown size
Storedge D1000 Full HD's unknown size
3 x Netra T1 105
Sparc 20
SparcServ1000
3 x Ultra 5


Unless you want to buy SCSI cards for them, the U5s are basically useless.  They have a very badly brain-damaged IDE chipset that ruins performance :(

The SS20 and the SS1000 won't run Linux.   The SS1000 won't run any modern Solaris, either, but it's a collectors item due to its rarity.

The others are all servers, with poor or no graphics.  I can't imagine running Linux on them when Solaris is available for free.

---

### Post by deserthowler on 2007-07-07
the SS20 may or may not run Linux, depending a lot of the components.  There is a problem with certain processors for one thing.  It sure won't run Ubuntu but Debian sarge (legacy) works fine on my SS20.  I stuck with the 2.4 kernel. 

It, however, is graphically and speed "challenged".  I use fvwm and command-line and text based programs.  Some very lightweight graphical front ends work too.  It's SLOW.

My friend, a professional system designer, uses NetBSD and swears by it.  He uses it as a file server with SSH.  

I think, if you go for Solaris, you are limited to something like Solaris 7 but am not sure.

If you are looking for something to occupy your time it works fine.

I know of people who use OpenBSD or Solaris on some of the other ones you mentioned.  They are happy.

Earl

---

### Post by HermanAB on 2007-07-08
The last one a SparcStation can run is Solaris 7.  FreeBSD is better.  There isn't anything else really.  

See this: [http://aeronetworks.ca/obsolix.html](http://aeronetworks.ca/obsolix.html)

---

### Post by toastkid on 2007-07-09
You won't get any modern release of FreeBSD to run on an SS20 - they all require 64-bit processors and the SS20 is 32-bit.

I am running NetBSD/sparc on a SparcStation 5 with 128M RAM and a 1G disk and it works really well. And it is the latest version of NetBSD. Makes a useful DNS server for my home network, but I don't think I'd want to compile anything on it. First time I ran SSH it took 5 minutes to generate the DSA key :biggrin:

---

