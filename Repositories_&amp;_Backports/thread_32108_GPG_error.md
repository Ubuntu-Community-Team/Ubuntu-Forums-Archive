---
title: "GPG error"
date: 2005-05-06
forum: Repositories &amp; Backports
---

### Post by fng on 2005-05-06
When i did my daily apt-get update today i got the folowing error : 

```
Fetched 17.2kB in 1s (14.3kB/s)
Reading package lists... Done
W: GPG error: http://be.archive.ubuntu.com hoary-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems
fng@butters:~$
``` 

running apt-get update again doesnt solve the problem.

Has this repository been comprimised?
Should i change it 2 another local repository?

---

### Post by fng on 2005-05-06
i got a second one : hoary-security mirror

```
W: GPG error: http://security.ubuntu.com hoary-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
```

---

### Post by wporzo on 2005-05-06
I have "It" too, fng :/

---

### Post by J. S. Jackson on 2005-05-06
[QUOTE=fng]i got a second one : hoary-security mirror

```
W: GPG error: http://security.ubuntu.com hoary-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
```[/QUOTE]
Getting this same error today also...

---

### Post by rps63ifid on 2005-05-09
I was seeing this same error last Friday (05/06) and am still seeing it this morning:

W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

Can someone let me know what I (or someone else) needs to do to clear this up?

Thanks!

-- 
rps63ifid

---

### Post by fng on 2005-05-09
I dont know what was wrong, but it got macigly fixed here friday evening.

---

### Post by pnix on 2005-05-17
Me too...

---

### Post by mtron on 2005-05-19
I do still have the problems. 

How can you get a new key from the ubuntu archive?

The synaptic error:
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

Please help me.

Thanks!

---

