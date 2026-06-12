---
title: "[SOLVED] How to know (the easy way) if my system has an intruder?"
date: 2008-12-16
forum: Security
---

### Post by juanp.contreras on 2008-12-16
Hi,

I want to know how can I verify easily if my system has been compromised by an external intruder. Im the only user logged in, but sometimes ubuntu blocks unexpectedly or some programs like compiz terminate without my will.

Thanks

---

### Post by damis648 on 2008-12-16
What sort of services do you have running? Is an SSH server running?

---

### Post by The Cog on 2008-12-17
I think chkrootkit and rkhunter ar the two most commonly recommended programs. But intruders don't normally like to bring attention to themselves, so I think your issues are most likely hardware or driver related problems.

---

### Post by x3roconf on 2008-12-17
> But intruders don't normally like to bring attention to themselves, so I think your issues are most likely hardware or driver related problems.

very true. ;-) BUT...

Have you checked with these commands that you are/were really the only user logged in?

```
w last lastlog
```

Do you see anything suspicious? like logins from odd hosts, odd login times suspicious usernames and etc?

thought logs can be easily modified.. but like damis648 said we need to know what services are running.

---

### Post by juanp.contreras on 2008-12-17
I am using an SSH server and SAMBA.

Following your insight, I've run chkrootkit and rkhunter. Apparently, there's nothing abnormal, but I have seen this:

On chkrootkit->

eth0: PACKET SNIFFER(/sbin/dhclient3[8114])
.
.
.
Checking `z2'... user xxxx deleted or never logged from lastlog!
user yyyy deleted or never logged from lastlog!

On rkhunter->

Checking if SSH root access is allowed                   [ Warning ]
Checking /dev for suspicious file types                  [ Warning ]

What do you think about?
How do I deactivate SSH root access?

---

### Post by Kinstonian on 2008-12-17
The *easiest* way is with anti-malware scanners such as rkhunter.  However, an incident is a series of adverse and anomalous events-- what you're looking for is anomalies.  So, the *best* way to find intrusions is to get a good idea of what is normal for your computer (normal processes, logs, network connections, activity, etc) and what is normal for attacks (common attacks, phases of an attack, what attacks do after gaining access, etc).  The better understanding you have of what is normal, the better position you are in to detect anomalies (i.e. attacks).

---

### Post by cdenley on 2008-12-17
> **juanp.contreras said:**
> 
How do I deactivate SSH root access?

There is no need in ubuntu. They will never be able to guess the root password, since there is no real password. However, if you set a root password (not recommended), then I would set this variable in /etc/ssh/sshd_config:
```

PermitRootLogin no

```

---

### Post by gTinker on 2008-12-17
I agree with Kinstonian about the "easiest" way. 

However your question specified "the easy way". The bottom line is that there is no easy way. The intruders that you need to be most worried about are very clever and good at covering their tracks. They won't leave log results that you can find and may even go so far as to replace the binaries of check programs like rkhunter or others. You need to have those check programs somewhere unmounted when the intrusion happens and run known clean versions when you are checking. And, you need to have known good backups to restore your system from when you suspect it is compromised.

Sorry, but security and easy don't go well together.

By the way:
It's normal for the dhclient to monitor an interface, it's what receives the IP address offer from your DHCP server.

You can't have anyone logon as root on SSH because the root account doesn't have a password, or did you change that someway?

---

### Post by juanp.contreras on 2008-12-17
I have set up the root password, only because I want full access in some situations... yes I know, it is dangerous, but... ¿can I deny root login for SSH?, or, ¿if I do as cdenley said the root login gets denied for my local console?

May be I'm quite paranoid... I'm acting that way because I do not know If I can trust all the packages I find in synaptic... I have installed every program of my system from it, so, if those sw is secure, my worry is vain and futile...

---

### Post by cdenley on 2008-12-17
> **juanp.contreras said:**
> I have set up the root password, only because I want full access in some situations... yes I know, it is dangerous, but... ¿can I deny root login for SSH?, or, ¿if I do as cdenley said the root login gets denied for my local console?

May be I'm quite paranoid... I'm acting that way because I do not know If I can trust all the packages I find in synaptic... I have installed every program of my system from it, so, if those sw is secure, my worry is vain and futile...

There is no need to set a root password for full access. You can use sudo, or if sudo breaks, you can boot into recovery mode from the grub menu.
```

sudo -i

```

The Ubuntu repository is considered secure in the sense that no intentionally malicious code ends up in it. You can review the code yourself if you want. As with any software, there are going to be security vulnerabilities, though.

---

### Post by juanp.contreras on 2008-12-17
Ok, so... ¿how do I disable root access or "unactivate" it?... 
yes, sudo, I've used sudo, but I'm quite unsure because, again, ¿how do I take for granted that my password can't or hadn't be stolen?

The other issue that caused me this doubt is related to user accesses in some programs. My system has an account without any privileges except manage audio and cdrom access. But, I'm suspecting that the user of that account has navigated with firefox to many (perhaps) dangerous pages. It is possible that firefox had been corrupted anyway?, yes, again I know about file permissions, and my own home is totally blocked for any user except myself. 

Also, if there isn't a web server or apache or any service hearing outside, ¿it is possible that some external (not added) user can navigate the file system?

Thanks a lot!

---

### Post by cdenley on 2008-12-17
> **juanp.contreras said:**
> Ok, so... ¿how do I disable root access or "unactivate" it?...

```

sudo usermod -p ! root

```
> **juanp.contreras said:**
> 
yes, sudo, I've used sudo, but I'm quite unsure because, again, ¿how do I take for granted that my password can't or hadn't be stolen?

If you don't trust using an admin user for everyday tasks, then use a non-admin user and treat your admin users as if they are root. You can always switch users for admin tasks, like you would with root on other distributions. What you don't want to do is use root any more than you have to, or allow attackers the possibility of authenticating as root.
> **juanp.contreras said:**
> 
The other issue that caused me this doubt is related to user accesses in some programs. My system has an account without any privileges except manage audio and cdrom access. But, I'm suspecting that the user of that account has navigated with firefox to many (perhaps) dangerous pages. It is possible that firefox had been corrupted anyway?, yes, again I know about file permissions, and my own home is totally blocked for any user except myself. 

The user does not have write permissions to the firefox binary. It is possible that a malicious page exploited an unpatched firefox vulnerability to corrupt that user's profile, but not firefox itself. If you're worried about malicious websites, use the noscript addon.
> **juanp.contreras said:**
> 
Also, if there isn't a web server or apache or any service hearing outside, ¿it is possible that some external (not added) user can navigate the file system?
Without a listening service, it is impossible for any remote user to do anything that the local user hasn't initiated, especially navigate the filesystem. If you install an ssh server, then users can authenticate remotely and navigate your filesystem.

---

