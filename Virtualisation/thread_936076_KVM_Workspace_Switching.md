---
title: "KVM Workspace Switching"
date: 2008-10-02
forum: Virtualisation
---

### Post by moloth on 2008-10-02
What i would like to do is have an easy way to switch between my Ubuntu 8.04 Gnome desktop and my KVM Windows XP install.

Currently I start the kvm using this:
kvm -M pc -soundhw all -m 1024 -std-vga -hda xp1.img

This allows me to set my resolution to 1680x1050 the same as my gnome desktop. I have both my gnome panel bars set to autohide to 1 pixel using:
#gconf-editor > apps > panel > toplevels

I think I can remove the window decoration using devils-pie > undecorate. 
[http://ubuntuforums.org/showthread.php?t=75749](http://ubuntuforums.org/showthread.php?t=75749)

And I would like the mouse to trigger a workspace change when i hit the left side of the screen with my mouse. (Haven't worked this out yet)

Im just wondering if there is an easier way to accomplish what I want?
Can you somehow set your KVM to fullscreen and switch workspaces without returning the KVM to windowed?

---

### Post by moloth on 2008-10-05
I also saw this thread: [XP/Ubuntu flip?]("http://ph.ubuntuforums.com/showthread.php?t=763332") But I cant seem to flip in KVM fullscreen mode. Also full screen only seems to work before the os is booted otherwise it flits in then out of fullscreen.

EDIT [SOLVED...sort of]: I have now switched to VirtualBox and can do fullscreen easily (ie. doesn't flit in and out). I can switch workspaces easily too using the combo: 
Right_Control(Host button) then Ctrl-Alt-Left_Arrow.  I am guessing Kvm still has a bit of work to do. Also I really love the Seamless mode it offers so that I can run my windows apps natively right on the gnome desktop.

---

### Post by kaivalagi on 2008-11-08
> **moloth said:**
> I also saw this thread: [XP/Ubuntu flip?]("http://ph.ubuntuforums.com/showthread.php?t=763332") But I cant seem to flip in KVM fullscreen mode. Also full screen only seems to work before the os is booted otherwise it flits in then out of fullscreen.

EDIT [SOLVED...sort of]: I have now switched to VirtualBox and can do fullscreen easily (ie. doesn't flit in and out). I can switch workspaces easily too using the combo: 
Right_Control(Host button) then Ctrl-Alt-Left_Arrow.  I am guessing Kvm still has a bit of work to do. Also I really love the Seamless mode it offers so that I can run my windows apps natively right on the gnome desktop.

Has anything changed on this front since Intrepid was released?

I am assuming as kvm is accessed through vnc, it's more a case of having vnc running seamless in fullscreen?

I would prefer to use kvm as it performs better....

---

