---
title: "Keyboard dead in VBox 4.0"
date: 2011-01-04
forum: Virtualisation
---

### Post by Palmstroem on 2011-01-04
Hello, virtualizers around,

I am running VirtualBox 4.0 with the extension pack under 64bit Ubuntu Lucid. The virtual machine is 32bit Windows XP SP3. It works but sometimes (!) my keyboard is just dead - in VBox only, not in the host. By the way, the keyboard is connected to the PC via USB.

Any suggestions? Thanks in advance.

---

### Post by Palmstroem on 2011-01-05
Hello again,

I found out that the described effect (keyboard in the guest becoming unresponsive) happens after the screensaver of the host system has come up. Also, when this occurs it is no longer possible to print from the guest via the host. A bug?

---

### Post by Santos1204 on 2011-01-11
Mine is exactly the same, only started happening yesterday although I've been running VirtualBox 4.0 r69151 with ubuntu 10.10 and a host windows 7 machine. 

I find that as soon as the host machine goes into screensaver the keyboard within the guest machine stops working. The only way to get control of the keyboard in the guest machine is to type something in the host.

---

### Post by Palmstroem on 2011-01-13
Thanks Santos1204,

at least I am not the only one with that problem! By the way, is your host a 64 bit system?

Anyone else? Solutions?

---

### Post by thomlark on 2011-01-13
Hello. I'm another VirtualBox 4.0 user on Ubuntu 10.04 (32bit) who is having the keyboard lose connection to client (any client).

I can get the keyboard back by going to host and entering something into a teminal window.

Is anyone working on fixing this bug?

It seems a lot of people have this problem!

---

### Post by jualin on 2011-08-17
> **thomlark said:**
> Hello. I'm another VirtualBox 4.0 user on Ubuntu 10.04 (32bit) who is having the keyboard lose connection to client (any client).

I can get the keyboard back by going to host and entering something into a teminal window.

Is anyone working on fixing this bug?

It seems a lot of people have this problem!

If you look at it closely, the keyboard is working correctly but the "Alt" key is "being held." For example, if you open the "Run" utility and press "B" it will open "Browse." Normally it should only open "Browse" by pressing Alt+B.

The solution that I found was to press the "Alt" key several times and try typing again on the Windows Host. 
I am running Ubuntu 11.04 and VirtualBox 4.04.
Hopefully this helps :)

---

