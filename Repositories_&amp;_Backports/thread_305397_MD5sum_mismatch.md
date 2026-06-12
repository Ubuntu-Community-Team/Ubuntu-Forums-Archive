---
title: "MD5sum mismatch"
date: 2006-11-23
forum: Repositories &amp; Backports
---

### Post by PatrickMay16 on 2006-11-23
Hey guys. Today I tried to do apt-get update, to see if there were new packages available. Though it's giving this error message:

```

patrick@ubuntu:~$ sudo apt-get update
Get: 1 http://security.ubuntu.com dapper-security Release.gpg [191B]                     
Get: 2 http://gb.archive.ubuntu.com dapper Release.gpg [189B]        
Ign http://wine.budgetdedicated.com dapper Release.gpg               
Hit http://security.ubuntu.com dapper-security Release               
Get: 3 http://gb.archive.ubuntu.com dapper-updates Release.gpg [191B]
Hit http://wine.budgetdedicated.com dapper Release
Hit http://gb.archive.ubuntu.com dapper Release
Hit http://security.ubuntu.com dapper-security/main Packages
Ign http://wine.budgetdedicated.com dapper/main Packages
Hit http://gb.archive.ubuntu.com dapper-updates Release
Hit http://security.ubuntu.com dapper-security/restricted Packages                                                        
Hit http://wine.budgetdedicated.com dapper/main Packages                                                                  
Hit http://security.ubuntu.com dapper-security/universe Packages     
Hit http://security.ubuntu.com dapper-security/multiverse Packages           
Hit http://gb.archive.ubuntu.com dapper/main Packages                        
Hit http://gb.archive.ubuntu.com dapper/restricted Packages
Hit http://gb.archive.ubuntu.com dapper/universe Packages
Hit http://gb.archive.ubuntu.com dapper/multiverse Packages
Get: 4 http://gb.archive.ubuntu.com dapper-updates/main Packages [128kB]
Hit http://gb.archive.ubuntu.com dapper-updates/restricted Packages
Fetched 128kB in 1s (109kB/s)
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.bz2  MD5Sum mismatch
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

What could this mean? Is this a problem on my end, or a tempoary problem with the repository which will eventually be fixed? It only happened today. The last time I updated was about a week or two ago, and it was fine then.

Also, even with this error message, it now reports that there are updates available. Is it safe to let it install these updates while apt is giving this error?

Sorry if these are stupid questions, I'd just prefer not to mess up my system since I kind of rely on it.

---

### Post by PatrickMay16 on 2006-11-24
FACKIN' LIKE A MASTER. I tell you, that error message has stopped happening now. I guess it was a temporary error to do with the servers or something.
So this is now solved.

---

