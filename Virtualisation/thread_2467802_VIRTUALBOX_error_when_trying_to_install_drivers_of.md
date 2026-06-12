---
title: "VIRTUALBOX error when trying to install drivers of the guest additions"
date: 2021-10-08
forum: Virtualisation
---

### Post by ronjjjg8885 on 2021-10-08
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289247&stc=1[/IMG]

hi
i'm trying to restore my windows 10 clone but get this.

how to fix it?

thank you!!

---

### Post by ronjjjg8885 on 2021-10-08
i've tried [this]("https://duckduckgo.com/?q=VBoxGuestAdditions_+is+inaccessible+and+is+being+ignored.+Please+select+a+different+image+file+for+the+virtual+DVD+drive..&t=ffab&ia=web") search but no good results there that solve it

this is the messege..

```
  The image file '/home/win/.config/VirtualBox/VBoxGuestAdditions_6.1.26.iso' is inaccessible and is being ignored. Please select a different image file for the virtual DVD drive..
 

 [TABLE]
[TR]
[TD] Error ID: [/TD]
[TD] DvdOrFloppyImageInaccessible[/TD]
[/TR]
[TR]
[TD] Severity: [/TD]
[TD] Warning[/TD]
[/TR]
[/TABLE]

```

---

### Post by QIII on 2021-10-08
Moved to Virtualisation as a more appropriate sub-forum.

---

### Post by SeijiSensei on 2021-10-08
Do you have a copy of VBoxGuestAdditions_6.1.26.iso? Is it in the /home/win/.config/VirtualBox/ directory? Do you have permissions to that directory and file? 

The error says it cannot find the Guest Additions iso. 

You might be able to get around the problem in the short term by changing the settings on the virtual machine and telling it not to use that ISO.

---

### Post by aug7744 on 2021-10-08
Download Virtualbox current version run file.
Try doing a unninstall command.
Install Python 2.7 and only after install VirtualBox. Not changing default settings the software will be installed in /opt.
After try mount the virtualbox addons using the virtualbox window menu and run the command with exact naming about the Ubuntu file in disc mounted root.

---

### Post by ronjjjg8885 on 2021-10-09
i'm checking that now
thanks!!!!

---

### Post by ronjjjg8885 on 2021-10-09
> Do you have a copy of VBoxGuestAdditions_6.1.26.iso? Is it in the /home/win/.config/VirtualBox/ directory?

no
it isn't there
i did ctrl + h for seeing all files but it isn't there.

do i need to get involved in changing permissions too?

where do i get the .iso file for copy it to there?

i need the file for making drivers installation.

i've tried both downloading the virtualbox installation from oracle and also with the apt get command (i did it separately and removed the packages before installing the other one) but i still got the error.

perhaps i just need the file but i don't know where to find this image file. do you know?

i'm not tech savvy

i will read the other comments now too......

---

### Post by MAFoElffen on 2021-10-09
Because... That is not how it is done...

[6.4. Installing the VirtualBox Guest Additions]("https://docs.oracle.com/cd/E36500_01/E36502/html/qs-guest-additions.html")
[Chapter 4. Guest Additions - VirtualBox]("https://www.virtualbox.org/manual/ch04.html")
[4.2. Installing and Maintaining Guest Additions]("https://docs.oracle.com/en/virtualization/virtualbox/6.0/user/guestadd-install.html")

Need I say  more?

---

### Post by ronjjjg8885 on 2021-10-09
in the past when i've used it it worked like a charm btw

i will read the links. maybe i could figure it out..

edit
BTW
i've followed this guide last time.....

it didn't ask to use any commands in the windows guest....

---

### Post by ronjjjg8885 on 2021-10-09
i think i could mount it by
> Select **Mount CD/DVD-ROM**               from the **Devices** menu in               the virtual machine's menu bar and then               **CD/DVD-ROM Image**. This               displays the Virtual Media Manager, described in               [Section 5.3, &#8220;The Virtual Media Manager&#8221;]("https://docs.oracle.com/en/virtualization/virtualbox/6.0/user/vdis.html").

there was not "**Mount CD/DVD-ROM" **option there in my version but i figured it out....

let me now see if everything is right

edit
thank you all!
it's working!!

---

