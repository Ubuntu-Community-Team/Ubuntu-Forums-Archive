---
title: "Problems when I tried git clone on raspberry pi"
date: 2017-03-26
forum: Server Platforms
---

### Post by sed_faster on 2017-03-26
Hello folks,

I have a repository git on raspberry pi and I have problems when I tried git clone on raspberry pi! I received this output:
```

xx@raspberrypi:/xx/xx/xx/levartogit $ git clone file://192.168.1.1:/media/pi/driveone/git/arci.git/
Cloning into 'arci'...
remote: Counting objects: 2193, done.
remote: fatal: Out of memory, malloc failed (tried to allocate 241210262 bytes)
error: git upload-pack: git-pack-objects died with error.B/s   
fatal: git upload-pack: aborting due to possible repository corruption on the remote side.
remote: aborting due to possible repository corruption on the remote side.
fatal: early EOF
fatal: index-pack failed

```

How can I fix this problem? This repository it is very important!
Thanks

---

### Post by TheFu on 2017-03-26
Can you clone it from a different system? Does that work?

How good are your backups?  git has cryptographic validation to fight corruption, so if it is suggesting corruption, that isn't good.

I have seen repo corruption due to a cracked motherboard, but that only happened once in 30+ yrs, so highly unlikely IME. Anywhere in the chain between the client and the server could cause corruption.  Use the process of elimination to determine where the issue lies.

If it is a public repo - post it here and I'll clone it. Can try x86 and my r-pi v2 here that way.

---

### Post by SeijiSensei on 2017-03-26
Looks to me like the real problem is insufficient memory:

```
remote: fatal: Out of memory, malloc failed (tried to allocate 241210262 bytes)
```

---

### Post by TheFu on 2017-03-26
True.  Did [Linus]("https://www.linux.com/blog/10-years-git-interview-git-creator-linus-torvalds") not handle an out of memory issue gracefully?  I'm inclined to think not, but who knows?

Nothing can be done about insufficient memory on a Pi, but if it is corruption or some other issue, there may be a solution. 

Anyway, that was my thought process.

If it is on github, can request the latest release as a ZIP file - without all the history. Any Pi should be able to handle that.

---

### Post by sed_faster on 2017-03-26
Ok, I took the disk from raspberry and put on my laptop.
I can did "git clone"
```

user@user:~/Documents/sandbox/recoverygit$ git clone file://192.168.1.1:/media/user/xxx/git/xx.git/
Cloning into 'xx'...
remote: Counting objects: 2193, done.
remote: Compressing objects: 100% (1835/1835), done.
remote: Total 2193 (delta 569), reused 1159 (delta 291)
Receiving objects: 100% (2193/2193), 9.50 GiB | 13.69 MiB/s, done.
Resolving deltas: 100% (569/569), done.
Checking connectivity... done.
Checking out files: 100% (1632/1632), done.


```

But now I have a new server, ubuntu server headless and I intend install my private repository on this machine. I have the disk connect on my laptop with the directory called "git" with all my repositories .git. How should I copy or transfer this directory to my new machine ubuntu server to use this as my git repository again?

thanks

---

### Post by TheFu on 2017-03-26
I'd use rsync.

There are many possible choices to do this. Which is best, only you can decide.

---

### Post by sed_faster on 2017-03-26
I will use rsync.
Which choices I can choose?

---

### Post by sed_faster on 2017-03-26
hello,
I tried this but I don't have success:
```

xx@headlessgit:/repository$ git clone --mirror file://192.168.1.1:/xx/xx/git/xx.git/ temp
Cloning into bare repository 'temp'...
remote: Counting objects: 2193, done.
error: pack-objects died of signal 985/1835)   
error: git upload-pack: git-pack-objects died with error.
fatal: git upload-pack: aborting due to possible repository corruption on the remote side.
remote: aborting due to possible repository corruption on the remote side.
fatal: early EOF
fatal: index-pack failed


```

what can I do?

---

