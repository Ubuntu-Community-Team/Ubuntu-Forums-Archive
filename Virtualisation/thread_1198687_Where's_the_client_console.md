---
title: "Where's the client console?"
date: 2009-06-27
forum: Virtualisation
---

### Post by walter554 on 2009-06-27
I've installed my first ever KVM on a new 9.04 server. I tried to create my first VM using virt-install and 
```
sudo virsh -c qemu:///system list
```
shows the VM is 'running', but I can't find it's text console. I've got linux servers and windows clients (2000, XP) - so no X GUI.
 
The docs imply a cli interface for KVM (and the need for a physical screen and keyboard) and I've found several unanswered posts with this same question so it is either real simple or real hard. All help appreciated.
 
I created my VM with this cmd
```
 
sudo virt-install -n test1 -r 128 -f test1.img -s 0.5 -c /dev/cdrom --accelerate --connect=qemu:///system --nographics --noautoconsole -v
 

```
 
Thks, 
Walt

---

### Post by juancarlospaco on 2009-06-28
SSH to the VM.
*Look at the Ubuntu VM-Builder its nice to deploy anything.*

If you have other PC with X, and want easy managment, install Convirt 1.1

---

### Post by walter554 on 2009-07-04
juancarlospaco,
Thanks for the help. I couldn't ssh until the VM was sucessfully started, and I needed a console to try and debug the setup. However, your vmbuilder tip was the vital clue as I managed to build a succesful VM 'blind' using vmbuilder instead of virt-install. I'll also leave a post called [[COLOR=#000000]How To use CLI to install KVM virtualisation on Ubuntu Server 9.04[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1204202") [FONT=Arial] [/FONT]
[FONT=Arial]in case anyone else is trying to do this.[/FONT]
[FONT=Arial]- walter[/FONT]

---

