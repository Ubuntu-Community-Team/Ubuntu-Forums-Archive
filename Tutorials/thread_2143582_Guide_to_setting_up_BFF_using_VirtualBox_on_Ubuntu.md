---
title: "Guide to setting up BFF using VirtualBox on Ubuntu 10.04"
date: 2013-05-09
forum: Tutorials
---

### Post by shayno90 on 2013-05-09
[COLOR=#000000][FONT=Verdana]The Basic Fuzzing Framework (BFF) consists of two main parts:[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]a Linux virtual machine that has been optimized for fuzzing[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]a set of scripts and a configuration file that orchestrate the fuzzing run[/FONT][/COLOR]


[COLOR=#000000][FONT=Verdana]1.Download BFF Debian VDMK file and Fuzzing scripts:[/FONT][/COLOR]
[http://www.cert.org/download/bff/d.html](http://www.cert.org/download/bff/d.html)
[COLOR=#000000][FONT=Verdana](Latest version is 2.6)[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]2.Launch virtual box and setup Virtual Debian BFF machine:[/FONT][/COLOR]
[http://askubuntu.com/questions/14254...-on-virtualbox]("http://askubuntu.com/questions/142549/how-to-install-ubuntu-on-virtualbox")

[COLOR=#000000][FONT=Verdana]Important to select at least:[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]512mb plus for memory[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Use existing disk (point to file location of Debian vmdk image)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Use VMDK image[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]3.Continue with the rest of the setup and finally launch the virtual vmdk image.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]4. IMPORTANT (ADD YOUR USER ACCOUNT TO VBOXUSERS GROUP TO ALLOW USB DEVICE SHARING)[/FONT][/COLOR]
[http://www.techfurs.net/1/post/2011/...on-ubuntu.html]("http://www.techfurs.net/1/post/2011/09/how-to-enable-virtualbox-usb-support-on-ubuntu.html")

[COLOR=#000000][FONT=Verdana]a.Enter this into the terminal, gpasswd -a 'yourusername' vboxusers[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]b. Logout of your account then log back in.[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]c. Open up VirtualBox and USB support should be enable. Sellect the USB drive like you would on Windows.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]5.Next install Guest additions package on the virtual machine in order to mount USB device:[/FONT][/COLOR]
[http://virtualboxes.org/doc/installi...ons-on-debian/]("http://virtualboxes.org/doc/installing-guest-additions-on-debian/")

[COLOR=#000000][FONT=Verdana]a.Login as root;[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]b.Update your APT database with apt-get update;[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]c. Install the latest security updates with apt-get upgrade;[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]d. Install required packages with apt-get install build-essential module-assistant;[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]e. Configure your system for building kernel modules by running m-a prepare;[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]f.Click on Install Guest Additions… from the Devices menu, then run mount /media/cdrom.[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]g.Run sh /media/cdrom/VBoxLinuxAdditions.run, and follow the instructions on screen.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]6.Finally you need to point the virtual machine to a media directory containing the[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]fuzzing scripts in order to start the BFF testing.[/FONT][/COLOR]
[http://asimplediscipleslife.blogspot...mework-in.html]("http://asimplediscipleslife.blogspot.ie/2011/08/cert-basic-fuzzing-framework-in.html")

[COLOR=#000000][FONT=Verdana]Set up the user to use the Virtual Box group as the default group (do this on virtual machine)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]a.sudo usermod -g vboxsf fuzz[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]b. Add a symlink where the framework expects the shared folder to be installed:[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]c. cd /mnt/hgfs; sudo ln -s /media/sf_fuzz fuzz[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]d. Restart the virtual machine, and you should be ready[/FONT][/COLOR]

---

