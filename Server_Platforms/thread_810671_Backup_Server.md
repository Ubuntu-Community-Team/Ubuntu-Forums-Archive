---
title: "Backup Server"
date: 2008-05-28
forum: Server Platforms
---

### Post by carbm1 on 2008-05-28
I have a business that is wanting to do automated offsite backups of their small servers.  I'm thinking about setting up a box that has OpenVPN and RSYNC on it for their backups.  I hope to set the box up at their house and port forward OpenVPN to the box.  Setup server with iptables and only allow the VPN connection.  Then have the box rsync its data to the backup server.

I'm thinking just any old desktop PC I can find.
Ubuntu 8.04 Server
3 500GB HDD's running RAID1 with one on standby.
IPTables Locked Down to only allow through VPN with ACLs of Static IPs
OpenVPN
Webmin & SSH(for me!)
Samba (Only through VPN, for copying data back!)
RSYNC Daemon (utilizing RSNAPSHOT)

So, I doubt there is an OpenSource solution that covers any of this topic is there?  Something for offsite encrypted and such?  Any ideas, suggestions?

---

### Post by MJN on 2008-05-28
If you're running SSH on it then there's no need for the VPN - Rsync will work quite happily over SSH.

It keeps things simple without compromising security/usability.

Mathew

---

### Post by NateMan on 2008-05-28
I think he just wants the vpn to secure samba for copying from the server to his windows box.

---

### Post by MJN on 2008-05-28
Ah, okay. He could just use rsync for copying the data back (in fact I would recommend doing so).

Mathew

---

### Post by NateMan on 2008-05-28
Ah I didn't realize there was a rsync client for windows, but I found a nice guide on installing it and setting it up.

[http://www.gaztronics.net/rsync.php](http://www.gaztronics.net/rsync.php)

---

### Post by Girya on 2008-05-28
What about keeping the backup server on the local network that the client server(s) is attached to and using a raid 5 setup and hot swapping one of the drives for offsite storage? I think rsync over the internet could be really slow and make for some long backups. also less security issues.

---

### Post by windependence on 2008-05-28
> **Girya said:**
> What about keeping the backup server on the local network that the client server(s) is attached to and using a raid 5 setup and hot swapping one of the drives for offsite storage? I think rsync over the internet could be really slow and make for some long backups. also less security issues.

The data is striped across the drives on a RAID 5 array. You can't just pull out one drive, it would be useless. 


Yes, I agree rsync over the net WILL be slow, but that could be mitigated by taking a snapshot to local disk and then doing the transfer. Also, VPN is not that reliable sometimes either. Anytime you have to rely on an outside connection you run the risk of getting disconnected half way through. Your script will need to be able to resume by itself.


If it was me I would just put it on the local network and run AMANDA or Bacula.

-Tim

---

### Post by MJN on 2008-05-29
> **Girya said:**
> I think rsync over the internet could be really slow and make for some long backups. also less security issues.

What security issues?

Rsync is designed to operate on low/poor bandwidth links by virtue of its ability to easily continue from where it left off should a link fail, and to also only require transmission of those files (or indeed *parts* of files) that have changed. It does of course support compression too if required.

I run daily offsite backups of multiple 120GB drives and the time taken each night is insignificant. In six years of operation I've also never had a link failure during the backup - not that this would be a big deal as if this threat were real it would be trivial to check the return status of the script and re-run if necessary to continue where it left off.

Manually hot-swapping drives for backup is prone to failure of the weakest link - the human operator.

Mathew

---

### Post by hyper_ch on 2008-05-29
MJN:

Don't forget to mention the possibility of making incremental snapshot-style backups using the power of hardlinks... I keep myself backups for 90 days.

---

