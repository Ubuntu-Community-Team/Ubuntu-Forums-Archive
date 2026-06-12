---
title: "SSH Refuses RSA Keys. Always."
date: 2008-08-12
forum: Server Platforms
---

### Post by tekno1001 on 2008-08-12
I can't seem to get RSA keys to work, no matter how hard I try. Here's what I've done:

1) Run puttygen to produce a public and private 1024 RSA key
2) Passphrase the private key and save it to my hard drive
3) SSH onto my server and append the public key to: /home/user/.ssh/id_rsa.pub and /home/user/.ssh/authorized_keys
4) Chmod .ssh to 700 and authorized_keys to 600
5) Enable RSA key login in /etc/ssh/sshd_config
6) Instruct putty to use the private key to authorize
7) Logon

But I keep getting "Server refused our key" from both work and home. I have repeated this process several times per several online manuals, and to no avail. I've even tried generating the keys on the server. What's the deal? ](*,)

---

### Post by cdtech on 2008-08-12
Did you do:

**$ ssh-add**

If you get:

**Could not open a connection to your authentication agent.**

then your session is not running under the ssh-agent. You can get around this by restarting a new shell under the agent by running:

**ssh-agent bash**

where you can replace bash with the shell of your choice. Once you do this, you should be able to run **ssh-add** to load your key for that shell.

---

### Post by y@w on 2008-08-12
Ok, just thought I'd ask.. in between steps 5 and 6 you restarted sshd, correct?

---

### Post by tekno1001 on 2008-08-12
> **cdtech said:**
> Did you do:

**$ ssh-add**

If you get:

**Could not open a connection to your authentication agent.**

then your session is not running under the ssh-agent

No, I didn't. But ssh-agent is for managing private keys, right? The server only has a public key on it, and putty manages its own private keys.

> Ok, just thought I'd ask.. in between steps 5 and 6 you restarted sshd, correct?
Of course ;)

---

### Post by moonpup on 2008-08-12
Have you tried converting the public key you created on windows into an openssh format?

On the server where your public key is try the following:

ssh-keygen -i -f id_rsa.pub >> .ssh/authorized_keys

see if that works...

---

### Post by ilrudie on 2008-08-12
the keys should go in ~/.ssh/authorized_keys2

otherwise they won't work with ssh 2.0 protocol which almost all servers these days should be defaulting to.  also if you can find a proper ssh client and run it with the -v flag you can see where the login is failing.  not sure if there is an option like this in putty.

---

### Post by moonpup on 2008-08-12
Sorry for the confusion, I'm a Redhat admin and they no longer use that designation and make it simply authorized_keys. It is true that Ubuntu uses authorized_keys2, so put your public key there and if it still doesn't work, try the conversion I stated above.

---

### Post by ilrudie on 2008-08-12
> **moonpup said:**
> Sorry for the confusion, I'm a Redhat admin and they no longer use that designation and make it simply authorized_keys. It is true that Ubuntu uses authorized_keys2, so put your public key there and if it still doesn't work, try the conversion I stated above.

I'm not absolutely sure about redhat but in centOS 5.1 (which should be the same as Redhat Enterprise 5.1 right?) authorized_keys2 still works.  Perhaps its just not required by redhat anymore?

---

### Post by tekno1001 on 2008-08-12
> the keys should go in ~/.ssh/authorized_keys2

Ok. The documentation for putty states authorized_keys, but I will still gladly give this a try :)

> ssh-keygen -i -f id_rsa.pub >> .ssh/authorized_keys

see if that works... 

Hm. Haven't seen this anywhere... I'll give it a try when I get home.

---

### Post by Vivaldi Gloria on 2008-08-12
authorized_keys2 is used in older implementations of OpenSSH. This file is still consulted for backward compatibility, but it has been deprecated. Only authorized_keys should be used to store public keys for users. Multiple keys are allowed in authorized_keys.

---

### Post by tekno1001 on 2008-08-12
> authorized_keys2 is used in older implementations of OpenSSH. This file is still consulted for backward compatibility, but it has been deprecated. Only authorized_keys should be used to store public keys for users. Multiple keys are allowed in authorized_keys.

That's what I thought too, but I still tried authorized_keys2. It didn't work.

> ssh-keygen -i -f id_rsa.pub >> .ssh/authorized_keys

see if that works...
It didn't.

I'm getting really frustrated with this. Perhaps its time to reinstall and start from scratch. I really think that there is some sort of external ssh or rsa think somewhere on my drive that is gumming this up.

---

### Post by ilrudie on 2008-08-12
> **Vivaldi Gloria said:**
> authorized_keys2 is used in older implementations of OpenSSH. This file is still consulted for backward compatibility, but it has been deprecated. Only authorized_keys should be used to store public keys for users. Multiple keys are allowed in authorized_keys.

