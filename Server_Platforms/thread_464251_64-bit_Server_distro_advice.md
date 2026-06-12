---
title: "64-bit Server distro advice"
date: 2007-06-04
forum: Server Platforms
---

### Post by ericdegen on 2007-06-04
Good day all!

I'm in need of a recommendation. I'm building a Linux based VMware server for hosting multiple windows servers. I have selected my HW.  An intel 975 based quad core box with 8 Gig of RAM and a SATA based raid.

I would like to run a GUI 64 Bit distro that I can use 64 bit VM with. I really like Ubuntu on the desktop, but have yet to try it as a server.  There is of course debian, which I would be happy to try or the old standard Fedora/Red Hat, which historically has made a good server platform.

I'm open to any others, but I have the most familiarity with these.  Also, I have never installed any 64 bit Linux so any pointers would be great.

Thanks,

---

### Post by lwh on 2007-06-05
Use Ubuntu LST or Debian 4.0

I have a 64bit Intel server based on the SE7520DB2 mother board running as a "vmware-host" using Dapper
The server have been running the last 12 months with not problems beside those I created myself.
Currently is the server hosting 8 vmware guest, which is a mix between w2k3 servers and debian/ubuntu server installations. ;)
 
If it was real server hardware you neede to install on there might be some advances in opensuse/ SLED, to have hardware driver support from the manufactor.

By the way make sure that vmware is supporting 64 bit guest systems on your _CPU_, my two Xeon 64bit is not supported, too "old" version of the 64bit CPU. :(

---

### Post by ericdegen on 2007-06-05
Thanks lwh,

That is exactly the kind of info I'm looking for!  Think I will be ok on the CPU front (a new Q6600) but I'll verify.  I'm still assembling the physical server, so I have some time yet till I load the OS, anyone who would recommend something other then Ubuntu/Deb and to chime in?  

I'm doing this all on newer HW and nothing exotic (3rd party RAID, etc.) so the need for SLED I'm just not seeing.

---

