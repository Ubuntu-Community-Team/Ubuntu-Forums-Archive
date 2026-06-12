---
title: "Apt-get issues?"
date: 2014-10-09
forum: Server Platforms
---

### Post by DigiAngel on 2014-10-09
Odd:

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main amd64 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted amd64 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe amd64 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse amd64 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages
  404  Not Found [IP: 91.189.91.15 80]
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/source/Sources)  404  Not Found [IP: 91.189.91.15 80]
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/main/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise/main/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.15 80]
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.15 80]
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.15 80]
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.15 80]
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.91.15 80]
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.91.15 80]
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.91.15 80]
E: Some index files failed to download. They have been ignored, or old ones used instead.

Some issue with updates this morning on the server?

---

### Post by TheFu on 2014-10-10
Wait a few hours and try again?

---

### Post by DigiAngel on 2014-10-10
Tried, same results...very peculiar..thanks for the response.

---

### Post by TheFu on 2014-10-10
So ... looks like the package links aren't looking for the gzip version of the files. Those are available from what I can see and on a 14.04 box here, it is working with the .gz files.

Perhaps running update again will help?

---

### Post by DigiAngel on 2014-10-13
Thanks for looking again...I've rebooted the machine and done "sudo apt-get update" with the same results:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/source/Sources)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/main/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise/main/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.91.14 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.

Very odd...any thoughts?

---

### Post by Bashing-om on 2014-10-13
DigiAngel; Hey;

Maybe a fault in the mirror, I have seen the same issue reported on #ubuntu, resolved by changing the mirror.

won't hurt to try

---

### Post by TheFu on 2014-10-13
Can you manually visit these pages with a normal browser?

---

### Post by wlraider70 on 2014-10-13
can you ping/access other pages?

---

### Post by DigiAngel on 2014-10-15
Thanks for looking all.  Here's the full output:

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg [198 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release.gpg
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [50.7 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release [98.7 kB]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [112 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources [479 kB]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [2,494 B]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [32.7 kB]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [1,780 B]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages [431 kB]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages [4,627 B]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages [99.3 kB]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages [2,443 B]
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [464 kB]
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources [8,056 B]
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources [110 kB]
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [4,620 B]
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [105 kB]
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [2,645 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources [8,889 B]
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main amd64 Packages [841 kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted amd64 Packages [13.7 kB]
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe amd64 Packages [248 kB]
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse amd64 Packages [15.3 kB]
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages [873 kB]
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages [13.7 kB]
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages [255 kB]
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages [15.5 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources
  404  Not Found [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main amd64 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted amd64 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe amd64 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse amd64 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages
  404  Not Found [IP: 91.189.91.14 80]
Fetched 4,295 kB in 4s (984 kB/s)
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/source/Sources)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/main/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise/main/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.91.14 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by TheFu on 2014-10-15
> 
    Can you manually visit these pages with a normal browser? 

??

---

### Post by Bashing-om on 2014-10-15
DigiAngel; TheFu .. well, well ....

Do not really understand what is not going on:
```

http://us.archive.ubuntu.com/ubuntu/dists/precise/main/binary-amd64/Packages

``` does for me result in a 404.
BUT
```

http://us.archive.ubuntu.com/ubuntu/dists/precise/main/binary-amd64/

```
resolves and I am able to manually download  Packages.{bz,bz2} .

As of last night I still observed that others have a similar issue with ' us.archive.ubuntu.com/ ' on IRC #ubuntu.

So I must ask, who do we contact to make sure the problem is not in-house at 'us.archive.ubuntu.com/' ?

[INDENT][INDENT][/INDENT][/INDENT]I do remain open to a learning experience

---

### Post by DigiAngel on 2014-10-15
Negative:

 wget [http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/source/Sources)
--2014-10-15 10:37:45--  [http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/source/Sources)
Resolving us.archive.ubuntu.com (us.archive.ubuntu.com)... 91.189.91.13, 91.189.91.15, 91.189.91.14, ...
Connecting to us.archive.ubuntu.com (us.archive.ubuntu.com)|91.189.91.13|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2014-10-15 10:37:45 ERROR 404: Not Found.

---

### Post by TheFu on 2014-10-15
So I did it from here on a VM server running 12.04.4 ... everything worked. Won't try to patch - can't until a maint window this weekend.

```
 ....
Get: 6 http://us.archive.ubuntu.com precise-updates/main Sources [479 kB]
Get: 7 http://security.ubuntu.com precise-security/restricted Sources [2,494 B]
Get: 8 http://security.ubuntu.com precise-security/universe Sources [32.7 kB]
Get: 9 http://security.ubuntu.com precise-security/multiverse Sources [1,780 B]
Get: 10 http://security.ubuntu.com precise-security/main amd64 Packages [431 kB]
Get: 11 http://us.archive.ubuntu.com precise-updates/restricted Sources [8,056 B]
Get: 12 http://us.archive.ubuntu.com precise-updates/universe Sources [110 kB]
Get: 13 http://us.archive.ubuntu.com precise-updates/multiverse Sources [8,889 B]
......
Get: 35 http://security.ubuntu.com precise-security/restricted TranslationIndex [72 B]
Get: 36 http://security.ubuntu.com precise-security/universe TranslationIndex [73 B]
Hit http://security.ubuntu.com precise-security/main Translation-en
Hit http://security.ubuntu.com precise-security/multiverse Translation-en
Hit http://security.ubuntu.com precise-security/restricted Translation-en
Hit http://security.ubuntu.com precise-security/universe Translation-en
Fetched 4,308 kB in 5s (826 kB/s)
Reading package lists...
```

91.189.91.14 is the IP for us.archive.ubuntu.com from here.
I can only guess that a content network picked up partial changes?  Is there a way to flush the local copies of these files to force a fresh start locally?

---

### Post by DigiAngel on 2014-10-15
Interesting...I'll look in a couple days and see if I still see the issue.

---

