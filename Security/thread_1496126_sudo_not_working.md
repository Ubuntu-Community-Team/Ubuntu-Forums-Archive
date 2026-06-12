---
title: "sudo not working"
date: 2010-05-28
forum: Security
---

### Post by davethefan on 2010-05-28
Hi,

I'm having some trouble using sudo - it did work fine, but now when I try to use it, I have the following error:


[FONT="Courier New"]ubuntu@ubuntu:~$ sudo
>>> /etc/sudoers: syntax error near line 2 <<<
>>> /etc/sudoers: syntax error near line 3 <<<
>>> /etc/sudoers: syntax error near line 4 <<<
>>> /etc/sudoers: syntax error near line 5 <<<
sudo: parse error in /etc/sudoers near line 2
sudo: no valid sudoers sources found, quitting[/FONT]

I understand that I have to modify[FONT="Courier New"] /etc/sudoers[/FONT] but need to have root access to do this.
I am using a bootable USB (lucid) with persistent changes and am unable to login as root, because I don't know the default root password, and am unable to use sudo to change it.

The problem occurred after I had some corruption to the casper file system, so I booted into Windows, moved the casper-rw file to another location on my flashdrive, and used a 1GB backup filesystem to repair the corrupt one using fsck.

After booting up from the restored filesystem, sudo would no longer work.


Any help would be appreciated,
Thanks

David Thefan

---

### Post by CharlesA on 2010-05-29
Boot into recovery mode by holding down shift while the machine is booting. Then you should be able to fix the sudoers file using visudo.

This is what my sudoers file looks like on a clean install of Lucid:

```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults        env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Allow members of group sudo to execute any command after they have
# provided their password
# (Note that later entries override this, so you might need to move
# it further down)
%sudo ALL=(ALL) ALL
#
#includedir /etc/sudoers.d

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

```

---

### Post by Bachstelze on 2010-05-30
Also, since Charles's post didn't stress this enough, you should **always** use the [font=monospace]visudo[/font] command to edit the sudoers file. Also, as a less important note, you should use [font=monospace]sudo -i[/font] instead of [font=monospace]sudo -s[/font] to get a root shell in order to get your environment right.

---

### Post by davethefan on 2010-06-08
Thanks guys, Sorry about the belated reply. I will try that now.

Will I be able to copy and paste that, or would it be worth writing it down before rebooting?
Actually, I'll just take a photo of it on my camera :-)


Thanks again,
David Thefan

---

### Post by anomie on 2010-06-09
[QUOTE=Bachstelze]... you should **always** use the [font=monospace]visudo[/font] command to edit the sudoers file.[/QUOTE]

For posterity's sake, I'll stress this a third time. ;) 

visudo performs a number of syntactical checks after you're done editing. In your case, it would have caught the problem and prompted you to correct the syntax right away. This is particularly important with Ubuntu, where by default you live and die by sudo (i.e. if you can't sudo, you can't fix a sudoer problem from within your normal operating environment)...

---

### Post by bodhi.zazen on 2010-06-09
> **Bachstelze said:**
> Also, since Charles's post didn't stress this enough, you should **always** use the [FONT=monospace]visudo[/FONT] command to edit the sudoers file. Also, as a less important note, you should use [FONT=monospace]sudo -i[/FONT] instead of [FONT=monospace]sudo -s[/FONT] to get a root shell in order to get your environment right.

> **anomie said:**
> For posterity's sake, I'll stress this a third time. ;) 

visudo performs a number of syntactical checks after you're done editing. In your case, it would have caught the problem and prompted you to correct the syntax right away. This is particularly important with Ubuntu, where by default you live and die by sudo (i.e. if you can't sudo, you can't fix a sudoer problem from within your normal operating environment)...

+1 

IMO to many people feel then know what they are doing and directly edit sudoers.

The main advantage of visudo it that it will check for syntax errors.

If you do not like vim , change your editor. I believe 91.0 + now default to nano, but you can set your editor 

export EDITOR=nano && sudo -E visudo
export EDITOR=gedit && sudo -E visudo

you can add the export EDITOR to .bashrc if you like (add to /root/.bashrc)

---

### Post by Ninja duck on 2010-11-20
I have a similiar problem. I restarted and held down shift (it's a single boot) but no menu showed up to let me start in recovery mode. I tried several times. I'm using a usb keyboard but it's worked before.

---

### Post by Ninja duck on 2010-11-20
Never mind, I booted with a livecd and fixed it.

---

### Post by davidw1957 on 2011-03-16
This is what my /etc/sudoers.d/README looks like after a clean install of Kubuntu 10.04 Lucid Lynx

#
# As of Debian version 1.7.2p1-1, the default /etc/sudoers file created on
# installation of the package now includes the directive:
# 
#     #includedir /etc/sudoers.d
# 
# This will cause sudo to read and parse any files in the /etc/sudoers.d 
# directory that do not end in '~' or contain a '.' character.
# 
# Note that there must be at least one file in the sudoers.d directory (this
# one will do), and all files in this directory should be mode 0440.
# 
# Note also, that because the sudoers file is not a 'conffile' in the Debian 
# sense, and sudoers contents can vary widely, no attempt is made to add this 
# directive to existing sudoers files on upgrade.  Feel free to add the above 
# directive to the end of your /etc/sudoers file to enable this functionality 
# for existing installations if you wish!
#

---

### Post by bk60544 on 2011-03-16
Another newbie here, Ubuntu 10.10:  Please elaborate on the direction: "you should **always** use the [FONT=monospace]visudo[/FONT] command to edit the sudoers file".  Understand going into Recovery Mode, but then what?

---

### Post by matt_symes on 2011-03-16
Hi

> Another newbie here, Ubuntu 10.10: Please elaborate on the direction: "you should always use the visudo command to edit the sudoers file". Understand going into Recovery Mode, but then what?

Open a terminal and type

```
sudo visudo
```

Enter your password. You will not see it echoed to the screen. 

That is the correct way to edit the sudoers file.

Kind regards

---

### Post by runeh76 on 2011-03-16
Can someone tell me, why i cant see some pictures in my Chromium?
Example thread starter *davethefan* avatar.
I see only this: [IMG]http://img.askleomedia.com/picprog.png[/IMG]

When i save it and trying to open it, i get error:
Not a JPEG file: starts with 0x

Other avatars are fine.
Pls post can u or not see that avatar.

---

### Post by matt_symes on 2011-03-16
Hi

> Pls post can u or not see that avatar.

I can see your avatar.

Kind regards

---

### Post by runeh76 on 2011-03-16
Oh! Okey then my browser have problem.. Thx!!

---

### Post by cariboo on 2011-03-16
> **runeh76 said:**
> Can someone tell me, why i cant see some pictures in my Chromium?
Example thread starter *davethefan* avatar.
I see only this: [IMG]http://img.askleomedia.com/picprog.png[/IMG]

When i save it and trying to open it, i get error:
Not a JPEG file: starts with 0x

Other avatars are fine.
Pls post can u or not see that avatar.

The avatar you are refering to is broken, it is either to large in pixel size, or the file itself is to large.

---

### Post by runeh76 on 2011-03-17
Allright that what i was thinking too, becouse i tryed many others browsers too! Thanks so much!

---

