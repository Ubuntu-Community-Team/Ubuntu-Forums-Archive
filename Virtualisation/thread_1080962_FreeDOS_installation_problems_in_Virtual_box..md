---
title: "FreeDOS installation problems in Virtual box."
date: 2009-02-26
forum: Virtualisation
---

### Post by jwbrase on 2009-02-26
I'm running VirtualBox under Ubuntu 8.10, and I've been having all kinds of trouble getting FreeDOS to work. I can boot from the ISO image, but I can't get the installer on the ISO image to install the OS to the disk image I set up for the VM in VirtualBox. All I get is "Failure Reading Partition Table".

---

### Post by HotShotDJ on 2009-02-26
> **jwbrase said:**
> I'm running VirtualBox under Ubuntu 8.10, and I've been having all kinds of trouble getting FreeDOS to work. I can boot from the ISO image, but I can't get the installer on the ISO image to install the OS to the disk image I set up for the VM in VirtualBox. All I get is "Failure Reading Partition Table".Why not try the premade VirtualBox image?  Get it here: [http://virtualbox.wordpress.com/images/freedos/](http://virtualbox.wordpress.com/images/freedos/) -- you may need to install p7zip-full to open this archive

(I just tested the VDI in the freedos-1.0-x86.7z archive that you get at the above link.  Worked fine.  Just copy the VDI from the archive to your ~/.VirtualBox/VDI directory.  Then open VirtualBox and click on "New" and then "Next."  Fill in the Name text box (I used "FreeDOS") and then select "Other" for Operating System and "DOS" for Version.  Click "Next." Choose the amount of RAM (I chose 128 MB) and click "Next."  Make sure "Boot Hard Disk" is checked off, and then select "Existing" and then "Add" then select your FreeDOS.vdi. And click "Open."  Highlight FreeDOS.vdi in the next window and then click "select" -- now you can click on "Next" in the Virtual hard Disk dialog.  Verify the settings and then click "Finish.")

---

### Post by mikeym88 on 2009-03-11
> **jwbrase said:**
> I'm running VirtualBox under Ubuntu 8.10, and I've been having all kinds of trouble getting FreeDOS to work. I can boot from the ISO image, but I can't get the installer on the ISO image to install the OS to the disk image I set up for the VM in VirtualBox. All I get is "Failure Reading Partition Table".

I get the same problem in the windows version of VirtualBox. Are you using a virtual machine with 512 MB of hdd space and 32 MB of ram?

---

### Post by cleanzero on 2009-03-12
> **mikeym88 said:**
> I get the same problem in the windows version of VirtualBox. Are you using a virtual machine with 512 MB of hdd space and 32 MB of ram?


I'm on a mac, but I'm having exactly the same problem "Failure Reading Partition Table" while trying to install freedos using virtualbox. 
I downloaded the suggested pre-built freedos vm and it works, but I'd rather prefer to built it on my system.
Also, on off-topic, someone can help me on figure out, how to put files on dos machine ? Can I copy from the mac to dos ? Or some other way ? Thanks.

---

### Post by Vorl the Magnificent on 2009-03-27
I believe I've figured these out.

(A) _Answer to the first question, roughly paraphrased as follows:  "What's going on with the 'Failure Reading Partition Table' error, and how do I fix it?"_

When you try to **format** your drive during the course of the install, FreeDOS doesn't recognize a valid/manipulable partition on your disk (i.e., the virtual disk you created for your FreeDOS installation).  This is because you haven't done the lower-level task of CREATING a FreeDOS-recognizable partition using **fdisk**.

Accordingly, you should {1} mount your FreeDOS CD image as normal, start up the FreeDOS virtual machine, {2} select the "boot FreeDOS from CD" option rather than the "install FreeDOS" option, {3} enter **fdisk c:** at the command prompt to get into the partition creation dialogue, {4} create a new primary or physical partition that uses all available space on your virtual c: drive (I forget whether it's "primary" or "physical," but it's NOT "logical"),  and then {5} power off the virtual machine (don't bother to save the machine state, do a soft off, or any other fancy power-downs; we're dealing with a DOS-like OS, remember?).

Now you should have a recognizable partition in your c: drive.  If you restart the machine with your installation CD image loaded, you should be able to select "Install FreeDOS," which will prompt you to format your virtual c: drive, and then you should proceed apace.

(B) _Question 2, roughly paraphrased: "How do I get files into the FreeDOS virtual disk from the computer inside which it is running?"_

Eh, that's a bit harder, since there don't seem to be any available Virtualbox add-ons for FreeDOS.  There may be ways to attach USB devices to the virtual machine from the virtualbox settings, but I haven't tried this.  My solution is rather quick and dirty: create an ISO file (i.e., a cd/dvd image file) containing the files you need, and mount that file as a CD before starting up your FreeDOS virtual machine.

Assuming your home directory is **/home/billy**, and assuming the files you want to put in the ISO are located in the directory **/home/billy/Desktop/myfiles**, and assuming you want your ISO to be named **myfiles.iso** and written to your desktop, you can create your ISO with the following command:

```
sudo mkisofs -Uo /home/billy/Desktop/myfiles.iso /home/billy/Desktop/myfiles
```

(You can look at the details of the **mkisofs** command by typing **man mkisofs** at the command line.)

Then, from within Virtualbox, you can mount this ISO, start up FreeDOS, and voila -- your files should be available from the d: drive.

I've posted the ISO-generating command along with some other command/settings info in my (mostly linux-concerned) computer wiki, which is located here:

[HTML]
http://home.windstream.net/marsh.cave/wikis/computer.html[/HTML]

Hope this helps!

-VoTMagn.

---

### Post by Pierre Maurette on 2009-04-18
> **Vorl the Magnificent said:**
> 
(B) _Question 2, roughly paraphrased: "How do I get files into the FreeDOS virtual disk from the computer inside which it is running?"_


[ Sorry for my poor english :( ]
Suppose you have - or decide to install - another guest, accepting additions, sharing a folder with the host. You just have to attach the FreeDOS disk (.vdi), as primary slave for example, to this guest, et voilà... You can "...get files into the FreeDOS virtual disk from the computer inside which it is running?", and also the opposite, easily modify the FreeDOS disk.
Hope this helps...
Pierre

---

