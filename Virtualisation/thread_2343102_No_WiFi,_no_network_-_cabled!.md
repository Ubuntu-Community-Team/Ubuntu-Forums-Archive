---
title: "No WiFi, no network - cabled!"
date: 2016-11-13
forum: Virtualisation
---

### Post by tjsilver on 2016-11-13
Hello,

I've installed Ubuntu 16.04 LTS as a virtual machine in Windows 10 Pro but I have no wifi (thought it rather strange that 'get updates' was greyed-out during installation).  I've connected to my router using a cable but Settings says cable unplugged. So I cannot get updates.  Help please - I haven't a clue what to do!

Dell Inspiron 17, Intel i5-3337U 1.8GHz, 6GB RAM, Windows 10 Pro 64bit; Ubuntu 16.04 LTS (reports only 4GB RAM) 64bit.

---

### Post by jeremy31 on 2016-11-13
*Thread moved to **Virtualisation**.*

---

### Post by wildmanne39 on 2016-11-13
Your guest system uses your hosts internet connection it does not use its actual hardware, so if you have an internet connection in the host it should work in the guest even if that connection is wifi, in the host it will show as an ethernet connection in the guest.

When you setup the vm you setup your network settings in the vm program you are using at the time of installing the guest, I use virtualbox and the settings I use are default I do not have to change any settings. You did not say what vm program you are using but I am going to post a screenshot of my settings.

There is one exception to the internet using the hosts connection and that is if you use an usb adapter you can then set the wifi up in the guest using the usb adapter but not an internal one.

---

### Post by kpatz on 2016-11-13
What VM software are you using to host your VM?  Virtualbox, VMWare, something else?

---

### Post by tjsilver on 2016-11-13
Thanks for reply.  I'm using Windows inbuilt Hyper-V.  A bad choice?

---

### Post by wildmanne39 on 2016-11-13
Even though you are not using virtualbox the settings for your netwwork should be about the same.

I do not know if you will find anyone here that knows anything about a windows virtual program.

---

### Post by jeremy31 on 2016-11-13
But microsoft has some online help for hyper v [https://technet.microsoft.com/en-us/library/jj945275.aspx](https://technet.microsoft.com/en-us/library/jj945275.aspx)

---

