---
title: "trying to install a minimal X/windows manager on Ubuntu server -- can't open display"
date: 2010-09-18
forum: Server Platforms
---

### Post by dash86no on 2010-09-18
Hi, 

I am trying to set up a very minimal X on my 10.04 64 bit version of Ubuntu running nothing but Open SSH and acting as a firewall/router, making a PPP connection. 

The reason, is that I want to set up KVM/Qemu and run a virtual machine. The virtual machine will have a graphical environment and will be connected to my TV so that I can watch movies, stream TV etc. using it. 

So far, I have done the following:

sudo apt-get install xserver-xorg xserver-xorg-core miwm

When I try to run miwm the error message is:

(null): can't open display. 

I have no DISPLAY variable set, but even when I set one myself using export DISPLAY=:0.0 it makes no difference. 

Can anyone give me pointers as to what I might be doing wrong?

Thanks.

---

### Post by CharlesA on 2010-09-18
It would be easier/better to just forward X over SSH.

```
ssh -x user@host
```

The only way you can pipe the video output to the display is to run in "full screen" mode, but that requires at least a desktop environment.

Check out LXDE or XFCE as they are lighter then Gnome or KDE.

---

### Post by dash86no on 2010-09-18
> **CharlesA said:**
> It would be easier/better to just forward X over SSH.

```
ssh -x user@host
```

The only way you can pipe the video output to the display is to run in "full screen" mode, but that requires at least a desktop environment.

Check out LXDE or XFCE as they are lighter then Gnome or KDE.

Thanks for your reply.

Actually, miwm is a windows manager. My understanding is this is the best thing to go for if you're looking for lightweight. Do I still need to install a desktop manager to get this to work? 

Quick update--I set up a virtual machine and managed to replicate the error. Installing gnome-desktop-environment to the server solved the problem as I was able to start x. However, I'm really trying to avoid installing something so bloated on my server. 

Thanks.

---

### Post by Bachstelze on 2010-09-18
You can start X with the command.... [font=monospace]startx[/font] :)

---

### Post by dash86no on 2010-09-18
> **Bachstelze said:**
> You can start X with the command.... [font=monospace]startx[/font] :)

No, I tried that, but I have no "startx"

I'm guessing that has something to do with the fact I followed this guide [https://help.ubuntu.com/community/ServerGUI](https://help.ubuntu.com/community/ServerGUI) and installed the light weight option vs the full desktop environment. 

i.e. sudo apt-get install xserver-xorg xserver-xorg-core

i know if you install ubuntu-desktop-environment you get the startx command, but I am keen to avoid all bloat.

Thanks

---

### Post by CharlesA on 2010-09-18
Try installing LXDE and see if it'll boot into that on startup.

---

### Post by dash86no on 2010-09-18
> **CharlesA said:**
> Try installing LXDE and see if it'll boot into that on startup.

Yes, that works. 

When I install a LXDE, I notice the startx command is now present. This I think is due to xinit being installed--there is now an xinit folder in my /etc/X11

Also added in /etc/X11: app-defaults folder. I wonder if this could be something to do with it? 

I really don't want anything heavy like LXDE: I just need something with a terminal app that can draw windows on the screen for KVM (or maybe virtualbox because I'm starting to suspect KVM is not good for graphics). 

Thanks

---

### Post by CharlesA on 2010-09-18
I thought you wanted to output the video to a monitor?

If you just wanted just a window, you could just forward X over SSH.

---

### Post by dash86no on 2010-09-18
> **CharlesA said:**
> I thought you wanted to output the video to a monitor?

If you just wanted just a window, you could just forward X over SSH.

I have a server in my house up 24/7. It's connected to the TV via HDMI, and thus far I have been using the TV as a monitor in case network problems stopped access over SSH

Now I have had the smart idea to put a virtual machine on the server and use it to play movies and stream TV to my TV set. 

So forwarding over SSH is not an option. 

I have made progress of sorts. I installed:

sudo apt-get install xinit

Then i edited /etc/X11/xinit/initrc

to add the line:

miwm


Now when I startx, a mouse pointer appears on the screen. If I right click, a menu also comes up. However, if I try to launch any program, I cannot. I'm thinking that it just isn't writing windows to the screen for some reason. 

I tested and found the same thing happened with openbox

Any ideas?

Thanks

---

### Post by CharlesA on 2010-09-18
I'm guessing you need the full GUI installed to do what you want to do.

That's the only way you can install a VM and get it to run full screen, as far as I know.

---

### Post by dash86no on 2010-09-18
OK this is solved:

I just needed to replace the miwm line in xinitrc with miwm-session

Also, you need to make sure you install xterm. 

To summarize, if you follow the [https://help.ubuntu.com/community/ServerGUI](https://help.ubuntu.com/community/ServerGUI)

guide, (minimum installation) then you also will need the additional commands to get things working:

sudo apt-get install xinit xterm

Then you need to manually edit the /etc/X11/xinit/xinitrc file to add, for example, miwm-session if you want to use miwm or I guess something like openbox-session if you want to use openbox. 

Thanks for you help everybody.

---

### Post by CharlesA on 2010-09-18
Awesome. Thanks for the info. :)

---

