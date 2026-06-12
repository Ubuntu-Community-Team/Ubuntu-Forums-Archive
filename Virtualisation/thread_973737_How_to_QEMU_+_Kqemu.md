---
title: "How to QEMU + Kqemu"
date: 2008-11-07
forum: Virtualisation
---

### Post by bodhi.zazen on 2008-11-07
[size=6][FONT=Times New Roman]**[center]How to QEMU + KQEMU[/center]**[/size]

[center][img]http://bellard.org/qemu/qemu-logo.png[/img][/center]

Home page: [http://bellard.org/qemu/](http://bellard.org/qemu/)

This will be brief :)

Pros :
[list][*]Open source.
[*]qemu allows emulation of multiple processors.
[*]Supports 64 bit guests (on 64 bit hosts).
[*]Portability. qemu will run on Windows as well.[/list]

Cons: The biggest disadvantage is qemu is slow, even with kqemu.

For a more complete how-to on qemu see:

[list][*][https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo](https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo)
[indent]_Note_: You do NOT need to compile kqemu (see below).[/indent]
[*][http://ubuntu-tutorials.com/2007/07/04/setting-up-qemu-kqemu-on-ubuntu-704-feisty/](http://ubuntu-tutorials.com/2007/07/04/setting-up-qemu-kqemu-on-ubuntu-704-feisty/)[/list]

[size=2]Installation[/size]

Installation is quite easy.

```
sudo apt-get install qemu
```

Qemu itself is slow so you may wish to add kqemu AKA "QEMU Accelerator".

For kemu :

_Note_: "kqemu" is an ambigious name.

[list=number][*][kqemu the qemu accelerator](http://bellard.org/qemu/kqemu-doc.html). This is a kernel module that makes qemu faster.
[*][kqemu the KDE application](http://www.kde-apps.org/content/show.php?content=19407) is a graphical interface/launcher for qemu.[/list]

```
sudo apt-get install kqemu-common kqemu-source
```

Add your user to the kqemu group 
Log off and back on

Using any editor, edit /etc/modules (gksu gedit /etc/modules)
Add kqemu to the bottom of the list.

This will load kqemu at boot.
To load without re-booting

```
sudo modporbe kqemu
```

Running qemu (from the command line, using "/media/data/ubuntu-desktop.iso" as an example, you will need to provide a path to an iso image or virtual hard drive):

**For [color=blue]32 bit[/color] hosts**:

```
qemu -cdrom /media/data/ubuntu-desktop.iso -m 512
```

**For [color=green]64 bit[/color] hosts**

```
qemu-system-x86_64 -cdrom /media/data/ubuntu-desktop.iso -m 512
```

**[color=blue]To confirm you are using kqemu[/color]**:

Enter the guest with your mouse (click in the box). Hit ctrl-alt-2
At the qemu command console enter "info-kqemu"
you should see:
> (qemu) info kqemu
kqemu support: enabled for user code

enter ctrl-alt-1 to return to the main console. 

[list][*]From the command line. See man qemu.
[*]See also [How to KVM](http://ubuntuforums.org/showthread.php?t=966739)[/list]

[size=2]GUI Options[/size]
[list][*]qemu-launcher.
[*]qemulator.
[*]qtemu.
[*][kqemu](http://www.kde-apps.org/content/show.php?content=19407) (bad name, this is the KDE graphical front end).[/list]

bodhi.zazen[/font]

---

### Post by TitaniumXJ on 2008-11-08
Hello, Im kinda new to this, so I apologize in advance. I followed the following guide to run windows on my linux box. 
[https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo](https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo)

Once I get to step 11 I run into problems.
Install Windows XP. Put the CD in the drive and run:

  qemu -localtime -cdrom /dev/cdrom -m 384 -boot d windows.img
I get this 

[IMG]http://i2.photobucket.com/albums/y42/evilcheshirecat/Screenshot-QEMU.png[/IMG]

I then googled around and found the following:
[http://ubuntuforums.org/showthread.php?t=407729](http://ubuntuforums.org/showthread.php?t=407729)

Im stopped at the first step I get the following:

titan@titan-desktop:~$ /media/cdrom$ mount
bash: /media/cdrom$: No such file or directory
titan@titan-desktop:~$ 

Im at a loss and look to you, the Ubuntu gods for my answers.

---

### Post by bodhi.zazen on 2008-11-08
It is working on my system with a kubuntu cd. Is you Windows CD in working order ?

---

### Post by pontifikas on 2009-01-11
I have trouble getting qemu running with kqemu.
i followed your instructions, loaded the modules(kqemu) but when I run qemu, info kqemu returns "disabled".

I noticed that there is no point in this howto describing how kqemu is connected to qemu. Does qemu use it automaticaly?

I run 8.10.

I red in the homepage of qemu that qemu must be compiled with kqemu support:[http://bellard.org/qemu/kqemu-doc.html]("http://bellard.org/qemu/kqemu-doc.html")
Is in ubuntu?

I thank you

---

### Post by bodhi.zazen on 2009-01-11
kqemu is a kernel module to accelerate qemu. In my experience it does not make qemu all *that* much faster and qemu + kqemu is slower then kvm, VirtualBox, or VMWare.

Can you provide a little more detail ? Did you add your user to the kqemu group ? log out and back in ? If you re-booted, did you re-load teh kqemu module ? Are you running a 64 bit host / guest ?

---

### Post by pontifikas on 2009-01-12
I'm running Intrepid guest on Intrepid host
I'm running at 32 bit using  linux-source-2.6.27 I added and compiled myself.
I added the user at the kqemu group by modifying /etc/group.
I also added the kqemu module at the /etc/modules(lsmod reveals it) and I have rebooted.
The /dev/kqemu seems correctly installed(this is done automatically in intrepid doesn't it?).
I used both QTemu and Qemulator. 
I even added -kernel-kqemu parameter in Qtemu or at the command produced by Qemulator and I still dont get kqemu to be used.

---

### Post by Brazen on 2009-03-03
These instructions seem to be lacking quite a few steps.  Here is how to get kqemu installed and working:

sudo aptitude install -R module-assistant kqemu-common kqemu-source qemu linux-headers-server bridge-utils
sudo module-assistant prepare

sudo module-assistant auto-install kqemu



create /etc/udev/rules.d/60-kqemu.rules and put this in it:

KERNEL=="kqemu", NAME="%k", GROUP="kqemu", MODE="0660"



Create the kqemu group and add my user to it:

sudo addgroup --system kqemu

sudo adduser $USER kqemu



add 'kqemu' to /etc/modules



reboot, or "sudo /etc/init.d/udev reload" "sudo depmod -a" and "sudo modprobe kqemu"


kqemu will now be working.  If you want to manage it with libvirt, also do this:

sudo aptitude install -R libvirt-bin virt-manager virt-viewer xauth

virt-manager and virt-viewer are gui apps that I sometimes use over an ssh X11 tunnel since I don't install X on my server.  You could leave them out and use any old vnc viewer though.  I'll often use a vnc viewer and connect by port forwarding through ssh to the vnc display port for the virtual machine on the server.

---

