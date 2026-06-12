---
title: "Problems onLinux CUPS as Printer server for Windows automation of install Print Drive"
date: 2009-04-23
forum: Server Platforms
---

### Post by wolfteeth on 2009-04-23
Problems onLinux CUPS as Printer server for Windows automation of install Print Drive

I am using Ubuntu 8.10 server as a File and printer server, had succssed joined the Samba to Win2003 AD and intergration with Kerberos with no problem for share driver.
however, I followed up [http://www.enterprisenetworkingplanet.com/netsysm/article.php/3621876](http://www.enterprisenetworkingplanet.com/netsysm/article.php/3621876)

failed on: cupsaddsmb -H localhost -U root -a -v , since I am a member of domain, so&#65292;Security=ADS&#65292;even I changed root toadministrator&#65292;but still errors:
NT_STATUS_MEDIA_WRITE_PROTECTED making remote directory \W32X86
NT_STATUS_ACCESS_DENIED opening remote file \W32X86/HPDeskjet6600.ppd
NT_STATUS_ACCESS_DENIED opening remote file \W32X86/ps5ui.dll
NT_STATUS_ACCESS_DENIED opening remote file \W32X86/pscript.hlp
NT_STATUS_ACCESS_DENIED opening remote file \W32X86/pscript.ntf
NT_STATUS_ACCESS_DENIED opening remote file \W32X86/pscript5.dll
no matter how I setup permission and modify the smb.conf
for [print$] in write list/writeable, the problem still same.

I am expecting some expert who has experience on this settings, or give me any guideline would be appreciated.

My part of smb.conf:

[printers]
comment = All Printers
Path = /var/spool/samba
browseable = yes
printable = yes
public = yes
writeable =no
printer admin = administrator

[print$]
comment = Printer Drivers
path = /etc/samba/drivers
browseable = yes
read only = yes
write list = administrator

---

### Post by wolfteeth on 2009-04-24
I believe the problem should be related on the security options!!!

---

