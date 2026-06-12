---
title: "windows 10 bash apt-get update not working (build 14332)"
date: 2016-04-29
forum: Windows
---

### Post by bhaverkamp on 2016-04-29
Trying to to an ap-get update on my brand new Windows 10 bash environment. I get the following output with errors. Using browser I checked the update site and it looks like these directories are in fact missing. The sources.list is at the end of this email. Anyone got this working.

```
bernieh@BERNIE-THINK:/$ sudo apt-get update
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty InRelease

Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates InRelease

Err [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease

Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty Release.gpg
  Could not resolve 'archive.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg
  Could not resolve 'security.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates Release.gpg
  Could not resolve 'archive.ubuntu.com'
Reading package lists... Done
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/trusty/InRelease](http://archive.ubuntu.com/ubuntu/dists/trusty/InRelease)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/trusty-updates/InRelease](http://archive.ubuntu.com/ubuntu/dists/trusty-updates/InRelease)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/trusty-security/InRelease](http://security.ubuntu.com/ubuntu/dists/trusty-security/InRelease)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/trusty/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/trusty/Release.gpg)  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/trusty-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/trusty-updates/Release.gpg)  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/trusty-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/trusty-security/Release.gpg)   Could not resolve 'security.ubuntu.com'bernieh@BERNIE-THINK:/etc/apt$  cat sources.list                                               
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty main restricted universe multiverse               
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-updates main restricted universe multiverse       
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted universe multiverse     

W: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by bhaverkamp on 2016-05-05
The issue turned out to be my security software. I removed bitdefender and now all is well.:)

---

### Post by joconnor on 2016-11-17
Also had a perennial problem with *apt-get update* not working - for months.

Update: 14 May 2017:

The actual error I always used to get was BADSIG for one of the package index files. I tried numerous times to uninstall Bash on Ubuntu on Windows as well as the WSL, but the error never disappeared. Eventually I re-installed Windows 10, and now *apt-get update* works fine.

I think I created the problem myself, by changing the repository mirror URL's in sources.list WITHOUT first doing an *apt-get clean*.
I think what was happening is that the signatures are stored outside the WSL somewhere in Windows and thus even by installing and re-installing the WSL the signatures were not being cleaned out.

Only by re-installing Windows was I able to solve the BADSIG error.

---

