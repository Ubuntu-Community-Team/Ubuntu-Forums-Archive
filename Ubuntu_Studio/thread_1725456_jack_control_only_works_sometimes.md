---
title: "jack control only works sometimes"
date: 2011-04-09
forum: Ubuntu Studio
---

### Post by poodoopealeoaph on 2011-04-09
So, I just have a quick question. I have become interested in ubuntu studio again so I installed it from my current ubuntu install with ```
sudo apt-get install ubuntustudio-desktop
``` and I also went into ubuntu software center and installed all of the other related packages for ubuntu studio. The only thing though is that jack doesn't work most of the time. When i try to hit start for jack it just says that it can not start and that I should check the message log. well when I check the message log it doesn't give me any useful information. It just says that the overall operation failed and that jack can't start. If I hit stop and start again though, it usually works after one or two tries. Then it just says that it can not allocate memory. So, I would really like some advice on some config files to edit so things work just like they do right out of the box with a fresh install of ubuntu studio. thanks for the help.

---

### Post by Pablo_F on 2011-04-10
Hi,

Please, show the terminal output of the following informative **commands**:

rtprio and memlock security limits:
**ulimit -r -l**    

Content of limits.conf files:
**cat /etc/security/limits.conf /etc/security/limits.d/audio.conf**

The groups you are in:
**groups**

You last jackd command:
**cat ~/.jackdrc**

File list in /dev/shm:
**ls -lah /dev/shm**

Some info on your audio cards:
**arecord -l && aplay -l**

Cheers! Pablo

---

### Post by poodoopealeoaph on 2011-04-10
here are all of the things you asked for in the order that you mentioned them:```
ulimit -r -l
real-time priority              (-r) 0
max locked memory       (kbytes, -l) 64

``````
cat /etc/security/limits.conf /etc/security/limits.d/audio.conf
# /etc/security/limits.conf
#
#Each line describes a limit for a user in the form:
#
#<domain>        <type>  <item>  <value>
#
#Where:
#<domain> can be:
#        - an user name
#        - a group name, with @group syntax
#        - the wildcard *, for default entry
#        - the wildcard %, can be also used with %group syntax,
#                 for maxlogin limit
#        - NOTE: group and wildcard limits are not applied to root.
#          To apply a limit to the root user, <domain> must be
#          the literal username root.
#
#<type> can have the two values:
#        - "soft" for enforcing the soft limits
#        - "hard" for enforcing hard limits
#
#<item> can be one of the following:
#        - core - limits the core file size (KB)
#        - data - max data size (KB)
#        - fsize - maximum filesize (KB)
#        - memlock - max locked-in-memory address space (KB)
#        - nofile - max number of open files
#        - rss - max resident set size (KB)
#        - stack - max stack size (KB)
#        - cpu - max CPU time (MIN)
#        - nproc - max number of processes
#        - as - address space limit (KB)
#        - maxlogins - max number of logins for this user
#        - maxsyslogins - max number of logins on the system
#        - priority - the priority to run user process with
#        - locks - max number of file locks the user can hold
#        - sigpending - max number of pending signals
#        - msgqueue - max memory used by POSIX message queues (bytes)
#        - nice - max nice priority allowed to raise to values: [-20, 19]
#        - rtprio - max realtime priority
#        - chroot - change root to directory (Debian-specific)
#
#<domain>      <type>  <item>         <value>
#

#*               soft    core            0
#root            hard    core            100000
#*               hard    rss             10000
#@student        hard    nproc           20
#@faculty        soft    nproc           20
#@faculty        hard    nproc           50
#ftp             hard    nproc           0
#ftp             -       chroot          /ftp
#@student        -       maxlogins       4

# End of file
# Provided by the jackd package.
#
# Changes to this file will be preserved.
#
# If you want to enable/disable realtime permissions, run
#
#    dpkg-reconfigure -p high jackd

@audio   -  rtprio     95
@audio   -  memlock    unlimited
#@audio   -  nice      -19

```
```
groups
*myname* adm dialout cdrom plugdev lpadmin admin sambashare
```
```
cat ~/.jackdrc
/usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2

```
```
ls -lah /dev/shm
total 372K
drwxrwxrwt  2 root root  180 2011-04-10 03:51 .
drwxr-xr-x 18 root root 3.7K 2011-04-10 03:47 ..
-r--------  1 *myname* *myname*  65M 2011-04-10 03:51 pulse-shm-1939903503
-r--------  1 *myname* *myname*  65M 2011-04-10 03:52 pulse-shm-2445904547
-r--------  1 *myname* *myname*  65M 2011-04-10 03:48 pulse-shm-3133271540
-r--------  1 *myname* *myname*  65M 2011-04-10 03:47 pulse-shm-3348181820
-r--------  1 *myname* *myname*  65M 2011-04-10 03:47 pulse-shm-3690824121
-r--------  1 *myname* *myname*  65M 2011-04-10 03:47 pulse-shm-3991579827
-r--------  1 *myname* *myname*  65M 2011-04-10 03:47 pulse-shm-872243639

```
```
arecord -l && aplay -l
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC272X Analog [ALC272X Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC272X Analog [ALC272X Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```

---

### Post by Pablo_F on 2011-04-10
Hi, 


You need to add your user name to the audio group, so it can get the rtprio and memlock privileges.

You can do it via "users and groups" in the system, administration menu, but it is faster with this command:

**sudo adduser your_user_name audio**

Then, you need to reboot.

Now, check that you have the said privileges:

**ulimit -r -l** should return now:

```
real-time priority              (-r) 95
max locked memory       (kbytes, -l) unlimited
```


Your jack configuration seems sane. Sometimes, it helps appending "-S" to the "server path" field as long as you run jackd2. I forgot to ask you for your jack version:

**jackd --version**

If it is jackdmp 1.9.x you are running jackd2.
It it is jack 0.xxx.x you are running jackd1.


Cheers, Pablo

---

### Post by Pablo_F on 2011-04-10
Ah, I almost forgot:

Those all pulse-shm-* in /dev/shm can be harmful. 
This is a known bug. I strongly recommend you clean them:

**rm -f /dev/shm/pulse-shm***

Cheers, Pablo

---

