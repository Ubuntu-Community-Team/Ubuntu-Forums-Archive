---
title: "Ubuntu update problem"
date: 2019-01-01
forum: Security
---

### Post by cam17 on 2019-01-01
I have noticed again 2 problems with Ubuntu 18.10 updates.

1. I had Ubuntu on a US update location using "software & update" application and did not receive any updates for several days. I changed to another update location and a "ubase" update was then made available.

2. I have selected "when there are security updates" "download and install automatically" but security updates are not install automatically. I see on occasional updates security updates pending.

The first issue has occurred twice. Is their a known problem with updates?

---

### Post by oldfred on 2019-01-01
If you notice different mirrors have different update schedules.
[https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)
So when switching mirrors you may have different updates.
Best not to switch often as then you can get into out of sync issues.

---

### Post by cam17 on 2019-01-12
I unable to find the update site "mirror.us.leaseweb.net" which is from Virginai, in "software & updates" but it was selected in my update list.

Is "mirror.us.leaseweb.net" a valid update site? this is my second reply my first reply went missing.

---

### Post by oldfred on 2019-01-12
I used to use a site that was listed, and happened to notice somewhere that they were only going to offer updates for internal use.
But it was still listed for a long time.

I would expect this list to be fairly current:
[https://launchpad.net/ubuntu/+cdmirrors](https://launchpad.net/ubuntu/+cdmirrors)

---

### Post by cam17 on 2019-01-13
Is there a way to search for the mirror "mirror.us.leaseweb.net" as the names listed in the United states such as "xTom"  and "layeronline" don't identify who they are. I suspect this mirror may not be providing correct updates

---

### Post by oldfred on 2019-01-13
I just clicked on your mirror link above and it works to show lots of distributions.
[http://mirror.us.leaseweb.net/](http://mirror.us.leaseweb.net/)

---

### Post by cam17 on 2019-02-01
How can I identify positively the links being downloaded. As an example if I see a download is available can the individual download files be identified from a source?

---

### Post by oldfred on 2019-02-02
I just did 
sudo apt update
then
sudo apt upgrade

It shows files like this as it downloads, but only the list before the download starts.

```
Get:52 http://us.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 mesa-va-drivers amd64 18.2.2-0ubuntu1~18.04.1 [1,888 kB]
Get:53 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 mesa-vdpau-drivers amd64 18.2.2-0ubuntu1~18.04.1 [2,008 kB]

```

---

### Post by cam17 on 2019-02-02
I am familiar with the update process. I am looking to identify updates before installing.  the reason is my Ubuntu.14.04.1 LTS after a install with no updates runs but crashes after installing a complete or all updates. I have also noticed that one of the commands from my Ubuntu was missing "ifconfig" then wifi did not work when starting up until several minutes later would then it would connect.   I am suspecting a false or faulty update causing problems on my Acer so to identify I would like to confirm the individual update then update that component then go to the next update.

---

### Post by cam17 on 2019-02-08
Is the best way to update via command or the "software updater"?

---

### Post by oldfred on 2019-02-08
Not sure it really matters.

I like to use terminal, just so I see each line being processed or with updater open the window to see the process.

---

### Post by &amp;KyT$0P# on 2019-02-08
> **cam17 said:**
> Is the best way to update via command or the "software updater"?

(For what it's worth, Software Updater is the only way to [phased updates]("https://wiki.ubuntu.com/PhasedUpdates").)

---

