---
title: "Segmentation fault with thunderbird-3.0"
date: 2010-03-18
forum: Ubuntuzilla
---

### Post by mmerlone on 2010-03-18
Hi all,

I am trying to run thunderbird-3.0 on Ubuntu 9.10. I followed the guides and added ubuntuzilla repos and got it installed, but when I try to run it I get:

```
mmerlone@ubuntu-box:~$ thunderbird-3.0 
Segmentation fault
mmerlone@ubuntu-box:~$ 
```

It is a clean machine install, clean home dir, no profile at all. What's next to make it run?

Thanks and best regards.

---

### Post by byStanderone on 2010-03-18
...segmentation faults usually happen after an improper or incomplete installation of an application. the *.bin are not removed from /var/cache/apt/ thereby causing the error...running an rm command is not advisable...a sudo apt-get autoclean usually corrects the problem.

---

### Post by nanotube on 2010-03-18
> **mmerlone said:**
> Hi all,

I am trying to run thunderbird-3.0 on Ubuntu 9.10. I followed the guides and added ubuntuzilla repos and got it installed, but when I try to run it I get:

```
mmerlone@ubuntu-box:~$ thunderbird-3.0 
Segmentation fault
mmerlone@ubuntu-box:~$ 
```

It is a clean machine install, clean home dir, no profile at all. What's next to make it run?

Thanks and best regards.

hi
ubuntuzilla does not install a 'thunderbird-3.0' link. it only installs a plain 'thunderbird' link. so the segfault you are getting is not from the ubuntuzilla version.

i'm guessing you installed from the ubuntu-mozilla-daily repository, a daily trunk build, which is what's causing problems.

try starting just a regular "thunderbird" and see if that behaves any different.

---

### Post by mmerlone on 2010-03-18
> **nanotube said:**
> hi
ubuntuzilla does not install a 'thunderbird-3.0' link. it only installs a plain 'thunderbird' link. so the segfault you are getting is not from the ubuntuzilla version.

i'm guessing you installed from the ubuntu-mozilla-daily repository, a daily trunk build, which is what's causing problems.

try starting just a regular "thunderbird" and see if that behaves any different.

Sure, really sorry. I am trying so many alternatives, and none is working. With ubuntuzilla version, this is what I get:

```

marcio.merlone@mic-062:~$ dpkg -l | grep thunderbird
ii  thunderbird-mozilla-build             3.0.3-0ubuntu1                                           Mozilla Thunderbird, official Mozilla build,
marcio.merlone@mic-062:~$ time thunderbird 
^C

real	2m37.716s
user	0m0.380s
sys	0m0.132s
marcio.merlone@mic-062:~$ 

```

I timed the execution just to make you sure I waited enough, it does nothing, just sits there. So, hoping to be of some help, I straced:

```

strace -o tb.log thunderbird

```

and. from another terminal tail -f tb.log:

```

(...)
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0xb786c938) = 6299
close(4)                                = 0
read(3, "/opt/thunderbird\n", 128)      = 17
--- SIGCHLD (Child exited) @ 0 (0) ---
read(3, "", 128)                        = 0
close(3)                                = 0
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0, NULL) = 6299
chdir("/home/usuarios/marcio.merlone")  = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0xb786c938) = 6300
wait4(-1, ^C
root@mic-062:~marcio.merlone# 

```

It simply stops there and go no further, dont know why, until it gets murdered, I mean, killed.

On time, this user comes from an LDAP database, with the help of pam, is not a regular /etc/passwd user. I will try with a regular user and post here.

(5 minutes later)

I just tested a local user and it works. With an LDAP user it does not, and just TB. Any hint or idea?

---

### Post by nanotube on 2010-03-18
hi
no idea, seems like maybe it's a bug in thunderbird? try snooping around on the mozilla support forums or looking through their bugzilla.

---

### Post by mmerlone on 2010-03-18
> **nanotube said:**
> hi
no idea, seems like maybe it's a bug in thunderbird? try snooping around on the mozilla support forums or looking through their bugzilla.

Indeed. Even ubuntuzilla package did not run, yet it didn't crash, but did nothing, just run and nothing happens. I had to install and run nscd so it could be executed accordingly.

Tks, best regards.

---

