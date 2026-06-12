---
title: "Was i hacked???"
date: 2008-09-21
forum: Security
---

### Post by GmAz on 2008-09-21
Ok, last night I come in my office to shut down my machine, and I notice that it has been used.  Mind you, I am the only one that uses this machine.  My wife doesn't use it because she doesn't know Linux.  Neither do I really, I just wanted a 'maintenance free' OS for home.  I no longer game on my PC so I figured Linux would be fun to have finally.  Anywho, I come in my office and I have two terminal windows open, and Firefox is open ith my router config page open.  Last thing I did on my PC was check a website (slickdeals.net) and then that was it.  Here are a list of commands that were put in the terminal windows:

ssh localhost -k mysqld
service
services
sudo
sudo su
exit
cat /etc/ssh/sshd_config
ssh localhost
nc -lvvp 31337
ifconfig
ping 192.168.*.* (hiding my local IP to my router)
ping 192.168.*.** (different IP)

There is now a new user called mysqld that wasn't there before.  

When I do cat /etc/ssh/sshd_config, there is this line:  
# What ports, IPs and protocols we listen for
Port 2200

When my router page was open, someone had set port 2200 to be forwarded to my desktop.  I turned off that port forwarding, and the one port I was intentionally forwarding.  I have also turned off remote access.  I use it at work to get to my home PC, but will no longer be doing that.

Should I be concerned (which I already am) and how can I tell if my machine is being used for malicious intentions?  I really don't feel like re-installing Ubuntu to make sure my system is clean.  Also, this is kind of annoying because I have used Windows for years, and was a very early adopter of Vista (which I have had zero issues with) and only went to Ubuntu to see how it is.  I have never had an issue like this on Windows and I had many ports open, and different servers running.  I have Ubuntu for a month and this happens.  This really does diminish the whole "Linux is a very secure OS" image that Linux is wanting people to believe it has.

Also, Ubuntu is 100% updated.  I do have GUFW Firewall installed.  My one bad thing is I had the computer auto log in my account, and I had my router's login password saved in FireFox.  It is no longer saved...and my account no longer auto logins.  Remote access is turned off as well.  All open ports have been closed and hearing from you guys is my last step before going back to windows, which I don't want to do.  I have no problems with Windows, but considering all i do on my desktop anymore is e-mail, and manage my digital photos, I see no reason to have to have windows.  And I really don't feel like buying a new anti-virus.  Yes, I'm cheap.  

Please advise me on a course of action so I can see if my machine is vulnerable.  

--Giuliano

---

### Post by pytheas22 on 2008-09-21
I admit that I'm not positive what could be going on, but I don't think you need to worry.  If someone hacks your machine remotely, they're not going to open up a terminal window and run commands in it to further hack the machine.  They would run all those commands in a separate shell running in the background, unless they're trying to scare you.

I'd really suspect that someone was in your office physically doing this.  Are you sure your wife didn't touch the computer?

Also, if you're behind a router, that makes it even more unlikely that someone hacked you from the public Internet, unless you have lots of ports open and forwarded to your Ubuntu machine.  Which ports were open on your router, and what services did you have running on it?  Did you have VNC or ssh running?

You should note that it does look like whoever was at the computer was able to login with your password to become root, using sudo.  Is there anyone who would know your password?

If you have a lot of common ports open, there are bots that crawl around the Internet trolling for weak passwords on certain services, like ssh.  Generally these pose no threat, but if you have a really weak password and a guessable username, they could conceivably have gotten into your machine.  That still doesn't explain why they'd run commands in graphical terminals, though.

If you type:
```

gedit /var/log/auth.log
```

a file will open showing you all users who have logged into your computer recently, allowing with the time and duration of the log in.  Are there any logins that don't make sense (keep in mind of course that in the unlikely event that you have been hacked, the hacker could have changed the auth.log file to hide his intrusion...but if he's running commands in a graphical terminal, it doesn't seem like he's try to hide much)?

---

