---
title: "Samba Upgrade Faliure Prevents Accepting Sudo Credenatils"
date: 2017-05-30
forum: Server Platforms
---

### Post by amitha3 on 2017-05-30
Hi All,

Today I upgraded all my Ubuntu server's (12.04) samba version to get rid of from SambaCry threat by giving the following commands

[B]sudo apt-get update
sudo apt-get install samba[/B]

since the server had only the samba client it prompts me to install the samba server. I selected "yes" option

**during the installation it prompted to restart some services or to  skip those, I selected the restart option. But the installation has  failed in the middle**.

now when I type "sudo reboot" command to reboot the server it doesn't accept my user's password [IMG]http://www.linuxforums.org/forum/images/smilies/icon_sad.gif[/IMG] [IMG]http://www.linuxforums.org/forum/images/smilies/icon_sad.gif[/IMG]

[B]But when I access the server using ssh it accepts the user's  password.but inside that ssh session when I try to give the "sudo  reboot" command, it also doesn't accept the password [IMG]http://www.linuxforums.org/forum/images/smilies/icon_sad.gif[/IMG] 
[/B]
What should I do to get my system back to the normal stage? **Your help is very much appreciated.**

Thanks

---

### Post by Michael_McKenney on 2017-05-30
Did you try removing Samba and reinstalling it?  Backup your smb.conf first

sudo apt-get remove --purge samba
sudo apt-get install samba

---

### Post by darkod on 2017-05-30
You didn't need to install samba if you did not have it installed. You need only to patch existing installations of samba, not to install new ones if you don't need them. Also you should have checked the samba version before doing anything because if you have the server set up to install security updates automatically, it is probably already patched. That was a security update and it would have installed automatically.

What exactly "failed in the middle"? If a package installation fails that wouldn't mess with your sudo rights.

---

### Post by Morbius1 on 2017-05-30
> Today I upgraded all my Ubuntu server's (12.04) samba version to get rid  of from SambaCry threat by giving the following commands

** There is no update to samba to fix the WannaCry vulnerability since samba isn't affected - you need a WindowsOS for that.

** If you mean you wanted to fix this [vulnerability]("https://www.ubuntu.com/usn/usn-3296-1/") there is no update available for Ubuntu 12.04.

** The reason there is no update available is because Ubuntu 12.04 is no longer supported.

Am I missing something?

---

### Post by darkod on 2017-05-30
> **Morbius1 said:**
> ** The reason there is no update available is because Ubuntu 12.04 is no longer supported.

Am I missing something?

That completely slipped my mind. :) 12.04 is EOL already...

The apt-get wouldn't even work unless you did some tweaks (changing the sources.list).

If what the OP actually did was upgrade of release from 12.04 to 14.04 and that stopped in the middle, in such case you could have serious issues...

---

### Post by amitha3 on 2017-05-31
Hi All,

Thanks for your information. **Currently I'm struggling to get the sudo command working**. pkexec is working fine for all the commands but that is not a proper solution. This production server is installed on ESXI host and am not able to log into the server bu giving the user credentials from ESXI console. But from ssh I am able to access the server in concern by giving the user credentials even though the sudo command doesn't work.

I tried the command :
**pkexec apt-get update && pkexec apt-get --purge --reinstall sudo** but it ends up with an error :(

==== AUTHENTICATING FOR org.freedesktop.policykit.exec ===
Authentication is needed to run `/usr/bin/apt-get' as the super user
Authenticating as: user1,,, (user1)
Password:
==== AUTHENTICATION COMPLETE ===
E: Invalid operation sudo

---

### Post by darkod on 2017-05-31
Please answer our question above first. How did you install samba when 12.04 is EOL and not supported any more? I believe apt-get can't install new packages in that case because the repositories are moved when a release goes EOL.

On another note, what you could try to solve the sudo rights issue is go to the vmware console for the VM, reboot it and start ubuntu in recovery mode (in grub menu go into Advanced Options and select the recovery entry). That can allow you to start a root shell, with read-only filesystem.

You can remount the filesystem to be read-write and as root allow sudo rights for your user. You can even reset the password for your user if you want to, but you obviously know the password and it lets you log in.

---

### Post by amitha3 on 2017-05-31
> **darkod said:**
> Please answer our question above first. How did you install samba when 12.04 is EOL and not supported any more? I believe apt-get can't install new packages in that case because the repositories are moved when a release goes EOL.

On another note, what you could try to solve the sudo rights issue is go to the vmware console for the VM, reboot it and start ubuntu in recovery mode (in grub menu go into Advanced Options and select the recovery entry). That can allow you to start a root shell, with read-only filesystem.

You can remount the filesystem to be read-write and as root allow sudo rights for your user. You can even reset the password for your user if you want to, but you obviously know the password and it lets you log in.

Hi Darkod, I just gave the command sudo apt-get install samba to update the samba version. It hitted some URLs and allow me to install the samba version. ( I ran apt-get update version before** since it's a LTS version** ) 

My server OD details are as follows


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.2 LTS"


[B]With the current condition of the server do you think that I can upgrade it to 14.04 first and 16.04, if the apt-get repositories are stopped? Also will the upgrade solve this sudo issue?

[/B]Thanks

---

### Post by darkod on 2017-05-31
Without sudo working it will not allow you to run the release upgrade command. There is a way to upgrade LTS to LTS when it is EOL, but in this case with the issues you already have on the machine, and since the latest LTS is actually 16.04, I would recommend doing a new clean install of 16.04 and restoring your data from backup.

Otherwise you need two upgrades to get to 16.04 and sometimes that can create issues. You already have issues before even starting release upgrades.

---

### Post by amitha3 on 2017-06-01
Thanks for your advice :)

---

