---
title: "Running existing Ubuntu in Windows"
date: 2008-03-18
forum: Virtualisation
---

### Post by Trunk_z on 2008-03-18
Hey,

I've been looking for a while now to see if I can run Ubuntu from within Windows. I can already run Windows inside of Ubuntu.

It was much easier than I thought, so I figured maybe some other people would benefit from my experiance.


First, some background info:
I dual boot (using grub), Ubuntu Gutsy and Windows Vista, on my Samsung Q35 laptop. There is a shared FAT32 partition, so I can access my files on both operating systems
I've been a windows user since 3.1, and only started using Linux recently, so please excuse me if I explain things in a Windows type way.


First, I installed VMware Server and created a new Virtual Machine using the wizard (I don't usually like wizards, but this one seemed ok to me). 

Rather than selecting Ubuntu as my Linux version, I selected "Other 2.6" Kernel, as research told me that Ubuntu Gutsy was 2.6.

I selected the whole drive to be used. However, this caused problems, Ubuntu wouldn't boot, I figured out that it didn't like booting anything that my Windows was using at the time... The FAT32 partition. I disabled this in the settings for the VM (Virtual Machine).
Intrestingly though, if i use Windows inside Ubuntu, this isn't a problem for me, although it's probably a bad idea to have 2 operating systems using the same partition at the same time.

Then I had the problem that it would just give me a command prompt terminal thing, apparently no displays existed. This makes sense, as the way I think VMs work is by emulating hardware, so the drivers would be different (something along those lines).
So to fix this I had to edit the xorg file (which apparently deals with drivers and things).
To do this, I used the command: sudo dpkg-reconfigure -phigh xserver-xorg

After I completed that screen, I typed in: startx
Or you can restart, this is better, as I received error messages from Gnome if I didnt.

I then installed Vmware Tools, to do this I simply went to the VM Server menu bar along the top, and found the "Install VM Tools" option.
This mounted a CD in Ubuntu, it had a .tar file in it, I extracted this to my desktop, and read the instructions, it was very straight forward, I had to run the install file, and it was a step-by-step process.

After one more restart, I was up and running with no problems at all.

I may have missed one or two minor things, apologies if I did, it was all from memory.


Then I exited the VM Server, and restarted Windows in order to see if Ubuntu would boot. But because I had changed my xorg file, it didn't work.
I didn't have a terminal, however, pressing Ctrl + Alt + F1 gave me this. I then typed in: sudo dpkg-reconfigure -phigh xserver-xorg
and I could boot Ubuntu.


So there we go. I can run Windows in Linux, and run Linux in Windows, both from existing partitions.

It would be nice however if there was a way to do the "sudo dpkg-reconfigure -phigh xserver-xorg" command automatically on startup, I did try briefly but it didn't want to play along. I'll work on it some more I guess.
Oh, and somehow sharing a folder/drive in Ubuntu on Windows.

Comments/questions are welcome, I'll do my best to answer, hope this can help someone

---

### Post by dcstar on 2008-03-21
> **Trunk_z said:**
> Hey,

I've been looking for a while now to see if I can run Ubuntu from within Windows. I can already run Windows inside of Ubuntu.

It was much easier than I thought, so I figured maybe some other people would benefit from my experiance.


First, some background info:
I dual boot (using grub), Ubuntu Gutsy and Windows Vista, on my Samsung Q35 laptop. There is a shared FAT32 partition, so I can access my files on both operating systems
I've been a windows user since 3.1, and only started using Linux recently, so please excuse me if I explain things in a Windows type way.


First, I installed VMware Server and created a new Virtual Machine using the wizard (I don't usually like wizards, but this one seemed ok to me). 

Rather than selecting Ubuntu as my Linux version, I selected "Other 2.6" Kernel, as research told me that Ubuntu Gutsy was 2.6.
............
So there we go. I can run Windows in Linux, and run Linux in Windows, both from existing partitions.

It would be nice however if there was a way to do the "sudo dpkg-reconfigure -phigh xserver-xorg" command automatically on startup, I did try briefly but it didn't want to play along. I'll work on it some more I guess.
Oh, and somehow sharing a folder/drive in Ubuntu on Windows.

Comments/questions are welcome, I'll do my best to answer, hope this can help someone

Ubuntu installs simply as a VM within Windows, just use the preset options and you won't have to muck around with any of this.

There are numerous posts on file sharing within VMs in this forum and many other places.

In my experience, running Ubuntu within Windows is like having a sports car tow a dump truck (a dump truck loaded down with Anti-virus and other Windows bloatware), sure you can do it, but why would you?

---

### Post by analyzer123 on 2008-03-29
This is cool Trunl_z! Now I run my native Ubuntu from within Windows XP! This rocks!

---

