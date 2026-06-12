---
title: "New Pangolin today"
date: 2009-02-16
forum: System76 Support
---

### Post by reaper308 on 2009-02-16
I have tried everything and I can not get my dvds to play

---

### Post by thomasaaron on 2009-02-16
Did you try following the instructions here...
[http://knowledge76.com/index.php/Installing_Restricted_Formats](http://knowledge76.com/index.php/Installing_Restricted_Formats)

---

### Post by reaper308 on 2009-02-16
im am running 64bit intrepid on my pangolin and this is the out put doing what you told me to do on that link

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0E931CE221789C97
W: You may want to run apt-get update to correct these problems

---

### Post by jdb on 2009-02-17
> **reaper308 said:**
> im am running 64bit intrepid on my pangolin and this is the out put doing what you told me to do on that link

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0E931CE221789C97
W: You may want to run apt-get update to correct these problems

Are you sure you ran this line:

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

jdb

---

### Post by thomasaaron on 2009-02-17
That error actually has nothing to do with the tutorial. It is probably a pre-existing problem in your sources.list file. See...

[https://answers.launchpad.net/ubuntu/+source/synaptic/+question/61145](https://answers.launchpad.net/ubuntu/+source/synaptic/+question/61145)

I'm going to have to research it. Will report back soon.

---

### Post by thomasaaron on 2009-02-17
Reaper,

Attached to this post is a file called sources.txt. It is the repository file for a freshly imaged Pangolin.

Download it to your **Desktop** and then run this commands...

```
cd Desktop
sudo mv sources.txt /etc/apt/sources.list
sudo apt-get update
sudo apt-get --assume-yes dist-upgrade
```

Now the error should not appear. Try again to run the aforementioned tutorial.

---

