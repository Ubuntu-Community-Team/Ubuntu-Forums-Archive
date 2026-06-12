---
title: "sysadmin newbie: wrong su password"
date: 2011-03-09
forum: Security
---

### Post by daveli on 2011-03-09
Hi, 

I am starting to learn how to create and manage users in my computer. I created a new user and changed users 

$ su john

I then tried to install a package with this user to confirm that it needs su rights, and when asked for the password, I entered it wrong

$ su apt-get install bastille
[sudo] password for john: 
john is not in the sudoers file.  This incident will be reported.


It says that the incident will be reported, but where can I find the information of this incident? where is it stored or how is it reported?

Thanks,

Dave

---

### Post by aneeshnair on 2011-03-09
the information will normally gets mailed to root user. you may find it in /var/mail directory.  root privilages are needed.

Alternatively, you may add the user to sudoers file in /etc/sudoers file.  To edit the sudoers file you should use the visudo command.  You may 'google' for further details.  There are plenty of information available about sudoers file and its editing.. Hope this helps !!

---

### Post by cariboo on 2011-03-09
By default, sudo doesn't actually send a message, you can enable mail using the instructions [here]("http://www.cyberciti.biz/faq/sudo-send-e-mail-sudo-log-file/").

---

### Post by skraps on 2011-03-09
opps nvm

---

