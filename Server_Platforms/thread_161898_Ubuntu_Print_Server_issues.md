---
title: "Ubuntu Print Server issues"
date: 2006-04-18
forum: Server Platforms
---

### Post by fredbear7232 on 2006-04-18
Well, I'm throwing this out there, and hopefully someone can at least point me in the right direction. I'm trying to configure my PSC 1210 as a raw printer, so I can print from XP machines. I do not have any form of GUI installed, and the server is headless.  I can get to Cups webadmin on the server by name and by IP, so I know cups is running for the most part. :)  I setup the printer in the webadmin as well. I can submit jobs, and as far as Cups shows me, it submits the job. I look at my printer, and nothing happens. No signs of life as far as any printer activity. Listed below is my cupsd.conf and printers.conf (that was built with the webadmin tool). I did set debug2 on my cupsd, and here is the excerpt of that error_log as well.. I did notice it gave a 404 file not found looking for my psc1210.ppd, but with a raw printer, is a ppd even required? Plus, when I get into the web admin, and click on configure printer, it gives me error client-error-not-possible. I can remove, readd.. anything else with the printer with no issues, just configure printer gives me that error. I wouldn't think it is a permissions issue, but maybe it is... Anyhow.. Here's the file's..

cupsd.conf:

AccessLog /var/log/cups/access_log
DataDir /usr/share/cups
DefaultCharset utf-8
DefaultLanguage en
ErrorLog /var/log/cups/error_log
MaxLogSize 10485760
LogLevel debug
Printcap /etc/printcap
RequestRoot /var/spool/cups
ServerBin /usr/lib/cups
ServerRoot /etc/cups
User lp
Group sys
Listen 127.0.0.1:631
Listen 192.168.1.10:631

<Location />
      Order Deny,Allow
      Deny From All
      Allow From 127.0.0.1
      Allow From 192.168.1.0/24
</Location>

<Location /admin>
      AuthType Basic
      AuthClass Group
      AuthGroupName dean
      Order Deny,Allow
      Deny From All
      Allow From 127.0.0.1
      Allow From 192.168.1.101
</Location>

Browsing Off
BrowseProtocols cups
BrowseOrder Deny,Allow
BrowseAllow from @LOCAL
BrowseAllow from @IF(eth0)


printers.conf:

# Printer configuration file for CUPS v1.1.23
# Written by cupsd on Mon 17 Apr 2006 08:18:23 AM EDT
<DefaultPrinter psc1210>
Info The Only Printer
Location Office
DeviceURI usb://Hewlett-Packard/psc%201200%20series?serial=MY342B831Z5H
State Idle
Accepting Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
</Printer>


Now as far as the deviceuri goes, it does show up as /dev/usb/lp0, and I'm assuming that hewlett packard mess points to that.. I even tried it utilizing the above (the dev path) and to no avail. 

Here's the chunk of the error_log too that I mentioned earlier about no ppd..

error_log:

D [17/Apr/2006:08:37:54 -0400] ProcessIPPRequest: 9 status_code=0
d [17/Apr/2006:08:37:54 -0400] ProcessIPPRequest: Adding fd 9 to OutputSet...
d [17/Apr/2006:08:37:54 -0400] WriteClient: Removing fd 9 from OutputSet...
d [17/Apr/2006:08:37:54 -0400] ReadClient: 9, used=0, file=-1
D [17/Apr/2006:08:37:54 -0400] ReadClient: 9 GET /printers/psc1210.ppd HTTP/1.1
d [17/Apr/2006:08:37:54 -0400] decode_auth(0xb79de870): Authorization string = $
d [17/Apr/2006:08:37:54 -0400] decode_auth: 9 username=""
d [17/Apr/2006:08:37:54 -0400] IsAuthorized: con->uri = "/printers/psc1210.ppd"
d [17/Apr/2006:08:37:54 -0400] FindBest: uri = "/printers/psc1210"...
d [17/Apr/2006:08:37:54 -0400] FindBest: Location / Limit 7f
d [17/Apr/2006:08:37:54 -0400] FindBest: Location /admin Limit 7f
d [17/Apr/2006:08:37:54 -0400] FindBest: Location CUPS_INTERNAL_BROWSE_ACL Limi$
d [17/Apr/2006:08:37:54 -0400] FindBest: best = "/"
d [17/Apr/2006:08:37:54 -0400] IsAuthorized: auth = 0, satisfy=0...
d [17/Apr/2006:08:37:54 -0400] get_file: 9 filename=/etc/cups/ppd/psc1210.ppd s$
D [17/Apr/2006:08:37:54 -0400] SendError: 9 code=404 (Not Found)
D [17/Apr/2006:08:37:54 -0400] CloseClient: 9
d [17/Apr/2006:08:37:54 -0400] CloseClient: Removing fd 9 from InputSet and Out$
d [17/Apr/2006:08:37:54 -0400] PID 11195 exited with no errors.
d [17/Apr/2006:08:37:54 -0400] DeleteCert: removing certificate for pid 11195
d [17/Apr/2006:08:37:54 -0400] ReadClient: 7, used=0, file=-1
d [17/Apr/2006:08:37:54 -0400] ReadClient: httpGets returned EOF...
D [17/Apr/2006:08:37:54 -0400] CloseClient: 7
d [17/Apr/2006:08:37:54 -0400] CloseClient: Removing fd 7 from InputSet and Out$
d [17/Apr/2006:08:37:54 -0400] WriteClient: Removing fd 5 from OutputSet...


Hopefully someone will have at least some insight into this.. Thanks in advance!!

---

### Post by fredbear7232 on 2006-04-18
Well.. I found my own insight to actually get it to print from the actual box itself.. FINALLY!!! :D  After racking my brain, and saying the hell with it and just installing the ppd for the printer itself, it worked. Here's what I loaded:

hplip-base
hplip-data
hplip-ppds   <-- to get the ppd for my PSC 1210
foomatic-db-engine <-- may not have needed, add anyhow just in case
foomatic-filters     <-- needs a filter for this printer out of here
foomatic-filters-ppds <-- just in case
gs-common  <-- doesn't install by default I guess.. needed gs
gs-esp
gs-gpl
hpijs <--- also gs calls this when it runs.. did not know that till now.. :) 

With all of those, plus the dependent .debs they require.. I was able to successfully print the test page.. I about dookied all over too.. :D  Been racking my brain for about a week on this thing.. But I'm only about halfway done.. the next thing is to get my windows machine to print to it.. <gulp> Will keep everyone informed..

---

