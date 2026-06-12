---
title: "Ubuntu 20.10 Legacy-Server Kickstart Live-Server"
date: 2020-06-01
forum: Server Platforms
---

### Post by genesoo77072 on 2020-06-01
Up until 20.04, my process to use a Kickstart Preseed file worked with the Ubuntu Legacy-server installation ISO to produce an automated install package. Since Ubuntu 20.10 became available for daily drops, the Legacy-Server file directory has been created however there are no instances of daily build files. Live-Server is the only version of server than can be found and is regularly updated. 
I've tried porting the Kickstart process to Live-Server and received errors during boot of the modified ISO.

Is Legacy-Server now obsolete starting from Ubuntu 20.10? 
Regardless of whether Legacy-Server has been obsoleted, will Live-Server ever support the Kickstart automated installation process currently documented in Ubuntu installation documentation?

---

### Post by LHammonds on 2020-06-01
They only want to support the "live" installer and the "legacy" installer for 20.04 is said to be the last of the old Debian installer.

There is a new process for creating an auto-installer and they say it is more flexible but I have not yet tried it.

More info can be found here: [https://wiki.ubuntu.com/FoundationsTeam/AutomatedServerInstalls](https://wiki.ubuntu.com/FoundationsTeam/AutomatedServerInstalls)

LHammonds

---

