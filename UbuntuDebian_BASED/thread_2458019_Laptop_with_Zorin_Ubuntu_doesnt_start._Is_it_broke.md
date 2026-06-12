---
title: "Laptop with Zorin Ubuntu doesnt start. Is it broken?"
date: 2021-02-14
forum: Ubuntu/Debian BASED
---

### Post by 3sawyer on 2021-02-14
Hi dear people from ubuntuforums, i hope smbdy can give me a tip or help. I can only look for help with my old phone. I have Zorin Ubuntu 18.04. installed. Now the laptop doesnt start anymore. Most of the time i cant see whats going on there is only the Zorin Letters on screen. Somehow one time i could change something and icould record the screen. I hope somebody can see what the problem is.
[https://youtu.be/X-8cP7tZISE]("https://youtu.be/X-8cP7tZISE")
Thank you for every bit of help.

One thing i should mention: I had sometimes a problem with the Laptop. I fixed it with 

"exit
fsck /dev/sda1 -y
reboot"

After reboot the laptop worked again. But i dont really know what the problem was...I just found the solution somewhere...

---

### Post by howefield on 2021-02-14
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by grahammechanical on 2021-02-14
Is Zorin the only operating system on that machine? If it is not, do you get a Grub boot menu? If Zorin is the only OS we can bring up the Grub boot menu by pressing shift during the laptop's early boot process whilst it is still showing its own boot screen. If our machine has a BIOS settings utility we press shift. If the machine has a UEFI settings utility we press esc.

[https://askubuntu.com/questions/16042/how-to-get-to-the-grub-menu-at-boot-time](https://askubuntu.com/questions/16042/how-to-get-to-the-grub-menu-at-boot-time)

From the Grub boot menu we can select Advanced options for Ubuntu. I am assuming that Zorin still has this feature. Advanced options will let us select a Linux kernel with recovery mode. The recovery menu will let us do several things.

resume = Resume normal boot. It loads with a basic open source videos driver. Useful if we are having problems with a proprietary video driver.
clean = Try to make free space.
dpkg = Repair broken packages. You may need to do that if the login screen is failing to load.
failsafeX = Run in failsafe graphic mode.
fsck = Check all file systems.
network = Enable networking. Needed if we want to install packages.
root = Drop to root shell prompt. Necessary if we want to run commands on the OS. Typing exit returns us to the recovery menu.
system-summary = system summary.

I do not know if Zorin has what Ubuntu developers call Friendly Recovery but it is somewhere to start.

Regards

---

### Post by 3sawyer on 2021-02-14
@grahammechanical 
Yes Zorin is the only os on the laptop. I can open the grub boot menu and select Linux kernel with recovery mode. What do you recommend now?
[IMG]https://ibb.co/rw95tYp[/IMG]
-resume
-clean
-dpkg
-fsck
-grub
-Network 
-root
-system-summary
Screenshot:
[https://ibb.co/rw95tYp](https://ibb.co/rw95tYp)

I guess dpkg?
"Continuing will remote / filesystem in read/write mode and mount any other filesystem defined in /etc/fstab. Do you wish to continue?"
Will my files and documents still be there when i try this?
Is the hdd dying?

---

### Post by 3sawyer on 2021-02-16
> **grahammechanical said:**
> 

dpkg = Repair broken packages. You may need to do that if the login screen is failing to load

When i try dpgk this happens:
[https://ibb.co/C2gmWnJ](https://ibb.co/C2gmWnJ)

---

### Post by Frogs Hair on 2021-02-16
Have you installed any software from unofficial sources including PPAs?

---

### Post by 3sawyer on 2021-02-20
> **Frogs Hair said:**
> Have you installed any software from unofficial sources including PPAs?

It is possible i guess. I cant remember. I had some problems and i tried fixing it without knowing what i am doing in the terminal. Sometimes it worked sometimes i pasted text in terminal and it didnt work. I cant remember if it was smth with ppa...
Icant use dpkg now? Can i force it to run?

---

### Post by yancek on 2021-02-20
Have you tried going to a root shell prompt as show in one of the images you posted and running the ppa-purge command suggested in an image you also posted?

---

### Post by 3sawyer on 2021-02-24
> **yancek said:**
> Have you tried going to a root shell prompt as show in one of the images you posted and running the ppa-purge command suggested in an image you also posted?

Can you please tell me how to do that? 
I tried just typing ppa-purge but it didnt work.

---

### Post by yancek on 2021-02-24
The link below explains using ppa-purge.  If you have a name of a specific package you installed from a ppa, you can simply comment out that line in the file:  /etc/apt/sourdes.list by putting a hash mark at the beginning of that line in the sources.lsit file.  If you don't see an entry for that specific ppa there, it may be in a file under /etc/apt/sources.list.d.

---

