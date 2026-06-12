---
title: "Advice on entry in log file."
date: 2011-09-09
forum: Security
---

### Post by Buckie_Bhoy on 2011-09-09
Hi, looking for some advice on some entries I found in my auth.log. I'm concerned about the entries at 17:43 relating to users and groups etc. To note, my ssh does not use passwords, but instead is set up to use keys and passphrase. Advice and thoughts welcome.
 
```
Sep  6 17:17:01 Ubuntu-Server CRON[7410]: pam_unix(cron:session): session closed for user root
Sep  6 17:31:20 Ubuntu-Server sshd[7418]: Set /proc/self/oom_adj to 0
Sep  6 17:31:20 Ubuntu-Server sshd[7418]: refused connect from 220.172.191.31 (220.172.191.31)
Sep  6 17:43:34 Ubuntu-Server groupadd[7541]: group added to /etc/group: name=guest, GID=125
Sep  6 17:43:34 Ubuntu-Server groupadd[7541]: group added to /etc/gshadow: name=guest
Sep  6 17:43:34 Ubuntu-Server groupadd[7541]: new group: name=guest, GID=125
Sep  6 17:43:34 Ubuntu-Server useradd[7545]: new user: name=guest, UID=117, GID=125, home=/, shell=/bin/bash
Sep  6 17:43:35 Ubuntu-Server usermod[7552]: change user 'guest' password
Sep  6 17:43:36 Ubuntu-Server chage[7559]: changed password expiry for guest
Sep  6 17:43:36 Ubuntu-Server chfn[7571]: changed user 'guest' information
Sep  6 17:43:36 Ubuntu-Server usermod[7596]: change user 'guest' home from '/' to '/tmp/guest-home.W8u9cS'
Sep  6 17:43:37 Ubuntu-Server su[7602]: Successful su for guest by root
Sep  6 17:43:37 Ubuntu-Server su[7602]: + ??? root:guest
Sep  6 17:43:37 Ubuntu-Server su[7602]: pam_unix(su:session): session opened for user guest by (uid=0)
Sep  6 17:43:37 Ubuntu-Server su[7602]: pam_unix(su:session): session closed for user guest
Sep  6 17:43:41 Ubuntu-Server gdm-session-worker[7824]: pam_unix(gdm-autologin:session): session opened for user guest by (uid=0)
Sep  6 17:43:41 Ubuntu-Server gdm-session-worker[7824]: pam_ck_connector(gdm-autologin:session): nox11 mode, ignoring PAM_TTY :3
Sep  6 17:48:51 Ubuntu-Server gdm-session-worker[1367]: pam_succeed_if(gdm:auth): requirement "user ingroup nopasswdlogin" not met by user "xxxxx"
Sep  6 17:48:56 Ubuntu-Server gdm-session-worker[1367]: pam_unix(gdm:session): session opened for user xxxxx by (uid=0)
Sep  6 17:48:56 Ubuntu-Server gdm-session-worker[1367]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0
Sep  6 17:48:58 Ubuntu-Server polkitd(authority=local): Registered Authentication Agent for session /org/freedesktop/ConsoleKit/Session2 (system bus name :1.28 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_GB.UTF-8)
Sep  6 17:49:01 Ubuntu-Server dbus-daemon: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.36" (uid=1001 pid=2134 comm="nautilus) interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply=0 destination=":1.6" (uid=0 pid=1085 comm="/usr/sbin/console-kit-daemon))
Sep  6 18:17:01 Ubuntu-Server CRON[2302]: pam_unix(cron:session): session opened for user root by (uid=0)
Sep  6 18:17:01 Ubuntu-Server CRON[2302]: pam_unix(cron:session): session closed for user root
Sep  6 18:32:55 Ubuntu-Server sshd[2314]: Set /proc/self/oom_adj to 0
Sep  6 18:32:55 Ubuntu-Server sshd[2314]: refused connect from 64.31.60.73 (64.31.60.73)

```

---

### Post by CharlesA on 2011-09-09
It looks like someone cracked your box.

Are you sure you disabled password auth? If you use keys, it won't prompt for the password unless you don't type in your passphrase correctly.

Can you post the contents of /etc/ssh/sshd_config in code tags?

---

### Post by Buckie_Bhoy on 2011-09-09
```
# Package generated configuration file
# See the sshd_config(5) manpage for details

# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes

# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 768

# Logging
SyslogFacility AUTH
LogLevel VERBOSE

# Authentication:
LoginGraceTime 20
PermitRootLogin no
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
AuthorizedKeysFile    %h/.ssh/authorized_keys

# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no
# similar for protocol version 2
HostbasedAuthentication no
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
#IgnoreUserKnownHosts yes

# To enable empty passwords, change to yes (NOT RECOMMENDED)
PermitEmptyPasswords no

# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication no

# Change to no to disable tunnelled clear text passwords
PasswordAuthentication no

# Kerberos options
#KerberosAuthentication no
#KerberosGetAFSToken no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes

# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes

X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

# Set this to 'yes' to enable PAM authentication, account processing,
# and session processing. If this is enabled, PAM authentication will
# be allowed through the ChallengeResponseAuthentication and
# PasswordAuthentication.  Depending on your PAM configuration,
# PAM authentication via ChallengeResponseAuthentication may bypass
# the setting of "PermitRootLogin without-password".
# If you just want the PAM account and session checks to run without
# PAM authentication, then enable this but set PasswordAuthentication
# and ChallengeResponseAuthentication to 'no'.
UsePAM yes

AllowUsers xxxxx
```

---

### Post by CharlesA on 2011-09-09
Hmm that looks right. Did you enable the guest account by chance?

If no, then wipe the drive and reinstall.

---

### Post by Buckie_Bhoy on 2011-09-09
Hi Charles, many thanks for your speedy responses on this, much appreciated.  My wife would have been on comp at that time, and I don't think she would have enabled it.  Notice that /etc/passwd was changed at that time and also /etc/passwd-

Think to be on safe side, I will reinstall over weekend.  Should I check for anything on my other partitions that are mounted at other points?  I have also blocked incoming traffic to that port on my router in the meantime.

---

### Post by haqking on 2011-09-09
> **charlesa said:**
> hmm that looks right. Did you enable the guest account by chance?

If no, then wipe the drive and reinstall.

+1

cracked ! :evil:

---

### Post by haqking on 2011-09-09
> **Buckie_Bhoy said:**
> Hi Charles, many thanks for your speedy responses on this, much appreciated.  My wife would have been on comp at that time, and I don't think she would have enabled it.  Notice that /etc/passwd was changed at that time and also /etc/passwd-

