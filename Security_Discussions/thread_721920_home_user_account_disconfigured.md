---
title: "home user account disconfigured"
date: 2008-03-11
forum: Security Discussions
---

### Post by wycito on 2008-03-11
Hi fellas, I am a newbie, just deleted a user account and changed my own home folder the  name was
 /home/luie2 
and changed it to /home/luie
now i canot log into my ID in the main login window, gives me an error
and I did not authorise root to log from the mail login window
now I am screwed, cannot access neither my home folder nor my files
Thanks
:confused:
Is there anyways to repair the user account ?

---

### Post by itix on 2008-03-11
Your files should be ok if you log in as root. Go to the log in screen and type root in the username space and then the root password that you speciefied when you installed ubuntu. From root you should be able to create a new user account and move the files to the new home folder

---

### Post by wycito on 2008-03-12
Thanks for the reply but I havent authorised root lo login from the main window, so no cant do, can login as root from the CLI in the rescue mode, but even from there, how to create a new -home folder- for a user(me)
Thanks again if I do not get out of this one will have to reinstall the OS
Thank you

---

### Post by itix on 2008-03-12
That'll mean lost data which is not very good. I sure hope for your sake that someone more of an ubuntu geek than me will solve it for you.

---

### Post by handydan918 on 2008-03-12
OK, let's take a swing at this, since no one else has....
Boot into rescue mode. 

Do```
 usermod  -l <new_username_here> <old_user_name_here>
```

You may then have to check man usermod to change back to your original UID if you can't access your files.
 
No guarantees, but it seems like you are running out of suggestions. It's better than hosing your installation and starting over.

---

### Post by wycito on 2008-03-12
thanks I will try that and i think the error is mostly that i changed in the user account the home folder name + the user name and rebooted
Thanks will be letting you guys know, appreciate your help

---

### Post by wycito on 2008-03-15
All fixed now, just created a new account with sudo cap. and from there could access my home folder and rename it, just had to think about it for a few days, thank you all
Wycito

---

