---
title: "Samba Issues after Kernel Update"
date: 2010-08-15
forum: Server Platforms
---

### Post by hibliss on 2010-08-15
Today when I logged into my fileserver it told me there were 20 updates available. I went ahead and installed them, one was a new kernel.

After reboot, I cannot see that machine when I browse the network. It still has the same static IP and I can still map to the shared drives, so Samba is working.

When I browse the network from Windows or my WDTV Live media play it no longer shows the server by name.

The smb.conf file is still intact and I restarted Samba. 

Not really sure where to start troubleshooting why I can't browse to it.

---

### Post by Thomas Garman on 2010-08-15
One thing I know about samba with the most recent 10.04 upgrades is that you have to go to synaptic and install libapache2.2 and also libapache2.2-dns-mod and why in the name of all that is holy you have to actually go manually install those two packages to get sharing to work is beyond me but that's what I discovered when I tried to use it.

---

### Post by Morbius1 on 2010-08-15
> **Thomas Garman said:**
> One thing I know about samba with the most recent 10.04 upgrades is that you have to go to synaptic and install libapache2.2 and also libapache2.2-dns-mod and why in the name of all that is holy you have to actually go manually install those two packages to get sharing to work is beyond me but that's what I discovered when I tried to use it.
Especially since none of that has anything to do with Samba. Those two packages are required to enable "Personal File Sharing" which creates a baby apache file server and uses avahi to broadcast the only folder it's capable of sharing: "Public" in your home folder.

hibliss, are the two samba related services running:
```
sudo service smbd status
sudo service nmbd status
```If not start them:
```
sudo service smbd start
sudo service nmbd start

```

---

### Post by Morbius1 on 2010-08-15
Duplicate post

---

### Post by capscrew on 2010-08-15
Make sure that there is no firewall installed that would block NetBIOS broadcasts.

---

### Post by mdlueck on 2010-08-15
Do you know which machine on your network is the Browse Master? Perhaps since you IPL'ed the Ubuntu Box, something else took over as Browse Master and it overlooks the existence of the Ubuntu box.

I configure my Samba PDC's to forcefully win all master browser elections, and even go as far as disabling the service in Windows.

For further details see:

"Samba 3 PDC for Windows Clients and Samba 3 Book Review" Presentation from 2007
[http://www.lueckdatasystems.com/Samba_3_PDC_for_Windows_Clients_and_Samba_3_Book_Review-Presentation_from_2007](http://www.lueckdatasystems.com/Samba_3_PDC_for_Windows_Clients_and_Samba_3_Book_Review-Presentation_from_2007)

---

### Post by hibliss on 2010-08-15
Thanks for your replies. I checked the status of the two services as suggested. SMBD was running of course, but NMBD was not. I started that as suggested and that did the trick.

I have never started this service separately before, but now I know.

Thank you again.

---

### Post by Morbius1 on 2010-08-15
It's my understanding that the starting of the nmbd daemon will fail if it is started before the network is up so if this is happening all the time you might want to try something like this:

Create a script:
```
gksu gedit /etc/network/if-up.d/nmbd 
```With this content:
```
#!/bin/sh
service nmbd start 
```Save the file and make it executable:
```
sudo chmod +x /etc/network/if-up.d/nmbd 
```Reboot

Any script placed in if-up.d will run only after the network is up. The only problem with this is that the launching of nmbd only after the network is up is the way it's supposed to work by default. Why it's not working that way for some now is a mystery.

---

### Post by hibliss on 2010-08-15
Thanks for that tip. If I continue to have issues I will do that.

This just started after upgrading to the newest kernel, so that may have something to do with it. There was no update to Samba that I could see in the history.

---

