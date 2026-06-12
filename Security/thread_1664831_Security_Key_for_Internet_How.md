---
title: "Security Key for Internet How?"
date: 2011-01-11
forum: Security
---

### Post by dontgetshocked on 2011-01-11
I chose not to use a security key upon installation to access the net but now wish to change this.I do not understand the help section.It has a login key but I don't understand how it works or how to edit or see what the command for it is.Can someone help me with this?

---

### Post by cariboo on 2011-01-11
I'm not exactly sure what it is you want to do, but if the gnome-keyring is asking you for a password, either disable automatic login, or set a blank password for the keyring. To do this, go to System->Preferences-> Passwords & Encryption, right click on the password and select change password.

---

### Post by dontgetshocked on 2011-01-11
use a password to prevent access to internet via a encryption key like it uses to login with

---

### Post by cariboo on 2011-01-11
The easiest way, to do what you want is to setup the internet connection so that only your user can access it, then setup another account for other users. Check the screen shot, and make sure available to all users is unchecked.

Make sure you log out when not at the computer.

---

### Post by dontgetshocked on 2011-01-11
The purpose of what i wanted was to stop someone from accessing the net if even if they broke my logon code.
At distro installation 3 things happen;
1.Asks for logon password
2.Asks for encryption for home folder if you choose to do so
3.Asks for key after os loads to further secure desktop.This means it needs
password to access net.
This is the way i understand it anyway.

---

### Post by bodhi.zazen on 2011-01-11
> **dontgetshocked said:**
> The purpose of what i wanted was to stop someone from accessing the net if even if they broke my logon code.
At distro installation 3 things happen;
1.Asks for logon password
2.Asks for encryption for home folder if you choose to do so
3.Asks for key after os loads to further secure desktop.This means it needs
password to access net.
This is the way i understand it anyway.

Seems like a long run for a short slide.

If someone can access the box, they can access the net with a live CD, unless you are taking wireless and WEP/WPA

I would simply encrypt your home directory and leave it at that.

---

### Post by dontgetshocked on 2011-01-11
Thanks,I do use Personal Wep/Wpa with big time password.Since I do have to access both of my pc's i don't think this is the solution for me since it would not let me access my home folder from the other pc.

---

