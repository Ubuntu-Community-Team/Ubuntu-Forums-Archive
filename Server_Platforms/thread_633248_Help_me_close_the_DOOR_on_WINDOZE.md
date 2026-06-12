---
title: "Help me close the DOOR on WINDOZE"
date: 2007-12-06
forum: Server Platforms
---

### Post by volkswagner on 2007-12-06
I am seeking advice on a whole house mythtv network setup.

What I would like:

Server connected to linksys router running myth-backend, LAMP server to serve my new website with shopping cart

One quite frontend for bedroom connected to 26" LCD 

One slave backend-frontend machine in family room

One office machine multi-boot or VM for xp, win2k, UBUNTU for various tasks including video editing, Auto-cad, office apps, etc.

two more wireless laptops (not much here)
Questions:[LIST=1]
[*]Can I reasonable secure the server forwarding x-sessions?
[*]Will the pent4 1.4 ghz, 1gig ram be adequet for 2-3 tuners, and LAMP?
[*]Since I am concerned with power usage shall I make the new pc act as server and master?
[*]How would you accomplish this?
[/LIST]

OK here is what I have:

New still building, Slave backend-frontend
[LIST]
[*]MOBO-GIGABYTE
GIGABYTE GA-MA69GM-S2H AM2
[*]CPU- AMD Athlon X2 BE-2400 Brisbane 2.3GHz 2
[*]PVR-350
[*]HD-250 gig SATA, 500 Gig SATA
[*]26" CRT TV via S-video out on MOBO
[/LIST]

Old pent4 Gateway upraded 1gig ram  (thinking server here) [http://support.gateway.com/s/MOTHERBD/INTEL/2510651/251065133.shtml]("http://support.gateway.com/s/MOTHERBD/INTEL/2510651/251065133.shtml")

Old Dell Dimension 4600 2gig Ram, Nvidia 6200 (quiet bedroom frontend)
[http://support.dell.com/support/edocs/systems/dim4600/en/4600/sm/specs.htm#1084976]("http://support.dell.com/support/edocs/systems/dim4600/en/4600/sm/specs.htm#1084976")        

HP M7470n running MCE 2005 performing DVR until mythbuntu network is stable then becomes office machine

Other machines avail:
        Old pent 4 1.6 ghz micro atx limited PCI slots 1gig ram Gateway 500se [http://support.gateway.com/support/srt/docs.asp?sn=0026885296]("http://support.gateway.com/support/srt/docs.asp?sn=0026885296")
       Really old pent 2 400mhz atx lots pci slots 384meg ram


Other tuners avail, PVR 150, Kworld 115, using ADS Technologies- MCE-3000-EF in windows probaly wont work in Linux

---

### Post by volkswagner on 2007-12-06
bump....

Can someone answer security issue?  Can I reasonably have a myth backend and keep customer info secure for a web site?  The website is new, no customer base, no SEO, so I am not ready for a paid hosting solution.  I see there are threads on the net to get mysql and php along with my current free hosting and paypal shopping cart. I just dont want to waste time setting that up If I can do it on my own server.

---

### Post by HermanAB on 2007-12-06
Yes, you can make any Linux system secure.  However, you may be trying to do too much on a single machine.  The issue is not just processor load, but ease of maintenance.

I would put any finance system on a separate machine, simply to prevent it from going down when working on something else.

Start by running Firestarter to configure iptables.

Cheers,

H.

---

