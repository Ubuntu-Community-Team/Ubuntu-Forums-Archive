---
title: "VirtualBox won't uncapture?"
date: 2008-09-21
forum: Virtualisation
---

### Post by AtomicClock on 2008-09-21
I am attempting to creature a Windows XP virtual machine from my existing XP Pro partition. 
I followed the basic guide by Balverine (create MBR, add to vboxusers and usbusers, create VMDK image, etc) and it seemed to be working fine. When I tried to mount the image as a hard drive in VirtualBox, it came up with a "VERR_ACCESS_DENIED" error. Changing the permissions with chmod didn't help. So I tried running VirtualBox as a superuser, and it worked. I have checked the IO APIC and have enabled USB and USB 2.0 support, as well as added the device filters. 
Now when I try to start the virtual machine, VB captures my input, and it just won't uncapture. Pressing right-Ctrl does nothing more than show and hide the Ubuntu cursor, while my actual mouse is still trapped inside the virtual machine. I end up having to restart the system, because even if I kill VirtualBox, the mouse doesn't come back.

My mouse and keyboard are a wireless Microsoft combination.

Any ideas?

---

### Post by AtomicClock on 2008-09-23
<bump>
Anyone?
</bump>

---

### Post by ericy on 2008-09-23
This may help:

File->Preferences->Input -> uncheck "Auto Capture Keyboard"

It doesn't solve the problem completely though. You still need to install "Windows Guest Additions".

---

### Post by AtomicClock on 2008-09-26
I installed Windows Guest Additions (at least I think I did, I clicked the option, but nothing happened. However, I know for a fact that the ISO is in the VB directory, I even mounted it as the CD/DVD drive), but that didn't do anything. I tinkered some more with the USB options, and I did what you said, so now it doesn't autocapture and also I can uncapture it, BUT now the USB isn't even working anymore. The filters are there, even the options are there when the guest is running, but they're grayed out; I can't select them.

If you need any more info, just ask. It'd be great if I could get this running.

---

### Post by AtomicClock on 2008-10-02
</Bump>

---

### Post by JKyleOKC on 2008-10-27
> **AtomicClock said:**
> I installed Windows Guest Additions (at least I think I did, I clicked the option, but nothing happened.

Sorry to be so late in getting here, but I only ran into this problem myself today. What I discovered was that the documentation for installing Windows Guest Additions is woefully incomplete! Just clicking the option does nothing.

You have to first unmount the CD/DVD device, then mount the .iso that contains the guest additions (the dialog offered it to me as a choice so I didn't have to type in a path). Only then will clicking the option work. When it does work, you get a wizard-style series of dialogs that walk through the installation.

This was all done with the Sun version 1.6.2, so if you're using an older version your mileage may vary...

---

### Post by raghavendramb on 2009-02-10
I was happy with my XP guest os :), until one day, my cousin was playing with hardy.....:).....Just after that I logged in and everything was fine, i really didnt check the virtualbox, after somedays when i checked the keyboard was not getting uncaptured! I finally figured out that If you have support to enter complex characters enabled in Language Support, then the keyboard input doesn't work in Virtual Box!, Check it out :)

---

### Post by AtomicClock on 2009-03-30
Thanks everyone for your help. I know it's been quite a while, but I just started tinkering with it again, and I've figured it out. What was happening was that Windows wasn't detecting the new hardware and it wasn't installing correctly because I had it set with a logon screen. I decided to test it by directly booting to the desktop, and it began detecting and installing the new hardware (I didn't use any USB filters). After that, the mouse and keyboard successfully capture and uncapture.

Later on I installed the Guest Additions, just like how JKyleOKC explained it. Apparently, the additions are installed directly in the guest OS, much like a standard application.

Because of the hardware change, Windows does need reactivation. I managed to fix it, but before I did, I tried booting into Windows natively, and that was unauthenticated as well. So, anyone contemplating virtualizing your existing partition, be warned.

Anyone, thanks a lot guys.

---

### Post by pointym5 on 2009-04-07
I've just brought up Virtualbox for the first time, and it captures the keyboard and won't release it.  I'm not doing anything with weird characters or anything, and it's running as root.  The helpful but incorrect startup dialog indicates that it will release the keyboard and mouse in response to pressing the right control key, but it does not.

---

### Post by Wharf Rat on 2009-04-08
> **pointym5 said:**
> I've just brought up Virtualbox for the first time, and it captures the keyboard and won't release it.  I'm not doing anything with weird characters or anything, and it's running as root.  The helpful but incorrect startup dialog indicates that it will release the keyboard and mouse in response to pressing the right control key, but it does not.

Same here.

---

### Post by MobiusCoffee on 2009-04-13
I need complex characters, it's not something I'm willing to disable.  This is a big problem for me because I can't exit VB or anything.  I'm just stuck inside unless I ctrl+alt+backspace or just turn off my computer.

On a different note, I have this same problem on windows with VB, bu I can get out of it without doing something so drastic.

---

### Post by dhughes on 2010-02-04
I've run into this, I finally got USB devices working and was trying it out (connected my N95 phone), the mouse was now very slow compared to the previous setup before this new USB config.

 The worst part was I could not get my mouse back to keyboard control back and then the screen saver kicked in, screen power actually, and I was stuck inside the VM, Windows XP.

 CTRL+Backspace didn't work, CTRL+ALT+F1,2,3 etc. didn't work, I even tried plugging in a USB thumbdrive and an external USB hard drive hoping to wake up my system from the screen saver but that didn't work.

 Even pressing the power button on my computer case didn't work, it did stop the screen saver but then it showed the count-down to Shutdown but then wouldn't proceed, I had to perform a forced hard reset with applications still running; the VM, Firefox, text editor and some other apps.

 Nothing mentioned above worked for me, just adding my 2 cents, I'll get back if I find something after my tea kicks in and my brain works.

---

