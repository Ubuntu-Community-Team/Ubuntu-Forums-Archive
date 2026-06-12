---
title: "My new Host System"
date: 2019-06-17
forum: Virtualisation
---

### Post by cruzer001 on 2019-06-17
tmux terminal emulator
[s]nano[/s]Jed text editor
[s]links2 browser[/s]
lynx text web browser
mc/Xfe file manager
xdm display manager
xorg
[s]openbox window manager[/s]
spectrwm Dynamic window manager
network-manager using _nmtui_ terminal user interface
net-tools for terminal only use

**Xfe** a X file manager
**Jed** a terminal text editor
**spectrwm** window stacking for the laptop/tiling for the external monitor + ease of use
[s]Xmonad was first choice for a WM, but I need some time to better understand it.[/s] **Replaced**
**Tmux** because its user friendly.
[s]links2 text side works out of the box, gui does too, but needs tweaking.[/s] **Replaced**
**lynx** it just works
**Midnight Commander** Just trying to use the terminal for everything.
**xdm** I have used startx in the pass, just taking a short cut.  Maybe I would of been better off with **nodm**

Anyhow its up and running after trying multiple other packages in the process of elimination.  This install will run [SIZE=3]**KVM**[/SIZE]VirtualBox and little else.

Anyone have any ideas for improvement on this?  The real install to my laptop will happen soon.

---

### Post by TheFu on 2019-06-17
Use the shell.
Manage VMs using virt-manager with libvirt running KVM VMs.  This allows the same management capabilities from another workstation as if it was local via ssh tunnels.  The tunnelling is built-in - use use the ssh checkbox.

If you want an amazing WM, check out fvwm-crystal. It has all the coolness factors of virtual desktops, opacity, and addons for almost everything. Plus it has been around 20+ yrs in one form or another, so you don't have to worry about RH or Canonical screwing it up.  Of course, if you enjoy fighting with a new GUI every 2-3 yrs because "change for no reason", perhaps fvwm isn't the best choice.

IMHO. ;)

---

### Post by cruzer001 on 2019-06-17
> **TheFu said:**
> Use the shell.
Manage VMs using virt-manager with libvirt running KVM VMs.  This allows the same management capabilities from another workstation as if it was local via ssh tunnels.  The tunnelling is built-in - use use the ssh checkbox.
Hi! TheFu
I hear what your saying, but I'm sticking with vBox for now.  I like what I'm reading about containers (LX) and will be jumping on that wagon in the future.
> **TheFu said:**
> If you want an amazing WM, check out fvwm-crystal. It has all the coolness factors of virtual desktops, opacity, and addons for almost everything. Plus it has been around 20+ yrs in one form or another, so you don't have to worry about RH or Canonical screwing it up.  Of course, if you enjoy fighting with a new GUI every 2-3 yrs because "change for no reason", perhaps fvwm isn't the best choice.
Fvwm-crystal - Thanks for that tip - Old school has its place, I'll check it out.

---

### Post by TheFu on 2019-06-17
You can use **virt-manager** to manage virtualbox VMs too.  Nice when you want to handle it remotely.

fvwm and the family lets you control *everything* about a window. EVERYTHING.  Colors, width, height, thickness, fonts for everything, what every different region of the window does - EVERYTHING.  The defaults aren't terrible, but we all want to  tweak something, right?  Obviously, you get total control over the menus and context-sensitive menus.

But GUIs are highly personal. Whatever works for anyone is the perfect GUI.  Probably less than 5% will enjoy fvwm and it isn't perfect.  Try it for 3 days. See if you like it.  It is about the light-est full WM available. The only one I know that is lighter is the SuckLess WM, dwm.  [https://dwm.suckless.org/](https://dwm.suckless.org/)   I don't prefer titling WMs.

For doing file management in the shell, there's [https://github.com/jlevy/the-art-of-command-line](https://github.com/jlevy/the-art-of-command-line) I try to add one more new trick every week.  Same for vim - 1 new trick every week.

---

### Post by cruzer001 on 2019-06-17
> You can use virt-manager to manage virtualbox VMs too.
No, I was not aware of that.  I need to look into this, thanks!
> fvwm and the family lets you control *everything* about a window. EVERYTHING. Colors, width, height, thickness, fonts for everything, what every different region of the window does - EVERYTHING. The defaults aren't terrible, but we all want to tweak something, right? Obviously, you get total control over the menus and context-sensitive menus.
Crystal is surprisingly full featured from what I have read and I think it looks exceptionally sharp out of the box.  I really like it, but like OB, its overkill for this project.  If I can run virt-manager from the terminal then I would be tempted not to use any window manager.
> The only one I know that is lighter is the SuckLess WM, dwm. [https://dwm.suckless.org/](https://dwm.suckless.org/) I don't prefer titling WMs.
I do like tiling and makes this another candidate for my laptop. The less feature rich, the better for this project.
> For doing file management in the shell, there's [https://github.com/jlevy/the-art-of-command-line](https://github.com/jlevy/the-art-of-command-line) I try to add one more new trick every week. Same for vim - 1 new trick every week.
Thanks!

---

### Post by TheFu on 2019-06-17
virsh - the shell version of virt-manager. No menu, but it can connect via libvirt to remote systems for controlling.
If you haven't looked already, might want to check out proxmox, but this requires a fresh OS install - or it did last time I looked. It takes over the entire machine.

fvwm-crystal is the fancy version of fvwm.  fvwm is like openbox, but lighter and more configurable.  fvwm2 has been stable since the late 1990s.

---

### Post by cruzer001 on 2019-06-18
**spectrwm** window stacking for the laptop/tiling for the external monitor + ease of use

Finally something I'm happy with :D
Not a feature rich gui, but not bare bones either.
Its just right for this project.

Also added **nmtui/net-tools** to my first post.

Need to kick it around some more, see what else might be needed.

Think I need to start with a fresh install and go from there.  It's time to partition 10G (the install takes 4.5G) and try a real world install next.  And add vBox to the mix, see if everybody plays nice.

---

### Post by cruzer001 on 2019-06-21
Did a real world install on my desktop, its working.  VirtualBox (6x) did complain of missing dependencies, but got lucky with the "-f install" command.

There are other considerations to make.  Like how to get bluetooth working.  Will a restricted graphic driver improve the virtual graphics?  Got to try it.  This list will no doubt grow.  But I'm going ahead and set it up on my lappy.  Its good enough to use.

I did decide to reinstall links2 and muck with it some more.  It's working better, but Lynx has it beat for text display at the moment so I'm keeping both on board.

Anyhow I'm calling this project is solved (enough) :)

---

### Post by cruzer001 on 2019-07-02
Update
I am liking this setup, its a keeper.

With no desktop on the host, vBox just doesn't feel like a good fit anymore.  @TheFu; I believe you have mention KVM once or twice, well guess what :)

---

### Post by cruzer001 on 2019-07-20
Update
@TheFu
Really didn't expect to see much of a difference since I'm running SSD, but I do see a difference.  KVM is snapper than vBox when running a desktop install on 2core.  Don't get me wrong, both are fast, but KVM has a notable edge to it over vBox.  Jury is still out on video performance.

---

