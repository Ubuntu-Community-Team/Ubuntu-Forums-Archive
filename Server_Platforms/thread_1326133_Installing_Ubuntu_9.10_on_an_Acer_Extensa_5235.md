---
title: "Installing Ubuntu 9.10 on an Acer Extensa 5235"
date: 2009-11-14
forum: Server Platforms
---

### Post by Slotkenov on 2009-11-14
Hello there,

Im new here and new to Linux. Im a professional web developer and therefore thought it would be usefull to learn some Linux and administer my own Linux server. Heard a lot about Ubuntu and it sounds good, so Ubuntu seems a good choise.

I specifically bought myself an Acer Extensa 5235 for the purpose of playing with a Linux server. I downloaded Ubuntu 9.10 64bit, burned it to a CD and started the installation on my laptop.

The first problem came when Ubuntu told me he couldn't find any network interfaces. I have the laptop plugged in on the wired network and I tried the connection before installation on the pre installed Windows on the laptop. And my connection was fine in Windows. Ubuntu gave me this message:

```
Configure the network

No network interfaces detected

No network interfaces were found. The installation system was unable to find a network device.

You may need to load a specific module for your network card, if you have one. For this, go back to the network hardware detection step.
```

To bad I tought, but lets just continue with the installation. Everytime he asked for some settings, I just left it to the default.

Then he came at the point where he asked me if I wanted to install additional software.

```
Software selection

At the moment, only the core of the system is installed. To tune the system to your needs, you can choose to install one or more of the following predefined collections of software.
```

I choose the following software:

[LIST]
[*]LAMP server
[*]Mail server
[*]OpenSSH server
[*]Samba file server
[/LIST]

He went on, installing that software, asking for some settings once in a while. Then he came back to me with the following error:

```
Select and install software

Installation step failed

An installation step failed. You can try to run the failing item again from the menu or skip it and choose something else. The failing step is: Select and install software
```

That's not looking good. So I retried the whole installation of Linux (again the warning that no network interfaces could be found), but then without selecting any additional software, just to see if that would work. And it did work. Ubuntu finished the installation.

So now Linux could boot, and it did. Some text was going by and then the screen went black. And it stayed black. And I could hit the keyboard however I want, but the screen stayed black.

So thats actually three problems in a row:

[LIST=1]
[*]No network interface found
[*]Install software fails
[*]Black screen after launching Ubuntu
[/LIST]

By the way, I have DHCP on my network

I hope someone can help me with these problems. Am I doing something wrong or have I just bought the wrong laptop (or both :p)?

Thanks in advance for any help!

---

### Post by Slotkenov on 2009-11-14
I tried with installing only
LAMP server
OpenSSH server

So the error about installing software lies with one of these:
Mail server
Samba file server

---

### Post by TwiceOver on 2009-11-14
I ran into this once before.  When you get to the Software selection screen do not select anything.  After the install is complete you can get back to this software selection by using the command:

sudo tasksel

This will bring up the software selection and installation screen.

You will need to work out your networking issues first though.  Do you plan on sticking with Windows as your primary OS?  If so, you may want to think of running Ubuntu Server as a Virtual Machine with VirtualBox on Windows.

---

### Post by Slotkenov on 2009-11-14
Ah thanks, I'll try that.

No Windows was just pre installed, but I formatted the whole hard disk for Ubuntu. It will be a dedicated Ubuntu server.

The weirdest part is that I get that black screen after launching Ubuntu (after I correctly installed it). Just the black screen and I can't seem to do anything. So I cant even try that command you gave me, or, somehow, try to fix the network. I just can't do anything.

I hope someone knows what I'm talking about? :)

Thanks again!

---

### Post by MartinGM on 2009-11-16
hello Slotkenov!

i am working with 910 on an extensa 5235 as well and have the same blank screen ... as long as i dont add a i915.modeset=0. 

i can only assume it is about KMS and that the screenwidth of 1366 isnt working out of the box. so, as long as there isnt a bugfix, this workaround is really great to live with. i am working with my machine since 3 weeks rock solid incl. all compiz hardware accelaration and desktop effects. if you want to give it a try, make a test ride with the live cd in the following way ...

- startup from the live cd!
- choose your language in the language menu
- press F6 for the bootparameters menu
- press esc to get back to the main menu
- type in the modeset: 'i915.modeset=0'
- press enter to start the live cd test drive

the i915 command can be also used in the grub menu, on startup hold down the shift key, you will get the list of installed kernels, just type 'e' to get into edit mode and insert the i915.modeset=0 right behind the splash quiet commands, after this just press ctrl + x to boot the machine with this setup.

the screen should work now, so it did for me! later on you can make this setup fix in the grub.cfg file, but for now, you just try this setup if it works fine for you. hope this helps!

---

### Post by Slotkenov on 2009-11-17
> **MartinGM said:**
> 
the i915 command can be also used in the grub menu, on startup hold down the shift key, you will get the list of installed kernels, just type 'e' to get into edit mode and insert the i915.modeset=0 right behind the splash quiet commands, after this just press ctrl + x to boot the machine with this setup.

the screen should work now, so it did for me! later on you can make this setup fix in the grub.cfg file, but for now, you just try this setup if it works fine for you. hope this helps!

Thats great, it works! Many thanks.

Now on to the next step. The most logical step would ofcourse be changing that grub.cfg file you mentioned. So I won't have to type it every time I boot.

