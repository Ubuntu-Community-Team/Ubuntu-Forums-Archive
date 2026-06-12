---
title: "Share VM machine"
date: 2012-01-11
forum: Virtualisation
---

### Post by SuperMiguel on 2012-01-11
I have a work computer (macbook air) and a home computer iMac... Is there a way to use the same VM (not at the same time)  so i dont have to update my files every time i use one or the other????

---

### Post by CharlesA on 2012-01-11
You can copy it between the two machines. Not ideal, but it should work.

---

### Post by dcstar on 2012-01-20
> **SuperMiguel said:**
> I have a work computer (macbook air) and a home computer iMac... Is there a way to use the same VM (not at the same time)  so i dont have to update my files every time i use one or the other????

You can put the VM files on a shared network folder and have the VM systems on both machines simply use those same files. Or copy them to both machines and sync the files every time they are networked.

---

### Post by japzone on 2012-01-20
All you have to do in Virtualbox is:
-Make a VM on one computer
-File-->Export Appliance, follow directions to export to OVA
-On 2nd Computer File-->Import Appliance and follow directions(If it asks, don't reinitialize the MAC)

Now all you have to do is: (Make sure to shutdown the VM before hand, don't save the state)
-Whenever you go to Work backup the Home VM's VDI file and take it to work
-Overwrite the Work VM's VDI and use the VM
-Before going Home, Backup the Work VM's VDI
-Overwrite the Home VM's VDI and use the VM
--Repeat

That's it. I know it's not exactly convenient but Syncing it over the Net would chew up a TON of Bandwidth and eat through Caps like candy.

Alternatively, you could leave the VM running at Home and then use Remote Control software to access it from Work. A good option is [**Teamviewer**](http://teamviewer.com/en/download/index.aspx)(Works on Windows, OSX, and Linux OSs), just install it on the GuestOS and setup Remote Access(No port fowarding or bridged connections required), then run the [**Teamviewer Portable app**](http://portableapps.com/apps/utilities/teamviewer_portable) to access the GuestOS from Work.

---

