---
title: "How to make your own Ubuntu Repository DVDs for Ubuntu 09.04"
date: 2015-07-18
forum: Ubuntu/Debian BASED
---

### Post by zmau1962 on 2015-07-18
Hello all,

I need to make your own Ubuntu Repository DVDs for _**Ubuntu 09.04**_

There is athread called "**[SIZE=5][COLOR=Gray]How to make your own Ubuntu Repository DVDs[/COLOR][/SIZE]**".
It looks very good and detailed.
So I was trying to follow that tutorial.
I failed, and I need some advice.
The step that fails is called "**03. The Big Download**"
It looks like the main issue is due to the fact that 09.04 has moved to another location [[COLOR=#0000ff]_[http://old-releases.ubuntu.com/ubuntu/dists](http://old-releases.ubuntu.com/ubuntu/dists)_[/COLOR]]("http://old-releases.ubuntu.com/ubuntu/dists/")  instead of [COLOR=#0000ff]_[http://archive.ubuntu.com/ubuntu/dists](http://archive.ubuntu.com/ubuntu/dists)_[/COLOR] because I am able to use the tutprioal to download 10.04 (which did not move yet).
So, I had fixed the command as suggested in the tutorial :
[INDENT]debmirror --nosource -m --passive --host/ --method=http --progress --dist=Jaunty,Jaunty-security,Jaunty-updates,Jaunty-backports, --section=main,restricted,universe,multiverse --arch=i386 ~/UbuntuRepos --ignore-release-gpg[/INDENT]
The result was :
[INDENT][  0%] Getting: dists/Jaunty/Release	 #** GET [http://old-releases.ubuntu.com/ubuntu//dists/Jaunty/Release](http://old-releases.ubuntu.com/ubuntu//dists/Jaunty/Release) ==> 404 Not Found
dists/Jaunty/Release failed 404 Not Found
[  0%] Getting: dists/Jaunty-security/Release	 #** GET [http://old-releases.ubuntu.com/ubuntu//dists/Jaunty-security/Release](http://old-releases.ubuntu.com/ubuntu//dists/Jaunty-security/Release) ==> 404 Not Found
dists/Jaunty-security/Release failed 404 Not Found
[  0%] Getting: dists/Jaunty-updates/Release	 #** GET [http://old-releases.ubuntu.com/ubuntu//dists/Jaunty-updates/Release](http://old-releases.ubuntu.com/ubuntu//dists/Jaunty-updates/Release) ==> 404 Not Found
dists/Jaunty-updates/Release failed 404 Not Found
[  0%] Getting: dists/Jaunty-backports/Release	 #** GET [http://old-releases.ubuntu.com/ubuntu//dists/Jaunty-backports/Release](http://old-releases.ubuntu.com/ubuntu//dists/Jaunty-backports/Release) ==> 404 Not Found
dists/Jaunty-backports/Release failed 404 Not Found


[/INDENT]
Any advice ???


**_There are some points that did not work :_**
The first command's result was "E: Unable to locate package libdigest-sha1-perl"
    So, I had fixed it to libdigest-sha-perl



Thanks

---

### Post by QIII on 2015-07-18
Ubuntu 9.04 is long past End Of Life (EOL) and is insecure.  10.04 is also EOL, so there is no point to upgrading to it.  There is no point in attempting to do what you propose.

The appropriate thing to do would be to do a fresh install a currently supported version:  12.04 LTS, 14.04 LTS or 15.04.

I would suggest 14.04 LTS since it is supported until 2019.

---

### Post by Skaperen on 2015-07-18
i recommend **14.04**.  if you are wanting to *avoid Unity*, there are _many ways_.  using 9.X is a bad/*insecure* way.  you cannot upgrade it to secure.

---

### Post by zmau1962 on 2015-07-18
Thanks,

Upgrading to 12.04 is not possible.
This has to do with an old project. I had tried that to begin with.
Moving to Newer Ubuntu causes many other changes (too many of them).

Any advice on how to achieve the original goal ?

Thanks
again

---

### Post by zmau1962 on 2015-07-18
Hi all,
I had solved the issue.
I wrote [http://old-releases.ubuntu.com/ubuntu/dists/Jaunty](http://old-releases.ubuntu.com/ubuntu/dists/Jaunty)  instaed of [http://old-releases.ubuntu.com/ubuntu/dists/jaunty](http://old-releases.ubuntu.com/ubuntu/dists/jaunty)   (J instead of j).

---

