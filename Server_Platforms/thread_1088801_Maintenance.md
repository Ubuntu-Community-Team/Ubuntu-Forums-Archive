---
title: "Maintenance"
date: 2009-03-06
forum: Server Platforms
---

### Post by measekite on 2009-03-06
**Point of Reference**:  :popcorn:

I know that the desktop edition of Ubuntu is replaced every 6 months and is maintained for 18 months with the version of the applications frozen at the time of release.

**My Question:**

I would like to know the same information about the server edition.

How long is it maintained for?  Changing server OS is a real pain
.
Are the versions of applications and utilities in the repository frozen at release?

Is there a new version every 6 months?

---

### Post by cdenley on 2009-03-06
[http://www.ubuntu.com/products/whatisubuntu/serveredition/benefits/lifecycle](http://www.ubuntu.com/products/whatisubuntu/serveredition/benefits/lifecycle)

The release cycle is the same for desktop and server, except LTS server releases are supported for 5 years.

---

### Post by measekite on 2009-03-06
> **cdenley said:**
> [http://www.ubuntu.com/products/whatisubuntu/serveredition/benefits/lifecycle](http://www.ubuntu.com/products/whatisubuntu/serveredition/benefits/lifecycle)

The release cycle is the same for desktop and server, except LTS server releases are supported for 5 years.

Correct me if I am wrong but if you install an LTS that was released 4 years ago then support stops in one year?

---

### Post by drubin on 2009-03-06
> **cdenley said:**
> [http://www.ubuntu.com/products/whatisubuntu/serveredition/benefits/lifecycle](http://www.ubuntu.com/products/whatisubuntu/serveredition/benefits/lifecycle)

The release cycle is the same for desktop and server, except LTS server releases are supported for 5 years.

> **measekite said:**
> Correct me if I am wrong but if you install an LTS that was released 4 years ago then support stops in one year?

The support is 5 years from the release date **not** the install date :) 

I am not 100% sure if this was a language issue or not just thought I would make it explicitly clear :)

---

### Post by Jekshadow on 2009-03-06
To update distro easily without losing files do this:

[quote=Ubuntu Guide]
Network Upgrade for Ubuntu Servers (Recommended)

Install update-manager-core if it is not already installed: 
```
sudo apt-get install update-manager-core
```

Edit /etc/update-manager/release-upgrades and set: 
```
Prompt=normal
```

Launch the upgrade tool: 
```
sudo do-release-upgrade
```
Follow the on-screen instructions.
[/quote]

It took officially 7 seconds (including page loads) to find that using google.

---

### Post by drubin on 2009-03-07
> **Jekshadow said:**
> It took officially 7 seconds (including page loads) to find that using google.

Not sure any one asked for help updating a distro.. and btw this isn't something you just do on live production servers! You generally wont just upgrade distributions because there is a new version it would take testing testing and lots more testing.

---

### Post by linux_tech on 2009-03-07
> **measekite said:**
> **Point of Reference**:  :popcorn:

I know that the desktop edition of Ubuntu is replaced every 6 months and is maintained for 18 months with the version of the applications frozen at the time of release.

**My Question:**

I would like to know the same information about the server edition.

How long is it maintained for?  Changing server OS is a real pain

Is there a new version every 6 months?
LTS or Long Term Support releases, occur every two years, and they are supported for five years on servers.

---

### Post by Dr Small on 2009-03-07
No matter how long the LTS server versions are supported, I moved to Debian since I can't afford bandwidth to upgrade. Running Debian stable suits me and occasionally I switch to testing to get a newer version of some software that doesn't have very many dependencies (so it won't break other things).

It really irked me when my Ubuntu 7.04 server couldn't install software because they dropped the repositories on it. So, oh well.

---

