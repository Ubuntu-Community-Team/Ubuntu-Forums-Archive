---
title: "New installation from a new user"
date: 2008-03-28
forum: Server Platforms
---

### Post by dagd on 2008-03-28
I'm new to linux I installed v6.06.2 server to my AMD 64 I chose install to my hard drive, installed Ok, during the installation i was ask to create a user which I did, but i did not setup the root password, that is the first.
Second after installation I reboot the system and login with the user account i created but I could see the desktop only a prompt, is that normal? do I need to do anything to have a GUI interface? can any anyone help me.
Thank you very much for your time.
DAGD

---

### Post by girasquid on 2008-03-28
Server installs usually don't come with a GUI at all - you don't really need one if all you're going to be running is a headless server(which is what most are, I'm told).

As to your first question, I do not quite understand. What is the problem? Do you want to set your root password?

---

### Post by dagd on 2008-03-28
yes I want to setup a root password

---

### Post by ryazkhan on 2008-03-28
Server edition does not come with GUI. If you want GUI you need Desktop Edition.
You dont need to login as root user. You can use regular user to login and then do this to be root
> sudo bash or sudo -i
To create password linux/unix password
> sudo passwd username
For samba password
> sudo smbpasswd -a username
Note: You need to add sudo only if you are not working as root user!

---

### Post by ryazkhan on 2008-03-28
change/set unix password for ryazkhan
> sudo passwd ryazkhan
change/set samba password for ryazkhan
> sudo smbpasswd -a ryazkhan

---

### Post by ruibernardo on 2008-03-28
You should not create a password for root unless you know what you're doing, even if you're a linux user new to Ubuntu and don't really understands sudo.

From this thread: [New forum policy on log-in-as-root tutorials]("http://ubuntuforums.org/showthread.php?t=716201")

>  We believe in and offer technical support for Ubuntu's default security model, which uses *sudo* for temporary privilege escalation on particular tasks for particular users with a password authentication. Generally speaking, those who desire a graphical root login fall into one of three categories:[LIST]
[*]**Users new to Linux** who receive an error message telling them they need to be root in order to execute a certain command or who are trying to follow a tutorial for a non-Ubuntu Linux distribution in which they are instructed to log in as root.
[*]**Users new to Ubuntu who have experience with other *nix systems** in which they are used to logging in as root.
[*]***nix experts who have very specialized tasks that can be accomplished only through a root login**.[/LIST]_The first group (users new to Linux) simply needs to be educated about how Ubuntu works_, since all they want to do is accomplish a certain task they *believe* requires a root login. Once they realize the task can be accomplished more simply with Ubuntu's *sudo*, they should have no reason to still want a root login.

The second group (Linux vets new to Ubuntu) may theoretically know about *sudo* but is acculturated to logging in as root. Many of our forum staff and forum members started out this way as well and disliked *sudo* at first. However, once we got used to *sudo*, we liked it better than the traditional root/user model, and realized there were both security and usability benefits to Ubuntu's security model. In other words, give Ubuntu a fair chance.

The third group (experts who know of special situations that require a root login) definitely does not need a root login tutorial. If they're really experts, they can easily figure out on their own how to enable a root login. And if they can't figure it out, perhaps they're not the experts they think they are.

To sum it up, if you can't figure out how to log in as root in Ubuntu, then you should be educated on how to use Ubuntu's *sudo* security model properly; and if you can figure out how to log in as root in Ubuntu and want to, then you certainly don't need a tutorial on how to do it.

Variations on the second and third groups are those who falsely believe *sudo* security model to be less secure than the traditional root/user model. You can find out more about Ubuntu's reasons for using *sudo* and the pros and cons of both security models here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
So please read _**[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)**_ and reconsider about not using the sudo command in a system where sudo is _the_ security feature.

The simplest way to get a «root» prompt is

```
$ sudo -i
#

```

---

### Post by ryazkhan on 2008-03-28
I agree with you and matter of facts I never use root account when I can do all things with unix user by typing sudo in fornt of each command which popup for password again to make sure you are the right user which is good secuirty feature.

---

### Post by 7aji88 on 2008-03-28
I'm still trying to get my first server to work too, and I don't have that much knowledge in command line so I installed a GUI with this command:
  [COLOR="DarkRed"][SIZE="2"] sudo apt-get install ubuntu-desktop   [/SIZE][/COLOR]
I guess it makes it easier for beginners. and you can change the word "ubuntu" in the command to "kubuntu" or "xubuntu" . Some people were saying that it's better for a server to install xubuntu since the Xfce environment is lighter than gnome.

---

### Post by Belnoctourne on 2008-03-29
a great bet for making server maintenance easy from my experience is webmin, doesn't bog your server down with a resource intensive ui like kde/gnome and at least for me its made things a lot easier, if you do want a gui I would advise something lightweight

---

