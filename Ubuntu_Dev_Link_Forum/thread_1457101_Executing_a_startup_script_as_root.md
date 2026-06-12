---
title: "Executing a startup script as root?"
date: 2010-04-18
forum: Ubuntu Dev Link Forum
---

### Post by usmanajmal on 2010-04-18
Hi
  **The main question:**
Can I make my script run as root at startup such that all commands (e.g mount, dd etc) may also run as root no matter  if root , administrator, desktop user or an unprivileged user logs in? 
 


   **What does the script do?**
  The script mounts a partition, looks for a file in that partition and finally on the basis of that file a decision of copying a partition to another partition is made. That copying is done via
  dd if=/dev/sda2 of=/dev/sda5
 **When does the script run finely?**
  Script runs smoothly when I run it from the terminal by 
  sudo ./my_copying_script
 This command asks me for the password of currently logged in user. I enter the password and the script starts working.
  **When does the script NOT run finely?**
  I want to run the script at startup. I set it a startup program by using the **Startup Applications** utility of Ubuntu. Script ran at startup but exited at the dd command returing following error:
  dd: opening '/dev/sda2': Permission denied 
  I then prefixed the dd with sudo as mentioned below
   sudo dd if=/dev/sda2 of=/dev/sda5
 but this returned following error:
sudo: no tty present and no askpass program specified

---

### Post by quixote on 2010-04-19
You're using dd commands in an automated script?  :shock:  Is that really what you want?

If yes, then I think you could have the script run with root permissions by putting it in a system dir, eg /usr/local/my-copying-script and giving it the right execute permissions.

If you're running it as a user, and "sudo ./my-copying-script" works, that implies you have it in your home directory.  Is that right?

---

