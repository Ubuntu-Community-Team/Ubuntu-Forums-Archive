---
title: "Virtualbox starts windows in invisable mode"
date: 2008-05-31
forum: Virtualisation
---

### Post by Robbyx on 2008-05-31
Using HH with VB 1.5.6 it all works but I am having problems seeing the virtual machine. It starts up and loads the image and then the image disappears. I have never been able to work with seamless mode that also causes the screen to disappear. I am using two monitors.

It looks as if the VM is displaying in an invisable screen but I can not find it.

Short of reseting the vm each time how do I get my visual screen back? Ctrl L does nothing, but then I have not worked out how to use it if the VM screen is not present.

Robin

---

### Post by Robbyx on 2008-06-01
It would be very helpful if I had some response because starting in seamless mode  is making it very difficult to use VB.

---

### Post by oomlout on 2008-06-03
I have the same problem: when I switch Vbox to 'seamless mode' everything disappears.  I've tried moving the bottom panel elsewhere, in case it is covering up the windows 'start' menu/panel, but to no avail.  I'm running 8.04 Xubuntu with 2 monitors.

---

### Post by starcannon on 2008-06-04
before you switch to seamless mode open a windows, I use notepad.

Then I just make it as small as I can by resizing (minimizing will not work for this kludge).

Now Press rCtrl-L and eureka the window stays happy.

Its a known bug, and this is a work around I read about somewhere out there.

Enjoy.

p.s. long story short, seamless mode requires a MS window to be open or it flakes out.

---

### Post by Robbyx on 2008-06-04
Thank you for your help. My own specific problem has been solved by only starting in full screen mode. This way the screen does not disappear when loaded. However I can not switch to seamless mode there after. I press rctrl home and choose seamless and nothing happens. I also tried rctrl L and there was no response. Probably due to due screens?

Robin

---

### Post by Robbyx on 2008-06-04
oomlout:

My solution of only using full screen mode is achieved whilst the virtual machine is loading. Before windows has loaded, I quickly go to the file settings and click on full screen mode. I have found in subsequent reloads it remains at full screen.

Robin

---

### Post by oomlout on 2008-06-04
After some more experimentation, I have a different flavor of the problem.  Before, I was trying to go into seamless mode on my 2nd monitor, which has the effect of everything disappearing (and yes, I already had an app running).

Now, when I go into seamless mode, my windows toolbar (i.e. the thing with the 'start' menu) remains stuck where it was before I switched.  It doesn't move to the bottom of the screen as I expected. And running apps are limited position-wise to the boundaries of the old VirtualBox guest window.

Also, it's disappointing that I can't run seamless on my 2nd monitor.

---

