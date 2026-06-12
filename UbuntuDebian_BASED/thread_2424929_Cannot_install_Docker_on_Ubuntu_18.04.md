---
title: "Cannot install Docker on Ubuntu 18.04"
date: 2019-08-17
forum: Ubuntu/Debian BASED
---

### Post by gab12121 on 2019-08-17
Hello,
I am having a problem with installing Docker. When I need to add the PPA with that command ```
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
``` I get this error:

```
E: The repository 'https://download.docker.com/linux/ubuntu juno Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

```

It may be because I am using Elementary OS, a distribution of Ubuntu which release name is Juno, it may try to get a release for the ubuntu juno version which does not exist and thus creates an error, hence the ***juno Release' does not have a Release file.*** part.

NOTE: I also get this error
```
Err:23 https://download.docker.com/linux/ubuntu/dists/bionic/Release bionic Release
  404  Not Found [IP: 143.204.101.42 443]
```



Thank you for helping me

---

### Post by deadflowr on 2019-08-17
*Thread moved to **Ubuntu/Debian BASED***

---

### Post by norobro on 2019-08-17
Caveat: I know nothing about this distro so not responsible for any breakage ;)

According to the Elementary OS website the Juno release is based on Ubuntu 18.04 (bionic) so try changing your command to this:```
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu [COLOR=#ff0000]bionic[/COLOR] stable"
```

---

