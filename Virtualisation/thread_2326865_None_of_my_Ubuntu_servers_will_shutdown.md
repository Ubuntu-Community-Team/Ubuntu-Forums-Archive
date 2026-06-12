---
title: "None of my Ubuntu servers will shutdown"
date: 2016-06-05
forum: Virtualisation
---

### Post by puil on 2016-06-05
I have about 10 Ubuntu servers, 14.04.4 LTS.
They are running under VMware Esxi 5.5.

Years ago, I could gracefully shutdown the servers.  Then, after an unknown upgrade, they won't shutdown any longer.

# shutdown -h now

will result in the server starting to shutdown, then it gets to this point:
```
[FONT=Calibri]
* Stopping System V runlevel      compatibilty [ OK ][/FONT]
Rcpbind: rcpbind terminating on signal. Restart with "rcpbind -w"

```
That's it.  It just hangs there forever.

I tried disabling acpi by editing /etc/default/grub and setting the line GRUB_CMDLINE_LINUX_DEFAULT to
[FONT=Calibri]"pci=noacpi acpi=off noapic"
[/FONT]
  [FONT=Calibri]# update-grub

This had no effect.

The only way I can reboot my servers is to do a "power off", which I really don't want to do.  And again, this problem is on ALL my servers.
Any suggestions?
[/FONT]

---

### Post by Habitual on 2016-06-06
does 
```
sudo halt 
```
shut any of the affected hosts down?

---

### Post by houstonbofh on 2016-06-06
You are doing a shutdown with "halt" and you want a shutdown with "power off."  "sudo shutdown -P now" will work.

---

### Post by puil on 2016-06-06
I tried "sudo halt" and "sudo shutdown -P now".

No change.  It continues to run.  The last line displayed is "rpcbind terminating on signal."

---

### Post by puil on 2016-06-06
I uninstalled rpcbind, but that didn't help.
It just hangs on "* Stopping System V runlevel compatibility  [ OK ]"

---

### Post by MAFoElffen on 2016-06-07
I noticed this 1st on vShere: on some Ubuntu Servers. then on a Centos server. The Centos server actually came up with a suggestion that worked for me
```

sudo shutdown -hP now

```
Just using the "-h" says halt but leave the final decision to the server by the run state set in variables to:
> 
"...with the choice as to which left up to the system"

Halt stopped working for me a few Ubuntu versions ago for me (with frustration, the meaning for me changed to "HANG"), so I went to "P" ... but now, with ESXi, well...

"-P" says to poweroff, but it recently stopped working (for me) consistently with Linux VM guest's running under ESXi.

"-hP" says to explicitly halt, but instead of leaving the secondary following decision to the system, to then poweroff. I can't say it will work 100% for everyone, but at least that works for me.

---

