---
title: "update linux kernel on server"
date: 2006-07-18
forum: Server Platforms
---

### Post by remsy on 2006-07-18
Hi. I have ubuntu dapper drake desktop and server versions installed. I noticed that the desktop version updated the linux image through the automatic update tool. 

How can I also update the server's linux kernel from the command line? is there an automatic update tool or something equivalent?

Thanks,

Remsy

---

### Post by Randomskk on 2006-07-18
sudo apt-get update
sudo apt-get upgrade

Those two commands will fetch new updates and apply them.

---

### Post by Kurt` on 2006-07-18
> **Randomskk said:**
> sudo apt-get update
sudo apt-get upgrade

Those two commands will fetch new updates and apply them.

Whenever I do that, it says the kernel updates have been "held back".

I have to go in through aptitude and do it.

I was actually considering setting up a script to automatically update/upgrade on shutdown, so any new kernel is installed automatically. (I realize you'd never do this on a production system, but it'd be cool on my local testing machine)

---

### Post by Randomskk on 2006-07-18
If it's getting held back and you want to upgrade, replace upgrade with dist-upgrade to force it to not hold anything back.

---

