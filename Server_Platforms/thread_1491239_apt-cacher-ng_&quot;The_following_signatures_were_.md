---
title: "apt-cacher-ng &quot;The following signatures were invalid: BADSIG&quot;"
date: 2010-05-23
forum: Server Platforms
---

### Post by davidshere on 2010-05-23
I've been running apt-cacher-ng for a while now and I just recently started getting this message when doing an apt-get update on clients:

**W: GPG error: [http://thebone](http://thebone) lucid-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>**

What can I do to clear this?  

Because of this error it's saying that the packages can't be authenticated.

---

### Post by davidshere on 2010-05-24
Upon suggestion I have also tried the command [B] sudo apt-get update -o Acquire::http::No-Cache=true
[/B] on the client and got similar results:

```
david@lucid-testing:~$  sudo apt-get update -o Acquire::http::No-Cache=true
Hit http://thebone lucid Release.gpg
Ign http://thebone/us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Ign http://thebone/us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Ign http://thebone/us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://thebone/us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Get:1 http://thebone lucid-updates Release.gpg [189B]
Ign http://thebone/us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://thebone/us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://thebone/us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://thebone/us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://thebone lucid-backports Release.gpg
Ign http://thebone/us.archive.ubuntu.com/ubuntu/ lucid-backports/main Translation-en_US
Ign http://thebone/us.archive.ubuntu.com/ubuntu/ lucid-backports/restricted Translation-en_US
Ign http://thebone/us.archive.ubuntu.com/ubuntu/ lucid-backports/universe Translation-en_US
Ign http://thebone/us.archive.ubuntu.com/ubuntu/ lucid-backports/multiverse Translation-en_US
Hit http://thebone lucid Release.gpg
Ign http://thebone/archive.canonical.com/ubuntu/ lucid/partner Translation-en_US
Hit http://thebone lucid-security Release.gpg
Ign http://thebone/security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Ign http://thebone/security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://thebone/security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://thebone/security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://thebone lucid Release
Get:2 http://thebone lucid-updates Release [38.5kB]
Ign http://thebone lucid-updates Release
Hit http://thebone lucid-backports Release
Hit http://thebone lucid Release
Hit http://thebone lucid-security Release
Hit http://thebone lucid/main Packages
Hit http://thebone lucid/restricted Packages
Hit http://thebone lucid/main Sources
Hit http://thebone lucid/restricted Sources
Hit http://thebone lucid/universe Packages
Hit http://thebone lucid/universe Sources
Hit http://thebone lucid/multiverse Packages
Hit http://thebone lucid/multiverse Sources
Hit http://thebone lucid-updates/main Packages
Hit http://thebone lucid-updates/restricted Packages
Hit http://thebone lucid-updates/main Sources
Hit http://thebone lucid-updates/restricted Sources
Hit http://thebone lucid-updates/universe Packages
Hit http://thebone lucid-updates/universe Sources
Hit http://thebone lucid-updates/multiverse Packages
Hit http://thebone lucid-updates/multiverse Sources
Hit http://thebone lucid-backports/main Packages
Hit http://thebone lucid-backports/restricted Packages
Hit http://thebone lucid-backports/universe Packages
Hit http://thebone lucid-backports/multiverse Packages
Hit http://thebone lucid-backports/main Sources
Hit http://thebone lucid-backports/restricted Sources
Hit http://thebone lucid-backports/universe Sources
Hit http://thebone lucid-backports/multiverse Sources
Hit http://thebone lucid/partner Packages
Hit http://thebone lucid/partner Sources
Hit http://thebone lucid-security/main Packages
Hit http://thebone lucid-security/restricted Packages
Hit http://thebone lucid-security/main Sources
Hit http://thebone lucid-security/restricted Sources
Hit http://thebone lucid-security/universe Packages
Hit http://thebone lucid-security/universe Sources
Hit http://thebone lucid-security/multiverse Packages
Hit http://thebone lucid-security/multiverse Sources
Fetched 190B in 19s (10B/s)
Reading package lists... Done
W: GPG error: http://thebone lucid-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
david@lucid-testing:~$
```

---

### Post by davidshere on 2010-06-13
bump :)

---

### Post by apalacheno on 2010-12-02
Yeah, that would interest me as well!

---

### Post by tajiknomi on 2010-12-07
[SIZE=2]Try these commands:-

[/SIZE]```
[SIZE=4]apt-get clean
cd /var/lib/apt
mv lists lists.old
mkdir -p lists/partial
apt-get clean
apt-get update[/SIZE]
```

---

### Post by WildTangent on 2011-03-01
Neither method fixed the problem. Any other ideas besides purging the entire cache?

---

### Post by smoka on 2011-08-05
Hi,

I know it's been a while since the question was asked, but if you never found a fix this may help...

I get a similar (known) problem regularly with the Virtualbox repository, and found that it also seems apt-cacher keeps whatever bad file.

So, as well as doing the steps listed.
Before doing the final "apt-get update"

Choose this from Apt-Cacher NG webpage on the server:
Force the download of index files (even having fresh ones) 

Takes a while, but found that was the only thing that fixed it for me.

hth

---

### Post by apalacheno on 2011-08-06
> **smoka said:**
> 
Choose this from Apt-Cacher NG webpage on the server:
Force the download of index files (even having fresh ones) 

Ah, good to know, I'll try that next time.

So far, a reliable method was deleting the cache files on the server:

```
rm -R /var/cache/apt-cacher-ng/download.virtualbox.org
```

After the next 'apt-get update' on the client, the error messages disappeared.

Although a bit harsh, it worked every time.

---

### Post by smoka on 2011-12-27
> **apalacheno said:**
> 

```
rm -R /var/cache/apt-cacher-ng/download.virtualbox.org
```



Thanks, that seems to have worked a treat also, and much faster than doing the "Force the download of index files (even having fresh ones)" option.

---

### Post by apalacheno on 2011-12-27
You're welcome :-)

---

