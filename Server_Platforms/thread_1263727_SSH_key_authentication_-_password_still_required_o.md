---
title: "SSH key authentication - password still required once."
date: 2009-09-11
forum: Server Platforms
---

### Post by habrys on 2009-09-11
I set up SSH key authentication from mu Ubuntu client machine to Ubuntu server using this guide:
[https://help.ubuntu.com/9.04/serverguide/C/openssh-server.html](https://help.ubuntu.com/9.04/serverguide/C/openssh-server.html)

It went well, but I still have to provide password the first time I connect to the server (opening the first terminal window). Sessions in the second and next terminal windows connect without password now (which was not the case before setting up SSH keys). Both machines are Ubuntu 9.04, client is 32-bit, server 64-bit.

I have another mini-server called bubba, which runs under Debian Lenny on an Arm processor. I performed exactly the same steps to set up SSH keys there and don't have this strange behaviour with first session there. I never have to provide password to open a session.

I compared /etc/ssh/sshd_config files between both machines and didn't find any differences. 

**What can be the cause of this strange phenomenon? Where can I look for more hints?**

---

### Post by Menthu_Rae on 2009-09-11
Is it asking for the password to **unlock the key**?

This would perform as you describe... unlock key once, then you can connect again without putting in the key...

Make sure you have the same settings as this site:

[http://www.debuntu.org/ssh-key-based-authentication](http://www.debuntu.org/ssh-key-based-authentication)

---

### Post by habrys on 2009-09-11
No, I entered an empty passphrase creating the keys.

I even changed the SSH user's password on the server to make sure if it's this password, which SSH asks for (I had the same username and password on the server and client machine before). And, yes, SSH asks for the password of the user on the server machine, but only once, for the first session. All next sessions get authenticated without password. It's crazy... 

I configured SSH key authentication many times and have never seen such behaviour. Either it works (no password required at all) or doesn't (password required always).

And yes, I checked the permissions of key files and .ssh directory locally, authorized_keys file on the server. Everything seems to be all right...

I also removed authorized_keys, generated and copied the keys again. Didn't help. It seems it's some configuration of the server, but not the /etc/ssh/sshd_config file. What else can it be?

---

### Post by habrys on 2009-09-11
Can it have something to do with the fact, that I chose to encrypt the home directory of the SSH user on the server during installation of the system? Maybe the password is needed to get the access to the encrypted home directory, to actually read the authorized_keys file first time and not for the sshd itself?

The whole partition is also an encrypted LVM partition. I have to provide passphrase on the beginning of the boot sequence. But I think it's irrelevant.

---

### Post by habrys on 2009-09-11
**Yes, the problem was an encrypted home directory. **

I just created a new test user with regular home directory (not encrypted), configured ssh keys authentication for him and it works now as expected - password is never required for a new ssh session.

---

### Post by rafaelmagu on 2009-09-28
Just posting here to say thank you for posting your solution. I was trying to diagnose a friend's server setup and could not understand why it was asking for passwords at first, then using keys for subsequent logins.

Something new to Ubuntu I guess (I manage a bunch of 8.04 servers and never ran into this problem).

---

