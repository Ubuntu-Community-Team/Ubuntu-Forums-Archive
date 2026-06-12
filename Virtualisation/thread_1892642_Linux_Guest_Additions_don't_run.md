---
title: "Linux Guest Additions don't run"
date: 2011-12-08
forum: Virtualisation
---

### Post by seattle vic on 2011-12-08
I'm running 11.10 as a host and also as a guest.  I'm pretty sure that my guest additions installed but when I went to add shared folders, it said they were not.  When I tried to install them in the usual fashion (sudo sh VBoxLinuxAdditions.run) the program quickly returns to the prompt and nothing is installed.

I thought maybe there was an old set of GA on the machine and I needed to uninstall them, but I don't know how to check that, or even how to uninstall them if that were the case.

In any event, the guest additions install does not return an error, just does nothing.

---

### Post by bluexrider on 2011-12-08
> **seattle vic said:**
> I'm running 11.10 as a host and also as a guest.  I'm pretty sure that my guest additions installed but when I went to add shared folders, it said they were not.  When I tried to install them in the usual fashion (sudo sh VBoxLinuxAdditions.run) the program quickly returns to the prompt and nothing is installed.

I thought maybe there was an old set of GA on the machine and I needed to uninstall them, but I don't know how to check that, or even how to uninstall them if that were the case.

In any event, the guest additions install does not return an error, just does nothing.
  
In my case I  sudo chmod +x VBoxLinuxAdditions-x86.run

then check in Devices>Install Guest Additions

---

### Post by Paddy Landau on 2011-12-08
How have you installed VB?

Don't install from the repository (if you have done so, uninstall it).

Rather:


[LIST=1]
[*]Go to the [VB Linux download page]("https://www.virtualbox.org/wiki/Linux_Downloads"), scroll down to the **Debian-based Linux distributions** heading, and follow the instructions to add the relevant PPA and its key.
[*]Reload your software sources.
[*]Install VB through Ubuntu Software Centre, Synaptic Package Manager or the command line (whichever you prefer).
[*]Having done that, go the the main [VB download page]("https://www.virtualbox.org/wiki/Downloads"). Download the VM VirtualBox Extension Pack.
[*]Start VirtualBox. File > Preferences > Extensions. Add the downloaded file.
[*]Start your Ubuntu guest. Devices > Install Guest Additions.
[/LIST]

It is much easier that way, I think.

---

### Post by memilanuk on 2011-12-08
Did you add a shared folder to the VM on its settings page?  Once the guest additions are installed, which usually involve a reboot to get all the graphics stuff updated and working, you should see the shared folder mounted automatically - assuming you selected that option.

---

