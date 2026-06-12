---
title: "Ubuntu 18.04 -&gt; 20.04 breaks libssh2 app"
date: 2022-02-24
forum: Security
---

### Post by mfleming on 2022-02-24
I moved to a new server running Ubuntu 20.04 LTS from one running 18.04, and an app I've been using stopped working. Among other things, it does sftp using libssh2. This now fails, with error message indicating that a session could not be initiated because key exchange fails. When I try to connect, I see this in auth.log: 

sshd[21850]: Unable to negotiate with 104.48.39.9 port 57156: no matching key exchange method found. Their offer: diffie-hellman-group14-sha1,diffie-hellman-group-exchange-sha1,diffie-hellman-group1-sha1 [preauth]

I rebuilt the app using the latest version of libssh2, which supposedly also can do diffie-hellman-group-exhange-sha256, but that wasn't listed as offered. I thought the version of openssh on Ubuntu 20.04 supports the 3 key exchange methods that it rejected. I tried adding

KexAlgorithms +diffie-hellman-group1-sha 
to /etc/ssh_config (and then restarting ssh) but it made no difference.

I can ssh and sftp to the server with various clients. It's only the one built against libssh2 that fails.

It seems that this should be a solvable problem, but I've spent hours on it today without solving it. Any assistance would be very much appreciated.

Matthew Fleming, MD
Fleming Dermatopathology
Milwaukee, WI

---

### Post by mfleming on 2022-02-25
I should point out that ssh -Q kex shows the following:

ssh -Q kex
diffie-hellman-group1-sha1
diffie-hellman-group14-sha1
diffie-hellman-group14-sha256
diffie-hellman-group16-sha512
diffie-hellman-group18-sha512
diffie-hellman-group-exchange-sha1
diffie-hellman-group-exchange-sha256
ecdh-sha2-nistp256
ecdh-sha2-nistp384
ecdh-sha2-nistp521
curve25519-sha256
[email]curve25519-sha256@libssh.org[/email]
[email]sntrup4591761x25519-sha512@tinyssh.org[/email]

So openssh on the server definitely supports the key exchange algorithms offered by libssh2. 

I tried rebuilding libssh2 using the WinCNG libraries, as in [https://jpassing.com/2021/02/29/2021-03-29-building-libssh2-on-windows-lessons-learnt/](https://jpassing.com/2021/02/29/2021-03-29-building-libssh2-on-windows-lessons-learnt/), and it was no different.

Any suggestions would be really appreciated. 

Matthew Fleming

---

