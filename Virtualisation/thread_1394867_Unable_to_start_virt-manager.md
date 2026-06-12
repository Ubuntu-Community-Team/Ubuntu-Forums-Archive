---
title: "Unable to start virt-manager"
date: 2010-01-31
forum: Virtualisation
---

### Post by satimis on 2010-01-31
Hi folks,

KVM
Virt-manager
host - Debian 5.0

Starting;

Gnome
Applications -> System Tools - Virtual Machine Manager

popup following error;```

Traceback (most recent call last):
  File "/usr/share/virt-manager/virt-manager.py", line 346, in <module>
    main()
  File "/usr/share/virt-manager/virt-manager.py", line 248, in main
    setup_logging()
  File "/usr/share/virt-manager/virt-manager.py", line 124, in setup_logging
    os.mkdir(vm_dir)
OSError: [Errno 17] File exists: '/home/satimis/.virt-manager'

```

~$ ls -al /home/satimis/ | grep virt-manager```

drwxr-xr-x  2 root    root           4096 2009-05-31 06:11 .virt-manager

```


$ mv /home/satimis/.virt-manager /home/satimis/.virt-manager.old01

Restart
Applications -> System Tools - Virtual Machine Manager

starting GUI virt-manager but without asking for login as root

$ ls -al /home/satimis/ | grep virt-manager```

drwxr-xr-x  2 satimis  satimis        4096 2010-01-31 10:00 .virt-manager

```


If changing the owner by running
$ sudo chown root:root /home/satimis/.virt-manager

GUI virt-manage can't start with abovementioned warning pop.


Please advise how to fix this problem.  I expect with root-password to start GUI virt-manager

TIA


B.R.
satimis

---

### Post by gbear14275 on 2010-05-31
you ever resolve this?  Running into the same problem myself...

---

### Post by satimis on 2010-05-31
> **gbear14275 said:**
> you ever resolve this?  Running into the same problem myself...

Hi,

I sorted out my problem already.

The host-Debian 5.0 has its kernel upgraded lately.  I booted it to its previous kernel.  All Ubuntu guests revived.  Then I rebooted the virtual machine to the new kernel of Debian 5.0.  Everything became normal.  I can't explain why?  Also I don't know Why?

Now all guests of KVM are working normally.

B.R.
satimis

---

