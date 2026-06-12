---
title: "Update Problem"
date: 2012-02-07
forum: The Cafe
---

### Post by kb9mnm on 2012-02-07
Hi All,
New user here, Dave, and when I go to update, I get this error:

W:Failed to fetch [http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

Ubuntu 11.10. Any ideas? 

Thanks,
Dave

---

### Post by Cavsfan on 2012-02-07
> **kb9mnm said:**
> Hi All,
New user here, Dave, and when I go to update, I get this error:

W:Failed to fetch [http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

Ubuntu 11.10. Any ideas? 

Thanks,
Dave

Just give is some time. It does that occasionally. It will OK in a little while.

---

### Post by Cavsfan on 2012-02-07
Do you use 
```
sudo apt-get update 
sudo apt-get upgrade
```To get your updates?

I believe that is the best way as it will tell you if anything is being help back like a kernel.

Then this is how to install the kernel if it is held back after the update:

```
sudo apt-get update 
sudo apt-get dist-upgrade
```

---

### Post by snowpine on 2012-02-07
These are unofficial/unsupported software sources that you added for some reason. I recommend simply going into Software Sources and uncheck the troublesome repositories. :)

---

### Post by oldfred on 2012-02-07
I thought it was a license thing. Plus the open java works well for most.

Java - Sun/Oracle non-free use std openjdk-6-jdk
[FONT=Arial]
[/FONT]Oracle (Sun) Java: removed from all repositories
[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

---

### Post by wojox on 2012-02-07
And there is no build for Orinic [Index of /sun-java-community-team/sun-java6/ubuntu/dists]("http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/dists/")

---

### Post by emiller12345 on 2012-02-07
If you use your browser to look at 
[http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/dists](http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/dists)
there are directories for hardy, lucid, and maverick, but not oneiric
they might not have one for that version of ubuntu__

---

### Post by Pjotr123 on 2012-02-07
Apply this easy solution (works for sure, and can be trusted): [http://www.duinsoft.nl/packages.php?t=en](http://www.duinsoft.nl/packages.php?t=en)

Or do it manually (almost as easy):
[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

... and your Java will be allright again. :)

---

