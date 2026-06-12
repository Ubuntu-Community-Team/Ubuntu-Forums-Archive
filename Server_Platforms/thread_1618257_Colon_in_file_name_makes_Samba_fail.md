---
title: "Colon in file name makes Samba fail"
date: 2010-11-10
forum: Server Platforms
---

### Post by ajaaskel on 2010-11-10
- Ubuntu 10.10
- Long file names including colon
- Samba with mangling disabled
 

I inserted "mangled names = no" to /etc/samba/smb.conf because I need to see long file names. That works ok except with those file names containing colon.  I have a lot files containing colon in file name since those files are  originally named according to date and time.  That is very common with  videos and photos. I have Linux-only environment i.e. colon is a legal character in a file name.  

Is there a way to fix that in Samba ?

---

### Post by dtfinch on 2010-11-10
This [https://bugzilla.samba.org/show_bug.cgi?id=6196](https://bugzilla.samba.org/show_bug.cgi?id=6196) claims it was fixed in 3.3.3, and Maverick has 3.5.4. Maybe this would make a good bug/regression report, though I haven't tried to verify it myself. I wasn't aware colons were supported for non-Windows clients before now.

---

### Post by HermanAB on 2010-11-10
Uhmmm... if you have a Linux only environment, why are you using Samba? Samba is for Windows.  NFS is for UNIX.

---

### Post by ajaaskel on 2010-11-10
> **HermanAB said:**
> Uhmmm... if you have a Linux only environment, why are you using Samba? Samba is for Windows.  NFS is for UNIX.

Ubuntu defaults to Samba when you share a folder.  While Samba is easy for a temporary share NFS is ok for more permanent sharing. For a quick directory share NFS is cumbersome and too complicated for an average user:

[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

---

### Post by strid3r on 2013-01-06
Just run this following script to take out all of the colons

```
 
#!/bin/bash
find "$@" -name '*:*' -exec rename 's/://g' {} +
```

Name save it with root priveledges in /bin/ and name it something like colonremover (lol)

```

sudo gedit /bin/colonremover

```

```
colonremover /path/to/folder/or/file 
```

---

### Post by overdrank on 2013-01-06
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

