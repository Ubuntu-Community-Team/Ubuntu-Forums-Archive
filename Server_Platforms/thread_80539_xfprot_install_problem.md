---
title: "xfprot install problem"
date: 2005-10-22
forum: Server Platforms
---

### Post by HJThis on 2005-10-22
Hey,To all

I was trying to install both xfprot & f-prot the 
installing of f-prot was great no problem at all
but the xfprot is a no go.

when i ./configure

all is good but once i try to Make i get an error
about make not found or somthing like that
anyone have an idea of how to fix this please

oh yes i also get this error when i try to use
make install

Thank you

---

### Post by KingBahamut on 2005-10-22
ClamAV user here. 

but do this instead. 

apt-get install f-prot-installer

---

### Post by HJThis on 2005-10-22
Hello,KingBahamut

First thanks for the reply but this will install f-prot NO
if so i do have f-prot installed.

that gave me no problem at all the only
thing i can't seem to get installed is this xfprot

when i do

./configure  all is good but when i try

Make  this is when i get the error make not found
or somthing like that.

i also get the same error if i try using

Make install

help

Thank you

---

### Post by deimos on 2005-12-14
sudo apt-get install make

---

