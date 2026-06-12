---
title: "Have there been any Ubuntu upgrades to LilyPond and Frescobaldi"
date: 2015-12-27
forum: Ubuntu Studio
---

### Post by Music_Guy on 2015-12-27
Hi,

I want to use LilyPond and Frescobaldi to write music. I noticed that the versions available from the Ubuntu Software Center are older versions. Are there any updates available through Ubuntu? If not, can I uninstall the Ubuntu provided versions and install the latest versions from the website?

---

### Post by ian-weisser on 2015-12-28
> **Music_Guy said:**
> I noticed that the versions available from the Ubuntu Software Center are older versions. Are there any updates available through Ubuntu?
Debian and Ubuntu seem up-to-date, with Lilypond's current stable release, version 2.18.2, available on Ubuntu 15.04, 15.10, and newer.
Most packagers are not interested in unstable versions - why spend effort on software with known bugs and problems? Debian and Ubuntu policy also affect the not-yet-stable versions they will accept.

 > **Music_Guy said:**
> [C]an I uninstall the Ubuntu provided versions and install the latest versions from the website?
Yes, but it's not easy.
There are good reasons Debian and Ubuntu volunteers expend all that effort packaging upstream software and maintaining repositories for your benefit. 

Uninstalling the Ubuntu version is, of course, very easy.
Installing Lilypond from upstream source is not for beginners. You can do it (everyone should know how!), and we can help you along that path if you wish...but it is a learning journey.
Since you are moving off the main path, the number of support gurus who can help you will be reduced.

---

### Post by Music_Guy on 2015-12-28
I'll check on the LilyPond version on my Ubuntu computer. I thought that it was 2.16. But, I read today that, in Frescobaldi, I can choose which version of LilyPond is the default. Maybe the current default is 2.16, while 2.18 is available. Is 2.18 available from the Ubuntu software center, or should I be looking somewhere else?

I'm currently running Ubuntu Studio 14 LTS; I did not think the version of Ubuntu Studio would make a difference. I'll gladly update to 15 if I can get the latest version of LilyPond.

I prefer to use the Ubuntu-provided packages. I am in no way an expert - I am really a novice with linux/Ubuntu. Having some background in programming and working with developers, I am well aware of the difficulties that can arise when building things like packages. I, for one, greatly appreciate the effort the volunteers put into theses packages. 

Thanks for your answers. It sounds like my life just got easier.

---

### Post by Irihapeti on 2015-12-29
You can download LilyPond 2.18 from the LilyPond website [http://www.lilypond.org/website/unix.html](http://www.lilypond.org/website/unix.html). It's not source code, but a precompiled program. This is in the form of a script which will install Lilypond in your home directory - at least, that's where I've put it. The instructions are on the download page. Choose 32 bit or 64 bit depending on what your Ubuntu install is.

There's no need to uninstall the repo version. (You may need the older version if you've already used it in previous files.) Frescobaldi lets you choose which one is going to be your default, and you declare the version you're using in the first line of your file.

---

### Post by howefield on 2015-12-29
> **Music_Guy said:**
> I'm currently running Ubuntu Studio 14 LTS; I did not think the version of Ubuntu Studio would make a difference. I'll gladly update to 15 if I can get the latest version of LilyPond.

You can check the repository version number at packages.ubuntu.com, eg [http://packages.ubuntu.com/search?suite=trusty&keywords=lilypond](http://packages.ubuntu.com/search?suite=trusty&keywords=lilypond)

Ubuntu Studio (15.10) will give you the current version of lilypond and version 2.18.1 of frescobaldi which I think is perhaps slightly older than the current 2.18.2 ?

One thing to note about the current Ubuntu Studio release (15.10) is that it goes end of life next July, you may want to consider holding off till April when the next LTS comes out which will be supported for 5 years.

---

