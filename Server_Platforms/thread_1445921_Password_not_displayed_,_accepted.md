---
title: "Password not displayed , accepted"
date: 2010-04-03
forum: Server Platforms
---

### Post by Focused100 on 2010-04-03
[SIZE=4]Hello[/SIZE],
[SIZE=4]I'm a Linux newbie
I installed Ubuntu server 9.10 with the mail server option without any problems. However when I tried to login the username was accepted and displayed but the password could not be entered. No matter what I did the password space remained blank and I could not login. Any help would be appreciated.  Thank you[/SIZE]

---

### Post by new_tolinux on 2010-04-03
In terminal or text-login it's default that Ubuntu doesn't display the password.

You should just type it, and press return after that. Normally that would be the way to login.

---

### Post by ajgreeny on 2010-04-03
If you typed it wrong, it would quickly tell you; try it out on purpose to see what I mean, so the system does see what you type, it's just that you can't see it.

---

### Post by Focused100 on 2010-04-03
[SIZE=4]Thank you both for your quick replies.
Unfortunately, your suggestion did not work.

The password cursor doesn't even move from the prompt when I type it and I'm still not able to login.

I tried reinstalling without a password but it would not let me.
 Any other suggestions?[/SIZE]

---

### Post by koenn on 2010-04-03
you have to hit the Enter key after you type the password

---

### Post by KB1JWQ on 2010-04-03
You using a GUI, or is this strictly at login in the CLI?

---

### Post by Focused100 on 2010-04-03
[SIZE=4]Text Login for the 1st time.[/SIZE]

---

### Post by KB1JWQ on 2010-04-04
Be sure you're not trying to log in as root.

---

### Post by Focused100 on 2010-04-07
[SIZE=4]Is there a way to login without user and pass?[/SIZE]

---

### Post by sisco311 on 2010-04-07
As new_tolinux already pointed it out, your password is being accepted in the terminal. You just aren't getting any visual feedback. Go ahead and type your password and hit Enter afterwards. If you typed your password correctly, there should be no problems.

[http://psychocats.net/ubuntu/passwordinterminal](http://psychocats.net/ubuntu/passwordinterminal)

If your password is still not accepted, then boot into the *recovery mode* & reset it.

[http://psychocats.net/ubuntu/resetpassword](http://psychocats.net/ubuntu/resetpassword)

---

### Post by Focused100 on 2010-04-07
[SIZE=4]Thanks for your help
I am now able to login. However, there is no GUI. I'm presented with a command prompt that looks like this:

focused100@ubuntu:~$

Any idea to get to the desktop? Thanks.[/SIZE]

---

### Post by mobilediesel on 2010-04-07
> **Focused100 said:**
> [SIZE=4]Thanks for your help
I am now able to login. However, there is no GUI. I'm presented with a command prompt that looks like this:

focused100@ubuntu:~$

Any idea to get to the desktop? Thanks.[/SIZE]

If you installed the server edition of Ubuntu there is no GUI installed by default. If you wanted a GUI installed by default you should have installed desktop edition. You can install a GUI onto the server edition.
For Gnome:
```
sudo apt-get install ubuntu-desktop
```
or KDE:
```
sudo apt-get install kubuntu-desktop
```
or for XFCE:
```
sudo apt-get install xubuntu-desktop
```

You can install any one of those or even all of them for a GUI.

---

### Post by new_tolinux on 2010-04-07
*deleted*

---

### Post by KB1JWQ on 2010-04-07
arguably ubuntu-desktop is the preferred meta-package. :-)

---

### Post by Focused100 on 2010-04-07
[SIZE=4]Forgive  me.  I thought almost everything had a GUI these days. So one of these GUI's can be installed on top of the 9.10 server I already have?
Will I still be able to run a mail server after the GUI is installed?
[/SIZE]

---

### Post by new_tolinux on 2010-04-07
Why not?

You're just installing another package, as long as that doesn't conflict with existing packages that's just fine (and up to you).
They shouldn't produce any problems when running together.

---

### Post by lisati on 2010-04-07
> **Focused100 said:**
> [SIZE=4]Forgive  me.  I thought almost everything had a GUI these days. So one of these GUI's can be installed on top of the 9.10 server I already have?
Will I still be able to run a mail server after the GUI is installed?
[/SIZE]

Yes. I installed the server edition of 9.04 some months back, then added an email server and a minimal gui. My website and email server have low volume traffic. So far I haven't had any problems that weren't of my own making (having a typo in the settings and stuff like that)

---

