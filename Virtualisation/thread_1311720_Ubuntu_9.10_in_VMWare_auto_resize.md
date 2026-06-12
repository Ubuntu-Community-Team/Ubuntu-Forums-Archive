---
title: "Ubuntu 9.10 in VMWare auto resize"
date: 2009-11-02
forum: Virtualisation
---

### Post by RealG187 on 2009-11-02
I am running Ubuntu in VM Ware and want to to auto resize the guest (change the resolution in Ubuntu) when I enter and exit full screen mode and change the size of the Window.

I installed VM Ware tools twice and had no success...

---

### Post by fjgaude on 2009-11-02
As I recall, in VM files tab (in Server) or something like that there are two buttons to check to get auto resize of the windows and the applications.

---

### Post by RealG187 on 2009-11-02
"VM Files tab" what the hell is that?

Where is the option to enbable it?

---

### Post by fjgaude on 2009-11-02
If you are running VMware Server the Tabs are at the top of the menu while the guest is running. I don't have my main computer running here so can't recall the exact names of the options available.

---

### Post by RealG187 on 2009-11-02
Oh that? There is only a devices menu and a menu to power off the VM, there is nothing about resize...

---

### Post by fjgaude on 2009-11-02
You are not using the Server but likely the Player?

---

### Post by RealG187 on 2009-11-02
I am using VM Ware server

---

### Post by fjgaude on 2009-11-03
Interesting... my menu for Server at the top, left has: File, Edit, Host, LM, Tabs, Help. In the Edit menu, there is Preferences and Display. In the Display menu you can check auto for the windwos sizes.

If you don't have this at the top line of your vmware server it is not like mine.

---

### Post by RealG187 on 2009-11-03
What version do you have? I am using VM Ware server 2...

---

### Post by fjgaude on 2009-11-03
Okay, that explains it, I'm with server 1.0.9... soon to go to 1.0.10.

I never liked the web-based server (v2.0 and beyond) and don't use it, but I can't believe you don't somehow have the elements to do what has to be done.

---

### Post by RealG187 on 2009-11-03
I started using it when I got Ubuntu 8.10 and 1 didn't work and I had to use 2. Now we just use 2 at school...

---

### Post by fjgaude on 2009-11-03
Yes, we had to use a patch for 8.04, 8.10, and 9.04 to use the 1.0.x version of vmware server... but I always thought because of the advanced features it was worth the extra effort.

I trust that 1.0.10 will not require a patch, as VMware Player 3.0 doesn't. We will see, likely tomorrow when I give it a try.

---

### Post by RealG187 on 2009-11-03
Did you have to use a different patch for each version of Ubuntu? Is it possible to get VM Ware workstation on Ubuntu?

---

### Post by fjgaude on 2009-11-03
If memory serves it took two different patchs to get through the three kernel changes. Not too much trouble when you think of what you get. Of course, all free.

Yes. VMware Workstation is the hot ticket for Ubuntu, but it cost $90 the last time I looked. If you install VMware Player 3.0, which seems to work with all kernels I've tried, you can upgrade directly from one of its menus to Workstation.

Tomorrow I'm gonna likely try Server 1.0.10 to see if it works with Ubuntu 9.10. If it does I'll likely use it in 9.04 and 8.10.

---

### Post by RealG187 on 2009-11-04
Where do you get these patches and how do you apply them?

---

### Post by fjgaude on 2009-11-04
Getting patches is easy. Try a google for: **vmware-update-2.6.27**. From there you have to study what it takes to get these kinds of patches to work with the various kernels and vmware server 1.0.xx.

BTW, Server 1.0.10 didn't work with kernel 2.6.31-14 of Karmic.

---

### Post by dannonin@hotmail.com on 2009-12-22
FYI for anyone using VMWare Workstation 6.5.3:

install vmware tools using the steps posted at beginning of this thread

reboot

in the **VMWare Workstation menubar **go to **View**

Make sure
[B]Autofit Window
Autofit Guest[/B]

are both selected.  Now window resizing works correctly.

been beating my head for 3 months thinking it was a tools issue

---

### Post by fjgaude on 2009-12-22
Yea, it pays to look around and see what all those drop-down menus control, eh?

---

### Post by Hopping_Ubu on 2009-12-29
> **RealG187 said:**
> I am running Ubuntu in VM Ware and want to to auto resize the guest (change the resolution in Ubuntu) when I enter and exit full screen mode and change the size of the Window.

I installed VM Ware tools twice and had no success...

I am running the same configuration as you. I made my changes to the resolution is in  Ubuntu. Select from the top, System, Preferences then Display. You will be able to choose the resolution that you would like when the guest opens in the console. I set mine not to open in full screen but rather something less than my monitor default size so that I can also see what else is on my regular desktop.

Hope this helps.

---

### Post by RealG187 on 2009-12-29
> **Hopping_Ubu said:**
> I am running the same configuration as you. I made my changes to the resolution is in  Ubuntu. Select from the top, System, Preferences then Display. You will be able to choose the resolution that you would like when the guest opens in the console. I set mine not to open in full screen but rather something less than my monitor default size so that I can also see what else is on my regular desktop.

Hope this helps.I don't wanna have to adjust the resolution in Ubuntu, I want it to be automatic to whatever the console is.

So if I make the console full screen, then it's full screen; if I make the window 800x600, then that's what the resolution will be...

---

