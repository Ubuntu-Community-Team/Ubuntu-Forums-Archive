---
title: "need help in final stages of cups + samba printer sharing"
date: 2008-07-23
forum: Server Platforms
---

### Post by opportunity on 2008-07-23
Hi,

I am trying to get cups/samba to feed the windows drivers to clients when adding a network printer. I am using the below tutorial for novell. 

[http://www.novell.com/coolsolutions/feature/18850.html](http://www.novell.com/coolsolutions/feature/18850.html)

When i do the "cupsaddsmb -v <cups printer name>" step, ubuntu tells me "No windows drivers are installed!".  I have dumped the specific drivers for the printer to /usr/share/cups/drivers.

File list:

eS850PS.chm  eS8mPcfg.dll  eS8mps.PDF    eS8mps.XPI   eSPDLDLG.dll
eS8mcfg.dll  eS8mpdrc.dll  eS8mpsui.dll  eS8mVal.xml  eSTsnmp.dll
eS8mdtp.dll  eS8mProf.gps  eS8mpsum.dll  eSPDLD.chm   TSeS8m_1.PPD
eS8mip.dll   eS8mps.dll    eS8mpswm.exe  eSPDLD.dll



samba conf :

[print$]
   comment = Printer Drivers
   path = /usr/share/cups/drivers
   browseable = yes
   read only = yes
   guest ok = no

---

### Post by opportunity on 2008-07-23
did a few more things from this tut:

[http://www.enterprisenetworkingplanet.com/netsysm/article.php/3621876](http://www.enterprisenetworkingplanet.com/netsysm/article.php/3621876)

Now when i run the smbadd command i get :


Unable to copy Windows 2000 printer driver files (1)!
Running command: smbclient //localhost/print$ -N -A /tmp/48873150a6e1d -c 'mkdir W32X86;put /tmp/4887314a80854 W32X86/Large_Toshiba_520_Copier.ppd;put /usr/share/cups/drivers/ps5ui.dll W32X86/ps5ui.dll;put /usr/share/cups/drivers/pscript.hlp W32X86/pscript.hlp;put /usr/share/cups/drivers/pscript.ntf W32X86/pscript.ntf;put /usr/share/cups/drivers/pscript5.dll W32X86/pscript5.dll'
Domain=[LSERVICES] OS=[Unix] Server=[Samba 3.0.28a]
tree connect failed: NT_STATUS_ACCESS_DENIED

---

### Post by opportunity on 2008-07-23
this last tut + comments gave the full picture and i was able to install.

[http://wdhawes.blogspot.com/2007/03/sharing-printers-with-windows-clients.html](http://wdhawes.blogspot.com/2007/03/sharing-printers-with-windows-clients.html)

Now however, my windows clients say that the correct drivers cannot be found on the print server. How can i test to see if the print driver share is accessable from these machines?

---

