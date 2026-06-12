---
title: "Password-less SSH key no longer unlocks"
date: 2009-05-09
forum: System76 Support
---

### Post by phyzome on 2009-05-09
I have a Pangolin (panp4i) that I recently upgraded from Intrepid to Jaunty, and I am now being prompted to enter a passphrase whenever I try to SSH out using Public Key authentication.

Some months ago I ran ssh-keygen to create an RSA keypair—with an empty passphrase—for remote authentication. I copied the public key to ~/.ssh/allowed_keys on the destination machine, aurail.ccs.neu.edu. After that, I could always just type `ssh aurail.ccs.neu.edu` and enter the machine instantly.

After the Jaunty upgrade, I am presented with a dialog box (see attachment) saying "Enter password to unlock the private key". If I leave the box empty, it pops back up. If I enter my Ubuntu login password, same results. If I hit deny, SSH defaults to password authentication.

How do I get rid of this box? Does it not know about password-less private keys, or what?

**Workaround:** Generate new keys. :-/

---

### Post by urasmm01 on 2009-05-20
I recently upgraded to Jaunty as well and have a password less ssh key. Every program that tries to use ssh in Gnome pops up a dialog to unlock the private key, even when I am connecting to servers which I have not setup the key pair for.

This is starting to sound like a bug.

---

### Post by apmcd47 on 2009-05-20
Not using Jaunty myself, but ...

Do you have a keyring or wallet set up? What happens when you use the passphrase for that?

Okay, I'm clutching at straws, here.

Andrew

---

### Post by urasmm01 on 2009-05-20
I didn't have a keyring or wallet setup that I knew about. When I was still running 8.10 I generated some public/private keypairs on the command line and installed them. Everything worked fine.

I upgraded to Jaunty, and Gnome started prompting with a dialog saying the private key 'myusername@mylaptopname' was locked and it asked for a password. I didn't setup passwords on the keys, and it wouldn't accept an empty response. I tried my user password, and that didn't work. I ended up pressing Deny, and then it would prompt for the password to the server I was trying to connect to, like it gave up on using the SSH keys, BUT it wouldn't take my password. I couldn't get into the server.

I just finished some searching, and I found this post that tells how to disable the gnome-keyring from setting itself as the SSH agent: [http://ubuntuforums.org/showthread.php?t=796410](http://ubuntuforums.org/showthread.php?t=796410).

1. run ```
gconf-editor
```
2. Navigate to apps->gnome-keyring->daemon-components
3. Uncheck the boxes next to ssh and pkcs11
4. Quit
5. Logout and login again or reboot the machine.

I just tried this and it works.

I see a similar bug reported in the Gnome Bugzilla: [http://bugzilla.gnome.org/show_bug.cgi?id=516097](http://bugzilla.gnome.org/show_bug.cgi?id=516097) and I saw a ton of bugs all related to the gnome-keyring at [https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/](https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/).

(On a side note, it also fixed the issue I was having with VirtualBox not resizing my Windows desktop. Guess the gnome-keyring was interfering there as well.)

---

### Post by apmcd47 on 2009-05-21
Glad you found the problem and solution. Looks like I was on the right track with my suggestion.

Phyzome, did the above solution help you?

Andrew

---

### Post by phyzome on 2010-03-08
> **apmcd47 said:**
> Phyzome, did the above solution help you?

Sorry for the late reply, I've only just now been able to upgrade Intrepid -> Karmic.

So... no, it doesn't help. Sure, it keeps the Gnome agent from popping up, but ssh still asks for my passphrase and won't allow me to use my empty passphrase.

---

### Post by jdb on 2010-03-08
> **phyzome said:**
> Sorry for the late reply, I've only just now been able to upgrade Intrepid -> Karmic.

So... no, it doesn't help. Sure, it keeps the Gnome agent from popping up, but ssh still asks for my passphrase and won't allow me to use my empty passphrase.

I don't know what the problem is, but here's my config file if you want to do a stare & compare.

```
#	$OpenBSD: ssh_config,v 1.23 2007/06/08 04:40:40 pvalchev Exp $

# This is the ssh client system-wide configuration file.  See
# ssh_config(5) for more information.  This file provides defaults for
# users, and the values can be changed in per-user configuration files
# or on the command line.

# Configuration data is parsed as follows:
#  1. command line options
#  2. user-specific file
#  3. system-wide file
# Any configuration value is only changed the first time it is set.
# Thus, host-specific definitions should be at the beginning of the
# configuration file, and defaults at the end.

# Site-wide defaults for some commonly used options.  For a comprehensive
# list of available options, their meanings and defaults, please see the
# ssh_config(5) man page.

Host *
PubkeyAuthentication yes
#   ForwardAgent no
#   ForwardX11 no
RhostsRSAAuthentication no
RSAAuthentication no
PasswordAuthentication no
HostbasedAuthentication no
GSSAPIAuthentication no
GSSAPIDelegateCredentials no
#   BatchMode no
CheckHostIP no
#   AddressFamily any
#   ConnectTimeout 0
StrictHostKeyChecking no
#   IdentityFile ~/.ssh/identity
#   IdentityFile ~/.ssh/id_rsa
#   IdentityFile ~/.ssh/id_dsa
#   Port 22
#   Protocol 2
#   Cipher 3des
#   Ciphers aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour,aes192-cbc,aes256-cbc
#   MACs hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160
#   EscapeChar ~
#   Tunnel no
#   TunnelDevice any:any
#   PermitLocalCommand no
HashKnownHosts no

```

jdb

---

### Post by phyzome on 2010-03-13
I believe that it has something to do with old and new formats. ssh-keygen won't recognize my old keys (insists on having a passphrase), but I can generate new ones that work. I think I just need to generate new keys for myself. :-/

---

### Post by spikyjt on 2010-05-07
Were your keys blacklisted? There was a bug some time back that allowed keys to be generated that were not very random at all. Any keys generated before the patch were blacklisted. Perhaps your keys were generated before that and the updated servers would not accept them due to the blacklist?

---

### Post by phyzome on 2010-05-08
> **spikyjt said:**
> Were your keys blacklisted? 

I'm sure I would have found out very quickly after the blacklist file was released.

---

### Post by sefs on 2010-12-11
What was your solution, the thread says solved but no solution is posted.

Thanks.

---

### Post by phyzome on 2010-12-11
> **sefs said:**
> What was your solution, the thread says solved but no solution is posted

Ack, sorry about that. It was a while ago, but I believe I finally created new keys. Not ideal, but it worked.

---

