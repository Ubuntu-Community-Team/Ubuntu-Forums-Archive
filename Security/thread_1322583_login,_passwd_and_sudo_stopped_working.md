---
title: "login, passwd and sudo stopped working"
date: 2009-11-11
forum: Security
---

### Post by zluspai on 2009-11-11
Dear All,

I'm using Ubuntu 9.1 now.
Since few days ago I have noticed that sudo stopped working. Also I can not change my own password, root password anything. If I go to the text console (ctrl-f1) that won't allow me to login, and I can only use my gnome desktop because the auto-login is configured. Interesting enough the network applet which connects to wifi asks for keyring password, and it accepts my password typed in, which is the same what the login should accept too. 
I have tried to change my password or root user's password in single user mode (by choosing the recovery mode during bootup), but that does not work either. It asks for the password, but the change is not applied. 
What can I do?

Btw; the logins got broken after I was playing with samba configuration. Maybe that is related? Since then I have removed the samba packages (using apt).

Thanks,
Zoltan

---

### Post by cariboo on 2009-11-11
Samba shouldn't have anything to do with passwords unless you went really wrong during the configuration. You should be able to start in recovery mode and reset your user password. Once at the prompt type:

```
passwd <username>
```

and create a new password.

---

### Post by zluspai on 2009-11-12
Actually the passwd etc does not work in single user mode (recovery console) either. If I try to change password of root or my user this silently fails - no error message is printed-, and the change is not in affect.

What else to check, fix?

---

### Post by rojertwose on 2009-11-12
Hi ,
I'm not expert but I'm regular user of Ubuntu 9.04.. I have some thing for you to solve you problem .. Make a closer look to it ... Follow this steps .. Good luck...

**Reset Your Ubuntu Password**
 Reboot your computer, and then as soon as you see the GRUB Loading screen, make sure to hit the ESC key so that you can get to the menu.
 
 **Root Shell – Easy Method**
 If you have the option, you can choose the “recovery mode” item on the menu, usually found right below your default kernel option.
 [IMG]http://www.howtogeek.com/wp-content/uploads/2008/09/image%5B3%5D.png[/IMG] 
  Then choose “Drop to root shell prompt” from this menu.
 [IMG]http://www.howtogeek.com/wp-content/uploads/2008/09/image%5B6%5D.png[/IMG]
 This should give you a root shell prompt.


 **Alternate Root Shell Method** 
 If you don’t have the recovery mode option, this is the alternate way to manually edit the grub options to allow for a root shell.
 First you’ll want to make sure to choose the regular boot kernel that you use (typically just the default one), and then use the “e” key to choose to edit that boot option.
 [IMG]http://www.howtogeek.com/wp-content/uploads/2008/09/image34.png[/IMG] 
 Now just hit the down arrow key over to the “kernel” option, and then use the “e” key to switch to edit mode for the kernel option.
 [IMG]http://www.howtogeek.com/wp-content/uploads/2008/09/image35.png[/IMG]
 You’ll first be presented with a screen that looks very similar to this one:
 [IMG]http://www.howtogeek.com/wp-content/uploads/2008/09/image36.png[/IMG]
 You’ll want to remove the “ro quiet splash” part with the backspace key, and then add this onto the end:[INDENT]**rw init=/bin/bash**
 [/INDENT][IMG]http://www.howtogeek.com/wp-content/uploads/2008/09/image37.png[/IMG] 
 Once you hit enter after adjusting the kernel line, you’ll need to use the B key to choose to boot with that option.
 [IMG]http://www.howtogeek.com/wp-content/uploads/2008/09/image38.png[/IMG] 
 At this point the system should boot up very quickly to a command prompt.


 **Changing the Actual Password**
 You can use the following command to reset your password:[INDENT]**passwd <username>**
 [/INDENT]For example my username being *geek* I used this command:[INDENT]passwd geek
 [/INDENT][IMG]http://www.howtogeek.com/wp-content/uploads/2008/09/image39.png[/IMG]
 After changing your password, use the following commands to reboot your system. (The sync command makes sure to write out data to the disk before rebooting)[INDENT][B]sync
reboot –f[/B]
 [/INDENT]I found that the –f parameter was necessary to get the reboot command to work for some reason. You could always hardware reset instead, but make sure to use the sync command first.
 And now you should be able to login without any issues.

---

