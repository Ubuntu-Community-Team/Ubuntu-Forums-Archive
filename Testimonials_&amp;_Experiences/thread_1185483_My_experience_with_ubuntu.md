---
title: "My experience with ubuntu"
date: 2009-06-12
forum: Testimonials &amp; Experiences
---

### Post by xusword on 2009-06-12
Please do not take the following as an attack on Ubuntu. I am just trying describe my experience and hopefully get some constructive suggestions. Honestly, I wish to switch to using Linux eventually because I really do not believe in what Microsoft and Apple has been doing with those DRM.


Last year when I was at school I received two identical (old) machines in my office. (P4 2.66GHz 512MB RAM).

I installed XP SP2 on one and XUbuntu on the other and use them side by side. For some reasons XUbuntu is significantly more laggy especially when it comes to UI tasks such as opening windows, switching between windows or Eclipse's autocomplete. (Note that the XP machine has McAfee installed and should have slowed everything down) Somehow, I discovered Linux can crash, and in my case it crashes more often than XP.

Another interesting discovery is that USB write speed are significantly different. Copying a big file (1~2G) to my flash disk takes 2~5 times longer on XUbuntu.

However, when it comes to networking. XUbuntu wins hands down. Downloading and uploading are noticeably faster on XUbuntu.

Finally: multimedia. I tried to watch videos on both machines. Images produced by Windows Media Player is noticeably more vivid than GStreamer, but, I know it is totally unfair to compare these two because Ubuntu have been having problem with these proprietary codecs. (and video card drivers?)

Recently, I had to install Ubuntu 9.04 on a P4 3.2HT with 1G RAM. It is really laggy. I disabled all effects but I am still bothered a great deal by it.

Why hasn't Linux be faster or more stable than XP, like I think it should have been. Have I been missing some manual configuration or optimization that could have made it faster?

---

### Post by eilios on 2009-06-12
If you have the intelligence to use it, try a lightweight distro such as Puppy Linux. It will run much faster, but it doesn't have Ubuntu's ease of use.

---

### Post by decoherence on 2009-06-12
anyone know if xubuntu ships with xfce's compositing turned on? that'd potentially make the UI feel laggy compared to XP.

if you are using the latest version of Ubuntu, there are regressions in certain video drivers that can cause slowness if you try to make use of graphics acceleration. This is a very unfortunate (some might say 'shameful') situation -- there are fixes that work to varying degrees. There are posts scattered about the forum... sorry I have none to link to off the top of my head.

You also might try the Ubuntu 8.04 LTS release. It's not as cutting edge but folks who have trouble with the latest sometimes find the LTS release works better. The option should be available on the download page.

Finally, if you want to put the following in to a terminal and post the output here, it might give us some clues as to why things are slow.

```
sudo lshw -C video
```

---

### Post by HappyFeet on 2009-06-12
I can assure you that your experiences are not typical. I've done my fair share of installing ubuntu on various computers, and have not had any those problems. It works great. Not every computer in the world will respond favoribly to ubuntu (just like any OS), and it seems like you were one of the unlucky few.

---

### Post by mdsmedia on 2009-06-12
> **HappyFeet said:**
> I can assure you that your experiences are not typical. I've done my fair share of installing ubuntu on various computers, and have not had any those problems. It works great. Not every computer in the world will respond favoribly to ubuntu (just like any OS), and it seems like you were one of the unlucky few.
I have to agree. I'm using Ubuntu, now, because XP was so slow. I've re-installed XP and it's a lot better than it was, but Ubuntu is just so much more "snappy" on low-end hardware.

I'm using a HP Compaq nx6120 notebook with a 1.6GHz Centrino chip and what calls itself 512MB RAM (it actually shows up as 492MB).

I recently re-installed XP on a friend's PC. It was so slow the LiveCD was painfully slow. I partitioned his HDD and installed Ubuntu, just to use as a tool for partitioning and backing up. He has 192MB RAM, and Ubuntu flew on his machine. A newly installed XP still dragged.

---

