---
title: "sudo update-grub fails"
date: 2024-03-27
forum: Ubuntu Development Version
---

### Post by ajgreeny on 2024-03-27
I have just installed **Xubuntu 24.04 LTS "Noble Numbat" - Daily amd64 (20240326)** then edited the grub config and run **sudo update-grub** but it is failing with output
```
andrew@Xubu26Mar:~$ sudo update-grub
[sudo] password for andrew: 
Sourcing file `/etc/default/grub'
/usr/sbin/grub-mkconfig: 33: /etc/default/grub: want: not found

```
I rebooted and tried again but no go!
Here's the content of **/etc/default/grub**

```
andrew@Xubu26Mar:~$ cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=2
GRUB_DISTRIBUTOR="Xubuntu26March"`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# If your computer has multiple operating systems installed, then you
# probably want to run os-prober. However, if your computer is a host
# for guest OSes installed via LVM or raw disk devices, running
# os-prober can cause damage to those guest OSes as it mounts
# filesystems to look for things.
#GRUB_DISABLE_OS_PROBER=false

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

---

### Post by jeremy31 on 2024-03-27
What happens if you delete the ` from the end of```
GRUB_DISTRIBUTOR="Xubuntu26March"`
```

---

### Post by ajgreeny on 2024-03-27
Oh gosh!!!

I had not even noticed that the ' was left behind after editing the file.
I'm not on he machine at the moment but will cerainly check tomorrow at some point and report back.

Thanks for noticing that error; I hope it is the answer!

---

### Post by ajgreeny on 2024-03-28
I realised after saying I would report back on this that I had already deleted the VM  of Xubuntu that had this problem.
Its successor installed this evening, 28 March from an iso also dated 28 March is working as expected.

However, when is the "quiet splash" option going to be the default?
All iso archives of Xubuntu at present don't have that enabled so it shows the scrolling boot text until that /etc/default/grub file is edited and **sudo update-grub** is run.
You still end up with the full GUI but it's still unnecessary and a bit annoying!

---

### Post by dajonaga on 2024-03-31
Please update the OP title with a [SOLVED] prefix.

Thanks!

---

### Post by ajgreeny on 2024-03-31
Please do not attempt to moderate posts or threads on Ububtu Forum; leave it to staff only to do this!

And no!
I shall not mark this thread as solved as I still don't know if it has been.

As I said above, I deleted the VM of that system before I could test it so a solution is not yet possible.
Having edited that file in another system where the update-grub worked as expected, adding the extra ' after the required " of my DISTRIBUTION edit I did not see the problem repeated so I suspect some other cause yet to be ascertained.

---

### Post by dajonaga on 2024-03-31
Fair enough... but I wasn't trying to moderate you...
I was looking for info about something related to GRUB and your last post reads to me as "oops... now it is working"... a waste of time... and now again.... a waste of my time... take care and have a good one tho...

---

### Post by MAFoElffen on 2024-03-31
"*Patience is truly a virtue.*" 

Do not ask for things to test that, or you may get examples to practice it... 

I do understand. I try to err towards being courteous and empathetic. We all live here together.

---