### Post by GmAz on 2008-09-21
Yes, I am sure it wasn't my wife.  Shes right next to me and snickered when she read that line.  Also, no one was in my house yesterday but the two of us and my 2 year old, and though she is pretty savvy on the computer, shes two...  =).  

The only port I had open was 5900.  It was for VNC.  That has been closed, and remote access is now disabled.  

For my password, its not super strong, but its also not weak.  Only a couple of people know my password.  My wife and my Dad.  And my dad has no idea what Linux even is.

I am not sure if SSH was running.  I've never used it, nor turned it on.  Does SSH come running when you install Ubuntu?

I've since changed all my passwords.  Made them a little more secure.  Special characters, numbers, and what not. 

I'll keep an eye on my machine.  I don't have to keep it running all day now since VNC is shut down.  

I'll run that command now and see what the log has to say.  Thanks.

---

### Post by GmAz on 2008-09-21
Ok, here is my log.  I have replaced all my username entries with ****.

Sep 20 00:17:01 office CRON[25997]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 00:17:01 office CRON[25997]: pam_unix(cron:session): session closed for user root
Sep 20 01:17:01 office CRON[26901]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 01:17:01 office CRON[26901]: pam_unix(cron:session): session closed for user root
Sep 20 02:17:01 office CRON[27804]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 02:17:01 office CRON[27804]: pam_unix(cron:session): session closed for user root
Sep 20 03:17:01 office CRON[28708]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 03:17:01 office CRON[28708]: pam_unix(cron:session): session closed for user root
Sep 20 04:17:01 office CRON[29612]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 04:17:01 office CRON[29612]: pam_unix(cron:session): session closed for user root
Sep 20 05:17:01 office CRON[30516]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 05:17:01 office CRON[30516]: pam_unix(cron:session): session closed for user root
Sep 20 06:17:01 office CRON[31420]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 06:17:01 office CRON[31420]: pam_unix(cron:session): session closed for user root
Sep 20 06:25:01 office CRON[31543]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 06:25:01 office CRON[31543]: pam_unix(cron:session): session closed for user root
Sep 20 07:17:01 office CRON[32325]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 07:17:01 office CRON[32325]: pam_unix(cron:session): session closed for user root
Sep 20 07:30:01 office CRON[32524]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 07:30:02 office CRON[32524]: pam_unix(cron:session): session closed for user root
Sep 20 07:35:04 office sudo:     root : TTY=unknown ; PWD=/ ; USER=**** ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/use_http_proxy
Sep 20 07:35:04 office sudo: pam_unix(sudo:session): session opened for user **** by (uid=0)
Sep 20 07:35:04 office sudo: pam_unix(sudo:session): session closed for user ****
Sep 20 07:35:04 office sudo:     root : TTY=unknown ; PWD=/ ; USER=**** ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/host
Sep 20 07:35:04 office sudo: pam_unix(sudo:session): session opened for user **** by (uid=0)
Sep 20 07:35:04 office sudo: pam_unix(sudo:session): session closed for user ****
Sep 20 07:35:04 office sudo:     root : TTY=unknown ; PWD=/ ; USER=**** ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/port
Sep 20 07:35:04 office sudo: pam_unix(sudo:session): session opened for user **** by (uid=0)
Sep 20 07:35:04 office sudo: pam_unix(sudo:session): session closed for user ****
Sep 20 08:17:01 office CRON[1032]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 08:17:01 office CRON[1032]: pam_unix(cron:session): session closed for user root
Sep 20 09:17:01 office CRON[1951]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 09:17:01 office CRON[1951]: pam_unix(cron:session): session closed for user root
Sep 20 10:17:01 office CRON[2868]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 10:17:01 office CRON[2868]: pam_unix(cron:session): session closed for user root
Sep 20 11:17:01 office CRON[3780]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 11:17:01 office CRON[3780]: pam_unix(cron:session): session closed for user root
Sep 20 12:17:01 office CRON[4685]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 12:17:01 office CRON[4685]: pam_unix(cron:session): session closed for user root
Sep 20 13:17:01 office CRON[5604]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 13:17:01 office CRON[5604]: pam_unix(cron:session): session closed for user root
Sep 20 14:17:01 office CRON[6663]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 14:17:01 office CRON[6663]: pam_unix(cron:session): session closed for user root
Sep 20 15:17:01 office CRON[7572]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 15:17:01 office CRON[7572]: pam_unix(cron:session): session closed for user root
Sep 20 16:17:01 office CRON[8481]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 16:17:01 office CRON[8481]: pam_unix(cron:session): session closed for user root
Sep 20 17:17:01 office CRON[9385]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 17:17:01 office CRON[9385]: pam_unix(cron:session): session closed for user root
Sep 20 18:17:01 office CRON[10289]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 18:17:01 office CRON[10289]: pam_unix(cron:session): session closed for user root
Sep 20 19:17:01 office CRON[11193]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 19:17:01 office CRON[11193]: pam_unix(cron:session): session closed for user root
Sep 20 20:17:01 office CRON[12097]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 20:17:01 office CRON[12097]: pam_unix(cron:session): session closed for user root
Sep 20 21:17:01 office CRON[13003]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 21:17:01 office CRON[13003]: pam_unix(cron:session): session closed for user root
Sep 20 22:17:01 office CRON[13905]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 22:17:01 office CRON[13905]: pam_unix(cron:session): session closed for user root
Sep 20 23:17:01 office CRON[14809]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 20 23:17:01 office CRON[14809]: pam_unix(cron:session): session closed for user root
Sep 21 00:17:01 office CRON[15717]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 21 00:17:01 office CRON[15717]: pam_unix(cron:session): session closed for user root
Sep 21 00:28:35 office sudo: pam_unix(sudo:auth): authentication failure; logname=**** uid=0 euid=0 tty=/dev/pts/0 ruser= rhost=  user=****
Sep 21 00:28:43 office sudo: pam_unix(sudo:auth): conversation failed
Sep 21 00:28:43 office sudo: pam_unix(sudo:auth): auth could not identify password for [****]
Sep 21 00:28:43 office sudo:     **** : pam_authenticate: Conversation error ; TTY=pts/0 ; PWD=/home/**** ; USER=root ; COMMAND=/usr/bin/id
Sep 21 00:30:09 office sudo: pam_unix(sudo:auth): authentication failure; logname=**** uid=0 euid=0 tty=/dev/pts/0 ruser= rhost=  user=****
Sep 21 00:30:18 office sudo:     **** : TTY=pts/0 ; PWD=/home/**** ; USER=root ; COMMAND=/usr/bin/id
Sep 21 00:30:18 office sudo: pam_unix(sudo:session): session opened for user root by ****(uid=0)
Sep 21 00:30:18 office sudo: pam_unix(sudo:session): session closed for user root
Sep 21 00:30:40 office sudo:     **** : TTY=pts/0 ; PWD=/home/**** ; USER=root ; COMMAND=/bin/su
Sep 21 00:30:40 office sudo: pam_unix(sudo:session): session opened for user root by ****(uid=0)
Sep 21 00:30:40 office sudo: pam_unix(sudo:session): session closed for user root
Sep 21 00:30:40 office su[15976]: Successful su for root by root
Sep 21 00:30:40 office su[15976]: + pts/0 root:root
Sep 21 00:30:40 office su[15976]: pam_unix(su:session): session opened for user root by ****(uid=0)
Sep 21 00:31:01 office groupadd[15998]: new group: name=mysqld, GID=1001
Sep 21 00:31:01 office useradd[15999]: new user: name=mysqld, UID=1001, GID=1001, home=/home/mysqld, shell=/bin/bash
Sep 21 00:31:06 office passwd[16002]: pam_unix(passwd:chauthtok): password changed for mysqld
Sep 21 00:31:09 office chfn[16004]: changed user `mysqld' information
Sep 21 00:31:13 office chfn[16006]: changed user `mysqld' information
Sep 21 00:32:05 office su[15976]: pam_unix(su:session): session closed for user root
Sep 21 00:38:41 office sudo:     **** : TTY=pts/0 ; PWD=/home/**** ; USER=root ; COMMAND=/bin/su
Sep 21 00:38:41 office sudo: pam_unix(sudo:session): session opened for user root by ****(uid=0)
Sep 21 00:38:41 office sudo: pam_unix(sudo:session): session closed for user root
Sep 21 00:38:41 office su[16181]: Successful su for root by root
Sep 21 00:38:41 office su[16181]: + pts/0 root:root
Sep 21 00:38:41 office su[16181]: pam_unix(su:session): session opened for user root by ****(uid=0)
Sep 21 00:39:39 office useradd[16298]: new user: name=sshd, UID=112, GID=65534, home=/var/run/sshd, shell=/usr/sbin/nologin
Sep 21 00:39:40 office usermod[16299]: change user `sshd' password
Sep 21 00:39:40 office chage[16300]: changed password expiry for sshd
Sep 21 00:39:40 office sshd[16338]: Server listening on :: port 22.
Sep 21 00:39:40 office sshd[16338]: error: Bind to port 22 on 0.0.0.0 failed: Address already in use.
Sep 21 00:42:07 office sshd[16406]: Accepted password for mysqld from 127.0.0.1 port 35107 ssh2
Sep 21 00:42:08 office sshd[16409]: pam_unix(sshd:session): session opened for user mysqld by mysqld(uid=0)
Sep 21 00:42:12 office su[16181]: pam_unix(su:session): session closed for user root
Sep 21 00:43:55 office sudo:     **** : TTY=pts/0 ; PWD=/home/**** ; USER=root ; COMMAND=/bin/su
Sep 21 00:43:55 office sudo: pam_unix(sudo:session): session opened for user root by ****(uid=0)
Sep 21 00:43:55 office sudo: pam_unix(sudo:session): session closed for user root
Sep 21 00:43:55 office su[16466]: Successful su for root by root
Sep 21 00:43:55 office su[16466]: + pts/0 root:root
Sep 21 00:43:55 office su[16466]: pam_unix(su:session): session opened for user root by ****(uid=0)
Sep 21 01:02:12 office sshd[16338]: Received signal 15; terminating.
Sep 21 01:02:16 office sshd[16900]: [COLOR="Lime"]Server listening on :: port 2200.[/COLOR]
Sep 21 01:02:16 office sshd[16900]: error: Bind to port 2200 on 0.0.0.0 failed: Address already in use.
Sep 21 01:11:53 office polkit-grant-helper[17084]: granted authorization for org.freedesktop.systemtoolsbackends.set to pid 17064 [uid=1000] [auth=****]
Sep 21 01:13:09 office su[16466]: pam_unix(su:session): session closed for user root
Sep 21 01:14:26 office sshd[5672]: Server listening on :: port 2200.
Sep 21 01:14:26 office sshd[5672]: error: Bind to port 2200 on 0.0.0.0 failed: Address already in use.
Sep 21 01:14:35 office gdm[6179]: pam_unix(gdm-autologin:session): session opened for user **** by (uid=0)
Sep 21 01:17:01 office CRON[6744]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep 21 01:17:01 office CRON[6744]: pam_unix(cron:session): session closed for user root
Sep 21 01:18:10 office polkit-grant-helper[6805]: granted authorization for org.freedesktop.systemtoolsbackends.set to pid 6773 [uid=1000] [auth=****]
Sep 21 01:18:25 office polkit-grant-helper[6822]: granted authorization for org.freedesktop.systemtoolsbackends.set to pid 6812 [uid=1000] [auth=****]
Sep 21 01:19:33 office sudo:     root : TTY=unknown ; PWD=/ ; USER=**** ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/use_http_proxy
Sep 21 01:19:33 office sudo: pam_unix(sudo:session): session opened for user **** by (uid=0)
Sep 21 01:19:33 office sudo: pam_unix(sudo:session): session closed for user ****
Sep 21 01:19:33 office sudo:     root : TTY=unknown ; PWD=/ ; USER=**** ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/host
Sep 21 01:19:33 office sudo: pam_unix(sudo:session): session opened for user **** by (uid=0)
Sep 21 01:19:33 office sudo: pam_unix(sudo:session): session closed for user ****
Sep 21 01:19:33 office sudo:     root : TTY=unknown ; PWD=/ ; USER=**** ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/port
Sep 21 01:19:33 office sudo: pam_unix(sudo:session): session opened for user **** by (uid=0)
Sep 21 01:19:33 office sudo: pam_unix(sudo:session): session closed for user ****
Sep 21 01:42:26 office gdm[6179]: pam_unix(gdm-autologin:session): session closed for user ****

No one was in my office (home office) from at all yesterday.  I checked one website when i woke up (around 7am) and my computer was on the rest of the day with my monitor off as it usually is.  

All of the stuff in the log above was done externally.

As mentioned in my last post, port 5900 was open for VNC, but no longer is.

The green text also concerns me since my router had a new port forwarding for it to port 2200.  And from the commands in my first port, it looks like someone was either turning on or using SSH on port 2200.

---

### Post by calraith on 2008-09-21
First thing, if you suspect your machine might've been compromised, change your user and root passwords, and make sure ~/.ssh/authorized_keys doesn't have anything you didn't add yourself.
```
passwd
cat ~/.ssh/authorized_keys
sudo su
passwd
cat ~/.ssh/authorized_keys
```You should also delete the mysqld account.  That's probably not legitimate.
```
sudo userdel mysqld
```Looks like the "sshd" user account password was also changed.  Keep the account, but make sure it's still set not to use any shell.
```
grep sshd /etc/passwd
```The output of that should be similar to mine, which appears as follows: sshd:x:111:65534::/var/run/sshd:/usr/sbin/nologin

Make sure all the security updates have been installed, and reboot if your machine recommends it.
```
sudo apt-get update
sudo apt-get dist-upgrade
```Next, install and run chkrootkit.  It's in the repos.  It does what the name implies -- checks for root kits which might've been installed if your machine was cracked.

If you're going to run sshd, it wouldn't be a bad idea to install fail2ban.  It's also in the repos.  After installing it, salt /etc/fail2ban/jail.conf to taste and sudo /etc/init.d/fail2ban restart.  After restarting fail2ban, sudo fail2ban-client status to make sure you didn't make any errors in fail2ban's config file.

Finally, if you know you're only going to be remotely accessing your machine from a specific range of addresses, you could add those addresses to /etc/hosts.allow, and deny everything else.  Example:

```
# hosts.allow example file -- man hosts_access for more info

# Your work has all IP addresses in the range of 123.456.*.*
ALL : 123.456.0.0/16
ALL : .yourworkdomain.com

# Your home network has IP addresses in the range of 192.168.1.*
ALL : 192.168.1.0/24, 127.0.0.0/8

# Deny everything else
ALL : ALL : deny
```That way even if your machine has been compromised, the perpetrator will either have to be at your work or in your house to make further connections to any service that uses tcpwrappers (including SSH).

---

### Post by GmAz on 2008-09-22
> **calraith said:**
> First thing, if you suspect your machine might've been compromised, change your user and root passwords, and make sure ~/.ssh/authorized_keys doesn't have anything you didn't add yourself.

You should also delete the mysqld account.  That's probably not legitimate.
```
sudo userdel mysqld
```

Make sure all the security updates have been installed by doing sudo apt-get update and sudo apt-get dist-upgrade.

Next, install and run chkrootkit.  It's in the repos.  It does what the name implies -- checks for root kits which might've been installed if your machine was cracked.

If you're going to run sshd, it wouldn't be a bad idea to install fail2ban.  It's also in the repos.  After installing it, salt /etc/fail2ban/jail.conf to taste and sudo /etc/init.d/fail2ban restart.  After restarting fail2ban, sudo fail2ban-client status to make sure you didn't make any errors in fail2ban's config file.

Finally, if you know you're only going to be remotely accessing your machine from a specific range of addresses, you could add those addresses to /etc/hosts.allow, and deny everything else.  Example:

```
# hosts.allow example file -- man hosts_access for more info

# Your work has all IP addresses in the range of 123.456.*.*
ALL : 123.456.0.0/16
ALL : .yourworkdomain.com

# Your home network has IP addresses in the range of 192.168.1.*
ALL : 192.168.1.0/24, 127.0.0.0/8

# Deny everything else
ALL : ALL : deny
```That way even if your machine has been compromised, the perpetrator will either have to be at your work or in your house to make further connections to any service that uses tcpwrappers (including SSH).

Thanks!  Yes, I only remote to my PC from work and from my own home network. 

I am however not planning on running SSHD.  How do I turn it off?

I have fail2ban installed and it appears to be working. Do I need to edit the conf any or will the default work fine?  I'll add my companies IP addresses tomorrow when I get them from work.  Luckily I have them.  I work in the IT department, but we don't utilize Linux there.  Windows only.

Also, I was fully up to date.  Being a windows user for so long, I am somewhat used to making sure I am fully up to date.

Also, the root account is there too.  Can I delete it?  I don't see a reason to have it for the uses I do on my machine.  sudo works fine for me.  Can I delete it and forget about it?

cat ~/.ssh/authorized_keys

Under my account and root, both came up as "file or folder not found"  I'm assuming thats fine.

[[EDIT]]

Ran chkrootkit.  everything came up as 'nothing found' or 'not infected'.  However, a couple had permission denied:

Searching for anomalies in shell history files... /usr/bin/find: //home/****/.gvfs: Permission denied
/usr/bin/find: //home/****/.gvfs: Permission denied
nothing found

