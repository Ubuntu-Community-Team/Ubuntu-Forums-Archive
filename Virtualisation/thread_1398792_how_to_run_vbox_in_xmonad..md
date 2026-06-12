---
title: "how to run vbox in xmonad."
date: 2010-02-04
forum: Virtualisation
---

### Post by bdws1975 on 2010-02-04
I recently installed xmonad and am loving it.  I love the simplicity of the interface, etc.

I have to run windows in vbox for some .net framework apps for my company. 

is there a way to use vbox in xmonad?  I've installed dmenu and have looked through everything I can find.  No dice.

Any help is appreciated.

Thanks,

Brett

---

### Post by bdws1975 on 2010-02-04
ok, here's what I did.  Is it a 'good' way to do it or should I be doing something else:
 
logged in in xmonad.
 
opened a terminal and entered 'gnome-open Desktop' where the icon for vbox is.  I double clicked on vbox, opened my VM and it's now running.  I disabled mouse integration so I could change the window algorithm.  It seems to work great.
 
Any thoughts?  I'm new to all this, but it's a blast.
 
thanks,
 
brett

---

### Post by falconindy on 2010-02-05
The executable is called VirtualBox. Notice the case. Depending on how you launch dmenu, you can alter this functionality to search case-insensitively.

Happy tiling!

---

### Post by bdws1975 on 2010-02-05
awesome!  you got it!  Thanks a bunch.

Brett

> **falconindy said:**
> The executable is called VirtualBox. Notice the case. Depending on how you launch dmenu, you can alter this functionality to search case-insensitively.

Happy tiling!

---

### Post by tim0804 on 2010-03-19
a better way to start VirtualBox is - VBoxManage startvm "the name of your virtual machine." If you type this command at a prompt the command processor launches your virtual machine and then releases the terminal. if you set up an alias or a script it is even easier.

Jusr be sure to have at least one terminal open on the screen in addition to the VM, if you use xmonad so you don't lose the ability to navigate from one screen to another.

---

### Post by kevr on 2010-11-07
If you open the VirtualBox UI, go to File->Preferences, go to Input, and uncheck the automatic keyboard input. If you do this, you will not need a terminal to navigate desktops.

---

