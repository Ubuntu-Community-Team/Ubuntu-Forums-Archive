---
title: "Vista says  printer &quot;access denied unable to connect&quot;"
date: 2009-07-20
forum: Server Platforms
---

### Post by kpictjl on 2009-07-20
I have an Ubuntu 9.04 server using CUPS and SAMBA to shared a printer across my home LAN.  I can print to the printer fine from my MS Vista laptop.  However, the Vista Printers tools says "access denied, unable to connect."  

How do I stop that message from coming up?  Do I need to open up some permissions in cups or samba or something?

Thank you.

---

### Post by swerdna on 2009-07-21
Add this line to the [global] stanza of smb.conf and see if it goes away:```
use client driver = yes
```

---

### Post by kpictjl on 2009-07-21
> **swerdna said:**
> Add this line to the [global] stanza of smb.conf and see if it goes away:```
use client driver = yes
```

thank you, that did the trick.

---

### Post by swerdna on 2009-07-21
[IMG]http://opensuse.swerdna.org/forumpics/smiley/thumbup.gif[/IMG]

---

### Post by razzbar on 2009-09-30
I located two copies of smb.conf on my system. Which one? 
/etc/samba/smb.conf
or 
/usr/share/samba/smb.conf

They appear to be identical. Which one does samba configure from?

---

### Post by swerdna on 2009-09-30
/etc/samba/smb.conf

---

### Post by aggrey on 2009-10-11
I had the same problem and this is what I found out. 
Make sure the browsable and read only lines in smb.conf file are set to no.
[printers]
    comment = All Printers
    browseable = no
    path = /var/spool/samba
    printable = yes
    guest ok = yes
    read only = no
    create mask = 0700
   In the system-config-samba GUI, confirm full permissions have been allowed.
This is how you do it in the samba GUI.
 Click on the printer share and choose properties and allow full permissions.
I hope this helps.
:)

---

### Post by andyamos79 on 2011-10-02
Just a thank you for the information. I found this post after hours of "messing" with my Ubuntu server and this post helped sort the issue. The only thing I had to do once I modified the settings as suggested was to restart the samba daemon using 

sudo /etc/init.d/smbd restart

Anyway, thanks again.

---

