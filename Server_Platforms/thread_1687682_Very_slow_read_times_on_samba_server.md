---
title: "Very slow read times on samba server"
date: 2011-02-14
forum: Server Platforms
---

### Post by jrtboht on 2011-02-14
I set up a home file server using [this ]("http://www.howtoforge.com/ubuntu-home-fileserver")tutorial.  Every works except it takes forever to open a file (maybe 40 seconds to open a 40k image).  I looked through the logs and found a lot of errors but I'm new to linux and not sure how to fix them.  Any help would be appreciated.

log.smbd

```
[2011/02/13 06:51:22, 0] printing/print_cups.c:cups_connect(69)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2011/02/13 06:51:22, 0] printing/print_cups.c:cups_connect(69)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2011/02/13 09:51:12, 0] printing/print_cups.c:cups_connect(69)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2011/02/13 09:51:12, 0] printing/print_cups.c:cups_connect(69)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2011/02/13 10:08:29, 0] printing/print_cups.c:cups_connect(69)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2011/02/13 10:08:29, 0] printing/print_cups.c:cups_connect(69)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2011/02/13 10:46:30, 0] printing/print_cups.c:cups_connect(69)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2011/02/13 10:46:30, 0] printing/print_cups.c:cups_connect(69)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2011/02/13 10:46:30, 0] printing/print_cups.c:cups_connect(69)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2011/02/13 10:46:30, 0] printing/print_cups.c:cups_connect(69)
```log.computername  (Partial)

```

[2011/02/08 14:20:16, 0] param/loadparm.c:widelinks_warning(5718)
  Share 'IPC$' has wide links and unix extensions enabled. These parameters are incompatible. Wide links will be disabled for this share.
[2011/02/08 14:20:16, 0] param/loadparm.c:widelinks_warning(5718)
  Share 'sdb1 public hard disk' has wide links and unix extensions enabled. These parameters are incompatible. Wide links will be disabled for this share.
[2011/02/08 14:20:16, 1] smbd/service.c:make_connection_snum(1060)
  laserengraver (192.168.1.47) connect to service sdb1 public hard disk initially as user nobody (uid=65534, gid=65534) (pid 6826)
[2011/02/08 14:20:56, 0] param/loadparm.c:widelinks_warning(5718)
  Share 'IPC$' has wide links and unix extensions enabled. These parameters are incompatible. Wide links will be disabled for this share.
[2011/02/08 14:22:49, 1] smbd/service.c:close_cnum(1257)
  laserengraver (192.168.1.47) closed connection to service sdb1 public hard disk
[2011/02/08 14:22:50, 0] param/loadparm.c:widelinks_warning(5718)
  Share 'IPC$' has wide links and unix extensions enabled. These parameters are incompatible. Wide links will be disabled for this share.
[2011/02/08 14:22:50, 0] param/loadparm.c:widelinks_warning(5718)
  Share 'sdb1 public hard disk' has wide links and unix extensions enabled. These parameters are incompatible. Wide links will be disabled for this share.
[2011/02/08 14:22:50, 1] smbd/service.c:make_connection_snum(1060)
  laserengraver (192.168.1.47) connect to service sdb1 public hard disk initially as user nobody (uid=65534, gid=65534) (pid 6826)
[2011/02/08 14:22:56, 0] param/loadparm.c:process_usershare_file(4610)
  process_usershare_file: stat of /var/lib/samba/usershares/sdb1 public hard dis failed. Permission denied
[2011/02/08 14:22:56, 0] param/loadparm.c:process_usershare_file(4610)
  process_usershare_file: stat of /var/lib/samba/usershares/sdb1 public hard dis failed. No such file or directory
[2011/02/08 14:22:56, 0] smbd/service.c:make_connection(1218)
  laserengraver (192.168.1.47) couldn't find service sdb1 public hard dis
[2011/02/08 14:22:56, 0] param/loadparm.c:process_usershare_file(4610)
  process_usershare_file: stat of /var/lib/samba/usershares/sdb1 public hard dis failed. No such file or directory
[2011/02/08 14:22:56, 0] smbd/service.c:make_connection(1218)
  laserengraver (192.168.1.47) couldn't find service sdb1 public hard dis
[2011/02/08 14:22:58, 0] param/loadparm.c:process_usershare_file(4610)
  process_usershare_file: stat of /var/lib/samba/usershares/sdb1 public hard dis failed. Permission denied
[2011/02/08 14:22:58, 0] param/loadparm.c:process_usershare_file(4610)
  process_usershare_file: stat of /var/lib/samba/usershares/sdb1 public hard dis failed. No such file or directory
[2011/02/08 14:22:58, 0] smbd/service.c:make_connection(1218)
  laserengraver (192.168.1.47) couldn't find service sdb1 public hard dis
[2011/02/08 14:22:58, 0] param/loadparm.c:process_usershare_file(4610)
  process_usershare_file: stat of /var/lib/samba/usershares/sdb1 public hard dis failed. No such file or directory
[2011/02/08 14:22:58, 0] smbd/service.c:make_connection(1218)
  laserengraver (192.168.1.47) couldn't find service sdb1 public hard dis
[2011/02/08 14:23:25, 1] smbd/service.c:close_cnum(1257)
  laserengraver (192.168.1.47) closed connection to service sdb1 public hard disk
[2011/02/08 14:23:55, 0] lib/util_sock.c:read_data(534)
  read_data: read failure for 4 bytes to client 192.168.1.47. Error = Connection reset by peer
[2011/02/08 14:25:00, 0] param/loadparm.c:widelinks_warning(5718)
  Share 'sdb1 public hard disk' has wide links and unix extensions enabled. These parameters are incompatible. Wide links will be disabled for this share.
[2011/02/08 14:25:00, 1] smbd/service.c:make_connection_snum(1060)
  laserengraver (192.168.1.47) connect to service sdb1 public hard disk initially as user nobody (uid=65534, gid=65534) (pid 6839)
[2011/02/08 14:25:01, 0] param/loadparm.c:widelinks_warning(5718)
```

---

