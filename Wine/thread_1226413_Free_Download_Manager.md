---
title: "Free Download Manager"
date: 2009-07-29
forum: Wine
---

### Post by Hoom@n on 2009-07-29
Hello.
I want to install FDM on my Wine. Should I do anything special before(after)? Or, just install it?
Thanks.

---

### Post by Hoom@n on 2009-07-29
I installed it. Everything was OK during installation and Free Download Manager is added to Applications->Wine->Programs->Free Download Manager->Free Download Manager. But, nothing happens when I click it! I restarted the computer and tried again and nothing happened again! What can I do?

---

### Post by ibutho on 2009-07-29
Why not use a native Linux download manager like gwget, kget, uget d4x etc?

---

### Post by ubuntu27 on 2009-07-30
I don't know the solution to your problem. I never used wine before.

As an alternative, you can install GNOME Transfer Manager (GTM). It is in the repository.

```
sudo apt-get install gtm
```

Quote:

GTransferManager allows the user to retrieve multiple files from the web.
These files can be retrieved in multiple parts and each part retrieved on a
separate session that the user is connected to the Internet. This is most
useful to users with dialup connections. The program performs these tasks
using wget as its back-end.

[URL="apt://gtm"]
Click here to install GTM[/URL]

---

### Post by Arup on 2009-07-30
Closest thing to FDM is Multiget and you can find it in the repos in case you have enabled medibuntu repos.

---

### Post by Hoom@n on 2009-07-30
Wow! I thought there is no native download manager for Linux! (I asked for a download manager 1 year ago in this forum and I got just some Firefox add-ons) I try to find something about them soon. And, please  explain the differences between gwget, kget, uget d4x, GTM, Multiget and put some screenshots.

---

### Post by Arup on 2009-07-30
> **Hoom@n said:**
> Wow! I thought there is no native download manager for Linux! (I asked for a download manager 1 year ago in this forum and I got just some Firefox add-ons) I try to find something about them soon. And, please  explain the differences between gwget, kget, uget d4x, GTM, Multiget and put some screenshots.

I have used all and find Multiget to be the closest to Windows DM.

[http://multiget.sourceforge.net/](http://multiget.sourceforge.net/)

---

### Post by kostkon on 2009-07-30
+1 for MultiGet. It reminds me of FlashGet.

You can easily install it using Synaptic.

---

### Post by Hoom@n on 2009-07-30
> **kostkon said:**
> +1 for MultiGet. It reminds me of FlashGet.

You can easily install it using Synaptic.
Thanks, I installed it. But, there is long way to FDM and it seems the project is not continued.
I still wait for an answer to main question of this topic.(What's the problem with my FDM?)
And, I may try other Linux-native download managers.(e.g. gtm)

---

### Post by Arup on 2009-07-30
> **Hoom@n said:**
> Thanks, I installed it. But, there is long way to FDM and it seems the project is not continued.
I still wait for an answer to main question of this topic.(What's the problem with my FDM?)
And, I may try other Linux-native download managers.(e.g. gtm)

Exactly what do you find missing in MutliGet, in my case it handles all downloads perfectly and does what FDM did for me in Windows. In case you are looking for a more powerful downloader that handles filesharing sites, check out Jdownloader.

---

### Post by ubuntu27 on 2009-07-31
> **Hoom@n said:**
> Wow! I thought there is no native download manager for Linux! (I asked for a download manager 1 year ago in this forum and I got just some Firefox add-ons) I try to find something about them soon. And, please  explain the differences between gwget, kget, uget d4x, GTM, Multiget and put some screenshots.


[B]
JDownloader[/B]: [http://www.jdownloader.org/](http://www.jdownloader.org/)

**GNOME Transfer Manager** (GTM): [http://gtm.sourceforge.net/](http://gtm.sourceforge.net/)
[B]
GWGET[/B]: [http://projects.gnome.org/gwget/](http://projects.gnome.org/gwget/)
[B]
KGet[/B]: [http://en.wikipedia.org/wiki/KGet](http://en.wikipedia.org/wiki/KGet)

[http://docs.kde.org/development/en/kdenetwork/kget/index.html](http://docs.kde.org/development/en/kdenetwork/kget/index.html)

**Uget**: [http://urlget.sourceforge.net/](http://urlget.sourceforge.net/)

**Downloader for X** (D4X): [http://en.wikipedia.org/wiki/Downloader_for_X](http://en.wikipedia.org/wiki/Downloader_for_X)

---

### Post by hariks0 on 2010-02-20
Nothing comes even close to FDM. Scheduling downloads, shutdown after completion and so many... Just no substitute at all.

---