Think to be on safe side, I will reinstall over weekend.  Should I check for anything on my other partitions that are mounted at other points?  I have also blocked incoming traffic to that port on my router in the meantime.


If i was you if you have a backup of your other data then restore from it, you never know, if you dont have the option then not alot you can do about that.

---

### Post by Buckie_Bhoy on 2011-09-09
:( Thanks for your help guys, curious as to how it happened, thought I had set things up according to how to's etc.  Guess when I reinstall, I'm just going to allow remote access from inside my network, and block all incoming traffic at my router.

---

### Post by CharlesA on 2011-09-09
The only thing I can think of would be not restarting sshd after changing the password to no. Not sure how else they could have gotten in there.

---

### Post by Buckie_Bhoy on 2011-09-09
Had been running for months with this setup, and had been restarted plenty of times.  Unless there is something wrong with setup of something elsewhere on my system.

---

### Post by haqking on 2011-09-09
> **Buckie_Bhoy said:**
> Had been running for months with this setup, and had been restarted plenty of times.  Unless there is something wrong with setup of something elsewhere on my system.

Do you connect remotely ? if so from a given source or is it changeable.

You could deny all bar your source if it is constant

---

### Post by Buckie_Bhoy on 2011-09-09
Usually from other laptops in my home network, did use occasionaly from my works pc, however that doesn't have a fixed IP.  Think when I reinstall, i'll just allow from my home network (though was useful to be able to connect from elsewhere).

---

### Post by jramshu on 2011-09-09
This looks like a hands on crack to me, unless the cracker erased some of his tracks in auth.log, but not all.

Usually, when access is through ssh, auth.log will log when a user name and password are entered. It also logs when a key is accepted and the ip it is accepted from. 

I just think it looks like someone did it sitting in front of the machine, or only erased parts of the log file. Or there was an update missed and it was exploited with an old vulnerability, and whoever did it didn't get all the logs. 

JMO.

---

### Post by Dangertux on 2011-09-09
Yeah your box definitely got owned.

Two things I notice from that log.  The first there is information missing. Particularly the IP that was successfully authenticated. And what they authenticated as.

Is there any more of that log prior to the first entry?

Also if in fact you do ONLY use keys with passphrases and log in from multiple computers, you may need to acknowledge the possibility that one of those machines is compromised as well. 

Also before reinstalling, I would suggest removing the key file for that machine and attempting to validate without it. Double check if you're prompted for a password or key authentication fails. If you're prompted for a password it was likely a brute force attack. If not, things get a little more complicated.

---

### Post by jramshu on 2011-09-09
May have a compromised Windows machine and they passed the hash or something.

@Dangertux
Looks like we were thinking along the same lines, the logs shown here don't show an outside source, or anything off the LAN.

---

### Post by Buckie_Bhoy on 2011-09-09
> **Dangertux said:**
> Yeah your box definitely got owned.

Two things I notice from that log.  The first there is information missing. Particularly the IP that was successfully authenticated. And what they authenticated as.

Is there any more of that log prior to the first entry?

Also if in fact you do ONLY use keys with passphrases and log in from multiple computers, you may need to acknowledge the possibility that one of those machines is compromised as well. 

Also before reinstalling, I would suggest removing the key file for that machine and attempting to validate without it. Double check if you're prompted for a password or key authentication fails. If you're prompted for a password it was likely a brute force attack. If not, things get a little more complicated.

Plenty of log prior to that entry, some more below.

```
   	 	 	 	 	 	  Sep  4 08:53:35 Ubuntu-Server gdm-session-worker[3785]: pam_unix(gdm:session): session opened for user xxxxx by (uid=0) 
 Sep  4 08:53:35 Ubuntu-Server gdm-session-worker[3785]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :1 
 Sep  4 08:53:37 Ubuntu-Server polkitd(authority=local): Registered Authentication Agent for session /org/freedesktop/ConsoleKit/Session4 (system bus name :1.63 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_GB.utf8) 
 Sep  4 08:53:41 Ubuntu-Server dbus-daemon: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.68" (uid=1000 pid=3899 comm="nautilus) interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply=0 destination=":1.5" (uid=0 pid=1073 comm="/usr/sbin/console-kit-daemon)) 
 Sep  4 09:17:01 Ubuntu-Server CRON[4150]: pam_unix(cron:session): session opened for user root by (uid=0) 
 Sep  4 09:17:01 Ubuntu-Server CRON[4150]: pam_unix(cron:session): session closed for user root 
 Sep  4 10:17:01 Ubuntu-Server CRON[4264]: pam_unix(cron:session): session opened for user root by (uid=0) 
 Sep  4 10:17:01 Ubuntu-Server CRON[4264]: pam_unix(cron:session): session closed for user root 
 Sep  4 10:34:46 Ubuntu-Server sshd[4276]: Set /proc/self/oom_adj to 0 
 Sep  4 10:34:46 Ubuntu-Server sshd[4276]: refused connect from 81.181.207.60 (81.181.207.60) 
 Sep  4 11:17:01 Ubuntu-Server CRON[4305]: pam_unix(cron:session): session opened for user root by (uid=0) 
 Sep  4 11:17:01 Ubuntu-Server CRON[4305]: pam_unix(cron:session): session closed for user root 
 Sep  4 11:18:36 Ubuntu-Server sshd[4308]: Set /proc/self/oom_adj to 0 
 Sep  4 11:18:36 Ubuntu-Server sshd[4308]: refused connect from 118.218.136.25 (118.218.136.25) 
 Sep  4 11:21:01 Ubuntu-Server CRON[4310]: pam_unix(cron:session): session opened for user xxxxx by (uid=0) 
 Sep  4 11:21:06 Ubuntu-Server CRON[4310]: pam_unix(cron:session): session closed for user xxxxx 
 Sep  4 12:17:01 Ubuntu-Server CRON[4346]: pam_unix(cron:session): session opened for user root by (uid=0) 
 Sep  4 12:17:01 Ubuntu-Server CRON[4346]: pam_unix(cron:session): session closed for user root 
 Sep  4 12:52:25 Ubuntu-Server sshd[4367]: Set /proc/self/oom_adj to 0 
 Sep  4 12:52:26 Ubuntu-Server sshd[4367]: refused connect from 81.181.207.60 (81.181.207.60) 
 Sep  4 13:17:01 Ubuntu-Server CRON[4384]: pam_unix(cron:session): session opened for user root by (uid=0) 
 Sep  4 13:17:01 Ubuntu-Server CRON[4384]: pam_unix(cron:session): session closed for user root 
 Sep  4 14:17:01 Ubuntu-Server CRON[4421]: pam_unix(cron:session): session opened for user root by (uid=0) 
 Sep  4 14:17:01 Ubuntu-Server CRON[4421]: pam_unix(cron:session): session closed for user root 
 Sep  4 15:17:01 Ubuntu-Server CRON[4452]: pam_unix(cron:session): session opened for user root by (uid=0) 
 Sep  4 15:17:01 Ubuntu-Server CRON[4452]: pam_unix(cron:session): session closed for user root 
 Sep  4 15:25:35 Ubuntu-Server sshd[4459]: Set /proc/self/oom_adj to 0 
 Sep  4 15:25:35 Ubuntu-Server sshd[4459]: refused connect from 81.181.207.60 (81.181.207.60) 
 Sep  4 16:17:01 Ubuntu-Server CRON[4484]: pam_unix(cron:session): session opened for user root by (uid=0) 
 Sep  4 16:17:01 Ubuntu-Server CRON[4484]: pam_unix(cron:session): session closed for user root 
 Sep  4 17:17:01 Ubuntu-Server CRON[4520]: pam_unix(cron:session): session opened for user root by (uid=0) 
 Sep  4 17:17:01 Ubuntu-Server CRON[4520]: pam_unix(cron:session): session closed for user root 
 Sep  4 18:17:01 Ubuntu-Server CRON[4553]: pam_unix(cron:session): session opened for user root by (uid=0) 
 Sep  4 18:17:01 Ubuntu-Server CRON[4553]: pam_unix(cron:session): session closed for user root 
 Sep  4 18:19:50 Ubuntu-Server sshd[4557]: Set /proc/self/oom_adj to 0 
 Sep  4 18:19:50 Ubuntu-Server sshd[4557]: refused connect from 81.181.207.60 (81.181.207.60) 
 Sep  4 19:17:01 Ubuntu-Server CRON[4590]: pam_unix(cron:session): session opened for user root by (uid=0) 
 Sep  4 19:17:01 Ubuntu-Server CRON[4590]: pam_unix(cron:session): session closed for user root 
 Sep  4 20:17:01 Ubuntu-Server CRON[4625]: pam_unix(cron:session): session opened for user root by (uid=0) 
 Sep  4 20:17:01 Ubuntu-Server CRON[4625]: pam_unix(cron:session): session closed for user root 
 Sep  4 21:17:01 Ubuntu-Server CRON[4660]: pam_unix(cron:session): session opened for user root by (uid=0) 
 Sep  4 21:17:01 Ubuntu-Server CRON[4660]: pam_unix(cron:session): session closed for user root 
 Sep  4 21:24:34 Ubuntu-Server sshd[4669]: Set /proc/self/oom_adj to 0 
 Sep  4 21:24:34 Ubuntu-Server sshd[4669]: refused connect from 81.181.207.60 (81.181.207.60) 
 Sep  4 22:17:01 Ubuntu-Server CRON[4697]: pam_unix(cron:session): session opened for user root by (uid=0) 
 Sep  4 22:17:01 Ubuntu-Server CRON[4697]: pam_unix(cron:session): session closed for user root 
 Sep  4 23:17:01 Ubuntu-Server CRON[4731]: pam_unix(cron:session): session opened for user root by (uid=0) 
 Sep  4 23:17:01 Ubuntu-Server CRON[4731]: pam_unix(cron:session): session closed for user root 
 Sep  5 00:01:01 Ubuntu-Server CRON[4763]: pam_unix(cron:session): session opened for user xxxxx by (uid=0) 
 Sep  5 00:17:01 Ubuntu-Server CRON[4794]: pam_unix(cron:session): session opened for user root by (uid=0) 
 Sep  5 00:17:01 Ubuntu-Server CRON[4794]: pam_unix(cron:session): session closed for user root 
 Sep  5 00:38:27 Ubuntu-Server sshd[4827]: Set /proc/self/oom_adj to 0 
 Sep  5 00:38:28 Ubuntu-Server sshd[4827]: refused connect from 81.181.207.60 (81.181.207.60) 
 Sep  5 00:48:31 Ubuntu-Server CRON[4763]: pam_unix(cron:session): session closed for user xxxxx 
 Sep  5 01:17:01 Ubuntu-Server CRON[4858]: pam_unix(cron:session): session opened for user root by (uid=0) 
 Sep  5 01:17:01 Ubuntu-Server CRON[4858]: pam_unix(cron:session): session closed for user root 
 Sep  5 02:17:02 Ubuntu-Server CRON[4896]: pam_unix(cron:session): session opened for user root by (uid=0) 
 Sep  5 02:17:02 Ubuntu-Server CRON[4896]: pam_unix(cron:session): session closed for user root 
 Sep  5 03:17:01 Ubuntu-Server CRON[4933]: pam_unix(cron:session): session opened for user root by (uid=0) 
 Sep  5 03:17:01 Ubuntu-Server CRON[4933]: pam_unix(cron:session): session closed for user root 
 Sep  5 04:17:01 Ubuntu-Server CRON[4970]: pam_unix(cron:session): session opened for user root by (uid=0) 
 Sep  5 04:17:01 Ubuntu-Server CRON[4970]: pam_unix(cron:session): session closed for user root 
 Sep  5 04:18:41 Ubuntu-Server sshd[4973]: Set /proc/self/oom_adj to 0 
 Sep  5 04:18:42 Ubuntu-Server sshd[4973]: refused connect from 81.181.207.60 (81.181.207.60) 
 Sep  5 05:17:01 Ubuntu-Server CRON[5007]: pam_unix(cron:session): session opened for user root by (uid=0) 
 Sep  5 05:17:01 Ubuntu-Server CRON[5007]: pam_unix(cron:session): session closed for user root 
 Sep  5 06:17:01 Ubuntu-Server CRON[5048]: pam_unix(cron:session): session opened for user root by (uid=0) 
 Sep  5 06:17:01 Ubuntu-Server CRON[5048]: pam_unix(cron:session): session closed for user root 
 Sep  5 06:25:01 Ubuntu-Server CRON[5055]: pam_unix(cron:session): session opened for user root by (uid=0) 
 Sep  5 06:25:01 Ubuntu-Server CRON[5055]: pam_unix(cron:session): session closed for user root 
 Sep  5 06:39:04 Ubuntu-Server sshd[5061]: Set /proc/self/oom_adj to 0 
 Sep  5 06:39:04 Ubuntu-Server sshd[5061]: refused connect from 202.160.122.156 (202.160.122.156) 
 Sep  5 07:17:01 Ubuntu-Server CRON[5088]: pam_unix(cron:session): session opened for user root by (uid=0) 
 Sep  5 07:17:01 Ubuntu-Server CRON[5088]: pam_unix(cron:session): session closed for user root 
 Sep  5 07:30:01 Ubuntu-Server CRON[5097]: pam_unix(cron:session): session opened for user root by (uid=0) 
 Sep  5 07:30:01 Ubuntu-Server CRON[5097]: pam_unix(cron:session): session closed for user root 
 Sep  5 08:17:01 Ubuntu-Server CRON[5298]: pam_unix(cron:session): session opened for user root by (uid=0) 
 Sep  5 08:17:01 Ubuntu-Server CRON[5298]: pam_unix(cron:session): session closed for user root 
 Sep  5 09:17:01 Ubuntu-Server CRON[5338]: pam_unix(cron:session): session opened for user root by (uid=0) 
 Sep  5 09:17:01 Ubuntu-Server CRON[5338]: pam_unix(cron:session): session closed for user root 
 Sep  5 10:17:01 Ubuntu-Server CRON[5375]: pam_unix(cron:session): session opened for user root by (uid=0) 
 Sep  5 10:17:01 Ubuntu-Server CRON[5375]: pam_unix(cron:session): session closed for user root 
 Sep  5 10:32:17 Ubuntu-Server gdm-session-worker[5438]: pam_succeed_if(gdm:auth): requirement "user ingroup nopasswdlogin" not met by user "xxxxx" 
 Sep  5 10:32:21 Ubuntu-Server gdm-session-worker[5438]: pam_unix(gdm:session): session opened for user xxxxx by (uid=0) 
 Sep  5 10:32:21 Ubuntu-Server gdm-session-worker[5438]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :2 
 Sep  5 11:17:01 Ubuntu-Server CRON[5554]: pam_unix(cron:session): session opened for user root by (uid=0) 
 Sep  5 11:17:01 Ubuntu-Server CRON[5554]: pam_unix(cron:session): session closed for user root 
 Sep  5 11:21:01 Ubuntu-Server CRON[5570]: pam_unix(cron:session): session opened for user xxxxx by (uid=0) 
 Sep  5 11:21:05 Ubuntu-Server CRON[5570]: pam_unix(cron:session): session closed for user xxxxx 
 Sep  5 11:52:37 Ubuntu-Server gnome-screensaver-dialog: gkr-pam: unlocked login keyring 
 Sep  5 12:04:16 Ubuntu-Server sshd[5663]: Set /proc/self/oom_adj to 0 
 Sep  5 12:04:16 Ubuntu-Server sshd[5663]: Connection from 87.255.38.88 port 48689 
 Sep  5 12:04:22 Ubuntu-Server sshd[5663]: User root from 87.255.38.88 not allowed because not listed in AllowUsers 
 Sep  5 12:04:22 Ubuntu-Server sshd[5665]: Set /proc/self/oom_adj to 0 
 Sep  5 12:04:22 Ubuntu-Server sshd[5665]: Connection from 87.255.38.88 port 49534 
 Sep  5 12:04:28 Ubuntu-Server sshd[5665]: User root from 87.255.38.88 not allowed because not listed in AllowUsers 
 Sep  5 12:04:28 Ubuntu-Server sshd[5667]: Set /proc/self/oom_adj to 0 
 Sep  5 12:04:28 Ubuntu-Server sshd[5667]: Connection from 87.255.38.88 port 50321 
 Sep  5 12:04:33 Ubuntu-Server sshd[5667]: User root from 87.255.38.88 not allowed because not listed in AllowUsers 
 Sep  5 12:04:34 Ubuntu-Server sshd[5669]: Set /proc/self/oom_adj to 0 
 Sep  5 12:04:34 Ubuntu-Server sshd[5669]: Connection from 87.255.38.88 port 51105 
 Sep  5 12:04:39 Ubuntu-Server sshd[5669]: User root from 87.255.38.88 not allowed because not listed in AllowUsers 
 Sep  5 12:04:39 Ubuntu-Server sshd[5671]: Set /proc/self/oom_adj to 0 
 Sep  5 12:04:39 Ubuntu-Server sshd[5671]: Connection from 87.255.38.88 port 51848 
 Sep  5 12:04:45 Ubuntu-Server sshd[5671]: User root from 87.255.38.88 not allowed because not listed in AllowUsers 
 Sep  5 12:04:45 Ubuntu-Server sshd[5673]: Set /proc/self/oom_adj to 0 
 Sep  5 12:04:45 Ubuntu-Server sshd[5673]: Connection from 87.255.38.88 port 52625 
 Sep  5 12:04:51 Ubuntu-Server sshd[5673]: User root from 87.255.38.88 not allowed because not listed in AllowUsers 
 Sep  5 12:04:51 Ubuntu-Server sshd[5675]: Set /proc/self/oom_adj to 0 
 Sep  5 12:04:51 Ubuntu-Server sshd[5675]: refused connect from 87.255.38.88 (87.255.38.88) 
 Sep  5 12:09:08 Ubuntu-Server sshd[5677]: Set /proc/self/oom_adj to 0 
 Sep  5 12:09:08 Ubuntu-Server sshd[5677]: refused connect from 118.218.136.25 (118.218.136.25) 
 Sep  5 12:17:01 Ubuntu-Server CRON[5683]: pam_unix(cron:session): session opened for user root by (uid=0) 
 Sep  5 12:17:01 Ubuntu-Server CRON[5683]: pam_unix(cron:session): session closed for user root 
 Sep  5 13:17:01 Ubuntu-Server CRON[5700]: pam_unix(cron:session): session opened for user root by (uid=0) 
 Sep  5 13:17:01 Ubuntu-Server CRON[5700]: pam_unix(cron:session): session closed for user root 
 Sep  5 14:17:01 Ubuntu-Server CRON[5721]: pam_unix(cron:session): session opened for user root by (uid=0) 
 Sep  5 14:17:01 Ubuntu-Server CRON[5721]: pam_unix(cron:session): session closed for user root 
 Sep  5 15:17:01 Ubuntu-Server CRON[5738]: pam_unix(cron:session): session opened for user root by (uid=0) 
 Sep  5 15:17:01 Ubuntu-Server CRON[5738]: pam_unix(cron:session): session closed for user root 
 Sep  5 15:18:39 Ubuntu-Server gnome-screensaver-dialog: gkr-pam: unlocked login keyring 
 Sep  5 16:17:01 Ubuntu-Server CRON[5838]: pam_unix(cron:session): session opened for user root by (uid=0) 
 Sep  5 16:17:01 Ubuntu-Server CRON[5838]: pam_unix(cron:session): session closed for user root 
 Sep  5 16:59:53 Ubuntu-Server gnome-screensaver-dialog: gkr-pam: unlocked login keyring 
 Sep  5 17:17:01 Ubuntu-Server CRON[6010]: pam_unix(cron:session): session opened for user root by (uid=0) 
 Sep  5 17:17:01 Ubuntu-Server CRON[6010]: pam_unix(cron:session): session closed for user root 
 Sep  5 18:17:01 Ubuntu-Server CRON[6048]: pam_unix(cron:session): session opened for user root by (uid=0) 
 Sep  5 18:17:01 Ubuntu-Server CRON[6048]: pam_unix(cron:session): session closed for user root 
 Sep  5 19:17:01 Ubuntu-Server CRON[6088]: pam_unix(cron:session): session opened for user root by (uid=0) 
 Sep  5 19:17:01 Ubuntu-Server CRON[6088]: pam_unix(cron:session): session closed for user root 
 Sep  5 19:45:17 Ubuntu-Server sshd[6109]: Set /proc/self/oom_adj to 0 
 Sep  5 19:45:17 Ubuntu-Server sshd[6109]: Connection from 211.151.52.37 port 63189 
 Sep  5 19:45:24 Ubuntu-Server sshd[6109]: User root from 211.151.52.37 not allowed because not listed in AllowUsers 
 Sep  5 19:45:25 Ubuntu-Server sshd[6112]: Set /proc/self/oom_adj to 0 
 Sep  5 19:45:25 Ubuntu-Server sshd[6112]: Connection from 211.151.52.37 port 64118 
 Sep  5 19:45:31 Ubuntu-Server sshd[6112]: User root from 211.151.52.37 not allowed because not listed in AllowUsers 
 Sep  5 19:45:32 Ubuntu-Server sshd[6114]: Set /proc/self/oom_adj to 0 
 Sep  5 19:45:32 Ubuntu-Server sshd[6114]: Connection from 211.151.52.37 port 18754 
 Sep  5 19:45:39 Ubuntu-Server sshd[6114]: User root from 211.151.52.37 not allowed because not listed in AllowUsers 
 Sep  5 19:45:39 Ubuntu-Server sshd[6116]: Set /proc/self/oom_adj to 0 
 Sep  5 19:45:39 Ubuntu-Server sshd[6116]: refused connect from 211.151.52.37 (211.151.52.37) 
 Sep  5 20:17:01 Ubuntu-Server CRON[6136]: pam_unix(cron:session): session opened for user root by (uid=0) 
 Sep  5 20:17:01 Ubuntu-Server CRON[6136]: pam_unix(cron:session): session closed for user root 
 Sep  5 20:58:29 Ubuntu-Server sshd[6158]: Set /proc/self/oom_adj to 0 
 Sep  5 20:58:29 Ubuntu-Server sshd[6158]: Connection from 121.26.253.98 port 56319 
 Sep  5 20:58:37 Ubuntu-Server sshd[6158]: User root from 121.26.253.98 not allowed because not listed in AllowUsers 
 Sep  5 20:58:38 Ubuntu-Server sshd[6160]: Set /proc/self/oom_adj to 0 
 Sep  5 20:58:38 Ubuntu-Server sshd[6160]: Connection from 121.26.253.98 port 56840 
 Sep  5 20:58:45 Ubuntu-Server sshd[6160]: Invalid user troot from 121.26.253.98 
 Sep  5 20:58:46 Ubuntu-Server sshd[6162]: Set /proc/self/oom_adj to 0 
 Sep  5 20:58:46 Ubuntu-Server sshd[6162]: Connection from 121.26.253.98 port 57390 
 Sep  5 20:58:54 Ubuntu-Server sshd[6162]: User root from 121.26.253.98 not allowed because not listed in AllowUsers 
 Sep  5 20:58:55 Ubuntu-Server sshd[6164]: Set /proc/self/oom_adj to 0 
 Sep  5 20:58:55 Ubuntu-Server sshd[6164]: Connection from 121.26.253.98 port 57899 
 Sep  5 20:59:03 Ubuntu-Server sshd[6164]: User root from 121.26.253.98 not allowed because not listed in AllowUsers 
 Sep  5 20:59:04 Ubuntu-Server sshd[6166]: Set /proc/self/oom_adj to 0 
 Sep  5 20:59:04 Ubuntu-Server sshd[6166]: Connection from 121.26.253.98 port 58418 
 Sep  5 20:59:11 Ubuntu-Server sshd[6166]: User root from 121.26.253.98 not allowed because not listed in AllowUsers 
 Sep  5 20:59:12 Ubuntu-Server sshd[6168]: Set /proc/self/oom_adj to 0 
 Sep  5 20:59:12 Ubuntu-Server sshd[6168]: refused connect from 121.26.253.98 (121.26.253.98) 
 Sep  5 21:17:01 Ubuntu-Server CRON[6179]: pam_unix(cron:session): session opened for user root by (uid=0) 
 Sep  5 21:17:01 Ubuntu-Server CRON[6179]: pam_unix(cron:session): session closed for user root 
 Sep  5 22:17:01 Ubuntu-Server CRON[6214]: pam_unix(cron:session): session opened for user root by (uid=0) 
 Sep  5 22:17:01 Ubuntu-Server CRON[6214]: pam_unix(cron:session): session closed for user root 
 Sep  5 23:17:01 Ubuntu-Server CRON[6249]: pam_unix(cron:session): session opened for user root by (uid=0) 
 Sep  5 23:17:01 Ubuntu-Server CRON[6249]: pam_unix(cron:session): session closed for user root 
 Sep  6 00:01:01 Ubuntu-Server CRON[6273]: pam_unix(cron:session): session opened for user xxxxx by (uid=0) 
 Sep  6 00:17:01 Ubuntu-Server CRON[6307]: pam_unix(cron:session): session opened for user root by (uid=0) 
 Sep  6 00:17:01 Ubuntu-Server CRON[6307]: pam_unix(cron:session): session closed for user root 
 Sep  6 00:48:44 Ubuntu-Server CRON[6273]: pam_unix(cron:session): session closed for user xxxxx 
 Sep  6 01:17:02 Ubuntu-Server CRON[6376]: pam_unix(cron:session): session opened for user root by (uid=0) 
 Sep  6 01:17:02 Ubuntu-Server CRON[6376]: pam_unix(cron:session): session closed for user root 
 Sep  6 02:17:01 Ubuntu-Server CRON[6414]: pam_unix(cron:session): session opened for user root by (uid=0) 
 Sep  6 02:17:01 Ubuntu-Server CRON[6414]: pam_unix(cron:session): session closed for user root 
 Sep  6 03:17:01 Ubuntu-Server CRON[6451]: pam_unix(cron:session): session opened for user root by (uid=0) 
 Sep  6 03:17:01 Ubuntu-Server CRON[6451]: pam_unix(cron:session): session closed for user root 
 Sep  6 04:17:01 Ubuntu-Server CRON[6488]: pam_unix(cron:session): session opened for user root by (uid=0) 
 Sep  6 04:17:01 Ubuntu-Server CRON[6488]: pam_unix(cron:session): session closed for user root 
 Sep  6 05:17:01 Ubuntu-Server CRON[6526]: pam_unix(cron:session): session opened for user root by (uid=0) 
 Sep  6 05:17:01 Ubuntu-Server CRON[6526]: pam_unix(cron:session): session closed for user root 
 Sep  6 06:17:01 Ubuntu-Server CRON[6562]: pam_unix(cron:session): session opened for user root by (uid=0) 
 Sep  6 06:17:01 Ubuntu-Server CRON[6562]: pam_unix(cron:session): session closed for user root 
 Sep  6 06:25:01 Ubuntu-Server CRON[6568]: pam_unix(cron:session): session opened for user root by (uid=0) 
 Sep  6 06:25:01 Ubuntu-Server CRON[6568]: pam_unix(cron:session): session closed for user root 
 Sep  6 07:17:01 Ubuntu-Server CRON[6598]: pam_unix(cron:session): session opened for user root by (uid=0) 
 Sep  6 07:17:01 Ubuntu-Server CRON[6598]: pam_unix(cron:session): session closed for user root 
 Sep  6 07:30:01 Ubuntu-Server CRON[6608]: pam_unix(cron:session): session opened for user root by (uid=0) 
 Sep  6 07:30:01 Ubuntu-Server CRON[6608]: pam_unix(cron:session): session closed for user root 
 Sep  6 08:17:01 Ubuntu-Server CRON[6800]: pam_unix(cron:session): session opened for user root by (uid=0) 
 Sep  6 08:17:01 Ubuntu-Server CRON[6800]: pam_unix(cron:session): session closed for user root 
 Sep  6 09:17:01 Ubuntu-Server CRON[6838]: pam_unix(cron:session): session opened for user root by (uid=0) 
 Sep  6 09:17:01 Ubuntu-Server CRON[6838]: pam_unix(cron:session): session closed for user root 
 Sep  6 10:17:01 Ubuntu-Server CRON[6872]: pam_unix(cron:session): session opened for user root by (uid=0) 
 Sep  6 10:17:01 Ubuntu-Server CRON[6872]: pam_unix(cron:session): session closed for user root 
 Sep  6 10:46:33 Ubuntu-Server sshd[6892]: Set /proc/self/oom_adj to 0 
 Sep  6 10:46:33 Ubuntu-Server sshd[6892]: refused connect from 109.73.160.78 (109.73.160.78) 
 Sep  6 11:17:01 Ubuntu-Server CRON[6910]: pam_unix(cron:session): session opened for user root by (uid=0) 
 Sep  6 11:17:01 Ubuntu-Server CRON[6910]: pam_unix(cron:session): session closed for user root 
 Sep  6 11:21:01 Ubuntu-Server CRON[6914]: pam_unix(cron:session): session opened for user xxxxx by (uid=0) 
 Sep  6 11:21:06 Ubuntu-Server CRON[6914]: pam_unix(cron:session): session closed for user xxxxx 
 Sep  6 12:17:01 Ubuntu-Server CRON[6943]: pam_unix(cron:session): session opened for user root by (uid=0) 
 Sep  6 12:17:01 Ubuntu-Server CRON[6943]: pam_unix(cron:session): session closed for user root 
 Sep  6 13:17:01 Ubuntu-Server CRON[6977]: pam_unix(cron:session): session opened for user root by (uid=0) 
 Sep  6 13:17:01 Ubuntu-Server CRON[6977]: pam_unix(cron:session): session closed for user root 
 Sep  6 14:17:01 Ubuntu-Server CRON[7015]: pam_unix(cron:session): session opened for user root by (uid=0) 
 Sep  6 14:17:01 Ubuntu-Server CRON[7015]: pam_unix(cron:session): session closed for user root 
 Sep  6 15:17:01 Ubuntu-Server CRON[7050]: pam_unix(cron:session): session opened for user root by (uid=0) 
 Sep  6 15:17:01 Ubuntu-Server CRON[7050]: pam_unix(cron:session): session closed for user root 
 Sep  6 15:38:58 Ubuntu-Server gnome-screensaver-dialog: gkr-pam: unlocked login keyring 
 Sep  6 16:17:01 Ubuntu-Server CRON[7191]: pam_unix(cron:session): session opened for user root by (uid=0) 
 Sep  6 16:17:01 Ubuntu-Server CRON[7191]: pam_unix(cron:session): session closed for user root 
 Sep  6 16:22:42 Ubuntu-Server gnome-screensaver-dialog: gkr-pam: unlocked login keyring 
 Sep  6 17:09:27 Ubuntu-Server gnome-screensaver-dialog: gkr-pam: unlocked login keyring 
 Sep  6 17:17:01 Ubuntu-Server CRON[7410]: pam_unix(cron:session): session opened for user root by (uid=0) 
 Sep  6 17:17:01 Ubuntu-Server CRON[7410]: pam_unix(cron:session): session closed for user root 
 Sep  6 17:31:20 Ubuntu-Server sshd[7418]: Set /proc/self/oom_adj to 0 
 Sep  6 17:31:20 Ubuntu-Server sshd[7418]: refused connect from 220.172.191.31 (220.172.191.31) 
 Sep  6 17:43:34 Ubuntu-Server groupadd[7541]: group added to /etc/group: name=guest, GID=125 
 Sep  6 17:43:34 Ubuntu-Server groupadd[7541]: group added to /etc/gshadow: name=guest 
 Sep  6 17:43:34 Ubuntu-Server groupadd[7541]: new group: name=guest, GID=125 
 Sep  6 17:43:34 Ubuntu-Server useradd[7545]: new user: name=guest, UID=117, GID=125, home=/, shell=/bin/bash 
 Sep  6 17:43:35 Ubuntu-Server usermod[7552]: change user 'guest' password 
 Sep  6 17:43:36 Ubuntu-Server chage[7559]: changed password expiry for guest 
 Sep  6 17:43:36 Ubuntu-Server chfn[7571]: changed user 'guest' information 
 Sep  6 17:43:36 Ubuntu-Server usermod[7596]: change user 'guest' home from '/' to '/tmp/guest-home.W8u9cS' 
 Sep  6 17:43:37 Ubuntu-Server su[7602]: Successful su for guest by root 
 Sep  6 17:43:37 Ubuntu-Server su[7602]: + ??? root:guest
 
```

Also, looks like machine was restarted prior to this, but another curious thing is timestamps all out of sequence on kern.log

```
Sep  6 17:42:58 Ubuntu-Server kernel: [282266.980201] #
Sep  6 17:42:58 Ubuntu-Server kernel: [282267.000199] #
Sep  6 17:43:01 Ubuntu-Server kernel: [282270.010493] #
Sep  6 17:43:15 Ubuntu-Server kernel: [282284.030310] #
Sep  6 17:43:16 Ubuntu-Server kernel: [282285.040307] #
Sep  6 17:43:17 Ubuntu-Server kernel: [282286.060320] #
Sep  6 17:43:17 Ubuntu-Server kernel: [282286.080322] #
Sep  6 17:43:18 Ubuntu-Server kernel: [282287.090332] #
Sep  6 17:43:21 Ubuntu-Server kernel: [282290.110245] #
Sep  6 17:43:24 Ubuntu-Server kernel: [282293.120286] #
Sep  6 17:43:24 Ubuntu-Server kernel: [282293.432286] #
Sep  6 17:43:29 Ubuntu-Server kernel: [282298.160643] #
Sep  6 17:43:30 Ubuntu-Server kernel: [282299.310371] #
Sep  6Sep  6 17:39:31 Ubuntu-Server kernel: imklog 4.2.0, log source = /proc/kmsg started.
Sep  6 17:39:31 Ubuntu-Server kernel: [    0.000000] Initializing cgroup subsys cpuset
Sep  6 17:39:31 Ubuntu-Server kernel: [    0.000000] Initializing cgroup subsys cpu
Sep  6 17:39:31 Ubuntu-Server kernel: [    0.000000] Linux version 2.6.35-30-generic (buildd@crested) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #56-Ubuntu SMP Mon Jul 11 20:01:08 UTC 2011 (Ubuntu 2.6.35-30.56-generic 2.6.35.13)
Sep  6 17:39:31 Ubuntu-Server kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-30-generic root=UUID=5fe76f8e-fcd5-4521-b026-d0565a8984c6 ro quiet splash noapic nolapic acpi=force irqpoll
Sep  6 17:39:31 Ubuntu-Server kernel: [    0.000000] BIOS-provided physical RAM map:
```

---

### Post by jramshu on 2011-09-09
There still isn't any authentication info.

What else are you running on that box? Are you hosting a site or a file server or something?

---

### Post by Buckie_Bhoy on 2011-09-09
only other things that were running was samba and vsftpd

---

### Post by haqking on 2011-09-09
> **Buckie_Bhoy said:**
> only other things that were running was samba and vsftpd

wasnt there a backdoor discovered earlier this year in a version of vsftpd ?

i will be back, im sure there was

Edit: yes see[ here]("http://www.theregister.co.uk/2011/07/05/ftp_backdoor_shenanigans/"), though probably not your version but i bet vsftpd could be a cause

---

### Post by Dangertux on 2011-09-09
What version of vsftpd also, is you samba configuration secure?

@haqking 2.3.4 was backdoored

---

### Post by jramshu on 2011-09-09
I would say you got cracked. Probably through a vulnerability that wasn't patched on your machine.

EDIT:
It already had a module in the framework.

---

### Post by Dangertux on 2011-09-09
At this point I think it's one of the following.

A ) Someone had physical access to the machine and did bad stuff
B ) Possibly a bad configuration of Samba 
C ) Possibly but much less likely vsftpd was exploited, note there are no published vulnerabilities for the version in repos. (did you tick someone off enough to go bug hunting?)
C.5) Possible brute force on vsftpd.
D ) Someone obtained login credentials (key) from one of your machines or had access to one of the client machines.

