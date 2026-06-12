---
title: "My 8.04 LTS box was hacked"
date: 2008-05-11
forum: Security
---

### Post by shawnerz on 2008-05-11
All,
My Linux box was hacked in to on 9 May.  The hacker (or bot-who knows) used ssh, and somehow got root access.  From there, he or she deleted /home.
Fortunatly, I don't have many users that log in to the computer.  Additionally, I think the hacker moved the data to another drive, then deleted /home.  Ethical hacker?
Anyway, I would like to know the error of my ways that allowed him (or her) in.
Here is my setup:
I am running 8.04 LTS.  In fact, I had upgraded 2 days beforehand.  It is up to date.
I have Firestarter firewall and fail2ban configured and enabled.
There are 2 hard drives in the system.  The main one has the OS and the second is mounted at boot.  It only contains the /home folders of all of the users except me and one or two other trusted users.
The hacker deleted /home on the second drive.

My questions:
What can I do to keep this from happening again?
I thought root was disabled by default?  When I go to Users and Groups, I see that root is enabled.  I do not see an option to disable the account.  If I try to delete it, Ubuntu says the OS will become unstable (understanibly).

Any comments and/or suggestions would be appreciated.
Thanks,
-Shawn

Here is auth.log an excerpt from auth.log:

May  9 07:56:35 localhost sshd[27450]: Received signal 15; terminating.
May  9 07:56:35 localhost sshd[20091]: Server listening on :: port 443.
May  9 07:56:35 localhost sshd[20091]: error: Bind to port 443 on 0.0.0.0 failed: Address already in use.
May  9 07:56:35 localhost sshd[20091]: Server listening on :: port 22.
May  9 07:56:35 localhost sshd[20091]: error: Bind to port 22 on 0.0.0.0 failed: Address already in use.
May  9 08:03:29 localhost sg[21556]: user `root' switched to group `slocate'
May  9 08:03:30 localhost sg[21556]: user `root' (login `???' on pts/1) switched to group `slocate'
May  9 08:03:30 localhost sg[21556]: user `root' (login `???' on pts/1) returned to group `root'
May  9 08:03:32 localhost groupadd[21567]: new group: name=mlocate, GID=126
May  9 08:17:01 localhost CRON[306]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  9 08:17:02 localhost CRON[306]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  9 08:17:02 localhost CRON[306]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  9 08:17:02 localhost CRON[306]: pam_unix(cron:session): session opened for user root by (uid=0)
May  9 08:17:02 localhost CRON[306]: pam_unix(cron:session): session closed for user root
May  9 08:21:44 celeron_633 groupadd[3299]: new group: name=polkituser, GID=127
May  9 08:21:44 celeron_633 useradd[3300]: new user: name=polkituser, UID=118, GID=127, home=/var/run/PolicyKit, shell=/bin/false
May  9 08:21:45 celeron_633 usermod[3301]: change user `polkituser' password
May  9 08:21:45 celeron_633 chage[3302]: changed password expiry for polkituser
May  9 08:21:45 celeron_633 chfn[3303]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  9 08:21:45 celeron_633 chfn[3303]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  9 08:21:45 celeron_633 chfn[3303]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  9 08:21:45 celeron_633 chfn[3303]: changed user `polkituser' information
May  9 08:36:13 celeron_633 sshd[5700]: Did not receive identification string from 75.147.113.234
May  9 08:46:46 celeron_633 sshd[5701]: reverse mapping checking getaddrinfo for 75-147-113-234-philadelphia.hfc.comcastbusiness.net [75.147.113.234] failed - POSSIBLE BREAK-IN ATTEMPT!
May  9 08:46:47 celeron_633 sshd[5701]: Invalid user staff from 75.147.113.234
May  9 08:46:47 celeron_633 sshd[5701]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  9 08:46:47 celeron_633 sshd[5701]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  9 08:46:47 celeron_633 sshd[5701]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  9 08:46:47 celeron_633 sshd[5701]: pam_unix(sshd:auth): check pass; user unknown
May  9 08:46:47 celeron_633 sshd[5701]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=75.147.113.234 
May  9 08:46:49 celeron_633 sshd[5701]: Failed password for invalid user staff from 75.147.113.234 port 51798 ssh2
May  9 09:17:01 celeron_633 CRON[5705]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  9 09:17:01 celeron_633 CRON[5705]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  9 09:17:01 celeron_633 CRON[5705]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  9 09:17:01 celeron_633 CRON[5705]: pam_unix(cron:session): session opened for user root by (uid=0)
May  9 09:17:02 celeron_633 CRON[5705]: pam_unix(cron:session): session closed for user root
May  9 10:15:16 celeron_633 sshd[5708]: Did not receive identification string from 212.123.91.195
May  9 10:17:01 celeron_633 CRON[5709]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  9 10:17:01 celeron_633 CRON[5709]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]