Both permission denied were in my home folder.  Is that ok?

---

### Post by cariboo on 2008-09-22
There are no external ip addresses in your listing, I don't think anybody would delete the ip addresses and not get rid of the rest of the commands in the log. It looks like all the activity took place between 00:28 and 01:42. It really looks like someone accessed your computer from your office.

Jim

---

### Post by calraith on 2008-09-22
> **GmAz said:**
> Thanks!  Yes, I only remote to my PC from work and from my own home network. 

I am however not planning on running SSHD.  How do I turn it off?

I have fail2ban installed and it appears to be working. Do I need to edit the conf any or will the default work fine?  I'll add my companies IP addresses tomorrow when I get them from work.  Luckily I have them.  I work in the IT department, but we don't utilize Linux there.  Windows only.

Also, I was fully up to date.  Being a windows user for so long, I am somewhat used to making sure I am fully up to date.

Fail2ban comes configured out of the box to protect sshd.  If you have other services you want to protect, such as ftp, you have to edit the conf file.  However, if you're not going to run any services, you can just remove fail2ban and openssh-server.

For what it's worth, I find it MUCH more secure (with better compression as an added bonus) to tunnel VNC over SSH, and deny direct VNC access without the tunnel.  In my experience VNC open to the Internet isn't terribly secure.  To be honest, I'm not even sure that authentication failures for VNC are logged by the syslog daemon.  I've seen many Windows servers rooted via VNC, and Linux isn't much different.  That's likely how your machine was compromised, making it appear that it was cracked from in front of the keyboard.

