---
title: "GoDaddy CNAME &amp; DynDNS &amp; FTP Solution"
date: 2011-08-14
forum: Server Platforms
---

### Post by DJCam on 2011-08-14
Figured I would share with the rest of the class something that took me hours upon hours to figure out the hard way (after doing due diligent searching with no answer).

This will work with vsftpd, proftpd, and all the other FTP's you can think of because the answer has nothing to do with the FTP it's GoDaddy's settings.

**PROBLEM**: When using GoDaddy (DNS) & DynDNS (HTTP + FTP) along with WebMin (or manual configs) and ProFTPD or vsftpd your forwarded domain will always resolve to secureserver.net when trying to login to your FTP from YourDomain.tld.  HTTP will work no problem but FTP for some reason fails.  FTP will work fine on localhost, direct IP, and DynDNS, but not your TLD hosted at GoDaddy.

**EXAMPLE:**
GoDaddy Domain Name: YourDomain.tld
[I]CNAME: www - yourname.dyndns-at-home.com
CNAME: ftp - yourname.dyndns-at-home.com[/I]
DynDNS Domain Name: yourname.dyndns-at-home.com

*FTP Login Success From: *
127.0.0.1
localhost
internal server ip (192.168.100.100)
external ip address (74.125.93.147)
yourname.dyndns-at-home.com (74.125.93.147)

*FTP Login Failure From: *
YourDomain.tld

**SOLUTION**: After creating a CNAME record for ftp to yourname.dyndns-at-home.com within GoDaddy's DNS manager simply login using ftp.yourdomain.tld NOT yourdomain.tld.  When you setup a CNAME it becomes ftp.yourdomain.tld so that's the url you have to login at.

Took me quite a few hours of trying to figure out why ftp login attempts were getting stopped at godaddy's (secureserver.net) dns. It wasn't vs or proftpd, wasn't dyndns dropping the ball either. It wasn't being forwarded properly because I wasn't using the CNAME correctly to login.  It was hopeful thinking that http & ftp would be split by Ubuntu Server to the appropriate ports.  It doesn't work like that.  If you use 2 of GoDaddy's CNAME records to point to the same DynDNS url the HTTP protocol will override everything else (on their side). Needless to say I have a much better understanding of how CNAME records really work.  You can't stack them and expect Ubuntu to split them with listening ports.  They are split before they leave GoDaddy.

I thought it was vsftpd screwing it up so I uninstalled it and went with proftpd.  Come to find out of course that wasn't the case and I removed vsftpd for nothing.  On the other hand I believe proftpd to be a much better solution than vsftpd so I'm not going back. If you have your LAMP server fully functional and configured correctly but can't login from FTP and meet all the other criteria for this issue well voila there's how it's done.

Hope that helps a lot of people get on their feet in making their DynDNS home servers (HTTP & FTP) a reality.  Toodles.

---

