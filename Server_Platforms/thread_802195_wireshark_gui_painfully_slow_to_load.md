---
title: "wireshark gui painfully slow to load"
date: 2008-05-21
forum: Server Platforms
---

### Post by trmentry on 2008-05-21
Hello,

I'm in the process of install multiple servers as VMs in our network to act as sniffers in our remote offices.  I used server as I wanted to make these LAMPs possiblly in the future.

Anyway.. I installed i386 hardy server.  Then installed xubuntu-desktop to get a gui enviroment.  Xubuntu seemed to work the best on getting xdmcp connections to work with multiple users conencting.

I then installed wireshark and tshark.

When I logon the box via gui (console or xdmcp) and run wireshark... it takes a very long time (45 min so far) to load wireshark.

Its at the window that says "Registering Dissector..." and all the little modules it loads.  So far 45 min since I started it, its at 35%.  

I'm not overly worried about this as I prefer the command line and will just ssh to the box normally.  But some of my techs aren't so keen on that and like the warm fuzzy gui.  

Any ideas why this is acting this way?  I can't find anythign wrong.

The VM is on ESX 2.5 with 1CPU 512MB.  

Thanks

---

### Post by windependence on 2008-05-21
> **trmentry said:**
> Hello,

I'm in the process of install multiple servers as VMs in our network to act as sniffers in our remote offices.  I used server as I wanted to make these LAMPs possiblly in the future.

Anyway.. I installed i386 hardy server.  Then installed xubuntu-desktop to get a gui enviroment.  Xubuntu seemed to work the best on getting xdmcp connections to work with multiple users conencting.

I then installed wireshark and tshark.

When I logon the box via gui (console or xdmcp) and run wireshark... it takes a very long time (45 min so far) to load wireshark.

Its at the window that says "Registering Dissector..." and all the little modules it loads.  So far 45 min since I started it, its at 35%.  

I'm not overly worried about this as I prefer the command line and will just ssh to the box normally.  But some of my techs aren't so keen on that and like the warm fuzzy gui.  

Any ideas why this is acting this way?  I can't find anythign wrong.

The VM is on ESX 2.5 with 1CPU 512MB.  

Thanks

Correct me if I'm wrong but I think wireshark has a web interface. that might load faster.

Your Vmware is also starving for RAM. You should be running like 2 gigs on that box. One downside to VMware, as much as I love it is it's RAM hungry.

-Tim

---

### Post by trmentry on 2008-05-21
> **windependence said:**
> Correct me if I'm wrong but I think wireshark has a web interface. that might load faster.

Your Vmware is also starving for RAM. You should be running like 2 gigs on that box. One downside to VMware, as much as I love it is it's RAM hungry.

-Tim


The box physically has lots o' ram... the 512 is what I gave to the VM.

Wireshark has a web interface?  /me heads over to Wireshark to research.

---

### Post by trmentry on 2008-05-21
Ok... I've been messing around with this and it appears to be an xdmcp thing.  When I thought I was testing the console, I wasn't paying attention to my windows.  *cough*

Anyway... console it works flawlessly and is very zippy.


When remoted in with xming and then running wireshark its takes a very long time to load.  I gave up after an hour and only like 40%.

---

