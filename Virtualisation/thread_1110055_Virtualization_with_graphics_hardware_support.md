---
title: "Virtualization with graphics hardware support???"
date: 2009-03-29
forum: Virtualisation
---

### Post by electrontau on 2009-03-29
I am running the 64bit version of Ubuntu 8.10 and want to have a virtual Windows. The virtual Windows needs to be able to use the full potential of my graphics cad. I tried VMWare but it seems to emulate the graphics.

Suggestions anyone???

---

### Post by Johnny19734 on 2009-03-29
Tutorial for Ubuntu as guest on Windows host or vise versa !

Go to [http://download.virtualbox.org/virtualbox/2.2.0_BETA1/](http://download.virtualbox.org/virtualbox/2.2.0_BETA1/)

Download it!

First thing, install the damn thing, set up the HD, whats type of system then install. Easy for techs, you will have no issues.

Now, your going to want to enable 3d acceleration and  sound card in virtual box image settings. Right click on the virtual machine and go to settings.

(After you PUT the CD in the physical drive)Then mount the Ubuntu CD when you launch the virtual environment. Its under devices, THEN INSTALL THE BEST OS !

After installation do all the updates. If you load the video driver then do the updates, you will have to reload your video driver again because it changes kernels in the updates.

Now comes the tricky part follow :

Launch the OS, then in the window under devices launch "install guest additions" This will mount the your special virtual drivers!

Now we have to install them.

For Windows just run the executable from mounted drive. 


Ubuntu installation is never easy unless it in repository :(

Next, open terminal.

Your going to CD to the location of the mounted  drivers.

Type: cd /media/cdrom0

Now your going to install the package the fits your system. Most likely it 32 bit.

Type:  LS

This will give you a list of available executable packages. Copy the the package the fits your guest machine.

 Now Type: ./VBoxLinuxAdditions-x86.run (32bit) ubuntu
           ./VBoxLinuxAdditions-amd64.run (64bit) ubuntu


Restart your guest machine and voila! Have fun guys

Pe@ce - JJ

---

