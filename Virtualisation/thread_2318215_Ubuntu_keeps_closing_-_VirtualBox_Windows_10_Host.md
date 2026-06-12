---
title: "Ubuntu keeps closing - VirtualBox Windows 10 Host"
date: 2016-03-24
forum: Virtualisation
---

### Post by Owain_Esau on 2016-03-24
Hi;

Im fairly new to Ubuntu and Linux in general and am having trouble with my virtualbox setup. I have 4 vms installed:


[LIST]
[*]Kali Linux
[*]CentOS 7
[*]OpenSUSE
[*]Ubuntu
[/LIST]

The other 3 work fine but for some reason Ubuntu tends to close when i change from full screen, or try to switch the display Ubuntu is displayed on (I have a laptop with 1 external monitor)

I have tried:


[LIST]
[*]Reinstalling Ubuntu
[*]Disabling 3D acceleration
[*]Reinstalling Oracle VirtualBox and Guest Additions
[/LIST]

Im not sure where to go from here, so any help would be much appreciated!

Thanks in advance

---

### Post by v3.xx on 2016-03-24
Hi :)

Look in /var/crash logs for clues.

Also this could be Unity.  You can install another desktop for testing purposes.  The Flashback desktop can take you off compiz and use metacity as a window manager.  To install..

```
sudo apt-get install gnome-panel
```

And choose your desktop environment at the login screen.

---

### Post by Owain_Esau on 2016-03-29
Hi;

Thanks for the reply, ive tried what you have said and it hasnt worked. I disabled 3D acceleration again and it seems to be working, however it becomes very laggy without that feature on.

There is also nothing in var/crash

Regards

---

### Post by Bucky Ball on 2016-03-29
*Thread moved to **Virtualisation**.*

---

### Post by v3.xx on 2016-03-30
I do not run the Unity desktop, but I'm pretty sure the 3D acceleration is needed or it will slow down.

3D acceleration should remain disabled when using Metacity, but you say..
> 
ive tried what you have said and it hasn't worked.

Metacity (Flashback) will not work at all?  Do you get any errors?

How much ram did you allocate to the guest?

---

### Post by Owain_Esau on 2016-03-31
Hi; 

I just tried it with 3D acceleration disabled with Metacity and yes it does work well enough, however id prefer to use unity so i have switched over VMware Workstation and its working fine now.

I have 16GB Ram allocated to Ubuntu for some reason, not sure why i allocated so much.

Regards

---

