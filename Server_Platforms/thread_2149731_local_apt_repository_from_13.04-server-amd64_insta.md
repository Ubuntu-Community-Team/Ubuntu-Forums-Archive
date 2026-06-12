---
title: "local apt repository from 13.04-server-amd64 installer iso"
date: 2013-05-29
forum: Server Platforms
---

### Post by aseguro on 2013-05-29
Is it possible to create a local repo using the regular iso installer?

Long story short, I'd like to match all packages' versions with the ones that come in the iso, tried to add the media into mirror.list and use apt-mirror, but it looks like apt-mirror does not support to use media as source.

Thanks in advance,

---

### Post by chrisguk on 2013-05-29
Im not sure why you would want to do this.  If you are trying to achieve network installs of a particular distro then you could as easily set that up.  The whole purpose of setting up a local repo (mirror) using apt-mirror is to save bandwidth on networks that have a lot of clients using Ubuntu.  It will be a nice learning curve for me if anyone says otherwise in response to this post though.

Remember that apt-mirror actually "mirrors" the directory structure of lets say "ubuntu" - archive.ubuntu.com/ubuntu/ then there are sub directories (main, restricted blah blah.........) So you would essentially have to mirror that I believe.  Another thing I am not sure what the benefit of syncing a package list this is already out of date.  This the reason for issuing "sudo apt-get update" immediately after a install from an ISO.

---

### Post by aseguro on 2013-05-29
Thanks for your answer!
In this case we have few servers deployed in production using the mentioned iso, we'd like to match these servers in a complete new mirror, that's why I can't use apt-mirror to clone an existing 'public' repo.

---

### Post by chrisguk on 2013-05-29
Well if you want a similar setup you dont need apt-mirror.  All that does is sync with the ubuntu repo.

This is what I would do:

Create a partition or folder of your choice.  Lets call is "repo"

The files you need are under /dists and /pool.  The later contains the actual packages.

If you setup the folder structure up the same as the official repo then is should all work.  Obviosly just replacing archive.ubuntu.com with your IP or FQDN.

---

### Post by aseguro on 2013-05-29
Great thanks. I tried that already (overwriting my existing and working pool and dists folders, maintaining my working pressed file) and something failed during the process (Menu item 'live-installer' selected, error: could not find any live images ), so I supposed somehow that the issue was some setting hard-coded in one of the files I was copying from the iso and didn't spend more time troubleshooting, I'll try again.
Thanks again.

---

### Post by chrisguk on 2013-05-29
I missed something out which is very important.  Install Apache web server.  Then create symbolic links to each directory.  For example:

ln -s /var/archive.ubuntu.com /var/www/ubuntu

Its these web links that the update looks at when trying to find images.

---

