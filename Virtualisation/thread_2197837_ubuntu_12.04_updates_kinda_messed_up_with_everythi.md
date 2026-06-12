---
title: "ubuntu 12.04 updates kinda messed up with everything"
date: 2014-01-05
forum: Virtualisation
---

### Post by reonz on 2014-01-05
Hello everyone, first of all, i have to say that i am new on ubuntu (linux in general) and virtualisation as well.

specs: 
windows seven 64 bit
VB 4.3.4r91027
ubuntu 12.04 LTS

So a couple of weeks ago i installed virtualbox and ubuntu 12.04, patch lot of stuff, installed guest addition followed lot of tutorials on the web and everything was working perfectly, i mean my mouse was working from windows to linux with the mouse integration on, scrolling as well, my screen was well sized, i could keep the VB cient windowed and it was scalling perfectly to my screen so i was able to switch between both systems without having to use tabing or anything.

On friday i updated ubuntu but didn't reboot the system until few hours ago, since then, nothing is working as before:
- the ubuntu resolution in settings>appearence is stuck at 1920x1280 (when my actual resolution is 1680x1050) so i have scroll bars x and y and can't scal it unless i like to watch stretched pixels.
- the resolution choices in display (VBX display) are all 4:3 choises, don't have any 16:10
- mouse scroll is not working anymore unless i disable mouse integration, but then if i do that, i have to use host to go back to windows

I would really like to not re-install everything since i did so much manipulations i don't really understand, following most of the time just tutorials and i want to keep my work so far, i also installed gconf-editor and nautilus-open-terminal so i could open terminal directly from a directory location.

I would really appreciate any help to prevent me from re-installing everything, thanks.

---

### Post by ibjsb4 on 2014-01-05
Your running Ubuntu in vBox and NOT taking snapshots for backup?  The whole situation could of been avoided with a backup snapshot.

Can you get to terminal or console?

```
sudo apt-get -f install
```

Get any errors?

---

### Post by joe_beasley on 2014-01-23
Some of that "stuff" you patched was probably the kernel.  You need to reinstall the vbox guest additions, so that the modules will be recompiled for the current running kernel.

---

### Post by QIII on 2014-01-23
To expand a bit ...

When you install the Guest Additions, third-party, non-open-source changes are made to the kernel of the Guest.  (The kernel becomes "tainted" in Linux vernacular -- and for this reason any kernel-level bug you report from your guest will be ignored by the developers.  They won't even bother debugging tainted kernels.)

When you do your updates and a new kernel is installed or the current one updated, those changes no longer exist in the kernel being used.

Every time you see a kernel update or upgrade when doing your update to the Guest OS, you'll have to shut down the guest, restart the guest, install Guest Additions, shut down the guest and then restart.  Just the way it is.

Cheers!

---

### Post by TheFu on 2014-01-24
> **QIII said:**
> Every time you see a kernel update or upgrade when doing your update to the Guest OS, you'll have to shut down the guest, restart the guest, install Guest Additions, shut down the guest and then restart.  Just the way it is.

But all the dependencies are already installed, so the reinstallation of the guest additions shouldn't take much effort - 20 seconds of effort, tops.

---

### Post by QIII on 2014-01-24
Indeed.  Takes very little time at all. Not painful.  Just needs to be done.

---

