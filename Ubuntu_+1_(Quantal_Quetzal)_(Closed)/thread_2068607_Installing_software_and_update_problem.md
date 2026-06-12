---
title: "Installing software and update problem"
date: 2012-10-09
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Skipy149 on 2012-10-09
Hello, I have using windows until now, so i'm totaly Linux beginner :)
I have downloaded Ubuntu 12.10 beta and successfully installed it on my pc. 
Problem is because I cant install any software from software center  and do update, it shows this message:

> Failed to download repository information

Check your Internet connection.

Details

W:GPG  error: [http://packages.medibuntu.org](http://packages.medibuntu.org) quantal InRelease: The following  signatures couldn't be verified because the public key is not available:  NO_PUBKEY 2EBC26B60C5A2783, W:Failed to fetch  bzip2:/var/lib/apt/lists/partial/rs.archive.ubuntu.com_ubuntu_dists_quantal_main_source_Sources   Hash Sum mismatch
, W:Failed to fetch  bzip2:/var/lib/apt/lists/partial/rs.archive.ubuntu.com_ubuntu_dists_quantal_universe_source_Sources   Hash Sum mismatch
, W:Failed to fetch  bzip2:/var/lib/apt/lists/partial/rs.archive.ubuntu.com_ubuntu_dists_quantal_main_binary-i386_Packages   Hash Sum mismatch
, W:Failed to fetch  bzip2:/var/lib/apt/lists/partial/rs.archive.ubuntu.com_ubuntu_dists_quantal_universe_binary-i386_Packages   Hash Sum mismatch
, E:Some index files failed to download. They have been ignored, or old ones used instead.It's problem whit internet connection, it work fine with wireless connection. 
Can somebody help me? 
Thanks in advance :)

---

### Post by sandyd on 2012-10-09
Can you post the output of
```

cat /etc/apt/sources.list
```
please?

Thanks!

---

### Post by papibe on 2012-10-09
> **Skipy149 said:**
> I have downloaded Ubuntu 12.10 beta and ...

Moved to **Ubuntu +1 (Quantal Quetzal)**.

---

