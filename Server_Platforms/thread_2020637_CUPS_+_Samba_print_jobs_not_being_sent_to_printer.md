---
title: "CUPS + Samba print jobs not being sent to printer"
date: 2012-07-08
forum: Server Platforms
---

### Post by violinuxer on 2012-07-08
Hi all!

I have just barely encountered a problem with one of my servers. I recently upgraded from Lucid (oh the good old days :p) and decided to set up a print server using CUPS and samba (Printer model Canon PIXMA iP4000 via USB on the server) . I need to be able to service Windows machines, so I went through the process of getting the windows drivers and exporting them from cups into Samba. After dealing with all the usual troubles with getting Samba to work, all went well. I was able to print from windows fine and everything seemed to be working all right.

Fast forward a couple days: I now try to print from my Ubuntu  machine. The print job submits without much trouble, and then does absolutely nothing. I can let the job sit for 10 minutes- it won't do anything. Same happens with the windows machine. Inside the CUPS status page (on port 631, this happens even when I am just printing a test page from the interface) the print job is being "sent to the printer". I tried disconnecting and reconnecting the printer, now, the status page says that it is "Waiting for the printer to become available" which, of course, does not happen.

I dug in to the cups logs (with debug log level) and turned up the following lines which seem to be the root of the problem:

```
D [08/Jul/2012:15:39:56 -0400] [Job 7] STATE: +connecting-to-device
d [08/Jul/2012:15:39:56 -0400] cupsdSetPrinterReasons(p=0x21a51cd8(Canon_iP4000),s="+connecting-to-device"
d [08/Jul/2012:15:39:56 -0400] cupsdAddEvent(event=printer-state-changed, dest=0x21a51cd8(Canon_iP4000), job=(nil)(0), text="Printer "%s" state changed.", ...)
D [08/Jul/2012:15:39:56 -0400] Discarding unused printer-state-changed event...
d [08/Jul/2012:15:39:57 -0400] select_timeout(0): 86400 seconds to do nothing
D [08/Jul/2012:15:40:01 -0400] [Job 7] Failed to set configuration 1 for 04a9:1093
D [08/Jul/2012:15:40:01 -0400] [Job 7] Failed to claim interface 0 for 04a9:1093: No such file or directory

```The problem is that I have no idea what to do with this. Other posts on the net point to conflicts with cups 1.4 and usblp- this doesn't make much sense as I am up to date with packages. usblp isn't even in modprobe.conf

Other notes:

[LIST]
[*]The server is connected to the printer via 2 daisy-chained usb extension cables. Would this have to do with anything?
[*]The above log messages appear to repeat themselves infinitely
[*]Samba has errors in its log about not being able to read a printer list, but these appear to have happened before printing
[*]The server has a restrictive firewall that IS opened to Samba
[*]All lights on the printer are not blinking (it supposedly is working correctly)
[*]All files in /dev/bus/usb/ are owned by root. Does that seem to be correct? Other posts have pointed to issues here
[/LIST]
Thanks so much!


violinuxer

---

### Post by violinuxer on 2012-07-08
Hello again!

Something I forgot to add: when I reconnect the printer (after disconnecting it) i get the following error in syslog:
```

Jul  8 16:21:12 [341727.073048] usb 3-2: can't set config #1, error -110
```Any ideas?

Thanks!

violinuxer

---

### Post by drdos2006 on 2012-07-08
Check out this thread. It may help.

[http://ubuntuforums.org/showthread.php?t=1967725](http://ubuntuforums.org/showthread.php?t=1967725)

regards

---

### Post by violinuxer on 2012-07-08
> **drdos2006 said:**
> Check out this thread. It may help.

[http://ubuntuforums.org/showthread.php?t=1967725](http://ubuntuforums.org/showthread.php?t=1967725)

regards

Thanks for the link! I've posted there with a link back here. Hopefully my info will be enlightening to someone :)

violinuxer

---

### Post by drdos2006 on 2012-07-08
Here is another link that might help.
I removed 12.04 and went back to 10.4 to get printing to work, until this matter is resolved further.

[http://ubuntuforums.org/showthread.php?t=2008682](http://ubuntuforums.org/showthread.php?t=2008682)

regards

---

### Post by violinuxer on 2012-07-08
Hi there!

Just got this in my syslog:

```

[11068.503482] type=1400 audit(1341791562.935:23): apparmor="DENIED" operation="file_lock" parent=1 profile="/usr/sbin/cupsd" name="/run/samba/gencache.tdb" pid=706 comm="cupsd" requested_mask="k" denied_mask="k" fsuid=0 ouid=0
```

This is is on one of the ubuntu clients. Now AppArmor is getting involved :confused:

Thanks for all your help!

violinuxer

---

### Post by martinto on 2013-01-13
Edit [FONT="Courier New"]/etc/apparmor.d/usr.sbin.cupsd[/FONT]

Around line 173 is the samba stuff. Add this line:

[FONT="Courier New"]  /{,var/}run/samba/*.tdb rwk,[/FONT]

Save the file and run this command:

[FONT="Courier New"]sudo apparmor_parser -r /etc/apparmor.d/usr.sbin.cupsd[/FONT]

---

