---
title: "Quickest way to run xp/vista as guest os"
date: 2008-03-02
forum: Virtualisation
---

### Post by RussellGee on 2008-03-02
Hi guys.

Im want to run my vista and xp partitions as a guest os while im in ubuntu.What im wanting to know is what you guys would recomend as the quickest.Im running hardy and gutsy but im mainly using hardy now.

I know what im doing and everything and i run virtual machines all the time in windows but instead of trying to find out which is fastest myself i though i would just ask here.:lolflag:

Specs:

Turion 2Ghz dual core
2GB RAM
Nvidia 7150 int. gfx

If it costs thats not really a problem.

Thanks

---

### Post by RussellGee on 2008-03-02
I also have visualization technology enabled from the BIOS

---

### Post by fjgaude on 2008-03-02
I have a similar setup, a Dell laptop, and I chose to install VMware server, the free one, to run WinXP. It works fine for me. See my signature.

Others like VirtualBox. It's good too.

---

### Post by RussellGee on 2008-03-02
Does it run close to native?

---

### Post by fjgaude on 2008-03-02
Once you power-up WinXP you can load all the drivers you need for the various programs, such as printers, scanners, USB flash and hard drives, etc. The quickness, speed is good, and not much slower than it would be if it were native.

With a fast box speed is not an issue. I'm a graphic designer and I wouldn't ever go back to native Windows, or ever buy an upgrade to Windows.

---

### Post by camini on 2008-03-07
Hello,

It looks like you want to run your existing (standalone) Vista & XP partitions as guest OS 'es?

I'd be really interested as well to achieve that with my vista partition..

Otherwise, for me, a new XP partition installed in the free virtualbox software runs great and does exactly what it needs.

let us know
cam

---

### Post by FrankVdb on 2008-03-08
I run XP in VirtualBox and it's runs almost as fast as native Windows. You do need enough memory and a reasonably fast processor.

When closing my XP machine, I usually don't power it down. Instead I click "Save the machine state", which kind of freezes the virtual machine, including any applications that are running.

When starting the virtual machine again, it merely needs seven seconds to open Windows with all of the applications that were running in your last session!

---

### Post by karyonix on 2008-03-09
Moving your Windows installation to differrent  machine (real -> virtual) may break your Windows Activation. 

If you want to do it, you can try. 

1. Backup you important files to somewhere else.

2. In Windows, configure your antivirus on-access scan, so that it will not start automatically at startup. 

3. In Ubuntu, unmount windows partition
  If some programs/daemons are using some files or directories in that partiton, close them first , then unmount the partition.  
  For example, let's assume Windows XP is in /dev/sda1.  
```
umount /dev/sda1
```
  You may also want to modify **/etc/fstab**, so that it will not be mounted automatically after reboot.  

4. Create raw vmdk to access windows partition.  VirtualBox OSE 1.5.6 cannot do this.  Use the proprietary edition.
Make sure you have raw access to the disk device.  
```
sudo chown *username*:disk */dev/sda*
sudo chown *username*:disk */dev/sda1*
```
Create raw vmdk, see VirtualBox manual for detailed explanation.
```
VBoxManage internalcommands createrawvmdk -filename /home/*username*/.VirtualBox/VDI/*rawwin.vmdk* -rawdisk */dev/sda* -partitions *1* -relative
```
After vmdk creation complete, you don't need raw access to whole disk anymore.  You still require raw read+write access to partition.  
```
sudo chown root:disk */dev/sda*
```

5. Create a virtual machine for your Windows. 
Windows XP requires approximately at least 256MB RAM to run fast. 
If the real machine that you install Windows on have ACPI + IO APIC, don't forget to enable them in virtual machine settings. 
Assign your vmdk from step 2 as primary master.

6. Try booting the virtual machine.  
Incompatible HAL can cause blank black screen at startup.  
If it stops at Welcome screen, try using command "Insert Ctrl-Alt-Del" in VirtualBox's menu 2 times.  When login dialog box comes, enter your username and password.  
If you can login successfully, congratulation.  
Staring windows for the first time will be slow because it discovers many new virtual hardwares.  Windows XP does not have drivers for some virtual hardware.  

7. Install guest additions and reboot virtual machine.

I don't know whether Windows Vista can survive hardware changes or not.

---

