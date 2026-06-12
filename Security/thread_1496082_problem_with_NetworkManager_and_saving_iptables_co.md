---
title: "problem with NetworkManager and saving iptables counters"
date: 2010-05-28
forum: Security
---

### Post by andrewthomas on 2010-05-28
I am trying to use a /etc/NetworkManager/dispatcher.d/ script to restore the iptables rules **and counters** on boot and save the rules and counters on shutdown.  The rules load fine, but the counters were reset each reboot.  This is the script that I am using (from [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo))
```
#!/bin/sh -e
if [ -x /usr/bin/logger ]; then
        LOGGER="/usr/bin/logger -s -p daemon.info -t FirewallHandler"
else
        LOGGER=echo
fi
case "$2" in
        up)
        if [ ! -r /etc/iptables.up.rules ]; then
                        ${LOGGER} "No iptables rules exist to restore."
                        return
                fi
                if [ ! -x /sbin/iptables-restore ]; then
                        ${LOGGER} "No program exists to restore iptables rules."
                        return
                fi
        ${LOGGER}  "02iptables is Restoring iptables rules"
                /sbin/iptables-restore -c < /etc/iptables.up.rules
                ;;
    down)
        if [ ! -x /sbin/iptables-save ]; then
                        ${LOGGER} "No program exists to save iptables rules."
                        return
                fi
        ${LOGGER} "02iptables is Saving iptables rules"
                /sbin/iptables-save -c > /etc/iptables.up.rules
                ;;
    *)
        ;;
esac
```NetworkManager calls the script at boot, but not at shutdown.
In order to save my counters, I have had to add the necessary code to /etc/init.d/network-manager
```
  stop)
   ** iptables-save -c > /etc/iptables.up.rules**
    log_daemon_msg "Stopping $DESC" "$NAME"
    d_stop
    case "$?" in
        0) log_end_msg 0 ;;
        1) log_progress_msg "already stopped"
           log_end_msg 0 ;;
        *) log_end_msg 1 ;;
    esac
```This is certainly not something that I like.  It works but I don't understand why the script alone is not enough.

---

