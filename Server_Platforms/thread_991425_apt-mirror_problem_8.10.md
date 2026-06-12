---
title: "apt-mirror problem 8.10"
date: 2008-11-23
forum: Server Platforms
---

### Post by Nick Payne on 2008-11-23
Trying to setup a local mirror for 8.10. My /etc/apt/mirror.list is very simple:

```
deb http://au.archive.ubuntu.com/ubuntu intrepid main restricted universe multiverse
deb http://au.archive.ubuntu.com/ubuntu intrepid-updates main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu intrepid-security main restricted universe multiverse

clean http://au.archive.ubuntu.com/ubuntu
```

When I run sudo apt-mirror I get:

```
nick@ubuntu:~$ sudo apt-mirror
Downloading 32 index files using 20 threads...
Begin time: Mon Nov 24 09:02:03 2008
[20]... [19]... [18]... [17]... [16]... [15]... [14]... [13]... [12]... [11]... [10]... [9]... [8]... [7]... [6]... [5]... [4]... [3]... [2]... [1]... [0]... 
End time: Mon Nov 24 09:02:03 2008

Proceed indexes: [Psh: cannot open au.archive.ubuntu.com/ubuntu//dists/intrepid/main/binary-i386/Packages.gz: No such file
apt-mirror: can't open index in proceed_index_gz at /usr/bin/apt-mirror line 390.
```

I thought the problem might be due to the double slash occurring in the pathname, so I edited apt-mirror and changed all occurrences of "/dist/" to "dist/", but that gave me the same error with no double-slash in the pathname.

I can go to [http://au.archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/]("http://au.archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/") in Firefox and download Packages.gz no problem. I also tried changing au.archive.ubuntu.com to archive.ubuntu.com to see if the problem was related to the mirror I was using, but the problem remained the same.

Any suggestion on what is causing this error?

Nick

ps. Should the double-slash be showing up in the pathname being spat out by the error msg?

---

### Post by syruis on 2009-02-14
Hi,

Same problem... No issues?

Regards,

---

### Post by jimv on 2009-02-14
Proceed indexes: [Psh: cannot open au.archive.ubuntu.com/ubuntu**//**dists/intrepid/main/binary-i386/Packages.gz: No such file

You have two /'s...that might be messing you up.

---

### Post by airtonix on 2009-11-14
1. Edit the apt-mirror script as admin 
```
sudo leafpad /usr/bin/apt-mirror
```
2. goto line 387
3. see this line : 
```
    system("gunzip < $path/$index.gz > $path/$index"); 
```
4. change it to this : 
```
    system("gunzip < $path$index.gz > $path/$index"); 
```
5. save it and try again.

---

### Post by mindfall903 on 2009-12-18
Airtonix,

Thanks for that reply.
I was setting up a local mirror (studying for the Ubuntu Certified Professional test right now) and I got the same error message.

With your help I was able to fix the problem which occured on Jaunty btw.

---

### Post by milegrin on 2012-05-11
Please excuse the necro...

I experienced the exact same problem and only found 4 possible solutions by trawling through various forums including this one, none of which helped.

After much ado and loss of precious hair I found the problem and it was obvious once I had it.

The public mirror I use to syncronise from ([ftp://ftp.is.co.za/mirror/ftp.ubuntu.com/](ftp://ftp.is.co.za/mirror/ftp.ubuntu.com/) ) restricts the number of connections from any given IP which means any connections after X get denied.  

Reducing my threads to "5" solved the problem! 

As this is an Ubuntu forum I trust posting it here saves many a stressful evening :)

Michael

---

### Post by Nopposan on 2013-03-01
Thanks everyone. The problem here wasn't solely to do with what yours turned out to be, but the reduction to 5 threads seemed sensible, so that's what I did. Also, I removed the forward slash from that one line in the apt-mirror executable like you said. I also had a permissions issue after running a cron job to update and I had to "chown apt-mirror" to those files, and somewhere along the line while experimenting I'd uncommented the "<defaultarch>" line in the mirrors.list; that threw up an error that "binary-" couldn't be found in the repos! That's because I am mirroring architectures other than the one I'm using on the server that holds the mirrors.

A few days ago, none of that would have made sense to me, but I'm very happy now that my mirrors are updating. Yay! Just had to share the joy. :-)

---

### Post by lisati on 2013-03-02
Old thread relating to old release closed.

---

