---
title: "Unable to apt-update Clearsigned file isn't valid, got 'NOSPLIT' (does the network re"
date: 2020-05-26
forum: Server Platforms
---

### Post by deepakdeshp on 2020-05-26
I am running Ubuntu server 20.04 64 bits. I cant ```
apt update
```. Please suggest. The error is

[HTML]sudo apt updateGet:1 http://archive.ubuntu.com/ubuntu focal InRelease [250 B]           Get:2 http://security.ubuntu.com/ubuntu focal-security InRelease [250 B] Err:1 http://archive.ubuntu.com/ubuntu focal InRelease        Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)Err:2 http://security.ubuntu.com/ubuntu focal-security InRelease                 Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)Get:3 http://archive.ubuntu.com/ubuntu focal-updates InRelease [250 B]         Err:3 http://archive.ubuntu.com/ubuntu focal-updates InRelease  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)Reading package lists... Done    N: See apt-secure(8) manpage for repository creation and user configuration details.N: Updating from such a repository can't be done securely, and is therefore disabled by default.E: The repository 'http://archive.ubuntu.com/ubuntu focal InRelease' is no longer signed.E: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/focal/InRelease  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)E: Failed to fetch http://security.ubuntu.com/ubuntu/dists/focal-security/InRelease  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)E: The repository 'http://security.ubuntu.com/ubuntu focal-security InRelease' is no longer signed.N: Updating from such a repository can't be done securely, and is therefore disabled by default.N: See apt-secure(8) manpage for repository creation and user configuration details.E: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/focal-updates/InRelease  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)E: The repository 'http://archive.ubuntu.com/ubuntu focal-updates InRelease' is no longer signed.N: Updating from such a repository can't be done securely, and is therefore disabled by default.N: See apt-secure(8) manpage for repository creation and user configuration details.
[/HTML]

---

