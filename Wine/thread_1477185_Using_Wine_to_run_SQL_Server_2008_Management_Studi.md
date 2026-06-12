---
title: "Using Wine to run SQL Server 2008 Management Studio"
date: 2010-05-08
forum: Wine
---

### Post by thefish123 on 2010-05-08
Hi everyone,

I am running Ubuntu 10.04 and have a question about which version of Wine I should install.  As you probably know there are two versions in the repositories.  Should I run the “old” one?  Or the new one based off the recent beta version of Wine.

I have a few programs (one in particular) that I would love to be able to run under Linux.  I need to be able to run the “SQL Server 2008 Management Studio” tool so I can manage some Microsoft SQL servers without the need to reboot into Windows.  This is on Microsoft’s website as a free (as in beer) download.  I have looked for free (as in freedom) alternatives to this tool and can only find similar products for MySQL.
[http://www.microsoft.com/downloads/details.aspx?familyid=08E52AC2-1D62-45F6-9A4A-4B76A8564A2B&displaylang=en](http://www.microsoft.com/downloads/details.aspx?familyid=08E52AC2-1D62-45F6-9A4A-4B76A8564A2B&displaylang=en)

The SQL Server 2008 Management Studio is my primary reason for looking at Wine.  The other programs I might like to run would be Microsoft’s own RDP client called “Remote Desktop Connection” (mstsc.exe) and maybe (just maybe) Internet Explorer 8 (for compatibility testing).

I have a complete and legal copy of Windows XP SP3.  Would I have better “luck” with Wine if I used more of the Windows-native libraries the Wine libraries?

Looking forward to hearing your suggestions...

Best regards,
The Fish

---

### Post by cogadh on 2010-05-08
You should definitely use the most recent version of Wine, the management studio won't work in anything older than 1.1.38, according to AppDB. As for the other apps you are interested in, both are a complete lost cause in Wine and have been for quite some time. Using native libraries in Wine should only be done when you encounter an error with a particular library and should not be used out of hand. In many cases, Wine's own "DLLs" are better than the Windows ones, so if you start replacing DLLs that aren't causing problems, you can break your Wine configuration.

---

### Post by thefish123 on 2010-05-08
> **cogadh said:**
> You should definitely use the most recent version of Wine, the management studio won't work in anything older than 1.1.38, according to AppDB.I am a little unclear what version of wine I would be installing in either case.  If I search for “wine” in Synaptic Package Manager I get a package called “wine1.2” and another called simply “wine”.  Both of these display version 1.1.42-0ubuntu4 in the “Latest Version” column.  So, should be be installing the wine1.2 package?  Or just stick with the one called “wine”?

> **cogadh said:**
> As for the other apps you are interested in, both are a complete lost cause in Wine and have been for quite some time.My only reason for wanting to install Microsoft's native RDP client (mstsc.exe) in the first place is because it seems that rdesktop cannot connect to a server when SSL is used.  The remote server must be configured with "Negotiate" as the security layer which allows the client to connect without using SSL.  While there is encryption built into the RDP protocol I prefer to keep my Internet facing Windows boxes as secure as possible.

Thanks again...
The Fish

---

### Post by cogadh on 2010-05-09
Go with the 1.2 package, just to be safe. There might be two different packages because at least one of them is just a "dummy" package that points at the same download as the other one, but I'm not sure.

---

### Post by molafish on 2010-10-28
> **thefish123 said:**
> My only reason for wanting to install Microsoft's native RDP client (mstsc.exe) in the first place is because it seems that rdesktop cannot connect to a server when SSL is used.  The remote server must be configured with "Negotiate" as the security layer which allows the client to connect without using SSL.  While there is encryption built into the RDP protocol I prefer to keep my Internet facing Windows boxes as secure as possible.

Use Remmina. It uses FreeRDP as the RDP library implementation, and that projects supports more of the newer RDP protocol specification than rdesktop. There are still some win08 servers I cannot RDP to when they use a certain configuration (the specifics of which escape me at the moment), but Remmina is far better than rdesktop.

---

### Post by d.coli on 2011-12-19
+1 for **Remmina**. Really solid (though IIRC it did crash on me once.) But it allowed me to connect to my Vista Business 64-bit just fine, and was very smooth.

---

