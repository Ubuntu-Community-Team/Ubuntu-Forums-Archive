---
title: "Port paranoia"
date: 2010-08-27
forum: Security
---

### Post by Nesaskewatch on 2010-08-27
I had my top panel change abruptly after an update, likely just the update, but I am easily spooked thanks to 15 years of M$.  I have searched around and run various commands and am realizing I have done little more than scare myself even more by noticing things that I don't understand.  So I have come here to this venerable security forum to ask a few simple questions that *should* put my mind at rest...

First and possibly most important; is the following all I need to see to feel safe?

 ```
laptop:~$ nmap 192.168.xxx.xxx

Starting Nmap 5.00 ( http://nmap.org ) at 2010-08-27 08:31 PDT
All 1000 scanned ports on 192.168.xxx.xxx are closed

Nmap done: 1 IP address (1 host up) scanned in 0.10 seconds

```

I ran ifconfig to get the correct ip to scan, so it ain't my router!

Second, and mostly to throw cold water on the paranoid blaze that flares up occasionally; is the following anything to worry about?

```
laptop:~$ sudo lsof -i -n -P
COMMAND    PID  USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
avahi-dae  932 avahi   13u  IPv4   4522      0t0  UDP *:5353 
avahi-dae  932 avahi   14u  IPv4   4523      0t0  UDP *:45232 
cupsd     1127  root    6u  IPv6   4837      0t0  TCP [::1]:631 (LISTEN)
cupsd     1127  root    7u  IPv4   4838      0t0  TCP 127.0.0.1:631 (LISTEN)
gvfsd-htt 3206  dave   14w  IPv4  25118      0t0  TCP 192.168.xxx.xxx:46689->91.189.89.31:80 (CLOSE_WAIT)
dhclient  5914  root    5w  IPv4  41274      0t0  UDP *:68 

```

I am seeing some things I have not seen in other similar threads.  That gvfsd-htt 3206 is something I have never seen before.  

Thanks.

---

### Post by CharlesA on 2010-08-27
It looks fine.

The "gvfsh-htt" is just an http request to an external server.

---

### Post by Nesaskewatch on 2010-08-27
> **CharlesA said:**
> It looks fine.

The "gvfsh-htt" is just an http request to an external server.

Thanks!  I'll try and feel secure now...

---

