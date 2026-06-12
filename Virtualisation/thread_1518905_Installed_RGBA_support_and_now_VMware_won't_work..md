---
title: "Installed RGBA support and now VMware won't work."
date: 2010-06-27
forum: Virtualisation
---

### Post by Nugar on 2010-06-27
Hi all,

Yesterday, I installed RGBA support to Ubuntu 10.04 using the instructions found [here ]("http://www.ghacks.net/2010/06/12/enable-rgba-support-in-ubuntu/")

It works, looks good, etc. But when I launch VMware, and try to boot any of the virtual machines I have, I just get a transparent window and can't boot the virtual machine.

Any pointers on how to solve this?

I'm using an NVIDIA card with the 195.36.24 driver, Ubuntu 10.04 64-bit, VMware 7.1

Thanks in advance,

---

### Post by Nohajc on 2010-06-30
I was dealing with the same problem today and I was able to solve it by editing **.profile** in my home directory.

All you have to do is add this code at the end of the file:
```
export GTK_MODULES=rgba
export GTK_RGBA_APPS=allbut:firefox-bin:vmware:vmplayer:gnome-mplayer:totem:soffice:amule:me-tv
```It is basically a list which specifies where to disable RGBA. However, when I added vmware only, Firefox stopped working, so I had to add it as well (along with OpenOffice etc...). 
It doesn't matter though, since firefox wasn't transparent anyway.

---

### Post by Nugar on 2010-06-30
Thanks Nohajc, I'll try that as soon as I get to my PC tonight and reprot back.

Cheers,

---

### Post by Nugar on 2010-07-01
No dice. Now VMware won't even start. Well, I did upgrade the kernel since there was an upgrade, but after rebooting and launching vmware, it crashed everytime.

Good thing that VirtualBox now supports more than one screen easily!

Cheers,

---

### Post by Nohajc on 2010-07-02
That's odd. I have pretty much the same configuration (VMware 7.1, Ubuntu 10.04 x64...)
When you run vmware in console what errors does it report? Can you post the output? I'm no expert but maybe someone else could help with more information.

Anyway, since my RGBA install I've had trouble with a few other programs too. Now I have to add **amule** and **me-tv** to the list.

---

### Post by Nugar on 2010-07-02
Sure, here it is:


progname=vmware-modconfig; RGBA=on
Logging to /tmp/vmware-nugar/setup-19413.log
ERROR: modinfo: could not find module vmmon
ERROR: modinfo: could not find module vmnet
ERROR: modinfo: could not find module vmblock
ERROR: modinfo: could not find module vmci
ERROR: modinfo: could not find module vsock
ERROR: modinfo: could not find module vmmon
ERROR: modinfo: could not find module vmnet
ERROR: modinfo: could not find module vmblock
ERROR: modinfo: could not find module vmci
ERROR: modinfo: could not find module vsock
ERROR: modinfo: could not find module vmmon
ERROR: modinfo: could not find module vmnet
ERROR: modinfo: could not find module vmblock
ERROR: modinfo: could not find module vmci
ERROR: modinfo: could not find module vsock
ERROR: modinfo: could not find module vmmon
ERROR: modinfo: could not find module vmnet
ERROR: modinfo: could not find module vmblock
ERROR: modinfo: could not find module vmci
ERROR: modinfo: could not find module vsock
ERROR: modinfo: could not find module vmmon
ERROR: modinfo: could not find module vmnet
ERROR: modinfo: could not find module vmblock
ERROR: modinfo: could not find module vmci
ERROR: modinfo: could not find module vsock

progname=vmware-gksu; RGBA=on
The program 'vmware-gksu' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
  (Details: serial 566 error_code 3 request_code 2 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

---

