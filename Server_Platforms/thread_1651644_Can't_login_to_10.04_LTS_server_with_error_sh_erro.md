---
title: "Can't login to 10.04 LTS server with error sh: error while loading shared libraries"
date: 2010-12-23
forum: Server Platforms
---

### Post by swankster on 2010-12-23
Hello, 

I recently setup a new server that serves files over samba and is a subversion repository for a number of projects. I did a simple apt-get update/upgrade for which the system requested a reboot. After I rebooted, I got to the login prompt, at which point I ran into a problem. After I enter my correct credentials, it spits out the following error:

sh: error while loading shared libraries libc.so.6: cannot open shared object file: Error 24

and returns me to the login prompt. Samba and Subversion are both still working, I simply can't login to the server either physically or via SSH.

What steps should I be taking to correct this issue? My thoughts are that I may need to use a Live CD to load the system and perhaps do another update, but before I go through that process I just wanted to check in and see if there might be some other solution.

I have tried googling the issue, and while I have seen other posts regarding shared library issues, there was never anything about not being able to login and I never did find anything specific to the error message I received.

Any help you can provide would be greatly appreciated.

---

### Post by kroon78 on 2010-12-23
did you ever setup the root account?

---

### Post by swankster on 2010-12-27
No, the root account hasn't been setup. There is only one user account "administrator" that was created during installation.

---

### Post by cariboo on 2010-12-27
You may have to hook up a monitor and keyboard and start in recovery mode, select netroot from the menu, then type:

```
apt-get -f install
```

you can also do updates at the same time.

---

### Post by swankster on 2010-12-27
> **cariboo907 said:**
> You may have to hook up a monitor and keyboard and start in recovery mode, select netroot from the menu, then type:

```
apt-get -f install
```

you can also do updates at the same time.

Hi cariboo,

I was successfully able to login via recovery mode netroot; however, when I ran apt-get -f install libc6 it simply told me it was at the newest version. I also tried doing an update/upgrade while I was at a working console but it hasn't corrected the issue. I'm still getting the same error message.

---

### Post by swankster on 2010-12-28
I've tried a few more things to get this working, including forcing a reinstall of libc6, running dpgk from the recovery console, and updating all my packages. 

I did give root a password while logged into the recovery console, and it can't log in normally either.

I'm really at a loss here, I've spent a good amount of time googling but I haven't had any more luck finding a similar problem to mine, or any advice that has solved the problem.

Are there any other suggestions for what I could do?

---

