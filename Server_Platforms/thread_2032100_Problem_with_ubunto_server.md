---
title: "Problem with ubunto server"
date: 2012-07-23
forum: Server Platforms
---

### Post by nikibg on 2012-07-23
Hello , I am new with linux and i have a problem which i cant solve

I wanna intall UUCP package but when type :
```
sudo apt-get install UUCP
[sudo] password for niki: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done

```
its out :
```
E: Unable to locate package UUCP
can someone help me

```

---

### Post by nothingspecial on 2012-07-23
Hi,

it's uucp

with lowercase letters.

---

### Post by nikibg on 2012-07-23
10x for fast answer but its show me that message
E: Unable to locate package  
for any package i try to install

---

### Post by nothingspecial on 2012-07-23
What happens when you type

```
sudo apt-get update
```

---

### Post by nikibg on 2012-07-23
```
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease
  
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg
  Temporary failure resolving 'security.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise InRelease
  
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates InRelease
  
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports InRelease
  
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release.gpg
  Temporary failure resolving 'us.archive.ubuntu.com'
Reading package lists... Done
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/precise/InRelease)  

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/InRelease)  

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/InRelease)  

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/InRelease](http://security.ubuntu.com/ubuntu/dists/precise-security/InRelease)  

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/precise-security/Release.gpg)  Temporary failure resolving 'security.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/precise/Release.gpg)  Temporary failure resolving 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/Release.gpg)  Temporary failure resolving 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/Release.gpg)  Temporary failure resolving 'us.archive.ubuntu.com'

W: Some index files failed to download. They have been ignored, or old ones used instead.
```

:confused:

---

### Post by nothingspecial on 2012-07-23
Is the server connected to the internet?

---

### Post by nikibg on 2012-07-23
yes i use secureCRT to connect with ubuntu on my other pc :confused:

---

### Post by nikibg on 2012-07-23
&#1040;ny ideas :confused::confused::confused:

---

