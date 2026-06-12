---
title: "sftp (ssh2) Not Working"
date: 2014-05-28
forum: Server Platforms
---

### Post by clalian on 2014-05-28
Hello everyone,
I recently "bought" a small VPS instance, and installed Ubuntu Server 14.04

Very happy with it so far!
I installed apache2.4, and WordPress.
Trying to be proactively secure, I installed a WordPress plugin that permits sftp uploads when you're working on WordPress' Control Panel.
Here is the link: [SSH SFTP Updater Support]("https://wordpress.org/plugins/ssh-sftp-updater-support/").

Now, I'm a server/linux n00b, so I'll try to go over everything I have done.

The problem: When the plugin is active, I enter a new user I created (*newUSER*), and the password I assigned to it.
The plugin errors out.

I created a new group for this user (*newGROUP*).
I then went ahead and did:
chown newUSER:newGROUP plugins/
[Note: plugins/ is the directory where WordPress, and thus the *SSH SFTP Updater Plugin* uploads files to.]

The plugin errors out and throws the error:
> Username/Password incorrect for newUSER.

So, I used KiTTY (PuTTY clone) to ssh into the server using newUSER.
Everything went swell.

The best I have been able to come up with has been by setting the /etc/ssh/sshd_config    LogLevel VERBOSE
Then, I check out the   /var/log/auth.log

When I log in via ssh with newUSER, I get this in auth.log:
> Starting session: shell on pts/5 for myUSER from ip.add.re.ss port 6887

And then it logs into the console just fine.

Now, when I place the information in the WordPress sftp plugin (myUSER and password), I get this:
> Starting session: subsystem 'sftp' for myUSER from ip.add.re.ss port 60048
May 29 04:09:42 server1 sshd[8160]: Received disconnect from ip.add.re.ss: 11:

I can see in the auth.log that myUSER logs in successfully, yet one second after that, it disconnects.
I would guess it has something to do with the *subsystem 'sftp'*?

Any ideas what I can check, or do?

I have googled tons of pages, and I found this one:
[Chroot users with OpenSSH: An easier way to confine users to their home directories]("http://www.techrepublic.com/blog/linux-and-open-source/chroot-users-with-openssh-an-easier-way-to-confine-users-to-their-home-directories/")

It says to add the following lines to /etc/ssh/sshd_config
```
Subsystem     sftp   internal-sftp
Match Group sftp
    ChrootDirectory %h
    ForceCommand internal-sftp
    AllowTcpForwarding no
```
I'm able to add only the very first line:
Subsystem     sftp   internal-sftp

If I add the other ones, and I do
service ssh restart

I can no longer ssh into the server.

Any ideas what I can try/do?

Thank you!!

---

### Post by steeldriver on 2014-05-29
Hello and welcome to the forums 

Using a chrooted jail for sftp requires very specific permissions and ownerships on the user's home directory and the parent directory, and is tricky to get right especially if you want to allow regular ssh login for the same account - I would suggest you focus on getting things working with the default openssh sftp subsystem first i.e. revert to the default /etc/ssh/sshd_config

I know nothing about wordpress, sorry

---

### Post by SeijiSensei on 2014-05-29
I don't know if this matters, but remember that WordPress is running with the permissions of the "www-data" user which owns the Apache server process.  This "user" has limited rights and may not be able to launch SFTP the way you need it to. 

Personally I'd much rather communicate directly with the server rather than going through something like WordPress.

---

### Post by clalian on 2014-05-29
steeldriver and SeijiSensei,
Thank you for your replies!
I'm going to work on this now...
I'll post in a short while what I find/achieve.

---

### Post by clalian on 2014-05-29
Hey guys,
So, I got it working, yet... I'm not sure if what I did was a bad decision.

I went to /var/www
In there I have my html/ 
I did:
chown -R www-data:www-data html/

Now, everything installs and works fine.

What do you think?
It was a permission issue?
And if so... is it secure?
Can I make it more secure?

Thank you for your feedback!

---

### Post by CharlesA on 2014-05-29
That should be fine, just make sure you only give write permission to the appropriate folders.

---

