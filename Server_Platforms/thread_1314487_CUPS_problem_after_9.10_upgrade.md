---
title: "CUPS problem after 9.10 upgrade"
date: 2009-11-04
forum: Server Platforms
---

### Post by danooch13 on 2009-11-04
Hello,

I am having a few problems with my CUPS ubuntu 9.10 print server.  Firstly, it was working fine all along with 9.04, but then cups was upgraded in 9.10 to 1.4.1 which is when my issues started.

What happens now, if I try to print a test page from the cups web interface to my networked printer, it just sits there forever processing and never prints.

In the error log, all I see are these errors!

```

E [04/Nov/2009:12:21:50 -0500] cupsdAuthorize: Empty Basic password!
E [04/Nov/2009:12:23:09 -0500] SSL shutdown failed: Error in the push function.
E [04/Nov/2009:12:23:19 -0500] SSL shutdown failed: Error in the push function.
E [04/Nov/2009:12:25:22 -0500] SSL shutdown failed: Error in the push function.
E [04/Nov/2009:12:25:22 -0500] SSL shutdown failed: Error in the push function.
E [04/Nov/2009:12:25:22 -0500] SSL shutdown failed: Error in the push function.
E [04/Nov/2009:12:25:22 -0500] SSL shutdown failed: Error in the push function.
E [04/Nov/2009:12:25:22 -0500] SSL shutdown failed: Error in the push function.
E [04/Nov/2009:12:25:29 -0500] SSL shutdown failed: Error in the push function.
E [04/Nov/2009:12:26:42 -0500] SSL shutdown failed: Error in the push function.
E [04/Nov/2009:12:27:02 -0500] SSL shutdown failed: Error in the push function.
E [04/Nov/2009:12:27:38 -0500] SSL shutdown failed: Error in the push function.
E [04/Nov/2009:12:27:38 -0500] SSL shutdown failed: Error in the push function.
E [04/Nov/2009:12:27:38 -0500] SSL shutdown failed: Error in the push function.
E [04/Nov/2009:12:27:38 -0500] SSL shutdown failed: Error in the push function.
E [04/Nov/2009:12:27:38 -0500] SSL shutdown failed: Error in the push function.
E [04/Nov/2009:12:27:46 -0500] SSL shutdown failed: Error in the push function.
E [04/Nov/2009:12:28:34 -0500] cupsdAuthorize: Empty Basic password!
E [04/Nov/2009:12:29:38 -0500] SSL shutdown failed: Error in the push function.
E [04/Nov/2009:12:30:03 -0500] SSL shutdown failed: Error in the push function.
E [04/Nov/2009:12:32:11 -0500] SSL shutdown failed: Error in the push function.
E [04/Nov/2009:12:32:36 -0500] SSL shutdown failed: Error in the push function.
E [04/Nov/2009:12:35:37 -0500] SSL shutdown failed: Error in the push function.
E [04/Nov/2009:12:35:37 -0500] SSL shutdown failed: Error in the push function.
E [04/Nov/2009:12:35:37 -0500] SSL shutdown failed: Error in the push function.
E [04/Nov/2009:12:35:37 -0500] SSL shutdown failed: Error in the push function.
E [04/Nov/2009:12:36:02 -0500] SSL shutdown failed: Error in the push function.
E [04/Nov/2009:12:37:06 -0500] SSL shutdown failed: Error in the push function.
E [04/Nov/2009:12:37:06 -0500] SSL shutdown failed: Error in the push function.
E [04/Nov/2009:12:37:06 -0500] SSL shutdown failed: Error in the push function.
E [04/Nov/2009:12:37:06 -0500] SSL shutdown failed: Error in the push function.
E [04/Nov/2009:12:37:06 -0500] SSL shutdown failed: Error in the push function.
E [04/Nov/2009:12:37:14 -0500] SSL shutdown failed: Error in the push function.
E [04/Nov/2009:12:39:34 -0500] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
E [04/Nov/2009:12:40:45 -0500] Unable to encrypt connection from 10.50.1.7 - A TLS fatal alert has been received.
E [04/Nov/2009:12:41:14 -0500] SSL shutdown failed: Error in the push function.
E [04/Nov/2009:13:59:52 -0500] SSL shutdown failed: Error in the push function.
E [04/Nov/2009:14:01:47 -0500] SSL shutdown failed: Error in the push function.
E [04/Nov/2009:14:01:47 -0500] SSL shutdown failed: Error in the push function.
E [04/Nov/2009:14:01:48 -0500] cupsdAuthorize: pam_acct_mgmt() returned 7 (Authentication failure)!
W [04/Nov/2009:14:01:48 -0500] Too many open files, holding new connections for 30 seconds...
E [04/Nov/2009:14:01:48 -0500] Unable to accept client connection - Too many open files.
E [04/Nov/2009:14:01:48 -0500] cupsdAuthorize: pam_start() returned 26 (Critical error - immediate abort)!
E [04/Nov/2009:14:01:48 -0500] cupsdAuthorize: pam_start() returned 26 (Critical error - immediate abort)!
E [04/Nov/2009:14:01:48 -0500] cupsdAuthorize: pam_start() returned 26 (Critical error - immediate abort)!
E [04/Nov/2009:14:01:48 -0500] cupsdAuthorize: pam_start() returned 26 (Critical error - immediate abort)!
E [04/Nov/2009:14:01:55 -0500] cupsdAuthorize: pam_start() returned 26 (Critical error - immediate abort)!
E [04/Nov/2009:14:01:55 -0500] [CGI] Unable to create pipe for /usr/lib/cups/cgi-bin/admin.cgi - Too many open files
E [04/Nov/2009:14:01:56 -0500] cupsdAuthorize: pam_start() returned 26 (Critical error - immediate abort)!
E [04/Nov/2009:14:01:56 -0500] [CGI] Unable to create pipe for /usr/lib/cups/cgi-bin/admin.cgi - Too many open files
W [04/Nov/2009:14:02:18 -0500] Too many open files, holding new connections for 30 seconds...
E [04/Nov/2009:14:02:18 -0500] Unable to accept client connection - Too many open files.
E [04/Nov/2009:14:02:18 -0500] Unable to encrypt connection from 10.50.1.7 - Could not negotiate a supported cipher suite.
W [04/Nov/2009:14:02:48 -0500] Too many open files, holding new connections for 30 seconds...
E [04/Nov/2009:14:02:48 -0500] Unable to accept client connection - Too many open files.
E [04/Nov/2009:14:02:48 -0500] Unable to encrypt connection from 10.50.1.7 - Could not negotiate a supported cipher suite.
W [04/Nov/2009:14:03:18 -0500] Too many open files, holding new connections for 30 seconds...
E [04/Nov/2009:14:03:18 -0500] Unable to accept client connection - Too many open files.
E [04/Nov/2009:14:03:18 -0500] Unable to encrypt connection from 10.50.1.7 - Could not negotiate a supported cipher suite.
W [04/Nov/2009:14:03:29 -0500] Too many open files, holding new connections for 30 seconds...
E [04/Nov/2009:14:03:34 -0500] Unable to remove temporary file "/var/spool/cups/tmp/.fontconfig" - Is a directory
E [04/Nov/2009:14:03:34 -0500] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
W [04/Nov/2009:14:03:18 -0500] Too many open files, holding new connections for 30 seconds...
E [04/Nov/2009:14:03:18 -0500] Unable to accept client connection - Too many open files.
E [04/Nov/2009:14:03:18 -0500] Unable to encrypt connection from 10.50.1.7 - Could not negotiate a supported cipher suite.
W [04/Nov/2009:14:03:29 -0500] Too many open files, holding new connections for 30 seconds...
E [04/Nov/2009:14:03:34 -0500] Unable to remove temporary file "/var/spool/cups/tmp/.fontconfig" - Is a directory
E [04/Nov/2009:14:03:34 -0500] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
E [04/Nov/2009:14:26:10 -0500] Unable to remove temporary file "/var/spool/cups/tmp/.fontconfig" - Is a directory
E [04/Nov/2009:14:26:10 -0500] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
E [04/Nov/2009:14:26:28 -0500] Unable to encrypt connection from 10.50.1.7 - A TLS packet with unexpected length was received.
E [04/Nov/2009:14:26:28 -0500] SSL shutdown failed: Error in the push function.
E [04/Nov/2009:14:26:28 -0500] Unable to encrypt connection from 10.50.1.7 - A TLS packet with unexpected length was received.
E [04/Nov/2009:14:27:13 -0500] Unable to remove temporary file "/var/spool/cups/tmp/.fontconfig" - Is a directory
E [04/Nov/2009:14:27:13 -0500] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory

```

