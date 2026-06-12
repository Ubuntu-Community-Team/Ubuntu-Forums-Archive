---
title: "rsync automated backups of entire file structure over ssh"
date: 2011-05-16
forum: Security
---

### Post by tnt533 on 2011-05-16
I am in the process of writing an rsync script to run unattended backups of my entire file system to another system located on my local network using ssh and password-less rsa keys. 

I will absolutely **_*will not*_** use password-less keys with the root account and this is the limitation preventing me from accomplishing my goal because root is required by rsync to access the / tree and copy it to another location. 

I decided that if I compiled the script into a binary that I didn't have a problem with the password being contained within the binary itself but from what I've read there is no way to elevate to root and then back down to user level from within the script/binary. I can create the script as the user and use chroot to make it owned by root but retain execution permission for the user but it will still cause the ssh login to be under root and therefore require either that I am there to enter my password or the use of password-less keys under the root account which I reiterate I will NOT do.

Currently the script is executed by the user on the machine containing the files to be backed up.

Any ideas?

---

### Post by HermanAB on 2011-05-17
Howdy,

There are two solutions:
1. Get over your mental block regarding passwordless keys.
2. Use ssh-agent.

Option one is much less painful.

---

### Post by Lars Noodén on 2011-05-17
You can use [sudo with rsync and ssh](http://en.wikibooks.org/wiki/OpenSSH/Cookbook/Automated_Backup#Backup_with_rsync_and_sudo) to get the whole system without having to give away everything.  Sudo can be quite locked down.  To see what parameters need to get entered in /etc/sudoers look at ssh in verbose mode (ssh -vv)

---

### Post by tnt533 on 2011-05-17
> **Lars Noodén said:**
> You can use [sudo with rsync and ssh](http://en.wikibooks.org/wiki/OpenSSH/Cookbook/Automated_Backup#Backup_with_rsync_and_sudo) to get the whole system without having to give away everything.  Sudo can be quite locked down.  To see what parameters need to get entered in /etc/sudoers look at ssh in verbose mode (ssh -vv)

Sudo will still require input in the form of a password though, right? I can run the script just fine if I use sudo and am at the machine when it executes but the goal is unattended use of the script with a cron job using elevated permissions without compromising security. I could set up a root cron job but then the script will be logging in through ssh as root and subsequently require credentials set up for the root account and I can't do that. It needs to log in to the remote machine as the user but execute the rsync command as root so it has the needed permissions to copy the / of the drive. 

As far as I've been able to determine you can't elevate to root from within a script unattended. 

Could you please elaborate a little on your idea?

---

### Post by tnt533 on 2011-05-17
> **HermanAB said:**
> Howdy,

There are two solutions:
1. Get over your mental block regarding passwordless keys.
2. Use ssh-agent.

Option one is much less painful.

Is ssh-agent really more secure than password-less keys considering that once you unlock the keys at the beginning of your session they stay unlocked until you logout or reboot? Wouldn't that still allow anyone who gains root on machine one access as root on the other machine though ssh?

---

### Post by Lars Noodén on 2011-05-17
> **tnt533 said:**
> Sudo will still require input in the form of a password though, right? 

Not if the line in /etc/sudoers is configured (carefully) to skip the password.  It's possible and easy (once you know) to elevate to root from an unattended script.

Sudo can be configured to not need a password.  Ideally this is done by defining *very* specifically how to do one single task.  

So you have one user for this one task.  If you need a user, make one. [Keys can be locked to a single task](http://en.wikibooks.org/wiki/OpenSSH/Cookbook/Key-based_Authentication#Single-purpose_keys).  You connect using locked down, passwordless keys as that user and then use locked down, passwordless sudo to run exactly one script.  The exact string to put in the key and in sudo must be worked out in detail using **ssh -v** 

Steps:

1. make a user
2. lock the key down
3. detail exact string for /etc/sudoers

---

### Post by tnt533 on 2011-05-17
> **Lars Noodén said:**
> Not if the line in /etc/sudoers is configured (carefully) to skip the password.  It's possible and easy (once you know) to elevate to root from an unattended script.

Sudo can be configured to not need a password.  Ideally this is done by defining *very* specifically how to do one single task.  

So you have one user for this one task.  If you need a user, make one. [Keys can be locked to a single task](http://en.wikibooks.org/wiki/OpenSSH/Cookbook/Key-based_Authentication#Single-purpose_keys).  You connect using locked down, passwordless keys as that user and then use locked down, passwordless sudo to run exactly one script.  The exact string to put in the key and in sudo must be worked out in detail using **ssh -v** 

Steps:

1. make a user
2. lock the key down
3. detail exact string for /etc/sudoers

Great information! Thank you for the point in the right direction and elaborating on your first post. I guess I don't have to get over my "mental block" after all.

---

### Post by Lars Noodén on 2011-05-17
> **tnt533 said:**
> Great information! Thank you for the point in the right direction and elaborating on your first post. I guess I don't have to get over my "mental block" after all.

No worries.  Here is more in [presentation on sudo](http://www.bsdly.net/~lars/Lectures/Network-2a-sudo.odp) that helps explain what it can do.  sudo is very underutilized and usually misused.

---

### Post by bodhi.zazen on 2011-05-17
Additional options:

1. Use a task specific key, with no password, but instead use forced commands.

[http://troy.jdmz.net/rsync/index.html](http://troy.jdmz.net/rsync/index.html)

[http://oreilly.com/catalog/sshtdg/chapter/ch08.html](http://oreilly.com/catalog/sshtdg/chapter/ch08.html)

You can use additional options to secure the key including no-ptty, no-agent-forwarding, etc.

2. Use sudo, but configure sudo to allow the requite commands with no password.

3. Script it with expect.

---

### Post by tnt533 on 2011-05-18
Thank you both for the great information. I've got it sorted out now. The balance between security and usability is a constant tug-o-war isn't it.

---

### Post by Lars Noodén on 2011-05-18
> **tnt533 said:**
> Thank you both for the great information. I've got it sorted out now. The balance between security and usability is a constant tug-o-war isn't it.

It's easy once you know how.  :)

---

### Post by tnt533 on 2011-05-18
> **Lars Noodén said:**
> It's easy once you know how.  :)

Agreed. Maybe I should have said security vs convenience. Thanks again guys.

---

