---
title: "Clarifying sources.list entries"
date: 2006-08-25
forum: Repositories &amp; Backports
---

### Post by TLE on 2006-08-25
Ok even though there are quite a lot of posts about the sources.list file, there are still a few things I'm not sure about. First of all is this line:
```
deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
```
the exact equivalent of these four lines?
```
deb http://archive.ubuntu.com/ubuntu dapper main
deb http://archive.ubuntu.com/ubuntu dapper restricted
deb http://archive.ubuntu.com/ubuntu dapper universe
deb http://archive.ubuntu.com/ubuntu dapper multiverse
```
or are there some sort of difference due to the syntax ?

Second. the local repositories. Are they exact mirrors and if so how much is available from them.
```
# Dapper Final Release Repository
deb http://archive.ubuntu.com/ubuntu dapper main
deb-src http://archive.ubuntu.com/ubuntu dapper main

deb http://archive.ubuntu.com/ubuntu dapper restricted
deb-src http://archive.ubuntu.com/ubuntu dapper restricted

deb http://archive.ubuntu.com/ubuntu dapper universe
deb-src http://archive.ubuntu.com/ubuntu dapper universe

deb http://archive.ubuntu.com/ubuntu dapper multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper multiverse

# Dapper Security Updates
deb http://archive.ubuntu.com/ubuntu dapper-security main
deb-src http://archive.ubuntu.com/ubuntu dapper-security main

deb http://archive.ubuntu.com/ubuntu dapper-security restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-security restricted

deb http://archive.ubuntu.com/ubuntu dapper-security universe
deb-src http://archive.ubuntu.com/ubuntu dapper-security universe

deb http://archive.ubuntu.com/ubuntu dapper-security multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-security multiverse

# Dapper Bugfix Updates
deb http://archive.ubuntu.com/ubuntu dapper-updates main
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main

deb http://archive.ubuntu.com/ubuntu dapper-updates restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-updates restricted

deb http://archive.ubuntu.com/ubuntu dapper-updates universe
deb-src http://archive.ubuntu.com/ubuntu dapper-updates universe

deb http://archive.ubuntu.com/ubuntu dapper-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates multiverse

```How many of the reposotories above are available from local repos ?

---

### Post by az on 2006-08-25
No difference and you have no local repos.

The local repos could probably be a few minutes late in getting new packages.

---

### Post by TLE on 2006-08-25
> **azz said:**
> No difference
Ok..

> **azz said:**
> and you have no local repos.
I know. It is because I wanted to enable them, I was just wandering if all of the repositories was available from the local sources.

---

### Post by az on 2006-08-25
> **TLE said:**
> I know. It is because I wanted to enable them, I was just wandering if all of the repositories was available from the local sources.

Oh!  Sorry.

All of them except the Dapper-Commercial one.  There is only one place for Dapper-Comercial.

---

### Post by TLE on 2006-08-25
Thank you

---