That's what I've got. Lemme know what you guys think on those.

EDIT: About D there is enough discrepancy in time stamps on the logs that they could have just removed their entries.

---

### Post by jramshu on 2011-09-09
@Dangertux
A) That's my first thought
B) Maybe not updated, exploitable
C) Same as above, poisoned version removed on 3JUL11, slim chance of exploit
D) No log files that show this, unless it was exploited and those files where deleted to hide identity but let him know it was done.

It looks like, by looking at the rest of the logs, that someone was scanning pretty hard prior to gaining root access.

---

### Post by CharlesA on 2011-09-09
> **jramshu said:**
> This looks like a hands on crack to me, unless the cracker erased some of his tracks in auth.log, but not all.

Usually, when access is through ssh, auth.log will log when a user name and password are entered. It also logs when a key is accepted and the ip it is accepted from. 

I just think it looks like someone did it sitting in front of the machine, or only erased parts of the log file. Or there was an update missed and it was exploited with an old vulnerability, and whoever did it didn't get all the logs. 

JMO.

Yep. I'm kinda wondering if they booted to recovery mode and made the changes that way. That's the only way I can think of having auth log not have connection info unless it was tampered with.

---

### Post by Buckie_Bhoy on 2011-09-10
> **Dangertux said:**
> At this point I think it's one of the following.
 
