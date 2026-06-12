---
title: "Package manager that fails if file exists?"
date: 2011-01-11
forum: The Cafe
---

### Post by nerdopolis on 2011-01-11
Hi. 

this is a quick survey, does anyone know if any "Linux"  package managers out there fail if it tries to install a file that  already exists? 

it seems DPKG bombs out if a package tries to create a file that exists in another *package* but it does not fail if it tries to overwrite a file that exists but does not exist in any package


```

sudo touch /usr/bin/konsole
sudo <package-manager-install-cmd> konsole

```
is run

will any package manager fail to overwrite the file, and/or bomb out?

It seems to work with apt-get/dpkg...

Anyone have experience of what happens with this in other package managers?

Thanks.

---

### Post by juancarlospaco on 2011-01-11
> **nerdopolis said:**
> 
It seems to work with apt-get


No.

```
sudo apt-get install --reinstall konsole
```

---

### Post by nerdopolis on 2011-01-11
Did tou get a updates-alternitives error...

I admit I did not notice any errors with /usr/share, and I assumed binary files will act the same when I gave that example.

Seeing that a package manager is willing to fail on a file like that, that stops my search early

Thanks.

---

### Post by jeffathehutt on 2011-01-11
Arch's pacman will stop with an error if a file already exists (I tried with a random package):

```
[root@arch ~]# touch /usr/bin/apvlv
[root@arch ~]# pacman -S apvlv
resolving dependencies...
looking for inter-conflicts...

Targets (1): apvlv-0.1.0-1

Total Download Size:    0.19 MB
Total Installed Size:   0.36 MB

Proceed with installation? [Y/n] y
:: Retrieving packages from community...
 apvlv-0.1.0-1-i686      195.1K  102.2K/s 00:00:02 [#####################] 100%
checking package integrity...
(1/1) checking for file conflicts                  [#####################] 100%
error: failed to commit transaction (conflicting files)
apvlv: /usr/bin/apvlv exists in filesystem
Errors occurred, no packages were upgraded.
[root@arch ~]# 

```

---

### Post by nerdopolis on 2011-01-11
> **jeffathehutt said:**
> Arch's pacman will stop with an error if a file already exists (I tried with a random package):

```
[root@arch ~]# touch /usr/bin/apvlv
[root@arch ~]# pacman -S apvlv
resolving dependencies...
looking for inter-conflicts...

Targets (1): apvlv-0.1.0-1

Total Download Size:    0.19 MB
Total Installed Size:   0.36 MB

Proceed with installation? [Y/n] y
:: Retrieving packages from community...
 apvlv-0.1.0-1-i686      195.1K  102.2K/s 00:00:02 [#####################] 100%
checking package integrity...
(1/1) checking for file conflicts                  [#####################] 100%
error: failed to commit transaction (conflicting files)
apvlv: /usr/bin/apvlv exists in filesystem
Errors occurred, no packages were upgraded.
[root@arch ~]# 

```

Thanks. That seals it. Unionizing /usr/share is not the best option for temporarily importing apps, as its going to mess with package managers...

---

