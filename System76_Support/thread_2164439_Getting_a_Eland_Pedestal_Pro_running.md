---
title: "Getting a Eland Pedestal Pro running"
date: 2013-07-31
forum: System76 Support
---

### Post by FrankT-Qc on 2013-07-31
Hi,

(Sorry for my English...)

Being on a budget, buying a server is a big decision. I was interested
in System76's Eland Pedestal Pro, and it took me quite a while to push
the "Go" button, mainly because information is sparse and I'm a bit
far (Québec, Canada) should there be a problem. In the end, I'm very happy
with my choice. Here's my tale, in case someone else is in the same
decision process.

tldr :
* Pros : Great server/platform, good hardware selection and
  assembly. Almost the same pricing as assembling it myself. Next time
  I'm doing a tower server, this is what I'm buying.
* Cons : Provided management tools don't support Ubuntu. Everything
  needed is available with a bit of research. Read the rest for my
  wrap-up.

Here is an enumeration of the incertitude I've encountered and the
answers / solutions so far.

# Hardware

Here's what i got (June 2013)

* Server : Intel P4000CP
* RAID : LSI 9261-8i
* Lights-Out : RMM4 
* Software : Intel Remote Server Management Suite (for Red Hat or SuSE
  only), LSI Storage Manager (for Red Had or SuSE only)
* Seagate Constellation ES Drives
* A whack of spare parts, case fittings, SATA cables, mounting
  brackets, etc.

Hardware wise, this is a great great great box. I have ~ 20 servers
under my jurisdiction and this is by far the best build I play
with. System76 does not claim to have SAS support; this specific build
happen to have it but I would not take that for granted. Beside the
RAID controller, there is a whack of space for more drives on the MB,
make sure you read the specs.

Remote management (Intel RMM4) : 
* A dedicated Ethernet card, 
* A web page with the status of every sensors and a few buttons to
  power the server up/down and a remote console.
* Access to the IPMI interface even with the server down.
* The MB already has a BMC with similar functions, but the RMM4 works
  when the server is down; I think you don't get the console either
  through the MB. 
* Anyway, for the price, you want the separate management LAN and the
  IPMI while powered off.

The drives are Constellation ES, which I'm pretty happy with. They are
great drive for the OS and can standing a fairly heavy load (imho). I
personally find them too expensive for "big volume low traffic"
stuff. I got two of them from System76 then went and bought a few
cheaper (Constellation CS) drives on my own for that specific
load. Hot plugged them in. Just worked.

System76 did a pretty good assembly job. Upon reception, I took the
cover and wind tunnels off. The assembly is quite clean, the cabling
is nicely routed everything is stable and tidy. A nice note : I bought
only one CPU, but the cooling gear for the second one is in place,
waiting for a second CPU.

A note : They had cabled some drives to the motherboard and some to
the RAID controller. It happens that my specific usage is such that I
wanted all of them going to the RAID controller. This requires a
different cable that I did not have on hand. Before buying a cable, I
chatted with their tech support asking if there was a reason for this
particular configuration or if switching was OK. They replied that it
was just as fine and actually sent me the missing cable. Not that it's
something very expensive, but getting parts shipped to me for free on
a moment's notice without even asking for it gives me quite a good
feel about System76's service.

# Software compatibility.

This server runs flawless on stock Ubuntu; there is no closed source
or external driver needed. It came pre-installed, but I am peculiar on
my partitioning so I did a fresh install of Precise amd64 and
everything works right out of the box.

The management suites provided for the server are a different
story. Intel and LSI both limit their support to Windows, Red Hat and
SuSE. While everything is there for a Linux system, the architecture
difference between Ubuntu and, let's say Red Hat, make the
installation less straightforward.

On the software side of things, System76 had a little less experience
with the tools than I would have expected. On this one, I'm between
two positions. 

If your not comfortable with IT and you want a pre-chewed solution to
get your business running, then official management tools are not
easily (factory?) installed. This server might be a bit opaque to you.

On the other hand, if you are willing to dig in a bit, everything is
actually readily available and the only thing missing is a bit of
documentation. Since they ship with Ubuntu, Something System76 could
provide is a guide on getting your thing up and running. Until then,
well, there is this poorly written post. 

I'm too busy/lasy to do it myself, but maybe System76 could consider
repackaging the tools and create a repo, that would make this server
also suitable for not-IT people.

## Managing the RAID Controller.

* The RAID controller can be configured at boot, through the WebBIOS
  interface.
* On LSI Website, there is a tool called "storcli". It's distributed
  through a RPM that actually only contains one file; just decompress
  the RPM and put the executable somewhere useful, like
  "/usr/local/bin" or whatever. This will give you a cli to manage the
  controller at runtime.
* storcli is a replacement of the old "MegaCLI" tool, but "storcli -h"
  will get you going in no time. If you liked the old one, storcli
  actually supports the old syntax to so you could copy/link/rename
  storcli to megacli. This is actually easier than getting the
  original MegaCLI running (though still easy).
* MSM (MegaRAID Storage Manager) can be found on their
  website. "alien" is capable of converting the RPM archives to
  deb. You will get an error on the very first launch of the service,
  restart it, no more errors. One note : this requires a Java
  Runtime. I installed the same debs on my management station to
  manage the server remotely. In the end, I prefer storcli; it is
  quite easy and complete. If you prefer a GUI, there you have it.
* SNMP Agent : I did not even try; I monigor using nagios and go my
  fined tuned values out of storcli. The sensor alerts are also read
  by the server platform so they are available there too.
  
## Managing the server

* The web interface provided by the RMM4 gives you a good GUI before
  you even have an OS on.
* I did not get the Active System Console (a web application) going by
  just unpacking the RPMs. Since the RMM4 and the BMC both already
  offer most fonctionalities, I realised it was not actually
  useful. You would need to get it running for the "multi server
  management" capabilities though. For those who want it, It's
  basically a local service and a dedicated lighttpd install, so I
  suspect it would be easy to get running.
* I did not even try setting up the SNMP agent. Intel has a pretty
  clean IPMI interface that, imho, does a cleaner job. SNMP traps, can
  be configured through the RMM4, the BMC or through the IPMI
  interface (including traps for the RAID controller). I did fuss with
  the executables a bit, and got values out of it; the main job would
  be to rewrite a few startup scripts.
* For those who only heard about SNMP while configuring nagios, give a
  look to the check_ipmi plugin. One line configuration and, added
  bonus, the IPMI interface is available through the RMM4 even when
  the server is down.

# Shipping to Canada : 

The import was quite simple. I used UPS broker service and ended up
total (fee, tax) of 207$ tax. Word of advice though, do not
underestimate the border's fudge factor. Anyway, was fast, easy and
cheap for me. The border added about two extra days to delivery.

Feel free to contact me if you have questions / ideas !
Have fun,
François

---

### Post by isantop on 2013-07-31
Just a quick note: if you order an 8-port RAID card, you're supposed to get all of the cables for it preinstalled regardless of how many drives you chose to have installed. This particular case was a mistake, and if yours went out without the proper cables (like OP), you should contact us for a free cable.

---

