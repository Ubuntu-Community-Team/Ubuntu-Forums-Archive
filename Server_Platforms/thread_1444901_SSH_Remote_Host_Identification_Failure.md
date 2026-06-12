---
title: "SSH Remote Host Identification Failure"
date: 2010-04-01
forum: Server Platforms
---

### Post by teejmya on 2010-04-01
I normally use SSH to remote into my webserver on 10.50.*.79:22.
I took a vacation, and my DCHP leases timed out. 
My server is now 10.50.*.78:22, which used to be my media center.

So now when I try to ssh 10.50.*.78:22, host key verification fails, and I don't get access.


Here's the output, ==== are things that I have removed.
> tm@main:~$ ssh 10.50.==.78 -l webservadmin
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
82:===============================================:15.
Please contact your system administrator.
Add correct host key in /home/tm/.ssh/known_hosts to get rid of this message.
Offending key in /home/tm/.ssh/known_hosts:2
RSA host key for 10.50.==.78 has changed and you have requested strict checking.
Host key verification failed.



Maybe it has something to do with:
> Add correct host key in /home/tm/.ssh/known_hosts to get rid of this message.
??

---

### Post by CharlesA on 2010-04-01
It happens if the IP address changes. Nothing to worry about, just add the key to the known_hosts file.

Also make sure that you are in fact connecting to the correct machine. If the DHCP lease expired, and changed IP addresses, it would be a major pain, my servers are set for static IP addresses.

---

### Post by teejmya on 2010-04-02
Yeah, that did the trick!
It was the same system, I only have about 7 people on this network. 

Thanks a lot.

---

### Post by cdenley on 2010-04-02
If you're using DHCP, you can make sure avahi is configured and use that for hostname resolution.
```

ssh user@myhostname.local

```
Then you don't have to worry about two server using the same address.

---

