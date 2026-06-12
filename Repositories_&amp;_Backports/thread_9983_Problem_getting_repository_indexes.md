---
title: "Problem getting repository indexes"
date: 2005-01-03
forum: Repositories &amp; Backports
---

### Post by tim.n.em on 2005-01-03
I am having trouble getting Synaptic and apt-get to work with the main restricted Repositories.  When ever I do an update in Synaptic I get:
```
Couldn't stat source package list http://archive.ubuntu.com/warty/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_warty_main_binary-i386_Packages) -stat (2 No such file or directory)
```

When I run sudo apt-get update I get:

```
Get:1 http://archive.ubuntu.com warty/main Packages [2145kB]
Err http://archive.ubuntu.com warty/main Packages
  Error reading from server - read (104 Connection reset by peer)
Hit http://archive.ubuntu.com warty/main Release
Get:2 http://archive.ubuntu.com warty/restricted Packages [21.3kB]
0% [2 Packages gzip 0] [Waiting for headers]
gzip: stdin: not in gzip format
Err http://archive.ubuntu.com warty/restricted Packages
  Sub-process gzip returned an error code (1)
Hit http://archive.ubuntu.com warty/restricted Release
Get:3 http://archive.ubuntu.com warty/main Sources [686kB]
Err http://archive.ubuntu.com warty/main Sources
  Error reading from server - read (104 Connection reset by peer)
Hit http://archive.ubuntu.com warty/main Release
Get:4 http://archive.ubuntu.com warty/restricted Sources [3159B]
0% [Connecting to archive.ubuntu.com (82.211.81.138)]
gzip: stdin: not in gzip format
Err http://archive.ubuntu.com warty/restricted Sources
  Sub-process gzip returned an error code (1)
Hit http://archive.ubuntu.com warty/restricted Release
Fetched 24.4kB in 1s (22.6kB/s)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/warty/main/binary-i386/Packages.gz  Error reading from server - read (104 Connection reset by peer)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/warty/restricted/binary-i386/Packages.gz  Sub-process gzip returned an error code (1)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/warty/main/source/Sources.gz  Error reading from server - read (104 Connection reset by peer)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/warty/restricted/source/Sources.gz  Sub-process gzip returned an error code (1)
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

I am on a network with a squid proxy server, but I don't think that is the problem since my internet/email/IM works fine.

---

### Post by nikopol on 2005-01-03
> I am on a network with a squid proxy server, but I don't think that is the problem since my internet/email/IM works fine.

Had the same problem earlier today (see my thread about it for the way I got around it) and am also behind a Squid proxy (transparent) which I therefore can't bypass... That's probably the problem then!

Come to think of it, we had problems earlier on in the week when accessing hotmail (which was later resolved by hotmail) and it had something to do with gz compression. for the record, I'm behind ipcop 1.4.2 using squid-2.5STABLE7 as a transparant proxy. I'll check tomorrow if it works with the proxy turned off


N

---

