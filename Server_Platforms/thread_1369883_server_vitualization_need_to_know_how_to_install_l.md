---
title: "server vitualization need to know how to install libsdl"
date: 2010-01-01
forum: Server Platforms
---

### Post by robertsaron on 2010-01-01
Installed ubuntu server 9.10 32 bit. Want to use this as a KVM. Then install virtual box. Virtual box will allow a gui to be used in a command line form of linux if the libsdl or another package is installed. These will then allow a GUI of virtual box to be used even if Gnome or KDE are not installed. 

The documentation for virtualbox, does not say how to do this. Any ideas or suggestions on this? For now installing KDE until I can figure it out.

---

### Post by kiranmurari on 2010-01-05
[SIZE=2]VirtualBox has command line tools to manage guest systems. It also provides the VirtualBox Remote Desktop Protocol (VRDP) to allow connection to the guest remotely. Using VBoxManage, you can create new VMs and manage their configuration etc. Using VBoxHeadless, you can start a VM to manage it remotely.[/SIZE] [SIZE=2]Please refer following links on how to install VirtualBox on server platform and
manage the VMs remotely.[/SIZE]
       [SIZE=2][http://burnz.wordpress.com/2008/09/04/how-to-setup-headless-xvm-virtualbox-on-ubuntu-server/](http://burnz.wordpress.com/2008/09/04/how-to-setup-headless-xvm-virtualbox-on-ubuntu-server/)[/SIZE]
       [SIZE=2][http://www.howtoforge.com/vboxheadless-running-virtual-machines-with-virtualbox-2.0-on-a-headless-ubuntu-8.04-server](http://www.howtoforge.com/vboxheadless-running-virtual-machines-with-virtualbox-2.0-on-a-headless-ubuntu-8.04-server)[/SIZE]
[SIZE=2]
PS: Please check with the options that are passed to VBoxManage and VBoxHeadless as the options might change from one version of VirtualBox to the other.

Let me know if you need further assistance.

Regards,
Kiran
[/SIZE]

---

### Post by whit on 2010-03-18
The links you give don't speak to which libsdl package to install. Does that get pulled in by dependencies?

Also, the burnz page is all command line. The VirtualBox GUI is handier, if you're in a context to use it - at least on other host systems.

---

### Post by whit on 2010-03-18
libsdl1.2-dev

---

