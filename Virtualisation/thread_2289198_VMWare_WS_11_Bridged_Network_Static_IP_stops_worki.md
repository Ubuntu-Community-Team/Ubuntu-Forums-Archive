---
title: "VMWare WS 11 Bridged Network Static IP stops working after 5-60 seconds"
date: 2015-08-02
forum: Virtualisation
---

### Post by daveomcd on 2015-08-02
I have a setup with VMWare Workstation 11 WIN 8.1 (Host) & Ubuntu 15.04 (Guest).  I'm trying to bridge my connection so I can access my host's SQL Server.  Currently I can access my host computer from guest just fine; however, accessing the internet from guest only works when attempting to do so right after establishing the connection.  I've set the connection up with a static ip. I commented out the connection settings in /etc/network/interfaces, but turned managed=true on in my [COLOR=#333333][FONT=inherit] /etc/NetworkManager/NetworkManager.conf file. After doing this I setup the connection through the GUI.  How can I troubleshoot the connection to find out why it's not staying connected?[/FONT][/COLOR]

---

### Post by howefield on 2015-08-02
Thread moved to the "*Virtualisation*" forum.

---

