---
title: "How am i find the User name?"
date: 2009-03-03
forum: Security
---

### Post by sanath1978 on 2009-03-03
I have installed a Ubuntu to my desktop and it is running Xp as well. When i installed Ubuntu, It is asking a User name and password. I have tried many and non of them are working. what is the log-in password?
Any one can help me
I will appreciate it

---

### Post by gvr2600 on 2009-03-03
When you installed ubuntu, you specified a username and a password, try to remenber them or reinstall os, it will take you less than 30 min of work, considering the fact that you havent installed nothing on your ubuntu yet.

---

### Post by Mud.Knee.Havoc on 2009-03-03
What??  You don't need to reinstall if you forget a password.  Honestly, gvr2600, you should avoid telling people to reinstall when it's not necessary.

From [http://ubuntuforums.org/archive/index.php/t-133102.html]("http://ubuntuforums.org/archive/index.php/t-133102.html"):

The Howto:
1. Boot up your computer, and when you see the screen that says something like "Press ESC to enter grub," press ESC (the escape key) as soon as you can.

2. Now you should see a menu with many options. Use the arrow keys to navigate to the newest kernel (the one with the highest number) that has "(recovery mode)" written next to it. Now, hit enter (return).

3. Next, your system should boot up normally. BUT, you WILL NOT see the boot splash. Don't worry about that. Lots and lots of text WILL fly past you.

4. Now you are at a root shell.

5. Type

passwd username

replacing username with your username

6. Now a little thing will come up and say "New UNIX Password" or similar. Type the new password that you want. Hit enter. Type it again. Hit enter

7. Then, your password has been changed! Type

shutdown -r now


8. Your system is now rebooting. Once it comes back up, login with your new username and password.

9. There is no step nine.


--------------

EDIT: Just occurred to me that you might have forgotten the username, as well.  You can also add a user at the command prompt by using the useradd command (replace <username> with your desired username):

```
adduser <username>
```

---

### Post by bodhi.zazen on 2009-03-03
Boot to recovery mode

You will get a root shell.

#List user names
ls /home

#Set password
passwd user_name

user_name = user to set a password

Then reboot.

---

