---
title: "Ubuntuzilla and VMware Workstation 6.0.2"
date: 2007-11-14
forum: Ubuntuzilla
---

### Post by jsmithy on 2007-11-14
Hello,

I'm a nooby to Ubuntu and Linux but I have learned a lot since I joined this forums.

As soon as I discovered Ubuntuzilla, I was very eager to try it.  I think it's a great idea.  Thank you for your time and effort.

Before I Installed Ubuntuzilla about a week ago, I had installed VMware 6.0.2, the latest build and I had created the first virtual machine.

I have Drapper 64 bit on the host with the latest updates.

I was very happy because Ubuntuzilla installed very easily and I had Firefox as current as it can be.

When I tried to run VMware Workstation it would not run.  I tried reconfigure it and all the time it would end reconfiguration as successful.  But every time I tried to run Workstation again, it was broken.  Something (remember I am learning) was breaking the install of Workstation every time I fixed it.

I uninstalled Ubuntuzilla and reinstalled Workstation and this time it run.

It seems to me there was some script on Ubuntuzilla that changed something in Workstation's dependencies every time I tried to fix it.

I am looking forward to try Ubuntuzilla again but I don't want to feel scare as to loose my VMware work again.

I will welcome your recommendations as to be able to install Ubuntuzilla without affecting VMware Workstation's installation.

Peace to you all :)

---

### Post by nanotube on 2007-11-14
hm, that's pretty strange... ubuntuzilla doesn't really touch anything system-wide... only thing it does is move the ubuntu-repo version of firefox link to firefox.ubuntu, and puts /usr/bin/firefox to link to /opt/firefox. that shouldn't affect vmware... (i run vmware on my feisty box, with ubuntuzilla, and no probelms...)

are you sure it's ubuntuzilla, and not something else? do you remember the exact text of any error messages (or have vmware logs)?

---