Sorry about my previous post.  I think I edited it a few times while you were responding.  I'll leave this one alone.

---

### Post by calraith on 2008-09-22
One other thought, it's likely that whoever got into your machine installed an IRC zombie.  Do a netstat | grep irc and see whether there are any connections from your machine to a chat network.

I've got to hit the hay.  If you don't get this figured out, leave your machine off or unplug its network cable till we have more time to investigate.  :)

---

### Post by GmAz on 2008-09-22
Do you have a page that can tell me step by step to route VNC through SSH.  ALso, there was positively no one in my office at all.  Its kind of hard for someone to be in there if I'm sitting in the living room and I can see the door from my couch.  Plus, I was up til about 2:30 that night and so I am very sure no one even came in my house.

I would have to say it was through VNC.  I'm sorry, but there is no other way.  My router's log shows no other logins espically since I use MAC address filtering for wireless connections and all my wired connections are filled.  Wii, Xbox360, Printer and my desktop.  And the router is in my vision under my TV.

There is so much to learn about Linux, and though I am picking it up, theres just a lot to learn still. 

I have no problems configuring the system and then just letting it run.

The only service I plan on running is VNC, if that is even considered a service.  I do like having access to my computer from work.  Our internet is strictly filtered and at times I need to check forums for information and all web forums are blocked (I work for a K-12 school district so it has to be strict).  But remoting to home and using my own internet is a handy 'work around'.  Its slow, but useable for a lot of text.

