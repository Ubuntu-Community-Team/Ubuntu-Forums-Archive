---
title: "Cups Connection Refused in Samba Logs"
date: 2010-02-04
forum: Server Platforms
---

### Post by smc18 on 2010-02-04
Hello everyone,

I was just checking some of the generated logs from Samba.

```
cat /var/log/samba/log.PC1
```

and I saw this that bothers me

> [2010/01/10 09:54:13,  0] printing/print_cups.c:cups_connect(68)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2010/01/10 10:08:14,  0] printing/print_cups.c:cups_connect(68)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2010/01/10 10:08:14,  0] printing/print_cups.c:cups_connect(68)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2010/01/10 10:21:14,  0] printing/print_cups.c:cups_connect(68)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2010/01/10 10:21:14,  0] printing/print_cups.c:cups_connect(68)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2010/01/10 10:37:14,  0] printing/print_cups.c:cups_connect(68)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2010/01/10 10:37:14,  0] printing/print_cups.c:cups_connect(68)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2010/01/10 10:53:14,  0] printing/print_cups.c:cups_connect(68)
  Unable to connect to CUPS server localhost:631 - Connection refused

I've looked over my smb.conf and it doesn't look like I even have any printer sharing enabled.

> ########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
;   load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
;   printing = cups
;   printcap name = cups



...(Output omitted)



;[printers]
;   comment = All Printers
;   browseable = no
;   path = /var/spool/samba
;   printable = yes
;   guest ok = no
;   read only = yes
;   create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
;[print$]
;   comment = Printer Drivers
;   path = /var/lib/samba/printers
;   browseable = yes
;   read only = yes
;   guest ok = no



Can anyone point me in the direction of how PC1 was refused a connection when it looks like I don't have any printers being shared throught Samba?  And also, what can I do to fix this?

This is just on a home LAN.

Thanks a bunch!!

---

### Post by smc18 on 2010-02-04
Searching on Google, I happened to find a few other people had this issue and they added the following to [global].

(I'll find out within the next couple of days if this works for me)

> load printers = no		
	show add printer wizard = no
	printing = none
	printcap name = /dev/null
	disable spoolss = yes


I entered the above and restarted the samba daemon and somehow broke something else. uh oh!

My public and private file shares are not longer working... back to the lab.


EDIT:  Found the problem :)

I also added the following to add some restriction on the shares

> hosts allow = 192.168.1 127.

Well it turns out I forgot the ending decimal on 192.168.1.

So I changed it to

> hosts allow = 192.168.1. 127.

And everything works!!  :)

---

