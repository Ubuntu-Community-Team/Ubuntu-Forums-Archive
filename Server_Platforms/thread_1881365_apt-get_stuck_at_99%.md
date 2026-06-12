---
title: "apt-get stuck at 99%"
date: 2011-11-15
forum: Server Platforms
---

### Post by dboss101 on 2011-11-15
Hi,

I have a server running with Ubuntu 10.04 LTS, and I have a very weird problem.

whenever I run apt-get update , it gets stuck at some point showing this :

```
root@proxy-pd:~# apt-get update
Hit http://security.ubuntu.com lucid-security Release.gpg
Hit http://us.archive.ubuntu.com lucid Release.gpg
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://security.ubuntu.com lucid-security Release
Hit http://security.ubuntu.com lucid-security/main Packages
Get:1 http://security.ubuntu.com lucid-security/restricted Packages [14B]
Get:2 http://security.ubuntu.com lucid-security/main Sources [68.0kB]
Get:3 http://security.ubuntu.com lucid-security/restricted Sources [14B]
Get:4 http://security.ubuntu.com lucid-security/universe Packages [94.3kB]
Get:5 http://security.ubuntu.com lucid-security/universe Sources [26.2kB]
Get:6 http://security.ubuntu.com lucid-security/multiverse Packages [4,423B]
Get:7 http://security.ubuntu.com lucid-security/multiverse Sources [1,750B]
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid Release
Hit http://us.archive.ubuntu.com lucid/main Packages
Get:8 http://us.archive.ubuntu.com lucid/restricted Packages [6,193B]
Get:9 http://us.archive.ubuntu.com lucid/main Sources [659kB]
Get:10 http://us.archive.ubuntu.com lucid/restricted Sources [3,775B]
Get:11 http://us.archive.ubuntu.com lucid/universe Packages [5,430kB]
Get:12 http://us.archive.ubuntu.com lucid/universe Sources [3,165kB]
Get:13 http://us.archive.ubuntu.com lucid/multiverse Packages [176kB]
Get:14 http://us.archive.ubuntu.com lucid/multiverse Sources [119kB]
99% [8 Packages bzip2 0B]

```when I run it with strace this is the output at the end :

```
 ...}) = 0
rt_sigprocmask(SIG_BLOCK, [WINCH], [], 8) = 0
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
99% [2 Packages bzip2 0B]) = 26p2 0B]", 26
select(10, [5 6 7 9], [], NULL, {0, 500000}) = 0 (Timeout)
stat("/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_lucid_restricted_binary-amd64_Packages.decomp", {st_mode=S_IFREG|0644, st_size=0, ...}) = 0
rt_sigprocmask(SIG_BLOCK, [WINCH], [], 8) = 0
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
99% [2 Packages bzip2 0B]) = 26p2 0B]", 26
select(10, [5 6 7 9], [], NULL, {0, 500000}) = 0 (Timeout)
stat("/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_lucid_restricted_binary-amd64_Packages.decomp", {st_mode=S_IFREG|0644, st_size=0, ...}) = 0
rt_sigprocmask(SIG_BLOCK, [WINCH], [], 8) = 0
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
99% [2 Packages bzip2 0B]) = 26p2 0B]", 26
select(10, [5 6 7 9], [], NULL, {0, 500000}^C <unfinished ...>
root@proxy-pd:~#

```this is my sources.list (very basic) :

```
deb http://us.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid main restricted
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse
```what can I do ?

can you please help ?

Thanks in advance.

---

### Post by BillyBoa on 2011-11-15
You have to change Main Server of downloads.

Go to your Software Sources, there are in Update Manager and from there choose the best server.

---

### Post by Elfy on 2011-11-15
If you've no gui then to change where the repos come from you'd need to change the lines manually I think.

---

### Post by dboss101 on 2011-11-15
I dont mind to change the repos but to what ?

---

### Post by Elfy on 2011-11-15
You could try the main server.

I'm running oneiric so the versions will be slightly different to you - but this is a line from using the UK server

deb http://[COLOR="Red"]gb.archive.ubuntu.com[/COLOR]/ubuntu/ oneiric-updates main restricted

and from using the main server 

deb http://[COLOR="Red"]archive.ubuntu.com[/COLOR]/ubuntu oneiric-updates main restricted

Check and see what your's say now and try - or you could paste your list here.

---

### Post by dboss101 on 2011-11-16
Thanks, I've tried to use the main server, but I still encounter the same problem ...

here :

```
Get:44 http://archive.ubuntu.com lucid-updates/restricted Packages [4,011B]
Get:45 http://archive.ubuntu.com lucid-updates/restricted Packages [4,011B]
Get:46 http://archive.ubuntu.com lucid-updates/main Sources [205kB]
Get:47 http://archive.ubuntu.com lucid-updates/main Sources [205kB]
Get:48 http://archive.ubuntu.com lucid-updates/main Sources [205kB]
Get:49 http://archive.ubuntu.com lucid-updates/main Sources [205kB]
Get:50 http://archive.ubuntu.com lucid-updates/restricted Sources [1,850B]
Get:51 http://archive.ubuntu.com lucid-updates/restricted Sources [1,850B]
Get:52 http://archive.ubuntu.com lucid-updates/universe Packages [238kB]
Get:53 http://archive.ubuntu.com lucid-updates/universe Sources [82.1kB]
Get:54 http://archive.ubuntu.com lucid-updates/multiverse Packages [10.4kB]
Get:55 http://archive.ubuntu.com lucid-updates/multiverse Sources [5,073B]
99% [26 Sources bzip2 0B]

```

any more ideas ?

---

### Post by Elfy on 2011-11-16
You could try removing the apt lists and updating again - I did have this once myself, trying to work backwards through some notes - old notes ... :(

Try 
```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update


```

---

### Post by dboss101 on 2011-11-16
it didn't help ... 

but I found the solution on google, it said to do this :

```
echo 'Acquire::http::Pipeline-Depth "0";' > /etc/apt/apt.conf.d/90localsettings
```

and it solved the problem !

---

### Post by Elfy on 2011-11-16
Sorry I couldn't help - but thanks for actually coming back with what did help you - many don't :)

---

