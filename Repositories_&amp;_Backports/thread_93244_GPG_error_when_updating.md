---
title: "GPG error when updating"
date: 2005-11-21
forum: Repositories &amp; Backports
---

### Post by PSH on 2005-11-21
Have been getting the following error on both my Ubuntu PCs over the last few days:

"W: GPG error: [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) breezy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>"

Know what the problem is? 

Thanks

---

### Post by linbetwin on 2005-11-21
[quote=PSH]Have been getting the following error on both my Ubuntu PCs over the last few days:
 
"W: GPG error: [http://nz.archive.ubuntu.com]("http://nz.archive.ubuntu.com") breezy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>"
 
Know what the problem is? 
 
Thanks[/quote]
 
Don't let that warning stop you, It's harmless.

---

### Post by aysiu on 2005-11-21
It's not harmless--it means you won't be able to download from that repository any more because the signature isn't valid.

Look at the first link in my sig.

---

### Post by matthew on 2005-11-21
This has been a pretty common problem recently. In the future I would like to urge you to use the forums' search function as you may be asking a question that has already been answered and you will find the information you want a bit faster. In the meanwhile, let me refer you to this thread which covers your problem.

[http://ubuntuforums.org/showthread.php?t=36529](http://ubuntuforums.org/showthread.php?t=36529)

---

### Post by PSH on 2005-11-22
I have searched other threads relating to this problem and have not yet found a viable solution.

The error does not seem to be preventing updates to be identified, nor installed, but not sure.

Any further ideas?

Thanks

---

### Post by aysiu on 2005-11-22
[QUOTE=PSH]I have searched other threads relating to this problem and have not yet found a viable solution.[/QUOTE] Try looking at post #3 in this thread.

---

### Post by PSH on 2005-11-22
[QUOTE=aysiu]Try looking at post #3 in this thread.[/QUOTE]

Of course I did (thanks for the detail). ..... and tried your footnote for when the main suggestion doesn't work. It's quite perplexing.

Do you think the problem is update server based or spontaneously happening on the user's Ubuntu PCs?

---

### Post by aysiu on 2005-11-22
[QUOTE=PSH]Of course I did (thanks for the detail). ..... and tried your footnote for when the main suggestion doesn't work. It's quite perplexing.

Do you think the problem is update server based or spontaneously happening on the user's Ubuntu PCs?[/QUOTE] It's not the server, because I just did this (literally seconds ago): ```
sudo apt-get update
Password:
Get:1 http://security.ubuntu.com breezy-security Release.gpg [189B]
Get:2 http://archive.ubuntu.com breezy Release.gpg [189B]
Get:3 http://archive.ubuntu.com breezy-updates Release.gpg [189B]
Hit http://security.ubuntu.com breezy-security Release
Get:4 http://archive.ubuntu.com breezy-backports Release.gpg [189B]
Hit http://archive.ubuntu.com breezy Release
Hit http://security.ubuntu.com breezy-security/main Packages
Hit http://archive.ubuntu.com breezy-updates Release
Hit http://security.ubuntu.com breezy-security/restricted Packages
Hit http://security.ubuntu.com breezy-security/main Sources
Hit http://archive.ubuntu.com breezy-backports Release
Hit http://archive.ubuntu.com breezy/main Packages
Hit http://archive.ubuntu.com breezy/restricted Packages
Hit http://archive.ubuntu.com breezy/main Sources
Hit http://archive.ubuntu.com breezy/restricted Sources
Hit http://archive.ubuntu.com breezy/universe Packages
Hit http://archive.ubuntu.com breezy/universe Sources
Hit http://archive.ubuntu.com breezy/multiverse Packages
Hit http://archive.ubuntu.com breezy/multiverse Sources
Hit http://security.ubuntu.com breezy-security/restricted Sources
Hit http://security.ubuntu.com breezy-security/universe Packages
Hit http://security.ubuntu.com breezy-security/universe Sources
Hit http://archive.ubuntu.com breezy-updates/main Packages
Hit http://archive.ubuntu.com breezy-updates/restricted Packages
Hit http://archive.ubuntu.com breezy-updates/main Sources
Hit http://archive.ubuntu.com breezy-updates/restricted Sources
Hit http://archive.ubuntu.com breezy-backports/main Packages
Hit http://archive.ubuntu.com breezy-backports/restricted Packages
Hit http://archive.ubuntu.com breezy-backports/universe Packages
Hit http://archive.ubuntu.com breezy-backports/multiverse Packages
Fetched 4B in 1s (3B/s)
Reading package lists... Done
```

---

