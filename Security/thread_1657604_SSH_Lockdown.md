---
title: "SSH Lockdown"
date: 2011-01-01
forum: Security
---

### Post by xathras1982 on 2011-01-01
Hi,
I have locked down my SSH Connections, as per the forum sticky posts. I have one question.
 
If i have a user say joeblogs who then uses sudo -i to root and logs in successfully, is there a way to log the user out after a period of inactivity. I know it can be achieved prior to authentication. But my aim here is to essentially lock out any inactive root ssh sessions.
 
Can this be done?
 
Thanks

---

### Post by jgedeon on 2011-01-01
To continue to lock down sudo add "timestamp_timeout=0 to the Defaults env_reset line in the sudoers file.  This will ensure the at the user is always asked for their password when using sudo.

To enable auto log out when connected complete the two tasks.

Edit /etc/ssh/sshd_config and add the following lines.  Adjusting the timeout, shown as 900 here, to the amount of time you wish.  900 is 15 minutes.

ClientAliveInterval 900
ClientAliveCountMax 0

To automatically log users out that forgot to log out add do the following.

Create the file /etc/profile.d/00-session-logout.sh adding the following content
export TMOUT=900
readonly TMOUT

Then set the permissions
chmod 0644 /etc/profile.d/00-session-logout.sh

Make it so the file can not be changed.
chattr +i /etc/profile.d/00-session-logout.sh

A user that is logged in and sudo -i's to root over ssh will now be completely logged out of the system in 30 minutes.  Users that are logged in on the console will also be logged out.  Users will be asked for their password each time they use the sudo command.

---

### Post by xathras1982 on 2011-01-02
Thanks :)

---

### Post by jgedeon on 2011-01-02
You're welcome.

You mentioned that you locked down your SSH connections from a sticky.  Can you provide a link to the one you used.  I would like to review how they are recommending to lock down SSH.  The ones that I have read here don't really lock down SSH much, IMO.

---

### Post by xathras1982 on 2011-01-02
Hi,
Below is what I've got noted down:
 
[LIST]
[*]Port 22 Changed from Default to 20222 for example.
[*]AllowUsers statement is configured. I allowed the least priveledged account access
[*]and then the user has to sudo to the appropriate level
[*]TCPWrappers is enabled with a /etc/hosts.deny entry as sshd: ALL and a /etc/hosts.allow entry of sshd: 192.168.1.0/255.255.255.0
[*]ServerKeyBits configuration changed from ServerKeyBits 768 to 2048. You'll need to remove your previous keys /bin/rm /etc/ssh/ssh_host_*
[*]PermitRootLogin without-password is enabled instead of Ubuntu Forums recommendation of PermitRootLogin no. This forces root with the ability to only login with an SSH Key
[*]LoginGraceTime default changed from 120 to 20
[*]DenyUsers statement is configured for privledges users. Not required because of
[*]AllowUsers above, but I do it anyway ;-)
[/LIST]

---

### Post by jgedeon on 2011-01-02
> **xathras1982 said:**
> Hi,
Below is what I've got noted down:
 
[LIST]
[*]Port 22 Changed from Default to 20222 for example.
[*]AllowUsers statement is configured. I allowed the least priveledged account access
[*]and then the user has to sudo to the appropriate level
[*]TCPWrappers is enabled with a /etc/hosts.deny entry as sshd: ALL and a /etc/hosts.allow entry of sshd: 192.168.1.0/255.255.255.0
[*]ServerKeyBits configuration changed from ServerKeyBits 768 to 2048. You'll need to remove your previous keys /bin/rm /etc/ssh/ssh_host_*
[*]PermitRootLogin without-password is enabled instead of Ubuntu Forums recommendation of PermitRootLogin no. This forces root with the ability to only login with an SSH Key
[*]LoginGraceTime default changed from 120 to 20
[*]DenyUsers statement is configured for privledges users. Not required because of
[*]AllowUsers above, but I do it anyway ;-)
[/LIST]

[LIST]
[*]Port 22 Changed from Default to 20222 for example.   <-- Security through obscurity.  :(  Firewall policy allowing listed sources to be allowed to access is better.  Network scan will still show the new port as openssh
[*]AllowUsers statement is configured. I allowed the least priveledged account access
[*]and then the user has to sudo to the appropriate level
[*]TCPWrappers is enabled with a /etc/hosts.deny entry as sshd: ALL and a /etc/hosts.allow entry of sshd: 192.168.1.0/255.255.255.0  <-- Firewall policy will do this.
[*]ServerKeyBits configuration changed from ServerKeyBits 768 to 2048. You'll need to remove your previous keys /bin/rm /etc/ssh/ssh_host_*  <-- Agree larger bits better.
[*]PermitRootLogin without-password is enabled instead of Ubuntu Forums recommendation of PermitRootLogin no. This forces root with the ability to only login with an SSH Key  <-- WHAT!  Never allow root ssh access.
[*]LoginGraceTime default changed from 120 to 20  <-- Agree
[*]DenyUsers statement is configured for privledges users. Not required because of
[*]AllowUsers above, but I do it anyway ;-)  <-- AllowUsers is nice when you don't have too many users that need ssh access.
[/LIST]

