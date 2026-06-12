---
title: "Unable to restart SAMBA - ubuntu server 18.04"
date: 2018-08-11
forum: Server Platforms
---

### Post by ChrisRChamberlain on 2018-08-11
Hi

Have edited /etc/samba/smb.conf using code carried forward from previous working server installations and modified paths as required.

```
sudo service smbd restart
```results in ```
Job for smbd.service failed because the control process exited with error code.
See "systemctl status smbd.service" and "journalctl -xe" for details.

``````
systemctl status smbd.service
```produces```
&#9679; smbd.service - Samba SMB Daemon
   Loaded: loaded (/lib/systemd/system/smbd.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Sat 2018-08-11 16:18:17 UTC; 12min ago
     Docs: man:smbd(8)
           man:samba(7)
           man:smb.conf(5)
  Process: 4463 ExecStart=/usr/sbin/smbd --foreground --no-process-group $SMBDOPTIONS (code=exited, status=1/FAILURE)
 Main PID: 4463 (code=exited, status=1/FAILURE)

Aug 11 16:18:16 econel-200 systemd[1]: Starting Samba SMB Daemon...
Aug 11 16:18:17 econel-200 systemd[1]: smbd.service: Main process exited, code=exited, status=1/FAILURE
Aug 11 16:18:17 econel-200 systemd[1]: smbd.service: Failed with result 'exit-code'.
Aug 11 16:18:17 econel-200 systemd[1]: Failed to start Samba SMB Daemon.

```Ideas please?

TIA

---

### Post by darkod on 2018-08-11
Did you modify just parts of the smb.conf or you replaced the whole content from a previous version? I had similar problems when replacing the whole file. It seems they are not 100% compatible between versions.

I suggest you try keeping the default smb.conf that comes with 18.04 and in it you add only the parts that you need. Try modifying bit by bit, restarting samba along the way to confirm it didn't break.

---

### Post by Morbius1 on 2018-08-11
If you didn't make a copy of your default smb.conf there is another one at: **/usr/share/samba/smb.conf**

I can easily reproduce that error by adding a line in the [global] section: **security = share. **Many users had that in their smb.conf files from way back but it's not a real option anymore and stops smbd from running. 

That may not be your exact issue but if you run the following command it may provide an error massage:
```
testparm -s
```

---

### Post by ChrisRChamberlain on 2018-08-12
Darkod, Morbius1

Thanks for your replies.

Replaced modified smb.conf with the default smb.conf, tested, fine.

Appended a share to smb.conf, tested, fine, excepting that the server is not visible to any Windows device on the WORKGROUP network.

Access via other linux boxes is ok.

In the smb.conf used for previous O/Ss, there was under Global settings```
netbios name = ServerName
```a reference to presumably identify the server on the WORKGROUP network.

Unable to locate any such or similar reference in the current smb.conf - so what's missing please?

---

### Post by Morbius1 on 2018-08-12
> In the smb.conf used for previous O/Ss, there was under Global settings     Code:
     netbios name = ServerName 
a reference to presumably identify the server on the WORKGROUP network.

Unable to locate any such or similar reference in the current smb.conf
It is usually not necessary to add that line because it is in the defaults ( smb.conf does not hold the defaults for samba only overrides ).

If you run this command you should see the default sets the netbios name to the host name:
```
testparm -sv /dev/null | grep "netbios name"
```

There is one problem with using netbios and that is the length of the host name. If it's more than 15 characters long it is unresolvable to a Windows client - A Linux client can use another method. That is when you would use smb.conf to override the netbios name.

---

### Post by ChrisRChamberlain on 2018-08-12
```
testparm -sv /dev/null | grep "netbios name"
```returns the server's name correctly - thanks.

Powered down the complete network and started again. 

Voila! Some of the Windows 10 pcs work as expected and log onto the share correctly - others do not but will accept mapping of the share, another demands credentials but won't accept them.

Windows, eh!

Many thanks to those who contributed to the thread, now marked as solved.

---