A ) Someone had physical access to the machine and did bad stuff
B ) Possibly a bad configuration of Samba 
C ) Possibly but much less likely vsftpd was exploited, note there are no published vulnerabilities for the version in repos. (did you tick someone off enough to go bug hunting?)
C.5) Possible brute force on vsftpd.
D ) Someone obtained login credentials (key) from one of your machines or had access to one of the client machines.
 
That's what I've got. Lemme know what you guys think on those.
 
EDIT: About D there is enough discrepancy in time stamps on the logs that they could have just removed their entries.
 
 
Hi guys, again thanks for all the thoughts and pointers.
A) Only other person that had access was my other half, and she's not savvy enough
B) Beginning to suspect that may be the case, have put my samba config below
C) Am running version 2.3.0, have done anything to anyone to tick them off to that extent, besides it's just a small server on my home network for music and stuff
C.5) Possible, but am sure when I set it up that ftpusers couldn't get out of the directories assigned when tested
D) Client machines were in our possession
 
SAMBA Conf (v3.5.4)
```

#
# Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which 
# are not shown in this example
#
# Some options that are often worth tuning have been included as
# commented-out examples in this file.
#  - When such options are commented with ";", the proposed setting
#    differs from the default Samba behaviour
#  - When commented with "#", the proposed setting is the default
#    behaviour of Samba but the option is considered important
#    enough to be mentioned here
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic 
# errors. 
# A well-established practice is to name the original file
# "smb.conf.master" and create the "real" config file with
# testparm -s smb.conf.master >smb.conf
# This minimizes the size of the really used smb.conf file
# which, according to the Samba Team, impacts performance
# However, use this with caution if your smb.conf file contains nested
# "include" statements. See Debian bug #483187 for a case
# where using a master file is not a good idea.
#
#======================= Global Settings =======================
[global]
## Browsing/Identification ###
# Change this to the workgroup/NT-domain name your Samba server will part of
 workgroup = XXXXXX-NETWORK
# server string is the equivalent of the NT Description field
 server string = %h server (Samba, Ubuntu)
# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no
# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z
# This will prevent nmbd to search for NetBIOS names through DNS.
 dns proxy = no
# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast
 usershare owner only = false
#### Networking ####
# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0
# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;   bind interfaces only = yes
 
#### Debugging/Accounting ####
# This tells Samba to use a separate log file for each machine
# that connects
 log file = /var/log/samba/log.%m
# Cap the size of the individual log files (in KiB).
 max log size = 1000
# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
#   syslog only = no
# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
 syslog = 0
# Do something sensible when Samba crashes: mail the admin a backtrace
 panic action = /usr/share/samba/panic-action %d
 
####### Authentication #######
# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
 security = user
# username map = /etc/samba/smbusers
# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
 encrypt passwords = true
# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
; passdb backend = tdbsam
 obey pam restrictions = yes
# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
 unix password sync = yes
# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<[EMAIL="kahan@informatik.tu-muenchen.de"]kahan@informatik.tu-muenchen.de[/EMAIL]> for
# sending the correct chat script for the passwd program in Debian Sarge).
 passwd program = /usr/bin/passwd %u
 passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
 pam password change = yes
# This option controls how unsuccessful authentication attempts are mapped
# to anonymous connections
 map to guest = bad user
########## Domains ###########
# Is this machine able to authenticate users. Both PDC and BDC
# must have this setting enabled. If you are the BDC you must
# change the 'domain master' setting to no
#
;   domain logons = yes
#
# The following setting only takes effect if 'domain logons' is set
# It specifies the location of the user's profile directory
# from the client point of view)
# The following required a [profiles] share to be setup on the
# samba server (see below)
;   logon path = [\\%N\profiles\%U]("file://\\%N\profiles\%U")
# Another common choice is storing the profile in the user's home directory
# (this is Samba's default)
#   logon path = [\\%N\%U\profile]("file://\\%N\%U\profile")
# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
#   logon home = [\\%N\%U]("file://\\%N\%U")
# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
;   logon script = logon.cmd
# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u
# This allows machine accounts to be created on the domain controller via the 
# SAMR RPC pipe.  
# The following assumes a "machines" group exists on the system
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u
# This allows Unix groups to be created on the domain controller via the SAMR
# RPC pipe.  
; add group script = /usr/sbin/addgroup --force-badname %g
########## Printing ##########
# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
#   load printers = yes
# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap
# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
; printing = cups
;   printcap name = cups
############ Misc ############
# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m
# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/speed.html
# for details
# You may want to add the following on a Linux system:
#         SO_RCVBUF=8192 SO_SNDBUF=8192
#   socket options = TCP_NODELAY
# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &
# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
#   domain master = auto
# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash
# The following was the default behaviour in sarge,
# but samba upstream reverted the default because it might induce
# performance issues in large organizations.
# See Debian bug #368251 for some of the consequences of *not*
# having this setting and smb.conf(5) for details.
;   winbind enum groups = yes
;   winbind enum users = yes
# Setup usershare options to enable non-root users to share folders
# with the net usershare command.
# Maximum number of usershare. 0 (default) means that usershare is disabled.
; usershare max shares = 100
# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
 usershare allow guests = yes
 username map = /etc/samba/smbusers
#======================= Share Definitions =======================
# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each 
# user's home director as [\\server\username]("file://\\server\username")
;[homes]
;   comment = Home Directories
;   browseable = no
# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
;   read only = yes
# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700
# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700
# By default, [\\server\username]("file://\\server\username") shares can be connected to by anyone
# with access to the samba server. Un-comment the following parameter
# to make sure that only "username" can connect to [\\server\username]("file://\\server\username")
# The following parameter makes sure that only "username" can connect
#
# This might need tweaking when using external authentication schemes
;   valid users = %S
# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes
;   share modes = no
# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be writable by all users so that their
# profile directory may be created the first time they log on
;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700
[printers]
 comment = All Printers
 browseable = no
 path = /var/spool/samba
 printable = yes
; guest ok = no
; read only = yes
 create mask = 0700
# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
 comment = Printer Drivers
 path = /var/lib/samba/printers
; browseable = yes
; read only = yes
; guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin
# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   read only = yes
;   locking = no
;   path = /cdrom
;   guest ok = yes
# The next two parameters show how to auto-mount a CD-ROM when the
# cdrom share is accesed. For this to work /etc/fstab must contain
# an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
# is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom
[Images]
 comment = Images
 path = /mnt/Images
 valid users = @users
 create mask = 660
 directory mask = 771
 writeable = yes
; browseable = yes
[Videos]
 comment = Videos
 path = /mnt/Videos
 valid users = @users
 create mask = 660
 directory mask = 771
 writeable = yes
; browseable = yes
[Documents]
 comment = Documents
 path = /mnt/Documents
 valid users = @users
 create mask = 660
 directory mask = 771
 writeable = yes
; browseable = yes
[Development]
 comment = Development
 path = /mnt/Development
 valid users = XXXXX
 create mask = 660
 directory mask = 771
 writeable = yes
; browseable = yes
[Music]
        comment = Music
        path = /mnt/Music
        valid users = @users
        create mask = 660
        directory mask = 771
        writeable = yes
;       browseable = yes

```

---

### Post by Buckie_Bhoy on 2011-09-24
Marking as solved, as I have re-installed 11.04.  Once again thank you to everyone for advice and help.  I will make sure to double check new set up with you guys as I configure things.

---

### Post by Ryan Dwyer on 2011-09-24
> **Buckie_Bhoy said:**
> My wife would have been on comp at that time

And you didn't think to ask her what she did? She could have installed something which required a guest account to be created. Or maybe she logged in as a guest from GDM and the account was created then. I'm not convinced your machine got compromised.

There's no evidence to suggest SSH has anything to do with this, but I recommend you run sshd on a non-standard port. Most bots will give up immediately when they can't get a connection on port 22.

---

### Post by Buckie_Bhoy on 2011-09-24
I asked her alright, but she claimed she never done anything.  Out of curiosity I logged in as guest and it created the same entries in the log, so she may well have done something.  Oh well, if anything the whole episode has made me somewhat more paranoid which can only be a good thing I suppose.

---

### Post by CharlesA on 2011-09-24
Too bad paranoia makes you loose your hair. ;)

---

### Post by Buckie_Bhoy on 2011-09-24
Started losing my hair a long time ago, funnily enough I think it was around the time I got married LOL

---

