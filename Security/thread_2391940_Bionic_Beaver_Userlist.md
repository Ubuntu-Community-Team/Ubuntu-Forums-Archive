---
title: "Bionic Beaver Userlist"
date: 2018-05-15
forum: Security
---

### Post by AbdRahim on 2018-05-15
Has anyone successfully hidden the userlist at login? I tried older method of creating lightdm.conf, ( in LUbuntu  but his alonwlong with adding username to noaccess in another file caused it not to boot. I need to do this in LUbuntu and Ubuntu 18.04.

Thanks in advance for your help.

---

### Post by deadflowr on 2018-05-15
What did you actually add to the ligthdm.conf file?
And what other file did you add to?

---

### Post by Qassis on 2018-05-15
Have you already added hidden-users to  /etc/lightdm/users.conf
Here's mine (Ubuntu 18.04) without hidden users.


#
# User accounts configuration
#
# NOTE: If you have AccountsService installed on your system, then LightDM will
# use this instead and these settings will be ignored
#
# minimum-uid = Minimum UID required to be shown in greeter
# hidden-users = Users that are not shown to the user
# hidden-shells = Shells that indicate a user cannot login
#
[UserList]
minimum-uid=500
hidden-users=nobody nobody4 noaccess
hidden-shells=/bin/false /usr/sbin/nologin

---

### Post by AbdRahim on 2018-05-15
Currently this method is not working because of a bug in lightdm.

Please check the bug status before applying this method.

Heres what you want to do:

First, make a backup of your config.

sudo cp /etc/lightdm/users.conf /etc/lightdm/users.conf.bak

Then, you need to edit your config:

sudo nano /etc/lightdm/users.conf

You'll see something like this:

#
# User accounts configuration
#
# NOTE: If you have AccountsService installed on your system, then LightDM will
# use this instead and these settings will be ignored
#
# minimum-uid = Minimum UID required to be shown in greeter
# hidden-users = Users that are not shown to the user
# hidden-shells = Shells that indicate a user cannot login
#
[UserAccounts]
minimum-uid=500
hidden-users=nobody nobody4 noaccess
hidden-shells=/bin/false /usr/sbin/nologin

Of interest to us is the part here:

hidden-users=nobody nobody4 noaccess

To hide the username james, just add it like this:

hidden-users=nobody nobody4 noaccess james

Then, reboot your computer and it should be gone.

---

### Post by AbdRahim on 2018-05-15
This method is not works on Ubuntu 13.10.

To hide user login names correctly You must to open LightDM config:

sudo vim /etc/lightdm/lightdm.conf

and add the following options:

greeter-hide-users=true
greeter-show-manual-login=true

---

### Post by again? on 2018-05-15
I am using Xubuntu 18.04 with lightdm using lightdm-gtk-greeter.
I can hide the userlist by simply creating a config @
**/etc/lightdm/lightdm.conf.d/99-hide-users.conf**
```
[Seat:*]
greeter-hide-users=true
```

This command will create the file:
```
echo -e "[Seat:*]\ngreeter-hide-users=true" | sudo tee /etc/lightdm/lightdm.conf.d/99-hide-users.conf
```

To revert to showing users, simply delete the config...
```
sudo rm /etc/lightdm/lightdm.conf.d/99-hide-users.conf
```

Check that settings from a config file in the /etc/lightdm directory doesn't override.

***Note from [https://wiki.ubuntu.com/LightDM](https://wiki.ubuntu.com/LightDM) ...
> **Later versions of lightdm (15.10 onwards) have replaced the obsolete [SeatDefaults] with [Seat:*]**

LightDM configuration is provided by the following files:

/usr/share/lightdm/lightdm.conf.d/*.conf
/etc/lightdm/lightdm.conf.d/*.conf
/etc/lightdm/lightdm.conf
System provided configuration is stored in /usr/share/lightdm/lightdm.conf.d/*.conf and is not user editable. 
System administrators can override this configuration in /etc/lightdm/lightdm.conf.d/*.conf and /etc/lightdm/lightdm.conf. 
Files are read in the above order and combined together to make the LightDM configuration.

---

### Post by oldos2er on 2018-05-15
> **AbdRahim said:**
> This method is not works on Ubuntu 13.10.

No one concerned about security should still be using 13.10, support for it ended in July 2014.

---

### Post by AbdRahim on 2018-05-17
I am not using 13.10, but am trying to apply that method in 18.04. Will by otherwise occupied for a few days before I can try anything else. I will get back on here when I find a solution that works.Thanks all.

---

### Post by oldos2er on 2018-05-17
> **AbdRahim said:**
> I am not using 13.10, but am trying to apply that method in 18.04. 

Thank you for the clarification.

---

