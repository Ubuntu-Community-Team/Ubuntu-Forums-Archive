---
title: "How to: Completely cripple an user account?"
date: 2007-07-16
forum: Server Platforms
---

### Post by tseven on 2007-07-16
I am taking measures to secure my server.

I have disabled root login via ssh.
Restricted access to open ports via iptables etc.

I would like to remotely login as a trivial user then su to root or other account when needed.

I will restrict ssh login to only this user and want to give the user access to only one command: su

If the user fails the password prompt 3 times then the session is ended (or equivalent).

I've read about using chroot, rbash, and shell menus for restricting a user, all of which have drawbacks and security issues.

How would I go about completely locking a user as I described above?

The idea is,. if -somehow- a deviant was able to login to my server, he/she would have 1 more wall to break down before serious damage can be done.

**I am open to suggestions and advice for other methods as well. **This makes the most sense to me at the moment.

Thanks in advance,
Steve

---

### Post by dfreer on 2007-07-16
Hi!


> **tseven said:**
> If the user fails the password prompt 3 times then the session is ended (or equivalent).
fail2ban can do this, in it's most basic form it monitors SSH logins, and after X amount of failed logins it will ban the IP address for Y amount of time.

---

### Post by Mr. C. on 2007-07-16
> **tseven said:**
> I will restrict ssh login to only this user and want to give the user access to only one command: su


This will be a challenge.  If you use chroot, and only place the su command in the jail, what command will be executed to spawn a shell?  So, we can see that you'll need a shell also.  And once you have a shell, what is the point of logging on remotely, if all you can do is login ?  No ls, no ps, no anything but su.

Hmmm...

A better solution is to disable password authentication, and instead enable public key encryption, and use long passphrases.  This requires both a key and a passphrase, thus giving you two layers.

Don't bother trying to create a hardened environment once logged in - you're only creating needless work for yourself.  If someone manages to a) gain your key, and b) learn your passphrase, your issue is not with a soft system, its weak protection of your confidential data.

MrC

---

### Post by dfreer on 2007-07-16
Yeah, if you are looking for a secure login just so **you** can remotely administrate, you shouldn't need to worry about securing an user account. Although enabling the root account isn't such a good idea, far better to use *sudo su* and have the root account locked.
As for securing SSH, you will probably want to look into what Mr. C said, along with:

[list]
[*]Changing Default Port Number of SSH
[*]Installing fail2ban to cut down on brute force hacks
[*]Using public/private key auth only to also prevent brute force hacks
[*]Keep your private key safe/encrypt private key with a password
[/list]

You shouldn't really allow anyone else SSH access to your box unless you absolutely need to, and if you do we can help batten down the hatches from the inside. The main thing there would be to make sure to use the sudo system, ensure proper file permissions are set, and don't allow the users access to sudo, although it is still a risk.

---

