---
title: "Updates broke SSH?"
date: 2011-02-18
forum: Server Platforms
---

### Post by ptmuldoon on 2011-02-18
I've been using Ubuntu 10.10 (Maverick) for some time now as the OS for a home Nasbox, along with webmin.  Its been great, and I've been able to SSH into the box without any issues in the past.

Last night, I ran apt-get update and apt-get upgrade to bring my system more current.

Now, I can't seem to log into SSH any longer, and get a "Connection failed, Windows error 10061" error.

I'm going to upgrade the OS to 11 as well in hopes things fix themselves.

As I'm a rookie at Ubuntu and Linux.  Does anyone have any suggestions on what to look for?

---

### Post by aeiah on 2011-02-18
i assume you're using putty? enable verbose error logging and see what it tells you - you should be able to get a lot more info out of it than that. 

does webmin tell you that the sshd service is running, by the way?

---

### Post by dtfinch on 2011-02-18
10061 is connection refused, so sshd probably isn't running anymore.

While updating sshd, it might have restarted it, thereby killing itself mid-update. Though I've never observed such behavior first hand, and I haven't been able to find a bug report.

If that's what happened, next time you get in (probably have to connect a monitor+keyboard to it), try running "apt-get -f install" to make it finish the upgrade. Then run "service ssh start" if it didn't get started automatically.

---

### Post by ptmuldoon on 2011-02-18
I'm actually not using putty, but Tunnelier instead (great program)

In webmin, the server is running and I've testing and get the following dev/tty error.  I've been trying to research that as well.
> 
> ssh -v localhost
OpenSSH_5.3p1 Debian-3ubuntu5, OpenSSL 0.9.8k 25 Mar 2009
Pseudo-terminal will not be allocated because stdin is not a terminal.
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to localhost [::1] port 22.
debug1: Connection established.
debug1: permanently_set_uid: 0/0
debug1: identity file /root/.ssh/identity type -1
debug1: identity file /root/.ssh/id_rsa type -1
debug1: identity file /root/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.3p1 Debian-3ubuntu5
debug1: match: OpenSSH_5.3p1 Debian-3ubuntu5 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.3p1 Debian-3ubuntu5
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr hmac-md5 none
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: read_passphrase: can't open /dev/tty: No such device or address
Host key verification failed.


and the log from tunnelier just tells me[
> 
11:23:41.524 Last used profile loaded successfully.
11:23:47.024 Starting a new SSH2 session.
11:23:47.024 Connecting to SSH2 server xxxxx.xxxxx.net:22.
11:24:00.274 Connection failed. Connect() failed: Windows error 10060: A connection attempt failed because the connected party did not properly respond after a period of time, or established connection failed because connected host has failed to respond.


---

### Post by ptmuldoon on 2011-02-18
Wanted to report back that is appears to a port issue with my oom VOIP box, as I was able to ssh from within my LAN.  And after deleting the port forwarding and resetting it up, it connecting again remotely as well.

Now just to get my ftp working properly again!!

---

