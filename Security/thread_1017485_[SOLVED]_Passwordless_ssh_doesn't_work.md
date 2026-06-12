---
title: "[SOLVED] Passwordless ssh doesn't work"
date: 2008-12-21
forum: Security
---

### Post by SiHa on 2008-12-21
I'm confused. I'm sure I've done something fundamentally stupid, but I can't fathom what it is.
Let me start by saying that I'm relatively new to linux, and this is my first foray any any sort of public/private key encryption, so I may be hazy on the terminology.

I'm trying to setup passwordless ssh authorization, I have done as follows.

On the host machine, I have run **ssh-keygen** and **ssh-keygen -t dsa** to create both dsa & rsa keys (rsa wasn't working, so I added dsa just in case). I have copied **~/.ssh/id_rsa.pub** to **~/.ssh/authorized_keys** on the remote machine, and added the contents of **~/.ssh/id_rsa.pub** on the second line.

According to the manpages, I should now be able to ssh from the remote machine to the host```
ssh mythbox@ip.address.of.host
```

But I'm still prompted for the password. If I ssh with the -v switch, I get the following:```
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /home/numpty/.ssh/identity
debug1: Trying private key: /home/numpty/.ssh/id_rsa
debug1: Offering public key: /home/numpty/.ssh/id_dsa
debug1: Server accepts key: pkalg ssh-dss blen 434
debug1: Next authentication method: password

```
where 'numpty' is the remote machine.

I'm guessing the problem is that the usernames are different on both machines ('numpty' on remote, 'mythbox' on host), but how to resolve this?

I'm stumped.

Very grateful for any help. Thanks.

---

### Post by koenn on 2008-12-21
> **SiHa said:**
>  I have copied **~/.ssh/id_rsa.pub** to **~/.ssh/authorized_keys** on the remote machine, and added the contents of **~/.ssh/id_rsa.pub** on the second line.
could you rewrite that  using absolute paths (with real user names) in stead of ~ ? 
~ is meaningless because it refers to "home of the currently logged in user" - could be anywhere ...

Other things to check:
did you set 'PubkeyAuthentication yes ' in the destination host's sshd_config ?
do you have permissions 600 on .ssh/authorized_keys (assuming it's in the right place to begin with).

---

### Post by SiHa on 2008-12-21
Hi Koenn,

Sorry - I just used the same terminlogy as in the ssh manpages.

Anyhow...

On the host machine, which autologs in as mythbox, the keys **/home/mythbox/.ssh/id_rsa.pub & /home/mythbox/.ssh/id_dsa.pub** are generated when I run ssh-keygen.
These keys are both copied to the remote machine, which autologs in as numpty, into  **/home/numpty/.ssh/authorized_keys**
This file looks like this:```
ssh-rsa AAAAB3N......= mythbox@mythbox-desktop
ssh-dss AAAAB3N......= mythbox@mythbox-desktop
```

I've now put the **authorized_keys** file on both machines - /home/mythbox/.ssh (host) & /home/numpty/.ssh (remote). I thought it needed to go on the remote machine, but I'm not so sure now.


I didn't have **'PubkeyAuthentication yes'**, I do now, thanks.
**authorized_keys** had permissions 644, I changed it to 600, but it made no difference.

Thanks so far...

---

### Post by koenn on 2008-12-21
hm, looks like the key part looks OK but the rest of the configuration needs work, or checking 
Assuming you're remote system is recent enough to support rsa, you'll need

on mythbox
- /home/mythbox/.ssh/id_rsa
- /home/mythbox/.ssh/id_rsa.pub

on the remote system
- /home/numpty/.ssh/authorized_keys containing mythbox's id_rsa.pub
- /home/numpty/.ssh should have 700 perms, owned by numpty
- /home/numpty/.ssh/authorized_keys should have 600 perms, owned by numpty
the file system permissions matter because ssh won't trust the keys if any user can edit them. 

- /etc/sshd/sshd_config  should contain
RSAAuthentication yes
PubkeyAuthentication yes
    			
I thought this were defaults on Debian and Ubuntu; what are you using ? 

sshd_config could also mention something about version - you need ssh v2 for rsa to work.

make sure remote sshd re-reads the modified configuration file, by restarting it :
/etc/init.d/ssh restart

if it still doesn't work, look in /var/log/auth for indications.

---

### Post by hyper_ch on 2008-12-21
on the local system run:

```

ssh-keygen -t dsa

```

then run on the local system
```

cat ~/.ssh/id_dsa.pub | ssh -l REMOTE_USER REMOTE_SERVER 'cat >> ~/.ssh/authorized_keys'

```

That's it.

Of course replace REMOTE_USER and REMOTE_SERVER with the actual values.

---

### Post by SiHa on 2008-12-21
Koenn / hyper_ch

Thanks both, turns out I had been a bit silly (my PC is called 'Numpty' for a reason!)

I'd got confused about what box wanted what, and I'd created the keys on the server (ie the box I wanted to connect **to**) and copied them to **authorized_keys** on the box I wanted to connect **from**. As I said in the OP this is my first outing into the whole field of public key encryption. I finally found the official pages on the Ubuntu Community Documentation, and I sorted it in the end.

->  /etc/sshd/sshd_config should contain
RSAAuthentication yes
PubkeyAuthentication yes

I thought this were defaults on Debian and Ubuntu; what are you using ? 
Ubuntu 8.04 AMD64. 

'RSAAuthentication yes' was OK, but 'PubkeyAuthentication' I'm sure said 'no', but I'm starting to doubt myself now...:confused:

Anyway thread solved, thanks both for your help.

---

### Post by abhinavshiva on 2013-05-01
For any other user apart from root, the permission for .ssh folder should be 700 (recommended is that one should keep permission of .ssh folder for root 700 for security reasons).
Below folder .ssh permission for my local user abhinav.

[root@server1 abhinav]# ls -ld .ssh
drwx------ 2 abhinav abhinav 4096 May  1 18:16 .ssh
[root@server1 abhinav]#




> **SiHa said:**
> Koenn / hyper_ch

Thanks both, turns out I had been a bit silly (my PC is called 'Numpty' for a reason!)

I'd got confused about what box wanted what, and I'd created the keys on the server (ie the box I wanted to connect **to**) and copied them to **authorized_keys** on the box I wanted to connect **from**. As I said in the OP this is my first outing into the whole field of public key encryption. I finally found the official pages on the Ubuntu Community Documentation, and I sorted it in the end.

-
Ubuntu 8.04 AMD64. 

'RSAAuthentication yes' was OK, but 'PubkeyAuthentication' I'm sure said 'no', but I'm starting to doubt myself now...:confused:

Anyway thread solved, thanks both for your help.

---

### Post by codemaniac on 2013-05-01
Old thread, closed now.

---

### Post by matt_symes on 2013-05-01
Old thread so **closed**.

Please don't post in threads older than a year if they have not had any reply in that time.

---

