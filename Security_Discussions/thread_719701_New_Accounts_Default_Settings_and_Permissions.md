---
title: "New Accounts Default Settings and Permissions"
date: 2008-03-09
forum: Security Discussions
---

### Post by thatsnicethat on 2008-03-09
Hi everyone,

Well I hope this is the right place to ask the question.. I'm trying to deepen my knowledge of Ubuntu, especially Terminal, and so I would like to create new accounts/users, with a default setting, which would include some directories which would have a certain permissions. So when I create a new user, this new account would have by default a couple of directories, with a set of permissions which would always be the same. Is there a command/set of commands to do this?

Thank you in advance for any responses.

Cheers

---

### Post by lloyd_b on 2008-03-09
> **thatsnicethat said:**
> Hi everyone,

Well I hope this is the right place to ask the question.. I'm trying to deepen my knowledge of Ubuntu, especially Terminal, and so I would like to create new accounts/users, with a default setting, which would include some directories which would have a certain permissions. So when I create a new user, this new account would have by default a couple of directories, with a set of permissions which would always be the same. Is there a command/set of commands to do this?

Thank you in advance for any responses.

Cheers

Here's a list of commands for you: "useradd" "groupadd" "mkdir" "chmod", and "chown".  Between them, they should be able to do everything you need.  For more information on them, "man {command}" in a terminal window.

What you'll probably wind up doing is creating a "shell script", which is basically a series of commands (with some extras - shell scripting is basically a type of programming).

If you're serious about *nix administration, you'll want to learn shell scripting anyway (it's EXTREMELY useful).  For examples of shell scripts, either search the forums, or use google.

Lloyd B.

---

### Post by thatsnicethat on 2008-03-09
> **lloyd_b said:**
> Here's a list of commands for you: "useradd" "groupadd" "mkdir" "chmod", and "chown".  Between them, they should be able to do everything you need.  For more information on them, "man {command}" in a terminal window.

What you'll probably wind up doing is creating a "shell script", which is basically a series of commands (with some extras - shell scripting is basically a type of programming).

If you're serious about *nix administration, you'll want to learn shell scripting anyway (it's EXTREMELY useful).  For examples of shell scripts, either search the forums, or use google.

Lloyd B.

Very useful stuff, thanks lloyd b, I think I'll get going learning some shell scripting

cheers

---

### Post by ung/xunil on 2008-03-09
> **thatsnicethat said:**
> I would like to create new accounts/users, with a default setting, which would include some directories which would have a certain permissions. So when I create a new user, this new account would have by default a couple of directories, with a set of permissions which would always be the same.
The best and easy way to make this is to change the content of the directory /etc/skel/. Inside that directory you can find the "template" of a home directory of a new user. When you use the command "adduser", it will copy all the content of that directory to /home/ and change the uid of the files.

So, if you add a directory a new directory inside /etc/skel/, when you execute "adduser", that new directory will exist in the new /home/$USER direcory. The same happens to the files inside /etc/skel/. If you change the file /etc/skel/.bashrc, that change will exist in the new user ~/.bashrc or ~/.profile in his new $HOME.

I think the same happens with permissions of the files/directories.

Another thing: if you don't want users to look inside the other users $HOME, run "sudo dpkg-reconfigure adduser -plow" and answer "No". You will have to change permissions to /home/ directories:
```
sudo chmod -R og-r /home/$USER
```
And change the umask of the users. It can be done adding/changing a umask commad in /etc/profile (system wide) or in the file /home/$USER/.profile. A link about umask: [http://ubuntudemon.wordpress.com/2007/10/24/default-umask/]("http://ubuntudemon.wordpress.com/2007/10/24/default-umask/")

---

