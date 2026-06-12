---
title: "Headless server woes"
date: 2012-04-17
forum: Server Platforms
---

### Post by cackles on 2012-04-17
Hi, I am tryig to use apt-get update, but when I do I gt lines of errors like this:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/source/Sources](http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/source/Sources)  404 Not Found [IP: 91.189.92.166 80]

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/source/Sources](http://gb.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/source/Sources)  404 Not Found

I had a look about but most solutions seem to be for the GUI version and when I try the solutions I get told I dont have 'x' command. So I dont know what to try next.

Also my server has stopped responding to its name, Azureus, PuTTY, now I can only access it via IP locally, though its webservers etc. still seem to be working fine. So I can access it by domain name accross the net, but not by its local name.

Any ideas?

---

### Post by Doug S on 2012-04-17
The version you are using is past end of life. There are no more updates.
see: [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)
The solution, in my opinion, is to get a current version.

---

### Post by hawkmage on 2012-04-17
I would assume that since the URLs you are referencing are for Jaunty Jackalope, 9.04, that was end of life on 10/23/10 I am not surprised that you can not find updates.

---

### Post by cackles on 2012-04-17
> **Doug S said:**
> The version you are using is past end of life. There are no more updates.
see: [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)
The solution, in my opinion, is to get a current version.

Thanks.

Im looking at the alternative CD method amongst other things. It tells how to upgrade version to version, but can I upgrade from my version of Jaunty 9.04 to the current or should I be trying to see how migrate settings etc?

---

### Post by hawkmage on 2012-04-17
If you can it is probably best to best to bite the bullet and migrate your settings to a new version.  You may want to think about doing an update to 10.04 LTS to get on a supported version and then in a few weeks you can do an distro update to the 12.04 LTS version when it is released.

---

### Post by arrrghhh on 2012-04-17
> **hawkmage said:**
> If you can it is probably best to best to bite the bullet and migrate your settings to a new version.  You may want to think about doing an update to 10.04 LTS to get on a supported version and then in a few weeks you can do an distro update to the 12.04 LTS version when it is released.

I would recommend this as well.  You don't even have to go to 12.04 that quickly, you can wait until April 2015.  The server/LTS releases are much better to stay on - everyone on the server platform should be on an LTS in my humble opinion ;).

Either way, try to backup everything you've created, config files you've changed, and do a fresh install of 10.04.  Watch when your release is near EOL - the LTS releases give you more than enough time!

---

### Post by cackles on 2012-04-18
Thanks for the advice, I slept on it. I will image the drive then upgrade.
If I have to copy out the files Ive modded, well, its a lot. Im not even sure of all the files Ive changed.
On the plus side, its responding to its name now.

---

