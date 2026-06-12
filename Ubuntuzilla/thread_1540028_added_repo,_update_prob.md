---
title: "added repo, update prob"
date: 2010-07-27
forum: Ubuntuzilla
---

### Post by shane2peru on 2010-07-27
Ok, I followed the wiki guide.  When I added the repo with the echo line there all was fine.  Next I added the key as specified:```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C1289A29
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com C1289A29
gpg: requesting key C1289A29 from hkp server keyserver.ubuntu.com
gpg: key C1289A29: public key "Daniel Folkinshteyn (Ubuntuzilla signing key) <email was here>" imported
gpg: Total number processed: 1
gpg:               imported: 1

``` (I removed the email to keep bots from eating it. :)) Adding the key was fine, update gave me this error:```
Hit http://archive.ubuntu.com lucid-updates/multiverse Sources     
Get:2 http://downloads.sourceforge.net all Release [961B]    
Fetched 198B in 3s (62B/s)    
W: Failed to fetch http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/dists/all/Release  Unable to find expected entry  main/binary-amd64/Packages in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.

```
Trying to install Thunderbird as specified in the wiki, it didn't find the package.  

Shane

**EDIT:**  As you can see I'm on 64bit install of Ubuntu latest release.

---

### Post by nanotube on 2010-07-27
Hi
ubuntuzilla only has 32bit binaries (since that's the only thing mozilla releases)
so... you'll have to look elsewhere for the latest thunderbird...
possibly the ubuntu-mozilla-daily ppa?

---

### Post by shane2peru on 2010-07-27
Right, but that is all that is installed via the repos the normal way too, so I wouldn't think that would be a problem.  Perhaps the way ppa's work it apparently seems to be a problem I guess I will just install it manually from the official Mozilla site.  Thanks anyway.

Shane

---

### Post by nanotube on 2010-07-28
> **shane2peru said:**
> Right, but that is all that is installed via the repos the normal way too, so I wouldn't think that would be a problem.  Perhaps the way ppa's work it apparently seems to be a problem I guess I will just install it manually from the official Mozilla site.  Thanks anyway.

Shane

the packages are marked for the i386 architecture... because they are 32bit. :) apt is smart enough to barf on that.

yes, you can try a manual download/extract from mozilla.

---