Please help me...this upgrade has caused so much havoc on my servers!

---

### Post by danooch13 on 2009-11-04
I have a feeling it is the URI in the printers.conf look at it!

```
DeviceURI dnssd://Photosmart%208400%20series%20(D29CFB)._pdl-datastream._tcp.local/
```

It would make sense why it never connects to the printer.  Why would 9.10 do this?

What is it supposed to be?

```

#
#
# Sample configuration file for the CUPS scheduler.  See "man cupsd.conf" for a
# complete description of this file.
#

# Log general information in error_log - change "warn" to "debug"
# for troubleshooting...
LogLevel warn

# Deactivate CUPS' internal logrotating, as we provide a better one, especially
# LogLevel debug2 gets usable now
MaxLogSize 0

# Administrator user group...
SystemGroup lpadmin


# Only listen for connections from the local machine.
Listen 631
Listen /var/run/cups/cups.sock

# Show shared printers on the local network.
Browsing On
BrowseOrder allow,deny
BrowseAllow all
BrowseAddress @LOCAL
#BrowseLocalProtocols CUPS dnssd

#Added by AP for 426 Upgrade Required error 11/4/09
DefaultEncryption Never

# Default authentication type, when authentication is required...
DefaultAuthType Basic


```

---

### Post by danooch13 on 2009-11-04
Now I used hp-makeuri to make the uri, and I pasted it into the Device URI string in printers.conf.

