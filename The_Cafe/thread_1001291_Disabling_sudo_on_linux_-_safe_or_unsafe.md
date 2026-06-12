---
title: "Disabling sudo on linux - safe or unsafe?"
date: 2008-12-03
forum: The Cafe
---

### Post by Grant A. on 2008-12-03
What do you think, safe or unsafe? I myself prefer su as it doesn't stick around for 15 minutes.

EDIT- Can a mod please change this to disabling sudo on Linux?

---

### Post by bruce89 on 2008-12-03
I can't be bothered having to remember another password. Also, I'm sure security-wise, both methods are much the same (prove me wrong).

---

### Post by Grant A. on 2008-12-03
> **bruce89 said:**
> both methods are much the same (prove me wrong).

Su dies after you kill the program/terminal session using it. Sudo on some distributions dies after 15 minutes.

---

### Post by Rokurosv on 2008-12-03
I say give an option during the install, like Mint does for creating a superuser account with its own password. It's one of the things I don't like about Ubuntu, that the super user password is the same as the normal user, I don't know much about cracking passwords and all of that but I imagine is easier to get a normal user's password than a superuser's.

---

### Post by Joeb454 on 2008-12-03
Title changed as requested :)

> **Grant A. said:**
> Su dies after you kill the program/terminal session using it. Sudo on some distributions dies after 15 minutes.

While this is true, you can change the timeout...personally I find it useful, and if I'm working via ssh I always run ```
sudo -k
``` after finishing any sudo work.

Either that or if it's for prolonged periods I just switch to root anyway to save a little hassle.

Personally I do think sudo is a good idea :)

---

### Post by Grant A. on 2008-12-03
> **Rokurosv said:**
> that the super user password is the same as the normal user, I don't know much about cracking passwords and all of that but I imagine is easier to get a normal user's password than a superuser's.

On Ubuntu the root password is randomized during install; however, due to the set up of the OS, you are quite correct, a normal user in some cases is a superuser.

Thank you for the title change Joeb! :D

---

### Post by damis648 on 2008-12-03
> **Rokurosv said:**
> I say give an option during the install, like Mint does for creating a superuser account with its own password. It's one of the things I don't like about Ubuntu, that the super user password is the same as the normal user, I don't know much about cracking passwords and all of that but I imagine is easier to get a normal user's password than a superuser's.

Sorry, that's wrong. The root (superuser) password is randomly generated upon installation. The user's password is the only account that uses the password you used during the installation.

---

### Post by Rokurosv on 2008-12-03
> **damis648 said:**
> Sorry, that's wrong. The root (superuser) password is randomly generated upon installation. The user's password is the only account that uses the password you used during the installation.

Ohh I didn't know that :o. Then how does sudo work exactly? Cause when you want to do something that involves super user rights and you type sudo the password you introduce is the normal user password, if I'm not mistaken.

---

### Post by Grant A. on 2008-12-03
> **Rokurosv said:**
> Ohh I didn't know that :o. Then how does sudo work exactly? Cause when you want to do something that involves super user rights and you type sudo the password you introduce is the normal user password, if I'm not mistaken.

You type in your user password it gives you the administrative rights for 15 minutes in some distros, such as Ubuntu, by default.

---

### Post by damis648 on 2008-12-03
> **Rokurosv said:**
> Ohh I didn't know that :o. Then how does sudo work exactly? Cause when you want to do something that involves super user rights and you type sudo the password you introduce is the normal user password, if I'm not mistaken.

Though I am not exactly sure technically how it works, it takes the normal user user password and authentication enough to run a superuser command. T modify settings, you can run 'sudo visudo'.

---

### Post by cardinals_fan on 2008-12-03
I don't like sudo, and the timeout is madness.  Just su to root, handle what needs to be handled, and exit.

*I realize that sudo may be useful in settings where carefully refined permissions policies are necessary, but this probably doesn't apply to most people here*

---

