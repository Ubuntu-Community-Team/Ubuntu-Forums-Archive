---
title: "Unable to add new user"
date: 2010-07-30
forum: Security
---

### Post by JKyleOKC on 2010-07-30
I was apparently invaded this morning via my private FTP server. The invader logged in with my user name and apparently knew the password for the account, then downloaded the following files:

```
Fri Jul 30 07:19:57 2010 0 monted.net 116 /home/jim/passwords.txt b _ o r backuppc ftp 1 * c
Fri Jul 30 07:20:01 2010 0 monted.net 995 /home/jim/xxx.txt b _ o r backuppc ftp 1 * c
Fri Jul 30 07:20:17 2010 0 monted.net 958 /home/jim/proof.txt b _ o r backuppc ftp 1 * c
Fri Jul 30 07:22:55 2010 0 monted.net 141 /etc/inetd.conf b _ o r backuppc ftp 1 * c
Fri Jul 30 07:23:10 2010 0 monted.net 1874 /etc/ssh/sshd_config b _ o r backuppc ftp 1 * c
Fri Jul 30 07:32:23 2010 0 monted.net 884 /home/jim/.ssh/known_hosts b _ o r jim ftp 1 * c
Fri Jul 30 07:47:15 2010 0 monted.net 805 /home/jim/.bash_history b _ o r jim ftp 1 * c
Fri Jul 30 07:51:49 2010 0 monted.net 1719 /etc/passwd b _ o r jim ftp 1 * c
```

I've tried several times to create a new user so that I can move all of my critical material out of harm's way, but the new files do not take effect. Could I have a rootkit in place here?

The system is Hardy LTS 8.04.4, fully updated. I have backups that pre-date the intrusion, stored on another system, so am not totally averse to reformatting and reloading everything -- although I'd like to avoid it if possible!

The "passwords.txt" file contains only a few passwords for online forums, including this one; it does not include anything critical such as banking information. I'm most concerned about the implications of the ssh config data...

---

### Post by bodhi.zazen on 2010-07-30
> **JKyleOKC said:**
> I have backups that pre-date the intrusion, stored on another system, so am not totally averse to reformatting and reloading everything -- although I'd like to avoid it if possible!

I would image the partition for forensics at a later date.

I would then perform a fresh installation, 10.04 if possible, and restore your data from a known good back up.

If possible convert from ftp to ssh (scp , sftp) or vsftp and use stronger passwords.

If possible, try to understand how you were cracked (weak passwords ?).

Secure your server , use iptables or fail2ban to guard against brute force password crackers.

---

### Post by JKyleOKC on 2010-07-30
> **bodhi.zazen said:**
> I would image the partition for forensics at a later date.

I would then perform a fresh installation, 10.04 if possible, and restore your data from a known good back up.

If possible convert from ftp to ssh (scp , sftp) or vsftp and use stronger passwords.

If possible, try to understand how you were cracked (weak passwords ?).

Secure your server , use iptables or fail2ban to guard against brute force password crackers.Unfortunately I don't have disk space to be able to image the partition. It contains five VBox VMs for more than 100 GiB of virtual drives; I'm currently copying those over to another box to preserve them since I do not include them in the daily backup rotation.

As for installing 10.04, I'm waiting for it to stabilize -- and seriously considering switching from Xubuntu to Debian since most of the things touted as improvements for 10.04 strike me as negative rather than positive.

Switching from ftp to a more secure protocol is impossible; I maintain the server so that my customers worldwide can upload database files for recovery. These files are sometimes as large as 2.5 GiB so anything that slows down the transfer is unacceptable. The break-in was not via my anonymous capability, which is locked down very tightly -- it came through the home-folder capability that I use to back up my wife's machine, which refuses to communicate with my LAN directly. 

And yes, the password was woefully weak. I'm sure that was how the breakin happened, although there was absolutely no evidence of a dictionary attack beforehand. That's why I'm trying to create a new user with a stronger password, but the GUI utility apparently just won't write to the /etc/passwd file to establish the new user!

The secret of the breakin might be my use of BackupPC, which created the backuppc user and requires that this user have no password at all. Since I've been active on the BackupPC mailing list, the intruder might have used that route to gain initial entry. The log extract above indicates that this user name was involved for at least some of the downloads. I'm still pondering how to overcome this vulnerability...

---

