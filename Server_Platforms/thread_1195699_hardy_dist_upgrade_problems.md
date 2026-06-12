---
title: "hardy dist upgrade problems"
date: 2009-06-24
forum: Server Platforms
---

### Post by tinny on 2009-06-24
Hello

I am trying to upgrade my hardy server to a newer release (say Jaunty).

I am having trouble doing this. Here are the steps I have tried.

1. Edit /etc/update-manager/release-upgrades

```

Prompt=normal

```

2. Make sure the current install is fully up to date

```

sudo aptitude update
sudo aptitude upgrade
sudo aptitude dist-upgrade

```

3. Use the release upgrade tool to upgrade

```

sudo do-release-upgrade

```

This results in the following

```

Done downloading            

Checking package manager
Reading package lists: Doneintrepid-security/multiverse Packages: 98   
Reading state information: Done
Reading state information: Done
Reading state information: Done

Calculating the changes

Restoring original system state

Aborting
Reading package lists: Done
Reading state information: Done
Reading state information: Done
Reading state information: Done

```

I have no idea why this was aborted, can anyone shed some light on this problem?

Thanks

---

### Post by Bucky Ball on 2009-06-24
One question: why were you upgrading? 8.04 is the long term release, perfect for a server environment as it is most stable. Was the install broken?

---

### Post by tinny on 2009-06-24
> **Bucky Ball said:**
> One question: why were you upgrading? 8.04 is the long term release, perfect for a server environment as it is most stable. Was the install broken?

Yeah I understand LTS versions

This is just a home server that I use for my own personal development etc...

I am unhappy with the very old version of Bugzilla that ships with Hardy. Jaunty has version 3 of Bugzilla. I have a strong preference to use the Ubuntu repositories to install applications. I dont want to manually install Bugzilla 3. 

Id just like to upgrade my distro version

---

### Post by Bucky Ball on 2009-06-24
Got ya. If it is home system you can experiment a bit with, you'll be able to help test and nut out the bugs (even though it's an official release). :)

---

### Post by tinny on 2009-06-24
bump

---

