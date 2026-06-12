---
title: "Virtualbox autostart VMs and save state upon host reboot"
date: 2013-03-30
forum: Virtualisation
---

### Post by jermanbdogg on 2013-03-30
Hello all,

First off I should state that I am new to scripting and some of the more advanced command line options in Ubuntu. (not afraid to learn tho). I am currently running Ubuntu Server 12.04 and Virtualbox 4.2. I have successfully got my first VM up and running and have viewed the manuals (and countless threads on the subject) using the built in autostart configurations. My problem is that reboots are not successfully starting my VMs. I reboot the server and when i run the VBoxManage list runningvms command it is not showing as running. Below are my configuration files. Could someone please tell me what I am doing wrong?

Notes
-Initial install was for the user "jerry". Installed Virtualbox as "vbox" and added vbox to the sudo group
-I used the VBoxManage setproperties to change the working directory to another mounted hard drive. I set the sticky bits for the path all the way through the VMs folder with 775 properties of vbox:vbox
-The "PHPVbox" virtual machine was created by the vbox user.
-I created and registered the vm through the command line, then used PHPVirtualbox to set the rest of the settings, start and install the Ubuntu Server OS in the VM.


/etc/default/virtualbox (permissions: -rwxr-xr-t 1 vbox vbox   91 Mar 27 04:42 virtualbox)
```
VBOXWEB_USER=vbox
VBOXAUTOSTART_DB=/etc/vbox/
VBOXAUTOSTART_CONFIG=/etc/vbox/autostart.cfg
```

Contents of: /etc/vbox/ (permissions the same for the vbox folder including the sticky bit)
-rwxrwxr-t 1 vbox vbox 69 Mar 27 05:01 autostart.cfg
-rwxrwxr-t 1 vbox vbox  1 Mar 27 04:48 vbox.start

autostart.cfg contents:
```
default_policy = allow

vbox = {
        allow = true
        startup_delay = 10
}
```

vbox.start has just "1" listed in the file which was enabled with the "VBoxManage modifyvm "PHPVbox" -autostart-enabled on" command.

I am only getting the following messages with the dmesg upon the reboot:
```
[   12.810463] vboxdrv: Found 6 processor cores.
[   12.810641] vboxdrv: fAsync=0 offMin=0x3bf offMax=0x1c6f
[   12.810725] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   12.810726] vboxdrv: Successfully loaded version 4.2.10 (interface 0x001a0004).
[   13.016290] vboxpci: IOMMU not found (not registered)
```

When I run the command: "sudo service vboxautostart-service start" the virtual machine starts

Any help here will be appriciated. Let me know if you need anything further. Not entirely sure if there is another log file I should be checking as well.

---

### Post by ttoilleb on 2013-03-30
I was looking into doing this myself.  But ran across this post - [https://forums.virtualbox.org/viewtopic.php?f=11&t=51529](https://forums.virtualbox.org/viewtopic.php?f=11&t=51529) which convinced me to put it aside for a while.  Not sure if this addresses your problem, but it seems to.

The next to last post (by aeichner**** » 16. Oct 2012, 11:56) says the API is not functional as of vbox 4.2.0 and not sure when it will be functional.

hth

---

### Post by ThePhantom0114 on 2013-03-31
I can't help with your specific issue, but I can recommend using this: [http://vboxtool.sourceforge.net/](http://vboxtool.sourceforge.net/) Instead of the built in tools for autostarting. This is very easy to set up, and allows any VM you want to autostart and save state at a reboot. The instructions on the site are very easy to follow.

---

### Post by jermanbdogg on 2013-04-01
So I decided to give up on it for now. I have vboxtool installed and working like a charm. I just hope that the issues are fixed in future versions of Virtualbox. While I enjoy third party scripts and workarounds as much as the next person, it is bad to think that I actually spent a week under the assumption that I was doing something wrong with vbox itself.

--ThePhantom0114 and ttoilleb: Thank you for my escape route. :D

---

### Post by WRwGY8c on 2013-08-15
Hi there, 

I do not know about saving the state of a vm upon shutdown. However, i do know a way to startup at boot. It is probably not the most elegant way but it works.

I'm using Linux Mint 15, which is a Ubuntu based distro. In Linux Mint is a program (or function) that manages the programs to run on startup/boot. I know Ubuntu has a similar or the same program/function. 

You need to go to this program/function and add a command/program.

Normally you would fill out something like this:

/usr/bin/program-you-need-to-startup

Now, you can use the VBoxManage program of virtualbox like this:

VBoxManage startvm <name-of-the-vm-here> type --headless 

You can set a different type but in my case it would be a server so I wanted it to run headless because I can access it thru SSH.

Kind regards,

DC80

---

