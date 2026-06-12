---
title: "Removing administrative abilities from users"
date: 2009-03-18
forum: Security
---

### Post by stareye on 2009-03-18
At my school we are starting up a test linux lab to see how it goes over with the students. We are trying three different versions, Ubunutu, Linux Mint, and Suse. The ubunutu install is under my control. I am attempting to create a student account with as few privileges as possible. Most of the main things, such as synaptic, were easy to lock out simply by unchecking all of the categories under the users and groups>configure>privileges menu. Yet still many things remain under the preferences and administrative panels that I would like to exclude, such as authorizations, network tools, system log, etc. In fact, what I would really love to do would be to remove the administrative menu from the main menu altogether in that account. 

Thanks in advance for the help!

---

### Post by kpatz on 2009-03-18
Make sure the account(s) used by students are NOT in the admin group.  This way they can't use sudo/gksudo.

You can delete the Administration menu from the Gnome menu editor for that user.

---

### Post by bodhi.zazen on 2009-03-18
You can and further restrict them with apparmor.

See this repository :

[http://bodhizazen.net/aa-profiles/](http://bodhizazen.net/aa-profiles/)

Jdong posted "jailbash" , a default shell.

I modified jailbash and use zsh, so jailzsh. With jailzsh can even give root access but still restrict even root from doing things I do not like.

---

### Post by stareye on 2009-03-18
Thanks! The student account is under its own group, also named student. It is now set so that the administrative menu does not appear.

---

### Post by stareye on 2009-03-18
Further testing - students can still right click on menu and get access to menu settings. Any way to restrict this?

---

### Post by bodhi.zazen on 2009-03-18
How much do you want to lock down the account ? Do you want to lock down the panels, menus, desktop background, themes, icons, ?

---

### Post by stareye on 2009-03-18
> **bodhi.zazen said:**
> How much do you want to lock down the account ? Do you want to lock down the panels, menus, desktop background, themes, icons, ?
Preferably: menus, background, themes, icons. I'm going to download and try out app armor.

---

### Post by bodhi.zazen on 2009-03-18
I strongly advise kde and kde kiosk :

[http://enterprise.kde.org/articles/kiosk-lp.php](http://enterprise.kde.org/articles/kiosk-lp.php)

---

### Post by lensman3 on 2009-03-18
You realize that all somebody has to do if they have physical access to the machine is boot up in single user mode.  Reset the password or add a user to root or the wheel groups, to have root access.  Or in single user mode copy the passwd and shadow files to a safe place to crack the passwords.

I would just restrict who has knowledge of the root password and modify the sudo  config file so that only certain users and groups can run sudo.


Why don't you for the Linux lab, tell the students that whoever cracks or gets the superuser password gets an "A" in class.  Let the class discover as part of their grade, how to secure a Linux machine.

---

