---
title: "I absolutely cannot get SSH key authentication to work."
date: 2013-02-08
forum: Server Platforms
---

### Post by drew870mitchell on 2013-02-08
I'm trying to use an SSH key pair to log into a remote Ubuntu 12.04 server from Putty on Windows.  I keep getting "Server refused our key." Here are the steps that I have taken:


[LIST=1]
[*]Repeated several tutorials
[*]Loaded key in Putty config and/or Pageant
[*]~ is encrypted when logged out; moved .ssh/authorized_keys to /etc/ssh/publickeys/authorized_keys (and changed sshd_config)
[*]My user on remote host owns publickeys/ and authorized_keys
[*]I have tried chmod 700, 600, 644, and any other mode suggested on Google searches for this
[*]I copy/pasted from Puttygen to add the public key to authorized_keys and made sure the extra lines were not present
[*]I SFTP'd the Puttygen public key file to publickeys/
[*]I used ssh-keygen to generate the pair on the remote host and transfer the private key from there to my desktop (I know this is bad practice) and then used puttygen to convert it to .ppk
[/LIST]
None of the above has worked and I've done this (generated and used key pair for login) before successfully on OS X and Ubuntu Desktop.


auth.log shows this:


```
time host sshd: error: key_read: uudecode ...public key\n... failed

```


I can't find anything relevant to this online.  Help?

---

### Post by CharlesA on 2013-02-08
Keys are user specific. What are the permissions of /etc/ssh/publickeys/ ?

Could check here too, but I don't think it's the same problem. [http://serverfault.com/questions/172156/why-isnt-my-public-key-allowing-me-to-sign-in-without-a-password](http://serverfault.com/questions/172156/why-isnt-my-public-key-allowing-me-to-sign-in-without-a-password)

---

### Post by papibe on 2013-02-08
Hi drew870mitchell. Welcome to the forums ):P

I've have success generating the keys on Putty, and then pasting the public part on the Linux system.

Did you restart the ssh service after modifying the ssh config file?

Could you post the result of this command?
```
grep -i keysfile /etc/ssh/sshd_config
```
Regards.

---

### Post by CharlesA on 2013-02-08
> **papibe said:**
> 
I've have success generating the keys on Putty, and then pasting the public part on the Linux system.

You have better luck than me. ;)

I've always had to generate the keys via ssh-keygen and convert them with PuTTYgen.

---

### Post by sandyd on 2013-02-08
> **CharlesA said:**
> You have better luck than me. ;)

I've always had to generate the keys via ssh-keygen and convert them with PuTTYgen.

+1
Had to do that too, esp with the amazon EC2 keys...

---

### Post by papibe on 2013-02-08
If you are interested, this [video]("http://www.youtube.com/watch?v=ioGYnsxzL94") describes the method I've used.

First, you left out the last line of the public key. Then you merge the two reminding lines into one.

Regards.

---

### Post by steeldriver on 2013-02-08
This walkthrough worked for me

[https://help.ubuntu.com/community/SSH/OpenSSH/Keys#Troubleshooting]("https://help.ubuntu.com/community/SSH/OpenSS/Keys#Transfer_Client_Key_to_Host")

I used puttygen on a Win7 box, then copied + pasted the key to /etc/ssh/*user*/authorized_keys using nano in a regular password-based putty session; then edited /etc/ssh/sshd_config to add
```
AuthorizedKeysFile    /etc/ssh/%u/authorized_keys
```and restarted the ssh service. Ownership and permissions that worked for me are user:user 755 for /etc/ssh/*user*  and user:user 644 for /etc/ssh/*user*/authorized_keys

```
$ ls -al /etc/ssh/steeldriver/                                    
total 12
drwxr-xr-x 2 steeldriver steeldriver 4096 Feb  9 01:15 .
drwxr-xr-x 3 root    root    4096 Feb  9 01:14 ..
-rw-r--r-- 1 steeldriver steeldriver  226 Feb  9 01:21 authorized_keys

```

---

### Post by drew870mitchell on 2013-02-10
Thanks all, I used ssh-keygen to make another pair on the remote host and then moved it to /etc/ssh/publickeys.  I guess out of the combinations of Puttygen, ssh-keygen, /home/%u/.ssh/, /etc/ssh/publickeys, I had missed that one.

Will mark thread as solved.  It seems a lot of people have issues with Puttygen-generated pairs; can anyone venture a guess why?

Thanks
drew870mitchell

edit: Another tiny question not worth its own thread:  are there any potential security risks from using a VM on my Windows box to log on to the remote host?

---

### Post by CharlesA on 2013-02-10
I don't know. In my case, I found it a lot easier to just generate the key on a *nix box and convert it.

*shrugs*

---

