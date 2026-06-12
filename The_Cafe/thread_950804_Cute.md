---
title: "Cute"
date: 2008-10-17
forum: The Cafe
---

### Post by iponeverything on 2008-10-17
Don't get me wrong, I think it's very sweet. I have had a root window open on my desktop for the past 15 years, and just now.. 

The thought that the os that perfected the 2 and 3 letter command would even suggest that I would add another 4 letters to every command.

Blasphemy, but sweet nonetheless.

fubar@foo-laptop:~$ xx -
Password: 
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

root@foo-laptop:~#

---

### Post by BackwardsDown on 2008-10-17
It's because the root has a random generated password in Ubuntu. In a default install, the user does not know the root-password. But with it's own password, he can execute commands as root.

---

### Post by cardinals_fan on 2008-10-17
> **BackwardsDown said:**
> It's because the root has a random generated password in Ubuntu. In a default install, the user does not know the root-password. But with it's own password, he can execute commands as root.
I've never understood the reasoning behind this, but whatever.

---

### Post by kaivalagi on 2008-10-17
If you want to set the root password to a known one, do this:

```
sudo passwd root
```

and enter your desired root password twice...

Now you can use "su" to stay as root etc

Hope that helps

---

### Post by iponeverything on 2008-10-17
> **BackwardsDown said:**
> It's because the root has a random generated password in Ubuntu. In a default install, the user does not know the root-password. But with it's own password, he can execute commands as root.

The default is that root accounted is locked out. In shadow for the passwd field you will see :*: Well, considering that there is no salt, it can't be be decrypted.

---

### Post by angryfirelord on 2008-10-17
> **cardinals_fan said:**
> I've never understood the reasoning behind this, but whatever.
I think it's because if a hacker compromises a user's account, the next time the user initiates the su command, the hacker is able to gain access to root privileges as well. Using sudo, there is a timeout in place so that it encourages users to not run as root all the time. In addition, sudo can be fine tuned to give users certain permission to run certain commands, whereas using su is basically and all-or-nothing approach. Also, most hackers will try to target the root account first. With Ubuntu, the root account has a scrambled password that is many characters long. In this sense, you are safer because the password is almost impossible to crack.

Of course, I don't think it makes an ounce of difference either. ;)

---

### Post by lswb on 2008-10-17
If you need run a lot of commands as root you can use sudo -i or sudo -l to get a root command prompt. Don't forget to exit when you're done!

---

