---
title: "How does one require authentication for remote CUPS printing?"
date: 2010-10-13
forum: Server Platforms
---

### Post by ocwo92 on 2010-10-13
I want to setup CUPS so that one can print from a remote location, that is, outside of the local area network.

CUPS on my server is currently setup to provide printer access on the LAN. However, when I check the "Allow printing from the Internet" option from the CUPS administration page (from the web front-end), it seems that anyone will be able to print to any printer without entering a password, since CUPS doesn't ask for a password.

What should I enter in cupsd.conf to require remote users to authenticate while allowing local users to print without authentication?

---

### Post by ocwo92 on 2010-10-29
> **ocwo92 said:**
> What should I enter in cupsd.conf to require remote users to authenticate while allowing local users to print without authentication?
My current cupsd.conf file works but doesn't require authorization. It contains the following section, among others, which I believe affects regular use such as browsing and printing:

```
<Location />
  Require valid-user
  Order allow,deny
  Allow all
</Location>
```
However, when I add an AuthType line as follows:

```
<Location />
  AuthType Basic
  Require valid-user
  Order allow,deny
  Allow all
</Location>
```
it causes my client machines to prompt me for a password when I connect to the server using System/Administration/Printing. However, that only opens a window with an error message stating that I'm "Not authorized", because "The password may be incorrect."

Setting the CUPS log level to debugging reveals that:

```
D [29/Oct/2010:17:11:11 +0200] cupsdAcceptClient: 19 from 192.168.2.103:631 (IPv4)
D [29/Oct/2010:17:11:11 +0200] cupsdReadClient: 19 OPTIONS * HTTP/1.1
D [29/Oct/2010:17:11:11 +0200] cupsdSetBusyState: Active clients
D [29/Oct/2010:17:11:11 +0200] cupsdAuthorize: No authentication data provided.
D [29/Oct/2010:17:11:11 +0200] Connection from 192.168.2.103 now encrypted.
D [29/Oct/2010:17:11:11 +0200] cupsdSetBusyState: Not busy
D [29/Oct/2010:17:11:11 +0200] cupsdReadClient: 19 POST / HTTP/1.1
D [29/Oct/2010:17:11:11 +0200] cupsdSetBusyState: Active clients
D [29/Oct/2010:17:11:11 +0200] cupsdAuthorize: No authentication data provided.
D [29/Oct/2010:17:11:11 +0200] cupsdIsAuthorized: username=""
D [29/Oct/2010:17:11:11 +0200] cupsdSendHeader: 19 WWW-Authenticate: Basic realm="CUPS"
D [29/Oct/2010:17:11:11 +0200] cupsdCloseClient: 19
```

which seems to indicate that my Ubuntu client doesn't even submit the username and password.

What am doing wrong in the cupsd.conf file, or possibly on the clients, that causes the CUPS authorization to fail?

---

### Post by ocwo92 on 2010-10-29
> **ocwo92 said:**
> which seems to indicate that my Ubuntu client doesn't even submit the username and password.
Actually, I missed a part of the log file which comes just before the quoted section:

```
D [29/Oct/2010:17:24:59 +0200] cupsdReadClient: 12 OPTIONS * HTTP/1.1
D [29/Oct/2010:17:24:59 +0200] cupsdSetBusyState: Active clients
D [29/Oct/2010:17:24:59 +0200] cupsdAuthorize: No authentication data provided.
D [29/Oct/2010:17:24:59 +0200] Connection from 192.168.2.103 now encrypted.
D [29/Oct/2010:17:24:59 +0200] cupsdSetBusyState: Not busy
D [29/Oct/2010:17:24:59 +0200] cupsdReadClient: 12 POST / HTTP/1.1
D [29/Oct/2010:17:24:59 +0200] cupsdSetBusyState: Active clients
D [29/Oct/2010:17:25:00 +0200] cupsdAuthorize: Authorized as wolf using Basic
D [29/Oct/2010:17:25:00 +0200] cupsdIsAuthorized: username="wolf"
D [29/Oct/2010:17:25:00 +0200] cupsdReadClient: 12 1.1 Get-Notifications 1
D [29/Oct/2010:17:25:00 +0200] Get-Notifications /
D [29/Oct/2010:17:25:00 +0200] Get-Notifications client-error-not-found: notify-subscription-id -1 no good!
D [29/Oct/2010:17:25:00 +0200] Returning IPP client-error-not-found for Get-Notifications (/) from 192.168.2.103
D [29/Oct/2010:17:25:00 +0200] cupsdSetBusyState: Not busy
D [29/Oct/2010:17:25:00 +0200] cupsdAcceptClient: 19 from 192.168.2.103:631 (IPv4)
D [29/Oct/2010:17:25:00 +0200] cupsdReadClient: 19 POST / HTTP/1.1
D [29/Oct/2010:17:25:00 +0200] cupsdSetBusyState: Active clients
D [29/Oct/2010:17:25:00 +0200] cupsdAuthorize: No authentication data provided.
D [29/Oct/2010:17:25:00 +0200] cupsdIsAuthorized: username=""
D [29/Oct/2010:17:25:00 +0200] cupsdCloseClient: 19
D [29/Oct/2010:17:25:00 +0200] cupsdSetBusyState: Not busy
```

This indicates that I'm in fact authenticated, but I'm getting the "Not authenticated" error nonetheless.

According to the [CUPS documentation](http://www.cups.org/documentation.php/spec-ipp.html), the "client-error-not-found for Get-Notifications" indicates that there's no job on the server. This is true, and probably isn't the reason I'm reported to not be authenticated.

Can someone help me out here?

---

### Post by ICEB3AR on 2010-10-29
Just a guess:

The man-page shows:
> 
Defines the access log filename. 
Allow all 
Allow none 
Allow host.domain.com 
Allow *.domain.com 
Allow ip-address 
Allow ip-address/netmask 
Allow ip-address/mm 
Allow @*IF(name)* 
Allow @LOCAL

Maybe Allow@IF(name) will bring the success. Or if it is possible (don't know if you have a static ip or a domain) just use the rule @LOCAL and for the remote users a ip-adress or domain.

---

### Post by ocwo92 on 2010-10-29
> **ICEB3AR said:**
> Maybe Allow@IF(name) will bring the success. Or if it is possible (don't know if you have a static ip or a domain) just use the rule @LOCAL and for the remote users a ip-adress or domain.

I thought of this, too, but the thing is, the computers that must be able to print are used for traveling and are logging on from various ISPs, so I can't know their IPs or domains.

It's an actual login I need, and I can't figure out whether I'm doing something wrong or if there's a bug somewhere.

---

### Post by Thirtysixway on 2010-10-29
To be encrypted abroad you could perhaps look at using VPN to print securely?

I've also had success printing remotely using ssh as a proxy into the print server :p

---

### Post by ocwo92 on 2010-10-30
> **Thirtysixway said:**
> To be encrypted abroad you could perhaps look at using VPN to print securely?
VPN might be an option, but since CUPS supports authorization, anything but CUPS authorization seems like an unnecessary workaround. I'm still in the dark as to what is wrong; I'm not even sure whether it might be a client bug in the System/Administration/Printer tool.

> I've also had success printing remotely using ssh as a proxy into the print server :p
I could do that, but I prefer not to try to explain to my girlfriend how to create ssh tunnels.

---

