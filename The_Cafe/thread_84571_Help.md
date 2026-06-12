---
title: "Help"
date: 2005-10-31
forum: The Cafe
---

### Post by ebonysurfer on 2005-10-31
I am new period  I can't even get the new section to work :(  I have loaded ubuntu at least five times trying to use root and still can't even after reading directions and yes i have the password right.

---

### Post by basketcase on 2005-10-31
so at the prompt you type su ?  It asks for a password, and then what?

---

### Post by Dr. Nick on 2005-10-31
Not sure I understand the entire question but can say that using "su" in ubuntu by default doesnt work. If you want root use sudo *command* then user password from the 1st user made in installation

---

### Post by basketcase on 2005-10-31
[QUOTE=Dr. Nick]Not sure I understand the entire question but can say that using "su" in ubuntu by default doesnt work. If you want root use sudo *command* then user password from the 1st user made in installation[/QUOTE]


Forgot that in my advertures of the weekend with a trip around Linux (5.04/Vector/Suse 10.0/5.10)

Sudo.....

---

### Post by Kvark on 2005-10-31
"su" doesn't work but "sudo su" works perfectly fine. Just add sudo or gksudo (gksudo is the gui version of sudo) in front of the command whenever you need root access.

---

### Post by ebonysurfer on 2005-11-02
Thanks  now let see if i have this right in the orignal(first) log in screen for user name i type sudo su  and then it will prompt for the password which i then type in correct](*,)

---

### Post by Ampersand on 2005-11-02
No, you log in with your usual username, then use sudo when running commands from a terminal.

---

### Post by basketcase on 2005-11-02
[QUOTE=ebonysurfer]Thanks  now let see if i have this right in the orignal(first) log in screen for user name i type sudo su  and then it will prompt for the password which i then type in correct](*,)[/QUOTE]


No, you would have created a user account during install. You use that username and password.

---

### Post by Kvark on 2005-11-02
You open a terminal and put "sudo" in front of any command you need root access for.

For example if you want to edit the sources.list file with gedit you'll have to add sudo in front of the command like this: "sudo gedit /etc/apt/sources.list".

If you have a lot of stuff to do that requires root access then you can type "sudo su". After that you will have root access for everything you do in that terminal and don't need to put "sudo" in front of every command.


Sudo is safer then to log in as root because now you have root access only for the commands you need it for. If you would go through the hassle of logging out from your normal user account and re-login as root then you would have root access for everything, which is why you can't log in as root.

---

