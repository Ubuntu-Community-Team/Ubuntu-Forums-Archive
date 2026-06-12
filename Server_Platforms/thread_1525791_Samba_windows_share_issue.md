---
title: "Samba windows share issue"
date: 2010-07-07
forum: Server Platforms
---

### Post by Leppie on 2010-07-07
I cannot browse the samba printers from windows xp professional clients.
I get the following message when trying to access the workgroup:
```
Example is not accessible. You might not have permission to use this network resource. Contact the administrator of this server to find out if you have access permissions.  
  
The list of servers for this workgroup is not currently available 
```
Another strange thing is that if I set the workgroup to EXAMPLE in smb.conf, the workgroup shows up as Example on my windows clients.

any help/suggestions much appreciated.

---

### Post by Morbius1 on 2010-07-07
On the WinXP box open **Command Prompt** and issue the following command:
```
net view
```If you get a 6118 error it's most likely a WinXP firewall issue. Try to temporarily disable the WinXP firewall just to see if it's in the way.

Either that or the "Computer Browser Service" in XP has not started. You can start it from services in the control panel. Sorry I'm not in front of an XP machine so I don't remember the path to get to the "Services" section.

---

### Post by DJYoshaBYD on 2010-07-07
well, in XP, if you have file and printer sharing on, then you should have no issues accessing printers on the LAN.. 

How did you set up your shares? 

And yes, it does sound like a firewall issue.. Windows XP can black SMB traffic.. I leave that thing off all the time anyway.. lol.. Its useless..

tell us how you set up your windows machine to access your network? are you using the same workgroup name? cause that would do that, as well..

---

### Post by Leppie on 2010-07-07
well, i've made some progress. i was able to join the xp machine to the domain.
the net view command shows my samba server as result, i've disabled the windows firewall just to ensure it's not hindering anything.
i can browse the printers offered through samba, but i cannot connect to them.
i get the error:
```
A policy is in effect on your computer which prevents you from connecting to this print queue. Please contact your system administrator.
```

a complication could be that this is a vm. xp is a guest os in VirtualBox.

---

### Post by Leppie on 2010-07-07
Ok, just found out that in xp sp1+ only power users and administrators can install printers.
after logging onto the machine as a local admin, i could add the network printers.

many thanks for your help guys :)

---