---

### Post by Monicker on 2008-05-12
The log snippet shows some failed attempts at connecting via ssh, but no successful login from a remote ip.

If you are really interested in finding out what happened, you should probably read over the Forensics section of the "Ubuntu Security" sticky thread for this forum.  Image it for further study, then rebuild from scratch.  You can't trust the system any longer if it truly was compromised.

---

### Post by daengbo on 2008-05-12
Agreed. Your logs show no intrusion, but they wouldn't if the guy knew how to clean up after himself. 

In Ubuntu, root doesn't have a usable password by default. You can't remove the user, but no one can log in as root. If there was a remote vulnerability, then the mad hatter could use that to get user-level access, then a local vulnerability to esclalate to root without a password. It's possible.

I'm more inclined to believe that no one actually broke in and that your problem with /home is related to something else, but if you believe (or even suspect) that someone broke in, you need to wipe everything and restore from May 8 backups.

I don't allow passwords on remote SSH. I use a non-default port. When I ran a web server in Korea a couple of years back, I got about 10,000 break-in attempts a day on Apache and SSH. You need to make sure that stuff is secure and updated. You need an IDS, too.

---

### Post by Puptentacle on 2008-05-12
As Monicker said, I see attempts in what you posted, but no actual entries. 

Also, you say you think the hacker moved the data. Is the data still present but in another directory? And my big question is WHY would a hacker do that? 

There has to be another explanation.

---

### Post by cdtech on 2008-05-12
A trusted user perhaps? :)

---

### Post by Dr Small on 2008-05-12
I don't see anywhere where there was any successful root logins. By the way, how do you have SSH setup?

If you really think it was an attacker, try checking around in some history files and see if you see anything. Most people forget about history, and might fail to clean it up.

Dr Small

---

### Post by lswest on 2008-05-12
i just wanted to mention, there are a few known exploits for 2.6.24 kernels that let you jump permissions, so try googling those and seeing if they work on your system.  Also, root is disabled by not supplying a password and preventing login from the system, the account does, however, exist.

Also, some people might recommend upgrading to the new 2.6.25 kernel via git, since it's supposedly more secure, but i'm not sure how stable it is at this point in time.

---

### Post by dsiembab on 2008-05-12
even though I don't believe this is relevant to the issue posted. 
I get the same messages in my log to this pam chick gets around and then the x-session gets stopped. does pam stand for pulse audio manager?

---

### Post by Monicker on 2008-05-12
> **dsiembab said:**
> I get the same messages in my log to this pam chick gets around and then the x-server crashes

The messages about pam_smbpass.so are a known issue in 8.04.  I do not believe they are relevant to the issue of whether the OP's machine was hacked or not.

---

### Post by eldragon on 2008-05-12
on defense of the not-a-hacker posture.
something similar happened to me on my notebook, i was reviewing different photomanagers, and gthumb was it (i dont remember which one exactly) moved some folders around when it hung up on me, i didnt realized until i killed the app and couldnt find anything anymore.
maybe something of this sort happened to you too.
its a good idea to move ports around. or disable password logins and allow only rsa(name?) logins. but thats quite cumbersome.

on my case, i cannot afford a different port than 22 since univ wont allow every port. rsa is a pain in the rearend, (i use it with my notebook, but allow password logins just in case i need it). so i just use really strong passwords. (and remember them ala rainman).
having backups on an external drive is a good idea too although a hacker with root access will be able to delete that if he pleases. (and finds it).

