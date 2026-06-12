---
title: "Replacing a possibly compromised OpenSSH key?"
date: 2010-09-22
forum: Security
---

### Post by laeg_ on 2010-09-22
I have an OpenSSH server running on Ubuntu 10.04, and it works fine. 

I'm concerned that my SSH key may have been compromised and would like to replace it.

I tried replacing keys before and reinstalling OpenSSH and SSH before but ran into terrible trouble so I'm asking for instruction before touching anything this time.

```
laeg@skyrocket:~/.ssh$ ls
authorized_keys  id_rsa  id_rsa.ppk  id_rsa.pub  known_hosts
```


```
laeg@skyrocket:/etc/ssh$ ls
ssh_config.dpkg-dist  sshd_config.factory-defaults  ssh_host_rsa_key
sshd_config	      ssh_host_dsa_key		    ssh_host_rsa_key.pub
sshd_config~	      ssh_host_dsa_key.pub
```

If relevant the only place I've ever SSH connected to from this box, is this box. The only thing I'd like to keep is the actual config of the server because I spent some time customizing it.

So can I just synpaptic 'fully' uninstall SHH (although probably even less necessary than..) and OpenSHH, backup sshd_config, delete the two dirs referenced above, reinstall both packages, insert my sshd_config backup, and then start from scratch following the guides linked below?

[Open SSH Server Guide]("https://help.ubuntu.com/9.04/serverguide/C/openssh-server.html")

[Configuring an OpenSSH Server]("https://help.ubuntu.com/community/SSH/OpenSSH/Configuring")

[SSH Key Authentication]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys")

---

### Post by CharlesA on 2010-09-22
You don't need to uninstall/reinstall SSH. Just generate a new key with:

```
ssh-keygen
```

Then try to connect with the new key and remove the old key if it works.

You could also do this:

Backup authorized_keys and just cat the new key into authorized_keys then restart ssh.

**Don't close out the current ssh session until you've verified that the new key allows you to connect, else you'll be locked out if the new key didn't take.**

```
cat id_rsa.pub > authorized_keys && sudo service ssh restart
```

---

### Post by laeg_ on 2010-09-22
> **CharlesA said:**
> You don't need to uninstall/reinstall SSH. Just generate a new key with:

```
ssh-keygen
```

Then try to connect with the new key and remove the old key if it works.

You could also do this:

Backup authorized_keys and just cat the new key into authorized_keys then restart ssh.

**Don't close out the current ssh session until you've verified that the new key allows you to connect, else you'll be locked out if the new key didn't take.**

```
cat id_rsa.pub > authorized_keys && sudo service ssh restart
```


Sorry, I should have mentioned this is my home box that the server is running on, so I'm on it now and have no problem accessing it when in front of it.

I was hoping to make the changes here when logged in to the desktop, and then take the id_rsa to work, change to be a .ppk at work on the windows box, and then SSH once again from work. 

Now knowing this, is there another way I should go about this? I can't test any keys until I'm next in there on Sunday, surely there's a way to do this in such a way that the new created key will just work?

---

### Post by CharlesA on 2010-09-22
You can test the keys locally. ;)

But if you added the public key to authorized_keys and converted the private key to a ppk, you are good to go. :)

---

### Post by laeg_ on 2010-09-22
> **CharlesA said:**
> You can test the keys locally. ;)

But if you added the public key to authorized_keys and converted the private key to a ppk, you are good to go. :)

> **CharlesA said:**
> You can test the keys locally. ;)

But if you added the public key to authorized_keys and converted the private key to a ppk, you are good to go. :)

To clarify, can I just delete from ~/.ssh; authorized_keys, id_rsa, id_rsa.ppk, id_rsa.pub and known_hosts, and from /etc/ssh; ssh_host_dsa_key, ssh_host_dsa_key.pub, ssh_host_rsa_key and ssh_host_rsa_key.pub, and then just create the keys again? I can't remember whether it was rsa or dsa I used, but it won't hurt to delete both sets, right?

