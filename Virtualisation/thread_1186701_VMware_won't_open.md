---
title: "VMware won't open"
date: 2009-06-13
forum: Virtualisation
---

### Post by Gp. on 2009-06-13
I've installed VMware 6.5.
x64 system, and I've installed the x64 version.
Installs fine, comes up in system tools menu but when I open it it says "Starting vmware workstation" in the taskbar and then it just dissapears.
Nothing else happens.

When I try to run vmware from terminal, I get this....
```
modinfo: could not find module vmmon
modinfo: could not find module vmnet
modinfo: could not find module vmblock
modinfo: could not find module vmci
modinfo: could not find module vsock
modinfo: could not find module vmmon
modinfo: could not find module vmnet
modinfo: could not find module vmblock
modinfo: could not find module vmci
modinfo: could not find module vsock
Segmentation fault

```

Any help :S

---

### Post by powel212 on 2009-06-14
I never found VMware all that easy to use.

The new Sun Virtualbox works very well though. Give it a try.

[http://www.virtualbox.org/](http://www.virtualbox.org/)

Runs perfectly in my 64Bit Jaunty and just as well as a Linux host in Windows.

Powel

---

### Post by dcstar on 2009-06-14
> **Gp. said:**
> I've installed VMware 6.5.
x64 system, and I've installed the x64 version.
........

And did you install it with all the instructions listed in the mega-thread at the top of this forum?

---

### Post by Gp. on 2009-06-14
> **powel212 said:**
> I never found VMware all that easy to use.

The new Sun Virtualbox works very well though. Give it a try.

[http://www.virtualbox.org/](http://www.virtualbox.org/)

Runs perfectly in my 64Bit Jaunty and just as well as a Linux host in Windows.

Powel

I am, but I'm switching to VMware beacause my Logitech QuickCam Pro 9000 doesn't work with Virtualbox. The light comes on but no video feed comes through. Unless you know how to fix that?

---

### Post by powel212 on 2009-06-14
I have had some problems with Virtualbox mounting some of my periferals correctly but after adding virtualbox to the usergroups everything works fine.

```
sudo gpasswd -a <your-user-id> vboxusers
```

Powel

---

### Post by Gp. on 2009-06-14
I updated vmware.
Works now.
And the camera issue stayed the same even when I added users.
Pretty sure it's a known virtualbox issue.

---

