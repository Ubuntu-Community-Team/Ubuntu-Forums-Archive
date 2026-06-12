---
title: "Server 10.04 boot fail"
date: 2011-11-15
forum: Server Platforms
---

### Post by lire on 2011-11-15
Hi, everybody has to reboot their servers once in a while, and today after a reboot I found our fileserver's Ubuntu Server 10.04 wouldn't boot normally and falls with an error
> 
fsck from util-linux-ng 2.17.2
/dev/sda1: clean, 6975124/30400512 files, ..... blocks
init: portmap main process (691) terminated with status 2
init: portmap main process emded, respawning
init: statd pre-start process (716) terminated with status 2
init: rpc_pipefs pre-start process (717) terminated with status 32

After the error the system did nothing and never booted. I did not change anything prior to the reboot, nor did I install any updates.

Google told me these lines deal with some NFS error. I unplugged all the HDDs except the system one and used an external HDD box to connect to the system disc and comment all the lines in /etc/fstab file. The problem persisted.

Eventually I found a way to boot: after 10-15 minutes of the message's display the Ctrl+Alt+Del keys wouuld not reboot the system like right after the turning on, but instead would boot Ubuntu normally.

Please help me to find what is the problem, I now can gain access to any log or config. Thanks

---

### Post by Jonathan L on 2011-11-15
> **lire said:**
> Hi, everybody has to reboot their servers once in a while, and today after a reboot I found our fileserver's Ubuntu Server 10.04 wouldn't boot normally and falls with an error

After the error the system did nothing and never booted. I did not change anything prior to the reboot, nor did I install any updates.

Google told me these lines deal with some NFS error. I unplugged all the HDDs except the system one and used an external HDD box to connect to the system disc and comment all the lines in /etc/fstab file. The problem persisted.

Eventually I found a way to boot: after 10-15 minutes of the message's display the Ctrl+Alt+Del keys wouuld not reboot the system like right after the turning on, but instead would boot Ubuntu normally.

Please help me to find what is the problem, I now can gain access to any log or config. Thanks

Hi Lire

To me sounds like some hardware is starting to fail: _if_ nothing changed in the software, then something must have changed in the hardare.  Is the computer old?

What does this server normally do: you mention removing all the non system disks.

Can you see anything useful in /var/log/dmesg?  

If you suspect hardware, then a good thing to try is to cool the system down by leaving it off, box open, can of freezer spray if you have it.  Then see if things persist.

Let us know what you find in the logs.

Hope that gives you a starting point.

Kind regards,
Jonathan.

---

