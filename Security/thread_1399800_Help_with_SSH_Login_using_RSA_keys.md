---
title: "Help with SSH Login using RSA keys?"
date: 2010-02-06
forum: Security
---

### Post by clevertomato on 2010-02-06
I'm having trouble logging in with SSH using RSA keys.

client: Karmic
server: FreeNAS (FreeBSD) ip: 192.168.0.100

I generated RSA keys on Karmic, added the id_rsa.pub to the authorized_keys file on FreeNAS, then removed the id_rsa.pub from Karmic (this is a poorly documented but necessary step I learned).

My Karmic username is shawn, FreeNAS username is shawnboy.

When I do ```
ssh -l shawnboy 192.168.0.100
``` from Karmic it prompts me for my RSA key _passphrase_ which it should do, but after I enter it, it fails and moves on to prompt me for my _password_. The output for this section (using -vvv on the ssh command) is:

```
Enter passphrase for key '/home/shawn/.ssh/id_rsa': 
debug1: read PEM private key done: type RSA
debug3: sign_and_send_pubkey
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey,password
debug1: Trying private key: /home/shawn/.ssh/id_dsa
debug3: no such identity: /home/shawn/.ssh/id_dsa
debug2: we did not send a packet, disable method
debug3: authmethod_lookup password
debug3: remaining preferred: ,password
debug3: authmethod_is_enabled password
debug1: Next authentication method: password
shawnboy@192.168.0.100's password:
``` Just to make sure, I added```
RSAAuthentication yes
``` to the FreeNAS sshd_config even though it defaults to yes already. I know this isn't a FreeNAS forum, but this works perfectly using Putty SSH with RSA keys on Windows XP, so I figure it's more appropriate to ask here than in FreeNAS forums.

---

### Post by CharlesA on 2010-02-06
Make sure you have the private key in that directory.

If it is elsewhere you use -i switch to tell ssh where the key is.

After you get keys set up, it would be wise to disable password logons.

---

### Post by movieman on 2010-02-06
Check the sshd logs on the server: 99% of the time when you can't log in with an RSA key, it's because the permissions on your key files are incorrect on the server.

---

### Post by clevertomato on 2010-02-06
CharlesA: the private key in form of "id_rsa" file is there.
movieman: What permissions should I have set on which files / dirs?

---

### Post by movieman on 2010-02-06
> **shawnboy said:**
> movieman: What permissions should I have set on which files / dirs?

AFAIR .ssh and authorized_keys should only be readable by the owner: but the server logs will tell you if that's the problem.

---

### Post by CharlesA on 2010-02-06
> **movieman said:**
> AFAIR .ssh and authorized_keys should only be readable by the owner: but the server logs will tell you if that's the problem.

.ssh should be 700. (rwx owner). authorized_keys and known_hosts should be 644 (rw owner, r group, r others).

Taking a look at the logs will tell you what the problem is.

---

### Post by Jive Turkey on 2010-02-07
Another thing is if your home dir on the server is encrypted the server will not be able to validate the key unless you are already logged in and have unencrypted the authorized_keys file.  The workaround would be to change the location of the authorized_keys file on the server (and in sshd_config).  Another thing, the log output you have mentions "id_dsa" but you said your keys are "id_rsa".

---

### Post by clevertomato on 2010-02-07
Sorry folks, but it turns out it *was* a FreeNAS issue. I found the solution on the FreeNAS forums. It's not very straightforward, in my opinion, to setup SSH passwordless login on FreeNAS.

I don't know if this is breaking protocol, but maybe this will help someone else looking on these forums for the answer.

Taken from FreeNAS forums:

( again, **THIS IS FOR LOGGING INTO SSH SERVER RUNNING ON FREENAS, NOT UBUNTU** )
What you need to do to customize your server for passwordless authentication:

[LIST=a]
[*]From **WebGUI|Advanced|Execute command** or shell
[LIST=1]
[*]protect the /mnt directory by setting the mode to 755(we don't want users to write on /mnt, that can fill up the RAM disk and crash the system. 
You must change the mod as startup command, after each reboot.```
chmod 755 /mnt
```
[*]For your safety change the mode for each mount, or at least one "mount".```
chmod 755 /mnt/mount
```
[*]Create the user(A) home directory /mnt/mount/userA```
mkdir /mnt/mount/userAdir
```
[*]Make userA the owner of his home directory```
chown userA /mnt/mount/userAdir
```
[*]Secure userA home directory```
chmod 700 /mnt/mount/userAdir
```
[/LIST]
 
[*]Set userA home directory on **WebGUI|Access|Users|Edit|Home directory** to point to /mnt/mount/userAdir
[*]From your remote client(ssh/PuTTy)
[LIST=1]
[*]Check if home directory is set corectly for userA. The output should be /mnt/mount/userAdir```
ssh -p 22 userA@FreeNASip 'pwd'
```
[*]Create the .ssh directory```
ssh -p 22 userA@FreeNASip 'mkdir .ssh'
```
[*]Upload your id_rsa.pub or id_dsa.pub to remote .ssh directory.```
cat id_rsa.pub | ssh -p 22 userA@FreeNASip 'cat >> .ssh/authorized_keys'
```
[*]Change the .ssh dir mode```
ssh -p 22 userA@FreeNASip 'chmod -R 700 ~/.ssh'
```
[/LIST]
 
[*]Now try to login passwordless
[/LIST]

---

