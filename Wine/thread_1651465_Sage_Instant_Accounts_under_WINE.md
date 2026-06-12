---
title: "Sage Instant Accounts under WINE"
date: 2010-12-23
forum: Wine
---

### Post by browndog289 on 2010-12-23
Hello

I have recently moved my system over to Ubuntu 10.10 64-Bit Desktop from Windows 7 64-Bit.

I need to get my accounts package working under Ubuntu. I use an old version of Sage Instant Accounts v8.2.

I have managed to install it in WINE and it loads up and I can access my customers, suppliers and invoices etc. However if I try and run a report or print anything from any of these screens I get the following message:

Report Designer
Unable to connect to Data Source.
Check configuration.

I have been reading up on this and I think it is to do with ODBC. Sage Report Designer uses ODBC for the report templates. I have tried to change the settings for odbc32.dll in the WINE configuration to use the native and then the built-in library but I get the same error.
If I change it to disabled I get a different error:

Report Designer
Failed to load report library ACCREP.DLL

Can anyone help me to get ODBC working under WINE so I can use my accounting package properly. I don't really want to go the route of installing VirtualBox and then XP to do this.

Thanks

---

### Post by ReetP on 2011-02-21
> **browndog289 said:**
> Hello

I have recently moved my system over to Ubuntu 10.10 64-Bit Desktop from Windows 7 64-Bit.

I need to get my accounts package working under Ubuntu. I use an old version of Sage Instant Accounts v8.2.

I have managed to install it in WINE and it loads up and I can access my customers, suppliers and invoices etc. However if I try and run a report or print anything from any of these screens I get the following message:

Report Designer
Unable to connect to Data Source.
Check configuration.

I have been reading up on this and I think it is to do with ODBC. Sage Report Designer uses ODBC for the report templates. I have tried to change the settings for odbc32.dll in the WINE configuration to use the native and then the built-in library but I get the same error.
If I change it to disabled I get a different error:

Report Designer
Failed to load report library ACCREP.DLL

Can anyone help me to get ODBC working under WINE so I can use my accounting package properly. I don't really want to go the route of installing VirtualBox and then XP to do this.

Thanks

Just managed to get Sage Line50 v7 running under wine 1.2.2 (10.04 AMD64). Had the same problem with ODBC/Report designer.

This got me thinking :
[http://www.unixodbc.org/doc/wine.html](http://www.unixodbc.org/doc/wine.html)
[http://wiki.winehq.org/NativeOdbc](http://wiki.winehq.org/NativeOdbc)

Then I tried this :

[http://www.justuber.com/linux:wine_hacks](http://www.justuber.com/linux:wine_hacks)

Installed jet40 mdac27 mdac28 and ran native_mdac to be sure.

I then had a look in the ODBC Control Panel but something still wasn't right. I remember yonks ago there had to be something Sage related in there.

Had a mooch in the Line50 directory and noticed the ODBC directory, with the Sage ODBC drivers. Ran the setup for that and Presto ! Off we went - Reports & Invoices etc. ran, and all the printers could be seen. I only really need to be able to PDF reports anyhow which does work so I guess hard copy should be OK too !

So I guess it just needed the Sage ODBC drivers.

If you are still stuck then let me know and I can always make the files available.

B. Rgds
John :D

---

