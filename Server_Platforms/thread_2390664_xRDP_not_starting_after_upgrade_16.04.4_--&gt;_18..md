---
title: "xRDP not starting after upgrade 16.04.4 --&gt; 18.04"
date: 2018-05-01
forum: Server Platforms
---

### Post by panja on 2018-05-01
Today I upgraded my Ubuntu VPS from 16.04.4 to 18.04.
Everything went smooth except I cannot connect to RDP anymore.
Please let's not start a flamewar why I use RDP to access an Ubuntu (server) GUI. :lolflag:

I had xRDP running with xfce4.
When I start the service I get this in return:

```

systemctl status xrdp.service

&#9679; xrdp.service - xrdp daemon
   Loaded: loaded (/lib/systemd/system/xrdp.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Tue 2018-05-01 12:05:16 CEST; 6min ago
     Docs: man:xrdp(8)
           man:xrdp.ini(5)
  Process: 8192 ExecStart=/usr/sbin/xrdp $XRDP_OPTIONS (code=exited, status=1/FAILURE)
  Process: 8177 ExecStartPre=/bin/sh /usr/share/xrdp/socksetup (code=exited, status=0/SUCCESS)


May 01 12:05:16 ubuntu-01 systemd[1]: Starting xrdp daemon...
May 01 12:05:16 ubuntu-01 systemd[1]: xrdp.service: Control process exited, code=exited status=1
May 01 12:05:16 ubuntu-01 systemd[1]: xrdp.service: Failed with result 'exit-code'.
May 01 12:05:16 ubuntu-01 systemd[1]: Failed to start xrdp daemon.

```

Any one have a clue how to fix this?

:confused:

---

### Post by LHammonds on 2018-05-01
OS upgrades are designed to upgrade the OS.  Applications are a whole other animal.  Dependencies may have changed, new versions of software might have new requirements, old software may not yet work on the new platform, etc.

Check to see how you would install xRDP today on 18.04 and see if this process differs from 16.04 (like different requirements, etc.)

LHammonds

---

### Post by panja on 2018-05-01
Yes, I get that of course.
I was just hoping someone here had the same problem and could point me to the right direction...

---

### Post by panja on 2018-05-02
Fixed it by completely removing xRDP (and re-installing).

```

sudo apt remove xrdp
sudo apt purge xrdp
sudo apt autoremove
sudo reboot

```

Also changed vnc4server for tightvnc-server.
Probably not needed but wanted to do that for a long time, finally did it. :)

---

### Post by LHammonds on 2018-05-02
The purge would have removed configuration files.  Did you keep a copy to see what the new version looks like?  There might be new required settings to make it work with the new version.

---

### Post by panja on 2018-05-03
To be honest I thought about that after I removed everything, after the purge. ;-)
So no unfortunately I did not.

---