Thanks for the list.

---

### Post by xathras1982 on 2011-01-02
Thanks for the tip. I'm a bit of a noob. Just reading away and playing around with a VirtualBox and a Ubuntu ISO Image :)

---

### Post by sholdowa on 2011-01-03
In addition to locking down ssh, I'd look at locking down sudo. If you disable sudo su, then you'll end up with an audit log of what that user has done. We all make mistakes, and having an audit trail will aid in rectifying them.

OK, it'll be too late to stop them, but at least you'll be able to work out what's happened...

I must disagree with some of @jgedeon's comments - connecting via ssh using a shared key is perfectly safe as long as you protect your own machine ( if you haven't disabled sudo su, then what's the difference? ). Also using a 2k bit key can make for some really, really long login times.

I don't bother with changing the ssh port - it's only a perceived security improvement. I also use denyhosts to feed /etc/hosts.deny - blacklist the script kiddies!

Finally, it is possible, although still a bit cumbersome, to chroot scp/sftp, which will allow you to completely ditch ftp. This is a major improvement in security.

---

### Post by xathras1982 on 2011-01-03
> **sholdowa said:**
> In addition to locking down ssh, I'd look at locking down sudo. If you disable sudo su, then you'll end up with an audit log of what that user has done. We all make mistakes, and having an audit trail will aid in rectifying them.
 
OK, it'll be too late to stop them, but at least you'll be able to work out what's happened...
 
I must disagree with some of @jgedeon's comments - connecting via ssh using a shared key is perfectly safe as long as you protect your own machine ( if you haven't disabled sudo su, then what's the difference? ). Also using a 2k bit key can make for some really, really long login times.
 
I don't bother with changing the ssh port - it's only a perceived security improvement. I also use denyhosts to feed /etc/hosts.deny - blacklist the script kiddies!
 
Finally, it is possible, although still a bit cumbersome, to chroot scp/sftp, which will allow you to completely ditch ftp. This is a major improvement in security.
 
Thanks. You've mentioned some tips, do you have any links on them?

---

### Post by memihir on 2012-08-20
Hi, 

Can you please tell me how did you lockdown SSH as i am newbie.

Thanks



> **xathras1982 said:**
> Hi,
I have locked down my SSH Connections, as per the forum sticky posts. I have one question.
 
If i have a user say joeblogs who then uses sudo -i to root and logs in successfully, is there a way to log the user out after a period of inactivity. I know it can be achieved prior to authentication. But my aim here is to essentially lock out any inactive root ssh sessions.
 
Can this be done?
 
Thanks

---

### Post by CharlesA on 2012-08-21
> **memihir said:**
> Hi, 

Can you please tell me how did you lockdown SSH as i am newbie.

Thanks

Read this:

> **xathras1982 said:**
> Hi,
Below is what I've got noted down:
 
[LIST]
[*]Port 22 Changed from Default to 20222 for example.
[*]AllowUsers statement is configured. I allowed the least priveledged account access
[*]and then the user has to sudo to the appropriate level
[*]TCPWrappers is enabled with a /etc/hosts.deny entry as sshd: ALL and a /etc/hosts.allow entry of sshd: 192.168.1.0/255.255.255.0
[*]ServerKeyBits configuration changed from ServerKeyBits 768 to 2048. You'll need to remove your previous keys /bin/rm /etc/ssh/ssh_host_*
[*]PermitRootLogin without-password is enabled instead of Ubuntu Forums recommendation of PermitRootLogin no. This forces root with the ability to only login with an SSH Key
[*]LoginGraceTime default changed from 120 to 20
[*]DenyUsers statement is configured for privledges users. Not required because of
[*]AllowUsers above, but I do it anyway ;-)
[/LIST]

Also:
[https://help.ubuntu.com/10.04/serverguide/openssh-server.html](https://help.ubuntu.com/10.04/serverguide/openssh-server.html)
[http://www.debian-administration.org/articles/87](http://www.debian-administration.org/articles/87)

If you have any other questions, please start a new thread as this one is over a year and a half old.

---

