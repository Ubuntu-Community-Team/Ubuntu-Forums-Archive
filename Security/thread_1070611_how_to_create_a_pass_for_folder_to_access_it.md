---
title: "how to create a pass for folder to access it ?"
date: 2009-02-15
forum: Security
---

### Post by hondacodonbk on 2009-02-15
may I ask some question ?
I`am a newbie for ubuntu,I`ve just install install ubuntu a few day,and now I want to ask : how do you do if you want to lock a folder which you only open it until you press right password which protect this folder ? It mean how to create a folder which have password,and you can`t open it until you press pass
Thank very much !

---

### Post by tubbygweilo on 2009-02-15
hondacodonbk, 
you can right click on the folder and select the encrypt option and although not a password it should keep the folder safe from others until the correct password is given. When using this method if you loose your password you can not recover the data.

You could also change the file access permissions so as to keep others from reading it in the first place by right click on the folder and selecting the Permissions tab.

Each method has it's pros and cons and I sure others may offer yet more ways to keep your folders safe from others.

---

### Post by cosine352 on 2009-02-15
you can do a folder woned by root and change the permission to that file so that only root can see and change it. 

> sudo mkdir Desktop/protected
sudo chmod 700 Desktop/protected

to open the folder

> sudo gnome-open Desktop/protected

---

### Post by bodhi.zazen on 2009-02-15
> **hondacodonbk said:**
> may I ask some question ?
I`am a newbie for ubuntu,I`ve just install install ubuntu a few day,and now I want to ask : how do you do if you want to lock a folder which you only open it until you press right password which protect this folder ? It mean how to create a folder which have password,and you can`t open it until you press pass
Thank very much !

Linux is not windows and so it does not have this feature directly.

In Linux each user should have a separate user name and log in. You then use permissions to restrict access to files or directories.

To make your home "private" use :

```
chmod 770 $HOME
```

See : [http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

=======

If you wish to password protect data or directories use encryption. You have several options for encryption and Ubuntu 9.04 will give you the option of encrypting your home directory if you wish.

---

### Post by hondacodonbk on 2009-02-15
uh,I know these commands,but they only make folder can be read,write or ex.And other peoper can see this folder,it mean they know that this folder is exist.How can I hide this or lock folder in order to other people can`t open them ??? 
Or,is there any software which can hide folder liki hidefolder in Window ???
thank for help me

---

### Post by cosine352 on 2009-02-15
you can do a folder woned by root and change the permission to that file so that only root can see and change it.

> sudo mkdir Desktop/protected
sudo chmod 700 Desktop/protected
to open the folder


> sudo gnome-open Desktop/protected 

to hide a folder rename it with a period at the beginig (protected ---> .protected)

---

### Post by hondacodonbk on 2009-02-15
uh,I search in internet and know that if I create a folder with "." and Ctrl + H,then folder will disappear,I did and this folder is disappear.When I Ctrl+H again,it is appear,but the other folder of system which have "." alse appear
It is seem compele,isn`t it ? Because,if I make my folder appear,then I forget disappeat it,next session I  log on Ubuntu I delete these folder of system,what happen to me ?????
sory for stupid question ^_^

---

### Post by bodhi.zazen on 2009-02-15
what is the question ?

Basic permissions are certainly sufficient to protect a file or directory, unless you are sharing an account or needing to restrict even the root user.

Let me make a directory "test" containing a file "secret_file" and change ownership to the user nobody and the group mail.

mkdir test
echo "For your eyes only" > test/secret_file
sudo chown -R nobody.mail test
sudo chmod -R 770 test

Now, since my curent user is not nobody, and I am not in the group mail, let us look at the file :

> [color=red]user@desktop:~$ ls test
ls: cannot open directory test: Permission denied

user@desktop:~$ cd test
cd: permission denied: test

user@desktop:~$ cat test/secret_file
cat: test/secret_file: Permission denied[/color]

Seems basic Linux permissions are completely effective in limiting access to the contents of the directory.

Let us look as root :

> user@desktop:~$ sudo ls test
secret_file

user@desktop:~$ sudo cat test/secret_file
For your eyes only

As this demonstrates, permissions alone can not restrict root. To restrict root you need selinux, apparmor, or encryption.

For encryption you can use gpg, truecrypt, encfs, LUKS ...

[http://www.cyberciti.biz/tips/linux-how-to-encrypt-and-decrypt-files-with-a-password.html](http://www.cyberciti.biz/tips/linux-how-to-encrypt-and-decrypt-files-with-a-password.html)

[https://wiki.kubuntu.org/EncryptedHomeFolder](https://wiki.kubuntu.org/EncryptedHomeFolder)

---

### Post by hondacodonbk on 2009-02-19
thank you for your help ^_^

---