You are correct:
~/.ssh/id_dsa.pub
             Contains the protocol version 2 DSA public key for authentica-
             tion.  The contents of this file should be added to
             *~/.ssh/authorized_keys* on all machines where the user wishes to
             log in using public key authentication.  There is no need to keep
             the contents of this file secret.

from: [http://www.openbsd.org/cgi-bin/man.cgi?query=ssh-keygen&sektion=1](http://www.openbsd.org/cgi-bin/man.cgi?query=ssh-keygen&sektion=1)

Learn something every day!

Did you look to see if putty has verbose options so you can see where it fails or try ssh -v?[FONT=Verdana][/FONT]

---

### Post by moonpup on 2008-08-13
Let's start at the beginning... please post back your sshd_config file so we can see what you have in there. If the config file looks ok, then we can begin to look elsewhere for your problem. I see no need to re-install as this is most likely a configuration issue or the way you generated your keys.

---

### Post by tekno1001 on 2008-08-14
> Let's start at the beginning... please post back your sshd_config file so we can see what you have in there. If the config file looks ok, then we can begin to look elsewhere for your problem. I see no need to re-install as this is most likely a configuration issue or the way you generated your keys.

Alright, will do. As soon as I get home :)

So, I totally had this working last night. I could log on from local and remote networks and sftp files using RSA keys alone. 

However, I made the dumbass mistake of chmod ing /home/user/.ssh to a lower permission. SSH promptly entered rigor mortis. I promptly chmod ed back to 700, but everything remains dead.

I guess there's something to say for leaving well enough alone. I can't believe I did that.

---

### Post by moonpup on 2008-08-14
Was this a recursive (-R) chmod through your .ssh directory. Maybe you chmod'ed back at the directory level but not at the file level inside the .ssh directory. Take a look at your file permissions within the directory.

---

### Post by tekno1001 on 2008-08-15
> Was this a recursive (-R) chmod through your .ssh directory.

No, it was a standard straight-up chmod of the .ssh folder (literally "sudo chmod 600 /home/user/.ssh")

I'm having a hard time getting the config file over successfully, but it is the default file with the following changes:
```
Port: 42
PermitRootLogin: no
LoginGraceTime: 45
AllowUsers: user
X11Forwarding: no

```

Everything else is untouched.

---

### Post by jpfiset on 2008-08-15
Use the **/var/log/auth.log** to try to figure out why your key is not accepted.

Maybe you are using an older implementation of ssh-keygen and that the key was blacklisted by the recent SSH updates.

---

### Post by moonpup on 2008-08-15
> **tekno1001 said:**
> No, it was a standard straight-up chmod of the .ssh folder (literally "sudo chmod 600 /home/user/.ssh")

I'm having a hard time getting the config file over successfully, but it is the default file with the following changes:
```
Port: 42
PermitRootLogin: no
LoginGraceTime: 45
AllowUsers: user
X11Forwarding: no

```

Everything else is untouched.

If the only change you say you made was the chmod of the file permissions on the .ssh directory, then you need to look carefully at the permissions of the directory itself and the files inside. Please post back the file listing permissions on both the directory and files inside. Also, for good measure post your sshd config file as well.

We'll get this working sooner or later :)

---

### Post by tekno1001 on 2008-08-17
sshd_config:
```
~$ cat /etc/ssh/sshd_config
# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 42
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
LoginGraceTime 45
PermitRootLogin no
StrictModes yes
AllowUsers user

RSAAuthentication yes
PubkeyAuthentication yes
AuthorizedKeysFile      %h/.ssh/authorized_keys

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
#PasswordAuthentication yes

# Kerberos options
#KerberosAuthentication no
#KerberosGetAFSToken no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes

# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes

X11Forwarding no
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

UsePAM yes

```

> Please post back the file listing permissions on both the directory and files inside.

```
~$ ls -l /home/user/.ssh
total 8
-rw------- 1 root   root   208 2008-08-16 19:55 authorized_keys
-rw-r--r-- 1 user   user   442 2008-08-16 19:54 known_hosts

```
Note: How do I view the permissions of the .ssh directory?

> Use the /var/log/auth.log to try to figure out why your key is not accepted.

```
~$ cat /var/log/auth.log
Aug 16 19:49:30 ftpServer sshd[5303]: Server listening on :: port 22.
Aug 16 19:49:30 ftpServer sshd[5303]: error: Bind to port 22 on 0.0.0.0 failed: Address already in use.
Aug 16 19:50:09 ftpServer login[5355]: pam_unix(login:session): session opened for user user by LOGIN(uid=0)
Aug 16 19:50:24 ftpServer sudo:   user : TTY=tty1 ; PWD=/home/user ; USER=root ; COMMAND=/usr/bin/vi /etc/networking/interfaces
Aug 16 19:50:24 ftpServer sudo: pam_unix(sudo:session): session opened for user root by user(uid=0)
Aug 16 19:50:24 ftpServer sudo: pam_unix(sudo:session): session closed for user root

```

