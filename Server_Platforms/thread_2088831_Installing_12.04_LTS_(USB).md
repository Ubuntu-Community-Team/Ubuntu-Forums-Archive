---
title: "Installing 12.04 LTS (USB)"
date: 2012-11-27
forum: Server Platforms
---

### Post by JIohn on 2012-11-27
Hi!
 
I've administered and maintained an Ubuntu server(10.04) for a couple of years now. Today I decided to wipe everything, and do a clean installation of the 12.04 LTS. The server I'm using has no CD-Drive, nor is it capable of having one, thus I tried the install via USB.
 
After I downloaded the iso I checked the checksum, which came back positive. Then I went onwards with the installation. After a while I got stuck at a screen saying something about not being able to mount CD. I looked in the installation log and found the following: 
 
main-menu[332]: DEBUG: resolver (libc6-udeb): package doesn't exist (ignored)
main-menu[332]: DEBUG: resolver (libnewt0.25): package doesn't exist (ignored)
 
I'm stuck. I've googled around everywhere and the commonly accepted solution to this have been to bypass it with CD/DVD. A solution which, sadly, I am not able to use.
 
Any Ideas?
 
I've located the files on the usb, there seem to be nothing wrong with them, yet the installer claims they don't exist. I've also tried using
 
EDIT: Solved using  **Catalyph's **advice using another USB device.

---

### Post by ibjsb4 on 2012-11-27
The mini.iso will not work either with the ubuntu usb installer.  I found that it will work with unetbootin installer.  I wonder if that would work with the server install.

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by JIohn on 2012-11-27
> **ibjsb4 said:**
> The mini.iso will not work either with the ubuntu usb installer. I found that it will work with unetbootin installer. I wonder if that would work with the server install.
 
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
 
I'm sorry I forgot to mention that I've tried the UNetBootin as well, without any luck

---

### Post by ibjsb4 on 2012-11-27
Not the greatest idea, but a work-a-round.  Use the mini.iso.  You can do just a console install with it or use the UI (user interface) for a server install.

---

### Post by Catalyph on 2012-11-27
Use a different USB stick.
I had an old 1GB USB stick and tried and i got the same error.
Then when i put the exact same iso and stuff using the PenDrive application onto a newer 8GB USB, everything worked perfectly.

---

### Post by JIohn on 2012-11-27
> **Catalyph said:**
> Use a different USB stick.
I had an old 1GB USB stick and tried and i got the same error.
Then when i put the exact same iso and stuff using the PenDrive application onto a newer 8GB USB, everything worked perfectly.
 
Eureka!
 
It worked and it did so without any fuzz, thanks a lot!!!
 
I'd like to thank everyone who spent a moment to help me out!

---

### Post by Catalyph on 2012-11-27
> **JIohn said:**
> Eureka!
 
It worked and it did so without any fuzz, thanks a lot!!!
 
I'd like to thank everyone who spent a moment to help me out!
 
 
Awesome glad I could help!

---

