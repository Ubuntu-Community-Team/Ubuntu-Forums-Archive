---
title: "Installing VirtualBox Guest additions break X server on Maverick guest"
date: 2010-10-12
forum: Virtualisation
---

### Post by soldier1st on 2010-10-12
> **_Virtualbox_**: When running Ubuntu 10.10 as a guest there is a small problem with the virtualBox additions. The graphical enhancements fail with the following message:

To resolve this, install the package from the Ubuntu repositories:

```
sudo apt-get install virtualbox-ose-guest-x11
```When asked, accept (type "y") to install the maintainers version.this solution will only work on the OSE version but if you use the non free version that fix will not work. i tried this on the non free one and it does not fix it actually it gives a strange colored window that covers the whole screen with various colors and numbers all over the place and the only way to recover is to press the reset button in virtualbox. and vmware do have a 10.10 version i believe. also i do have a picture of what happens. 
[IMG]http://img52.imageshack.us/img52/4331/screenshotir.png[/IMG]
Update: some forums have suggested leaving the screen like the screenshot i have posted for 10-15 minutes then do a reset in virtualbox and you should be able to change the resolution and the guest tools are updated and installed(it worked for me)

---

### Post by CharlesA on 2010-10-12
Strange, it works for me, and I'm running the "non-free" version of VBox.

It sounds like you tried to reinstall the guest additions after they were installed and it dumped out when trying to configure the X server.

---

### Post by soldier1st on 2010-10-12
> **CharlesA said:**
> Strange, it works for me, and I'm running the "non-free" version of VBox.

It sounds like you tried to reinstall the guest additions after they were installed and it dumped out when trying to configure the X server.
well i followed the instructions you provided. it is not a problem with ubuntu. it is virtualbox that does not have updated virtualbox tools. no biggie

---

### Post by CharlesA on 2010-10-12
> **soldier1st said:**
> well i followed the instructions you provided. it is not a problem with ubuntu. it is virtualbox that does not have updated virtualbox tools. no biggie

Indeed, which is why you need to install "virtualbox-ose-guest-x11" inside the guest and tell it Y to replace, and reboot.

---

