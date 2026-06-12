---
title: "Linux Standard User Lacks Privileges to Mount External VeraCrypt Drive"
date: 2021-11-16
forum: Security
---

### Post by raywood on 2021-11-16
I am using a standard (i.e., non-administrative) user account in Ubuntu 20.04.3 LTS. To this system, I connect an external (USB) drive. Ubuntu cannot mount the drive itself: the drive is encrypted using VeraCrypt (VC).

VC runs successfully in the standard user account. But when I tell VC to mount that encrypted drive, there is a problem.

The problem is not that VC requests the password used to encrypt the drive. I enter that password; VC seems to accept it.

The problem is what happens next. Something -- the Ubuntu system, it seems -- presents me with a dialog that says, "Administrator privileges required. Enter your user password or administrator password."

When I enter that password, I get a warning: "Failed to obtain administrator privileges: [standard user account] is not in the sudoers file. This incident will be reported."

It seems that Ubuntu requires admin privileges to mount the external drive. How can I enable the standard user to do that?

---

### Post by TheFu on 2021-11-17
Good. Working as planned.

The power to mount is the power to destroy.  Accessing devices directly is extremely dangerous on any Unix-like OS.

I consider the automatic mounting of USB devices under /media to be a fatal security flaw too.

You can setup some sudoer settings to allow an exact mount command, with specific mount options, by a specific user. You could also allow veracrypt to be started only be specific non-sudo/root users and give them free reign over the system.  If it was me, I'd setup autofs to address as much of this as possible, but I've never used veracrypt on Linux and don't know if that can be scripted or not.  I know that LUKS (dm-crypt) can be addressed using **autofs**.

**The power to mount is the power to destroy.**

Of course, there are other opinions on this and I think they are all wrong. ;)

---

### Post by raywood on 2021-11-17
Agreed. I'm not trying to set up automatic login. I just want to know how to do what you said -- set up sudoer to specify the command, options, and user.

I'm just hoping that someone who has used VeraCrypt on Linux can advise how to do that. Thanks.

---

### Post by TheFu on 2021-11-17
> **raywood said:**
> Agreed. I'm not trying to set up automatic login. I just want to know how to do what you said -- set up sudoer to specify the command, options, and user.

I'm just hoping that someone who has used VeraCrypt on Linux can advise how to do that. Thanks.

You've confused me by saying "automatic login".  I'm not suggesting anything that happens at login.  Autofs causes storage to be mounted WHEN accessed, not before.  The storage doesn't even need to be seen from a GUI (before it is mounted), so the user would need to know where it was, make the access request, before it would show on the file system or in any GUI.

Here's the non-secure solution: [https://bbs.archlinux.org/viewtopic.php?id=250824](https://bbs.archlinux.org/viewtopic.php?id=250824)  sudo on Arch is the same as sudo on Ubuntu. I think that link has a bad idea, since it makes any sudo/wheel group member able to use veracrypt.  "wheel" was the SunOS equivalent of the sudo group on Ubuntu. If you use that solution and want just a specific userid access to veracrypt - but total access to everything it allows, don't use "wheel" or "sudo" as the group in the linked solution.

High-Level steps to solve this ... 
First, determine the exact command line with veracrypt that mounts the storage.
[LIST]
[*]There should be a manpage for veracrypt. [https://www.veracrypt.fr/en/Command%20Line%20Usage.html](https://www.veracrypt.fr/en/Command%20Line%20Usage.html)  Inside it, there should be explanations for the different options.   [https://arcanecode.com/2021/06/21/veracrypt-on-the-command-line-for-ubuntu-linux/](https://arcanecode.com/2021/06/21/veracrypt-on-the-command-line-for-ubuntu-linux/) was the first result that seemed relevant to me. I didn't look to close, but the fact that the password was part of the command set of BEWARE OF BAD SECURITY HERE warnings.  Anything on a command line is in the process table which any user can see.
Test doing the mount with sudo and veracrypt until it works exactly as you like, then take that exact command and make a Cmd_Alias in the sudoers, as spelled out in the sudoers documentation - use the exact exact command and options that work when you did it manually, BUT leave off the first sudo in the command.
[/LIST]
Second, setup a Cmd Alias 
[LIST]
[*]Now, you just need to allow that Cmnd_Alias to run as the unprivileged userid(s) you want. That is also in the sudoers documentation.  I don't have an example of these things, sorry.
[/LIST]

The Cmnd_Alias and command can be put into a file in /etc/sudoers.d/ directory, which should already be included at the bottom of the main sudoers file.  This way, new stuff is separate from the main file and won't be clobbered if there is an update.  
The User_Alias can with with listed userids or normal POSIX groups or netgroups. 
The Runas_Alias is where the User_Alias and Cmnd_Alias are merged.

I use 1 new file in that directory for each new command allowed so it is easier to maintain.

Have a **Try Ubuntu** flash drive handy, since an error in these files can make it so that sudo doesn't work for any userids.  Once I was making a change, but not thinking carefully enough about it and locked myself out of the sudo capability.  Without sudo, you can't modify the sudoers ...  To shorten this story, I did it wrong 3 times and had to use the Try Ubuntu flash boot to correct it each time before I realized my mistake. I'm stubborn in that way. ;)  

You could allow a specific userid to use veracrypt with any options, but then they could mount the storage anywhere and I've said it before - *the power to mount is the power to destroy.*

In the sudoers manpage, there is a useful EXAMPLES section with explanation for each example entry. I think there must be 50+ examples. Beware of the warnings and caveats, since subtle issues can allow users much more access than intended.

Sudo has hundreds of options which can be overwhelming. If you post the exact veracrypt command line and the list of usernames you want to be able to run it without entering a password, someone can provide the sudoers file lines.

After the encrypted volume is open, do you still need to mount the file system?  Which file system does your VC volume use?  NTFS or some native Linux one?

Sorry if I babbled and confused things. I'm just ignorant about veracrypt on Linux.

---

