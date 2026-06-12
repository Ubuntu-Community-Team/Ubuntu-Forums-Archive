---
title: "Locked Out Of Kubuntu"
date: 2010-01-15
forum: Security
---

### Post by Dynamata on 2010-01-15
I installed Kubuntu in persistent mode to a USB stick using Linux Live USB Creator:
 
[http://www.linuxliveusb.com/](http://www.linuxliveusb.com/)
 
I installed Firefox but could not see it in Applications, so I logged out to re-start Xserver only to be asked for login details. I tried ubuntu:ubuntu, kbuntu:kbuntu, root:root,ubuntu:_, kbuntu_, root:_, re-booted PC & am still locked out.
 
What are the login details? I was never given any. :(

---

### Post by adam814 on 2010-01-15
I'm guessing it automatically logs in as "liveuser" or something similar.  Try rebooting to see if it logs you in automatically again, then open a terminal and type "whoami" to find out your username.  Then run "passwd" in the same terminal to set the password to one you do know.

---

### Post by Dynamata on 2010-01-16
Did reboot, there is a terminal link at the login, I typed "ls /home" to display a list of users & got "ubuntu". I typed "passwd ubuntu" & re-set password to 1234567. Trouble is the cursor doesn't move so if you have a key-bounce on the same digit when repeating the password you wouldn't know.

In any case I couldn't login, now when I try another re-set I am asked for the old password & 1234567 is rejected.

---

### Post by adam814 on 2010-01-16
I suppose.  It's just unusual to have the same key-bounce twice in a row.

Try "sudo passwd ubuntu" instead.  That might let you change it without the old one.

---

### Post by Dynamata on 2010-01-17
Unusual but not impossible, anyway sudo allowed me to set a new password but typing exit didn't get me back to the login panel so I re-booted. The new password was rejected, when I tried to re-set I got the message: "Authentication token manipulation error".

I'm going to re-install, pointless having an OS that is so secure it becomes unusable. Thanks for the help. :|

---

