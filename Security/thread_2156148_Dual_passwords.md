---
title: "Dual passwords?"
date: 2013-06-20
forum: Security
---

### Post by kr651129 on 2013-06-20
Is there a way I can hack my Ubuntu desktop install to have two passwords where one logs me in like normal and the other say logs me into another user or preforms some action?

---

### Post by papibe on 2013-06-20
Hi kr651129.

Not really. However, that exact same thing can be accomplish creating another user, and choosing between them at login time.

Just a thought.
Regards.

---

### Post by kr651129 on 2013-06-20
Oh I know, I'm just in a creative mood today wanted to do some coding/hacking didn't know if that was something that had already been done.  Is there a way to hide a username at the login screen?

---

### Post by CharlesA on 2013-06-20
> **kr651129 said:**
> Oh I know, I'm just in a creative mood today wanted to do some coding/hacking didn't know if that was something that had already been done.  Is there a way to hide a username at the login screen?

Assuming you are using Unity, this might be helpful:
[https://wiki.ubuntu.com/LightDM#Hiding_the_User_List](https://wiki.ubuntu.com/LightDM#Hiding_the_User_List)

---

### Post by KlipperKyle on 2013-06-28
By default, Ubuntu's root account comes with no password (to prevent you from accidentally logging in as root). However, it is quite easy to create a root password:

```
sudo passwd
```

Now, you can log in as either your regular account, or the root account. (However, lightdm might need additional configuration to allow login as root. Go ahead and try it. You can always log into a tty as either user by pressing ctl+alt+f1 through ctl+alt+f6. (lightdm is usually on ctl+alt+f7 or ctl+alt+f8.))

By default, sudo asks you for the password of the current account you are logged into. However, sudo can be configured to ask for the root password instead:

[https://wiki.archlinux.org/index.php/Sudo#Root_password](https://wiki.archlinux.org/index.php/Sudo#Root_password)

Be careful when modifying /etc/sudoers. Before modifying it, create a root password so that you can use su in case something goes wrong. (su always asks for the root password and is entirely separate from sudo.)

---

### Post by CharlesA on 2013-06-28
> **KlipperKyle said:**
> By default, Ubuntu's root account comes with no password (to prevent you from accidentally logging in as root). However, it is quite easy to create a root password

True, but it is normally a bad idea to login to the GUI as root.

I would say you have given enough warning about enabling the root account, but please keep [this]("http://ubuntuforums.org/showthread.php?t=1486138") in mind. :)

---

### Post by deadflowr on 2013-06-28
> **KlipperKyle said:**
> By default, Ubuntu's root account comes with no password (to prevent you from accidentally logging in as root). However, it is quite easy to create a root password:

```
sudo passwd
```

Now, you can log in as either your regular account, or the root account. (However, lightdm might need additional configuration to allow login as root. Go ahead and try it. You can always log into a tty as either user by pressing ctl+alt+f1 through ctl+alt+f6. (lightdm is usually on ctl+alt+f7 or ctl+alt+f8.))

By default, sudo asks you for the password of the current account you are logged into. However, sudo can be configured to ask for the root password instead:

[https://wiki.archlinux.org/index.php/Sudo#Root_password](https://wiki.archlinux.org/index.php/Sudo#Root_password)

Be careful when modifying /etc/sudoers. Before modifying it, create a root password so that you can use su in case something goes wrong. (su always asks for the root password and is entirely separate from sudo.)

No, there is a root password.
It just so happens that the root account is locked and disabled.
But, just because it's locked doesn't mean it doesn't have password.
running sudo passwd root doesn't just create a password, but resets a new password.

Think of it this way though, even if you unlock and enable the original root password, do you know it?

Anyway, logging in as root is for the most part a waste, in Ubuntu.
It's far easier to sudo -i to grab a root session, then to set a password and reconfigure some files, which may or may not get totally borked from ones own incompetence.
And you can su into any user on the system, and gain their rights.
I su from a normal user into an admin user when I want to do an install or something, but don't want to fully switch out to that user.

So there really no need to enable root's password.

---

