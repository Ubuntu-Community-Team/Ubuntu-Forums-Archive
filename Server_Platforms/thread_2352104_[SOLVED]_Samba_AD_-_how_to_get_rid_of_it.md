---
title: "[SOLVED] Samba AD - how to get rid of it"
date: 2017-02-09
forum: Server Platforms
---

### Post by xdracco on 2017-02-09
Just updated to 16.10 and now Samba is giving me errors.

> [$:/etc/samba] # systemctl status samba-ad-dc.service&#9679; samba-ad-dc.service - Samba AD Daemon
   Loaded: loaded (/lib/systemd/system/samba-ad-dc.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Thu 2017-02-09 09:45:43 PST; 15s ago
     Docs: man:samba(8)
           man:samba(7)
           man:smb.conf(5)
  Process: 3613 ExecStart=/usr/sbin/samba $SAMBAOPTIONS (code=exited, status=1/FAILURE)
 Main PID: 3613 (code=exited, status=1/FAILURE)
   Status: "daemon failed to start: Samba failed to start services"

Feb 09 09:45:43 orion.xdracco.lan systemd[1]: Starting Samba AD Daemon...
Feb 09 09:45:43 orion.xdracco.lan systemd[1]: samba-ad-dc.service: Supervising process 3613 which is not our child. We'll most likely not notice when it exits.
Feb 09 09:45:43 orion.xdracco.lan systemd[1]: samba-ad-dc.service: Failed to parse ERRNO= field in notification message: -1073741796
Feb 09 09:45:43 orion.xdracco.lan systemd[1]: samba-ad-dc.service: Main process exited, code=exited, status=1/FAILURE
Feb 09 09:45:43 orion.xdracco.lan systemd[1]: Failed to start Samba AD Daemon.
Feb 09 09:45:43 orion.xdracco.lan systemd[1]: samba-ad-dc.service: Unit entered failed state.
Feb 09 09:45:43 orion.xdracco.lan systemd[1]: samba-ad-dc.service: Failed with result 'exit-code'.

I don't need Active directory, i don't know why Ubuntu decided to configure AD for me during the upgrade to 16.10 but i hope it doesn't happen again.

anyways, my quick fix was to comment out all of the following from /etc/samba/smb.conf:
```
/etc/init.d/samba-ad-dc start
```

so forums, how do i completely disable Samba's Active Directory? Or better, how do i just remove it (if possible)?

thanks

---

### Post by darkod on 2017-02-10
I think the first question should be in fact why did you upgrade a server to 16.10 which is non-LTS release and has very short support? If you have full backup from before the upgrade I would actually roll back.
Always use only LTS releases for servers, even for home servers. They have 5yrs support and are generally more stable.

The interim releases are more for testing.

As for your question, I'm no samba expert but I believe it installs with all services that are available. That doesn't mean that ubuntu or samba decided to install/configure AD for you. They would never do that unless you already had such config in your smb.conf.
The errors might be because samba got upgraded with an error or corrupted. Or simply because it's 16.10 and maybe some bug exists...

Probably purging and reinstalling samba will fix it, but you have to make sure you backup all settings first and know how to put them back after the purge.

---

### Post by xdracco on 2017-02-10
So, here's how I actually addressed the issue,,,, by commenting out samba-ad-ac:

```
#!/bin/sh

### BEGIN INIT INFO
# Provides:          samba
# Required-Start:
# Required-Stop:
# Default-Start:
# Default-Stop:
# Short-Description: ensure Samba daemons are started (nmbd, smbd and samba)
# Description: Starts Samba, a Windows AD and SMB/CIFS fileserver for UNIX
### END INIT INFO


set -e


# start nmbd, smbd and samba-ad-dc unconditionally
# the init scripts themselves check if they are needed or not
case $1 in
    start)
        /etc/init.d/nmbd start
        /etc/init.d/smbd start
#        /etc/init.d/samba-ad-dc start
        ;;
    stop)
#        /etc/init.d/samba-ad-dc stop
        /etc/init.d/smbd stop
        /etc/init.d/nmbd stop
        ;;
    reload)
        /etc/init.d/smbd reload
        ;;
    restart|force-reload)
        /etc/init.d/nmbd "$1"
        /etc/init.d/smbd "$1"
#        /etc/init.d/samba-ad-dc "$1"
        ;;
    status)
        status=0
        NMBD_DISABLED=`testparm -s --parameter-name='disable netbios' 2>/dev/null || true`
        SERVER_ROLE=`samba-tool testparm --parameter-name="server role"  2>/dev/null | tail -1 || true`
        if [ "$SERVER_ROLE" != "active directory domain controller" ]; then
            if [ "$NMBD_DISABLED" != "Yes" ]; then
                /etc/init.d/nmbd status || status=$?
            fi
            /etc/init.d/smbd status || status=$?
        else
            /etc/init.d/samba-ad-dc status || status=$?
        fi
        exit $status
        ;;
    *)
        echo "Usage: /etc/init.d/samba {start|stop|reload|restart|force-reload|status}"
        exit 1
        ;;
esac
```

suggesting to roll back or to purge samba was honestly... absurd advice.

thanks anyways.

---

### Post by LHammonds on 2017-02-10
> **xdracco said:**
> 
So, here's how I actually addressed the issue,,,, by commenting out samba-ad-ac:

Hmmm...that entire case section isn't part of a normal smb.conf file.

> **xdracco said:**
> 
suggesting to roll back or to purge samba was honestly... absurd advice.

No, not absurd at all.  Its the same advice I was about to suggest if a re-load of samba didn't fix your problem but seeing how you have a customized config file, the problem would likely just come back again if you re-added the same config file.

Install a new 16.10 server, install samba and compare the differences in your config to a default copy and only enable/use what you need.  If you don't know why something exists in your current config, don't include it in the new one.

The 1st step when I install samba is to make backup copies of the config files before editing them.

Even though we get an option to upgrade a server in-place after the 1st point release, I never use it.  I only create new servers and backup/restore to them for my upgrade process because that always gives me an easy rollback by switching an IP address and I can test if the applications work.  Just because the OS can do an upgrade in-place does not mean that applications installed on them can too...especially if their are newer versions with different config files.

LHammonds

---

### Post by xdracco on 2017-02-10
thanks for your point of view.

---

