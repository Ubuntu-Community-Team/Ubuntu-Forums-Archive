---
title: "Flash-Plugin Installer Hangs Apt-Get"
date: 2013-02-27
forum: Ubuntu Development Version
---

### Post by cole.mickens on 2013-02-27
So, yeah. I'll just post this:
```

$ sudo apt-get install flashplugin-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libllvm3.1:i386 libpgm-5.1-0 libzmq1 ttf-droid ttf-umefont ttf-unfonts-core
Use 'apt-get autoremove' to remove them.
Suggested packages:
  x-ttcidfont-conf ttf-bitstream-vera ttf-dejavu ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-installer
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/7,034 B of archives.
After this operation, 139 kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  flashplugin-installer
Install these packages without verification [y/N]? Y
Preconfiguring packages ...
Selecting previously unselected package flashplugin-installer.
(Reading database ... 271190 files and directories currently installed.)
Unpacking flashplugin-installer (from .../flashplugin-installer_11.2.202.273ubuntu0.12.10.1_amd64.deb) ...
Processing triggers for update-notifier-common ...
flashplugin-installer: downloading http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.273.orig.tar.gz

```

And then it hangs!!!!! In Konsole, in ZSH, in Bash, in Xterm. Doesn't matter, it hangs.

And when I have to restart my computer since it doesn't respond to CTRL+C... I run

```
sudo dpkg --configure -a
```

and it stalls out again, but thank god, I can at least kill it with CTRL+C.

At the very least, APT+flashplugin-installer should PROPERLY respond to SIGTERM. Also, if the installer worked, that'd be great ;)

---

### Post by cole.mickens on 2013-02-27
This issue was also confirmed by a 12.04 user in #ubuntu.

---

### Post by cole.mickens on 2013-02-27
Actually, as penguinman in IRC noted, this is going to hang the installs of anyone doing a fresh ubuntu install tonight. Obviously not great news.

---

### Post by carl4926 on 2013-02-27
I can confirm
Just wait it out
Someone will fix it

---

### Post by deadflowr on 2013-02-27
> **carl4926 said:**
> I can confirm
Just wait it out
Someone will fix it

+1 for just wait it out.

How long are people waiting and deciding to shutdown and reboot?

I've noticed the flashplugin updates have been seemingly hanging for extended periods of time. However, if I let it roll and avoid messing with it, it installs fine.

```
flashplugin-installer:
  Installed: 11.2.202.273ubuntu0.12.04.1
  Candidate: 11.2.202.273ubuntu0.12.04.1

```

Here's the latest version, I installed tonight, I think it took about four minutes hanging there, but it finally installed.

And bug reports on the matter should be thrown at Adobe.

---

### Post by Harry33 on 2013-02-27
> **deadflowr said:**
> +1 for just wait it out.

How long are people waiting and deciding to shutdown and reboot?

I've noticed the flashplugin updates have been seemingly hanging for extended periods of time. However, if I let it roll and avoid messing with it, it installs fine.

```
flashplugin-installer:
  Installed: 11.2.202.273ubuntu0.12.04.1
  Candidate: 11.2.202.273ubuntu0.12.04.1

```Here's the latest version, I installed tonight, I think it took about four minutes hanging there, but it finally installed.

And bug reports on the matter should be thrown at Adobe.


I don't think it is Adobe to be blaimed.
I used the adobe-flashpugin (11.2.202.273-0quantal1) package (from Quantal repo)
and that one installed just fine and fast with no issues.

---

### Post by cole.mickens on 2013-02-27
> **deadflowr said:**
> +1 for just wait it out.

How long are people waiting and deciding to shutdown and reboot?

I've noticed the flashplugin updates have been seemingly hanging for extended periods of time. However, if I let it roll and avoid messing with it, it installs fine.

```
flashplugin-installer:
  Installed: 11.2.202.273ubuntu0.12.04.1
  Candidate: 11.2.202.273ubuntu0.12.04.1

```

