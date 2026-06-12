---
title: "Problem with Feisty Repository??"
date: 2007-05-09
forum: Repositories &amp; Backports
---

### Post by utUtu on 2007-05-09
I don't see any one having this problem here but I'm getting some gzip error

```
Get:8 http://us.archive.ubuntu.com feisty/universe Sources [1523kB]
99% [8 Sources gzip 0]            
gzip: stdin: not in gzip format
Err http://us.archive.ubuntu.com feisty/universe Sources
  Sub-process gzip returned an error code (1)
Fetched 2320B in 1s (2029B/s)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
```

Any ideas??  Appreciate any help.

---

### Post by idzeeboo on 2007-11-08
I get the same when attempting to upgrade to Ubuntu 7.10

"Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz) Sub-process gzip returned an error code (1)"

:confused:

---

### Post by Seisen on 2007-11-09
Comment out the line that is producing the error, reload your source list, and then uncomment that line and it shouldn't produce the error.

---

### Post by natebenn on 2007-12-15
Did anybody get it working? I am having the same problem and as a total noob I can hardly decipher the meaning of the last post. :)

---

### Post by Seisen on 2007-12-16
> **natebenn said:**
> Did anybody get it working? I am having the same problem and as a total noob I can hardly decipher the meaning of the last post. :)


Can you post your source list?

```
cat /etc/apt/sources.list
```

---

### Post by cjluck on 2008-12-09
nwc7@corvette:~$ cat /etc/apt/sources.list
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted universe

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main restricted universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main restricted universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security main restricted universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security main restricted universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security multiverse

---

### Post by nmb3000 on 2008-12-09
If you go look at the repository you're pulling from at [http://archive.ubuntu.com/ubuntu/dists/](http://archive.ubuntu.com/ubuntu/dists/) you will see that the feisty distribution has been removed.  This probably means the error you're getting is a 404 because the directory wasn't found on that server.

I don't know if the repository was removed because Feisty isn't supported anymore or if it was some kind of mistake.  Either way it's been missing for over a week now.

---

### Post by vermeer on 2008-12-09
I also have the same problem. My ubuntu feisty becomes unusable on several desktop computers in my company, but we cannot updgrade to hardy now.

Is there any solution to keep being able to update feisty?

Do anybody confirm the reason why the feisty directory has been removed from [http://archive.ubuntu.com/ubuntu/dists/](http://archive.ubuntu.com/ubuntu/dists/) ? is it a bug, or just it is not supported anymore? Removing the directory seems strange to me. They could just leave it as is, even if unsupported.

---

### Post by stromgren on 2008-12-10
I have the same problem. I'm not able to install new packages on a production server. Is there any solution to this problem?

---

### Post by xfred on 2008-12-10
Same problem on my work computer.  Is this just a glitch, or has this branch been terminated for good and I have to do a complete reinstall just to add some packages?

EDIT: looks like I missed the use by date given elsewhere :(.  Oh well, reinstallation here we come.

---

### Post by kostkon on 2008-12-10
Ubuntu 7.04 (Feisty Fawn) reached its end-of-life, as expected. Non-LTS versions get 18 months of support. It was officially announced [here]("http://www.ubuntu.com/news/ubuntu-7.04-end-of-life").

But the repos were just moved. Check [my post]("http://ubuntuforums.org/showpost.php?p=6319924&postcount=4") for a solution.

---

### Post by stromgren on 2008-12-12
Thanks!

---

