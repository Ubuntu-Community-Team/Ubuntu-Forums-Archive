---
title: "rsyncd not running with systemd"
date: 2015-02-11
forum: Ubuntu Development Version
---

### Post by crcarson on 2015-02-11
Been running 15.04 under systemd for a week or so without any problems.  Noticed that my rsync job on my laptop is failing to connect to the 15.04 desktop.  The rsyncd is not running on the desktop.  There is what appears to be a valid rsync.service file in /lib/systemd/system which is supposed to start the rsyncd (in fact manually issuing the command returns no errors and the rsyncd runs and the laptop rsync job completes).  Check the systemd journal and do not see any indication that the start of the rsync.service job failed.  What should I check or try to get the rsyncd running?

---

### Post by crcarson on 2015-02-11
Running "systemctl stop rsync" and "systemctl start rsync" will stop and restart the rsyncd without any indication of an error.  Seems that something is stopping systemd from working on the rsync.service file when I boot the system.

---

### Post by crcarson on 2015-02-13
After booting the system ran the following "systemctl status rsync" and got the output....

cliff@Desktopps:/etc/systemd/system$ systemctl status rsync
&#9679; rsync.service - fast remote file copy program daemon
   Loaded: loaded (/lib/systemd/system/rsync.service; disabled; vendor preset: enabled)
   Active: inactive (dead)


Appears the service (or unit) is disabled and not starting automatically.  How do I enable the service?

---

### Post by crcarson on 2015-03-03
Maybe I'm asking the wrong question so how about this one...

Running 15.04 with systemd and want to ensure that the rsync daemon is started at boot.  What needs to be set?  Don't remember having an rsyncd problem when running 15.04 and upstart.

---

### Post by zika on 2015-03-04
```
sudo systemctl status rsync.service
sudo systemctl start rsync.service 
sudo systemctl enable rsync.service
sudo systemctl disable rsync.service 
```to check, start, make/stop it start on boot...

---

### Post by crcarson on 2015-03-04
> **zika said:**
> ```
sudo systemctl status rsync.service
sudo systemctl start rsync.service 
sudo systemctl enable rsync.service
sudo systemctl disable rsync.service 
```to check, start, make/stop it start on boot...

Thanks, running "sudo systemctl enable rsync" now starts rsyncd at boot.

---

### Post by zika on 2015-03-04
> **crcarson said:**
> Thanks, running "sudo systemctl enable rsync" now starts rsyncd at boot.Yeap, as it should. Enjoy... ;)

---

