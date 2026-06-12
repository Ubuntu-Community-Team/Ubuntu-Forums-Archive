---
title: "Qemu and vde network not working"
date: 2014-07-17
forum: Virtualisation
---

### Post by mctiew on 2014-07-17
[COLOR=#000][FONT=HelveticaNeue]I am using ubuntu 14.04 64 bit LTS with qemu 2.0.0-dfsg-2ubuntu1


[COLOR=#000000][FONT=HelveticaNeue]My qemu scripts using vde is like this :-[/FONT][/COLOR]
[COLOR=#000000][FONT=HelveticaNeue]
  #  vde_switch -sock /tmp/vde.ctl0 -tap tap0 -daemon --mgmt /tmp/myvde.mgmt0[/FONT][/COLOR]
[COLOR=#000000][FONT=HelveticaNeue]   # vde_switch -sock /tmp/vde.ctl1 -tap tap1 -daemon --mgmt /tmp/myvde.mgmt1[/FONT][/COLOR]
[COLOR=#000000][FONT=HelveticaNeue] # cat qemu.hd.vde2 
[/FONT][/COLOR]
[COLOR=#000000][FONT=HelveticaNeue]qemu-system-i386 -enable-kvm \
 -net nic,model=rtl8139,vlan=0,macaddr=00:90:00:00:00:22 \
 -net nic,model=rtl8139,vlan=1,macaddr=00:45:12:00:00:21 \
 -boot c -m 512 -hda /tmp/hd.test \
 -net vde,vlan=0,sock=/tmp/vde.ctl0 \
 -net vde,vlan=1,sock=/tmp/vde.ctl1
[/FONT][/COLOR]
[COLOR=#000000][FONT=HelveticaNeue]
[/FONT][/COLOR]
[COLOR=#000000][FONT=HelveticaNeue]All  these scripts used to be working when I am running a older system. Then  I recently change the distro to ubuntu 14.04 (64bit) with qemu 2.0.0,  then when I run the script qemu.hd.vde2, it complains these :-[/FONT][/COLOR]
[COLOR=#000000][FONT=HelveticaNeue]
[/FONT][/COLOR]
[COLOR=#000000][FONT=HelveticaNeue] Warning: vlan 0 is not connected to host network
[/FONT][/COLOR]
[COLOR=#000000][FONT=HelveticaNeue]Warning: vlan 1 is not connected to host network
[/FONT][/COLOR]
[COLOR=#000000][FONT=HelveticaNeue]
[/FONT][/COLOR]
[COLOR=#000000][FONT=HelveticaNeue]I lost the connectivity in the guest  OS ! I tried using qemu-system-x86_64, still networking is not working.
[/FONT][/COLOR]
[COLOR=#000000][FONT=HelveticaNeue]
[/FONT][/COLOR]
[COLOR=#000000][FONT=HelveticaNeue]( I also have virtualbox installed on this machine with networking using vde. The vde networking is working with virtualbox ).[/FONT][/COLOR]
[COLOR=#000000][FONT=HelveticaNeue]
[/FONT][/COLOR]
[COLOR=#000000][FONT=HelveticaNeue]Any clues ?
[/FONT][/COLOR]
[COLOR=#000000][FONT=HelveticaNeue]
I could only think it's a bug with qemu. 
[/FONT][/COLOR]
[/FONT][/COLOR]

---

### Post by mctiew on 2014-07-18
So indeed it's a bug or no more supported. 

Because I did a 'ldd qemu-system-i386', I could not find a binding to libvdeplug.

On the older system, I could find that the qemu executables ( qemu-system-i386 and qemu-system-x86 ) have a binding to libvdeplug.so.2

---

### Post by mctiew on 2014-07-18
Apparently there is already a bug report for this since a few years back and as it seems there is no plan to fix this.

Looks like compiling qemu my ownself is the way to go, if I really need it.

---

### Post by mctiew on 2014-07-19
> **mctiew said:**
> Apparently there is already a bug report for this since a few years back and as it seems there is no plan to fix this.

Looks like compiling qemu my ownself is the way to go, if I really need it.

OK I compiled it myself and vde is now working.

I spent much less time doing the compilation than earlier trying to figure out what's wrong. LOL.):P

---

