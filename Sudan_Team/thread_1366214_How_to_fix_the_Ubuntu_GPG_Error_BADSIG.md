---
title: "How to fix the Ubuntu GPG Error BADSIG"
date: 2009-12-28
forum: Sudan Team
---

### Post by zero-n on 2009-12-28
If you have got this error:

```
[COLOR="Red"][B]W: GPG error: http://archive.canonical.com intrepid Release: The following 
signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key[/B][/COLOR]

```

when you try to use:

```
apt-get update
```

then there is two methods to fix this :


**_Method 1:_**
Run these commands one after another:

```
sudo -i
apt-get clean
cd /var/lib/apt
mv lists lists.old
mkdir -p lists/partial
apt-get clean
apt-get update
```


**_Method 2:_**
Run these commands one after another:

```
sudo aptitude -o Acquire::http::No-Cache=True -o Acquire::BrokenProxy=true update

sudo apt-get update
```


Thanks to **[COLOR="Red"][ubuntu-geek]("http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html")[/COLOR]**

---

