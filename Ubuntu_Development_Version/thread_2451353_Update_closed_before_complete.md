---
title: "Update closed before complete"
date: 2020-10-02
forum: Ubuntu Development Version
---

### Post by andrew80 on 2020-10-02
Hi All,

Looking for some help, I decided I wanted to update my system from 20.04 to 20.10 BETA so I started it and left it to it. In the mean time I had another terminal tab open doing "speedtest -cli --simple" I then closed this tab but its also closed the update process by accident!!! 

So in the about menu now its listed as Groovy Gorilla but if I do an apt upgrade for example it comes back with errors 

```
andrewjb@andrewjb:~$ sudo apt updateHit:1 http://archive.canonical.com/ubuntu groovy InRelease
Hit:2 http://security.ubuntu.com/ubuntu groovy-security InRelease        
Hit:3 http://archive.ubuntu.com/ubuntu groovy InRelease                  
Hit:4 http://archive.ubuntu.com/ubuntu groovy-updates InRelease
Get:5 http://security.ubuntu.com/ubuntu bionic-security InRelease [88.7 kB]
Hit:6 http://archive.ubuntu.com/ubuntu groovy-backports InRelease
Get:7 http://archive.ubuntu.com/ubuntu bionic-updates InRelease [88.7 kB]
Err:5 http://security.ubuntu.com/ubuntu bionic-security InRelease    
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3B4FE6ACC0B21F32
Err:7 http://archive.ubuntu.com/ubuntu bionic-updates InRelease
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3B4FE6ACC0B21F32
Fetched 177 kB in 1s (273 kB/s)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up-to-date.
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://security.ubuntu.com/ubuntu bionic-security InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3B4FE6ACC0B21F32
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://archive.ubuntu.com/ubuntu bionic-updates InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3B4FE6ACC0B21F32
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/bionic-updates/InRelease  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3B4FE6ACC0B21F32
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/bionic-security/InRelease  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3B4FE6ACC0B21F32
W: Some index files failed to download. They have been ignored, or old ones used instead.



```

If I try upgrade or distro upgrade it does nothing, I don't think the update has completed and reckon their is a lot of software/packages which haven't updated. Is there anyway to rescue this install?

Its a Dell XPS Ubuntu Edition, was only supposed to support LTS version but I've switched it to non-LTS since. I get notifications about Dell BIOS updates in the Ubuntu software centre etc so its a proper install.

---

### Post by andrew80 on 2020-10-02
I've managed to sort the above update error out by disabling bionic-security and bionic-updates repositories. 

However I'm not 100% convinced the system is "fully upgraded"

---

### Post by deadflowr on 2020-10-02
Look at
```
lsb_release -a
```
and ```
uname -a
```
The first should have current release.
And the second would show current kernel version.

---

### Post by CelticWarrior on 2020-10-02
If all the repositories point to the new release now, you can try

```
sudo apt update && sudo apt full-upgrade
```

---

### Post by andrew80 on 2020-10-02
```
andrewjb@andrewjb:~$ lsb_release -aNo LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu Groovy Gorilla (development branch)
Release:	20.10
Codename:	groovy



```

```
Linux andrewjb 5.8.0-20-generic #21-Ubuntu SMP Wed Sep 23 00:39:43 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux


```

So it looks like its done it.

---

### Post by andrew80 on 2020-10-02
@celticwarrior just tried that, only update was for " xserver-xorg-video-amdgpu" which has now been done.

---

### Post by CelticWarrior on 2020-10-02
You're good to go. Enjoy Groovy Gorilla.

---

### Post by coffeecat on 2020-10-02
*Thread moved to **Ubuntu Development Version** sub-forum.*

---

