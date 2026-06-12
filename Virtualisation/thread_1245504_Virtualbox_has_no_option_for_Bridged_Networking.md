---
title: "Virtualbox has no option for Bridged Networking"
date: 2009-08-20
forum: Virtualisation
---

### Post by xmrkite on 2009-08-20
Hello. I just did a fresh install of the latest virtualbox (2.1.4_ose) but i don't see how to do bridged networking.

The instructions on this page: [https://help.ubuntu.com/community/VirtualBox/Networking](https://help.ubuntu.com/community/VirtualBox/Networking)

are rather vague for kubuntu 9.04 users.

Any help would be greatly appreciated.

-Thanks

---

### Post by howefield on 2009-08-20
> **xmrkite said:**
> Hello. I just did a fresh install of the latest virtualbox (2.1.4_ose) but i don't see how to do bridged networking.

That isn't the latest virtualbox, current version is 3.0.4

Bridged networking is one of the options in the network settings, but not sure about version 2.1.4

---

### Post by xmrkite on 2009-08-20
You know, you're right. After looking at the virtualbox site, there is a much newer version. Synaptic shows the version i have as the latest. Perhaps the Ubuntu repositories are way behind?

-I'll install the newer version and post back.

-Thanks

---

### Post by xmrkite on 2009-08-20
Wow, that was easy. Now it works great. Any idea why ubuntu would have such an old version in its repositories?

-Thanks

---

### Post by howefield on 2009-08-20
> **xmrkite said:**
> Any idea why ubuntu would have such an old version in its repositories?

Glad you are sorted, 2.1.4 would have been the current Virtualbox when the Ubuntu version that you are running was released. Most software in the repository is not updated till the next version of Ubuntu is released, there are a few notable exceptions to this rule but virtualbox is not one of them.

There have been a few updates to virtualbox in the meantime with a huge number of fixes and features added such as the one you have encountered.

---

### Post by jocampo on 2009-08-20
> **xmrkite said:**
> Wow, that was easy. Now it works great. Any idea why ubuntu would have such an old version in its repositories?

-Thanks

You need to add the repositories (depending of your Ubuntu version)

Add the VirtualBox Repository.
```

sudo sh -c "echo 'deb http://download.virtualbox.org/virtualbox/debian jaunty non-free' >> /etc/apt/sources.list"

```

Add the Sun public key for the VirtualBox Repository.
```

wget -q http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc -O- | sudo apt-key add -

```

then

```
sudo apt-get update
```

Once there, you can browse for most recent version and download...but be aware...3.04 or most recent version, has some bugs. It did not work for me on my Ubuntu Server. I would download 1 version lower and use that instead but it's up to you. I think 2.4 includes Bridged networking and is stable.

---

### Post by xmrkite on 2009-08-21
Since i put 3.0.4 on yesterday, can i downgrade? Should i downgrade? It seems stable so far. What sorts of bugs are there in 3.0.4?

-Thanks

---

