---
title: "dont work in hoary local reposties"
date: 2005-04-11
forum: Repositories &amp; Backports
---

### Post by insulae on 2005-04-11
(my english is bad)

in warty i made a local repostiroies with my downloaded ubuntu debs with:

1- :dpkg-scanpackages  debs /dev/null > Packages
2- :gzip -c Packages > Packages.gz
3- then i modified the /etc/apt/source.lst with a new line: file: /files/debs/ ./
4- sudo apt-get update

with this commands i have a work repositorie in warty but in hoary this work but synaptic dont wont install my debs from my local repositorie because dont have gpg "autentification", synaptic take debs from [http://archive.ubuntu.org](http://archive.ubuntu.org) and i dont wont this, my connection is dialup, so i want create a repositorie with my downloaded files for another machines but i dont know how to do that in hoary.

please help me!!!

---

