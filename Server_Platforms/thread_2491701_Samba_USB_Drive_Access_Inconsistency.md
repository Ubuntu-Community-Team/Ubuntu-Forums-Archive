---
title: "Samba USB Drive Access Inconsistency"
date: 2023-10-18
forum: Server Platforms
---

### Post by w-kym-wittal on 2023-10-18
I have Samba running on my server, Win 10 computer access works well.  I have had a USB hard drive attached for years and again, Win 10 can access the USB drive with no issues.

I have recently added a new USB hard drive and copied the smb.conf code to duplicate the access for the new hard drive (just changed the name).  Code in smb.conf below.  Existing USB hard drive is 'Seagate Backup Plus Drive' and the new USB hard drive is 'FreeAgent GoFlex Drive'.

```
[Seagate Backup Plus Drive]
    path = /media/kym/Seagate Backup Plus Drive
    writeable = yes
    browseable = yes
;    valid users = kym, nobody, W. Kym Wittal

        guest ok = yes
        public = yes
      
        read only = no
        writable = yes
        force user = root
 
[FreeAgent GoFlex Drive]
    path = /media/kym/FreeAgent GoFlex Drive
    writeable = yes
    browseable = yes
;    valid users = kym, nobody, W. Kym Wittal

        guest ok = yes
        public = yes
       
        read only = no
        writable = yes
        force user = root
```

The inconsistency is that now, the new USB drive can be accessed by Win 10, no issues, however, the original USB drive states:

'Windows cannot access \\UBUNTU\Seagate Backup Plus Drive'
'Error code: 0x80070043'
'The network name cannot be found'

I can go to the server, restart smbd with the following:

```
sudo systemctl restart smbd
```

Once complete, both drives are now accessible.

After a while, the original USB drive will become inaccessible again.  Restart smbd.conf again, all good for a while.

System is up to date.

Any advice on where to start looking or what the issue might be?

Thanks, Kym.

---

### Post by TheFu on 2023-10-18
Don't mount under /media/ and don't let magical semi-automatic mounts be used.
Use either autofs or the fstab to mount the file system.

Oh ... and never mount to places with spaces in the name.  If you do, you are expected to quote the entire string.  Easier just to set a LABEL and use that to setup autofs using the LABEL= mount option.

If the network name cannot be found, that's a name resolution issue. The easiest solution is to use the static IP for the storage server and to be 100% certain it isn't using DHCP to get network IPs.  There are harder ways to make it work, but MSFT changed from using nmbd to some new-fangled directory-service lookup a few years ago.  Morbius1 posts how to do that in these forums a few times.

Looked it up ...

Install Samba, WS-Discovery tool, and Avahi:
```
  sudo apt update
  sudo apt install samba wsdd avahi-daemon
```
The name to look for will be {hostname}.local   ... so you'd need ubuntu.local if I'm understanding your attempts above.

And don't have spaces in the directory names OR in the Samba mount names.

---

### Post by w-kym-wittal on 2023-10-18
Thank you very much for the feedback.  The only thing I have already done is use a static IP.  Looks like I have some work to complete.

If I run into any issues, I will update this thread.

---