---

### Post by Oldsoldier2003 on 2008-05-12
> **eldragon said:**
> on defense of the not-a-hacker posture.
something similar happened to me on my notebook, i was reviewing different photomanagers, and gthumb was it (i dont remember which one exactly) moved some folders around when it hung up on me, i didnt realized until i killed the app and couldnt find anything anymore.
maybe something of this sort happened to you too.
its a good idea to move ports around. or disable password logins and allow only rsa(name?) logins. but thats quite cumbersome.

on my case, i cannot afford a different port than 22 since univ wont allow every port. rsa is a pain in the rearend, (**i use it with my notebook, but allow password logins just in case i need it**). so i just use really strong passwords. (and remember them ala rainman).
having backups on an external drive is a good idea too although a hacker with root access will be able to delete that if he pleases. (and finds it).

Unless every user account on that machine has a strong password, you have effectively negated any gains you have made by setting up public key authentication.

---

### Post by shawnerz on 2008-05-12
In reading over the responses, I guess my system was not hacked in to.
As puptentacle (and others) pointed out, it does seem odd that someone would copy a folder to another drive, then delete the original.
I do know that I installed HH (8.04) on the 6th or 7th of last week.
Would the installation process have moved data from /home on the second drive to /home on the primary drive?  My guess is that it would not.
I only had 5 user folders.  /mnt/oldhd is the path to get to the second hard drive.  As an example:
/mnt/oldhd/home/bob
/mnt/oldhd/home/jane
/mnt/oldhd/home/carol
/mnt/oldhd/home/john
/mnt/oldhd/home/jim

../home/bob had 50 MB of files and all of the others were empty (with the excpetion of the hidden . files)

I found that /bob had been moved to /home/shawn (my folder) and there was nothing in /mnt/oldhd.

It's possbile I could have backed up bob's folder under my folder, but I don't remember ever doing that - although I've lost a few brain cells over the last few months ;).

daengbo: What is an "IDS"?

Thanks,
-Shawn

---

### Post by TerryT on 2008-05-12
This is a very interesting post, as I've just had a related incident on one of my machines. Here is a snip of the auth.log file. It appears that someone was conducting a brute force login attack, and then bingo, they were able to login using the user id "guest". This was the original account that I created when doing a fresh install of 8.04. I created a password for sure for this account although perhaps it wasn't a very high quality password. But it seems to me that the attacker guessed my password on the first try, which seems doubtful. The thing that scares me is that I'm wondering if samba is using the same id (guest) for access.

Once the attacker logged in it appears that he/she tried to run a root kit but there is no evidence that this was successful.

Any comments would be much appreciated.

Thanks,
Terry

May  4 19:07:42 crow sshd[24606]: Invalid user admin from 221.141.2.233
May  4 19:07:42 crow sshd[24606]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  4 19:07:42 crow sshd[24606]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  4 19:07:42 crow sshd[24606]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  4 19:07:42 crow sshd[24606]: pam_unix(sshd:auth): check pass; user unknown
May  4 19:07:42 crow sshd[24606]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=221.141.2.233 
May  4 19:07:44 crow sshd[24606]: Failed password for invalid user admin from 221.141.2.233 port 42152 ssh2
May  4 19:07:51 crow sshd[24608]: Invalid user test from 221.141.2.233
May  4 19:07:51 crow sshd[24608]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  4 19:07:51 crow sshd[24608]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  4 19:07:51 crow sshd[24608]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  4 19:07:51 crow sshd[24608]: pam_unix(sshd:auth): check pass; user unknown
May  4 19:07:51 crow sshd[24608]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=221.141.2.233 
May  4 19:07:52 crow sshd[24608]: Failed password for invalid user test from 221.141.2.233 port 42631 ssh2
May  4 19:07:59 crow sshd[24611]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  4 19:07:59 crow sshd[24611]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  4 19:07:59 crow sshd[24611]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  4 19:07:59 crow sshd[24611]: Accepted password for guest from 221.141.2.233 port 43084 ssh2
May  4 19:07:59 crow sshd[24613]: pam_unix(sshd:session): session opened for user guest by (uid=0)
May  4 19:08:03 crow sshd[24613]: pam_unix(sshd:session): session closed for user guest

