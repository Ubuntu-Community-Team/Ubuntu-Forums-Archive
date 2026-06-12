---
title: "Firefox security update. Where is the Security Notices?"
date: 2012-08-29
forum: Security
---

### Post by kleenex on 2012-08-29
Hi, today (2012-08-29) was available an security update for Firefox from [COLOR=Blue]14.0.1+build1[/COLOR] to [COLOR=Blue]15.0+build1[/COLOR] version. Unfortunately  [COLOR=Green]_[Ubuntu security notices]("http://www.ubuntu.com/usn/precise/")_[/COLOR] does not contain any information about this update, or am I missing something. Is there any possibility, that information can be added with a delay? I mean: first there is available update e.g. with Update-Manager or [COLOR=SeaGreen][COLOR=Black]via[/COLOR] **apt-get** [COLOR=Black]utility[/COLOR][/COLOR] and then note about security issues are added to the USN? Is it normal? If not, what was the type  of this update if there is no official note? How often happens  something like that?

[COLOR=SeaGreen][COLOR=Black]Here are the informations from the[/COLOR] /var/log/apt/history.log[/COLOR] file:
```
**[COLOR=Blue]Start-Date:[/COLOR]** 2012-08-29  13:44:58
**[COLOR=Blue]Commandline:[/COLOR]** [COLOR=Green]apt-get upgrade[/COLOR]
**[COLOR=Blue]Upgrade:[/COLOR]** [FONT=Courier New]firefox-globalmenu:i386 (14.0.1+build1-0ubuntu0.12.04.1, 15.0+build1-0ubuntu0.12.04.1),
firefox:i386 (14.0.1+build1-0ubuntu0.12.04.1, 15.0+build1-0ubuntu0.12.04.1),
firefox-gnome-support:i386 (14.0.1+build1-0ubuntu0.12.04.1, 15.0+build1-0ubuntu0.12.04.1),
firefox-locale-en:i386 (14.0.1+build1-0ubuntu0.12.04.1, 15.0+build1-0ubuntu0.12.04.1)[/FONT]
**[COLOR=Blue]End-Date:[/COLOR]** 2012-08-29  13:45:08
```

---

### Post by thnewguy on 2012-08-29
Typically there aren't any relevant notes on the upgrade, which bothers me a bit. However, if you want to see what is new with Firefox you can look at the project's website.

---

### Post by ottosykora on 2012-08-29
This is simply an update of firefox, the release of new version was done for all operating systems including linux, so what ever was changed is matter of mozilla.

---

### Post by kleenex on 2012-08-29
Hi **thnewguy**! You know, I do not really care what's new (well, maybe not entirely). As you already mentioned, I can check any news on the Project website. I am just curious, why there is not any information at the **Ubuntu Security Notices** site! That's all.

Wait a minute! Maybe it was not a security update? No, it is not possible. During [COLOR=SeaGreen]apt-get upgrade[/COLOR] command I saw **[COLOR=Red]red[/COLOR]** notification on the panel, which means, that there are available security updates, right? Instead of **[COLOR=Yellow][COLOR=DarkOrange]orange[/COLOR][/COLOR]** notification - which simply means all other updates.

---

### Post by ottosykora on 2012-08-30
because it is an update by mozilla for all firefoxes on all computers worldwide. It is nothing specific for ubuntu.
Any computer connected to internet was informed abt new version of firefox during last days so it is obvious that there is also an update for linux.
They produce now new version almost every month in which some of the more recent security problems are solved (but not all) and this is usually a longer list of items which you can get from mozilla any time.

---

### Post by kleenex on 2012-08-30
OK, **[COLOR=Blue][Ubuntu Security Notices]("http://www.ubuntu.com/usn/usn-1548-1/")[/COLOR]** now contains information about Firefox. This entry was added on August 29, so I just wrote this thread a little too fast. Thanks!

---

