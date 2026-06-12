---
title: "Secure Calendar Server"
date: 2009-04-03
forum: Server Platforms
---

### Post by contax on 2009-04-03
I have two offices which are federally mandated to pass all electronic information via encrypted transmission.  Both offices are equipped with recent vintage Macs, which have wonderful non-secure push calendar sync via MobileMe.  Bottom line.. I can't use the iCal sync feature.  I have been searching for a calendar-SSH solution, or some other facility that will allow for a central secure calendar server and real time calendar syncing.

All other data is easily and securely synced via a central Ubuntu server.

 I would appreciate any pointers, or suggestions as to where I might looks for a solution.  Right now I've mastered the throw my hands up and pull my hair out solution.

Thanks in advance.

---

### Post by hyper_ch on 2009-04-03
I don't quite understand what the problem is...

but couldn't you do a mysql replication (if data is stored in mysql)?

---

### Post by michaelzap on 2009-04-03
One easy option which should comply with the federal mandate as you describe it would be just to set up a Google Apps for Domains account and use gCal. You can force SSL connections to it, and it has an integrated user access permissions system. gCal can be accessed using pretty much any calendar software on all platforms, or you could use the web interface.

You'd have to trust Google, of course...

---

### Post by contax on 2009-04-06
It sounds like the Google route may be my best bet.  I was hoping that Apple would upgrade to a secure version, but I don't know if that is possible with WebDav.

Thanks Everyone.

---

### Post by HermanAB on 2009-04-06
Citadel is a complete groupware server, is very easy to install (almost trivial) and it can do everything over SSL:
[http://www.citadel.org](http://www.citadel.org)
[http://aeronetworks.ca/citadel-howto.html](http://aeronetworks.ca/citadel-howto.html)
[http://aeronetworks.ca/citadel-clients.html](http://aeronetworks.ca/citadel-clients.html)

---

### Post by contax on 2009-11-08
Thanks for all the info.  I've had three different Ubuntu servers (hardware), each running various software servers, but have yet to setup the shared calendar feature.  I'm now about to open the second office and will either use the new Mac Mini Leopard Server, or another Ubuntu Server.  I'll go Google in desparation, but my calendaring function is so very critical that I'm rather nervous about putting it off to Google.  So, will go through all suggestions above.  Thanks...

---

### Post by michaelzap on 2009-11-08
gCal now has offline access via their web interface, also.

---

### Post by contax on 2009-11-09
Yes, I have a trial run with iCal (which runs on both iMac scheduling front end computers).  It seems rather easy to sync both calendars with Google under Snow Leopard.  This would free my server to perform other tasks, but is Google 100% reliable?  Do others use them for critical scheduling tasks.  If I lost my calendar information, my offices would be in chaos.  Well.. they are usually chaotic, but more so if calendars were down.

---

### Post by Lars Noodén on 2009-11-09
> **contax said:**
> It sounds like the Google route may be my best bet.  I was hoping that Apple would upgrade to a secure version, but I don't know if that is possible with WebDav.


You can run WebDAV through HTTPS.  

[http://httpd.apache.org/docs/2.2/mod/mod_dav.html](http://httpd.apache.org/docs/2.2/mod/mod_dav.html)
[http://linuxgazette.net/131/cressatti.html](http://linuxgazette.net/131/cressatti.html)

SSL/TLS has become a bit easier to deploy since the above tutorial

---

### Post by Lars Noodén on 2009-11-09
> **contax said:**
> ... I'm rather nervous about putting it off to Google. ...

You have more choices and it's possible to use just part of a larger groupware package.

[LIST]
[*]Darwin Calendar Server
   [http://trac.calendarserver.org/](http://trac.calendarserver.org/)

[*]Citadel (it's end to end GPLv3!)
[http://www.citadel.org/](http://www.citadel.org/)

[*]Kolab
[http://www.kolab.org/](http://www.kolab.org/)

[*]Bedework
[http://www.bedework.org/](http://www.bedework.org/)

[*]OpenGroupware
[http://www.opengroupware.org/en/about/](http://www.opengroupware.org/en/about/)

[*]Zimbra
[http://www.zimbra.com/](http://www.zimbra.com/)
[/LIST]

---

### Post by michaelzap on 2009-11-09
> **contax said:**
> Yes, I have a trial run with iCal (which runs on both iMac scheduling front end computers).  It seems rather easy to sync both calendars with Google under Snow Leopard.  This would free my server to perform other tasks, but is Google 100% reliable?  Do others use them for critical scheduling tasks.  If I lost my calendar information, my offices would be in chaos.  Well.. they are usually chaotic, but more so if calendars were down.

A lot of people that I know use Google for scheduling, but that doesn't mean that it never goes down. Everything goes down sometimes. Depending upon the software that you use to access Google Calendar, you could still access all existing events in the event that it went down.

I've used and liked other groupware software also, but I probably would trust it less than Google in terms of reliability.

The main reasons that I might use groupware software instead of Google would be if you didn't want to trust your data with them, which is a reasonable thing to be concerned about (but perhaps outweighed by practical considerations), or if you needed features that Google doesn't provide.

---

### Post by Thirtysixway on 2009-11-09
Are you looking for a calendar application, or something webbased?  I'm sure you can find plenty of calendar web apps that can use ssl simply by being on apache.

---

### Post by Haventfoundme on 2012-02-10
Citadel looks great

---

