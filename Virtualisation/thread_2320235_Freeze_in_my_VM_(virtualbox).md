---
title: "Freeze in my VM (virtualbox)"
date: 2016-04-11
forum: Virtualisation
---

### Post by floown on 2016-04-11
Hello,
My host is a Windows 8.1 and I have installed a Kubuntu in a guest VM (Virtualbox). The problem I have is that Kubuntu freeze sometimes and I can not click on any button or interface element in the GUI. The keyboard is not frozen so I can quit proprely my VM with a sudo reboot now.

Where can I search the bug, for perhaps correct this issue?

Thx for your help

---

### Post by SeijiSensei on 2016-04-11
How much memory did you allocate to the virtual machine?  I give desktop Ubuntu versions 2 GB and the server version 1 GB.  I have 8 GB of physical memory.

If the Windows host becomes starved for memory, it may start trying to swap out parts of memory.  The next time the VM freezes, look at the hard drive indicator light and see if it is continuously flashing.  If so, Windows is swapping and will pay less attention to the desktop tasks as a result.  One of them is the virtual machine.

In the Kubuntu VM, open a Konsole and type "top" at the prompt.  You'll get a constantly updated display of CPU and memory usage and a list of the most active processes.  That will help diagnose any problems on the Linux side.  If the machine appears to freeze, but top continues to update, then it's likely the problem is on the Windows side.

I generally like to run Linux as the host OS and Windows in a VirtualBox.  I think Linux is more stable and has better performance.  When Linux is hosting a VM, it's largely running as a server, a task Linux is ideally suited for.

---

### Post by bapoumba on 2016-04-15
*Thread moved to **Virtualisation**.*

---

### Post by linuuxi on 2016-04-15
> **SeijiSensei said:**
> ...

**I generally like to run Linux as the host OS and Windows in a VirtualBox.  I think Linux is more stable and has better performance.  When Linux is hosting a VM, it's largely running as a server, a task Linux is ideally suited for.**

Thanks for this great advice. It's something many (including me:tongue:) might neglect easily.

---

