---
title: "Can't fetch Release file from my repository"
date: 2012-05-31
forum: Ubuntu Dev Link Forum
---

### Post by ColinMcQueen on 2012-05-31
I created a repository on one VM and the other one VM is receiving this error when updating the package list:

```
Ign http://10.31.31.89 ./ InRelease
Get:1 http://10.31.31.89 ./ Release.gpg [836 B]
Hit http://10.31.31.89 ./ Release
Fetched 836 B in 0s (10.7 kB/s)
W: Failed to fetch http://10.31.31.89/shiftRepo/dists/stable/main/binary/./Release  

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

When I click on the link it shows me the contents of the Release file in the browser.

Also my /etc/apt/sources.list is

```
deb http://10.31.31.89/shiftRepo/dists/stable/main/binary ./
```

Everything else is commented out because I only want to update my repository.

Also, on the VM with the repository I have the Release, index, and Release.gpg file in the same directory, which is binary.

---

### Post by ColinMcQueen on 2012-05-31
I figured it out. I used apt-ftparchive to create the index file and release file. Then I used these two commands:

```
gpg --clearsign -o InRelease Release
gpg -abs -o Release.gpg Release
```

---

