---
title: "sshd refusing connection from one host"
date: 2008-05-24
forum: Security
---

### Post by mootpoint on 2008-05-24
This morning I apt-get upgraded my 8.04 server box, and got some of the recent ssh fixes that have gone in since the last apt-get upgrade I ran on May 13. I believe I also installed a couple of recommended packages I saw listed for openssh (I had to do the install manually; openssh was in the held back list in apt-get).

I've been able to log into the new server from my laptop (running gutsy) for months. Now I can't log into the box from my laptop, but am able to log in fine from my old server (Debian Etch). When I try logging in from the laptop, the following appears in /var/log/auth.log:

May 24 13:57:14 mercury sshd[13227]: Disabling protocol version 1. Could not load host key
May 24 13:57:14 mercury sshd[13227]: refused connect from ::ffff:192.168.200.250 (::ffff:192.168.200.250)
May 24 13:57:25 mercury sshd[13229]: Disabling protocol version 1. Could not load host key
May 24 13:57:25 mercury sshd[13229]: refused connect from ::ffff:192.168.200.250 (::ffff:192.168.200.250)

On the laptop:

junk@lapdog:~$ ssh -vvv mercury
OpenSSH_4.6p1 Debian-5ubuntu0.5, OpenSSL 0.9.8e 23 Feb 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to mercury [192.168.200.222] port 22.
debug1: Connection established.
debug1: identity file /home/junk/.ssh/identity type -1
debug1: identity file /home/junk/.ssh/id_rsa type -1
debug1: identity file /home/junk/.ssh/id_dsa type -1
ssh_exchange_identification: Connection closed by remote host



Things I've tried:

1) I've grepped all the files in /etc/ssh for 200.250; it's not in any of the files there.

2) The old server has address 192.168.200.200, so the problem is host-specific, but not the entire 192.168.200.0/24 subnet.

3) I created a test user account on the laptop and a corresponding user on the server. Didn't help. So it's not user keys, or user known hosts, or anything user-specific as far as I can tell.

4) The laptop can ssh fine to the Debian Etch box, and also to an apt-get upgraded feisty server.

5) The laptop is updated with the recent ssh fixes for gutsy. It can ssh fine to the Debian Etch box.

Any thoughts? 

m00t

---

### Post by Dr Small on 2008-05-24
You must be using KeyBasedAuth, and the Etch box has the correct key to access the server, whereas the laptop no longer has a key, or is no longer valid.

---

