---
title: "[Boot-Repair] Endless errors after trying to establish internet connection"
date: 2023-03-10
forum: Windows
---

### Post by zebazga on 2023-03-10
Hi, I have Windows 10 and after updating my NVidia drivers, my PC did nothing but boot to BIOS. Nothing would get past that; in fact, trying various fixes led to nothingness. I removed the graphic card and using the motherboard graphics, was able to access the Boot-Repair USB I burned with Rufus. A website for troubleshooting Windows problems recommended Boot Repair after all else failed, such as the Windows Repair options.

A GUI came up and a message appeared saying to connect to the internet and then click the button on the message. I clicked several icons trying to find the one to enter the wifi info including an icon on the bottom left that I think tried to open a webpage, failed, and had a reload option. I finally found intern info and entered info, but password was wrong. I tried to reload page and it still wouldn't connect (go figure, right). I then entered the correct password. To verify it was correct, I went to reload that webpage again--not clicking the button to close the popup telling me to connect to internet.

I don't know exactly what happened in the next few seconds, I clicked nothing else, but I ended up in what seems to be a full-screen shell with continual error messages. I'm afraid of making something worse, so haven't done anything and it's been running nonstop for more than 2 days now. I took a video so I could pause and see the messages, which seems to be;

[93069.916469 pcieport 0000:00:1c.6: AER: PCIe Bus Error: Severity=Corrected, type=Physical Layer, (Receiver ID) device [806:a116] error status/mask=00000001/00002000 [ 0] RxErr

All the errors seem to be exactly the same except for the incrementing number at the start.

Can anyone tell me what is going on and what I need to do now?

Thank you for your time and consideration.

---

### Post by MAFoElffen on 2023-03-10
Am I confused? I did not hear once where you said anything about Ubuntu or even Linux... Waiting for more info.

Tell me if there is something different there: The way you explained it, you have Windows 10, and updated your NVidia drivers in Windows 10.... On reboot, you system would not start Windows, but rather would only go to the BIOS boot(?)

You then downloaded the Boot-Repair disk, where on booting it, then you had problems connecting to wifi(?). 

Am I right so far? If so, and there were problems, reboot and try again. No harm in that...

---

### Post by zebazga on 2023-03-10
The website that started me on this latest quest indicated that Boot-Repair could fix boot issues on a Windows system.

Yes to all of the above except that I don't know if the problem was connecting to wifi or something else. 

What you're saying is that I won't make anything worse by rebooting while it's in the middle of listing the error(s) repeatedly?

If you verify I won't damage by rebooting, I will promptly do so!

Thanks for taking the time to reply.

---

### Post by lucant on 2023-03-10
It's been a while since I've used Windows...
And the windows forum didn't help me at all with my intel Bay Trail bug...
But I think you should look for the Microsoft forum.
And restarting your machine won't make anything worse, it might even make it better.

---

### Post by zebazga on 2023-03-10
It struck me as odd to post in an ubuntu-specific forum, but that's where it seems yannubuntu has documented Disk-Repair.

Y'all were right that interrupting in the middle of the errors didn't do anything bad to Disk Repair. Its GUI came up, I connected to wifi, it updated, and suggested repartioning. Instead of making any changes I just created a pastebin of what it found.

I'm not familiar with these, but it kinda looks like it's saying not only do I not have any OS I also don't have my 1tb harddrive. Is that right? If so, I guess I just start crying?

[https://pastebin.ubuntu.com/p/mcsZv9Nh9h/](https://pastebin.ubuntu.com/p/mcsZv9Nh9h/)

---

### Post by oldfred on 2023-03-10
Moved to Windows sub-forum since no Ubuntu.

What site recommended Boot-Repair for fixing Windows issues?
Boot-Repair cannot fix Windows issues. Its primary fix is either an update to grub to total reinstall of grub to boot Linux.
The report can be useful, but often users have left Windows fast start up and/or hiberntion on or need chkdsk. Then the Linux NTFS driver will not mount any NTFS partitions to prevent damage to a hibernated system or one that needs Windows repairs.

Best to use your Windows repair/recovery disk.

For Windows 10, but similar for other versions.
[https://www.tenforums.com/software-apps/27180-windows-10-recovery-tools-bootable-rescue-disk.html](https://www.tenforums.com/software-apps/27180-windows-10-recovery-tools-bootable-rescue-disk.html)
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)

---

### Post by zebazga on 2023-03-11
> **oldfred said:**
> Moved to Windows sub-forum since no Ubuntu.

What site recommended Boot-Repair for fixing Windows issues?


The site is http;//makeuseof.com/tag/windows-10-wont-boot and the specific step is step 11. 

I did try booting from a Windows 10 USB and going through the troubleshooting/repair options. However, as I mentioned above, none of it worked. All the various commands I found about things to check partitions from command prompt, etc, none of it provided information, much less help.

The boot repair page on sourceforge says that the boot info tool can get info on whatever system is installed on your disk running boot info from a Debian derivative. I assumed that Boot-Repair could work with Windows 32 or 64 bit OSes as well as others but the tool was booting/loading from an Ubuntu USB, hence me asking for help on Boot Repair in the ubuntu forum where the boot-repair developer has posted about it.

Thanks again for everyone's time.

---

### Post by yancek on 2023-03-11
As indicated by oldfred in post 6, boot repair does not repair windows boot problems.  What it can do if you have Grub installed on a Linux system is to simply add a windows menuentry to the grub.cfg file.  If the windows boot files are corrupted or there is some other problem with them, boot repair won't help.  The site that said boot repair could fix windows boot issues was an exaggeration, to say the least as all it does is add a menuentry for window which, in some cases at least, can 'repair' the windows boot.  You don't hae Grub so that won't help.

In your initial post, you refer to entering a password.  What needed a password as boot repair doesn't use any?

Given the above, I would also suggest posting at a windows forum posting the information/error/warning messages you got when using the windows repair disk.
Since the problem occurred after installing new drivers for your Nvidia card, you might try going to the NVidia site or forums.

---

### Post by MAFoElffen on 2023-03-11
I would try a Windows Disk > Repair > Troubleshoot > Startup Repair... But first go into the UEFI BIOS and see if it even see's your hard disk... Because, whether it had Windows with no other (Linux) OS on it, the Boot-Repair Disk didn't see any internal hard disks on the system at all. That is not good. That could be a few things, like the SATA Mode masking it from Linux, but I would still investigate that.

---

