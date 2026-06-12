---
title: "What is this whole thing with all these respository problems?"
date: 2005-11-14
forum: The Cafe
---

### Post by magomago on 2005-11-14
Just wondering....I've been hit with them, as well as many others and it is apparant if you check out the first page on the repository forum....

Outta curiosity what the heck happened!  Did a server crash and burn and they forget to load it up agan? ;)

---

### Post by pinoyskull on 2005-11-14
what are u talking about, havent encountered problems with repository at the moment

---

### Post by magomago on 2005-11-14
[QUOTE=pinoyskull]what are u talking about, havent encountered problems with repository at the moment[/QUOTE]
Really?  Now that is interesting...its been around two to three weeks since I've last been able to access the official repos.  All i get now is the PLF one, and the repo that was given to update to final OpenOffice 2

---

### Post by aysiu on 2005-11-14
[QUOTE=magomago]Really?  Now that is interesting...its been around two to three weeks since I've last been able to access the official repos.  All i get now is the PLF one, and the repo that was given to update to final OpenOffice 2[/QUOTE] Maybe your official repositories list isn't up-to-date. See the first link in my sig. I just ran an update, and it came out perfectly fine: ```
sudo apt-get update
Password:
Get:1 http://security.ubuntu.com breezy-security Release.gpg [189B]
Get:2 http://archive.ubuntu.com breezy Release.gpg [189B]
Get:3 http://archive.ubuntu.com breezy-updates Release.gpg [189B]
Get:4 http://security.ubuntu.com breezy-security Release [19.6kB]
Get:5 http://archive.ubuntu.com breezy-backports Release.gpg [189B]
Hit http://archive.ubuntu.com breezy Release
Get:6 http://archive.ubuntu.com breezy-updates Release [19.6kB]
Get:7 http://archive.ubuntu.com breezy-backports Release [11.3kB]
Hit http://security.ubuntu.com breezy-security/main Packages
Hit http://archive.ubuntu.com breezy/main Packages
Hit http://archive.ubuntu.com breezy/restricted Packages
Hit http://archive.ubuntu.com breezy/main Sources
Hit http://archive.ubuntu.com breezy/restricted Sources
Hit http://archive.ubuntu.com breezy/universe Packages
Hit http://archive.ubuntu.com breezy/universe Sources
Hit http://archive.ubuntu.com breezy/multiverse Packages
Hit http://archive.ubuntu.com breezy/multiverse Sources
Hit http://security.ubuntu.com breezy-security/restricted Packages
Hit http://security.ubuntu.com breezy-security/main Sources
Hit http://security.ubuntu.com breezy-security/restricted Sources
Hit http://security.ubuntu.com breezy-security/universe Packages
Hit http://security.ubuntu.com breezy-security/universe Sources
Hit http://archive.ubuntu.com breezy-updates/main Packages
Hit http://archive.ubuntu.com breezy-updates/restricted Packages
Hit http://archive.ubuntu.com breezy-updates/main Sources
Hit http://archive.ubuntu.com breezy-updates/restricted Sources
Hit http://archive.ubuntu.com breezy-backports/main Packages
Hit http://archive.ubuntu.com breezy-backports/restricted Packages
Hit http://archive.ubuntu.com breezy-backports/universe Packages
Hit http://archive.ubuntu.com breezy-backports/multiverse Packages
Fetched 51.1kB in 2s (23.4kB/s)
Reading package lists... Done
```

---

### Post by Samuel on 2005-11-15
i had the gpg error problem, but backing up, deleting the file sources.list and restoring it from the backup fixed it, not sure why but it worked.........

i found the tip in a thread on these forums

---

### Post by pinoyskull on 2005-11-15
as evidence, here's mine

```

freedom:~$ sudo apt-get update
Get:1 http://security.ubuntu.com breezy-security Release.gpg [189B]
Get:2 http://archive.ubuntu.com breezy Release.gpg [189B]
Get:3 http://archive.ubuntu.com breezy-updates Release.gpg [189B]
Hit http://archive.ubuntu.com breezy Release   
Hit http://archive.ubuntu.com breezy-updates Release                
Hit http://security.ubuntu.com breezy-security Release
Hit http://archive.ubuntu.com breezy/main Packages
Hit http://archive.ubuntu.com breezy/restricted Packages
Hit http://archive.ubuntu.com breezy/main Sources
Hit http://security.ubuntu.com breezy-security/main Packages
Hit http://archive.ubuntu.com breezy/restricted Sources
Hit http://archive.ubuntu.com breezy/universe Packages
Hit http://archive.ubuntu.com breezy/universe Sources
Hit http://archive.ubuntu.com breezy/multiverse Packages
Hit http://archive.ubuntu.com breezy/multiverse Sources
Hit http://archive.ubuntu.com breezy-updates/main Packages
Hit http://archive.ubuntu.com breezy-updates/restricted Packages
Hit http://archive.ubuntu.com breezy-updates/main Sources
Hit http://security.ubuntu.com breezy-security/restricted Packages
Hit http://security.ubuntu.com breezy-security/main Sources
Hit http://security.ubuntu.com breezy-security/restricted Sources
Hit http://archive.ubuntu.com breezy-updates/restricted Sources
Hit http://security.ubuntu.com breezy-security/universe Packages
Hit http://security.ubuntu.com breezy-security/universe Sources
Fetched 3B in 3s (1B/s)  
Reading package lists... Done

```

---

