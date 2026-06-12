---
title: "Getting &quot;Kernal driver not installed (rc=1908)"
date: 2014-01-27
forum: Virtualisation
---

### Post by free_bird573 on 2014-01-27
I know someone has posted this error and their issue was resolved, but I am using the newest VBox with Ubuntu version 12.10 and getting the same error.

OS:  Linux 12.10
Virtual Box:  4.3.6-91406
5 G of Ram
XP SP3 is what I'm trying to run

I have tried 4.2.20 and I get the same error.

I ran the suggested command as root user:  /etc/init.d/vboxdrv setup

Results:  Stopping VirtualBox kernel modules ...done.
Recompiling VirtualBox kernel modules ...failed!
  (Look at /var/log/vbox-install.log to find out what went wrong)

Don't know how to find /var/log/vbox-install.log

---

### Post by QIII on 2014-01-28
Hello!

Please use the terminal and execute the following command

```
cat /var/log/vbox-install.log
```

Copy the results by highlighting the text in the terminal and pressing cntl+shift+C.

Paste the results back here [I][B]between code tags.

[/B][/I]To use code tags - 

If you are using New Reply button - highlight text and use the # button in the text box header.

If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by free_bird573 on 2014-01-28
Thankyou for responding, hope you can help

```

freebird573@freebird573-TA790GX-128M:~$ cat /var/log/vbox-install.log
Makefile:183: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Stop.
Makefile:183: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Stop.
freebird573@freebird573-TA790GX-128M:~$ 

```

---

