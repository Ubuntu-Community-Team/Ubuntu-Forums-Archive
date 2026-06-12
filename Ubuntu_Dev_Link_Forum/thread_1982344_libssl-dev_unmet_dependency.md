---
title: "libssl-dev unmet dependency"
date: 2012-05-18
forum: Ubuntu Dev Link Forum
---

### Post by stevebu56 on 2012-05-18
I am trying to install rails and one of the needed libraries is libssl-dev.  I get the following error when I try to install it with apt. 

```
The following packages have unmet dependencies:
 libssl-dev : Depends: libssl1.0.0 (= 1.0.1-4ubuntu3) but 1.0.1-4ubuntu5 is to be installed
              Recommends: libssl-doc but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

I just upgraded to 12.04 from 11.10 keeping my home partition intact.  I have updated apt and upgraded so everything looks to be current.  dpkg says I have libssl1.0.0 

I'm at a loss on what to do next.  If I'm reading the error correctly libssl1.01 is what libssl-dev depends on but it's trying to install 1.0.1.  Is this a bug with the libssl-dev package? 

Any help getting this installed would be appreciated.

---

### Post by MadCow108 on 2012-05-19
what is the output of this command:
```
apt-cache policy libssl-dev
```

maybe also try to install the version from precise-updates explicitly:
```
sudo apt-get install libssl-dev=1.0.1-4ubuntu5
```

---

### Post by stevebu56 on 2012-05-20
```
sburke@sewer:~$ apt-cache policy libssl-dev
libssl-dev:
  Installed: (none)
  Candidate: 1.0.1-4ubuntu3
  Version table:
     1.0.1-4ubuntu3 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/main amd64 Packages
```

---

### Post by stevebu56 on 2012-05-20
I tried to install the version explicitly but it doesn't look to be in the repo.  

```
sburke@sewer:~$ sudo apt-get install libssl-dev=1.0.1-4ubuntu5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Version '1.0.1-4ubuntu5' for 'libssl-dev' was not found
```

---

### Post by MadCow108 on 2012-05-20
you need to enable the precise-updates repository
this can be done in software sources (search in the dash)

---

### Post by stevebu56 on 2012-05-21
Thanks. Enabling precise-updates worked and I was able to install libssl-dev and later rails. I was mucking with the sources file because apt was telling me I had a duplicate entry so I started commenting out the duplicates and most likely commented out the updates line as well.

---

### Post by slouse on 2012-08-15
Thanks for the advice, but I have a similar problem and have not succeeded yet, although precise-updates is enabled. Do you have any other ideas? Here is my output:
```
$ apt-cache policy libssl-dev
libssl-dev:
  Installed: (none)
  Candidate: 1.0.1-4ubuntu5.3
  Version table:
     1.0.1-4ubuntu5.3 0
        500 [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) precise-updates/main amd64 Packages
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main amd64 Packages
     1.0.1-4ubuntu3 0
        500 [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) precise/main amd64 Packages
```

---

### Post by slouse on 2012-08-15
Following another thread, I did:

```
$sudo su
#aptitude install libssl-dev
```

Aptitude recommended to remove a whole bunch of i386 packages, which I accepted. When repeating the above command, I had to refuse the proposed "solution" to keep libssl-dev [Not Installed] and instead was offered the solution to downgrade 
```
libssl1.0.0 [1.0.1-4ubuntu5.4 (now) -> 1.0.1-4ubuntu5.3 (precise-security
```

I accepted this solution and libssl-dev was installed successfully. I have no idea what other problems I may have caused with this, but it seems to have worked...

---

