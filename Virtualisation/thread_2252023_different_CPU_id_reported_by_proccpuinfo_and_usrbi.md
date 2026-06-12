---
title: "different CPU id reported by /proc/cpuinfo and /usr/bin/cpuid?"
date: 2014-11-08
forum: Virtualisation
---

### Post by dankegel on 2014-11-08
A unit test of our cpuid-checking function started failing when it was moved to a new vmware server.
The test essentially just compares the output of two commands

cat /proc/cpuinfo | grep model.name | sort -u
cpuid | grep brand

On the old host, this worked fine; both output 
Intel(R) Xeon(R) CPU           X5450  @ 3.00GHz

But on the new host, they output different strings:

$ cat /proc/cpuinfo | grep model.name | sort -u
model name	: Intel(R) Xeon(R) CPU           X5450  @ 3.00GHz
$ cpuid | grep brand
Extended brand string: "Intel(R) Xeon(R) CPU           E5410  @ 2.33GHz"

WTF.  Does VMware let admins configure different CPU strings for
the linux kernel and for userspace apps?  Or is there some other explanation?

---

