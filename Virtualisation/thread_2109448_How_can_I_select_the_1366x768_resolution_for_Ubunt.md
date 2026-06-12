---
title: "How can I select the 1366x768 resolution for Ubuntu in VMware Player?"
date: 2013-01-27
forum: Virtualisation
---

### Post by MacGoose on 2013-01-27
Running Ubuntu 12.10 on VMware Player 5.0.1 build-894247. I have installed the VMware Tools and can choose the resolution 800x600 and up to 2560x1600. So I have a fair amount of resolutions to choose from.

But my laptops native resolution, and the one that Windows 7 is running on, is 1366x768. Why can't I get that resolution in Ubuntu on VMware? Those 3 extra pixels on each side is very annoying - especially when the mouse pointer moves there and directs the input outside Ubuntu.

Is there any way to edit the resolutions I can choose from in Ubuntu so I can get true fullscreen for my laptop?

---

### Post by Udayan C on 2013-01-29
Hey!

What it seems is that you didn't install the drivers for VGA for Ubuntu...if so then it will take a standard driver for display and won't support higher resolution. 

To check:
go to System Settings icon on right hand top corner -->  Under Settings >> Go to Details 

Check for Graphics .... if it says Unknown then you need to install one to support higher resolutions

Hope this info works for you.

Udayan C

---

### Post by MacGoose on 2013-01-29
Thanx for your reply and I will check that later.

But "higher resolutions" I don't have any problems with.  I can choose up to 2560x1600 and that is a high resolution.  It's the resolution in between I have a problem with - especially the 1366 width.

---

### Post by dcstar on 2013-02-04
> **MacGoose said:**
> 
..........
Is there any way to edit the resolutions I can choose from in Ubuntu so I can get true fullscreen for my laptop?

What happens when you expand the VM screen with the mouse of simply maximise it?

On my system the VM scales to whatever size you stretch it to.

---

### Post by MacGoose on 2013-02-05
> **dcstar said:**
> What happens when you expand the VM screen with the mouse of simply maximise it?

On my system the VM scales to whatever size you stretch it to.

Thanx.  Running it in windowed mode made Ubuntu resize its screen to whatever the size of the window.  So starting up Ubuntu from windowed and then choosing full screen got me the true fullscreen of 1366x768.

And now I can choose that resolution in the setting.  However, when I now start up Ubuntu with a 1366x768 resolution it fails with an error that the monitor doesn't support that resolution.

Still not sure if it's Ubuntu or VMware Player that has issues with this though.

---

