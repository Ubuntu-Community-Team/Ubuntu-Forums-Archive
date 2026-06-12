---
title: "how to use telinit"
date: 2008-03-10
forum: Server Platforms
---

### Post by rperrones on 2008-03-10
Hi,

how to force runlevel 1 in ubuntu 7.10 ? When i try  "telinit 1" in console, the system  reboot but all services are started normally, including Gnome Graphical interface. I need to run only basic services in single user mode.

Thanks
Ricardo

---

### Post by astrotech226 on 2008-03-11
That should work for you.  There's two other ways you can try.  From the command line, try:

```
init 1
```

You could also reboot the computer into single user mode.  When it boots up, interrupt grub (I think it's escape).  Highlight the kernel you want to boot and type "e" for edit.  You then need to highlight line that starts with "kernel" and press "e" again.  Go to the end of line and append a "1" or the word "single".  Press "b" to boot it and it should put you into single user mode.

---

### Post by MJN on 2008-03-11
> **rperrones said:**
> Hi,
 
how to force runlevel 1 in ubuntu 7.10 ? When i try "telinit 1" in console, the system reboot but all services are started normally,
 
The system should not have rebooted. As you were expecting it should have entered single-user mode, and rebooting is not required to do this.
 
Without modifying the grub config (either in menu.1st or manually as Astrotech mentions) the reboot will have entered a multi-user mode, hence the full services.
 
The question is, why did single-user mode reboot? What do you have in /etc/rc1.d/ ? Have you played around with anything that might be remotely connected to runlevel operation?
 
Mathew

---

### Post by rperrones on 2008-03-11
Sorry,

but the boot problem occurred by one remote user that was logged and executed reboot command at the same moment that the telinit command. Moreover, a grub's vga parameter was wrong and the system properly choosed runlevel 2 to continue and starting all services ignoring any other paramter

Thanks
Ricardo

---