Found the file and took a look at it. But it doesn't look like the code I saw in the edit screen when booting. You have any idea how to edit this file so it would work permanently?

ps First thing I saw in the file was: DO NOT EDIT THIS FILE :p

---

### Post by MartinGM on 2009-11-18
wonderful!

now that you know it works, you can add the command to your grub.cfg file!

mine looks like this:

```
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set f5e03e0b-c66a-4fa5-8bd9-0b8d5712f3cd
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set f5e03e0b-c66a-4fa5-8bd9-0b8d5712f3cd
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=f5e03e0b-c66a-4fa5-8bd9-0b8d5712f3cd ro   quiet splash[COLOR=Red] i915.modeset=0[/COLOR]
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set f5e03e0b-c66a-4fa5-8bd9-0b8d5712f3cd
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=f5e03e0b-c66a-4fa5-8bd9-0b8d5712f3cd ro single [COLOR=Red]i915.modeset=0[/COLOR]
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
```as you can see, you have to change the following line ...

 linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=f5e03e0b-c66a-4fa5-8bd9-0b8d5712f3cd ro   quiet splash

to this ...

 linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=f5e03e0b-c66a-4fa5-8bd9-0b8d5712f3cd ro   quiet splash[COLOR=Red] i915.modeset=0[/COLOR]

just add the i915.modeset=0 command at the end of the line and :) dont use my UUID's LOL

before you can save the file, you have to edit via root the permissions! or just start nautilus with sudo throughout the terminal (sudo nautilus) and edit the permissions (right click, properties, rights) to allow the grub.cfg to be saved!

my machine runs rock solid and with all compiz effects, the new intel driver are  really a plus in 9.10! i'm sure you will enjoy it, have fun :)

addendum:  there is only one handicap, with each update to grub coming via update manager (might happen some times, not that often) the grub.cfg gets reconfigured and you have to add the command again!

---

### Post by Slotkenov on 2009-11-18
Nice, I'll try



Awsome, works like a charm.

Now, did you also have the problem that on install Ubuntu couldn't find any network interfaces? And if so, how did you fix it?

I saw something on the internet, the file etc/network/interfaces containing the text:

auto lo
iface lo inet loopback

Changed it to:

auto lo
iface lo inet dhcp

Don't know if that helps. But now i'm wondering how I can check if my network works :P



Again, many thanks for the help so far!

---

### Post by Slotkenov on 2009-11-18
ping ofcourse :p

I did: ping 192.168.0.1

and I got: connect: Network is unreachable

---

### Post by ambucks on 2009-12-19
Hello, I am having thr same problem (Black screen on live CD when trying to install Ubuntu 9,10 on Acer Aspire 5738.  I tried following the instructions below, but there it seems to me that there is a step missing (I don't know very much about Linux).  I wonder if anyone can help me out and was wondering the same thing.

Step #3 below says to press F6 for the bootparameters menu.  I'm wondering which boot parameter should be selected for this to work?

Thanks so much



> **MartinGM said:**
> hello Slotkenov!

i am working with 910 on an extensa 5235 as well and have the same blank screen ... as long as i dont add a i915.modeset=0. 

i can only assume it is about KMS and that the screenwidth of 1366 isnt working out of the box. so, as long as there isnt a bugfix, this workaround is really great to live with. i am working with my machine since 3 weeks rock solid incl. all compiz hardware accelaration and desktop effects. if you want to give it a try, make a test ride with the live cd in the following way ...

- startup from the live cd!
- choose your language in the language menu
- press F6 for the bootparameters menu
- press esc to get back to the main menu
- type in the modeset: 'i915.modeset=0'
- press enter to start the live cd test drive

the i915 command can be also used in the grub menu, on startup hold down the shift key, you will get the list of installed kernels, just type 'e' to get into edit mode and insert the i915.modeset=0 right behind the splash quiet commands, after this just press ctrl + x to boot the machine with this setup.

the screen should work now, so it did for me! later on you can make this setup fix in the grub.cfg file, but for now, you just try this setup if it works fine for you. hope this helps!

---

### Post by Slotkenov on 2009-12-20
What I did was this:

> **MartinGM said:**
> hello Slotkenov!
the i915 command can be also used in the grub menu, on startup hold down the shift key, you will get the list of installed kernels, just type 'e' to get into edit mode and insert the i915.modeset=0 right behind the splash quiet commands, after this just press ctrl + x to boot the machine with this setup.

That worked for me, you tried that?

---

### Post by hislordship on 2010-02-18
Hi Slotkenov, thanks a million for that great idea! I am totally new to Linux as well and don't know much about computers, so I need to ask a dumb question here: how did you find the grub.cfg file in order to permanently change it?
Thanks...

---

### Post by Slotkenov on 2010-02-19
Good question, I don't remember. But I will look it up...


/boot/grub/grub.cfg


Btw. I got my network fixed also, eventually.

---

### Post by hislordship on 2010-02-21
thanks slotkenov:-) here is what worked for me:

1. open terminal, type sudo nano /etc/default/grub
2. replace quiet splash by nomodeset or i915.modeset=0
3. ctr+x; y enter
4. sudo update-grub


now I'm dealing with the next problem that laptop seems to have, about the ar928x chipset (wlan connection unstable), i have reopened another thread hence again I'm not linux experienced enough to follow the fixes suggested...

thanks again,
bye

---

