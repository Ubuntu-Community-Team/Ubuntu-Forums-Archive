---
title: "Skypeforlinux - File has unexpected size (2248 != 2466)"
date: 2018-09-24
forum: Ubuntu/Debian BASED
---

### Post by valtam on 2018-09-24
System - Linux lite 4.0 (based of Ubuntu 18.04)

Issue:

Install skypeforlinux_8.30.0.50_amd64.deb from the Skype repo.

Then, running sudo apt-get update from the Terminal returns:

```
Get:1 https://repo.skype.com/deb stable InRelease [4,487 B]
Hit:2 http://nz.archive.ubuntu.com/ubuntu bionic InRelease                                                                                                                              
Hit:3 http://repo.linuxliteos.com/linuxlite diamond InRelease                                                                                                                   
Get:4 https://repo.skype.com/deb stable/main amd64 Packages [2,466 B]                                               
Err:4 https://repo.skype.com/deb stable/main amd64 Packages                                                               
  File has unexpected size (2248 != 2466). Mirror sync in progress? [IP: 23.222.100.28 443]
  Hashes of expected file:
   - Filesize:2466 [weak]
   - SHA512:79cb854cd725e4cdc99f0d6afa41ae61337ca04099e67380e3e5a6864120260968c209f50a8f9d08d75f121634895ec12f20483e7282ddfaa167355959889d86
   - SHA256:a0453e5885a2271269304b181a68bd5687ee6b6716d7290d096582f79f6277b6
   - SHA1:5fa6a73ff3b40fef39dc608ca06d424c95d8748e [weak]
   - MD5Sum:053d034b3a31b3c6b92e8d26b985e1ce [weak]
  Release file created at: Mon, 24 Sep 2018 06:36:19 +0000
Hit:5 http://nz.archive.ubuntu.com/ubuntu bionic-security InRelease                                                       
Hit:6 http://archive.canonical.com/ubuntu bionic InRelease                                    
Hit:7 http://nz.archive.ubuntu.com/ubuntu bionic-updates InRelease      
Hit:8 http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu bionic InRelease
Hit:9 http://nz.archive.ubuntu.com/ubuntu bionic-backports InRelease     
Hit:10 http://ppa.launchpad.net/teejee2008/ppa/ubuntu bionic InRelease        
Fetched 4,487 B in 2s (2,427 B/s)                  
Reading package lists... Done
E: Failed to fetch https://repo.skype.com/deb/dists/stable/main/binary-amd64/Packages.bz2  File has unexpected size (2248 != 2466). Mirror sync in progress? [IP: 23.222.100.28 443]
   Hashes of expected file:
    - Filesize:2466 [weak]
    - SHA512:79cb854cd725e4cdc99f0d6afa41ae61337ca04099e67380e3e5a6864120260968c209f50a8f9d08d75f121634895ec12f20483e7282ddfaa167355959889d86
    - SHA256:a0453e5885a2271269304b181a68bd5687ee6b6716d7290d096582f79f6277b6
    - SHA1:5fa6a73ff3b40fef39dc608ca06d424c95d8748e [weak]
    - MD5Sum:053d034b3a31b3c6b92e8d26b985e1ce [weak]
   Release file created at: Mon, 24 Sep 2018 06:36:19 +0000
E: Some index files failed to download. They have been ignored, or old ones used instead.
```

Uninstall Skypeforlinux, problem goes away.


Thank you in advance for any help.

---

### Post by gregory7 on 2018-09-24
I have the same problem and I installed skype through snap so i need to learn how to reinstall through that i suppose

---

### Post by lucawin on 2018-09-24
I had the same problem yesterday simply doing the usual 
```
sudo apt update
```
since I had already installed *skypeforlinux* a few months ago.
I temporarily solved by disabling that repository, but I hope they'll fix it soon (so that I can keep updating it).

---

### Post by 1clue on 2018-09-24
I have skype installed through the repo. Skype worked more or less this morning (I always have audio issues since the upgrade to 18.04) and I just upgraded now. Everything worked, but I had an especially difficult time getting my audio to work.

<rant>

Before Microsoft bought Skype, it was a much better app for all platforms, except Linux.

Shortly after Microsoft bought it, Skype improved dramatically on Linux and simultaneously it became trash on Windows. Imagine that.

Lately, coinciding exactly with my upgrade to Ubuntu 18.04, Skype has become extremely difficult on Linux, especially with the sound settings.

EVERY time I get on a voice call, my incoming sound is over-amplified and sounds clipped. I need to go to my system sound settings, choose a different sound card, then reselect my normal one before the sound becomes normal again. Most of the time my microphone just doesn't work until I twiddle the settings on that.

This time, it took a good 5 minutes with the skype test call before I got all the way through the call. The message was chopping off halfway through, and there was no section where it recorded audio, it just stopped the call. Then it took another 2 or 3 minutes to get my voice back on the test call.

If there were another app which did the same things as Skype I'd be all for it. I need:
[LIST=1]
[*]Group voice calling, where people don't have to be waiting for it.
[*]Desktop sharing to the group.
[*]Text messages to the group.
[/LIST]

</rant>

---

### Post by coffeecat on 2018-09-24
*Thread moved to **Ubuntu/Debian BASED**.*

---

