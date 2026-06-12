---
title: "VMWare automatically start at boot?"
date: 2008-02-05
forum: Virtualisation
---

### Post by loopjeremyloop on 2008-02-05
Can I get VMWare Server running automatically at bootup?  Ideally, I'd like to power on a machine as soon as possible in case of a reboot and with no user intervention.

Any ideas here?

---

### Post by luisromangz on 2008-02-05
You can set up the login manager to log a user automatically, and in this user session's start launch VMware. You should check if VMware is able to launch a given virtual machine at the program's launch.

---

### Post by loopjeremyloop on 2008-02-05
> **luisromangz said:**
> You can set up the login manager to log a user automatically, and in this user session's start launch VMware. You should check if VMware is able to launch a given virtual machine at the program's launch.

eeek... for security purposes, I'm not too keen on doing the auto-login.  
I'm still looking into the other.

---

### Post by darkkith on 2008-02-05
You can start a vmware image onboot via crontab:

```

crontab -e

```

Then add the necessary entry:
```

@reboot  /usr/bin/vmware-cmd "/path/to/my.vmx" start

```

---

### Post by loopjeremyloop on 2008-02-06
AWESOME.  I just added the line, and I'll be testing its function in a bit.  Thank you!!

---

### Post by coolnezz on 2009-10-23
cool.
how can you start it in full screen mode?
tnx.

---

### Post by jatatar on 2011-02-04
Seems like cheating, but all vmware workstations (7.1 included) come with CLI-interface installed.

test run with:
```
vmrun start [path to *.vmx] nogui
```
where "path to .vmx" is vm you want to run. If it works add it to Gnome startup applications.

Computer > Control Center > Startup Applications (in SUSE SLED Menu) 

I use Gnome in openSUSE 11.3 (Ubuntu has similar route to startup applications)!!!

I prefer nogui, just loads and is put in system tray.  Play around with it, the cli can even be called up from ssh too! Not sure how to start multiple files, suppose you could add multiple startup entries.  

[http://www.vmware.com/pdf/vix162_vmrun_command.pdf]("http://www.vmware.com/pdf/vix162_vmrun_command.pdf")

---

### Post by CharlesA on 2011-02-04
Old thread is old.

Closed.

---

