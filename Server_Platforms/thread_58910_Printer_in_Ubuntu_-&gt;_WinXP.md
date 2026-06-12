---
title: "Printer in Ubuntu -&gt; WinXP"
date: 2005-08-22
forum: Server Platforms
---

### Post by Vampis on 2005-08-22
I'm starting with informing that I searched the forum, read the post's and the refered links in these posts. I have also used google, and I still can't solve my problem.

I have installed the printer Brother HL-1230 on my Ubuntu-server and it is working like a charm. Now I have tried to share this printer with my Window's machines @ home with Samba, but this does not work at all. Windows finds the printer and connect's to it but when I'm trying to print the error-messege pops up "Test page failed to print" 

This is my smb.conf
```

[printers]
   comment = All Printers
   browseable = yes
   path = /var/spool/samba
   printable = yes
   public = yes
   writable = yes
   guest ok = yes
   printer admin = niclas

[print$]
   comment = Printer Drivers
   path = /etc/cups/ppd
   browseable = yes
   read only = yes
   guest ok = yes
   write list = root

[HL-1230]
   comment = HL-1230
   printable = yes
   path = /var/spool/samba
   public = yes
   guest ok = yes
   printer admin = niclas

```

Under HL-1230 where I put path var/spool/samba i copy pasted from an example, maybe it's wrong? What should I put there if it is?

printer admin = niclas I use because if I use root there I'm not allowed to connect to the server, with niclas I am allowed to do that.

I'll appriciate som help because I need the printer and my new computer doesn't have any LPT port and my linuxserver has, this is my last hope :(

EDIT: 
It is maybe worth to mention that further up in the smb.conf there is also:
```

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
;   printing = cups
;   printcap name = cups

```

---

