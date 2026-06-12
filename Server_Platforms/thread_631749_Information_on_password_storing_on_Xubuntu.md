---
title: "Information on password storing on Xubuntu"
date: 2007-12-04
forum: Server Platforms
---

### Post by giuffsalvo on 2007-12-04
Hi, I need an advice...Basicly, I created a VMware virtual machine dedicated for P2P, by starting from an Ubuntu 7.10 installation, removing all the unnecessary software, installing Azureus and MLDonkey, configuring them to be controlled remotely (by web and telnet interface), and deactivating automatic starting of GDM in runlevel 2. I also configured the VM to block connections to and from IPs of known anti-P2P companies, by using a program called ipblock, that auto-updates its lists once every 2 days.
Now, I'd like to share this VM with the rest of the world, by posting it on the VMware website. The problem is that I must change the password for the only 'normal' user (which I called p2pvm), which currently is set to the one I regularly use on other services (I know that in theory I should use a different password for any software/service I use), and I wonder if, even if I'd type

passwd

the old password would be cached somewhere (I already saw a disturbing, from a security point of view, series of backup configuration files in /var/backups).
What I want to avoid is someone downloading my VM from the VMware website, and then finding this password...
Thanks a lot

---

### Post by p_quarles on 2007-12-04
Ubuntu stores user's passwords in an encrypted format in the file:
```
/etc/shadow
```
Essentially, if you change the password, you be able to look at this file to reassure yourself that the main user only has one encrypted password. It's the second field in the user's row, following the user name.

---

### Post by giuffsalvo on 2007-12-06
I know this, but is there any other place where previous passwords are cached, like /tmp, or some other temporary file?
Thanks a lot

---

### Post by p_quarles on 2007-12-06
The only way that could happen is if you accidentally typed your password in plain text (e.g., you typed "sudo something," which returned a "command not found," you didn't notice this, and typed your password). This would then be stored in .bash-history. I suppose it could also be compromised if you, for some reason, installed a keylogger on this vm. 

Anyway, you can safely delete .bash-history from your home dir before distributing this vm. 

I've never heard of a Linux password system storing passwords anywhere other than /etc/shadow or /etc/passwd (that would be a pretty terrible security practice -- and GNU/Linux isn't really known for that), but even if it were to get stored in a /tmp folder, it would be cleaned up upon the next reboot.

---

### Post by dfreer on 2007-12-06
> **p_quarles said:**
> I've never heard of a Linux password system storing passwords anywhere other than /etc/shadow or /etc/passwd (that would be a pretty terrible security practice -- and GNU/Linux isn't really known for that), but even if it were to get stored in a /tmp folder, it would be cleaned up upon the next reboot.

Actually, there's a sticky concerning passwords stored in temporary setup files in this very forum:
[http://ubuntuforums.org/showthread.php?t=143334](http://ubuntuforums.org/showthread.php?t=143334)
Of course, this is no longer an issue.

However, if your are still wanting to ensure that your password is nowhere to be found, why not just grep all the files in your filesystem for your password? Of course, after doing this, your password may be in ~/.bash_history, but you can delete this as already mentioned. You may also want to grep for your password hash as shown in /etc/passwd, just in case the hash is being stored elsewhere.

---

### Post by HermanAB on 2007-12-06
Even Windows doesn't store passwords, only hashes.

'Nuff sed.

Cheers,

H.

---

