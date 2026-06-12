---
title: "Login failures after a power cut"
date: 2017-03-15
forum: Server Platforms
---

### Post by dionum on 2017-03-15
The server was accessible via SSH using some specific credentials, including root access. At some point, there was a power failure so the server was suddenly switched off. When the power was restored, the server rebooted but it is not accessible anymore. Although SSH is enabled, the credentials are not working with a  “Permission denied, please try again” error message. When using a console, the system is asking for username and once you enter some valid ‘username’, it keeps going back to username request prompt and not through the password. 
 
Even when boot in “recovery mode”, for some unknown reason it is asking for the root password and once this is entered, it logs in ok. Not sure why it is asking for a password since a physical presence on the machine and via recovery mode it should let you in without password as this is a standard procedure to reset root password.  Anyways, I’ve tried to reset password using the passwd command but it keeps showing “Permission Denied”. I’ve also tried to remove password hashed string from /etc/shadow but still no access.

Looking forward for any advice. I hope I do not have to re-install again the OS.

---

### Post by lisati on 2017-03-15
When you say "root password" do you mean "admin user password"? The "root" user is normally locked by default in Ubuntu.

---

### Post by dionum on 2017-03-15
Yes, the 'roor' user. I know that by default it is locked and you need to unlock in order to gain access remotely. In addition, no other accounts can log in either and I'm running a server Ubuntu 12.04 in case it helps.

---

### Post by lisati on 2017-03-15
The reason that "root" is locked by default on Ubuntu is that using root assumes that you know what you're doing, and it is very easy to accidentally do serious mischief to your system. The preferred method recommended here is to use "sudo" to temporarily grant elevated permissions to your "admin" account.

It has been a while since I've used SSH to access any of my machines, and I never had to unlock root to be able to use it.

12.04 will reach the end of its support life in a month or two, you might want to consider upgrading to a newer release.

---

### Post by dionum on 2017-03-15
Thanks for your recommendations. I understand the reasons why root is locked but this is not the issue here. No user can login either via SSH or from the console (physically attached on the server). The only way to have access is through recovery mode but still asks for password when it shouldn't and yet it accepts these credentials.

---

### Post by volkswagner on 2017-03-15
> **dionum said:**
> The only way to have access is through recovery mode but still asks for password when it shouldn't and yet it accepts these credentials.

Can you explain what you mean 'asks when it shouldn't'?

---

### Post by darkod on 2017-03-16
Once you are in with recovery mode, have you checked logs like auth.log and syslog? Maybe it will have some error messages that can help you troubleshoot why ssh sessions don't work.
Have you checked ssh is actually running, like with telnet from the client machine?

---

### Post by dionum on 2017-03-16
> **darkod said:**
> Once you are in with recovery mode, have you checked logs like auth.log and syslog? Maybe it will have some error messages that can help you troubleshoot why ssh sessions don't work.
Have you checked ssh is actually running, like with telnet from the client machine?

Unfortunately there are no auth.log or syslog as the rsyslogd is not running. And yes, ssh [COLOR=#000000]from a remote machine [/COLOR]it seems to be working as it provides [COLOR=#000000]“Permission denied, please try again” error message.[/COLOR]

---

### Post by darkod on 2017-03-16
There is no logging at all? It doesn't have to be remote logging, once you are logged into the machine you should be able to see its logs.

If not even logs are created it looks like there was some kind of corruption related to the power cut. Did you check that all partitions are mounted correctly?

Also check the .ssh folders and authorized_keys file to make sure they are not corrupted. That could prevent you starting ssh sessions using keys.

If you can't provide any logs or more specific info, it is difficult for us to guess. Many things could have got wrong by unexpected reboot.

For example, if you had /home on separate partition/disk and that is missing, no user will be able to log in because their home will be missing... At least I think so.

---

### Post by dionum on 2017-03-16
> **volkswagner said:**
> Can you explain what you mean 'asks when it shouldn't'?

My misunderstanding  :( ..... All posts that I've read so far, when you are changing root password, mention to go into the recovery mode and enter the root prompt. No instructions say to enter the root password but I've tried it on another server and indeed it asks for one, only if the root login access is enabled. It is strange that only from recovery mode the password works and not from ssh or console when it used to work in the past.

---

### Post by dionum on 2017-03-16
> **darkod said:**
> There is no logging at all? It doesn't have to be remote logging, once you are logged into the machine you should be able to see its logs.

If not even logs are created it looks like there was some kind of corruption related to the power cut. Did you check that all partitions are mounted correctly?

Also check the .ssh folders and authorized_keys file to make sure they are not corrupted. That could prevent you starting ssh sessions using keys.

If you can't provide any logs or more specific info, it is difficult for us to guess. Many things could have got wrong by unexpected reboot.

For example, if you had /home on separate partition/disk and that is missing, no user will be able to log in because their home will be missing... At least I think so.

Root's home folder /root/ and some user's home folder are under the / partition so these are not running on any other disks. Also, there are no authorizes_keys just the known_hosts files under the .ssh folder.

---

### Post by darkod on 2017-03-16
I understood that you are using ssh keys for users, but maybe I understood wrong. Because you wouldn't be able to use ssh keys without authorized_keys file.

I have no ideas really... Try checking the permissions and content of /etc/passwd. Are all the users inside that file as you expect? Also check each user home folder.

You can also try running smart tests on the hdd in case it is corrupted.

---

