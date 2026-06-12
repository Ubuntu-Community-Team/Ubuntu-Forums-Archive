---
title: "CUPS in Chrome - Not Authorized"
date: 2018-04-06
forum: Ubuntu Development Version
---

### Post by drs305 on 2018-04-06
Within the past day I've lost the ability to modify any CUPS settings via localhost:631 in Chome. I get a 

```
Unauthorized Enter your username and password or the root username and password to access this page. If you are using Kerberos authentication, make sure you have a valid Kerberos ticket.
``` 
message when trying to modify an HP printer via Administration > Manage Printers. Printing & modifying printers had not been a problem previously in 18.04.

Otherwise, things seem to be going really well with 18.04 and I've had very few issues.

I post this to let others know that modifications can still be made to the printers if using Firefox - it appears to be a Chrome/CUPS issue. I'm sure this will be addressed; if not I'll file a bug report.

---

### Post by TheFu on 2018-04-07
Could it be related to an https cert that chrome is becoming pickier about?

---

### Post by VMC on 2018-04-07
I just had this same problem. I thought it had to do with something I deleted (blues-cups?). So I installed beta version, and under Firefox it now works. I never thought about a browser problem. Looking at "/etc/cups" config files, nothing was out of place.

---

### Post by drs305 on 2018-04-08
I found nothing about this issue with Chrome. The package I'm using to give me version 65 I downloaded from the Google site so it isn't really an Ubuntu bug. Firefox still works as normally (add, delete, modify CUPS).

Anyway, I've tried a lot of different things and finally got one to allow me to alter my printers without getting the "Unauthorized" message while accessing CUPS from Chrome.

I edited /etc/cups/cupsd.conf and changed the AuthType to None and commented the Require user @SYSTEM:
> 
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default CUPS-Get-Devices>
[COLOR="#FF0000"]    AuthType Default
    Require user @SYSTEM[/COLOR]
    Order deny,allow
  </Limit>

to:
> 
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default CUPS-Get-Devices>
[COLOR="#FF0000"]       AuthType None
#    AuthType Default
#    Require user @SYSTEM[/COLOR]
    Order deny,allow
  </Limit>


Then run
```

sudo service cups restart

```

Disclaimer: Although my avatar still reflects some knowledge of Ubuntu, I 'retired' from the forums a long time ago. I don't know what, if any, ramifications there might be from altering this file (other than allowing me to use CUPS in Chrome). If you aren't comfortable altering system files, I'd highly recommend you just access CUPS via other means, including through Firefox.

I'd also like to emphasize that I believe this is a problem with Chrome. If you edit the /etc/cups/cupsd.conf file, I'd make a copy first so you can restore it at a later date - when Chrome's issues with the way CUPS works gets resolved.

---

### Post by VMC on 2018-04-08
I didn't have issue with CUPS on manjaro-xfce using chrome. I checked cups config files on both manjaro and xubuntu. Their identical.

---

### Post by VMC on 2018-04-10
I'm having the same issue using chromium-browser. Usually there are some differences. Both fail on xubuntu editing cups.

---

### Post by VMC on 2018-04-19
With the recent update of chrome([COLOR=#757575][FONT=Roboto]Version 66.0.3359.117 (Official Build) (64-bit))[/FONT][/COLOR], manjaro cups now doesn't work.

edit: Archlinux user have the same issue:
[https://bbs.archlinux.org/viewtopic.php?id=235841](https://bbs.archlinux.org/viewtopic.php?id=235841)

---

### Post by BFG on 2018-06-22
I've also had this problem with Chrome in Xubuntu 18.04, and I can confirm that the workaround to remove permissions from /etc/cups/cupsd.conf works.

I'd add that the lines quoted from drs305 above are correct, though there are three similar entries in /etc/cups/cupsd.conf with little to distinguish between them.
Look for the one containing "CUPS-Get-Devices" on the end of the row.



> **drs305 said:**
> 
```

<Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default [COLOR="#FF0000"]CUPS-Get-Devices[/COLOR]>

```


---

### Post by slickymaster on 2018-06-22
Ubuntu 18.04 is released.

Thread closed.

---

