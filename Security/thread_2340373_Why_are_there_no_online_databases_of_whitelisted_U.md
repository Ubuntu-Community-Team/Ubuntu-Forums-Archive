---
title: "Why are there no online databases of whitelisted Ubuntu binaries?"
date: 2016-10-18
forum: Security
---

### Post by hip13044b on 2016-10-18
The existing tools for searching for rootkits seem to require you to maintain your own brittle whitelist of acceptable binaries (tripwire, rkhunter, chkrootkit).

Why is there no online database of acceptable SHA256 hashes that I can use to compare the contents of my system to?

My definition of a whitelist is: the set of SHA256 hashes of every binary found in every release of Ubuntu.

My ideal rootkit searching experience would be like this (requiring no prior effort):

1. Insert a LIVE cd, called rkhunter++ or something like that. It would work on any Ubuntu installation.
2. Have it compute the SHA256 sums of all binaries in my system, cross-reference them with a online database.
3. Highlight any "mysterious" binaries.

The key advantage of this system over something like the existing rkhunter is that you don't have to maintain your own whitelist. Eg. with rkhunter, if you update your system legitimately, but then don't update the rkhunter whitelist, your next report tells you your system is full of rootkits.

---

### Post by HermanAB on 2016-10-18
Te checksums are on the system installation servers.  To get it all, you have to make your own mirror server.

---

### Post by hip13044b on 2016-10-18
Does it include hashes for PPA binaries?

---