---

### Post by CharlesA on 2010-09-22
Not exactly.

You only need to remove the old key from authorized_keys and add the new one.

You don't need to remove the entire .ssh directory.

EDIT: To clarify, you don't usually touch anything in the /etc/ssh/ directory unless you are editing ssh_config (ssh client config) or sshd_config (ssh daemon config).

This is what my ~/.ssh/ directory looks like:

```
charles@luna:~$ ls -l .ssh
total 12
-rw------- 1 charles charles  386 2010-09-22 08:14 authorized_keys
-rw------- 1 charles charles 1675 2010-09-22 08:18 id_rsa
-rw-r--r-- 1 charles charles  394 2010-09-22 08:18 id_rsa.pub

```

When you run ssh-keygen, it'll ask to overwrite your current id_rsa file and overwrite id_rsa.pub automatically. It also defaults to RSA keys, if you don't specify DSA.

All you would need to do is cd into the .ssh directory and use this:

```
cat id_rsa.pub > authorized_keys
```

---

### Post by laeg_ on 2010-09-22
> **CharlesA said:**
> Not exactly.

You only need to remove the old key from authorized_keys and add the new one.

You don't need to remove the entire .ssh directory.

EDIT: To clarify, you don't usually touch anything in the /etc/ssh/ directory unless you are editing ssh_config (ssh client config) or sshd_config (ssh daemon config).

This is what my ~/.ssh/ directory looks like:

```
charles@luna:~$ ls -l .ssh
total 12
-rw------- 1 charles charles  386 2010-09-22 08:14 authorized_keys
-rw------- 1 charles charles 1675 2010-09-22 08:18 id_rsa
-rw-r--r-- 1 charles charles  394 2010-09-22 08:18 id_rsa.pub

```

It'll ask to overwrite your current id_rsa file and overwrite id_rsa.pub automatically. All you would need to do is cd into that directory and use this:

```
cat id_rsa.pub > authorized_keys
```

I have 5 lines of text in there starting but only one string 'ssh-rsa', does that mean I just delete all the text in that file, create the keys again which will just overwrite the old keys and delete them?

I know I'm asking lots of questions, and appreciate your help.

---

### Post by CharlesA on 2010-09-22
What it looks like?

It should look like this:

```
ssh-rsa AAAAB3NzaC1yc2EAAAABIwAAAQEAx2TEd9QFNY0h1RawjoplwXdnwHh0TJ4PxDPUNF3Qx9VnfjnLimgQy5R0WHhz1Yp/ASSYW+loL8U0jFvjJelC5BAoxL5Uw8T81oUEwtX8m7Jj0HxASRAe8xjcLLl06Cd878wk0pn7TkQo8tLoGwx4SIpgnpDJAlF2bDKmkwp+TDE0gAE9CT15GfnOYu+vS4YdVP+xpf+sOTU7+AYEB0KCCpMxSN6mLCVfBnmbd6qqAZM3P6x5SiT11UkdKt7Dk/+/X8lTLwgAj1kGYwfNR2QFAJ9W3ETq+IvBYDIudOnPKXjiH7xx3KLPsjxPqKwxGLMbAO8DgYMEYlqQFR/x4GuhiQ== charles@luna

```

Note: That's the public key, so there's no security risk in posting that one.

---

### Post by laeg_ on 2010-09-22
> **CharlesA said:**
> What it looks like?

It should look like this:

```
ssh-rsa AAAAB3NzaC1yc2EAAAABIwAAAQEAx2TEd9QFNY0h1RawjoplwXdnwHh0TJ4PxDPUNF3Qx9VnfjnLimgQy5R0WHhz1Yp/ASSYW+loL8U0jFvjJelC5BAoxL5Uw8T81oUEwtX8m7Jj0HxASRAe8xjcLLl06Cd878wk0pn7TkQo8tLoGwx4SIpgnpDJAlF2bDKmkwp+TDE0gAE9CT15GfnOYu+vS4YdVP+xpf+sOTU7+AYEB0KCCpMxSN6mLCVfBnmbd6qqAZM3P6x5SiT11UkdKt7Dk/+/X8lTLwgAj1kGYwfNR2QFAJ9W3ETq+IvBYDIudOnPKXjiH7xx3KLPsjxPqKwxGLMbAO8DgYMEYlqQFR/x4GuhiQ== charles@luna

```

