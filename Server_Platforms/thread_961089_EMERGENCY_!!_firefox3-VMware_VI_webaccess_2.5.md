---
title: "EMERGENCY !! firefox3-VMware VI webaccess 2.5"
date: 2008-10-28
forum: Server Platforms
---

### Post by Phulerock on 2008-10-28
I'm using Ubuntu 8.04 64bit, firefox3. I cant install VI web access plugin for Firefox in  
VMware Virtual Infrastructure Web Access (64191)
VMware VirtualCenter: 2.5.0 (64192)

This VI Web access use for VMware ESX server commercial. The web document this VI Web access say firefox 1.5 or later can install this plugin, but I can't.

My firefox3 can only connect to VI Webaccess of Vmware Server 2.0 Build 116503 that provide VI web access 2.0.0 Build 116487

Anyway to help me !

---

### Post by tomwerner470 on 2008-10-28
I am assume the error is that you are getting a version error, if so read on...

I am not sure about that version of web access, however the plugin that comes with Vmware Server 2 is not compatiable with Firefox 3. To fix this you need to make a quick change to the ff plugin stored on your VMware server. On my Linux server the files are located in:

/usr/lib/vmware/webAccess/tomcat/apache-tomcat-6.0.16/webapps/ui/plugin/

However, just do a 

```
sudo find / -name *.xpi
```

To find where they are hiding. 

The XPI files are just zip files with a different extension, so make a copy of the plugin, extract it and open install.rdf for editing. Find the Description section and change the MaxVersion paramter to '3.*' (without quotes). Zip up the modified plugin and drop it back in the original location, enuring you have the same filename. Next time you try to install, the plugin should install. There are several xpis, make sure you alter the ones for the correct architecture and platform.

A WARNING THOUGH - This worked for the Remote Access Console in Vmware Server 2, however, there could be good reason why the plugin you mentioned is not enabled to work with 3.x - it may make FF unstable.

---

### Post by Phulerock on 2008-10-29
The newest version of VMware server 2.0 (is Build 116503) is now install plugin and work smoothly with FF3.

I only have the problem is Vmware Virtual Center 2.5 (commercial vesion) don't provide the plugin that compatible with ff3 for Linux.

Plugin of Vmware server 2.0 is different plugin of Vmware Virtual Center 2.5, and Infrastructure Client tool only have for Windows. 

sad

---

