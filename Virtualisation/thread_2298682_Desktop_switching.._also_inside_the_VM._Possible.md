---
title: "Desktop switching.. also inside the VM. Possible?"
date: 2015-10-13
forum: Virtualisation
---

### Post by simba4 on 2015-10-13
Hello there,

I am ~new to ubuntu but not new to computers.


I would like to "jump" from the desktop to the VM (Windows) APP by clicking a shortcut that I set through the keyboard shortcuts module.


The shortcut (CTRL-ALT-1) up to (CTRL-ALT-4) does work within the ubuntu desktops, but while inside the VM (Window) screen, it does not respond.


Is there a way to make it respond while I'm inside the VM windows?


Thank you, 


James

---

### Post by howefield on 2015-10-13
While inside the VM try pressing the right Ctrl key before executing your shortcut.

---

### Post by simba4 on 2015-10-13
Thanks mate.
That actually did it.

James

---

### Post by howefield on 2015-10-13
> **simba4 said:**
> Thanks mate. That actually did it.

I know, and you're welcome :)

---

### Post by simba4 on 2015-11-02
OK, I came back with another (related) problem.

Well, Right-CTRL do re_Call the host system in order to switch the desktop, But..

On the VM, I work with a script that needs a certain application's sub_menu (right_click) to stay open while I switch the desktop.

The problem is that when I click Right-CTRL, that sub_menu closes. 

Is there a trick to go around this issue?

James

---

### Post by howefield on 2015-11-02
Try remapping the Host Key Combination..... Virtualbox > Preferences > Input > Virtual Machine tab.

---

### Post by simba4 on 2015-11-02
OK, I did what you taught me to do. Obviously it worked.
But then, I realized that I can solve my problem in another way.

Basically, all I wanted is to watch TV (Kodi aka XBMC - a Linux app) while watching graphs movements (A 'stock trading' - Windows app) in VM full screen mode.

To make a long story short, I installed xdotool in order to call that TV app in to focus: **[FONT=arial black]xdotool search --class kodi windowactivate[/FONT]**

Also I made a custom key: shift <somthing> to call that 'xdotool' command.

BTW, I did not find any 'built in' way to call a running window's app in to focus.

Well, that ''xdotool" does the jobs, but if there is a 'built in' way, I'd like to hear about it.

Dear howefield, thank you very much for your help and patience.
I hope that one day, I will be able to repay the favor.

James

---

