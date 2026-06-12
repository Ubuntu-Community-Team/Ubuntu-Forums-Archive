---
title: "Restart display driver in WMware workstation"
date: 2014-01-04
forum: Virtualisation
---

### Post by matsmath on 2014-01-04
I am running Ubuntu 64 bit on WMware workstation (host OS is Windows 8.1). My display driver/hardware was ``stopped responding and has recovered'' in Windows, and even though Windows is working perfectly, as a consequence of this I lost all display in WMware (Ubuntu is static black). It seems, based on the CPU and memory consumptions, and the change of mouse pointers at certain places (e.g. at the edge of various windows, etc.) that Ubuntu did not crash, but I have no idea what it is doing.

I want to restart the display, or at least get access to my system and see what is going on remotely, but I absolutely do not want to stop any of the running processes whatsoever.

I am thinking of ssh-ing to my account remotely, but I have no idea how to do that? Is it possible at all?

OR

I just want to ``forward'' my screen to a new channel, e.g. to an external display, or a new window manager in ubuntu. I am thinking of using the alt+ctrl+F1, etc. tty's, and then give some commands (what?) but under WMware these hotkeys (since they contain alt+ctrl together) do not work.

Any ideas how to salvage my system? Seems like a challanging task.

---

### Post by TheFu on 2014-01-05
In order to ssh in, the machine must be running an ssh-server already. If this is a desktop machines image, then ssh-server probably was not installed, turned on, or running.  From Windows, putty is the tool most people use for ssh.  From UNIX/Linux, the command is "ssh".

Display drivers are almost always built as a kernel module, so to restart them, you'd need to restart the OS.

I haven't used VMware-anything in a few years, but it used to be that "saving state" was possible with the commercial versions like workstation. However, if the machine state is saved, then that would probably include the bad state of the virtual GPU driver.

So ... it appears you'll have a next to worthless machine until you restart it.

---

