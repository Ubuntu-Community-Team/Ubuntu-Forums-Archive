---
title: "Re: Ubuntu 16.10 Virtualization"
date: 2016-10-18
forum: Virtualisation
---

### Post by peterhull90 on 2016-10-18
I know this doesn't help, but it's running (almost) fine for me. I installed Ubuntu 16.10 on Virtual Box Version 5.1.6 r110634, with Windows 10 64 bit host. The only problem I have is that the desktop background doesn't resize when I resize the VBox window.

[edit] I used the default settings suggested by VBox except I increased the RAM to 2GB, the disk to 12GB, and selected virtio-net for networking. I used a downloaded ISO (ubuntu-16.10-desktop-amd64.iso) to install.

What system/settings are you using?

---

### Post by howefield on 2016-10-18
Post moved to its own thread.

The desktop itself or the wallpaper ?

Do you have guest additions installed ?

---

### Post by peterhull90 on 2016-10-18
> **howefield said:**
> Post moved to its own thread.

That confused me!

It's the desktop background that doesn't resize and the launcher icons get corrupted. I actually posted it [here]("http://askubuntu.com/questions/836982/how-to-use-ubuntu-as-a-guest-os-in-virtual-box-full-screen") previously. I do have the guest additions installed and I am sure they're working 'somewhat'; without them the window doesn't resize at all.

Thanks for any help/advice!

[IMG]https://i.stack.imgur.com/ZpHy1.jpg[/IMG]

---

### Post by ajgreeny on 2016-10-18
I had big problems with the VBox 5.1.x versions and the guest extensions did not work at all in some situations (shared folders, clipboard sharing, or USBs) so quickly reverted to 5.0.26, the current 5.0 version which works extremely well.

It might be worth trying the 5.0 version in your situation as well, but how you do that will depend on how you installed VBox on your host machine, and as it's a Windows host I can't help with that at all.

It may also be worth turning off 3D acceleration in the display settings of the VM as that can cause a number of graphics problems though not quite what you are seeing here.

---

### Post by peterhull90 on 2016-10-18
3D acceleration was already turned off (I also tried it turned on, which didn't change the situation)

Good point about 5.0.x - I can't remember now if I had an actual problem that was solved by 5.1.x, or whether it was just my eternal quest for the latest and greatest (same reason I installed Ubuntu 16.10, I suppose :rolleyes: )

---

