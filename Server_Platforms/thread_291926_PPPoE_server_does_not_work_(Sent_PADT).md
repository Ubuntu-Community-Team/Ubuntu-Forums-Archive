---
title: "PPPoE server does not work (Sent PADT)"
date: 2006-11-03
forum: Server Platforms
---

### Post by netventure on 2006-11-03
Hi,

I have been trying for quite some time to setup a PPPoE access concentrator (PPPoE server) on Ubuntu dapper and (edgy). I borrowed a ***working*** PPPoE server configuration from a Redhat 9 system but the server disconnects immediately after receiving a request. 

I've ensured that the following packages have been installed:

```
#apt-get these:
ppp
pppconfig
pppoe
pppoeconf
```

Here's the working configuration I borrowed:

/etc/ppp/pap-secrets:
```
# Secrets for authentication using PAP
# client	server	secret			IP addresses
  user1          *       upass1                  *
  test1           *       tpass1                  *
```

/etc/ppp/pppoe-server-options:
```
# PPP options for the PPPoE server
require-pap
login
lcp-echo-interval 10
lcp-echo-failure 10
ms-dns 40.0.0.1
ms-dns 40.0.0.2
mtu 1492
```

/etc/ppp/options:
```
lock
```

This is how I start the pppoe server from the shell:

```
ifdown eth0
ifconfig eth0 0.0.0.0
pppoe-server -I eth0 -L 40.0.0.1 -R 40.0.0.5 -O /etc/ppp/pppoe-server-options
```

Few other variations of the pppoe server options are:

```
pppoe-server -I eth0 -L 40.0.0.1 -R 40.0.0.5 -O /etc/ppp/pppoe-server-options -s
```
and
```
pppoe-server -I eth0 -L 40.0.0.1 -R 40.0.0.5 -O /etc/ppp/pppoe-server-options -C pppoeserv
```
and 
```
pppoe-server -I eth0 -L 40.0.0.1 -R 40.0.0.5 -O /etc/ppp/pppoe-server-options -S accesscon
```


For all of the above settings, here's what I get in syslog:

```
Nov  3 15:15:01 localhost pppoe-server[19865]: Session 23 created for client 00:a1:b2:c3:d4:e5 (45.0.0.24) on eth0 using Service-Name ''
Nov  3 15:15:01 localhost pppoe-server[19316]: Session 23 closed for client 00:a1:b2:c3:d4:e5 (45.0.0.24) on eth0
Nov  3 15:15:01 localhost pppoe-server[19316]: Sent PADT
Nov  3 15:15:12 localhost pppoe-server[19866]: Session 24 created for client 00:a1:b2:c3:d4:e5 (45.0.0.25) on eth0 using Service-Name ''
Nov  3 15:15:12 localhost pppoe-server[19316]: Session 24 closed for client 00:a1:b2:c3:d4:e5 (45.0.0.25) on eth0
Nov  3 15:15:12 localhost pppoe-server[19316]: Sent PADT
Nov  3 15:15:24 localhost pppoe-server[19867]: Session 25 created for client 00:a1:b2:c3:d4:e5 (45.0.0.26) on eth0 using Service-Name ''
Nov  3 15:15:24 localhost pppoe-server[19316]: Session 25 closed for client 00:a1:b2:c3:d4:e5 (45.0.0.26) on eth0
Nov  3 15:15:24 localhost pppoe-server[19316]: Sent PADT
Nov  3 15:15:35 localhost pppoe-server[19868]: Session 26 created for client 00:a1:b2:c3:d4:e5 (45.0.0.27) on eth0 using Service-Name ''
Nov  3 15:15:35 localhost pppoe-server[19316]: Session 26 closed for client 00:a1:b2:c3:d4:e5 (45.0.0.27) on eth0
Nov  3 15:15:35 localhost pppoe-server[19316]: Sent PADT
Nov  3 15:15:47 localhost pppoe-server[19869]: Session 27 created for client 00:a1:b2:c3:d4:e5 (45.0.0.28) on eth0 using Service-Name ''
Nov  3 15:15:47 localhost pppoe-server[19316]: Session 27 closed for client 00:a1:b2:c3:d4:e5 (45.0.0.28) on eth0
Nov  3 15:15:47 localhost pppoe-server[19316]: Sent PADT
Nov  3 15:15:58 localhost pppoe-server[19870]: Session 28 created for client 00:a1:b2:c3:d4:e5 (45.0.0.29) on eth0 using Service-Name ''
Nov  3 15:15:58 localhost pppoe-server[19316]: Session 28 closed for client 00:a1:b2:c3:d4:e5 (45.0.0.29) on eth0
Nov  3 15:15:58 localhost pppoe-server[19316]: Sent PADT
```


This happens on Dapper as well as Edgy.

The config i tried has been working on Redhat 9, so, it should work on ubuntu too (unless there are debian specific things that I've missed out).

Has anyone setup a PPPoE server before and if so, please post your configuration here.

Thanks
--NV

---

### Post by netventure on 2006-11-22
Ok. I got it working after stumbling over [bug #380584]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=380584") filed in debian's bugzilla. This note is for posterity, with the hope that it will help others.

NOTE: I tried this in Edgy, not Dapper, but looking at the version numbers of pppd between dist-versions, this fix may apply to Dapper too.

Here's my understanding of how PPPoE server works:
1. pppoe-server starts up and waits for request
2. After receiving an auth request from pppoe client, it does some stuff on it's side 
3. It calls pppd (of ppp-2.4.x package) and passes on the authentication info to it.
4. pppd does the auth work (and anything else that it should) and tells pppoe-server whether a session has been established.
5. For each pppoe client, a separate pppd session is established.

I used strace to debug the server and found that when the pppoe-server daemon tries to spawn /usr/sbin/pppd, it receives "ENOENT: No such file or directory" or something to that tune. It means that pppoe-server is asking the OS to call pppd, but the OS tells pppoe-server that it could not find any file named pppd.

After pppoe-server starts up, it chdir()'s to / (no matter which directory you are currently in). And as mentioned in the bug #380584, pppoe-server tries to call "pppd" instead of "/usr/sbin/pppd". When it fails to call pppd, the rest of the steps (2-4) fail and that causes pppoe-server to end the session abruptly.

What I did was to create a link:

```
cd /
ln -sf /usr/sbin/pppd pppd
```

And edit /etc/ppp/pap-secrets to contain only this:

```
# Allow all system users (/etc/passwd) to connect
*    *     ""   *
```

Howtos on other forums suggest adding a user to pap-secrets, but this did not work for me on edgy. It seems that debian/ubuntu's version of pppd is linked to PAM. That means that PAP auth requests are internally passed on to PAM, which checks against /etc/passwd. In plain words, you need to create an account in the system database (/etc/passwd) instead of adding a new user in the pap-secrets file. Adding a user in the pap-secrets file will not work (there may be other configuration options to do this, but I haven't looked them up).

Now, from the pppoe client, I could type in the username and password of an account already added to the system (/etc/passwd) and connect!

Hope that was useful.

--NV

PS: I will paste output logs here and probably convert this into a howto at at later time.

---

