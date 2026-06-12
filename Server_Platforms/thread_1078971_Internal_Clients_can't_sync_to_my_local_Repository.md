---
title: "Internal Clients can't sync to my local Repository"
date: 2009-02-23
forum: Server Platforms
---

### Post by shebangs on 2009-02-23
I'm hosting a single local apt-mirror for the Ubuntu Servers on my LAN.  To save bandwidth and downloads.

Everything was working, but recently clients started throwing the dreaded: ***W: Failed to fetch http://ubuntu.company.com/ubuntu/dists/hardy-updates/main/binary-i386/Packages.gz  Hash Sum mismatch*** error mid way through an apt-get update.

I have no proxies, and my ISP doesn't transparent cache (ADSL2 Business plan).
I've tried *[FONT="Courier New"]rm /var/lib/apt/lists/*[/FONT]* waiting 10 minutes then [FONT="Courier New"]*apt-get update*[/FONT] on a client and it still fails.

The only thing I am left to assume is somehow my local mirror is corrupted.  When I run apt-mirror, it returns 0 packages need to be downloaded, and 0 need to be cleaned.   launchpad also seems to think my chosen local public mirror is in Sync.

So here I am, I'm in the middle of downloading a fresh 30G (hardy) from a different mirror.  

[LIST=1]
[*]What options do I have? 
[*]What else should I try?
[*]How can I confirm the 'validity' of my local mirror?
[*]Is it possible to point 2 externals sources to my single local mirror?  Use my local ISP mirror for quick downloads, but run a confirmation health check by using an official mirror?
[/LIST]

If I point my clients to an official mirror it works fine.





Actual apt-get update output below:
```

root@client:~# apt-get update
Hit http://ubuntu.company.com hardy Release.gpg
Ign http://ubuntu.company.com hardy/main Translation-en_AU
Ign http://ubuntu.company.com hardy/restricted Translation-en_AU
Ign http://ubuntu.company.com hardy/universe Translation-en_AU
Ign http://ubuntu.company.com hardy/multiverse Translation-en_AU
Hit http://ubuntu.company.com hardy-updates Release.gpg
Ign http://ubuntu.company.com hardy-updates/main Translation-en_AU
Ign http://ubuntu.company.com hardy-updates/restricted Translation-en_AU
Ign http://ubuntu.company.com hardy-updates/universe Translation-en_AU
Ign http://ubuntu.company.com hardy-updates/multiverse Translation-en_AU
Hit http://ubuntu.company.com hardy-security Release.gpg
Ign http://ubuntu.company.com hardy-security/main Translation-en_AU
Ign http://ubuntu.company.com hardy-security/restricted Translation-en_AU
Ign http://ubuntu.company.com hardy-security/universe Translation-en_AU
Ign http://ubuntu.company.com hardy-security/multiverse Translation-en_AU
Hit http://ubuntu.company.com hardy Release
Hit http://ubuntu.company.com hardy-updates Release
Hit http://ubuntu.company.com hardy-security Release
Ign http://ubuntu.company.com hardy/main Packages
Ign http://ubuntu.company.com hardy/restricted Packages
Ign http://ubuntu.company.com hardy/universe Packages
Ign http://ubuntu.company.com hardy/multiverse Packages
Hit http://ubuntu.company.com hardy/main Packages
Hit http://ubuntu.company.com hardy/restricted Packages
Hit http://ubuntu.company.com hardy/universe Packages
Hit http://ubuntu.company.com hardy/multiverse Packages
Ign http://ubuntu.company.com hardy-updates/main Packages
Ign http://ubuntu.company.com hardy-updates/restricted Packages
Ign http://ubuntu.company.com hardy-updates/universe Packages
Ign http://ubuntu.company.com hardy-updates/multiverse Packages
Get:1 http://ubuntu.company.com hardy-updates/main Packages [546kB]
Hit http://ubuntu.company.com hardy-updates/restricted Packages
Hit http://ubuntu.company.com hardy-updates/universe Packages
Hit http://ubuntu.company.com hardy-updates/multiverse Packages
Ign http://ubuntu.company.com hardy-security/main Packages
Ign http://ubuntu.company.com hardy-security/restricted Packages
Ign http://ubuntu.company.com hardy-security/universe Packages
Ign http://ubuntu.company.com hardy-security/multiverse Packages
Hit http://ubuntu.company.com hardy-security/main Packages
Hit http://ubuntu.company.com hardy-security/restricted Packages
Hit http://ubuntu.company.com hardy-security/universe Packages
Hit http://ubuntu.company.com hardy-security/multiverse Packages
Fetched 1B in 0s (2B/s)                      
W: Failed to fetch http://ubuntu.company.com/ubuntu/dists/hardy-updates/main/binary-i386/Packages.gz  Hash Sum mismatch

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by maximevaillant on 2009-04-08
I have the same issue. Local server running apt-mirror that clients point to. Running "sudo aptitude update" returns no error.

Where you able to find a solution?

---

