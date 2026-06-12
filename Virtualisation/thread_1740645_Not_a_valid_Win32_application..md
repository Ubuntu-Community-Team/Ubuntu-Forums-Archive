---
title: "Not a valid Win32 application."
date: 2011-04-27
forum: Virtualisation
---

### Post by Pengwyn44 on 2011-04-27
In Virtual Box I am running Windows XP with SP2. Generally speaking all programs run as expected, but I have a problem with Nuance Dragon 10. This CD runs OK on a Windows machine running XP with SP2, yet when attempting to load onto VBox XP I get the error message "Setup.exe is not a valid Win32 application."
Can any one suggest a solution please?


Pengwyn44

---

### Post by Joe of loath on 2011-04-27
Is it an nLite version? Also, you'll want to update to SP3. I had the same error in 2000 until I updated to SP4.

---

### Post by Pengwyn44 on 2011-04-28
Thanks for the suggestion. It is the Standard version. I have upgraded to SP3 but it makes no difference. My older Windows machine with SP3 won't even read the drive!
My newer XP machine with only SP2 did read it!
This is the only Windows program that I need, if only Nuance would port it to Linux.

---

### Post by ddjohnson6 on 2012-12-03
Similar Nuance problem with Dragon 12 in a qemu virtual machine running Windows 7 Ultimate SP1.

Both setup.exe and windows installer do not run from the mounted CD with above error message.

---

### Post by ddjohnson6 on 2012-12-03
Solved, but I don't know why/how.

In virt-manager, details screen, /dev/sr0, shared was unelected, the virtual machine restarted.
In windows 7 the setup.exe file was "troubleshot" to XP SP3 and virtual machine restarted. 
In windows 7 setup.exe was run as administrator with apparent success!
:P

---

