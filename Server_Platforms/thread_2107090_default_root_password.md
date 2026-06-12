---
title: "default root password"
date: 2013-01-21
forum: Server Platforms
---

### Post by guesss on 2013-01-21
Hey Ubuntu fans,
 I just installed the Server 12.04.1 LTS on my Virtualbox and after the server being installed, I am prompted with the login screen on the terminal. I've been looking around the forum for a solution, but only come across individuals who are soo trigger happy with the "sudo" command. I've found one person saying there IS NO root password. I'm not sure understand how that's possible. So people have suggested re-installation, and that I should have created a user&password sometime earlier in the install. 

So I've done so research, and was reading some of the installation documentation for Ubuntu, but still can't figure out this issue. 
Thanks for reading. :popcorn:

---

### Post by sidzen on 2013-01-21
Die-hard ubuntuites don't like it, but with the following command, one makes a root passwd
[PHP]sudo passwd root[/PHP]
since you asked.

---

### Post by guesss on 2013-01-21
> **sidzen said:**
> Die-hard ubuntuites don't like it, but with the following command, one makes a root passwd
[PHP]sudo passwd root[/PHP]

I understand this command. I'm familiar with it. But I'm pretty sure I can't enter that command in, at a login screen. Almost positive you must be already logged into as another user.

---

### Post by deadflowr on 2013-01-21
> **guesss said:**
> Hey Ubuntu fans,
 I just installed the Server 12.04.1 LTS on my Virtualbox and after the server being installed, I am prompted with the login screen on the terminal. I've been looking around the forum for a solution, but only come across individuals who are soo trigger happy with the "sudo" command. I've found one person saying there IS NO root password. I'm not sure understand how that's possible. So people have suggested re-installation, and that I should have created a user&password sometime earlier in the install. 

So I've done so research, and was reading some of the installation documentation for Ubuntu, but still can't figure out this issue. 
Thanks for reading. :popcorn:

That is correct. By default Ubuntu has no root password, as it is not needed, sudo handles root privileges just fine.

Look at this for more help and understanding on the issue of Ubuntu and root passwords:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Also, I really have no idea how anyone could install any Ubuntu system without an initial user, though I guess it's possible.

---

### Post by Cheesemill on 2013-01-21
You are prompted to set up your username and password during the installation. You can't continue with the installation without doing so.

---

### Post by spynappels on 2013-01-21
I'm not sure I understand where you're coming from. You will have created a user and password during the install as said by others, these are what you use to log in initially.

I'm confused by your use of the term "trigger happy with the sudo command", surely running as root is equivalent to being super trigger happy with the command as you are effectively running every command as sudo?

There are times when running as root is fine for a careful admin, but by default in Ubuntu sudo is used as per the link DeadFlower posted.

---

