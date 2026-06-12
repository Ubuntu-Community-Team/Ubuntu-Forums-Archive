---
title: "Apple X11"
date: 2008-04-02
forum: Virtualisation
---

### Post by atcronos on 2008-04-02
I'm running Ubuntu on my Mac using VirtualBox. I'm running it "seamlessly" using SSH -Y to connect to my virtual machine, but I encountered a wired problem. It runs with a very ugly theme, I can fix this by running Appearance from System>Preferences but when I do my keyboard configuration gets messed up and everything I type becomes gibberish. 

Also is there any way I can run OpenGL, XGL and Compiz thru ssh.

---

### Post by atcronos on 2008-04-04
I found a work around the theme problem, it works if you start the ssh connection from Terminal instead of Xterm.

1. Make sure X11 is NOT running.

2. Connect via SSH to the virtual machine thru Terminal.

3. Run "gnome-appearance-properties" from terminal.

That last command starts X11 and loads the gnome theme. Once it loads you can close the appearance window and run gnome-panel from terminal.

You should have MacOS and Ubuntu with a nice skin running together.

---

