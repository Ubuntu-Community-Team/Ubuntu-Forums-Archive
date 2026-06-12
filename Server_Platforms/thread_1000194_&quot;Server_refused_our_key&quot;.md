---
title: "&quot;Server refused our key&quot;"
date: 2008-12-02
forum: Server Platforms
---

### Post by shdawson on 2008-12-02
Hi,


Have enabled key authentication.  Getting, "Server refused our key" when trying to login.  What is missing here?


Thanks...

---

### Post by MJN on 2008-12-02
> **shdawson said:**
> What is missing here?More detail beyond 'it doesnt work'...

Post your SSH config (assuming that's what you're talking about), details of what client you're using and how you're using it, how you generated your keys and where you put them.

If you put the effort in to describe your problem we will be more than happy to do likewise with trying to find a solution.

Mathew

---

### Post by dashah76 on 2008-12-14
i am using open ssh SSH-2.0-OpenSSH_3.8.1p1 on windows 2000 when i used the password to login to the sftp server i cn sucessfully login withou err but when i use publc and privte it says serve refused the key and promps fr a pssword.the wiscp log is as below
the .ssh folde permis iss 700 and authorized_keys file permssn is 644
Looking up host "192168025"
 2008-12-15 05:49:37812 Connecting to 192.168.0.25 port 22
 2008-12-15 05:49:37812 Waiting for the server to continue with the initialisation
 2008-12-15 05:49:37812 Detected network event
 2008-12-15 05:49:37827 Detected network event
 2008-12-15 05:49:37827 Server version: SSH-20-OpenSSH_381p1
 2008-12-15 05:49:37827 We claim version: SSH-20-WinSCP_release_418
 2008-12-15 05:49:37827 AcquireCredentialsHandle: No credentials are available in the security package
 2008-12-15 05:49:37827 GSSKEX disabled: The operation completed successfully
 2008-12-15 05:49:37827 Using SSH protocol version 2
 2008-12-15 05:49:37827 Waiting for the server to continue with the initialisation
 2008-12-15 05:49:37827 Detected network event
 2008-12-15 05:49:37827 Doing Diffie-Hellman group exchange
 2008-12-15 05:49:37827 Waiting for the server to continue with the initialisation
 2008-12-15 05:49:37843 Detected network event
 2008-12-15 05:49:37843 Doing Diffie-Hellman key exchange with hash SHA-1
 2008-12-15 05:49:37890 Waiting for the server to continue with the initialisation
 2008-12-15 05:49:37921 Detected network event
 2008-12-15 05:49:37984 Host key fingerprint is:
 2008-12-15 05:49:37984 ssh-rsa 1024 d4:b7:01:45:0b:82:31:88:ae:9e:71:3e:af:18:70:af
 2008-12-15 05:49:37984 Initialised AES-256 SDCTR client->server encryption
 2008-12-15 05:49:37984 Initialised HMAC-SHA1 client->server MAC algorithm
 2008-12-15 05:49:37984 Initialised AES-256 SDCTR server->client encryption
 2008-12-15 05:49:37984 Initialised HMAC-SHA1 server->client MAC algorithm
 2008-12-15 05:49:37984 Waiting for the server to continue with the initialisation
 2008-12-15 05:49:37984 Detected network event
 2008-12-15 05:49:37984 Reading private key file "C:\newppk"
 2008-12-15 05:49:37984 Using username "new"
 2008-12-15 05:49:37984 Waiting for the server to continue with the initialisation
 2008-12-15 05:49:38031 Detected network event
 2008-12-15 05:49:38906 Offered public key
 2008-12-15 05:49:38906 Waiting for the server to continue with the initialisation
 2008-12-15 05:49:38906 Detected network event
 2008-12-15 05:49:38906 Server refused our key
 2008-12-15 05:49:38906 Server refused public key

---

