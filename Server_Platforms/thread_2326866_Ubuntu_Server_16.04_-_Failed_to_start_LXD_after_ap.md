---
title: "Ubuntu Server 16.04 - Failed to start LXD after apt-get dist-upgrade (HELP!)"
date: 2016-06-05
forum: Server Platforms
---

### Post by Freddy08 on 2016-06-05
Hi,

I'm trying to update an instance running Ubuntu 16.04 LTS (amd64 xenial image built on 2016-05-16) over GoogleCloud.

There are no issues at all getting it to boot and it runs flawless (was). However when I run $ sudo apt-get update && sudo apt-get dist-upgrade, it trows an error and fails at the LSD service:

I am aware already and understand that Ubuntu released a new LXD package on May30 addressing two security issues.

Is there anything I need to do to my 16.04 instance to get the LXD container to load at boot? Be error free in other words

Error trace:

```
lxd-containers.service - LXD - container startup/shutdown
   Loaded: loaded (/lib/systemd/system/lxd-containers.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Sun 2016-06-05 18:20:04 UTC; 35s ago
     Docs: man:lxd(1)
  Process: 9794 ExecStop=/usr/lib/lxd/shutdown (code=exited, status=0/SUCCESS)
  Process: 9800 ExecStart=/usr/bin/lxd activateifneeded (code=exited, status=1/FAILURE)
 Main PID: 9800 (code=exited, status=1/FAILURE)

Jun 05 18:20:04 mydomain.com systemd[1]: Starting LXD - container startup/shutdown...
Jun 05 18:20:04 mydomain.com lxd[9800]: error: open /var/lib/lxd/containers: no such file or directory
Jun 05 18:20:04 mydomain.com systemd[1]: lxd-containers.service: Main process exited, code=exited, status=1/FAILURE
Jun 05 18:20:04 mydomain.com systemd[1]: Failed to start LXD - container startup/shutdown.
Jun 05 18:20:04 mydomain.com systemd[1]: lxd-containers.service: Unit entered failed state.
Jun 05 18:20:04 mydomain.com systemd[1]: lxd-containers.service: Failed with result 'exit-code'.
```

Grateful for any advice or heads up RE where to start looking

F.

This is what happen when I $ sudo service lxd restart

```
Jun  5 18:58:20 mydomain systemd[1]: Stopped LXD - main daemon.
Jun  5 18:58:20 mydomain systemd[1]: Starting LXD - network bridge...
Jun  5 18:58:20 mydomain kernel: [ 2417.134306] bridge: automatic filtering via arp/ip/ip6tables has been deprecated. Update your scripts to load br_netfilter if you need this.
Jun  5 18:58:20 mydomain systemd-udevd[14490]: Could not generate persistent MAC address for lxdbr0: No such file or directory
Jun  5 18:58:20 mydomain systemd[1]: Started LXD - network bridge.
Jun  5 18:58:20 mydomain systemd[1]: Starting LXD - main daemon...
Jun  5 18:58:20 mydomain kernel: [ 2417.198978] audit_printk_skb: 15 callbacks suppressed
Jun  5 18:58:20 mydomain kernel: [ 2417.198983] audit: type=1400 audit(1465153100.737:30): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/bin/lx$
Jun  5 18:58:20 mydomain kernel: [ 2417.203806] audit: type=1400 audit(1465153100.741:31): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="lxc-contain$
Jun  5 18:58:20 mydomain kernel: [ 2417.203816] audit: type=1400 audit(1465153100.741:32): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="lxc-contain$
Jun  5 18:58:20 mydomain kernel: [ 2417.203822] audit: type=1400 audit(1465153100.741:33): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="lxc-contain$
Jun  5 18:58:20 mydomain kernel: [ 2417.203826] audit: type=1400 audit(1465153100.741:34): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="lxc-contain$
Jun  5 18:58:20 mydomain lxd[14551]: t=2016-06-05T18:58:20+0000 lvl=warn msg="CGroup memory swap accounting is disabled, swap limits will be ignored."
Jun  5 18:58:22 mydomain ntpd[1513]: Listen normally on 6 lxdbr0 [fe80::bc9c:eaff:fedc:f874%3]:123
Jun  5 18:58:22 mydomain ntpd[1513]: Listen normally on 7 lxdbr0 [fe80::1%3]:123
Jun  5 18:58:22 mydomain ntpd[1513]: new interface(s) found: waking up resolver
Jun  5 18:58:23 mydomain systemd[1]: Started LXD - main daemon.
```

```
$ systemctl status lxd-containers.service

lxd-containers.service - LXD - container startup/shutdown
   Loaded: loaded (/lib/systemd/system/lxd-containers.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Sun 2016-06-05 18:20:04 UTC; 38min ago
     Docs: man:lxd(1)
  Process: 9794 ExecStop=/usr/lib/lxd/shutdown (code=exited, status=0/SUCCESS)
  Process: 9800 ExecStart=/usr/bin/lxd activateifneeded (code=exited, status=1/FAILURE)
 Main PID: 9800 (code=exited, status=1/FAILURE)

Jun 05 18:20:04 mydomain .com systemd[1]: Starting LXD - container startup/shutdown...
Jun 05 18:20:04 mydomain .com lxd[9800]: error: open /var/lib/lxd/containers: no such file or directory
Jun 05 18:20:04 mydomain .com systemd[1]: lxd-containers.service: Main process exited, code=exited, status=1/FAILURE
Jun 05 18:20:04 mydomain .com systemd[1]: Failed to start LXD - container startup/shutdown.
Jun 05 18:20:04 mydomain .com systemd[1]: lxd-containers.service: Unit entered failed state.
Jun 05 18:20:04 mydomain .com systemd[1]: lxd-containers.service: Failed with result 'exit-code'.
```

---

### Post by howefield on 2016-06-05
Thread moved to the "*Server Platforms*" forum for a better fit.

---

### Post by Freddy08 on 2016-06-05
thanks, apologies for initially posting this in the wrong place

(and thanks for the quick edit!)

---

### Post by Freddy08 on 2016-06-05
Just a quick update; you need to restart the instance 'twice' and the service finally kicks in. Won't work if you reboot only once. Go figure - love computers that self-fix xxx

oddities....

[I]softerroot@mydomain:~**$ systemctl status lxd-containers.service**
&#9679; lxd-containers.service - LXD - container startup/shutdown
   Loaded: loaded (/lib/systemd/system/lxd-containers.service; enabled; vendor preset: enabled)
   Active: active (exited) since Mon 2016-06-06 03:21:12 CST; 11min ago
     Docs: man:lxd(1)
  Process: 1006 ExecStart=/usr/bin/lxd activateifneeded (code=exited, status=0/SUCCESS)
 Main PID: 1006 (code=exited, status=0/SUCCESS)
    Tasks: 0
   Memory: 0B
      CPU: 0
   CGroup: /system.slice/lxd-containers.service

Jun 06 03:21:12 mydomain.com systemd[1]: Starting LXD - container startup/shutdown...
Jun 06 03:21:12 mydomain.com systemd[1]: Started LXD - container startup/shutdown.[/I]

---

### Post by Freddy08 on 2016-06-06
^ Slight correction:

After apt-get dist-upgrade:[I]

## LXD service needs to be restarted using the root account > then reboot[/I]
$ sudo su
$ service lxd restart
$ reboot

*## check if service is up*
$ systemctl status lxd-containers.service

* all should be back to normal - the update adds up a new bri interface btw, not sure why loll

---

