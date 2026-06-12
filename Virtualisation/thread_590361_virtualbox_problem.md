---
title: "virtualbox problem"
date: 2007-10-24
forum: Virtualisation
---

### Post by Tucatts on 2007-10-24
Have it installed and it starts ok then I get this:

VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel and execute '/etc/init.d/vboxdrv start' as root.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 I installed from synaptic package manager. What else do I need to do to find the required drivers?
Thanks!!!!

---

### Post by DagMan on 2007-10-24
Does it work if you do this?
```
sudo apt-get install --reinstall virtualbox-ose-modules
sudo modprobe vboxdrv
```
With the modprobe thing, I don't know if that's still the correct name of the module though because I'm still using a build from feisty that I got elswhere.

---

### Post by Tucatts on 2007-10-25
Nope, didn't work, still get the same message. Thanks for the help, at least have eliminated one possible cause. This will take some more research, lol. Anybody else have an idea? 
Many thanks!

---

### Post by basic0 on 2007-10-25
```
sudo /etc/init.d/vboxdrv setup
```

I've had to run this every time my kernel got updated from Feisty to Gutsy development to Gutsy stable. It might solve your problem.

---

### Post by Tucatts on 2007-10-25
After trying the following:sudo /etc/init.d/vboxdrv setup I got this:

 * Usage: /etc/init.d/vboxdrv {start|stop|restart|status}

 Not sure what that means but the same problem does persist. One more thing eliminated I guess!  Onward and upward!

---

### Post by basic0 on 2007-10-25
Hmm that tells me that for whatever reason, your vboxdrv init script doesn't do "setup". Are you running the latest version of VirtualBox? AFAIK the latest major release is 1.5.0 and it adds support for "seamless" mode with the host OS's desktop. It's pretty nifty.

.deb packages are available at:
[http://www.virtualbox.org/wiki/Downloads]("http://www.virtualbox.org/wiki/Downloads")

---

### Post by Tucatts on 2007-10-25
Thanks for the reply. I have the latest apparently 1.5.0.. I installed it from add/remove programs on this new Gutsy insatll. Infact I have installed and uninstalled twice to see if maybe I had a bad install but still get the same response.

---

### Post by basic0 on 2007-10-25
I've always installed/updated VirtualBox manually by downloading the .deb package from their website, that's the only major difference I can see between us. You might want to have a look at [http://www.ubuntugeek.com/create-and-manage-virtual-machines-using-virtualbox.html]("http://www.ubuntugeek.com/create-and-manage-virtual-machines-using-virtualbox.html"), it's a little outdated, but it was my introduction to VirtualBox and it's still a decent overview of installing it.

---

### Post by Tucatts on 2007-10-25
Hey, sounds like a plan. Thanks for the help. Linux is a bit of a puzzle, lol. I enjoy solving all the stuff you run into. When you have finished and the OS is actually running like you want it too it's like you had a real part in building it. Not just something you took out of the box and wentfor a coffee while it does all the work for you, lol. 
I will try your suggestion  now and see what happens. Again thanks for the response.

---

### Post by jualin on 2007-10-26
I had the same problem and followed the steps and now it works like a charm. The only thing is that after adding a user to the vboxusers groups, the computer has to be restarted, but after that it works.
Thanks for the posts!

---

