---
title: "Ubuntu server 20.04 cant update"
date: 2020-06-24
forum: Server Platforms
---

### Post by deepakdeshp on 2020-06-24
Hello,
I am not able to update server 20.04 64 bits running as a VM. Please advise . The error 

```
sudo apt update[sudo] password for uma: 
Get:1 http://archive.ubuntu.com/ubuntu focal InRelease [250 B]           
Get:2 http://security.ubuntu.com/ubuntu focal-security InRelease [250 B] 
Err:2 http://security.ubuntu.com/ubuntu focal-security InRelease         
  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
Err:1 http://archive.ubuntu.com/ubuntu focal InRelease      
  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
Get:3 http://archive.ubuntu.com/ubuntu focal-updates InRelease [250 B]
Err:3 http://archive.ubuntu.com/ubuntu focal-updates InRelease
  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
Reading package lists... Done
N: See apt-secure(8) manpage for repository creation and user configuration details.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
E: The repository 'http://security.ubuntu.com/ubuntu focal-security InRelease' is no longer signed.
E: Failed to fetch http://security.ubuntu.com/ubuntu/dists/focal-security/InRelease  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
E: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/focal/InRelease  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
E: The repository 'http://archive.ubuntu.com/ubuntu focal InRelease' is no longer signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/focal-updates/InRelease  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
E: The repository 'http://archive.ubuntu.com/ubuntu focal-updates InRelease' is no longer signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.



```

---

### Post by LHammonds on 2020-06-24
You did not say if you looked elsewhere for a solution.  Have you tried these which were results from a web search with your specific error:

[sudo apt update always giving Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?](https://askubuntu.com/questions/899009/sudo-apt-update-always-giving-clearsigned-file-isnt-valid-got-nosplit-does)
[[apt error] Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)](https://www.reddit.com/r/trisquel/comments/d80yaz/apt_error_clearsigned_file_isnt_valid_got_nosplit/)
[Ubuntu &#8211; Sudo apt update always giving Clearsigned file isn&#8217;t valid, got &#8216;NOSPLIT&#8217; (does the network require authentication?)](https://itectec.com/ubuntu/ubuntu-sudo-apt-update-always-giving-clearsigned-file-isnt-valid-got-nosplit-does-the-network-require-authentication/)

LHammonds

---

### Post by deepakdeshp on 2020-06-28
It somehow corrected itself. One more of the mysteries, I was able to update and upgrade without any problems,

Thanks for the answer though.

---

### Post by deepakdeshp on 2020-06-30
The problem re-appeared today.

---

### Post by deepakdeshp on 2020-06-30
> **LHammonds said:**
> You did not say if you looked elsewhere for a solution.  Have you tried these which were results from a web search with your specific error:

[sudo apt update always giving Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?]("https://askubuntu.com/questions/899009/sudo-apt-update-always-giving-clearsigned-file-isnt-valid-got-nosplit-does")
[[apt error] Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)]("https://www.reddit.com/r/trisquel/comments/d80yaz/apt_error_clearsigned_file_isnt_valid_got_nosplit/")
[Ubuntu – Sudo apt update always giving Clearsigned file isn’t valid, got ‘NOSPLIT’ (does the network require authentication?)]("https://itectec.com/ubuntu/ubuntu-sudo-apt-update-always-giving-clearsigned-file-isnt-valid-got-nosplit-does-the-network-require-authentication/")

LHammonds
All the links above were not applicable to me.

---

