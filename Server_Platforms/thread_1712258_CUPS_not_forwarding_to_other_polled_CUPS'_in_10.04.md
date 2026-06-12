---
title: "CUPS not forwarding to other polled CUPS' in 10.04"
date: 2011-03-22
forum: Server Platforms
---

### Post by fdelin on 2011-03-22
Hello all,

I've been trying to figure this out for longer than I care to admit.  We upgraded our print server (sysadmin) to 64 bit lucid and that moved our cups server from 1.3.7 to 1.4.3.  We have a remote server that is still 1.3.7 (printhost1) but version difference doesn't seem to be relevant to the problem.

If I'm on console on sysadmin and do an lpr to a printer on printhost1, everything is copacetic.  However, If I'm on a host that specifies "ServerName sysadmin" in its "/etc/cups/client.conf" access_log on sysadmin shows:

172.16.10.52 - - [22/Mar/2011:11:11:40 -0500] "POST /printers/103_hp4250 HTTP/1.1" 200 306 Create-Job client-error-not-authorized

and error_log shows:
E [22/Mar/2011:11:11:40 -0500] Returning IPP client-error-not-authorized for Create-Job (ipp://localhost:631/printers/103_hp4250) from 172.16.10.52

We've been using this method of sharing printers between locations for years and years so it not working now is a surprise.

cupsd.conf on sysadmin looks like this and is as open as I can imagine:

ServerName sysadmin
ServerAlias *
ServerAdmin webmaster
FileDevice Yes
SystemGroup staff
LogLevel info
MaxLogSize 0
SystemGroup lpadmin
# Allow remote access
Port 631
# Show shared printers on the local network.
Browsing On
BrowseOrder allow,deny
BrowseAllow all
BrowseRemoteProtocols CUPS
BrowseLocalProtocols
BrowseInterval 1800
BrowsePoll printhost1:631
BrowseTimeout 864000
DefaultAuthType Basic
<Location />
  # Allow remote administration...
  Order allow,deny
  Allow all
</Location>
<Location /admin>
  # Allow remote administration...
  Order allow,deny
  Allow all
</Location>
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  # Allow remote access to the configuration files...
  Order allow,deny
  Allow all
</Location>
<Policy default>
  <Limit All>
    Order allow,deny
    Allow *
    Allow from all
  </Limit>
</Policy>

Additional symptoms are that only printers locally defined on sysadmin show up when the client uses System>Administration>Printing in gnome.  Same thing when you browse printers in windows on our samba domain controller that backends on CUPS.

I just know that it's something simple that's going to make me facepalm but I'm at a loss.

Thanks,

Frank

---

### Post by fdelin on 2011-03-22
OK, other info, if I configure client.conf on the CUPS server to say "Servername sysadmin" instead of "Servername localhost" the local lpq/lpr doesn't work either.

---

### Post by fdelin on 2011-03-22
OK, If I http to [http://sysadmin:631/printers/103_hp4250](http://sysadmin:631/printers/103_hp4250) rather than try to send a print job it opens a page but the options are:
**(Idle, Accepting Jobs, Not Shared, Server Default)**

Any changes I try to make are applied on the remote CUPS server listed as

Connection:ipp://printhost1:631/printers/103_hp4250

I think I'm getting closer.

---

### Post by fdelin on 2011-03-23
No further progress, the only thing I notice other thatn that is it doesn't seem to be getting defaults either:

Defaults:job-sheets={job_sheets_default} media=unknown

remote.cache is missing the Sharing Yes

---

### Post by fdelin on 2011-03-23
Looking at the patch for 1.4 located at:

[http://www.cups.org/strfiles/2233/str2233.patch](http://www.cups.org/strfiles/2233/str2233.patch)

and noticing:

 [23/Mar/2011:09:51:48 -0500] [CGI] server_is_sharing_printers[0]="1"

on debug2 in error_log

---

### Post by fdelin on 2011-03-23
you got me, I went into the ./scheduler/printers.c for 1.4.6 and forced true on line 727:

ippAddBoolean(CommonData, IPP_TAG_PRINTER, "server-is-sharing-printers", 1);

compiled, installed on two systems to test, installed a new printer on server 1 where it shows shared and on server 2 it shows not shared.

---

### Post by fdelin on 2011-03-23
From: Michael Sweet
Date: 13:37 Wed
 
On Mar 23, 2011, at 1:28 PM, frank delin wrote:
> Is this still the case for 1.4.6?

Yes, it is still the case.=20

> If so then why CUPS_SERVER_SHARE_PRINTERS and =
ippAddBoolean(CommonData, IPP_TAG_PRINTER, "server-is-sharing-printers"

cupsd only shared local print queues. Sharing only refers to sharable =
queues. Remote queues are not sharable.

---

