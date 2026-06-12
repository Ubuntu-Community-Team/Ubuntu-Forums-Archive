---
title: "need source.list for server to install rar"
date: 2006-09-30
forum: Server Platforms
---

### Post by mojoman on 2006-09-30
Hi, I'm running an old machine as an FTP-server using Ubuntu 6.06 server OS and glFTPd. I need to unrar some files on it in order to rename them but RAR isn't installed. I tried apt-get install rar but I get the following output:

```
Package rar is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package rar has no installation candidate
```

I would rather unrar the files on the server, rename them and repack them instead of downloading them, going through the procedure and then uploading them again. I really don't have a lot of traffic on the server (it's mainly for private use) so I don't mind if some capacity is directed to this.

My guess is that it could be fixed by amending the sources.list but the various sources.list I've seen are intended for desktop/laptop. Can anyone help me out with this one?

best regards
Mojoman

Ps: My source list look like this. Ds:

```

# deb cdrom:[Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted

#deb cdrom:[Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted

deb http://se.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://se.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://se.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://se.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://se.archive.ubuntu.com/ubuntu/ dapper universe
deb-src http://se.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://se.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://se.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe
```

---

### Post by Jussi Kukkonen on 2006-09-30
rar and unrar are in multiverse. 

looke here for examples: [https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)


EDIT: forgot to mention: there's a unrar-free package in universe, but it doesn't open all rars.

---

### Post by mojoman on 2006-09-30
> **Jussi Kukkonen said:**
> rar and unrar are in multiverse. 

looke here for examples: [https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)


EDIT: forgot to mention: there's a unrar-free package in universe, but it doesn't open all rars.

I added multiverse after universe in my sources.list and that did the trick. Thanks for the help :D 

/mojoman

---

