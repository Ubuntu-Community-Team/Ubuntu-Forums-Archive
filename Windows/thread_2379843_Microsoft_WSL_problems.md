---
title: "Microsoft WSL problems"
date: 2017-12-10
forum: Windows
---

### Post by truephoenyx on 2017-12-10
Has anyone heard of any problems with updating Microsoft's BASH on Ubuntu on Windows in the past few days? The apt-get is trying to go to archive(or security).ubuntu.com for Xenial updates and it keeps coming back like this:

Err:1 [https://cerebrate.github.io/wsl-translinux](https://cerebrate.github.io/wsl-translinux) xenial InRelease
  Could not resolve host: cerebrate.github.io
Err:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial InRelease
  Temporary failure resolving 'archive.ubuntu.com'
Err:3 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease
  Temporary failure resolving 'security.ubuntu.com'
Err:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates InRelease
  Temporary failure resolving 'archive.ubuntu.com'
Err:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports InRelease
  Temporary failure resolving 'archive.ubuntu.com'
Reading package lists... Done
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/xenial/InRelease](http://archive.ubuntu.com/ubuntu/dists/xenial/InRelease)  Temporary failure resolving 'archive.ubuntu.com'
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/xenial-updates/InRelease](http://archive.ubuntu.com/ubuntu/dists/xenial-updates/InRelease)  Temporary failure resolving 'archive.ubuntu.com'
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/xenial-backports/InRelease](http://archive.ubuntu.com/ubuntu/dists/xenial-backports/InRelease)  Temporary failure resolving 'archive.ubuntu.com'
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/xenial-security/InRelease](http://security.ubuntu.com/ubuntu/dists/xenial-security/InRelease)  Temporary failure resolving 'security.ubuntu.com'
W: Failed to fetch [https://cerebrate.github.io/wsl-translinux/dists/xenial/InRelease](https://cerebrate.github.io/wsl-translinux/dists/xenial/InRelease)  Could not resolve host: cerebrate.github.io
W: Some index files failed to download. They have been ignored, or old ones used instead.

The thing is I'm on that same pc using Chrome to do this message! This is confusing me badly, so if anyone has a clue please send it to me.:confused:

---

### Post by dragonfly41 on 2017-12-10
I have  just run sudo apt-get update && sudo apt-get upgrade on WSL
without errors if that helps.

---

### Post by truephoenyx on 2017-12-18
That's what I've been doing. Except that what I showed above is the response I'm getting when I try. I've checked the hosts, host.allow and host.deny files, but they are all empty except for the standard comments on how to use them. What is weird is Windows itself has no problem going there. I can open Chrome and go to [http://archive.ubuntu.com](http://archive.ubuntu.com) and get a page that says "Index of /" and has a ubuntu link on it. So Windows has no problem with it. I open WSL Ubuntu and run the update/upgrade command and "no dice, I can't get there from here". I am seriously confused by this. So if anyone can help by pointing anything out to me, please do!

---

### Post by howefield on 2017-12-18
Thread moved to the "*Windows*" forum.

---

### Post by truephoenyx on 2018-01-01
Still no luck so I tried doing a wget to mosquitto.org to get a gpg.key. It won't talk to the Internet at all. I uninstalled Ubuntu, turned off WSL, rebooted and did a disk cleanup, turned WSL back on, rebooted and reinstalled Ubuntu. It still won't talk to the Internet. Windows 10 has no problems going anywhere on the Internet but WSL won't work. Is there anyone who has *any* clue at all as to what's going on? Please?

---

### Post by ryandammrose on 2018-01-18
Hi truephoenyx,

I was able to resolve this issue by going into /etc/resolv.conf [e.g. sudo nano /etc/resolv.conf ] and making sure it had proper nameservers; it should read like:
nameserver 8.8.8.8
nameserver 8.8.4.4

as described in this StackOverflow thread: [https://askubuntu.com/questions/892569/apt-get-update-not-working-in-ubuntu-16-04-temporary-failure-resolving/907569#907569](https://askubuntu.com/questions/892569/apt-get-update-not-working-in-ubuntu-16-04-temporary-failure-resolving/907569#907569)

After that, I was able to apt-get update and apt-get upgrade just fine.

---

