---
title: "can not connect to terminal through SSH"
date: 2009-04-30
forum: Server Platforms
---

### Post by fabianus on 2009-04-30
Hello all !

I installed a server 8.10 and did a mistake during the installtion : I selected the wrong keyboard and thus typed a wrong password : 

dsdföd

(see the letter ö !)

Once the box was up I changed the keyboard version through the graphical interface and the password, too (System/Administration/Users Groups).

But the password doesn't change ! It remains with this ö caracter and when I try to access get access to terminal through ssh(with putty from windows) I do not get access. 

I tried to set the password in terminal by typing passw but this doesn't help, too. 

Do you know where I might set the password ?

Thanks a lot for any help !

Regards, Fabianus

---

### Post by spiderbatdad on 2009-04-30
for password login to ssh, you login using the user acount password. You need access to the machine to change the password. ```
sudo passwd username
```sudo will require the admin password...that of the user account you are logged into. Then you will be asked to create a password for the user account you are editing.
More on ssh here:

[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

[https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)

---

### Post by fabianus on 2009-04-30
Hello spiderbatdad, 

thanks a lot for this feedback ! This is exactly what I needed !

Regards, 
Fabianus

---

