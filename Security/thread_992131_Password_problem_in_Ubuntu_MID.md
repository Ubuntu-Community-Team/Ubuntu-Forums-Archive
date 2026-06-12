---
title: "Password problem in Ubuntu MID"
date: 2008-11-24
forum: Security
---

### Post by citizenphil on 2008-11-24
I've installed Ubuntu MID using the default settings and not setting a password during install. After the installation, I set the root and user password using 'passwd' and 'sudo passwd root' (I've also tried 'sudo -i' then 'sudo passwd' and also 'sudo bash' then 'sudo passwd'). Both of these report success. After rebooting the machine, I am still able to sudo by just typing Enter at the password prompt.

I've been unable to find any documentation on this problem. Has anyone run into this, and is there a fix?

---

### Post by cdenley on 2008-11-24
> **citizenphil said:**
> I've installed Ubuntu MID using the default settings and not setting a password during install. After the installation, I set the root and user password using 'passwd' and 'sudo passwd root' (I've also tried 'sudo -i' then 'sudo passwd' and also 'sudo bash' then 'sudo passwd'). Both of these report success. After rebooting the machine, I am still able to sudo by just typing Enter at the password prompt.

I've been unable to find any documentation on this problem. Has anyone run into this, and is there a fix?

I just tested it, and it works fine for me in intrepid. What is MID? What version are you running? Are you sure you're not just re-using the sudo timestamp. You should not set a root passwd. The password sudo  prompts you for is your password, not root's.
```

sudo -K
passwd
sudo usermod -p ! root

```

---

### Post by citizenphil on 2008-11-24
MID is the mobile edition of Ubuntu, and I believe it's the most recent version. Setting the password works fine in Intrepid for me also; it seems to be specific to the mobile edition.

My thinking was that without a root password set, someone would be able to log on to the machine via ssh as root, or use the 'su' command without needing a pass. Is this incorrect?

In any case, I did reboot the machine to reset the timestamp, and the new user password I set was still not needed to sudo.

---

### Post by cdenley on 2008-11-24
> **citizenphil said:**
> MID is the mobile edition of Ubuntu, and I believe it's the most recent version. Setting the password works fine in Intrepid for me also; it seems to be specific to the mobile edition.

My thinking was that without a root password set, someone would be able to log on to the machine via ssh as root, or use the 'su' command without needing a pass. Is this incorrect?

In any case, I did reboot the machine to reset the timestamp, and the new user password I set was still not needed to sudo.

By default, the password HASH for root is "!". This means there is no valid root password. The root account is basically disabled, but you can still gain root access with sudo.

There must be something special about MID, then. You can try checking the sudoers file:
```

sudo EDITOR=nano visudo

```
There should not be a line uncommented with "NOPASSWD". Without comments, it should look like:
```

Defaults env_reset
root ALL=(ALL) ALL
%admin ALL=(ALL) ALL

```
The password was actually set for your user, right? You needed to enter it to use the system?

---

### Post by citizenphil on 2008-11-25
No valid root password. That makes sense now. Good to know.

We came up with a workaround: Set the root password and remove the user from the admin group. This way they can still type 'su' and enter the root password but cannot sudo. Not what I'd like, but it works.

The password was set for the user but not needed to login. That seems to be the default for MID. Still, 'sudo passwd', followed by a reboot, should reset the password that is required for sudo, right?

We're installing these as internet kiosks at a hotel, so they'll be out of our hands in a while. I'll look into the sudoers file and see if anything's out of place. I'd do it now, but won't be able to look at it again till Monday. If we still can't figure it out I guess we'll stick with the workaround.

Thanks for the help.

---

### Post by cdenley on 2008-11-26
> **citizenphil said:**
> Still, 'sudo passwd', followed by a reboot, should reset the password that is required for sudo, right?

By default, sudo asks for YOUR password, not root's. That can be changed in the sudoers file, though.
```

man sudoers

```

---

### Post by terencelhl on 2009-02-06
> **citizenphil said:**
> I've installed Ubuntu MID using the default settings and not setting a password during install. After the installation, I set the root and user password using 'passwd' and 'sudo passwd root' (I've also tried 'sudo -i' then 'sudo passwd' and also 'sudo bash' then 'sudo passwd'). Both of these report success. After rebooting the machine, I am still able to sudo by just typing Enter at the password prompt.

I've been unable to find any documentation on this problem. Has anyone run into this, and is there a fix?

Man, I didn't see any password field during the installation but able to figure it out.

From "Terminal", type below

passwd

When prompted for password, just hit "Enter" key, it will asks for new password.

Good Luck!

Regards,

Terence at tlc dot com dot my

---

