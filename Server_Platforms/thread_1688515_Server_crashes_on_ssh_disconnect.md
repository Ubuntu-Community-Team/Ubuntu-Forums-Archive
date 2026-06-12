---
title: "Server crashes on ssh disconnect"
date: 2011-02-15
forum: Server Platforms
---

### Post by ekaj. on 2011-02-15
I have a very weird problem. 

I am running Hardy server on a pretty old machine (~7 years) with a gig of RAM (or around that) and a new, large hard drive (750GB). Its on my home network behind a router. But that's not the issue. 

I have had it up and running for some time now, and its viewable and accessible from the outside world (e.g. I have all the ports forwarded correctly). I can access it via ssh from anywhere on teh internets, most of the time. 

Usually I access it from my macbook via leopard's terminal. And that's all fine and dandy until I (often accidentally) close the lid and the ssh connection is broken. Or, if i close the terminal window without logging out explicitly with 'exit'. At this point its still mostly okay. I can still access my website and whatnot. But when I try to reconnect with ssh, the **** hits the fan. The ssh process (I have it on verbose mode) looks fine. No errors, no anomalies. It talks to the server fine, until the very last step when the prompt is supposed to come up. The logon message even appears, but the servername:~user$ never shows up. At this time, I can no longer access my website and the server does not respond at all. Not to pings, not to anything. If I am physically at the computer, it does not respond to any keystroke and the screen is black. The only remedy is to power cycle by holding down the power button until it turns off, then reboot. Major annoyance, especially when I'm two states away.

I'm kinda baffled at this point. I don't know how to diagnose it because the log files are clean (I think). There's no sign of any error, just the computer not responding. 

Any ideas? I'm lost....

---

### Post by PapaNerd on 2011-02-15
I have a problem with a server of similar age and memory with it hanging when I do something that is CPU intensive (like a grep through a large file).  And yes, it also requires a hard power reset in those instances, and luckily is within reach.  

Perhaps breaking the ssh connection in an unclean way is causing a bit of cleanup action that is CPU intensive in a way that is similar to the hangs I am experiencing.  If so, you might be able to gain some debugging information by using a second remote computer and running "top" when the lid of the first computer is closed.

---

### Post by ekaj. on 2011-02-15
What would the top command look like? I didn't see a way to access a remote computer in the man page...

And I'm not exactly sure where to look for any possible logs of the issue; are there ssh logs? What system logs should I check?

Thanks for your help

---

### Post by PapaNerd on 2011-02-15
On the ssh command line just enter "top".

You would want to check both:
/var/log/syslog
/var/log/auth.log

My system, however, doesn't show anything unusual in those files when it hangs.

---

### Post by ekaj. on 2011-02-16
The last few lines before hanging in auth.log are: 

```

Feb 14 23:55:19 seafalcon sudo: pam_unix(sudo:session): session opened for user root by jake(uid=0)
Feb 14 23:55:19 seafalcon sudo: pam_unix(sudo:session): session closed for user root
Feb 14 23:58:37 seafalcon sshd[15792]: Disabling protocol version 1. Could not load host key
Feb 14 23:58:48 seafalcon sshd[15792]: Accepted publickey for jake from 129.210.138.200 port 65294 ssh2
Feb 14 23:58:48 seafalcon sshd[15795]: pam_unix(sshd:session): session opened for user jake by (uid=0)
```

and in syslog:

```

Feb 14 23:45:01 seafalcon /USR/SBIN/CRON[15497]: (www-data) CMD (php usr/share/cacti/site/poller.php >/dev/null 2>/var/log/cacti/poller-error.log)
Feb 14 23:50:01 seafalcon /USR/SBIN/CRON[15602]: (www-data) CMD (php /usr/share/cacti/site/poller.php >/dev/null 2>/var/log/cacti/poller-error.log)
Feb 14 23:55:01 seafalcon /USR/SBIN/CRON[15667]: (www-data) CMD (php /usr/share/cacti/site/poller.php >/dev/null 2>/var/log/cacti/poller-error.log)
Feb 14 23:55:54 seafalcon nmbd[6299]: [2011/02/14 23:55:54, 0] nmbd/nmbd_browsesync.c:find_domain_master_name_query_fail(        351)
Feb 14 23:55:54 seafalcon nmbd[6299]:   find_domain_master_name_query_fail:
Feb 14 23:55:54 seafalcon nmbd[6299]:   Unable to find the Domain Master Browser name WORKGROUP<1b> for the workgroup WORKGROUP.
Feb 14 23:55:54 seafalcon nmbd[6299]:   Unable to sync browse lists in this workgroup.

``` 

neither of which seem to have anything out of the ordinary. I'm not going to force a hang right now, but let's say I find a process that spikes the CPU usage. Is there a way to detect that and end it before it crashes the computer?

---

### Post by tgalati4 on 2011-02-16
If you are running cacti on the system, then you should be able to access the cacti webpage and see what is going on.

I just did a test.  I ssh'd into my hardy server that is on my LAN from my Jaunty laptop (IBM thinkpad).  I put it to sleep for 5 minutes then woke it up.  My ssh session was still intact.

So, I would say there may be an issue between the mac terminal or Apple's ssh implementation.  I use iTerm on my powerbook and I've never had any problems with ssh.

Install cpuburn and run some tests to determine if the server is stable:
sudo apt-get install cpuburn
man cpuburn
burnP6  (control-C to quit, run it twice if dual-core)

If it locks up during a cpuburn test, then it's time for a cleanout and heatsink reseating with new thermal paste.

---

### Post by ekaj. on 2011-02-16
Good news and bad news. The server did not crash with the cpu test, however it did just hang again when I attempted to ssh into it. I am positive I exited my sessions cleanly with the exit command and did not shut my lid, so its not that. I'm at even more of a loss now. Again, it was the same situation where I logged on with ssh, all the authorization was fine, but just before the prompt appears, it stops and does not respond whatsoever. Oh, and this time it was using iTerm. 

I doubt anything will come to light in the ssh log, but here it is anyway: 
```
OpenSSH_5.2p1, OpenSSL 0.9.8l 5 Nov 2009
debug1: Reading configuration data /etc/ssh_config
debug1: Connecting to seafalcon.selfip.com [67.171.23.146] port 22.
debug1: Connection established.
debug1: identity file /Users/jake/.ssh/identity type -1
debug1: identity file /Users/jake/.ssh/id_rsa type 1
debug1: identity file /Users/jake/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.7p1 Debian-8ubuntu1.2
debug1: match: OpenSSH_4.7p1 Debian-8ubuntu1.2 pat OpenSSH_4*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.2
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr hmac-md5 none
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'seafalcon.selfip.com' is known and matches the RSA host key.
debug1: Found key in /Users/jake/.ssh/known_hosts:3
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /Users/jake/.ssh/identity
debug1: Offering public key: /Users/jake/.ssh/id_rsa
debug1: Server accepts key: pkalg ssh-rsa blen 277
debug1: read PEM private key done: type RSA
debug1: Authentication succeeded (publickey).
debug1: channel 0: new [client-session]
debug1: Entering interactive session.
Linux seafalcon.selfip.com 2.6.24-23-server #1 SMP Wed Apr 1 22:22:14 UTC 2009 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

To access official Ubuntu documentation, please visit:
http://help.ubuntu.com/
You have new mail.
Last login: Wed Feb 16 15:56:53 2011 from 129.210.138.200
```

---

