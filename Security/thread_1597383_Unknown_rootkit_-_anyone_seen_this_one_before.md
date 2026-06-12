---
title: "Unknown rootkit - anyone seen this one before?"
date: 2010-10-15
forum: Security
---

### Post by mubes on 2010-10-15
My external facing network, and the machine that hosts it, has been hacked.

Somehow a compromised sshd has been installed.  This allows login as root with the password [FONT="Courier New"]@#$%TheInfinit0fLife@#$%[/FONT]. Once logged in it then connects via IRC to a server somewhere on the planet. No processes appear on the process list but you can see the IRC connection via netstat -t.

The files that have been modified appear to be;
 
[FONT="Courier New"]/usr/bin/ssh
/usr/bin/sftp
/usr/bin/scp
/usr/sbin/sshd
[/FONT]
I deleted the first three before deciding it might be a good idea to keep them (doh), so I only have stats for sshd;
[FONT="Courier New"]
# file /usr/sbin/sshd
/usr/sbin/sshd: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.4.1, not stripped
# md5sum /usr/sbin/sshd
7c0f035319718f567a08b68903446446  /usr/sbin/sshd
# ls -al /usr/sbin/sshd
-rwxr-xr-x 1 1001 1001 895258 2010-01-29 14:04 /usr/sbin/sshd
[/FONT]
Each of the files was locked into place with a chattr call - which is how I found it since they couldn't be upgraded.  This made me suspicious and then I went hunting and found the password above via 'strings'. The userid and groupid on the files are set to a user that no longer exists on my system, which leads me to think that this was done a long while ago. This machine is kept current and fully patched so I'm guessing sometime between April (Release of Ubuntu 10.04) and now.  This looks like a old rootkit (note the Linux kernel version number).

Anyone seen anything like this before and can suggest where to point me for more information? Note that chkrootkit doesn't see anything amiss.. :-(

Mubes

---

### Post by bodhi.zazen on 2010-10-15
rootkits are not the only potential for this result. Access could have been via another server or physical access or who knows really.

I advise you image the HD for forensics and re-install. When you install use strong passwords.

From there, what services are you running ? VNS ? SSH ? FTP ?

---

### Post by teejaybee on 2010-10-15
+1 for full reinstall. DO NOT rely on just deleting files and reinstalling what you think has been compromised - there could be all kinds of hidden goodies that will take quite some skill and time to find. Make a note of what you have used the machine for - check your email? Log into websites? Do your banking? Everything you've accessed needs to be locked down also, such as changing the password from a non-compromised machine, on a non-compromised network.

Mirror the hard drive, or pull it out completely. Put it in another machine without network access. Copy files that you need onto a cd or usb drive and put them on your freshly installed machine. Make sure the files you are copying from the compromised machine aren't able to compromise the new machine (eg. dont copy kernels, libraries, etc. just userspace data). Anything you copy from the compromised machine must be thoroughly inspected.

It's now time to start thinking about who you want to have access to that machine (read: who you trust) and if you want to notch your security up a level. Firewall, apparmor, intrusion detection, and maybe something like auditctl or tripwire to let you know when files have changed (make a note of every time you apply updates to avoid false positives).

Good luck.

---

### Post by HermanAB on 2010-10-16
Howdy,

I have been using UNIX machines since 1985 and have yet to see a rootkit.  A compromise is usually a simple brute force attack done via VNC, SSH, FTP or Apache when someone used a stupid password.

The only thing you can do now, is to re-install and ensure that in future, you use proper passwords for everything.  My user passwords are 12 characters and my root passwords are 16 characters, semi pronounceable.

---

### Post by mubes on 2010-10-16
I'm with you in the 'Never seen one' camp.  My personal history is only back to '92 with Unix/Linux but I've never seen a 'real' Trojan unless someone's done something silly.

In this case though it's difficult to see how it got in.  The only external service running on the box was ssh and that was on a non-standard port...and passwords were all relatively complex with only a few users.  The only way I can see that it got in is if I accidentally updated openssh with an unsigned version. Looking back in the logs I see the last time it was modified via a deb file was back on Jun 13th.

Machine has now been reformatted and re-installed...no idea exactly what little presents had been left lying around by my visitor, better safe than sorry.  Kept the logfiles just in case they're useful later, but threw the rest in the bin.  ssh has been switched off too as it's not really needed on this box...it's now properly isolated.

At least my files were on encfs, but even then, with root access, its not difficult to get to them.

Oh well, I've learned something....and I now feel a lot more humble in my security-fu.

---

### Post by SeijiSensei on 2010-10-17
If you have root logins enabled in sshd_config, turn it off.  Using shared-key authorization rather than passwords is also more secure.

---

