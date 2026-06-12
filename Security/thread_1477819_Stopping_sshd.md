---
title: "Stopping sshd"
date: 2010-05-09
forum: Security
---

### Post by planetofsound on 2010-05-09
Can anyone tell me how to temporarily disable sshd? I only need remote access to my PC occasionally. I'm frequently getting blasted with brute-force hacking attempts, so I'd prefer to only have sshd running when necessary. I figured the following ought to work, but it doesn't.

$ sudo /etc/init.d/ssh stop
 * Stopping OpenBSD Secure Shell server sshd               [ OK ] 
$ sudo /etc/init.d/ssh status
 * sshd is running

And it clearly is still running because 'tail -f auth.log' continues to report regular break-in attempts. Shouldn't 'stop' mean stay stopped?!

---

### Post by CharlesA on 2010-05-09
Try this:

```
sudo service ssh stop
```

Otherwise, you can leave SSH on, but use key-based authentication instead of using passwords, or install something like Fail2Ban or DenyHosts to help slow down the bruteforce attacks.

---

### Post by planetofsound on 2010-05-09
Thanks very much, that works fine. Was already only allowing key based authentication, but that still seems to do the Diffie-Hellman key-exchange stuff and chomps loads of CPU. Now connections are dropped as soon as they arrive.

---

### Post by CharlesA on 2010-05-09
Interesting. If someone tries to connect without the key, it should immediately refuse the key and disconnect them.

Are passwords disabled?

---

### Post by planetofsound on 2010-05-10
I think its working as its supposed to. When I try to break in from an external system, I don't get prompted for a password and get "Permission denied (publickey)." and I can only login to a single specific username, and not root. Wireshark shows that ssh first sets up an encrypted session then uses that for the user authentication, even when using public key authentication:

No.   Time      Source     Destination Protocol Info
   71 9.370406  remote     local       SSHv2  Server Protocol: SSH-2.0-OpenSSH_5.3p1 Debian-3ubuntu3\r
   73 9.370688  local      remote      SSHv2  Client Protocol: SSH-2.0-OpenSSH_5.3\r
   75 9.405915  local      remote      SSHv2  Client: Key Exchange Init
   76 9.411709  remote     local       SSHv2  Server: Key Exchange Init
   79 9.485717  local      remote      SSHv2  Client: Diffie-Hellman GEX Request
   80 9.526351  remote     local       SSHv2  Server: Diffie-Hellman Key Exchange Reply
   82 9.528497  local      remote      SSHv2  Client: Diffie-Hellman GEX Init
   83 9.579512  remote     local       SSHv2  Server: Diffie-Hellman GEX Reply
   84 9.594925  local      remote      SSHv2  Client: New Keys
   86 9.671757  local      remote      SSHv2  Encrypted request packet len=48
   88 9.715538  remote     local       SSHv2  Encrypted response packet len=48
   89 9.716000  local      remote      SSHv2  Encrypted request packet len=64
   92 9.834044  remote     local       SSHv2  Encrypted response packet len=48

So even a failed login attempt without password prompts takes a not insignificant amount of CPU time and bandwidth. If ssh is disabled, then the TCP connection gets immediately rejected. Of course as you point out it might be better to use some sort of firewalling technique to slow down or block the bad guys, but I'm happy I can now start/stop ssh as required and minimise the effect on my system.

---

### Post by CharlesA on 2010-05-10
I haven't noticed that. It may be due to having locked down SSH using keys and setting IP tables to only allow SSH traffic from one outside IP address, which is the only address I access it from outside my local LAN.

---

### Post by HermanAB on 2010-05-11
SSH attack scripts are pretty retarded.  All you need to do is change it to run on a non standard port.

An intelligent hacker can create a port scanner that will find SSH wherever you move it to, but that doesn't happen in practice.

---

