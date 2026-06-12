---
title: "Removing Sudo"
date: 2011-07-10
forum: Security
---

### Post by enicchi on 2011-07-10
Hi,  

I'm sorry to start my first post in this forum with a support question already.     

I've installed Ubuntu via UNetbootin from USB on my child's computer. It comes by default with the sudo command which I find really annoying to work with. I'd rather have my su command.    

Now, while googling for a removal instruction, I've read that the sudo command is tied to system functions on some Ubuntu live systems and can't be removed easily. Does anyone know if this applies to the 10.04 live version used by UNetbootin and how to work around this problem?    

If not, is it simply enough to remove 'sudo' via the software center? I find many tutorials on how to switch from su to sudo but not much about the other way around.    

Thank you very much in advance for any help.    
~eni

---

### Post by ajgreeny on 2011-07-10
You can not remove sudo from ubuntu as it will stop you doing anything that needs root permissions.  See Root-sudo in my signature for all the details.

It is possible to remove the need for a password from some or all applications/utilities that need root permissions, but it is a very bad idea, will remove one of the main security advantages of linux and ubuntu, and therefore I will not give you details of how to do it.  I think this thread will be removed if I do tell you as I believe it's against the forum rules.

Just to check, what exactly is the problem with sudo that you have?  Also did you know that you can get a persistent terminal with root permissions enabled with the command ```
sudo -i
```rather like the su command of other distros where the root account is not disabled as it is in ubuntu.

---

### Post by Mr. Shannon on 2011-07-10
The command below will give you a persistent terminal as well.  The only difference I know of is that it does not change the current directory to the root users home directory.

```
sudo su
```

---

### Post by Rubi1200 on 2011-07-10
The correct command to gain privileges with a root shell has already been mentioned by ajgreeny.

See here for more details about why:
[http://ubuntuforums.org/showpost.php?p=6188826&postcount=4](http://ubuntuforums.org/showpost.php?p=6188826&postcount=4)

---

### Post by cariboo on 2011-07-11
> **Mr. Shannon said:**
> The command below will give you a persistent terminal as well.  The only difference I know of is that it does not change the current directory to the root users home directory.

```
sudo su
```

<offtopic>

Mr. Shannon, your signature is just plain wrong, Unity works on top of gnome, so saying you use a gnome-desktop means nothing. You may be better off saying you use Gnome 2.X or Gnome 3, either the shell or fallback mode.

</offtopic>

---

### Post by enicchi on 2011-07-11
Hallo,

I'm sorry, maybe it wasn't well explained. I don't want by any means remove any need for passwords, I just want to use su instead of sudo since I prefer the handling and the clear separation of root and user. The computer belongs to my child and he's the only user on it, I only need root access for administration via my admin account.

If I understood the Ubuntu Wiki correct than sudo can be removed after enabling the root account but it's not recommended. It can cause problems with applications but I wonder why. If I administrate pretty much completely via the command line than what problematic conflicts can there be? :(

~eni

---

### Post by karlson on 2011-07-11
> **enicchi said:**
> Hallo,

I'm sorry, maybe it wasn't well explained. I don't want by any means remove any need for passwords, I just want to use su instead of sudo since I prefer the handling and the clear separation of root and user. The computer belongs to my child and he's the only user on it, I only need root access for administration via my admin account.

If I understood the Ubuntu Wiki correct than sudo can be removed after enabling the root account but it's not recommended. It can cause problems with applications but I wonder why. If I administrate pretty much completely via the command line than what problematic conflicts can there be? :(

~eni

I don't think there is a problem administrating via a command line using SU vs. SUDO.  If you want to use su you are entirely welcome to it just set the root password.  You don't need to remove sudo to do this.

But if all you want is for your child not to have access remove him from an admin group.

---

### Post by bodhi.zazen on 2011-07-11
You do not need to remove sudo, simply do not use it.

See man sudo, man sudoers, and the following page:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

We do not support this activity here, just point you to the resources, so with that I am going to close this thread now.

---

