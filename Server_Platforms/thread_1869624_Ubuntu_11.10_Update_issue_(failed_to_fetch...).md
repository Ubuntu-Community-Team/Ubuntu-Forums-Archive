---
title: "Ubuntu 11.10 Update issue (failed to fetch...)"
date: 2011-10-26
forum: Server Platforms
---

### Post by Rihoj on 2011-10-26
Hello, I am running Ubuntu 11.10 Server, and am getting errors that I can not find the answers to. 

I have tried to use 
```
sudo apt-get update
```

But I always end up with it returning (after many hours) that it has failed to fetch the websites. there error is:

```
Fetched 425 kB in 16h 50min 43s (7 B/s)
W: GPG error: http://extras.ubuntu.cm natty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty/main/source/Sources 404 Not Found [IP: 91.189.92.183 80]
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty/universe/source/Sources 404 Not Found [IP: 91.189.92.183 80]
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty/main/binary-i386/Packages 404 Not Found [IP: 91.189.92.183 80]
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty/universe/binary-i386/Packages 404 Not Found [IP: 91.189.92.183 80]
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-updates/main/binary-i386/Packages 404 Not Found [IP: 91.189.92.183 80]
W: Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_natty-backports_universe_binary-i386_packages Hash Sum mismatch
E: Some index files failed to download. They have been ignored, or old ones used instead.

```

Yes I know it says natty, but that is because that is one of the "fixes" that I have found said to replace everything that said onric with natty in the sources list. I have been told to take off the "us." from them as well. I can not find anything on google telling me how to fix this. I can not get anything installed, because I can not update, and if i try to install anyways I get an error saying that the package can not be found. PLEASE HELP.

---

### Post by vasile002 on 2011-10-26
can you post the contents of your /etc/apt/source.list file?

---

### Post by Rihoj on 2011-10-26
Alright here it is....
i have to type it all out, because I can not get SSH to work atm.
but then when i went to post I lost it... So i am just leaving out all commented out lines.
```

deb http://us.archive.ubuntu.com/ubuntu/ natty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ natty main restricted

deb http://us.archive.ubuntu.com/ubuntu/ natty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates main restricted

deb http://us.archive.ubuntu.com/ubuntu/ natty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ natty universe
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates universe


deb http://us.archive.ubuntu.com/ubuntu/ natty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ natty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates multiverse

deb http://us.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu natty-security main restricted
deb-src http://security.ubuntu.com/ubuntu natty-security main restricted
deb http://security.ubuntu.com/ubuntu natty-security universe
deb-src http://security.ubuntu.com/ubuntu natty-security universe
deb http://security.ubuntu.com/ubuntu natty-security multiverse
deb-src http://security.ubuntu.com/ubuntu natty-security multiverse

deb http://download.webmin.com/download/repository sarge contrib
deb http://webmin.mirror.somersettechsolutions.co.uk/repository sarge contrib

```

---

### Post by vasile002 on 2011-10-27
I can't see anything wrong, it should work as usual. Did you try apt-get update again? Maybe there were some temporary problems with the mirrors you were using. Try changing the mirrors from us.archive... to simplu archive.ubuntu.com and see if that fixes

---

### Post by Rihoj on 2011-10-27
I have been trying for at least 4 days. I have already removed the us. prefix to the urls. I changed the oneiric to natty, and when it was oneiric i tried both with and without the us. on the urls. I have absolutly no clue what is going on. What gets me is I know it is not my internet connection because at the end I have the webmin urls and they download just fine, I just can't install webmin because i can't update the rest of my system.

---

### Post by Rihoj on 2011-10-28
I still have not figured this out, but I am giving up, and just installing the desktop version. I am going to assume it can still do what I want. So Thank you for the help.

---

### Post by blue3c on 2011-10-29
I am getting the same thing with desktop. So not cool. One more reason to get away from ubuntu and this unity fail. 

Failed to to fetch g:zip/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_oneiric_universe_sources_Sources Hash Sum mismatch

---

### Post by patryk_w on 2011-10-30
i would guess they are doing something with repos.
apt-get was hanging in my system with '[waining for headers]' for all night.
i've changed to uk. prefix and everything works just fine

---

