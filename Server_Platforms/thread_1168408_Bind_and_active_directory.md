---
title: "Bind and active directory"
date: 2009-05-24
forum: Server Platforms
---

### Post by comandrei on 2009-05-24
I installed bind9 on my debian server and Active Directory on a Win2k3 server configured as a domain controller.
Stations always try to make updates in DNS, but I do not want this because i have statically configured the whole network and bind my filled logs with entries like:
Code:

SERVER1 named [2369]: client 192.168.4.21 # 50833: update 'dns_zone / IN' denied

I guess Windows is to blame, but how il get bind not login all it's faults?

---

### Post by koenn on 2009-05-24
You probably can reduce the loglevel for these updates by defining  logging in named.conf
see here : [http://www.zytrax.com/books/dns/ch7/logging.html](http://www.zytrax.com/books/dns/ch7/logging.html)

but it's probably a better idea to configure the windows systems to not do dynamic upates in DNS. Since you have Active Directory, you can use GPO to accomplish this.

---

### Post by comandrei on 2009-05-24
Could you give me an example of a GPO? I'm new to Active Directory

---

### Post by koenn on 2009-05-24
Ah, but this is a ***Linux*** support forum. You should probably use the Microsoft support channels, really. 

Anyway, it's pretty simple, conceptually, but can become a bit of a headache in practice. 
What you do is 
- open Active Directory Users and Computers
- create a GPO and link it to the OU where the computers are that you want to configure

something like this :
[http://users.telenet.be/mydotcom/library/sysadmin/graph/gpoprecedence2.png](http://users.telenet.be/mydotcom/library/sysadmin/graph/gpoprecedence2.png)

- Edit the GPO you created and set the required conf options. In your case, you'll probably want to find Computer Configuration/Administrative Templates/System/DNS Client/Disable Dynamic Update and **Enable** it.

(and some people still think a linux shell and text files are complex compared to Windows GUI system administration...)

----
edit:
this looks a bit more recent:
[http://myitkb.net/2357/group-policy-dynamic-update.html](http://myitkb.net/2357/group-policy-dynamic-update.html)
---

Here's a step-by-step : [http://support.microsoft.com/kb/294832](http://support.microsoft.com/kb/294832)

GPO FAQ : [http://technet.microsoft.com/en-us/windowsserver/grouppolicy/cc817587.aspx](http://technet.microsoft.com/en-us/windowsserver/grouppolicy/cc817587.aspx)

In stead of ADUC you can also use GPMC : [http://www.microsoft.com/windowsserver2003/gpmc/gpmcintro.mspx](http://www.microsoft.com/windowsserver2003/gpmc/gpmcintro.mspx)

---

