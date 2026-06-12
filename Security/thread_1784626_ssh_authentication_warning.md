---
title: "ssh authentication warning"
date: 2011-06-17
forum: Security
---

### Post by stabby on 2011-06-17
When login into a linux device I keep getting

```
[root@linuxbox ~]# ssh root@192.168.xxx.xxx
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
<some fingerprint code here>.
Please contact your system administrator.
Add correct host key in /root/.ssh/known_hosts to get rid of this message.
Offending key in /root/.ssh/known_hosts:6
Password authentication is disabled to avoid man-in-the-middle attacks.
Keyboard-interactive authentication is disabled to avoid man-in-the-middle attacks.
X11 forwarding is disabled to avoid man-in-the-middle attacks.
-bash-3.2#  
```

I know this is because the IP/fingerprint in known_hosts don't match. The security is not an issue, so in .ssh/config I set StrictHostKeyChecking=no which allows successful login.

Problem is my couple dozens linuxboxes run scripts that make all sorts of ssh connections to many devices, so I can't avoid the IP/fingerprint mismatch, and this warning is filling up my stdout and stderr logs making them more difficult to read.

I tried ssh in quiet mode to suppress it, but it still pops up in stderr for some reason. :(
I know I can do UserKnownHostsFile=/dev/null, which is an interesting trick and sort-of helps. Instead of the man-in-the-middle warning I always get this:

```
Warning: Permanently added '192.168.xxx.xxx' (RSA) to the list of known hosts.
```

Its less clutter in logs, but it's still an unnecessary line, and since it is in stderr, my reporting tool counts as error.

Is there any way to get rid of the warnings completely??? Or somehow disable the host checking altogether?

---

### Post by hrishikesh1988 on 2011-06-17
remove this file 
[FONT=monospace]
sudo rm /root/.ssh/known_hosts
[/FONT]

---

### Post by stabby on 2011-06-17
So it's as simple as that. Wow. Problem solved. Didn't think of that. Thanks! :)

---

### Post by Lars Noodén on 2011-06-17
> **stabby said:**
> Offending key in /root/.ssh/known_hosts:6


Getting rid of /root/.ssh/known_hosts gets rid of all the known keys not just the one causing problems there on the 6th line.  

A better way would be to go into the file and manually take out the key on line 6.

Yet another way is to use [ssh-keygen](http://manpages.ubuntu.com/manpages/natty/en/man1/ssh-keygen.1.html) to remove the offending key:

```

ssh-keygen -R 192.168.xxx.xxx

```

That will extract the key for that host and save it in a separate file in case it really is needed.

---

### Post by Lars Noodén on 2011-06-17
```

$ ssh -o CheckIP=no -o StrictHostKeyChecking=no \
      -o HostKeyAlias=192.168.xxx.xxx   192.168.xxx.xxx

```

---

### Post by crispy_420 on 2011-06-18
Couldn't static/reserved IP resolve this issue simply? That way when an IP was accessed it would be the same as last time so the key would be consistent. No scripts and no thinking, the router does the leg work.

Is that a viable option?

---

### Post by Lars Noodén on 2011-06-18
Yes, if you have the ability to set static or reserve IP addreses so that the machine always has the same number, then that would definitely be the way to go.

---

### Post by stabby on 2011-06-20
Static IP is something that immediately comes to mind, but half of my linux boxes get reinstalled couple times a day (it's the whole point of the setup), and their fingerprint changes. That's why the other half of them need to be intelligent enough to connect and not care about the fingerprint.
Deleting known_hosts made PCs connect very nice and with no warnings, but broke connection to report servers, so I had to restore it. Fortunately ssh-keygen approach seems to work well enough. It's not prefect, since I still get 1 warning when IP/fingerptint mismatch occurs, but it happens only once per linux reinstall instead of for every ssh call, so it's the best solution so far.

---

### Post by Lars Noodén on 2011-06-20
> **stabby said:**
> ... half of my linux boxes get reinstalled couple times a day (it's the whole point of the setup), and their fingerprint changes...

It's not necessary for the keys to change each time.  As part of your post-installation procedures, you can restore the keys from a backup copy.

[indent]
/etc/ssh/ssh_host_dsa_key      
/etc/ssh/ssh_host_dsa_key.pub  
/etc/ssh/ssh_host_ecdsa_key    
/etc/ssh/ssh_host_ecdsa_key.pub
/etc/ssh/ssh_host_rsa_key
/etc/ssh/ssh_host_rsa_key.pub
[/indent]

---

