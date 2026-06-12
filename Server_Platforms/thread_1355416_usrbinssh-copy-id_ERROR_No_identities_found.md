---
title: "/usr/bin/ssh-copy-id: ERROR: No identities found"
date: 2009-12-14
forum: Server Platforms
---

### Post by dzaletnev on 2009-12-14
Hi,
I have 2x Ubuntu 9.10 x64 Server (ubuntu0 and ubuntu1) connected by patchcord. IPs and netmasks are set by ifconfig. Gateway isn't set. Ping - OK. NFS share - OK.
I have run at ubuntu1:
**sudo /etc/init.d/ssh restart** (Port 22 and PubkeyAuthentication yes are set in /etc/ssh/sshd_config) 
**ssh-keygen -t dsa** (either empty for no passphrase or logins' password)
**ssh-copy-id user@ubuntu0**
resulting in output:
/usr/bin/ssh-copy-id: ERROR: No identities found

What's wrong? What's my mistake?
Thank you in advance.

---

### Post by Muttley99 on 2009-12-15
Just to check; you made the keys under user A and specified the correct path for user A's /home/A/.ssh directory?
The permissions are correct for .ssh/ at 755?
check that the id_rsa key is in that directory!
Is the remote computer identity the same as the local, if not there was a switch to allow other users - see man!

---

### Post by dzaletnev on 2009-12-15
I ought to enter **ssh-keygen -t rsa** instead of **ssh-keygen -t dsa**. All works correctly.

---

### Post by BkkBonanza on 2009-12-15
Or I believe you can use the -i option to specify exactly which identity file to use. If not indicated then it defaults to ~/.ssh/id_rsa.pub

---

### Post by Saghaulor on 2010-02-09
I'm having the same issue.

Generated an rsa 4096 bit keypair
Changed permissions as per [https://help.ubuntu.com/community/SSH/OpenSSH/Keys]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys")

After running ssh-copy-id, I receive no identities found error.

Please help.

---

### Post by Saghaulor on 2010-02-09
Oddly enough, it started to work all by itself.

---

### Post by Saghaulor on 2010-02-09
I lied.

I can't get the server to recognize my key.

I don't know what I'm doing wrong. The directions need to be more granular as I'm not sure which machine to modify permissions on, etc.

Where I'm at, the key is generated, but I can't authenticate with it. I don't know what I'm doing wrong.

---

### Post by Saghaulor on 2010-02-18
BUMP

Please assist.

---

### Post by Saghaulor on 2010-02-23
Saghaulor, you really should read the directions more carefully, or at least when you are more alert.

> The first step involves creating a set of RSA keys for use in authentication.

**This should be done on the client.**

And, > f you can log in to a computer over SSH using a password, you can transfer your RSA key by doing the following **from your own computer**:

So, after reading the directions more carefully, you have learned that this process occurs on your local machine, and not the remote machine. That is why yesterday, you successfully created a keypair, copied the public key to your remote server, and were able to securely log into the remote server without password authentication.

By the way, I'd like to thank the community for their help, especially the authors of [https://help.ubuntu.com/community/SSH/OpenSSH/Keys]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys").

---

### Post by Muttley99 on 2010-02-26
Missing out what may seem an irrelevant step can lead to hours of messing about! It's happened to me so many times!
Earlier this year I spend days trying the above only to find out my /home directory was encrypted and it was never going to work while I left it that way :o

---

### Post by tc0nn on 2011-07-14
Make sure the file you are referring to (if specified) has a ".pub" or you will get the same "/usr/bin/ssh-copy-id: ERROR: No identities found" error.

---

### Post by ttanev on 2012-03-31
There is something interesting about all this. Yesterday I tried to ssh-copy-id a newly created dsa key and got the same error. Today after some searching around found that the command ssh-copy-id gives the "No identities found" error every time when there's no default RSA key generated at least in Mint 12/Oneiric.
You can try to create a new default key without changing the type and try ssh-copy-id again.
So I wiped out the ~/.ssh folder again and tried to create again "ssh-keygen -t dsa", because this is the only key type that my nexenta authenticates automatically (rsa always gives "admitting failure to authenticate"). At this point "ssh-copy-id" with or without arguments gives the same error. Tneh "ssh-keygen" without any arguments to create default rsa key and then the problem does not occur. Hope that helps someone.

---

### Post by MalditohoN on 2012-07-02
Thank you for this tip!

Really help me when I'm updating my subversion folder on another network computer.

---

