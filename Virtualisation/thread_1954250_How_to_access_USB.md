---
title: "How to access USB?"
date: 2012-04-07
forum: Virtualisation
---

### Post by LeeM on 2012-04-07
I just installed VirtualBox ok! Under it, I have installed a Windows 7 virtual machine, which is running ok, too. Hit one roadblock, though. When I go to add USB access, the manual says
to execute the command
sudo usermod -a -G vboxusers username

I assume it means the username for Windows 7, which in my case is 'Lee'. But when I run that command 
     sudo usermod -a -G vboxusers Lee
it responds
      usermod: user 'Lee' does not exist
 Should I be using my linux username instead?? I tried that, and
it accepts it, but still doesn't let me access USB.

HELP!  Thanks in advance!

---

### Post by na5h on 2012-04-07
The username refers to your username in Ubuntu, NOT in Windows 7. Try doing it again with your Ubuntu username.
Edit: You should also restart your computer after doing this.

---

### Post by Dedoimedo on 2012-04-08
No need to restart, just relogin.
Or in theory, open a new shell.
Dedoimedo

---

### Post by Cheesemill on 2012-04-08
Also for USB access you need to install the VirtualBox extension pack available here:
[https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)

---

### Post by DWade on 2012-04-09
And remember when the kernel updates in Ubuntu
you have to run this command to use virtual box 
"sudo /etc/init.d/vboxdrv setup"

---

