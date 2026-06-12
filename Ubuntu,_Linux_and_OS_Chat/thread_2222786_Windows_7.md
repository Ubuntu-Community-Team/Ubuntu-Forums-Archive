---
title: "Windows 7"
date: 2014-05-08
forum: Ubuntu, Linux and OS Chat
---

### Post by Thomas_Rutherford on 2014-05-08
I have just converted to Ubuntu 14.04 LTS the other day accidentally wiping Windows 8 and all of my content. However feeling like a complete moron because I study computing at university I wouldn't expect such a fatal mistake, although in my defence the messages that appeared whilst installing Ubuntu were misleading to say the least and resulted in the loss of my OS and data.

As I am studying computing at university, the core programming language I'm learning is C# and need a way to gain access to Visual Studio. I am aware there is another piece of software called Mono that offers some of the same functionality that Visual Studio offers, but it is not the same and part of my course is learning out to use Visual Studio.

Would anyone be able to tell me how I could run a Windows 7 virtual machine inside of my Ubuntu OS, it would be much appreciated.:smile:

---

### Post by ian-weisser on 2014-05-08
Install the 'virtualbox' package.
Open VirtualBox.
Use the Windows 7 install media (you provide) to install a Win7 guest onto the Ubuntu host.

---

### Post by keithcleaver2010 on 2014-05-09
> **ian-weisser said:**
> Install the 'virtualbox' package.
Open VirtualBox.
Use the Windows 7 install media (you provide) to install a Win7 guest onto the Ubuntu host.

To add to that advice, when you do setup your VM, be aware of how much RAM you have in your PC, and how much of that you can spare to the VM, and whether it will be enough for you to run Visual Studio. I tried to setup a VM with win 7 with 1.5G (of my 4GB) of RAM, and it ran fairly slowly for me. Gave up on it after a day.

---

