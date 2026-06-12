---
title: "Setting Permissions for Guest"
date: 2008-09-16
forum: Security
---

### Post by mistman123 on 2008-09-16
I can't find my specific problem on here so I'll just ask.

I have Ubuntu installed in the Windows partition and I like it that way because I don't heavily use it so that way I could uninstall it anytime I want with no big hassle.

The problem is related to permissions for user accounts such as a Guest account I created. I want to stop it from being able to open the host folder. I've tried using chmod and chown to set permissions for "Other" on the "host" folder to "Nothing" but haven't been able to. The current owner is obviously root and even when logging in as root through either the terminal or even the gnome desktop and manually right clicking the folder and changing permissions, it won't save the setting and will automatically revert to the old permission.

I'd like to have the Guest account login automatically so that someone may use the computer in a very low permission setting (and not be able to see the host file).

I've been able to set the permissions for all other user folders so that Guest can't get to them, except the host folder.

Is there any way I could do this? Is there even a command that would limit ALL Guest's permissions to any other folder except its own "home" folder? Help please!

---

### Post by cdenley on 2008-09-16
> **mistman123 said:**
> I can't find my specific problem on here so I'll just ask.

I have Ubuntu installed in the Windows partition and I like it that way because I don't heavily use it so that way I could uninstall it anytime I want with no big hassle.

The problem is related to permissions for user accounts such as a Guest account I created. I want to stop it from being able to open the host folder. I've tried using chmod and chown to set permissions for "Other" on the "host" folder to "Nothing" but haven't been able to. The current owner is obviously root and even when logging in as root through either the terminal or even the gnome desktop and manually right clicking the folder and changing permissions, it won't save the setting and will automatically revert to the old permission.

I'd like to have the Guest account login automatically so that someone may use the computer in a very low permission setting (and not be able to see the host file).

I've been able to set the permissions for all other user folders so that Guest can't get to them, except the host folder.

Is there any way I could do this? Is there even a command that would limit ALL Guest's permissions to any other folder except its own "home" folder? Help please!

What's the "host folder"? Is that a wubi thing which mounts your windows partition as "host"? What is the output of these commands
```

mount
sudo cat /etc/fstab

```

As far as taking away the user's permissions for everything, that wouldn't work. They would need access to stuff like gnome, xserver, or a shell, otherwise they would be staring at a black screen.

---

### Post by cariboo on 2008-09-16
The way to setup your Guest account, is to go to System-->Aministration-->Users and Groups, click on the unlock button and enter your password. Then select the guest and click properties, then click the User Privileges tab. Put check marks on the functions you want to allow the user, then click OK.

To let the Guest autologin, Go to System-->Administration-->Login Window, enter your password when asked. Click the Security tab, click Enable Automatic Login, then click the dropdown and select your Guest user, click the Close button and your done. To check if it works, do it the windows way and restart or hit Ctrl-Alt-Backspace to restart X.

Jim

---

