---
title: "Samba won't stop"
date: 2015-11-30
forum: Server Platforms
---

### Post by MeneM on 2015-11-30
Hi All,

I'm trying to stop a samba service. Something I've done a million times... But this time, samba just get's re spawned by init when I stop it:


```
root@sudev03:/etc/samba# /etc/init.d/samba stop
root@sudev03:/etc/samba# /etc/init.d/samba status
 * nmbd is running
 * smbd is running
root@sudev03:/etc/samba# ps -fe | grep -i smbd
root      1503     1  0 10:35 ?        00:00:00 smbd -F
root      1508  1503  0 10:35 ?        00:00:00 smbd -F
```

And in syslog:

```
Nov 30 10:35:38 sudev03 kernel: [  302.156376] init: nmbd main process (905) killed by KILL signal
Nov 30 10:35:38 sudev03 kernel: [  302.156405] init: nmbd main process ended, respawning
Nov 30 10:35:38 sudev03 kernel: [  302.165417] init: smbd main process (687) killed by KILL signal
Nov 30 10:35:38 sudev03 kernel: [  302.165436] init: smbd main process ended, respawning
```


This is a 14.04 server. And yes I've also tried service samba stop. The darn thing just won't stop running...

What obvious thing am I not seeing?

Thanks!

---

### Post by MeneM on 2015-11-30
So I tried doing a `apt-get remove --purge samba` so I could re-install it.

After removing it, I tried installing it with `apt-get install samba`
Now it wont start! WTF?

```
Nov 30 12:58:21 sudev03 samba[3185]:   ===============================================================
Nov 30 12:58:21 sudev03 samba[3185]: [2015/11/30 12:58:21.460920,  0] ../lib/util/fault.c:73(fault_report)
Nov 30 12:58:21 sudev03 samba[3185]:   INTERNAL ERROR: Signal 11 in pid 3185 (4.1.6-Ubuntu)
Nov 30 12:58:21 sudev03 samba[3185]:   Please read the Trouble-Shooting section of the Samba HOWTO
Nov 30 12:58:21 sudev03 samba[3185]: [2015/11/30 12:58:21.461040,  0] ../lib/util/fault.c:75(fault_report)
Nov 30 12:58:21 sudev03 samba[3185]:   ===============================================================
Nov 30 12:58:21 sudev03 samba[3185]: [2015/11/30 12:58:21.461105,  0] ../lib/util/fault.c:144(smb_panic_default)
Nov 30 12:58:21 sudev03 samba[3185]:   PANIC: internal error
Nov 30 12:58:21 sudev03 kernel: [  350.990110] init: smbd main process (3114) terminated with status 1
Nov 30 12:58:21 sudev03 kernel: [  350.990131] init: smbd main process ended, respawning
Nov 30 12:58:21 sudev03 kernel: [  351.043768] init: smbd main process (3199) terminated with status 1
Nov 30 12:58:21 sudev03 kernel: [  351.043831] init: smbd main process ended, respawning
Nov 30 12:58:21 sudev03 kernel: [  351.088124] init: smbd main process (3203) terminated with status 1
Nov 30 12:58:21 sudev03 kernel: [  351.088146] init: smbd main process ended, respawning
Nov 30 12:58:21 sudev03 kernel: [  351.130272] init: smbd main process (3207) terminated with status 1
Nov 30 12:58:21 sudev03 kernel: [  351.130288] init: smbd main process ended, respawning
Nov 30 12:58:21 sudev03 kernel: [  351.164490] init: smbd main process (3211) terminated with status 1
Nov 30 12:58:21 sudev03 kernel: [  351.164505] init: smbd main process ended, respawning
Nov 30 12:58:21 sudev03 kernel: [  351.202178] init: smbd main process (3215) terminated with status 1
Nov 30 12:58:21 sudev03 kernel: [  351.202194] init: smbd main process ended, respawning
Nov 30 12:58:21 sudev03 kernel: [  351.244526] init: smbd main process (3219) terminated with status 1
Nov 30 12:58:21 sudev03 kernel: [  351.244537] init: smbd main process ended, respawning
Nov 30 12:58:22 sudev03 kernel: [  351.267594] init: smbd main process (3223) terminated with status 1
Nov 30 12:58:22 sudev03 kernel: [  351.267604] init: smbd main process ended, respawning
Nov 30 12:58:22 sudev03 kernel: [  351.299232] init: smbd main process (3227) terminated with status 1
Nov 30 12:58:22 sudev03 kernel: [  351.299249] init: smbd main process ended, respawning
Nov 30 12:58:22 sudev03 kernel: [  351.324250] init: smbd main process (3231) terminated with status 1
Nov 30 12:58:22 sudev03 kernel: [  351.324264] init: smbd main process ended, respawning
Nov 30 12:58:22 sudev03 kernel: [  351.347240] init: smbd main process (3235) terminated with status 1
Nov 30 12:58:22 sudev03 kernel: [  351.347249] init: smbd respawning too fast, stopped
```

I've never seen this from a simple samba installation before....

---

### Post by bab1 on 2015-11-30
> **MeneM said:**
> Hi All,

I'm trying to stop a samba service. Something I've done a million times... But this time, samba just get's re spawned by init when I stop it:


```
root@sudev03:/etc/samba# /etc/init.d/samba stop
root@sudev03:/etc/samba# /etc/init.d/samba status
 * nmbd is running
 * smbd is running
root@sudev03:/etc/samba# ps -fe | grep -i smbd
root      1503     1  0 10:35 ?        00:00:00 smbd -F
root      1508  1503  0 10:35 ?        00:00:00 smbd -F
```

