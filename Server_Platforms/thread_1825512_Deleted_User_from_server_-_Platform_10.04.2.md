---
title: "Deleted User from server - Platform 10.04.2"
date: 2011-08-15
forum: Server Platforms
---

### Post by mytinytown on 2011-08-15
I did the dumbest rookie mistake possible.

I changed my server's location and it needed a new user/password. So I deleted my user/password first. After this I realize now there is no user to add the new user/password. Any help here? I tried using the root and the original user/password, but as I expected, it did not work.

You should always add the user first, then delete the old one!

---

### Post by maikel.b on 2011-08-15
If you have forgotten your[ ubuntu password]("http://ubuntuguide.net/execute-sudo-command-without-asking-for-password"),please don’t worry,it incredibly easy to reset your password.
Just reboot your computer and select [***the recovery mode***]("http://ubuntuguide.net/prevent-resetting-ubuntu-password-from-recovery-mode"),which is usually the second line in Grub menu.
Then,you’ll see the *Recovery Menu*,choose “*root Drop to root shell prompt*” in this menu.
Now,you can use following command to change password.
cd /home

passwd usernameMy username is *wraith*,so I use:
passwd wraiththen,enter the new password and confirm.
Go back to Recovery Menu by this command,and choose “*resume resume normal boot*”
exit

"I found this on the INTERNET, it should work also for root"

I hoop this will work for you, and you can use the server again!

You should use the command passwd root 

Enter a new password for the root user, reboot the system and log in as user root!

Good luck!

---

### Post by mytinytown on 2011-08-15
I did not forget the password, but logging in and setting my root as active worked! So Thank you!!

---

