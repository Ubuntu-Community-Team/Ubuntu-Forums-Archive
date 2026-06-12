---
title: "Ubuntu 14.04 Desktop will not shutdown in Hyper-V 2012 R2 VM"
date: 2014-07-13
forum: Virtualisation
---

### Post by applegate2 on 2014-07-13
Hi,

I have installed Ubuntu 14.04 with all updates, but it will not shutdown without having to manually poweroff the ubuntu VM in Hyper-V Manager.  It will show the Ubuntu moving dot screen endlessly and never shutdown....

Why? Is a fix available?

[I]_Additional information:_
VM client: Ubuntu 14.04 desktop with generation 2 vhdx uefi boot (none secure), minimum of 2048 MB dynamic ram, 127 GB dynamic virtual harddrive .
Host: I7 3770s - 32 GB memory - 2 x 224 GB SSD samsung EVO (no raid) - 2 x 2 TB Disk (no raid).
Host OS: Hyper-V 2012 R2 (bare bone) with all microsoft updates.[/I]

---

### Post by applegate2 on 2014-07-13
I found this: [http://ubuntuforums.org/showthread.php?t=2229882&page=2](http://ubuntuforums.org/showthread.php?t=2229882&page=2) and solved the issue. 

Re: virt-manager cannot power off virtual machines		 [INDENT]					I found a corresponding bug here (did not find the time to test).

 The problem seems to be related to the  **apparmor profile**!

[[COLOR=#dd4814]https://bugs.launchpad.net/ubuntu/+s...t/+bug/1324393[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/libvirt/+bug/1324393")

 After 

       service apparmor teardown

 I can shutdown the machine :guitar:
 So this is definitely a problem of a

 I did:

  apt-get install --reinstall apparmor

 And everything works now.				 [/INDENT]

			 [INDENT]									Last edited by apos; 2 Days Ago at [COLOR=#3e3e3e]10:26 PM[/COLOR].													 **Reason:** Solution [/INDENT]

---

### Post by applegate2 on 2014-07-13
Oke!

Shutdown is working but rebooting not!!!

Something still wrong.

---

### Post by Calvin_Kong on 2014-10-15
Hi, did you get a solution to the reboot issue? I am having the same issue. Ubuntu stuck at the shutdown splash "Ubuntu ......" screen, and would not proceed.

---

### Post by parisv on 2015-02-02
I'm having the same issue and reinstalling apparmor doesn't help.

[ATTACH=CONFIG]259656[/ATTACH]

---

### Post by TheFu on 2015-02-02
Don't know if this is related, but do your VMs have the ACPId (acpid) package installed?

Is is the "Advanced Configuration and Power Interface event daemon" according to the manpage.

---

### Post by parisv on 2015-02-02
yes it is installed. Should it be?

I followed this thread but that didn't work also.

[http://askubuntu.com/questions/125844/shutdown-does-not-power-off-computer](http://askubuntu.com/questions/125844/shutdown-does-not-power-off-computer)

---

### Post by TheFu on 2015-02-02
I need it so that libvirt can stop/destroy VMs, though I haven't needed that in years. KVM is extremely stable and fast.
Never touched hyper-v, sorry.

---

### Post by ivan84 on 2015-04-30
I was having the same issue. What solved this was turning off dynamic memory for the VM.

Actually, I just re-enabled that setting, but you'll need to update the grub.

Edit the /etc/default/grub file

Change [B]GRUB_CMDLINE_LINUX_DEFAULT=""

[/B]To **GRUB_CMDLINE_LINUX_DEFAULT="nohz=true** (or just add nohz=true in addition to whatever is currently in there)

Update grub (sudo update-grub)

and it should work now with dymanic memory (both shutdowns and reboots).

---

### Post by ivan84 on 2015-04-30
Also, I noticed, by default the VM drivers aren't running. I followed these steps (also note that I'm not sure if these modules would render the previous grub 'fix' obsolete).

[http://baudlabs.com/how-to-install-hyper-v-integration-services-in-ubuntu-12-04-lts/](http://baudlabs.com/how-to-install-hyper-v-integration-services-in-ubuntu-12-04-lts/)

EDIT: yes, it was the integration piece that was apparently missing on my setup (it's built-in to ubuntu, but not activated by default). After I enabled the modules, I undid the grub setting, and dynamic memory works fine with the VM now.

---

