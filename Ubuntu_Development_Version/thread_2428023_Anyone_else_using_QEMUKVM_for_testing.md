---
title: "Anyone else using QEMU/KVM for testing?"
date: 2019-09-29
forum: Ubuntu Development Version
---

### Post by Irihapeti on 2019-09-29
As the title says: is anyone else using QEMU/KVM for testing?

I've been running into some graphics problems with standard Ubuntu (Gnome) that I'm not getting with flavours such as Xubuntu, Ubuntu-Budgie and Lubuntu. I'm wondering if this is just me missing something important, or whether I need to report some bugs.

---

### Post by Skaperen on 2019-09-29
i sometime do QEMU.  but i'm running Xubuntu.  what graphics problems do you see happening?

---

### Post by Irihapeti on 2019-09-29
Graphics are freezing some of the time. The first one was during install, but the install was able to complete successfully. Also several times after reboot. I did check that the VM is running X11.

The other issue is that guest agent is not available, even though it's installed, so I have to manually release the mouse pointer every time I go from the VM to something on the host.

---

### Post by Skaperen on 2019-09-29
are you running a DM that lets you switch users?  i switch users frequently and put QEMU in its own user, which makes it easy to run multiple instances in full screen mode (using keyboard shortcuts in Xfce to do the switch ... no idea if Gnome can do this).  does full screen mode work for you?

---

### Post by Irihapeti on 2019-09-29
The host machine is running Xubuntu 18.04. I run all the VMs as my own user - never thought of doing anything different until you mentioned it. Budgie runs fine, and as I gather it's Gnome-based, I thought standard Ubuntu would behave similarly.

Most of the VMs are servers (for testing stuff) with a few 19.10 VMs mainly for ISO testing. There's also a Windows 10 VM for doing my paid proofreading work in MS Office. (I can't take any chances with compatibility issues when I'm asking for payment and am dealing with deadlines.)

Oddly enough, I had more issues with the Linux VMs than the Windows one in the beginning. A bit of searching and testing ironed out most of them, and I've decided I prefer QEMU/KVM to Virtualbox.

---

### Post by Skaperen on 2019-09-29
my VM setup was in my old 16.04 system.  i effectively lost those when a major crash on June 30 caused me to install 18.04 (turns out i didn't really need to, but i didn't know, at the time) back on July 1.  it was more of a hurry to get back online.  i haven't needed the VMs since then and haven't set them back up, yet.  i had been thinking of running them in a Linux container just to have another layer around whatever i run there, but i haven't figured out how to do that in lightdm, yet.  so, i didn't bother to back them up, since i had planned to rebuild it all  i guess i'll let containers wait until 20.04 and go ahead and rebuild them tomorrow.  at least i can do the scripts in python3, this time, instead of bash.  i had 4 VMs before.  i might push it this time and do 10.

i understand your need to run Windows.  i'd do it that way, too, if i didn't have a dedicated laptop like i had on my last job.  turns out they didn't want it back, so i wiped it and gave it to my nephew (it was a low-end Acer).  the only copy of Windows i have is an old copy of Vista.  but i'm gonna leave it in its original shrink wrap.

---

### Post by Irihapeti on 2019-09-29
As it turned out, I was prompted to file a bug against qemu-ga. Which is a little tricky to do when your graphics have frozen. :) However, we got there in the end.

The testing VMs don't currently get backed up, but the Windows one gets copied regularly to a USB3 external drive.

---

### Post by TheFu on 2019-09-29
Something is vastly different in Gnome3 GPU use when compared to Gnome2.  IME, Gnome3 has never worked well inside a VM that didn't support 2D accel in the fake GPU drivers. Gnome2-based DEs have always worked well.

But I've never ran Gnome3 more than just a few hours, long ago, to learn that.  Something about the built-in compositor. OpenGL might be part of the problem.  I suspect KDE with kwin would have similar issues, but don't know and I haven't seen complaints about it.

Which GPU hardware is being simulated?  SPICE? Cirrus?  VGA? One of the other choices?  In theory, SPICE should be the most capable and perform the best, but it requires a client-side driver install for Windows.

---

### Post by cruzer001 on 2019-09-29
I switched over to KVM not long ago, running 18.04 (gnome3) host/guest.  When installing a guest my experience has been that the guest resolution never gets set right and it is necessary to use "virtio".

I still have vBox installed and still use it. VirtualBox does not have this problem and will run gnome3 without any issues.

---

### Post by TheFu on 2019-09-29
> **cruzer001 said:**
> I switched over to KVM not long ago, running 18.04 (gnome3) host/guest.  When installing a guest my experience has been that the guest resolution never gets set right and it is necessary to use "virtio".

I still have vBox installed and still use it. VirtualBox does not have this problem and will run gnome3 without any issues.

Having both KVM and virtualbox on the same physical machine isn't a good idea. Hypervisors have conflicts, but if you have that working, guess the rmmod and insmod is working as needed.

Gnome 3.32 additions [https://www.phoronix.com/scan.php?page=news_item&px=GNOME-3.32-Features](https://www.phoronix.com/scan.php?page=news_item&px=GNOME-3.32-Features)  Which should be in 19.04 and later releases.  The new VirtIO-GPU sounds good.  That part of the announcement was for Gnome-Boxes. If standalone versions support it too, great!

---

### Post by cruzer001 on 2019-09-29
> Hypervisors have conflicts
They can both be install, but not run at the same time.  I did research this before trying it and has proven to be stable for the past couple of months.

IMO vBox is better suited for a GUI environment, but KVM is much more efficient with resources and worth the extra effort.

So for what its worth, thats my two cents :)

ps
I run xwayland

---

### Post by Irihapeti on 2019-09-29
For what it's worth, I've installed Kubuntu in a VM and it's running very nicely. No graphics problems of the sort that were showing up with standard Ubuntu. It does seem that Gnome 3 might be the problem.

---

### Post by TheFu on 2019-09-30
Blog post by Kraxel about different QEMU/KVM display choices
[https://www.kraxel.org/blog/2019/09/display-devices-in-qemu/](https://www.kraxel.org/blog/2019/09/display-devices-in-qemu/)
There are many more than I knew about, each with a purpose.

---

### Post by Irihapeti on 2019-09-30
> **TheFu said:**
> Blog post by Kraxel about different QEMU/KVM display choices
[https://www.kraxel.org/blog/2019/09/display-devices-in-qemu/](https://www.kraxel.org/blog/2019/09/display-devices-in-qemu/)
There are many more than I knew about, each with a purpose.

Thanks for that. Bookmarked for future reference.

---

### Post by Irihapeti on 2019-10-01
It turns out that there were some bugs causing this behaviour, and they seem to have been fixed. (well, so far, at least)

---

