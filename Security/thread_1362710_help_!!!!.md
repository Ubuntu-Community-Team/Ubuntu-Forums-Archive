---
title: "help !!!!"
date: 2009-12-23
forum: Security
---

### Post by havoc9985 on 2009-12-23
i have just purchased a pc with kubuntu and didn't receive the password or user name is there a way a can get around theshack

---

### Post by HeadHunter00 on 2009-12-23
Sorry, but you need to reinstall kubuntu. Where did you get it anyway?

---

### Post by havoc9985 on 2009-12-23
i was stupid i got it on craigs list and it worked just find  so how can i uninstall it without getting in to the computer ??

---

### Post by HermanAB on 2009-12-23
Simple.  Boot into single user mode and set the password with the 'passwd' command.

---

### Post by cdenley on 2009-12-23
Boot into "recovery mode", open a root shell, get the user with:
```

getent passwd 1000|cut -d : -f 1

```

So once you get the username, let's say it is 'myuser', set the password with
```

passwd myuser

```

---

### Post by HeadHunter00 on 2009-12-23
> **havoc9985 said:**
> i was stupid i got it on craigs list and it worked just find  so how can i uninstall it without getting in to the computer ??
I am a little confused. What do you mean?

---

### Post by havoc9985 on 2009-12-23
how do i get to the recovery menu ?

---

### Post by wsonar on 2009-12-23
Since it's not your laptop data just download a new ISO and do a fresh install.

It's your computer now the first step in personalization should be sanitation

Do a clean install

---

### Post by havoc9985 on 2009-12-24
i need step by step how to reset this password guys?

---

### Post by cariboo on 2009-12-24
IF you know your user name. start in recovery mode by pressing esc when you see the word grub on the screen, this will bring up the grub menu. Use the arrow keys to navigate to recovery mode, then press enter. Once at the menu use the arrow keys to navigate to drop to root prompt, then press enter. Once you are at the root prompt type:

```
passwd <username>
```

and press enter. Remember <username> = your user name. Enter your password, it will not be echoed back to you then press enter, you will be asked to enter your password a second time, it will not be echoed back to you again, and press enter. Once you have entered your new password, type:

```
exit
```

Then navigate using the arrow keys to resume and press enter. You should now be able to sign on at the desktop.

---

### Post by Axel777 on 2009-12-24
> **cariboo907 said:**
> IF you know your user name. start in recovery mode by pressing esc when you see the word grub on the screen, this will bring up the grub menu. Use the arrow keys to navigate to recovery mode, then press enter. Once at the menu use the arrow keys to navigate to drop to root prompt, then press enter. Once you are at the root prompt type:

I dont think he knows the username. 

See if you can contact the previous owner to get the details. Else i agree that it is best that you do a clean install. Hope you come right. cheers

---

### Post by BkkBonanza on 2009-12-24
As cdenley above stated it's easy to find out the user name. Just follow his steps after getting into the recovery console. You ARE better off installing fresh with your own software but if you want to be snoopy then go ahead. Just know that if you decide to use the system as is then you have no idea what trojans or malware may already be present or where it could send any of your info.

---

### Post by tubbygweilo on 2009-12-24
As stated above it is far, far safer to level the machine and start a new with a clean install of your own. 

Nuking a machine can be done using the Dban application, just search about the forum if considering nuking via dban.

---

### Post by cdenley on 2009-12-24
> **tubbygweilo said:**
> As stated above it is far, far safer to level the machine and start a new with a clean install of your own. 

Nuking a machine can be done using the Dban application, just search about the forum if considering nuking via dban.

I also agree that you should install your OS yourself. I don't think 'nuking' or erasing is necessary, though. Simply install your choice of OS, and select to use the entire disk.
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

---

### Post by garryknight on 2009-12-24
> **Axel777 said:**
> I dont think he knows the username. 


If he's going in as root it won't matter, but a simple 'ls /home' will reveal that information.

---

### Post by cariboo on 2009-12-24
I really dislike suggesting a reinstall just for something simple as a forgotten password, it is a little bit of over-kill, and as the op seems to be a fairly new user, he may not have the skills to install an os.

---

### Post by cdenley on 2009-12-24
> **cariboo907 said:**
> I really dislike suggesting a reinstall just for something simple as a forgotten password, it is a little bit of over-kill, and as the op seems to be a fairly new user, he may not have the skills to install an os.

I don't think it was suggested as a solution. It was a security recommendation.

---