And in syslog:

```
Nov 30 10:35:38 sudev03 kernel: [  302.156376] init: nmbd main process (905) killed by KILL signal
Nov 30 10:35:38 sudev03 kernel: [  302.156405] init: nmbd main process ended, respawning
Nov 30 10:35:38 sudev03 kernel: [  302.165417] init: smbd main process (687) killed by KILL signal
Nov 30 10:35:38 sudev03 kernel: [  302.165436] init: smbd main process ended, respawning
```


This is a 14.04 server. And yes I've also tried service samba stop. The darn thing just won't stop running...

What obvious thing am I not seeing?

Thanks!
The service you are trying to stop is smbd not samba.  So you should use ```
[ sudo] service smbd stop
```... sudo if you are logged in as a mortal user.  Look in the /etc/init.d/ directory and read both of the scripts.  The samba script is for samba-ad-dc and the smbd script is for the smbd daemon.

---

### Post by bab1 on 2015-11-30
> **MeneM said:**
> So I tried doing a `apt-get remove --purge samba` so I could re-install it.

After removing it, I tried installing it with `apt-get install samba`
Now it wont start! WTF?

```
Nov 30 12:58:21 sudev03 samba[3185]:   ===============================================================
Nov 30 12:58:21 sudev03 samba[3185]: [2015/11/30 12:58:21.460920,  0] ../lib/util/fault.c:73(fault_report)
Nov 30 12:58:21 sudev03 samba[3185]:   INTERNAL ERROR: Signal 11 in pid 3185 (4.1.6-Ubuntu)
Nov 30 12:58:21 sudev03 samba[3185]:   Please read the Trouble-Shooting section of the Samba HOWTO
Nov 30 12:58:21 sudev03 samba[3185]: [2015/11/30 12:58:21.461040,  0] ../lib/util/fault.c:75(fault_report)
Nov 30 12:58:21 sudev03 samba[3185]:   ===============================================================
Nov 30 12:58:21 sudev03 samba[3185]: [2015/11/30 12:58:21.461105,  0] ../lib/util/fault.c:144(smb_panic_default)
Nov 30 12:58:21 sudev03 samba[3185]:   PANIC: internal error
..
```

I've never seen this from a simple samba installation before....
Samba isn't so simple anymore and the problems can be compounded by installing it using *tasksel*.  Did you originally install using *tasksel*.

---

### Post by MeneM on 2015-12-01
> **bab1 said:**
> Samba isn't so simple anymore and the problems can be compounded by installing it using *tasksel*.  Did you originally install using *tasksel*.

Nope, this was a clean iso install with nothing selected but openssh. Typical stuff.

And yes I tried:

```
/etc/init.d/samba stop/start
/etc/init.d/samba-ad-dc stop/start
/etc/init.d/smbd stop/start
/etc/init.d/nmbd/start
```

as well as:

```
service samba stop/start
service samba-ad-dc stop/start
service smbd stop/start
service nmbd/start
```

I tried running nmbd as a program (Not daemonised).

I'm also thinking this is not Samba's problem, but Ubuntu's init. As I'm basically asking init to stop the daemon but it is instead re spawning it immediately.

---

### Post by bab1 on 2015-12-01
> **MeneM said:**
> Nope, this was a clean iso install with nothing selected but openssh. Typical stuff.

And yes I tried:

```
/etc/init.d/samba stop/start
/etc/init.d/samba-ad-dc stop/start
/etc/init.d/smbd stop/start
/etc/init.d/nmbd/start
```

as well as:

```
service samba stop/start
service samba-ad-dc stop/start
service smbd stop/start
service nmbd/start
```

I tried running nmbd as a program (Not daemonised).

I'm also thinking this is not Samba's problem, but Ubuntu's init. As I'm basically asking init to stop the daemon but it is instead re spawning it immediately.
For sure this is not a Samba problem per se.  The only thing you need to stop/start smbd is```
service smbd stop/start
```
It does not sound like an inherent Ubuntu problem to me.  I can easily stop the smbd daemon on my 14.04 host.  The normal method is to run smbd as a program, not run as a daemon.  It is run as a forked instance.  Look below and you will see the -F showing the fork. 


This is what I get for running and then after stopping the smbd damon forking.```

bab@maui:~$ ps -ef|g mbd
root       723     1  0 21:22 ?        00:00:00 smbd -F
root       731   723  0 21:22 ?        00:00:00 smbd -F
root      1766     1  0 21:22 ?        00:00:00 nmbd -D


bab@maui:~$ sudo service smbd stop
[sudo] password for bab: 
smbd stop/waiting

bab@maui:~$ ps -ef|grep mbd
root      1766     1  0 21:22 ?        00:00:00 nmbd -D

```
I think that there is something damaged internally with the Ubuntu install or with the samba libs.  That would account for the seg-fault and the unusual behavior.  Under normal conditions everything works perfectly with just a minor tweak to the smb.conf.

Have you added anything other that the samba package?    Maybe winbindd or some such?

[COLOR="#0000FF"]Edit:  I have installed samba on Ubuntu 14.04 many times (25+).  Sometimes by just guiding clients on how to install.   I have never had one instance of a Samba or Ubuntu problem.   I have had problems with a tasksel install and or misguided client fingers. [/COLOR]

---