Here's the latest version, I installed tonight, I think it took about four minutes hanging there, but it finally installed.

And bug reports on the matter should be thrown at Adobe.

Not to be abrasive, but I disagree pretty strongly with the last statement : The script flashplugin-installer runs should NOT have the ability to hang the terminal. It SHOULD respond to SIGTERM/Ctrl+c.


Also, you can see from the URL that Canonical is hosting Flash in this instance, it's not grabbing it from Adobe's servers.

Also, I waited a really long time and then killed sabnzbdplus and then waited even longer. And then rebooted, made sure I didn't have sab running and tried again and still it took longer than it took Chrome to download from the same link....


Quite frankly, if THIS is the reason that every so often I get a super slow install of Ubuntu... that'd be disappointing to hear.

---

### Post by vasa1 on 2013-02-27
Hi, cole!

I saw what you saw on Lubuntu 12.10. The first time I was impatient and went the Ctrl+C route. The next time, I let it take its own time ... which it did with no indication at all that anything was happening. After a disproportionately long while, without any intervention by me, it completed successfully.

I suspect there are days/times something is dead slow. All the same, I wish there was some screen output showing the progress of the download from wherever.

---

### Post by zika on 2013-02-27
It is to be expected that whenever new version of plugin is available there is a sort of jam on that route...

---

### Post by carl4926 on 2013-02-27
Obviously
You can grab the other updates if you unmark flash

But flash was still blugger'd for me this Lunch time UK (noon)

---

### Post by vasa1 on 2013-02-27
> **cole.mickens said:**
> ...
Also, you can see from the URL that Canonical is hosting Flash in this instance, it's not grabbing it from Adobe's servers.
...
Isn't that url for the downloader? After that, doesn't the downloader get it direct from Adobe?

---

### Post by zika on 2013-02-27
> **vasa1 said:**
> Isn't that url for the downloader? After that, doesn't the downloader get it direct from Adobe?[IMG]http://www.sherv.net/cm/emoticons/yes/nod-yes-smiley-emoticon.gif[/IMG]

---

### Post by carl4926 on 2013-02-27
Seems OK now
Though a little slow

---

### Post by cole.mickens on 2013-02-27
> **vasa1 said:**
> Isn't that url for the downloader? After that, doesn't the downloader get it direct from Adobe?


> **zika said:**
> [IMG]http://www.sherv.net/cm/emoticons/yes/nod-yes-smiley-emoticon.gif[/IMG]

Um, no.

[http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.273.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.273.orig.tar.gz)

Look at the filename. It's nearly 14MB. It's not a downloader, that's the actual flash plugin. Canonical.com.

---

### Post by vasa1 on 2013-02-27
> **cole.mickens said:**
> Um, no.

[http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.273.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.273.orig.tar.gz)

Look at the filename. It's nearly 14MB. It's not a downloader, that's the actual flash plugin. Canonical.com.
Interesting! I'll watch more carefully the next time.

In that case, why is it a two-step process? And why does [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/) have both deb (~6M) and .tar.gz (13M)? Anyone?

---

### Post by cariboo on 2013-02-28
> **vasa1 said:**
> Interesting! I'll watch more carefully the next time.

In that case, why is it a two-step process? And why does [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/) have both deb (~6M) and .tar.gz (13M)? Anyone?

The tar.gz file has both the i386 and amd64 versions, while the .deb has only either the i386 or amd64 version only.

---

### Post by vasa1 on 2013-02-28
> **cariboo907 said:**
> The tar.gz file has both the i386 and amd64 versions, while the .deb has only either the i386 or amd64 version only.
Okay, thanks :)

---

### Post by zika on 2013-02-28
> **cole.mickens said:**
> Um, no.

[http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.273.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.273.orig.tar.gz)

Look at the filename. It's nearly 14MB. It's not a downloader, that's the actual flash plugin. Canonical.com.
Then I was wrong... Mea culpa.

---

