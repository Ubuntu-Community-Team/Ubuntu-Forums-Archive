---
title: "FreeSSHd running on Windows Server"
date: 2013-06-06
forum: Server Platforms
---

### Post by Tropicalbound on 2013-06-06
Hello,

I have installed FreeSSHd on a Windows server and I can connect successfully from Ubuntu 13.04.  However, all the text that is on the terminal window prior to establishing the SSH connection stays.  It will not purge.  I've tried both the Ubuntu 'Clear' command, and the Windows 'cls' command.  I've also tried the carriage return several times in hopes the text would scroll off the screen, but nothing helps.  Can someone please tell me what I'm doing wrong?

Thanks!!

TB

---

### Post by matt_symes on 2013-06-06
Thread moved to **Server Platforms**.

@OP. This may be moved again to 'Other OS/Distro Talk'.

---

### Post by Tropicalbound on 2013-06-06
I found a work around for this issue.  Not an elegant solution, but it works.

gnome-terminal ssh <servename> -l <username>

This opens the ssh session in a fresh new terminal window without any of the previous commands.

---

