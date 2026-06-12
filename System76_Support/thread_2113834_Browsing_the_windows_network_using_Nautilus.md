---
title: "Browsing the windows network using Nautilus"
date: 2013-02-08
forum: System76 Support
---

### Post by apdobaj on 2013-02-08
I'm at my wits end, hoping you can help. I have a Darter Ultra running 12.10 and I cannot browse my local network using Nautilus (Browse Network -> Windows Network shows nothing after churning for a bit). I can connect to a specific share using Go -> Location... either using IP address or computer name. I've made the changes to smb.conf and nsswitch.conf as suggested in the forums. Turning off all the firewalls doesn't help. The command "smbclient -d3 -L *ipaddr*" returns the expected share and server list (ipaddr is that of the router). I would like to be able to browse the network rather than typing and remembering computer names all the time. I could make them persistent (modify fstab) but we have lots of devices that come and go. Suggestions?

---

### Post by isantop on 2013-02-08
> **apdobaj said:**
> I'm at my wits end, hoping you can help. I have a Darter Ultra running 12.10 and I cannot browse my local network using Nautilus (Browse Network -> Windows Network shows nothing after churning for a bit). I can connect to a specific share using Go -> Location... either using IP address or computer name. I've made the changes to smb.conf and nsswitch.conf as suggested in the forums. Turning off all the firewalls doesn't help. The command "smbclient -d3 -L *ipaddr*" returns the expected share and server list (ipaddr is that of the router). I would like to be able to browse the network rather than typing and remembering computer names all the time. I could make them persistent (modify fstab) but we have lots of devices that come and go. Suggestions?

Wait a moment after clicking on the Network folder; it should list the computers available there, without clicking on "Windows Network", which I've never had much success with.

---

### Post by apdobaj on 2013-02-14
this doesn't work for me. the shares were shown as expected the other day when I was messing with my router settings to try and get a VPN session to work. I attempted to retrace my steps to no avail. Any other ideas?

---

### Post by isantop on 2013-02-14
You can check the settings on the Windows machine. I can't replicate any issues like that doing an Ubuntu-to-Ubuntu share. I can't test with a Windows share.

---

### Post by apdobaj on 2013-11-06
This seems to have been resolved in 13.10.

---

