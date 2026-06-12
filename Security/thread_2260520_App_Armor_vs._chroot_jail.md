---
title: "App Armor vs. chroot jail"
date: 2015-01-12
forum: Security
---

### Post by stick.deb on 2015-01-12
I am planning on setting up a server for mail, web hosting, secondary DNS, internal LAN DHCP, et. al.  The server WAN NIC would face the Internet.  From what I've been reading it sounds like the services with open ports should be confined to their appropriate sandboxes to limit the potential damage from intrusion.  Is chroot jailing of each service appropriate?  Is there a new best practice?  Are App Armor's restrictions comparable to chroot jailing?  I was curious if these options were recommended in combination or if they were redundant.  I realize there probably isn't really one "right" answer, but while I'm teaching myself how to build a secure server I wanted to absorb the options.  

I did find the thread [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812) to be helpful, by the way.

-Stick

---

### Post by HermanAB on 2015-01-13
Chroot is a server management tool, not a security tool.  For server management, using virtual machines may be less hassle than using chroots (chroot is kinda old fashioned with diminishing support).

On a wild wild web server, I would say that App Armor or SELinux is an essential security tool.

The problem is that chroots are hard to configure and easy to break, while virtual machines are easy to configure and easy to break...  they don't provide security.

---

### Post by thnewguy on 2015-01-13
If you want to keep your services isolated from the host, then virtual machines is the way to go. Or maybe LXC/Docker containers. chroot is hard to set up and of limited use. AppArmor is more capable, but also a huge pain to get working right. Containers and virtualization are much easier to set up and will similarly protect your host operating system.

---

### Post by kevdog on 2015-01-13
Hey guys -- just set up my first virtual machine with VB (Macbook running arch)-- YEA!! Just a quick question on this point -- if you don't set up the VM to have access to the host machine files --- isn't the VM completely isolated from the host?   This seems like a very good way to actually run servers and such while only putting the VM at risk.  There aren't any known vulnerabilities are there of a process breaking out of the VM onto the host???

---

### Post by bashiergui on 2015-01-13
> **kevdog said:**
> There aren't any known vulnerabilities are there of a process breaking out of the VM onto the host???Yes there have been some guest breakout exploits. They generate a lot of press and vendors usually patch them pretty quickly because they are the holy grail of vm exploits. 

Patching is key. 
>  if you don't set up the VM to have access to the host machine files --- isn't the VM completely isolated from the host?Just as with everything in Linux, it depends on the configuration.

You can set up vms to be isolated from each other, but they can also be set up to be highly connected. Most hypervisors provide guest <--> host passthrough tools (guest additions and various settings) which need to be configured properly to achieve isolation. There are a wide variety of virtual networking and subnetting you can do to improve isolation, too, and it is generally as complex (maybe even moreso) as physical networking.

---

### Post by stick.deb on 2015-01-14
Thanks for the responses.  Is there a VM-hosting application for command line, or would I need to run a GUI of some sort on my server?

---

### Post by kevdog on 2015-01-15
I'm no VM expert -- only done it once.  However using the VM Virtual Machine, the setup is a GUI.  I don't think setting something like a window manager like awesome or OpenBox would take that many resources.  It might be able to be done from the command line, however it's a lot more easy from the GUI.  I could see possibly something like SLiM for the login manager coupled with OpenBox for the display manager that would be really light on resources.

---

### Post by kpatz on 2015-01-15
Virtualbox can be used to host VMs without a GUI.  The VMs can be accessed via RDP.

---

### Post by thnewguy on 2015-01-16
You do not need a GUI to run virtualized machines. KVM will run fine without a GUI (though GUI tools are available). With KVM you don't even need to run the manager software on the same machine. You can set up a headless server and run the virtual machine manager GUI from your desktop. (The client connects over OpenSSH).

As others pointed out, you don't technically need a GUI for VirtualBox either.

Virtual machines are not a machine bullet, they can be compromised, but it doesn't happen often. Still, it is important you keep the client operating systems secure (and backed up) because the guest OS can still be compromised.

---

### Post by stick.deb on 2015-01-16
Thanks for the suggestions.

---

