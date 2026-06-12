---
title: "ksh (pdksh) for ubuntu"
date: 2022-01-30
forum: Repositories &amp; Backports
---

### Post by rmstock2 on 2022-01-30
pdksh 5.2.14 has been adapted to run on Ubuntu versions :

[https://crashrecovery.org/pdksh/DEB/](https://crashrecovery.org/pdksh/DEB/)
[DIR]    ubuntu1404/    2017-12-18 03:34     -      
[DIR]    ubuntu1604/    2017-12-21 19:27     -      
[DIR]    ubuntu1804/    2022-01-27 19:34     -      
[DIR]    ubuntu2004/    2022-01-28 02:21     - 

[https://crashrecovery.org/pdksh/DEB/ubuntu2004/img/ksh-28012022-2.png](https://crashrecovery.org/pdksh/DEB/ubuntu2004/img/ksh-28012022-2.png)
Screenshot from Ubuntu 20.04.1 LTS

---

### Post by rmstock2 on 2022-01-30
as an example and reply to 

ksh vs bash: setting variable in piped loops are lost
[https://ubuntuforums.org/showthread.php?t=312017](https://ubuntuforums.org/showthread.php?t=312017)

This works in mksh 35b:
```
n=0
du | sort -n |& 
while read -p size dir
 
do
  if [ "$size" -gt 1000 ]
  then
    n=$((n+1))
  fi
done
echo "Found $n too big files"
```

This works in pdksh_5.2.14-30ubuntu1_amd64.deb :
```
#!/bin/ksh
n=0
(du | sort -n) |& 
while read -p size dir
 
do
  if [ "$size" -gt 1000 ]
  then
    n=$((n+1))
  fi
done
echo "Found $n too big files"

exit 0
```

---

