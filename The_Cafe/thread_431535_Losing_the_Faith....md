---
title: "Losing the Faith..."
date: 2007-05-03
forum: The Cafe
---

### Post by GSF1200S on 2007-05-03
Im sure youve all probably seen me around the forums lately.. asking tough questions and stupid ones. But you know what? After all this investment, im beginning to lose the faith.

So im running in KDE, but ive got an issue.. programs wont load half the time. Im told by posts that WACOM entries in the Xorg.conf are to blame. So, I # them out and restart x.. and I still have the problem. So I decide on a hard reboot, because I havent got any replies on my post and I hope that just maybe it will do something. Upon rebooting, my xwindow fails to load. So a sudo dpkg-reconfigure -phigh xserver-xorg later, im on NV drivers preparing to reinstall my NVIDIA drivers and my madwifi drivers. I kill x (sudo /etc/init.d/gdm stop), and install the drivers. startx, and xwindow still fails to load- this with a new Xorg and a new driver install. Tried it once more, and the same thing happened. Figuring Id check the forums, I went to install my madwifi drivers like I did every time a new kernel release or xorg release came as an update (dont ask me what the Xorg has to do with wireless). I installed them twice, both times with a reboot, and no wireless. So, I hook up to a cable, and boot KDE to browse firefox for a solution.

But guess what? Firefox wont load.. Wacom issues remember? So, ctrl alt backspace, and on to Gnome I go. About 5 minutes into browsing the net for solutions, GNOME freezes, and I have to do a hard power off. For some reason, XFCE wont go on the net.

So, here I am on windows, seriously considering a wipe of my linux partition. Im not really asking for technical advice... I know how Ive fixed it since Ive started.. it just magically doesnt work anymore.

Im frustrated like mad guys...

---

### Post by DoctorMO on 2007-05-03
It seems like you have a rather unfortunate set up and experience.

I had a wacom tablet, didn't work until feisty and the troubles I had compiling the kernel to get it working. I ended up just waiting for feisty and you know what works perfectly.

Nothing in this world is perfect, linux draws me because it's ethical no really because it works all the time.

You take your choices.

---

### Post by SunnyRabbiera on 2007-05-03
maybe its feisty...
maybe you should try another distro too as ubuntu is not the only one out there

---

### Post by Sammi on 2007-05-03
You could try to reinstall Ubuntu. The clean slate option seems to work for many. Maybe you installed from a corrupt CD. Try to do a full check from the menu when you boot the CD. Maybe :-k

It's definitively a last resort though.

---

### Post by use a name on 2007-05-03
You could check for ram problems. I was surprised to find that to be the cause of a lot of problems a few weeks ago. The system ran, but certain tasks were more prone to error than others.

---