How do I view the blacklist? That could be a problem...

> We'll get this working sooner or later 

Thanks a million for all the time you are dedicating to this. Even if it doesn't work, I still really appreciate everything that's being done for me here :)

---

### Post by goexplode on 2008-08-17
This is just a thought, but have you checked your authorized_keys file to make sure that there are no extra line breaks? The entire key needs to be on one line. I've used putty to generate keys in the past and it seemed to add line breaks into the file. Removing the extra line breaks seemed to fix everything for me.

---

### Post by moonpup on 2008-08-18
To check permissions on the .ssh directory itself from within your home directory type the below and look at the .ssh. This will show all files in your home directory including hidden files/directories. 

```
ls -la
```

Also, why do you have a %h at the authorized_keys line in your sshd config file? It should simply read .ssh/authorized_keys

Change the above line in the sshd config file, save it and restart ssh. Everything else looks ok. Also, as the above person stated, open your authorized_keys file in a full screen console and make sure there are no extra spaces or line breaks in the key block of text.

One more thing... if you only want key based authentication make sure you change the PasswordAuthentication line to no

---

### Post by tekno1001 on 2008-08-18
```
~$ ls -la /home/user
total 28
drwxr-xr-x 3 user   user   4096 2008-08-16 19:54 .
drwxr-xr-x 3 root   root   4096 2008-08-16 19:45 ..
-rw------- 1 user   user   846 2008-08-16 21:14 .bash_history
-rw-r--r-- 1 user   user   220 2008-08-16 19:45 .bash_logout
-rw-r--r-- 1 user   user   2940 2008-08-16 19:45 .bashrc
-rw-r--r-- 1 user   user   586 2008-08-16 19:45 .profile
drwx------ 2 user   user   4096 2008-08-16 19:56 .ssh
-rw-r--r-- 1 user   user   0 2008-08-16 19:50 .sudo_as_admin_successful

```

> Also, why do you have a %h at the authorized_keys line in your sshd config file?
This is the default value

> have you checked your authorized_keys file to make sure that there are no extra line breaks? The entire key needs to be on one line. I've used putty to generate keys in the past and it seemed to add line breaks into the file.
Although 'cat /home/user/.ssh/authorized_keys' displays three lines of output, 'vi /home/user/.ssh/authorized_keys' displays it as one single line. There is a space character preceding the actual key, but removing it makes no difference.

> if you only want key based authentication make sure you change the PasswordAuthentication line to no
Of course :) I have it turned on while the server is rejecting keys so I can still ssh.

