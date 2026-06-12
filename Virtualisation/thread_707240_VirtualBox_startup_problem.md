---
title: "VirtualBox startup problem"
date: 2008-02-25
forum: Virtualisation
---

### Post by madkid on 2008-02-25
Hello. I'm attempting to run VirtualBox under Ubuntu 7.04. Every time I try to load the virtual machine, I get an error message telling me that their is a driver or something running on a different version of VirtualBox, but I only have one version installed. How do I get around this so that I can install and run Windows 98 in it?

Here is the error message I get.


The VirtualBox support driver which is running is from a different version of VirtualBox. You can correct this by stopping all running instances of VirtualBox and reinstalling the software..
VBox status code: -1912 (VERR_VM_DRIVER_VERSION_MISMATCH).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 I've already attempted to reinstall it to no avail.

---

### Post by Arwen on 2008-02-25
I [googled ]("http://www.google.gr/search?hl=el&q=Virtualbox+VERR_VM_DRIVER_VERSION_MISMATCH&btnG=%CE%91%CE%BD%CE%B1%CE%B6%CE%AE%CF%84%CE%B7%CF%83%CE%B7+Google&meta=")  it and according to [this]("http://www.virtualbox.org/ticket/425") it's an old kernel module version that causes that problem.I'm sorry I can't help you furthermore,strange VBox status codes aren't sth I like to mess with(I usually get errors in VB when I try to install older distros.)
Good luck!

---

### Post by snow_56767 on 2008-02-29
Hi,
   One thing you should try doing is downloading VirtualBox-1.5.4_OSE.tar.bz2 from either [http://www.softpedia.com]("http://www.softpedia.com")
in the linux section and make sure it is the source not the ubuntu package. And then extract it onto your desktop or were ever your downloaded files go. Then open the terminal and tap into the extracted folder and run configure.
```
./Configure
```
Then it will tell you what to do, just make to pay attention to the status of your configure (in other words, watch it). after doing what it said to do, then restart your computer and report back! :)

---

