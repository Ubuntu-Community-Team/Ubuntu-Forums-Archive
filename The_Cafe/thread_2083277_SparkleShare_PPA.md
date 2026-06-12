---
title: "SparkleShare PPA"
date: 2012-11-12
forum: The Cafe
---

### Post by sandyd on 2012-11-12
I found that the version in the repos lagged behind a few versions, so I created a PPA for it.

[s][https://launchpad.net/~sandyd/+archive/sparkleshare](https://launchpad.net/~sandyd/+archive/sparkleshare)[/s]
**Updated** [https://launchpad.net/~pribosek-jan/+archive/sparkleshare](https://launchpad.net/~pribosek-jan/+archive/sparkleshare)

**Setup Instructions**

On Server (replacing PROJECT_NAME with the name of your project)
```

sudo curl https://raw.github.com/hbons/Dazzle/master/dazzle.sh --output /usr/bin/dazzle && chmod +x /usr/bin/dazzle
sudo dazzle setup
sudo dazzle create PROJECT_NAME

```
Copy down the output (Server address and path) for use when setting up the clients later on

On Client (PPA Repository maintained by GreatDanton)
```

sudo apt-add-repository ppa:pribosek-jan/sparkleshare
sudo apt-get update
sudo apt-get install sparkleshare

```
Now, setup sparkleshare on each of your clients. You will recieve an ssh key for each.

On the server, run the following and enter the entire SSH key
```

sudo dazzle link
```

NOTE: there are no guarantees that this actually works perfectly - might take a few patches to get it running perfectly

---

### Post by sandyd on 2012-11-14
bumpity bump bump

---

### Post by juancarlospaco on 2012-11-14
Cool !, im sharing this, very interesting!

---

### Post by MadCow108 on 2012-11-15
please follow the standard versioning rules or you will break upgrade paths in respect to backports
0.9.7-0~ppa1+quantal0 instead of 0.9.7-quantal0

that is so an official backport (0.9.7-1~u12.10) can superseed it
see dpkg --compare-versions

---

### Post by sandyd on 2012-11-15
> **MadCow108 said:**
> please follow the standard versioning rules or you will break upgrade paths in respect to backports
0.9.7-0~ppa1+quantal0 instead of 0.9.7-quantal0

that is so an official backport (0.9.7-1~u12.10) can superseed it
see dpkg --compare-versions

Alright - Im sending in the changes now.
Should finish building in a while

---

