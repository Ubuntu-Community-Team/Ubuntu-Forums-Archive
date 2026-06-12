---
title: "Citadel won't run (libcurl.so.4: no version info available) Ubuntu"
date: 2009-05-12
forum: Server Platforms
---

### Post by etali on 2009-05-12
Hi all,

I'm trying to get Citadel to run on Intrepid, and I'm having problems.  I've tried both apt-get, and the Citadel Easy Install. 

The installer runs through, but has an error in the final stage, then says the install has finished, but Citadel won't start.


If I try to start it manually with /etc/init.d/citadel start, I get:

/usr/local/lib/libcurl.so.4: no version information available (required by
/usr/sbin/citserver)

I've updated all my packages, but it hasn't helped.

I'm using:

[http://ubuntu.citadel.org/ubuntu/](http://ubuntu.citadel.org/ubuntu/) intrepid main

As my source at the moment.

I've asked on the Citadel boards, but they haven't been able to help much, so I thought I'd ask here in case it's an Ubuntu specific issue.

Thanks in advance.

---

### Post by Luz77 on 2011-08-11
Maybe you still got the problem, maybe someone other searches a solution for his own problems:

I think you haven't installed the libcurl package.
to check if you got it:

```
curl-config --version
```or try this to look what files you got already:

```
ls /usr/lib/libcurl.so*
```maybe you need one of these packages:

```
sudo apt-cache search libcurl4 --names-only
```my solution (with another tool than citadel) was:

```
sudo apt-get install libcurl4-openssl-dev
```

---

### Post by juky_ae on 2011-11-18
the solution for me was to remove all the curl libraries and links from /usr/local/lib/

...they where left there from a previous manual installation.

This removal let the system use the right libraries in /usr/lib/i386-linux-gnu

Please note, that one is a debian system, but the Idea should be the same, try:

locate libcurl

to search for duplilcates...

and verify libcurl* pagaged file list

---

