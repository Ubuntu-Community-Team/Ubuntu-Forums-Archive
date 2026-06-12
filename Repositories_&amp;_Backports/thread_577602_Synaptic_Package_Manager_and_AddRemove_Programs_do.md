---
title: "Synaptic Package Manager and Add/Remove Programs do not update"
date: 2007-10-16
forum: Repositories &amp; Backports
---

### Post by Roobin on 2007-10-16
Well, as the title says, they don't update, even after running apt-get update, apt-get upgrade, clicking Reload.

Here is my sources.list
```

# Automatically generated sources.list
# http://www.ubuntu-nl.org/source-o-matic/
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -
#
# If you don't know what to do with this file, read
# https://help.ubuntu.com/community/Repositories/CommandLine

# Ubuntu supported packages
# GPG key: 437D05B5
deb http://gb.archive.ubuntu.com/ubuntu feisty main restricted 
deb http://gb.archive.ubuntu.com/ubuntu feisty-updates main restricted
deb http://security.ubuntu.com/ubuntu feisty-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb http://gb.archive.ubuntu.com/ubuntu feisty universe multiverse 
deb http://gb.archive.ubuntu.com/ubuntu feisty-updates universe multiverse
deb http://security.ubuntu.com/ubuntu feisty-security universe multiverse

# Medibuntu multimedia packages
# GPG key: 0C5A2783
deb http://medibuntu.sos-sts.com/repo/ feisty free non-free 
```

Here's what happens when I run apt-get update:

```
Get: 1 http://gb.archive.ubuntu.com feisty Release.gpg [191B]
Hit http://gb.archive.ubuntu.com feisty/main Translation-en_GB               
Get: 2 http://security.ubuntu.com feisty-security Release.gpg [191B]         
Ign http://security.ubuntu.com feisty-security/main Translation-en_GB
Ign http://gb.archive.ubuntu.com feisty/restricted Translation-en_GB 
Ign http://gb.archive.ubuntu.com feisty/universe Translation-en_GB   
Hit http://gb.archive.ubuntu.com feisty/multiverse Translation-en_GB
Get: 3 http://gb.archive.ubuntu.com feisty-updates Release.gpg [191B]
Ign http://gb.archive.ubuntu.com feisty-updates/main Translation-en_GB      
Ign http://gb.archive.ubuntu.com feisty-updates/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com feisty-updates/universe Translation-en_GB
Get: 4 http://medibuntu.sos-sts.com feisty Release.gpg [189B]
Ign http://medibuntu.sos-sts.com feisty/free Translation-en_GB
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_GB
Ign http://security.ubuntu.com feisty-security/universe Translation-en_GB
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_GB
Ign http://gb.archive.ubuntu.com feisty-updates/multiverse Translation-en_GB
Hit http://gb.archive.ubuntu.com feisty Release
Ign http://medibuntu.sos-sts.com feisty/non-free Translation-en_GB             
Hit http://medibuntu.sos-sts.com feisty Release                      
Hit http://gb.archive.ubuntu.com feisty-updates Release              
Hit http://security.ubuntu.com feisty-security Release             
Hit http://gb.archive.ubuntu.com feisty/main Packages               
Hit http://gb.archive.ubuntu.com feisty/restricted Packages          
Hit http://gb.archive.ubuntu.com feisty/universe Packages            
Hit http://gb.archive.ubuntu.com feisty/multiverse Packages          
Ign http://medibuntu.sos-sts.com feisty/free Packages                
Hit http://gb.archive.ubuntu.com feisty-updates/main Packages        
Hit http://security.ubuntu.com feisty-security/main Packages
Hit http://gb.archive.ubuntu.com feisty-updates/restricted Packages
Hit http://gb.archive.ubuntu.com feisty-updates/universe Packages
Hit http://gb.archive.ubuntu.com feisty-updates/multiverse Packages  
Ign http://medibuntu.sos-sts.com feisty/non-free Packages            
Hit http://security.ubuntu.com feisty-security/restricted Packages
Hit http://security.ubuntu.com feisty-security/universe Packages
Hit http://security.ubuntu.com feisty-security/multiverse Packages
Hit http://medibuntu.sos-sts.com feisty/free Packages
Hit http://medibuntu.sos-sts.com feisty/non-free Packages
Fetched 4B in 0s (4B/s)
Reading package lists... Done

```

Ok, so I guess what I'm asking here is:

1) Should I be concerned about the number of Ign in the above?
2) How do I update this properly - e.g. aMsn is listed as version 0.96, when I know the latest is 0.97

Thanks

---

### Post by ruibernardo on 2007-10-16
> **Roobin said:**
> 
1) Should I be concerned about the number of Ign in the above?
2) How do I update this properly - e.g. aMsn is listed as version 0.96, when I know the latest is 0.97


You have your repositories working well. I can't answer your first question, but I think the Ign are related to your locale (which are fine) but APT don't want to or can't update (some definition set by default to not do it?).

You are getting "get" and "hit" from all the repositories, so they are all working.

About question 2, amsn 0.96 is the latest available version in Feisty. In Gutsy, there is a 0.97 RC version available. It might become available in backports repositories of Feisty later.

Generally packages from universe and multiverse aren't upgraded after the release (Feisty was in April 2007), but when the next release is made, many packages are backported to previous releases, so maybe it will be available in Feisty soon.

More on this here: [https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

---

### Post by Ocxic on 2007-10-16
ign = ignored ,,, in other words, no updates are available it's normal

---

