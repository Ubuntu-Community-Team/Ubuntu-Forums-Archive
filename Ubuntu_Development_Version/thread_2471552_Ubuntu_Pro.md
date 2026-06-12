---
title: "Ubuntu Pro ?"
date: 2022-02-02
forum: Ubuntu Development Version
---

### Post by Frogs Hair on 2022-02-02
I'm seeing an enable Ubuntu Pro message after login followed by system problem message. Anybody know anything about this ?  (Ubuntu Budgie)

---

### Post by #&amp;thj^% on 2022-02-02
I was told we would be notified by e-mail, so you must of been on the list a while.
Did you even register for it?
[https://discourse.ubuntu.com/t/ubuntu-advantage-client/21788](https://discourse.ubuntu.com/t/ubuntu-advantage-client/21788)

---

### Post by Frogs Hair on 2022-02-02
I did not signup for Ubuntu Pro , this was a software updater message not an email. I thought it may be an option on 22.04.

Edit: There is an update for Ubuntu Advantage Tools. See Attached

---

### Post by VMC on 2022-02-02
I didn't see the problem part, but I have seen the Pro message a few times on startup.

---

### Post by Frogs Hair on 2022-02-02
> **VMC said:**
> I didn't see the problem part, but I have seen the Pro message a few times on startup.

 Ok , the error maybe unrelated , I'll select report next time to see what the error is.

---

### Post by VMC on 2022-02-03
I searched the net to try and figure out how to stop it or what it was. This post is the first I found on the subject.
In response to 1fallen comment, I don't recall ever signing up or being put on the Pro list.
It's been a couple of days now that the message appeared. Hopefully it stopped.
"Software&Updates>Ubuntu Pro" is un-selected

---

### Post by Frogs Hair on 2022-02-03
The don't remind me again option in the notification is not working for me right now.

---

### Post by #&amp;thj^% on 2022-02-03
It seems this is a surprise addition, I've sent some emails out to figure out if this is an early pushed release.
No one seems to know in my circle, and I've dropped all my Ubuntu privileges. so it may take a minute for me to hear back.
But no surprise it has a few rough edges to it, right?
> Ubuntu PRO

Ubuntu PRO premium images are published to AWS 5, Azure 1 and GCP [B]which come with Ubuntu Advantage support and services built in. On first boot, Ubuntu PRO images will automatically attach to an Ubuntu Advantage support contract and enable necessary security and support out of the box so that no extra setup is required to ensure a secure and supported Ubuntu machine.
[/B]
There are two primary flavors of Ubuntu PRO images in clouds:

    Ubuntu PRO: Ubuntu LTS images with attached Ubuntu Advantage support with kernel Livepatch and ESM security access already enabled. Ubuntu PRO images are entitled to enable any additional UA services.
    Ubuntu PRO FIPS: Specialized Ubuntu PRO images for 16.04 and 18.04 which come pre-enabled with the cloud-optimized FIPS-certified kernel and all additional SSL and security hardening enabled are available in AWS Ubuntu PRO FIPS 6 and Azure Ubuntu PRO FIPS 2.

Source: [https://discourse.ubuntu.com/t/ubuntu-advantage-client/21788](https://discourse.ubuntu.com/t/ubuntu-advantage-client/21788)
I'd wait to file a bug yet, might get smoothed out in a soon update.

---

### Post by Frogs Hair on 2022-02-03
> **1fallen said:**
> It seems this is a surprise addition, I've sent some emails out to figure out if this is an early pushed release.
No one seems to know in my circle, and I've dropped all my Ubuntu privileges. so it may take a minute for me to hear back.
But no surprise it has a few rough edges to it, right?

Source: [https://discourse.ubuntu.com/t/ubuntu-advantage-client/21788](https://discourse.ubuntu.com/t/ubuntu-advantage-client/21788)
I'd wait to file a bug yet, might get smoothed out in a soon update.

Thanks , I looked it up yesterday. Not too worried about the notification at this point. It seems to be tied to the advantage tools which was not a proposed update.

---

### Post by #&amp;thj^% on 2022-02-03
> **Frogs Hair said:**
> Thanks , I looked it up yesterday. Not too worried about the notification at this point. It seems to be tied to the advantage tools which was not a proposed update.

I now know why one of my test-install hasn't seen this yet>>KVM
I'm part of all Ubuntu Advantage, Livepatch and ESM security access.
No support for KVM systems at this point, and maybe never will.

---

### Post by deadflowr on 2022-02-03
Here: [https://discourse.ubuntu.com/t/ubuntu-pro-has-a-memory-leak/26487]("https://discourse.ubuntu.com/t/ubuntu-pro-has-a-memory-leak/26487")

Maybe also related to this: [https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/1958311]("https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/1958311")

---

### Post by #&amp;thj^% on 2022-02-03
> **deadflowr said:**
> 
Maybe also related to this: [B][https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/1958311]("https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/1958311")
[/B]
Thanks deadflowr In my case(KVM) i would also have to replace my ESM security access page>>>so I'm weighing my thoughts here. (Yep it hurts ;))

---

### Post by Frogs Hair on 2022-02-03
Confirmed bug report here.

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-advantage-tools/+bug/1959869](https://bugs.launchpad.net/ubuntu/+source/ubuntu-advantage-tools/+bug/1959869)

---

### Post by VMC on 2022-02-03
> **Frogs Hair said:**
> Confirmed bug report here.

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-advantage-tools/+bug/1959869](https://bugs.launchpad.net/ubuntu/+source/ubuntu-advantage-tools/+bug/1959869)

Per that fix, my update-notifier isn't updated yet:```
$ apt-cache show update-notifier
Package: update-notifier
Architecture: amd64
Version: 3.192.48
``` 3.192.49 is the fix

Correction: I just now updated my system and the fix ,3.192.49, is now installed.```
$ apt-cache show update-notifier
Package: update-notifier
Architecture: amd64
Version: 3.192.49
```

---

### Post by zebra2 on 2022-02-07
Ubuntu Pro is available as an option in the Repositories in Ubuntu 22.04 (don't know about other releases). It resides next to the "Proposed" option.  Ubuntu Pro (if enabled) offers auto unattended updates and on the fly kernel unattended upates for free for up to three systems.  It also offers machine certification at different levels where needed (probably per pay). Ubuntu Pro is a feature and not a bug. If you don't want it then just don't enable it. If you click on the flag when it appears you can click the option "don't ask me again", and you won't be bothered by the flag again.  If you want to fuss about this, I guess it is ok but some users may actually want this feature. My experience is that Canonical is going to do what they want. My guess is "make some money", if possible.

---

### Post by Frogs Hair on 2022-02-07
> when it appears you can click the option "don't ask me again", and you won't be bothered by the flag again.

The option to disable the flag was not working and has since been corrected by an update to the update notifier. Please read all the posts.

```
apt-cache show update-notifier
Package: update-notifier
Architecture: amd64
Version: 3.192.49
```

---

