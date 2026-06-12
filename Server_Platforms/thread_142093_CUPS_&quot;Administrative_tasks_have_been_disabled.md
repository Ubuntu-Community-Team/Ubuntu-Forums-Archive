---
title: "CUPS &quot;Administrative tasks have been disabled for security reasons&quot;"
date: 2006-03-09
forum: Server Platforms
---

### Post by angussf on 2006-03-09
Just repeated the 'SAMBA (Domain Controller) Server For Small Workgroups With Ubuntu 5.10 "Breezy Badger"' ([http://www.howtoforge.com/book/print/917](http://www.howtoforge.com/book/print/917)) for the second time, since the first time CUPS was just not behaving.  This time I followed the tutorial EXCEPT for the placement of "AuthGroupName" in cupsd.conf -- i put it inside the <Location /admin></Location> block instead of where the tutorial suggests it belongs.  

However, when I go to [http://ubuntuserver:631/admin](http://ubuntuserver:631/admin) (which the tutorial explains wrong - it says to go just to the [http://server:631/](http://server:631/)) I see this disconcerting message: > Administrative tasks have been disabled for security reasons. Please use Menu System > Administration > Printing. and none of the images are present (HTML of the page refers to IMG SRC="/images/navbar.gif", IMG SRC="/images/left.gif", IMG SRC="/images/right.gif", IMG SRC="/images/add-class.gif", IMG SRC="/images/manage-classes.gif", IMG SRC="/images/manage-jobs.gif", IMG SRC="/images/add-printer.gif", and IMG SRC="/images/manage-printers.gif", all of which **ARE** in the /usr/share/cups/doc-root/images/ directory). Is the CUPS install incomplete as done in the tutorial, or is there some other problem?  FWIW I see that .../doc-root/ is owned by root, not cupsys.

Could it be something related to the change from group 'lpadmin' to group 'shadow'?  cupsd.conf (see below) refers only to group 'lpadmin' while cupsys is a member of group 'shadow' as per the tutorial.

Also, I found this by googling:
[http://people.ubuntu.com/~scott/ongoing-merge/cupsys/cupsys_merged.debdiff](http://people.ubuntu.com/~scott/ongoing-merge/cupsys/cupsys_merged.debdiff)
> 
+    - ubuntu-nowebadmin: display a red warning on the web interface that
+      administrative functions are disabled for security reasons


This suggests to me that in CUPS 1.1.20 and later the web-admin pages have been disabled.  If this is true, how do we administer CUPS on server machines that don't have GNOME running?

FWIW here's my cupsd.conf, with verbose comments removed for brevity, but commented-out-but-still-default settings left in as reminders :
> 
########
######## Server Identity
########
#ServerName myhost.domain.com
#ServerAdmin [email]root@your.domain.com[/email]

########
######## Server Options
########
ConfigFilePerm 0600
#AccessLog /var/log/cups/access_log
#Classification classified
#Classification confidential
#Classification secret
#Classification topsecret
#Classification unclassified
#ClassifyOverride off
#DataDir /usr/share/cups
DefaultCharset notused
#DefaultLanguage en
#DocumentRoot /usr/share/cups/doc-root
#ErrorLog /var/log/cups/error_log
#FileDevice No
#FontPath /usr/share/cups/fonts
LogLevel info
#MaxLogSize 0
#PageLog /var/log/cups/page_log
#PreserveJobHistory Yes
#PreserveJobFiles No
#AutoPurgeJobs No
#MaxCopies 100
#MaxJobs 500
#MaxJobsPerPrinter 0
#MaxJobsPerUser 0
#MaxPrinterHistory 10
Printcap /var/run/cups/printcap
#PrintcapFormat BSD
#PrintcapFormat Solaris
#PrintcapGUI /usr/bin/glpoptions
#RequestRoot /var/spool/cups
#RemoteRoot remroot
#ServerBin /usr/lib/cups
#ServerRoot /etc/cups
#ServerTokens Minor

########
######## Fax Support
########
#FaxRetryLimit 5
#FaxRetryInterval 300

########
######## Encryption Support
########
#ServerCertificate /etc/cups/ssl/server.crt
#ServerKey /etc/cups/ssl/server.key

########
######## Filter Options
########
#User cupsys
#Group lpadmin
RunAsUser Yes
#RIPCache 8m
#TempDir /var/spool/cups/tmp
#FilterLimit 0

########
######## Network Options
########
Listen 127.0.0.1:631
Listen 10.69.2.35:631
#HostNameLookups On
#KeepAlive On
#KeepAliveTimeout 60
#MaxClients 100
#MaxClientsPerHost 0
#MaxRequestSize 0
#Timeout 300

########
######## Browsing Options
########
Include cupsd-browsing.conf
#BrowseProtocols cups
BrowseAddress @LOCAL
#BrowseShortNames Yes
#BrowseAllow address
#BrowseDeny address
#BrowseInterval 30
#BrowseOrder allow,deny
#BrowseOrder deny,allow
#BrowsePoll address:port
#BrowsePort 631
#BrowseRelay source-address destination-address
#BrowseRelay @IF(src) @IF(dst)
#BrowseTimeout 300
#ImplicitClasses On
#ImplicitAnyCLasses Off
#HideImplicitMembers On

########
######## Security Options
########
#SystemGroup lpadmin
#RootCertDuration 300
<Location />
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
</Location>
<Location /jobs>
AuthType Basic
AuthClass User
</Location>
<Location /admin>
AuthType Basic
AuthClass Group
AuthGroupName shadow
## Restrict access to local domain
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
Allow From 10.69.2.26
#Encryption Required
</Location>

#
#


---

