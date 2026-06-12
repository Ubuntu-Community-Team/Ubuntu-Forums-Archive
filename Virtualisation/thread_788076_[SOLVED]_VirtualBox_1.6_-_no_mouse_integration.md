---
title: "[SOLVED] VirtualBox 1.6 - no mouse integration"
date: 2008-05-09
forum: Virtualisation
---

### Post by rdoolen on 2008-05-09
I have never been able to get mouse integration to work on my WindowsXP guest. I started with VirtualBox 1.5.4 on Gutsy, upgraded to 1.5.6 on Hardy and then to 1.6 on Hardy. In every case I get the same problem. I do have Guest additions installed. I also have a KDE4 virtual machine as a guest and the mouse integration works fine in that VM. Sidebar-- KDE4 in seamless mode on top of Hardy's Gnome is fairly entertaining. :)

Here is how my mouse behaves. If I have mouse integration enabled, the mouse doesn't respond to motion. In fact, if the pointer is visible in the VM, and I drag the mouse over the window, the pointer moves down and to the right -- no matter what direction I move the mouse. It will do this until it is out of sight in the bottom corner. The mouse does respond to the button clicks.

If I disable mouse integration, the mouse works fine.

If I can get this to work, all of my computers will work perfectly. LOL

Thanks to anyone that can help.

---

### Post by rdoolen on 2008-05-12
Also, I have tried several different mice.

---

### Post by rdoolen on 2008-05-19
bump

---

### Post by erat123 on 2008-05-21
I have the same problem on my system.  I'm running Ubuntu Hardy.  I'm running Windows XP Pro in VirtualBox.

---

### Post by rdoolen on 2008-05-24
Now if we can get someone to help us out.

---

### Post by Steve413z on 2008-05-24
you need to install the guest OS tools

---

### Post by rdoolen on 2008-05-25
Well, thanks for being the first person to attempt to help, but I have already installed guest additions, as it says in the first post. If you have another suggestion I'd love to hear it.

Thanks

---

### Post by Steve413z on 2008-05-25
> **rdoolen said:**
> Well, thanks for being the first person to attempt to help, but I have already installed guest additions, as it says in the first post. If you have another suggestion I'd love to hear it.

Thanks


whoops, i should read more closely, 

The OS type is set to "Windows XP" right? not other?

---

### Post by rdoolen on 2008-05-25
Something I handn't checked, alas it was set to XP.

I have tried playing with my mouse and viseo setting in xorg.conf to no avail.(At least I didn't screw up my xorg.conf) I tired toggling the auto-capture keyboard setting also.

I have ACPI and IOACPI enabled. I didn't disable them because I heard it was bad to disable them once they have been enabled. I have AMD-V disabled because my CPU doesn't have that capability. I have PAE/NX disabled becasue I don't know what it is. I think its new to 1.6.

VirtualBox is a very cool application even with this issue. I'd love to get it solved though.

---

### Post by twade on 2008-05-27
I can't help other than to sympathize.  The only solution I've found so far that works is to regress back to VirtualBox version 1.5.4.  Unfortunately this isn't without some other issues so I am looking forward to a more satisfactory solution.

---

### Post by rdoolen on 2008-06-03
I didn't have mouse intregration working in 1.5.4 so I&#12288;don't think that will help me.

---

### Post by rdoolen on 2008-06-07
So, I got it to work. Everytime there is a new kernal, I uninstall and re-install the guest additions. Well, this time it worked.

---

