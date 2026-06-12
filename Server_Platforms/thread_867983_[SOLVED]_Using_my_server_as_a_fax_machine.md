---
title: "[SOLVED] Using my server as a fax machine"
date: 2008-07-23
forum: Server Platforms
---

### Post by Jordanwb on 2008-07-23
I can't believe that fax machines are still being used. I have a fax modem (although not in the server), and a laser printer connected to the network with a HP JetDirect card. Is there someway that my parents can print to a "virtual printer" on my server from Windows XP, are prompted for a phone number, and it's sent? Also is there someway to send incoming faxes to the printer mentioned?

---

### Post by windependence on 2008-07-23
[http://www.hylafax.org/content/Main_Page](http://www.hylafax.org/content/Main_Page)

-Tim

---

### Post by Jordanwb on 2008-07-23
Ok cool. But can I "print" to it from a Windows box?

---

### Post by songshu on 2008-07-23
hylafax is the server, it runs on the server and you basically do not see it, but there are a lot of clients you can use, both linux and windows, there is a list on the avantfax site.

personally i use avantfax, this is a very nice and simple friendly web based frontend.

instead of using a client on the server or desktop, you could even have it done by sending e-mail to and from the server.

---

### Post by Jordanwb on 2008-07-23
What I want my parents to be able to do is Hit File->Print in Word, select a fax printer, they're asked for the phone number, the file is sent to the server, much like cutePDF printer, and HylaFax faxes it. Is there (there probably is) that has that specific Client end feature? My parents aren't very Technologically inclined.

Doesn't Windows have a feature like that? I wonder if that would work?

---

### Post by songshu on 2008-07-23
> **Jordanwb said:**
> What I want my parents to be able to do is Hit File->Print in Word, select a fax printer, they're asked for the phone number, the file is sent to the server, much like cutePDF printer, and HylaFax faxes it. Is there (there probably is) that has that specific Client end feature? My parents aren't very Technologically inclined.

Doesn't Windows have a feature like that? I wonder if that would work?

there is a list on the avantfax site

---

### Post by Jordanwb on 2008-07-23
AvantFax seems to work only on Linux OS's. My parent's PC has Windows.

I found this: [http://www.hylafax.org/content/Desktop_Client_Software](http://www.hylafax.org/content/Desktop_Client_Software)

---

### Post by songshu on 2008-07-23
> **Jordanwb said:**
> AvantFax seems to work only on Linux OS's. My parent's PC has Windows.

it runs on the server as a website, you can use any browser on any platform to use it.

---

### Post by Jordanwb on 2008-07-23
I know HylaFax runs on a server. Next what I'm looking for is a Client where my parents can simply select a printer in Microsoft Word, are prompted for the number, and HylaFax faxes it.

I found this: [http://winprinthylafax.sourceforge.net/](http://winprinthylafax.sourceforge.net/) that seems drop dead simple enough. Do you know what other packages or stuff I'd need to install for my fax modem itself?

---

### Post by cariboo on 2008-07-23
Here is a link o exactly what you are looking for even though it is for suse:

[http://linuxgazette.net/issue79/fraile.html](http://linuxgazette.net/issue79/fraile.html)

Here is a howto for Debian which is closer to Ubuntu:

[http://www.aboutdebian.com/fax.htm](http://www.aboutdebian.com/fax.htm)

All the software is available for Ubuntu, but the versions are newer, except smbfax which is linked in the article.

Jim

---

