---
title: "Ubuntu won't boot after every other reboot"
date: 2014-06-27
forum: Virtualisation
---

### Post by kakashi_12 on 2014-06-27
I have Ubuntu 14.04 64 bit installed in a virtual machine with 3 other OS's. GRUB is installed to the same partition as the ext4 (Linux) partition, rather than the MBR.
When I used Grub Customizer though, I think it may have written it additionally to the MBR. Not sure.

Anyways, some times when I boot the system and choose the OS from the boot menu (BCD boot menu) sometimes it loads fine and some time it gets stuck and I need to reboot it. Then it's fine again. See attachments to see the screen it gets stuck on. See 2nd attachment, as sometimes it will display this extra line and get one line further, but freeze still.

---

### Post by Bucky Ball on 2014-06-27
*Thread moved to **Virtualisation**.*

---

### Post by kakashi_12 on 2014-06-27
Re-installed the OS on a brand new disk. This time installed GRUB directly to MBR. Still no difference. Still freezes at boot up on same screen.
Only does it on Reboots and not Shutdown then fresh Boot up. It seems so.
Edit... or not. It happens on both Reboots and after a Shutdown and Startup.

---

### Post by Bucky Ball on 2014-06-27
Might be an idea to run [bootinfoscript]("http://sourceforge.net/projects/bootinfoscript/") and post the link here.

---

### Post by kakashi_12 on 2014-06-27
good idea.

---

### Post by kakashi_12 on 2014-06-28
Or not. Not working.
ubuntu@ubuntu:~/Downloads/bootinfoscript-061$ sudo bootinfoscript
sudo: bootinfoscript: command not found
su
password:
root@ubuntu:/home/ubuntu/Downloads/bootinfoscript-061# bootinfoscript
The program 'bootinfoscript' is currently not installed. You can install it by typing:
apt-get install boot-info-script
You will have to enable the component called 'universe'
root@ubuntu:/home/ubuntu/Downloads/bootinfoscript-061# apt-get install boot-info-script
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package boot-info-script
root@ubuntu:/home/ubuntu/Downloads/bootinfoscript-061# ls
bootinfoscript  CHANGELOG  README
root@ubuntu:/home/ubuntu/Downloads/bootinfoscript-061# bootinfoscriptThe program 'bootinfoscript' is currently not installed. You can install it by typing:
apt-get install boot-info-script
You will have to enable the component called 'universe'

---

### Post by Bucky Ball on 2014-06-28
Easiest to perhaps use Boot Repair and that will create one for you. 

[https://help.ubuntu.com/community/Boot-Repair#Getting_Boot-Repair](https://help.ubuntu.com/community/Boot-Repair#Getting_Boot-Repair)

You can install in 'Try Ubuntu' booting from the LiveDVD or download the ISO, burn a disk/USB and boot from that.

---

### Post by kakashi_12 on 2014-06-28
ok. I've used that before.

---

### Post by kakashi_12 on 2014-06-28
[http://paste.ubuntu.com/7716312/](http://paste.ubuntu.com/7716312/)

---

### Post by kakashi_12 on 2014-06-28
I ran Ubuntu Updates, there were several updates to be installed. So far, it's been successful ever since. Not sure if this was the source of the issue or not. Maybe an update fixed something.

---

### Post by Bucky Ball on 2014-06-28
See if it stays fixed for awhile and if so, please mark this thread as solved to help others. Cheers. ;)

I could see nothing amiss with your bootinfoscript output ...

---

### Post by kakashi_12 on 2014-06-28
Nope. It's still intermittently not booting.

---

### Post by kakashi_12 on 2014-07-05
I'm booting the virtual pc and choosing to boot the hard drive from the BIOS Boot Menu, Rather than from the boot loader. And I don't even see those screens (in my attachment). So it seems like a problem with BCD, not GRUB. From what I can gather.

---

### Post by kakashi_12 on 2014-07-05
I've booted several times from BIOS boot menu, boots EVERY time.
I've already posted in BCD forum. Their help was worthless. No response yet.

---

### Post by kakashi_12 on 2014-07-11
I think I've fixed this for good now. And this is on my physical PC! :)
Instead of installing Linux last, I installed it first.
However, Linux was on it's seperate HDD while installing and configuring the other HDD with Windows OS's was unplugged.
After installing Linux, I ran Grub Customizer and told it to not display boot menu, remove recovery entries, and not to look for other OS's.
Then I shutdown, unplugged HDD with Linux on it. Plugged in blank HDD. Turned on and installed all Windows OS's on this drive.
Shutdown, plugged both drives in.
Booted into BIOS, made the HDD with Windows OS's on it the First Boot Device (after CD drive of course).
Installed and ran Easy BCD. Configured it. Rebooted and tested all entries. Rebooted Ubuntu about 5 times. Seemed to work every time without halt.

Seemed when I did this before, installing Linux last and unplugging HDD's and such, Grub Customizer was complaining about that it use to be 'sda' and that it was now 'sdb' or something. I think that's the problem. Because I was plugging and unplugging. But since I ran Grub Cust first, things stayed one way.

---

