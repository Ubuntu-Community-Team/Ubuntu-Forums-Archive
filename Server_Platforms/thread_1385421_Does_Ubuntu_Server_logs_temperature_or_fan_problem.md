---
title: "Does Ubuntu Server logs temperature or fan problems at log?"
date: 2010-01-19
forum: Server Platforms
---

### Post by jocampo on 2010-01-19
Hi

My $50 bucks ebay/cheap server crashed :-) and I believe has something to do with CPU fan or power supply but would like to confirm before spending money in replacements. Does Ubuntu save such information at default logs, like faulty fan or abnormal temperature? If does, which log and which words should I check. I took a quick look and was not able to find anything but maybe I'm looking in the wrong log. 

My "marvelous" machine is a Dell™ OptiPlex™ GX270.

Thanks,

---

### Post by softclean on 2010-01-19
Hi there, try to see:
/var/log/kern.log

and see it contents.

It was just one time, or it crashes after some kind of event (starting a program, ...) ?

---

### Post by tgalati4 on 2010-01-21
Power supplies were problematic on Dell business machines.  Do a search on your model and you will probably find lots of failure modes.  Cheap capacitors or mosfets usually fail just beyond the warranty period.

Hardware failures often don't show up in the software logs unless you are running a special monitoring daemon.

For Dell servers (e.g. poweredge) I'm running OMSA--Dell's openmanage server administration.  It has been ported from Red Hat to Debian and seems to work OK on Ubuntu Hardy Server.  You get messages such as:

	Tue Mar 16 16:37:00 2004		Log cleared
Status: Critical		Tue Apr 6 09:47:39 2004		Cover Intrusion sensor detected an intrusion
Status: OK		Tue Apr 6 09:47:45 2004		Cover Intrusion sensor return to normal
Status: Non-Critical		Thu Apr 17 14:38:07 2008		ECC Single Bit Fault detected - Bank 2, DIMM A
Status: Non-Critical		Thu Apr 17 14:38:07 2008		ECC Single Bit Fault detected - Bank 2, DIMM A
Status: Non-Critical		Mon Jan 4 19:46:27 2010		Ambient temperature sensor detected a warning (10.0 C)
Status: Critical		System Boot		CPU 1 processor sensor CPU missing
Status: Critical		System Boot		CPU 1 processor sensor CPU missing
Status: Critical		System Boot		CPU 1 processor sensor CPU missing
Status: Critical		System Boot		CPU 1 processor sensor CPU missing
Status: OK		Mon Jan 4 19:46:36 2010		Ambient temperature sensor returned to normal (11.0 C)
Status: Non-Critical		Mon Jan 4 19:47:05 2010		Ambient temperature sensor detected a warning (10.0 C)
Status: OK		Mon Jan 4 19:50:02 2010		Ambient temperature sensor returned to normal (11.0 C)
Status: Non-Critical		Mon Jan 4 19:50:31 2010		Ambient temperature sensor detected a warning (10.0 C)
Status: OK		Mon Jan 4 19:50:49 2010		Ambient temperature sensor returned to normal (11.0 C)
Status: Non-Critical		Mon Jan 4 19:50:59 2010		Ambient temperature sensor detected a warning (10.0 C)
Status: Non-Critical		Mon Jan 4 20:40:08 2010		BP Bottom Temp temperature sensor detected a warning (9.0 C)
Status: OK		Tue Jan 5 08:55:50 2010		Ambient temperature sensor returned to normal (11.0 C)
Status: Non-Critical		Tue Jan 5 08:56:09 2010		Ambient temperature sensor detected a warning (10.0 C)
Status: OK		Tue Jan 5 08:56:18 2010		Ambient temperature sensor returned to normal (11.0 C)
Status: OK		Tue Jan 5 16:40:40 2010		CPU Planar temperature sensor returned to normal (11.0 C)
Status: Non-Critical		System Boot		BP Bottom Temp temperature sensor detected a warning (9.0 C)
Status: Non-Critical		System Boot		Ambient temperature sensor detected a warning (9.0 C)
Status: Non-Critical		System Boot		CPU Planar temperature sensor detected a warning (7.0 C)

You can try running it on an Optiplex, but omsa gathers data from on-board server monitoring hardware.  This is data that is stored in the monitoring BIOS.  You can drill down through all of the hardware from a secure webpage and see what is going on.  With 7 fans in a poweredge, if one is out of range, you will know about it.

For a desktop, lm-sensors, hddtemp, smartmontools and probably others can all be set to log data at intervals.  Gnome desktop has a monitoring applet that also logs data and sends emails/alerts when values are out of bounds.

If you really want to get serious about running a server, look for a used poweredge.  There are lots of them around in tower and rack configurations.

---

