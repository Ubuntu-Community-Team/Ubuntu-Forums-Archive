---
title: "REMMINA: saving the configuration file in a non-standard location"
date: 2012-08-21
forum: Security
---

### Post by askold on 2012-08-21
Objective: to save user profiles on an external drive or an encrypted container TrueCrypt. In the case of Firefox & Thunderbird simple and clear: use the terminal "thunderbird-P", a window profile switch. Remove existing and create a new, specify the path where the data will be based on the profile.
Q: how to change the settings remmina so that configuration is stored on an external drive or an encrypted container TrueCrypt, not ".. / Home / user / home folder / .remmina /"?

---

### Post by askold on 2012-08-23
The issue:
Create a container TrueCrypt.Mount it say how truecrypt1. We go to the home directory, cut the folder ". Remmina" and place it in a container. In the terminal, we collect "ln-s / media/truecrypt1/.remmina / home / user /". After that, the user's home directory there is a link to a folder ". Remmina". Now, when the mounted container available all settings remmina, if the container removed-remmina opens completely empty shell without any configuration. By the way an attempt to create and save a new connection, is doomed to failure, nothing sohranyaetsya.Edinstvennoe on what to look for: trying to download the configuration and not finding them (at unmounted container TrueCrypt), remmina believes that the configuration file is corrupt and has to remove it. And it's not necessary to do - if you delete a link remmina create new directory "/ user / .remmina / " will continue to load the configuration from here.

---