Note: That's the public key, so there's no security risk in posting that one.

```
ssh-rsa AAAAB3NzaC1yc2EAAAABIwAAAgEAwFbRj5kUcXK0VGG7FA1fqfMdkSPNfH4tPuJz5yj+kB3SCobLZIjXKB7zabjH8YIQbsAXBgVrkM3yLXtK0q/8lXud4dfzhZxTVLL6nnfy38QMXaKITrpPmzF2K7nMTCZRqt99GUIlXZtsEtYx3Yu0fmSJw05tZ91coFwzhlZvYxu5bSllleX1l+cSjfGF/tUk+nteaA5bKI4FqQKnMySX8oTLynO8RfNbQIP19qTkuymMl/LtOaivj1AiTgOr1Wj0PfnQGaM7wcVVpFEAAZVs0oiWCQ5JFY+l+ri3GffROhxXU2xWBHh/yMUH8tS9NyEiBQ2LgPKK2s0kOYMowVo4v1yBo3nKwd7umma4oKzQ2uCLm9YSQHIAy9MifFXtEgGvfQrLCste8CimYlFUSR7dKH2EZip/qw5HrHk0NmE6WuSXFeq6agrTfXmplDFMgRXGegGo51hRKwKA8CcGWg04Bdz8353oETuCNBt2/x/v3R9daCJQfsr8X9zV1MrgFdAYe2CeauiM1ZbN0+V0NMxZZdk/dO6sGVZXN+JsWxb5mIq+WruXWibzVk6U3kHEaIqF4/n23cu3xq1Qx1DWyeBlqG2wlUcph9VsnG7T9TQy8ZuCSXaAXDg78R9pXAkpCHFpDJ5IsUX+jaoMy18G6+NL82TXY2u6XZBHr5Y2IhCsv5k= laeg@skyrocket
```

---

### Post by CharlesA on 2010-09-22
Yup that's just one line of text. You can delete it with yer favorite editor, or just overwrite it using: ```
cat id_rsa.pub > authorized_keys
```

---

### Post by laeg_ on 2010-09-22
> **CharlesA said:**
> Not exactly.

You only need to remove the old key from authorized_keys and add the new one.

You don't need to remove the entire .ssh directory.

EDIT: To clarify, you don't usually touch anything in the /etc/ssh/ directory unless you are editing ssh_config (ssh client config) or sshd_config (ssh daemon config).

This is what my ~/.ssh/ directory looks like:

```
charles@luna:~$ ls -l .ssh
total 12
-rw------- 1 charles charles  386 2010-09-22 08:14 authorized_keys
-rw------- 1 charles charles 1675 2010-09-22 08:18 id_rsa
-rw-r--r-- 1 charles charles  394 2010-09-22 08:18 id_rsa.pub

```

When you run ssh-keygen, it'll ask to overwrite your current id_rsa file and overwrite id_rsa.pub automatically. It also defaults to RSA keys, if you don't specify DSA.

All you would need to do is cd into the .ssh directory and use this:

```
cat id_rsa.pub > authorized_keys
```

wouldn't that just add the new key to the old one, why not delete the old one altogether if i fear it may have been compromised?

---

### Post by CharlesA on 2010-09-22
Nope. The > redirect overwrites whatever you send it to. The >> redirect appends. :)

---

### Post by laeg_ on 2010-09-22
Okay dude, thanks again for explaining everything step by step.

Like I said, won't be able to test til Sunday when I next have to sit in front of a Windows box but I'll post in thread how I get on :)

---

### Post by CharlesA on 2010-09-22
It should work fine. :)

---