---

### Post by zerofool2005 on 2008-05-12
Yeh. He tried some passwords but they all failed. Make sure you use quite a strong password. And make sure any web services dont have permissions for /etc/shadow

---

### Post by hyper_ch on 2008-05-12
and use deny host or fail2ban

---

### Post by shawnerz on 2008-05-12
One thing I forgot to ask in my previous post:
What is "polkituser" and why does it have a group id?

I found some info concerning "polkit" ("policy kit"), but nothing about "polkituser".
I deleted user and group "polkituser" from my system.
-Shawn

---

### Post by eldragon on 2008-05-12
> **Oldsoldier2003 said:**
> Unless every user account on that machine has a strong password, you have effectively negated any gains you have made by setting up public key authentication.

im actually allowing ssh from 2 users, both are strong passwored.

the rsa idea is just because i hate to type passwords all the time :D
it wasnt set for security measures. but i get your point, and my post was actually misleading into thinking i was being running a more secure box.

---

### Post by zazuge on 2008-05-13
> **shawnerz said:**
> 
daengbo: What is an "IDS"?

Intrusion Detection Software
like snort and nessus
but you don't need them (only if you have a secure sensitive network) 
they use alot of ressources (like AntiVirus)

---

### Post by shawnerz on 2008-05-14
All,
I just thought I'd give an update.
In my ealier post I said that all of the /home folders under /mnt/oldhd/ was gone.
The reason: I had a drive failure.  The hard drive died.

Not being able to get to /home coupled with auth.log entries that I didn't fully understand made me think my system was hacked.

Thanks to everyone for their help.
-Shawn

---

### Post by yaztromo on 2008-05-15
> **TerryT said:**
> 7:42 crow sshd[24606]: Invalid user admin from 221.141.2.233
May  4 19:07:42 crow sshd[24606]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  4 19:07:42 crow sshd[24606]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  4 19:07:42 crow sshd[24606]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  4 19:07:42 crow sshd[24606]: pam_unix(sshd:auth): check pass; user unknown
May  4 19:07:42 crow sshd[24606]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=221.141.2.233 
May  4 19:07:44 crow sshd[24606]: Failed password for invalid user admin from 221.141.2.233 port 42152 ssh2
May  4 19:07:51 crow sshd[24608]: Invalid user test from 221.141.2.233
May  4 19:07:51 crow sshd[24608]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  4 19:07:51 crow sshd[24608]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  4 19:07:51 crow sshd[24608]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  4 19:07:51 crow sshd[24608]: pam_unix(sshd:auth): check pass; user unknown
May  4 19:07:51 crow sshd[24608]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=221.141.2.233 
May  4 19:07:52 crow sshd[24608]: Failed password for invalid user test from 221.141.2.233 port 42631 ssh2
May  4 19:07:59 crow sshd[24611]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  4 19:07:59 crow sshd[24611]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  4 19:07:59 crow sshd[24611]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  4 19:07:59 crow sshd[24611]: Accepted password for guest from 221.141.2.233 port 43084 ssh2
May  4 19:07:59 crow sshd[24613]: pam_unix(sshd:session): session opened for user guest by (uid=0)
May  4 19:08:03 crow sshd[24613]: pam_unix(sshd:session): session closed for user guest

Was the password something really simple like "guest" or "password". Maybe sheer luck?

---

### Post by yaztromo on 2008-05-15
A few things with your ssh config should mitigate this:

```

# Authentication:
LoginGraceTime 20
PermitRootLogin no
StrictModes yes
AllowUsers justputyourusernamehere

# What ports, IPs and protocols we listen for
Port 4530 # use a non-standard port

PermitEmptyPasswords no

```

If you're really paranoid disable sudo for your username and just use su for things you need root for. Then even if an intruder gains access via your username, they still need to get the root password to do anything really bad.

---

