---
title: "[SOLVED] Samba log file"
date: 2006-08-08
forum: Server Platforms
---

### Post by tjansson on 2006-08-08
I have a server setup with samba and everything is works fine. The only thing that annoys me is that the log files are filled with lines like this:
```

[2006/08/08 12:59:00, 0] printing/pcap.c:pcap_cache_reload(159)
  Unable to open printcap file /etc/printcap for read!

```

all the log files in /var/log/samba are filled with these lines, so I tried to disable all printer settings in /etc/samba/smb.conf and afterwards it look like this:
```

   load printers = no

;   printing = bsd
;   printcap name = /etc/printcap
;   printing = cups
;   printcap name = cups
;   printer admin = @lpadmin

;[printers]
;   comment = All Printers
;   browseable = no
;   path = /tmp
;   printable = yes
;   public = no
;   writable = no
;   create mode = 0700

;[print$]
;   comment = Printer Drivers
;   path = /var/lib/samba/printers
;   browseable = yes
;   read only = yes
;   guest ok = no

```

The reloaded the samba server with /etc/init.d/samba reload, but appereantly it didn't work since the log files still contains the lines:
```

root@utopia:/var/log/samba# tail log.smbd
[2006/08/08 13:45:31, 0] printing/pcap.c:pcap_cache_reload(159)
  Unable to open printcap file /etc/printcap for read!
[2006/08/08 13:45:31, 0] printing/pcap.c:pcap_cache_reload(159)
  Unable to open printcap file /etc/printcap for read!
[2006/08/08 16:14:47, 1] smbd/server.c:open_sockets_smbd(360)
  Reloading services after SIGHUP
[2006/08/08 16:14:47, 0] printing/pcap.c:pcap_cache_reload(159)
  Unable to open printcap file /etc/printcap for read!
[2006/08/08 16:14:47, 0] printing/pcap.c:pcap_cache_reload(159)
  Unable to open printcap file /etc/printcap for read!

```

---

### Post by mynameisjohn on 2006-08-09
i believe you want some lines like these

```
   printcap name = /dev/null
   load printers = no
   printing = bsd
```

hth

---

### Post by tjansson on 2006-08-09
Nice - that seems to have worked! Thanks alot!

---

