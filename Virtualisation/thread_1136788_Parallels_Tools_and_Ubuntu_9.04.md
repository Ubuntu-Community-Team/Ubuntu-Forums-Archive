---
title: "Parallels Tools and Ubuntu 9.04"
date: 2009-04-25
forum: Virtualisation
---

### Post by _Poincare on 2009-04-25
Hi,

I am having a problem that I cannot install Parallels Tools with a Ubuntu 9.04 guest. The Parallels Tools just borks and says non-descript error message that "the install fails."

Has anyone successfully installed Parallels Tools with Parallels Desktop v4.3810 *AND* Ubuntu 9.04?!

:confused:  Please help since this stops Ubuntu 9.04 from working correctly.

---

### Post by _Poincare on 2009-04-27
Hello? Anyone there? I can't believe I am the only one having this problem.... It seems to me support for Ubuntu 9.04 is quite lacking......  :confused:

---

### Post by MacSkyrate on 2009-04-27
Youre not.. I have 3.0 but the login screen just loops.. I see that others have the same problem too but no good answers yet.

As the matter a fact.. NO answers yet :P

---

### Post by penneyft on 2009-04-29
When running the Parallels Tools install script, it will fail due to the version of Xorg in Ubuntu 9.04.

But it will install the network driver and toolgate driver (whatever they do).

You can manually get the link to shared folders working:

    edit /etc/fstab and add to end:

    # Parallels Shared Folder mount
    none        /media/psf    prl_fs    sync,nosuid,nodev,noatime,share    0    0
    
    sudo mkdir /media/psf
    sudo mount /media/psf
    
    then, recreate link on Desktop
    cd ~/Desktop
    ln -s /media/psf Parallels\ Shared\ Folders


So the only thing not working is automatic resolution switching, and the ability to move your mouse in and out of the virtual machine automatically.  But I do wish the Parallels team worked on this ahead of release time....  Oh well.


Fletcher

---

### Post by penneyft on 2009-05-02
> **penneyft said:**
> So the only thing not working is automatic resolution switching, and the ability to move your mouse in and out of the virtual machine automatically.  But I do wish the Parallels team worked on this ahead of release time....  Oh well.


I've also discovered that clock synchronization doesn't seem to be happening - when I pause the VM, the clock stops and doesn't reset when I unpause the VM.  I also couldn't get Ubuntu to automatically sync with ntp.  But I could get a cron job to work, so it runs the ntpdate command every 5 minutes....   Good enough for now.

F-

---

