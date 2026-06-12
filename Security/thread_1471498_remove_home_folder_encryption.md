---
title: "remove home folder encryption?"
date: 2010-05-03
forum: Security
---

### Post by The Question on 2010-05-03
When I installed, I selected the option to encrypt my home folder.  I believe this is causing constant crashes now, since error message is user id/password related.  Is there a way to remove the encryption?

Thanks in advance.

---

### Post by Rokyking on 2010-05-03
1. Backup the home directory while you are logged in
sudo cp -rp /home/user /home/user.backup
1.1. Check that your home backup has everything!!!
2. reboot into root via grub
3. Delete your home directory
rm -rf /home/user
4. Remove the packages
apt-get remove ecryptfs-utils libecryptfs0
5. Restore your home directory
mv /home/user.backup /home/user
6. reboot
7. Remove any of those .Private .ecryptfs folders
rm -rf ~/.Private
rm -rf ~/.ecryptfs
8. Reboot. Should be working now. 

This worked for me. Home folder file permissions stay intact and does not bugger up Dropbox or git repos. Some reason my fresh install on Ubuntu 9.10 would not do the first command. Just make sure you think the process through when using rm -rf.

Taken from: Jemmrich 

Remember, the search bar and Google are your best friends.

---

### Post by The Question on 2010-05-03
Ok, I follow you on everything except step 2.  I have installed grub and tried to boot.  Apparently I am supposed to specify the kernel file it is going to use.  Where is it?

---

### Post by Rokyking on 2010-05-04
Once you see the GRUB menu you need to Press EXC After pressing 'ESC' you will be presented with a  list of kernels and operating systems that you can boot.
 You can press an up or down  arrow key to highlight a different kernel or operating system to boot.
 For example, you might need to  boot into 'recovery mode' to fix some problem with your operating  system.
 
To modify the boot options *within* the grub  menu, highlight the operating system you want to edit and press 'e'.
 There you will be presented  with lines starting with 'root', 'kernel', 'initrd', 'quiet' and  'savedefault'.
 You may wish to make changes  to any of these lines before booting.
 Boot options can be appended  to the end of the 'kernel' line, [Boot  Parameters]("https://help.ubuntu.com/7.04/installation-guide/i386/boot-parms.html").
 To receive a more verbose boot  process you can remove the 'quiet' line by highlighting it and pressing  'd' to remove that line.
 You may also want to highlight  the 'kernel' line press 'e' to edit and remove the word 'splash' from  the end of the line.
 After making any necessary  modifications you can press 'b' to boot that operating system.
 These modifications will not  persist across reboots.

---

### Post by The Question on 2010-05-05
Thanks for the info.  With my last question, I was actually running grub from the Terminal, not at start up, which was not quite right.

I did eventually figure out what to do.  You have to hold down SHIFT for grub2 (grub-pc package) now in 10.04 instead of ESC in grub.

Also, I needed to remove the /user.backup/.ecryptfs file before removing the ecryptfs-utils package as it doesn't work if it's in use by the .ecryptfs file.

Unfortunately all this didn't solve the crashing. :)

---

### Post by s0c0 on 2010-10-08
This worked fine for me.  One bit of advice.  Don't copy a backup of your home folder to /tmp.  Mine was removed after a reboot.  I ended up losing some settings after the reboot.  Luckily it was just email accounts that I can re-add to evolution (all of its IMAP).  Instead copy it some place not dumb, like /var/myhomefolder or something.

---