When I try to print a test page, I get this now

```
/usr/lib/cups/backend/hp failed
```

---

### Post by danooch13 on 2009-11-04
Please close this.  It was my dumb a** brothers fault.  He had the photo tray engaged and I was not home to see it.  That is why nothing was printing.

All of those errors were caused by me futzing around...

Sorry

---

### Post by Neva on 2010-10-08
I had a somewhat similar problem on Ubuntu 10.04.

In my case, I could not see the printer listed on lsusb

Error -71 was typical.

Tried various fixes, they didn't help:
Step 7 here - [http://hplipopensource.com/hplip-web/install/manual/distros/ubuntu.html](http://hplipopensource.com/hplip-web/install/manual/distros/ubuntu.html)
```
sudo usermod -a -G lp $USER
```Hotfix here - [http://www.novell.com/support/search.do?cmd=displayKC&docType=kc&externalId=7002864&sliceId=1&docTypeID=DT_TID_1_1](http://www.novell.com/support/search.do?cmd=displayKC&docType=kc&externalId=7002864&sliceId=1&docTypeID=DT_TID_1_1)
```
echo -1 > /sys/module/usbcore/parameters/autosuspend
```Then tried the fix in this thread:
[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9790032](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9790032)

Which is to shut down the computer completely, turn off the power supply for 30mins.

That worked and lsusb shows the printer again.

---

### Post by shrimpy89 on 2011-02-22
I was griefed by "/usr/lib/cups/backend/hp failed" for a long time in Lucid and Maverick.  I solved it by installing gs-esp

```
sudo apt-get install gs-esp
```


I found the fix on Debian's forums.  It may be an easy solution for those searching.

---