[[EDIT]]

netstat | grep irc came up empty.  No results listed.

Thanks for the replies.  Hope to hear back from you tomorrow, hopefully with a site or threat that has instructions for tunneling vnc through ssh.

---

### Post by pytheas22 on 2008-09-22
An ssh server was definitely installed on your machine at some point, and set up to listen on port 2200, which is a bit strange (default ssh port is 22).  An ssh server is not installed by default in Ubuntu desktop edition (it is in the server edition I think, but you're not using that, right?), so if you didn't put it there or install any software that would want to run an ssh server, then something strange must be going.

I guess it's possible that one of these script kiddies happened to port scan your router, see that a VNC server was running, attacked it and got in.  That's the only way I can think that this would have happened, if your sure that there was absolutely no physical access to the machine, and VNC was the only service running.

The steps suggested by the other posters are good for containing this attack, although if I were you I'd probably just reinstall Ubuntu completely now, and make sure to use a really strong VNC password.  I would also unplug the Ubuntu computer from the network so that it can't be used to attack your other computers.
> 
Do you have a page that can tell me step by step to route VNC through SSH. ALso, there was positively no one in my office at all. Its kind of hard for someone to be in there if I'm sitting in the living room and I can see the door from my couch. Plus, I was up til about 2:30 that night and so I am very sure no one even came in my house.

What do you mean?  VNC and ssh are separate protocols and services.  You can use ssh to forward a graphical desktop over a remote connection, like VNC does, and ssh is way more secure than VNC, but I'm not sure what exactly you want to do.

By the way, sorry this happened; it is pretty extraordinary to hear of an Ubuntu machine getting compromised like this.  If it was just some VNC script kiddie, there's not much that Windows or Linux could have done to stop him, if your password wasn't secure.  VNC is not a particularly secure protocol--after all, with maximum passwords of eight characters, brute-forcing is a real possibility even if you did choose a good password and someone wanted to get in badly enough--but mostly I think this just comes down to bad luck.

Linux *is* much more secure than Windows from the standpoint of trojans and other malware that are introduced through browser vulnerabilities, email attachments, bugs in certain Windows applications, etc.  These kinds of exploits are very different from someone hacking into your VNC server, which isn't a virus or malware at all--it's an active attack against your machine by an individual targeting you individually.  Neither Linux nor Windows can claim to be any more secure against such an attack--if someone wants in badly enough and is able to find a hole like an unsecured VNC server, he'll be able to get in.

Whether Linux's effective immunity on the malware front is due to its low market share or better system design is a debatable topic, but few people would argue that the likelihood of your Linux machine being compromised by a malicious email attachment or clicking a bad link in Firefox is almost nil, in comparison to Windows, where these things are a fact of life even for smart users.  So I hope that this doesn't turn you off to Linux.

---

### Post by airtonix on 2008-09-22
gmaz, 
you mention using vnc remotley? 
is the remote location secure when you use vnc? 
are you tunneling vnc through ssh to make sure noone between your remote and home connection are sniffing your passwords?
do you lock your screen when not at your computer?

since you changed the port forwarding to none...risk is gone for now. unless the above points have been addressed it may happen again.

basically i am saying your personal security habits are not that good...and the fact that you never experienced this on windows...well how can you be sure? windows is even less verbose about certains aspects unless you purchase extra software.

---

### Post by tarun.winlin on 2008-09-22
Here is a nice writeup to tunnel VNC over SSH:
[http://www.erikjheels.com/?p=470](http://www.erikjheels.com/?p=470)

With SSH, even if you intend to use it, use it with RSA authentication, never use open passwords.

Try to tunnel as much traffic as you can through SSH, to an extent that the only open port to the world is SSH.

Set SSH port to something random.

---

### Post by RavUn on 2008-09-22
Is it possible to use keys when you're sshing from a Windows computer to a Ubuntu server?  I've read how to setup keys but it was for linux to linux.

---

### Post by tarun.winlin on 2008-09-22
Yup, you can very well do it. I manage my home computer which is linux box from my office laptop which is windows.
The procedure is also the same, I use putty as the client on windows.

---

### Post by calraith on 2008-09-22
> **GmAz said:**
> Thanks for the replies.  Hope to hear back from you tomorrow, hopefully with a site or threat that has instructions for tunneling vnc through ssh.

I think the tutorial mentioned earlier might be a bit confusing, as it focuses on setting up an sshd and hosting VNC on Windows via cygwin.  A quick Google search turned up [this page]("http://home.chattanooga.net/%7Ejohn/Putty-Tunnel/putty-tunnel.html") which trims the fat and focuses primarily on setting up PuTTY on your work machine to establish the tunnel.

At home I have port 22 as the only open port.  I run fail2ban to prevent dictionary attacks.  (FWIW, I've also set up a honeypot so that any machines that try to brute force me will be submitted to a [DNSBL]("http://en.wikipedia.org/wiki/Dnsbl").  See me, rojo, in #dronebl on irc.atheme.org if you're interested in doing the same.)  I also have a line set up in /etc/hosts.deny as follows:

```
sshd : ALL : aclexec /usr/local/bin/checkdnsbl %a
```... pointing to [a bash script]("http://headcandy.org/rojo/checkdnsbl") which queries a few DNSBL services before allowing connections.  If you do the same, it's important that this line go in hosts.deny rather than hosts.allow.  To get the checkdnsbl script into your /usr/local/bin, do the following:

```
cd /usr/local/bin
sudo wget http://headcandy.org/rojo/checkdnsbl
sudo chmod 755 checkdnsbl
```Anyway... So, at work, I connect to home via PuTTY with a setup very similar to the tutorial I linked at the beginning of this message.  After PuTTY is connected, I start the VNC server from within PuTTY (rather than having it run 24/7).  I minimize putty, launch the VNC client, and connect from work computer to itself on the tunnelled port (again, very similarly to the tutorial).  All traffic from work to home goes over port 22.

Something else you might consider was hinted at by tarun.winlin earlier, setting up public key authentication for SSH.  See [this example tutorial]("http://www.ualberta.ca/CNS/RESEARCH/LinuxClusters/pka-putty.html") for more details.  In spite of that website's dire warnings, I haven't bothered to set a passphrase for my private key, and nothing bad has ever happened to me.  That's probably treading on the fine line between convenience and obsessive security which could be debated for hours given the right trolls.  :)  But as long as you're confident that only you have access to your putty client and your private key on your work computer, I think it's nice to enjoy having one fewer password to type.

---

### Post by GmAz on 2008-09-22
Thanks to everyone.  Right now I'm at work and since my VNC is turned off right now, as well as my machine, I will have to work on this stuff when i get home.  Its a lot to go over, and with my limited know how on Linux, it may take me longer than others to implement it.  Thanks again!  

:KS

---

