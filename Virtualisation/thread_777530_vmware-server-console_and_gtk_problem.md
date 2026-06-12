---
title: "vmware-server-console and gtk problem"
date: 2008-05-01
forum: Virtualisation
---

### Post by sdahlin on 2008-05-01
Apparently with the 1.0.5 release of vmware-server-console and 8.0.4 Hardy heron there is a problem with gtk.  When the /usr/bin/vmware-server-console script executes it calls /usr/lib/vmware-server-console/lib/wrapper-gtk24.sh prior to calling /usr/lib/vmware-server-console/bin/vmware-server-console.  The wrapper-gtk24.sh returns an exitcode of 1 in the vm_run() section.

I used earlier posts dealing with vmware-server (i.e., [http://ubuntuforums.org/showthread.php?t=613976](http://ubuntuforums.org/showthread.php?t=613976)) to get vmware-server up and running.  I tried also providing symbolic links

sudo ln -sf /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1
sudo ln -sf  /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0

as well as trying various settings (yes,no,force) for the $VMWARE_USE_SHIPPED_GTK var to no effect.  Has anyone else dealt with this?

Thanks,
Steve

---

### Post by Kokopelli on 2008-05-02
> **sdahlin said:**
> Apparently with the 1.0.5 release of vmware-server-console and 8.0.4 Hardy heron there is a problem with gtk.  When the /usr/bin/vmware-server-console script executes it calls /usr/lib/vmware-server-console/lib/wrapper-gtk24.sh prior to calling /usr/lib/vmware-server-console/bin/vmware-server-console.  The wrapper-gtk24.sh returns an exitcode of 1 in the vm_run() section.

I used earlier posts dealing with vmware-server (i.e., [http://ubuntuforums.org/showthread.php?t=613976](http://ubuntuforums.org/showthread.php?t=613976)) to get vmware-server up and running.  I tried also providing symbolic links

sudo ln -sf /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1
sudo ln -sf  /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0

as well as trying various settings (yes,no,force) for the $VMWARE_USE_SHIPPED_GTK var to no effect.  Has anyone else dealt with this?

Thanks,
Steve

Can you try and run console from a command line and post whatever errors occur?

---

### Post by sdahlin on 2008-05-02
Unfortunately, it gives no error messages.  It just simply quits.  The scripts will give error messages for certain types of problems but a failure of the type I describe gives nothing.  The process just ends.

---

### Post by leafpaul on 2008-05-03
> **sdahlin said:**
> Unfortunately, it gives no error messages.  It just simply quits.  The scripts will give error messages for certain types of problems but a failure of the type I describe gives nothing.  The process just ends.


When running vmware-server-console from the command line I get the following:

/usr/lib/vmware-server-console/lib/wrapper-gtk24.sh: 316: /usr/lib/vmware-server-console/bin/vmware-server-console: not found

/usr/lib/vmware-server-console/lib/wrapper-gtk24.sh: 370: /usr/lib/vmware-server-console/bin/vmware-server-console: not found

Sounds like the same issue.  Any ideas?

vmware-server-console is in the path specified despite the not found.  Running as root gives the same error.

---

### Post by fjgaude on 2008-05-03
What do you get from just running vmserver, not -server-console?

---

### Post by leafpaul on 2008-05-03
> **fjgaude said:**
> What do you get from just running vmserver, not -server-console?

The vmserver is on another machine I was doing a standalone install of the console on hardy.

---

### Post by kvasimongo on 2008-05-07
> **leafpaul said:**
> When running vmware-server-console from the command line I get the following:

/usr/lib/vmware-server-console/lib/wrapper-gtk24.sh: 316: /usr/lib/vmware-server-console/bin/vmware-server-console: not found

/usr/lib/vmware-server-console/lib/wrapper-gtk24.sh: 370: /usr/lib/vmware-server-console/bin/vmware-server-console: not found

Sounds like the same issue.  Any ideas?

vmware-server-console is in the path specified despite the not found.  Running as root gives the same error.

I get the same error messages trying to run vmware-server-console on hardy.

---

### Post by turn1200 on 2008-05-08
I'm getting the error as well.  I may try installing the full server as well to see if it helps since I might use that anyway.

---

### Post by turn1200 on 2008-05-08
I'm using 64bit so I had to install ia32-libs.

sudo apt-get install ia32-libs

---

### Post by turn1200 on 2008-05-08
I then had to run

sudo cp /usr/lib/gcc/x86_64-linux-gnu/4.2/libgcc_s.so /usr/lib/vmware-server-console/lib/libgcc_s.so.1/libgcc_s.so.1

then

sudo cp /usr/lib/libpng12.so.0 /usr/lib/vmware-server-console/lib/libpng12.so.0/

I should mention I performed the steps in the last two posts instead of installing the server portion of vmware.

---

### Post by fjgaude on 2008-05-08
Has folks here tried the Sticky, exactly, at the top of this Forum?

---

### Post by turn1200 on 2008-05-09
Not me.  I ended up fixing the problem without.

---

### Post by leafpaul on 2008-05-17
The fix described by turn1200 sorted me out too

---

