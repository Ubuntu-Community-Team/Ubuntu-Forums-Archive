---
title: "Ubuntu 9.10 Apt-mirror error - doesn't work with non-standard HTTP port (8080)"
date: 2009-11-05
forum: Server Platforms
---

### Post by Deniska on 2009-11-05
EDIT: Sorry for my poor english (:.

Hi all. I'm setting up local ubuntu repo for my network. I've apt-update and apt-upgrade my system and install apt-mirror on a clean ubuntu 9.10 x32 server, then i met two problems.
At first - my /etc/apt/mirror.list:
```
############# config ##################
set run_postmirror 0
set nthreads     20
set _tilde 0
############# end config ##############

deb http://repo.opentomsk.net:8080/ubuntu/ru.archive.ubuntu.com/ubuntu karmic main restricted universe multiverse
deb http://repo.opentomsk.net:8080/ubuntu/ru.archive.ubuntu.com/ubuntu karmic-updates main restricted universe multiverse
deb http://repo.opentomsk.net:8080/ubuntu/ru.archive.ubuntu.com/ubuntu karmic-security main restricted universe multiverse
deb http://repo.opentomsk.net:8080/ubuntu/ru.archive.ubuntu.com/ubuntu karmic-backports main restricted universe multiverse

clean http://repo.opentomsk.net:8080/ubuntu/ru.archive.ubuntu.com/ubuntu

```repo.opentomsk.net is another repo mirror accessible from my local town network. I'm connected with this mirror with a cable 100mbit, so i prefer to mirror this site, not official (1mbit connection speed). As you can see, it's serves requests on 8080 port, not on default HTTP port - 80.

The first problem: /var/spool/apt-mirror/var/apt-mirror.lock lock file doesn't removed if apt-mirror fails. It's removed *only* if apt-mirror finished successfully. So you *must* remove this file manually after any unsuccessfull apt-mirror launch (file non found, connection lost etc) or you will always get error 
```
apt-mirror is already running, exiting at /usr/bin/apt-mirror line 187.
```Hope this helps someone. Google say that this error is 9.10 specific and already reported to developers.

And the second problem: apt-mirror doesn't work with non-standard port correctly.
In the [manual page]("http://manpages.ubuntu.com/manpages/karmic/man1/apt-mirror.1.html") i've found this:
```

...
HTTP and FTP Auth or non-standard port: deb[URL="http://user:pass@example.com:8080/debian"]
http://user:pass@example.com:8080/debian[/URL] stable main contrib non-free
...

```So.. Non-standard ports are supported.
But when i'm run apt-mirror, i got this message

```
# sudo apt-mirror
Downloading 64 index files using 20 threads...
Begin time: Thu Nov  5 16:04:05 2009
[20]... [19]... [18]... [17]... [16]... [15]... [14]... [13]... [12]... [11]... [10]... [9]... [8]... [7]... [6]... [5]... [4]... [3]... [2]... [1]... [0]...
End time: Thu Nov  5 16:04:06 2009

Proceed indexes: [Psh: cannot open **repo.opentomsk.net**/ubuntu/ru.archive.ubuntu.com/ubuntu//dists/karmic/main/binary-i386/Packages.gz: No such file
apt-mirror: can't open index in proceed_index_gz at /usr/bin/apt-mirror line 436.
```Double slashes in "..ubuntu**//**dists.." automatically translates to single slash by web-server, so **repo.opentomsk.net:8080**/ubuntu/ru.archive.ubuntu.com/ubuntu**//**dists/karmic/main/binary-i386/Packages.gz is successfully accessible by browser - file exists. But the port number (8080) is removed. Google gives me [this link]("http://ubuntuforums.org/showthread.php?t=1290930"). The error message was the same, but the reason of a problem is another. In my case "Packages.gz" **in fact successfully downloads** and places in /var/spool/apt-mirror/skel/repo.opentomsk.net**:8080**/ubuntu/ru.archive.ubuntu.com/ubuntu/dists/karmic/main/binary-i386 (i'm check md5 sum both for downloaded file and manually downloaded Packages.gz from a web-server - they are equal) and then apt-mirror checks /var/spool/apt-mirror/skel/repo.opentomsk.net/.. without port number 8080.
Okay. You boss. I've copy /var/spool/apt-mirror/skel/repo.opentomsk.net:8080/ to /var/spool/apt-mirror/skel/repo.opentomsk.net/. The directory size of repo.opentomsk.net:8080 was 26Mb (not all files were fetched). Then i run apt-mirror again.. And voila - apt-mirror goes well. At first, he finish populate /var/spool/apt-mirror/skel/repo.opentomsk.net so it's 59Mb now. Then he continue mirroring packages in /var/spool/mirror/**repo.opentomsk.net:8080**. Yes, he appends port number to the directory name.
Looks like he works in a such way: making skel from repo.opentomsk.net:8080 to skel/repo.opentomsk.net:8080, then checks skel/repo.opentomsk.net (without port number) and then continue downloading packages to mirror/repo.opentomsk.net:8080.

Guys, where i'm lame? ]: How can i force apt-mirror to check skel/repo.opentomsk.net:8080 instead of non-existent (by default) skel/repo.opentomsk.net? I do not want to copy this directory manually and check it integrity every time i'm update my mirror.
Thank you.

---

