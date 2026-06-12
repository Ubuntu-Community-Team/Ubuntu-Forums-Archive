---
title: "Controling VirtualBox window with compiz"
date: 2008-03-02
forum: Virtualisation
---

### Post by Sasa Sijak on 2008-03-02
I`m trying for a few hours now to make my guest XP system run on boot in second workspace fullscreaned. I added the command to start-up "virtualbox startvm "XP"" and it is ok. But when I try in compiz Place Window plugin to place it on other workspace it just wont listen. I xprop-ed the VM window and it says : name=VirtualBox, class=VirtualBox. I used that in Place Window to place it on secon workspace but it appears on that workspace just for a blink of a second and than gets back to the initial first workspace. I cant get it right :/ One interesting thing is that when I try to close that guest system on "X" in the window corner, that promt asking if I want to power off my guest system appeares on the wanted second workspace :/ And also how can I tell the guest system to start automaticly in fullscreen? I tried with Compiz Window Rules but didn`t get it to work. Maybe there is a terminal command to start VM in fullscreen? I know that there is similar topics here, but I have read them all and could not solve my problem. Thanks in advance.

---

### Post by Sasa Sijak on 2008-03-04
Anybody please? :(

---

### Post by Hero of Time on 2008-03-11
Man VBoxManage or VBoxManage --help should give the proper help for your problem. The point is that VirtualBox doesn't start a VM, but VBoxManage does. If you read the Manual, you could have read that if you want to start a VM from CLI, you need to call VBoxManager startvm "VM Name".

---

### Post by sirlancelot on 2008-09-28
Sorry to dig up this thread, but I've got the exact same problem.

1. Configure Compiz Fusion's "Place Windows" plugin to move (class=VirtualBox) to workspace 2.
2. Start VirtualBox via $ VBoxManage startvm "Windows XP"
3. VM Window appears on desired workspace, but almost instantly moves to the current workspace.

Anyone able to offer answers?

---

### Post by t1010011 on 2008-12-27
> 
**sirlancelot**:
Sorry to dig up this thread, but I've got the exact same problem.

1. Configure Compiz Fusion's "Place Windows" plugin to move (class=VirtualBox) to workspace 2.
2. Start VirtualBox via $ VBoxManage startvm "Windows XP"
3. VM Window appears on desired workspace, but almost instantly moves to the current workspace.

Anyone able to offer answers?

Same here....

---

### Post by Dedoimedo on 2008-12-28
I'll check at home later today or maybe tomorrow, see what gives.
I'll try to recreate your issue.
Dedoimedo

---

### Post by t1010011 on 2008-12-28
My theory is that during the virtual Windows XP boot there seems to be a lot size changes in the VirtualBox window of and it somehow messes up with Place windows. 

Managed to solve the issue by launching 
```

ccsm
```

and then under Window Rules

setting:
Maximized class=VirtualBox

and that solved the problem for me....

but before I also used:
Skip taskbar class=VirtualBox
Skip pager class=VirtualBox

I think those are not necessary to solve the bug, only a matter of taste...

---

### Post by t1010011 on 2008-12-29
Have another problem...
When I maximize a window in the guest Windows XP my Gnome panels in the Ubuntu host disappear.

When the window is restored they come back though...

See attachments:

---

