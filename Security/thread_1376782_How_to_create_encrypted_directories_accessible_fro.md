---
title: "How to create encrypted directories accessible from logged in user?"
date: 2010-01-09
forum: Security
---

### Post by R4KFFE on 2010-01-09
This is the issue that has prevented me from moving to Ubuntu from Windows. Windows has a feature where you can encrypt a folder / file and it will behave transparently to the user once the user is logged in (meaning there is no need to enter any additional credentials).

It is important that at login the encrypted folder is accessible and that certain system processes can access said folder.

The reason being that apache will serve files from this folder (on my test machine). So, here is my question.... Can linux do the following:

1) Encrypt a folder that is only accessible to user accounts that have the encryption key associated with the account

2) Require no associated user account to enter in any additional credentials (tie it to the user account).

3) Allow other processes (such as apache) to also access the encrypted folder.

I believe last time I tried this (6 months ago)... I was able to get an encrypted folder associated with my login. However, apache and related programs could not access the folder.

---

