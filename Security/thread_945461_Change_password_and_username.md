---
title: "Change password and username"
date: 2008-10-12
forum: Security
---

### Post by Flame_Phoenix on 2008-10-12
Hi guys, a friend of mine installed Ubuntu on my computer and he with a username and a password. However now I want to change them so I am the only one who knows those data. Can some one help me out?

---

### Post by Oracle_The_Blind on 2008-10-12
Open the terminal (Application -> Accessories -> Terminal)

Type ```
passwd
```

Press **enter**.
Type your **current password**
Press **enter**
Type your desired **new password**.
Press **enter**.
Re-enter your desired **new password**.
Press **enter**.
Type ```
exit
```

Your password has now been changed.

---

### Post by Flame_Phoenix on 2008-10-12
yeee =) Thx for help. I know how to use the terminal, I just don't know the commands I have to use. 
However:
1 - Is there a way to change the username ?
2 - Is there a way to give a bonus to people who help us in this forum ?? (I am newbie xD)

---

### Post by cariboo on 2008-10-12
You can use adduser. boot up in recovery mode, at the menu select drop to root prompt. At the prompt type:

```
useradd -m <username>
```

then

```
passwd <username>
```

The first command will create a new user and a home directory for that user. THe second commad creates a password of the new user. After you have done the above, log in as the origional  user and go to System-->Administration-->Users and Groups, unlock the application using the origional password highlight the new user and click porperties-->User Privileges. Give the new user all the privileges you think he will need, make sure you give the new user Administer The System privileges, then click close. You can now log out and log in as your new user.

You may want to copy any files or folders you created in the origional users home directory to the new users home directory. Once you transfered what you need go back to Users and Groups and delete the origional user.

Jim

---

### Post by aysiu on 2008-10-12
You can also reset the password of the current user:
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

That might make it easier to add a new user through System > Administration > Users and Groups

---

### Post by Flame_Phoenix on 2008-10-13
But if I create a new user, I will lose everything I currently have on this user, and I will have 2 users right ?
Than I will have permission problems as well =S

Maybe I will just stick to changing password.Thx for help.
Is there a way to give "coffee seeds" to people to thank their help ?

---