EDIT: I tried SSHing with a different client, WinSCP. It had the following to say:
```
. 2008-08-18 17:39:47.687 Waiting for the server to continue with the initialisation
. 2008-08-18 17:39:47.687 Detected network event
. 2008-08-18 17:39:47.734 Detected network event
. 2008-08-18 17:39:47.734 Server version: SSH-2.0-OpenSSH_4.7p1 Debian-8ubuntu1.2
. 2008-08-18 17:39:47.734 We claim version: SSH-2.0-WinSCP_release_4.1.6
. 2008-08-18 17:39:47.875 SSPI: acquired credentials for: userComp@HAL
. 2008-08-18 17:39:47.875 Constructed service principal name 'host/www.user.endofinternet.org'
. 2008-08-18 17:39:47.906 GSSKEX disabled: No credentials are available in the security package

. 2008-08-18 17:39:47.906 Using SSH protocol version 2
. 2008-08-18 17:39:47.906 Waiting for the server to continue with the initialisation
. 2008-08-18 17:39:47.906 Detected network event
. 2008-08-18 17:39:47.906 Doing Diffie-Hellman group exchange
. 2008-08-18 17:39:47.906 Waiting for the server to continue with the initialisation
. 2008-08-18 17:39:47.968 Detected network event
. 2008-08-18 17:39:47.968 Doing Diffie-Hellman key exchange with hash SHA-1
. 2008-08-18 17:39:48.140 Waiting for the server to continue with the initialisation
. 2008-08-18 17:39:48.328 Detected network event
. 2008-08-18 17:39:48.484 Asking user:
. 2008-08-18 17:39:48.484 The server's host key was not found in the cache. You have no guarantee that the server is the computer you think it is.
. 2008-08-18 17:39:48.484 
. 2008-08-18 17:39:48.484 The server's rsa2 key fingerprint is:
. 2008-08-18 17:39:48.484 ssh-rsa 2048 25:80:05:dc:c6:d5:5a:a2:e8:08:22:3c:0b:c3:3f:56
. 2008-08-18 17:39:48.484 
. 2008-08-18 17:39:48.484 If you trust this host, press Yes. To connect without adding host key to the cache, press No. To abandon the connection press Cancel.
. 2008-08-18 17:39:48.484 
. 2008-08-18 17:39:48.484 Continue connecting and add host key to the cache? ()
. 2008-08-18 17:39:51.125 Host key fingerprint is:
. 2008-08-18 17:39:51.125 ssh-rsa 2048 25:80:05:dc:c6:d5:5a:a2:e8:08:22:3c:0b:c3:3f:56
. 2008-08-18 17:39:51.125 Initialised AES-256 SDCTR client->server encryption
. 2008-08-18 17:39:51.125 Initialised HMAC-SHA1 client->server MAC algorithm
. 2008-08-18 17:39:51.125 Initialised AES-256 SDCTR server->client encryption
. 2008-08-18 17:39:51.125 Initialised HMAC-SHA1 server->client MAC algorithm
. 2008-08-18 17:39:51.125 Waiting for the server to continue with the initialisation
. 2008-08-18 17:39:51.125 Detected network event
. 2008-08-18 17:39:51.125 Reading private key file "C:\Documents and Settings\userComp\Desktop\user\vkey.ppk"
! 2008-08-18 17:39:51.125 Using username "user".
. 2008-08-18 17:39:51.125 Waiting for the server to continue with the initialisation
. 2008-08-18 17:39:51.156 Detected network event
. 2008-08-18 17:39:51.171 Offered public key
. 2008-08-18 17:39:51.171 Waiting for the server to continue with the initialisation
. 2008-08-18 17:39:51.171 Detected network event
! 2008-08-18 17:39:51.171 Server refused our key
. 2008-08-18 17:39:51.171 Server refused public key
. 2008-08-18 17:39:51.171 Prompt (6, SSH password, , &Password: )
. 2008-08-18 17:39:57.750 Sent password
. 2008-08-18 17:39:57.750 Waiting for the server to continue with the initialisation
. 2008-08-18 17:39:57.750 Detected network event
. 2008-08-18 17:39:57.750 Access granted
```
Okay, so I guess the public key is not being accepted? Does this mean that the problem is the key in .ssh/authorized_keys?

---

### Post by moonpup on 2008-08-19
At this point I would empty out your authorized_keys file, delete the keys from your .ssh directory and generate some new ones. Let us know how that works out... 

From looking at the above things look good, that's why I suggest trying new keys. Good luck!

---

### Post by ilrudie on 2008-08-19
At this point I'd agree with creating new keys.  Its been mentioned before but maybe putty simply generated a black listed key.

---

### Post by moonpup on 2008-08-21
So did you get this working? Please keep up posted :)

---

### Post by gizmobay on 2008-08-22
I just set this up and I had all kinds of problems with Putty. From linux to linux, everything worked well but when I tried from WinXP to linux Putty would reject me keys or disconnect me. I tried converting keys to both formats but Putty just said keys didn't work. In the end, I generated the new keys on the Ubuntu PC and added the pub key to the authorized_keys file I then moved my private key to winxp and then fired up puttygen and just loaded the private key and it converted it to putty format. I then saved the key and tried connecting and everything worked.

I followed the guides I found on the internet on Putty so I don't know if there's a hidden step I was missing something like ssh-add.

---

### Post by tekno1001 on 2008-08-28
Sorry for the delay everyone, a crisis came up... :)

> At this point I would empty out your authorized_keys file, delete the keys from your .ssh directory and generate some new ones.

Tried it. Twice. To no avail... :/

> In the end, I generated the new keys on the Ubuntu PC and added the pub key to the authorized_keys file I then moved my private key to winxp and then fired up puttygen and just loaded the private key and it converted it to putty format. I then saved the key and tried connecting and everything worked.

I did this before and it didn't work, but I haven't tried it recently... I'll give it another try.

---

### Post by gizmobay on 2008-09-05
I should've given a little more detail. I loaded the private key I generated on Ubuntu with puttygen.exe and this converted the private key into putty's format. I then saved the key and then started putty.exe and then put in the connect information and then I added the newly converted key under auth. I hit connect and everythin worked.

---

### Post by jerome1232 on 2008-09-05
When I had this problem and it was permisision related I had an entry in /var/log/auth.log that cleary indicated it was so.

```
sudo grep sshd /var/log/auth.log | less
```

looking for things that say permissions incorrect I forget the exact wording.

If it is permissions I found that these permsision are in all cases correct, in my case it was the group write on ~ that broke keys for me.

```
chmod go-w ~/
chmod 700 ~/.ssh
chmod 600 ~/.ssh/authorized_key
```

---

