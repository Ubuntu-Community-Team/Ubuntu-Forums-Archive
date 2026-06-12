---
title: "macOS can't connect to samba share"
date: 2017-05-30
forum: Server Platforms
---

### Post by mattiash on 2017-05-30
I have a 16.04 ubuntu server with a RAID10 storage, I got a samba group with all the users and the share is accessible from Windows10, but not from macOS 10.12.
I get all the way to what share I want to put on the Desktop, I choose the share and then after a small while I get an error stating that something went wrong.

This is what I find in the samba log file:
```

[COLOR=#4D2F2D][FONT=Courier][2017/05/30 22:41:30.510945,  0] ../source3/smbd/service.c:710(make_connection_snum)[/FONT][/COLOR]
[COLOR=#4D2F2D][FONT=Courier]  canonicalize_connect_path failed for service meteorpr, path /storage/meteorpr[/FONT][/COLOR]
[COLOR=#4D2F2D][FONT=Courier][2017/05/30 22:41:30.519086,  0] ../source3/smbd/service.c:710(make_connection_snum)[/FONT][/COLOR]
[COLOR=#4D2F2D][FONT=Courier]  canonicalize_connect_path failed for service meteorpr, path /storage/meteorpr[/FONT][/COLOR]
[COLOR=#4D2F2D][FONT=Courier][2017/05/30 22:41:33.906725,  0] ../source3/param/loadparm.c:2988(check_usershare_stat)[/FONT][/COLOR]
[COLOR=#4D2F2D][FONT=Courier]  check_usershare_stat: file /var/lib/samba/usershares/ owned by uid 0 is not a regular file[/FONT][/COLOR]

```

A bit new to samba on Ubuntu and a bit tired. :)

---

