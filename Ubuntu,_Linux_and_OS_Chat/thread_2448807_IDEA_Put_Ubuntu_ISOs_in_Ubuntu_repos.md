---
title: "IDEA: Put Ubuntu ISOs in Ubuntu repos"
date: 2020-08-14
forum: Ubuntu, Linux and OS Chat
---

### Post by ardouronerous on 2020-08-14
In 2016, [Linux Mint's website was hacked and links to their ISOs were changed to compromised ISOs]("https://blog.linuxmint.com/?p=2994"), and what's worst, [the hackers changed the checksums on the site to match their compromised ISOs]("https://www.ghacks.net/2016/02/21/linux-mint-hacked-iso-images-compromised/"), so even if you diligently checked the checksums, you are still tricked into downloading compromised Linux ISOs.

So, my idea is, for existing users, why not put the Ubuntu ISOs, ISOs of the various Ubuntu flavors, in the Ubuntu repos for secure downloading instead? I believe downloading from the repos is more secure than downloading from a website.

---

### Post by mastablasta on 2020-08-14
repo is a website (well it can be accessed through web browser)

---

### Post by ardouronerous on 2020-08-14
> **mastablasta said:**
> repo is a website (well it can be accessed through web browser)

But isn't the Ubuntu repositories more secure though than a website though?

---

### Post by mastablasta on 2020-08-14
it has mirrors and probably some additional protection than the average website or blog. but nothing is 100%. 

i had a breach via an addon that was installed but disabled. so all the strong passwords didn't help.

you have:
active releases: [https://releases.ubuntu.com/](https://releases.ubuntu.com/)
old releases: [http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/)
and cd image server: [http://cdimage.ubuntu.com/](http://cdimage.ubuntu.com/)

basic apache server helps keeping things simple and secure.

---

### Post by grahammechanical on 2020-08-14
All Ubuntu ISO images including those for the 10 flavours of Ubuntu are hosted on cdimage.ubuntu.com. I cannot imagine the repository for the ISO images being less secure than the repositories for the software packages in the Ubuntu distribution.

Regards

---

### Post by &amp;KyT$0P# on 2020-08-14
For what it's worth, the shaXXXsums.gpg files are detached signature of the corresponding shaXXXsums file, this signature can be verified using Ubuntu APT's default keyring, which is also used to verify stuff from the Ubuntu repos.

---

### Post by aaronrv2008 on 2020-09-09
This is a good idea, I like your suggestion. ;)

---

