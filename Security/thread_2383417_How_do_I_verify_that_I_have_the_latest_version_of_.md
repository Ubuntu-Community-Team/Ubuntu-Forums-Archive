---
title: "How do I verify that I have the latest version of VLC + repository questions."
date: 2018-01-24
forum: Security
---

### Post by jedi123 on 2018-01-24
Hello folks, I have a question about VLC.  When I downloaded Ubuntu , I  wrote ```
** sudo apt-get install VLC **
``` to get VLC.   

Quesitons: 

1. Since I did not add  another repository through terminal, does this mean that VLC's repository is linked to teh UBuntu one? 

2. If I did not add the VLC repository for nightly builds or newest builds , does this mean```
  sudo apt-get update
```  or ```
 sudo apt-get upgrade  
```will automatically get me the newest  VLC?

Thanks.

---

### Post by cruzer001 on 2018-01-24
> Since I did not add another repository through terminal, does this mean that VLC's repository is linked to teh UBuntu one? 

To find out what version(s) you have in the repository:

```
apt policy vlc
```

---

### Post by ajgreeny on 2018-01-24
The repository versions will not be the most up to date version available, but the version that is tested and known to work with whatever version of Ubuntu you are using.

If you wish to push the boundaries and try a much newer version (which may be unstable), have a look at the PPA at [https://launchpad.net/~videolan/+archive/ubuntu/master-daily](https://launchpad.net/~videolan/+archive/ubuntu/master-daily) but be prepared for things to go wrong; they may not but you will need to try it yourself.

---

