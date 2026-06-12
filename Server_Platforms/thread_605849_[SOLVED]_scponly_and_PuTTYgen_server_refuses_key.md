---
title: "[SOLVED] scponly and PuTTYgen: server refuses key"
date: 2007-11-07
forum: Server Platforms
---

### Post by basherdesigns on 2007-11-07
I need some help fellas.

I've setup scponly and jailed the users to their home folders.  This is working great!  Now I want them to use a private/public key pair to authenticate.  I can not get this to work with a scponly user, it works fine with a regular user.

Here's what I do:
On Windows box, open puttygen.exe, generate the key pairs. Save the private key to Windows box as id_rsa.ppk

On Ubuntu 7.10 server, login as shell user (since scponly user can not shell in), sudo -i, then go to the scponly users home folder:
```
mkdir .ssh
chown scponlyuser .ssh
chmod 700 .ssh
echo "publickeycopiedfromputtygen" >> .ssh/authorized_keys2
chmod 600 .ssh/authorized_keys2 
```

Now back on Windows box I try to use psftp to login to Ubuntu server:
```
psftp servername -l scponlyuser -i id_rsa.ppk -pw passwd
Using username "scponlyuser".
Server refused our key
Remote working directory is /incoming
psftp>
```

Until I get this working I have left 'PasswordAuthentication yes' enabled in my sshd_config.

I'm not sure if scponly is not allowing the keys to pass or am I not creating the keys correctly.  Does anyone use scponly with Windows psftp clients?  I don't know what my next step is at this point.

Thanks!

---

### Post by ruibernardo on 2007-11-07
Hi,

maybe this can help you: [[SOLVED] SSH Keys and puTTY.]("http://ubuntuforums.org/showthread.php?t=507559")

---

### Post by basherdesigns on 2007-11-07
Ok. .I just figured it out. 

I set sshd to LogLevel DEBUG2 and looked thru thru auth.log and saw that scponly was causing the login attempts to look for the keys in the chrooted directory which is /incoming. Not in /home/username/.ssh/ rather /home/username/incoming/.ssh/

So to fix, I created the .ssh directory within the incoming/ directory, moved the keys into that folder and bamo!!!  Works great now! thank you for debug2 LogLevel eh!

Hope this helps someone else.

---

