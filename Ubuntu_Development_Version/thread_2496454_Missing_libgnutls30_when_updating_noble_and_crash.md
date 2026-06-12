---
title: "Missing libgnutls30 when updating noble and crash"
date: 2024-03-28
forum: Ubuntu Development Version
---

### Post by csmth on 2024-03-28
I tried to update my 24.04 kubuntu and crashed. I can reach a login screen but kubuntu-desktop is gone. My target is to recover the kubuntu-desktop and try to avoid complete reinstall of kubuntu. On recovery mode I tried to recover the desktop by 'apt update' and 'apt --fix-broken install'  but there is an error message about missing libgnutls30. That missing package make http and other internet access fails. I try to download libgnutls30 at noble repos but none of them is available:

[https://packages.ubuntu.com/noble/amd64/libgnutls30/download](https://packages.ubuntu.com/noble/amd64/libgnutls30/download)

Please verify whether the missing package is normal or not.

Update: I realize some source is good for unload, for example from fr.archive.ubuntu.com/ubuntu. But I believe I did tried the france archive before I write this thread.

---

### Post by MAFoElffen on 2024-03-31
[COLOR=#ff0000]<<This thread should be moved to the "Ubuntu Development Version" Section.>>[/COLOR] 

^^^ REASON: Noble is still beta = not due for release for 2-3 weeks. The repo freeze is in about a week. We need to see these problems and have them reported so they can get fixed before the release...

Please report this a bug report at "LaunchPad.Net" . That is the fastest way to get this fixed in the code before the release.

---

### Post by MAFoElffen on 2024-03-31
I don't see that package in the Noble Repo for amd64. I see it for other arches, but not for amd64.

What is the exact error you are getting?

---

### Post by ajgreeny on 2024-04-01
Thread moved to **Ubuntu Development version** where all discussion of 24.04 takes place.

---

