---
title: "How to start command prompt at booting"
date: 2018-03-06
forum: Virtualisation
---

### Post by satimis on 2018-03-06
Hi all

Ubuntu 16.04 desktop

Please advise how to start command prompt at boot.  F12 doesn't work. It starts;
```

Deteted Hard disks

ANCL controller
1) Hard dist

O(ther boot device
f) Floory
c) DD-ROM
l) LAN

b) Continue booting

```

1) and b) start normal booting

Because on  normal booting the menu bar disappears.  I need start the Terminal to fix it.

Thanks

Regards
satimis

---

### Post by again? on 2018-03-06
ctrl+alt+F1 at the login greeter.

---

### Post by satimis on 2018-03-06
> **guber2 said:**
> ctrl+alt+F1 at the login greeter.
Hi,

Thanks for your advice.

But this is a VM of Oracle VirtualBox

ctrl+alt+F1 starts the terminal of the Host which is also running Ubuntu 16.04 desktop

Regards
satimis

---

### Post by westie457 on 2018-03-06
As the VM is booting tap the 'Esc' key a couple of times. This should bring up the GRUB menu with the usual options.
From there go to Advanced hit 'Enter', got to Recovery hit 'Enter', you should now be at a screen with the usual recovery options including 'Drop to a Root Shell prompt'.

I hope this is what you meant.

---

### Post by satimis on 2018-03-06
> **westie457 said:**
> As the VM is booting tap the 'Esc' key a couple of times. This should bring up the GRUB menu with the usual options.
From there go to Advanced hit 'Enter', got to Recovery hit 'Enter', you should now be at a screen with the usual recovery options including 'Drop to a Root Shell prompt'.

I hope this is what you meant.
Hi,

Thanks for your advice.

start   GNU Grub
-> Advanced Options ......	
-> Ubuntu .... (recovery mode)
-> root  Drop in root shell prompt

Enter root passwd

But I am not allowed to edit /etc/apt/sources.list

ls -al /etc/apt/sources.list```

-rw-rw-r-- 1 root root 2890 Apr 19  2017 /etc/apt/sources.list

```

It is strange to me

Regards
satimis

---

### Post by westie457 on 2018-03-06
Have just tried a couple of things here.

When you go to the 'root shell' there is no need for SUDO or password. Warning, it is now possible to damage your system completely.

Did you see these lines of text ```
Enter for maintenance
Ctrl+D to continue
```?
Hit 'Enter' you are now in the ROOT prompt. The sentence and warning above are now in use.

In the prompt window the file system is read only at the moment we have to mount as rw so edits to files can be made.
run ```
mount -o rw,remount /
```

To edit a system file I suggest using 'nano' to edit files. ```
nano /etc/apt/sources.list
```
Make your changes then 'Ctrl+o to save then Ctrl+x to quit.
Now your back to the prompt try ```
apt update
``` this will probably fail completely because you probably won't have any networking capabilities at the moment. DO NOT PANIC.
At the prompt type 'exit' to return to the recovery menu and attempt to enable 'networking' or any other options presented.
Better option IMHO is at the prompt type 'reboot' > hit 'Enter'.

---

### Post by ajgreeny on 2018-03-06
*Thread moved to **Virtualisation**.* which is more appropriate and a better fit for this thread as it is about a guest OS in VirtualBox.

---

### Post by satimis on 2018-03-06
Hi  westie457,

Lot of thanks for your detail advice.

I have spent more than 2 hours unable to sort out what has happened to this VM.  I can edit files under /etc/ after running```

mount -o rw,remount /

```
as mentioned in your previous posting.  However on running apt update ; apt upgrade;```

....
E: Failed to fetch http://hk.archive.ubuntu.com/ubuntu/pool/main/u/unity-control-center/unity-control-counter-faces_15.04.0+16.04.20171130-0utubutu1_all.deb Temporary failure resolving 'hk.archive.ubuntu.com'

```

Tried;
```

apt update --fix-missing

```
unable to solve my problem

The complete story is as follows;
1) VM - After running update and upgrade
2) Reboot VM
3) Then install "VBoxGuestAdditions_5.2.2.iso"
4) Reboot VM  
The menu list on the left found disappeared.

Then I try to reinstall ubuntu-desktop. It comes to present situation.

I have compared the sources.list of Host and VM.  They looks similar.

Edit
===
This is NOT my first time encountering this problem after installing VBoxGuestAdditions_5.2.2.iso. (The old VBoxGuestAdditions version is NOT this version).  Previously I created a new Ubuntu 16.04 desktop VM.  After installing VBoxGuestAdditions_5.2.2.iso it came to the same situation compelling me to delete it.

Regards
satimis

---

### Post by &amp;KyT$0P# on 2018-03-06
> **satimis said:**
>  this is a VM of Oracle VirtualBox

ctrl+alt+F1 starts the terminal of the Host which is also running Ubuntu 16.04 desktop
Try Host key + F1.

---

### Post by satimis on 2018-03-06
> **halogen2 said:**
> Try Host key + F1.
Hi,

Thanks for your advice.

Hot-Key + F1 works for me here.

On Terminal (not drop to root shell)
I can run update upgrade and dist-upgrade without problem.  But the menu-bar still disappears after boot up and login

I have tried follow solutions without result

1)
sudo apt-get update
sudo apt-get install --reinstall ubuntu-desktop
sudo apt-get install unity
sudo reboot

2)
sudo mv ~/.cache/compizconfig-1 ~/.cache/compizconfig-renamed
sudo shutdown -r 0

3)
initctl restart unit-panel-service```

initctl: Name 'com.ubuntu.Upstart" does not exit

```

sudo initctl restart unit-panel-service```

initctl: unable to connect to Upstart: Failed to connect to socket /com/ubuntu/upstart: Connection refused

```

Please help.  Thanks

satimis

---

### Post by satimis on 2018-03-06
Hi all,

Through pain and difficult finally I got the menu bar back by running following commands

sudo aptitude install upstart-sysv
sudo update-initramfs -u
sudo reboot


Edit
===
I'll create a new Ubuntu 16.04 VM later.  Then install VBoxGuestAdditions_5.2.2.iso to see what will happen.  I'll come back afterwards.

satimis

---

### Post by satimis on 2018-03-06
Hi all,

Unfortunately the solution mentioned on #11 above couldn't solve similar problem encountered on Ubuntu 16.04, recently installed, menu bar found missed after booting up.

Steps performed:
After having run the commands mentioned, on reboot it drops to text mode.  I have spent 1~2 hours without a solution including;

Edit /etc/default/grub
Change GRUB_CMDLINE_LINUX=&#8221;&#8221; to GRUB_CMDLINE_LINUX=&#8221;3&#8221;
sudo update-grub

After reboot it still drop to command prompt (text mode)

Please help.  Thanks

Regards
satimis

---

