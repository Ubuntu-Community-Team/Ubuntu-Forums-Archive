---
title: "vmware-view on Ubuntu 16.04"
date: 2016-04-27
forum: Virtualisation
---

### Post by tony-sales on 2016-04-27
Just upgraded to 16.04 and found there is no vmware-view package available in the repositories! I need this for work so installed it from the vmware website, but I can only get it to launch from a terminal by typing vmware-view. I have tried creating launchers in a variety of ways but they don't work :confused: nothing happens - unless I use the command: gnome-terminal -e vmware-view - which opens a terminal first then vmware-view. Why won't the launcher work when the same command runs from command line? Do I need to configure something so unity can launch a gui app? I can also launch it using Alt+F2 but there must be a simple way to create a unity launcher...

Any suggestions gratefully accepted.

drbongo :cool:

---

### Post by slickymaster on 2016-04-27
*Thread moved to **Virtualisation**.*

---

### Post by tony-sales on 2016-04-28
Solved - the .desktop file created automatically by locking the icon to the unity launcher did not contain the Terminal=false line - after adding this the launcher worked fine :)

---

### Post by michiel-nass on 2016-05-20
Did you manage to get Horizon View Client working on 16.04 LTS x64?

Just curious cause I'm having troubles on a fresh install (client installed flawlessly, stopped working after one succesfull session)

---

### Post by Bob_Swift on 2016-06-02
I would be very interested in knowing the resolution to this. Which version did you install and where from?

There isn't any vmware-view-client package in 16.04, I'm not sure why?

Thanks

---

### Post by michiel-nass on 2016-06-16
This is how i installed 64 bit version:

1) Download client from from [https://www.vmware.com/go/viewclients](https://www.vmware.com/go/viewclients)

2) Uninstall previous version
   Open a Terminal window
   Change directories to the directory that contains the installer file
   Run the installer command with the -u  option:

```

sudo ./VMware-Horizon-Client-4.5.0-5650368.x64.bundle -u vmware-horizon-client

```


3) Install using Terminal:

```

cd Downloads
chmod +x VMware-Horizon-Client-4.6.0-6617224.x64.bundle        
gksudo ./VMware-Horizon-Client-4.6.0-6617224.x64.bundle

```

4) Check for missing requirements

```

ldd /usr/lib/vmware/view/bin/vmware-view                                                                                                                                                                                                                                                                                           

```                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
5) Add missing (install packet and creat symlinks)

Example:
when missing libssl.so.1.0.2 make a soft link:
```

sudo ln -s /lib/x86_64-linux-gnu/libssl.so.1.0.0 /lib/x86_64-linux-gnu/libssl.so.1.0.2

```

6) Optional: Install FreeRDP
```

sudo apt-get install freerdp-x11

```

---

### Post by ABPeed on 2016-08-09
I had the same issue (flawless install, only one successful session); I was able to fix it by adding  /usr/lib/vmware to /etc/ld.so.conf.d/libc.conf and then running ldconfig. [Both of these steps require sudo.]

---

### Post by alan-b-goldblatt on 2016-10-18
I was still having trouble with vmware not finding libudev.so.0 -- the symlink was not pointing to anything valid.   It turns out that on Mint, at least, there is a 64 bit version, libudev.so.1.6.4  So, linking it this way: "sudo ln -sf libudev.so.1.6.4 libudev.so.0" solved the problem.

---

### Post by vassil-peytchev on 2016-12-29
Just a quick note (to myself mostly) - installed the 64-bit version 4.3 on Ubuntu 14.04 LTS. All I needed was the symlink

sudo ln -sf /lib/x86_64-linux-gnu/libudev.so.1.3.5 /lib/x86_64-linux-gnu/libudev.so.0

There was no need to install any i386 libraries.

---

### Post by vishnuvathsan on 2017-02-12
> **vassil-peytchev said:**
> Just a quick note (to myself mostly) - installed the 64-bit version 4.3 on Ubuntu 14.04 LTS. All I needed was the symlink

sudo ln -sf /lib/x86_64-linux-gnu/libudev.so.1.3.5 /lib/x86_64-linux-gnu/libudev.so.0

There was no need to install any i386 libraries.

Thanks. That worked.

---

