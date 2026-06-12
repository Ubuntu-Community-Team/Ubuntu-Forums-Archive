---
title: "Chromium vs Google Chrome.  (Any difference at all?)"
date: 2012-10-08
forum: The Cafe
---

### Post by cbanakis on 2012-10-08
Just wondering if anyone knows what the difference is between Google Chrome, and Chromium.

As far as I can tell, the only difference is the colors of the logo, and the name.

Did Google actually do anything?

Or did they just slap their name on it?

Not that I think its a bad thing.

Just curious.

---

### Post by mamamia88 on 2012-10-08
> **cbanakis said:**
> Just wondering if anyone knows what the difference is between Google Chrome, and Chromium.

As far as I can tell, the only difference is the colors of the logo, and the name.

Did Google actually do anything?

Or did they just slap their name on it?

Not that I think its a bad thing.

Just curious.
no flash or pdf in chromium by default.  you can install both the pdf and flash though really easily at least in arch.   i actually find chromium faster.

---

### Post by jerrrys on 2012-10-08
[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Chromium+vs+Google+Chrome&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Chromium+vs+Google+Chrome&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by Cheesemill on 2012-10-08
This is the page I always point people to:

[http://news.softpedia.com/news/Google-Chrome-vs-Chromium-Understanding-Stable-Beta-Dev-Releases-and-Version-No-140060.shtml](http://news.softpedia.com/news/Google-Chrome-vs-Chromium-Understanding-Stable-Beta-Dev-Releases-and-Version-No-140060.shtml)

---

### Post by IWantFroyo on 2012-10-08
Google's Chrome comes with Flash (and not the legacy that's in the Ubuntu repositories - Google provides newer Flash). That's the biggest difference.

---

### Post by rft183 on 2012-10-08
The sad thing is, I prefer Chrome because the icon is prettier :P

---

### Post by mamamia88 on 2012-10-08
> **rft183 said:**
> The sad thing is, I prefer Chrome because the icon is prettier :P
google image search google chrome icon and then replace the chromium icon with the downloaded image

---

### Post by ojdon on 2012-10-08
chromium is the completely open-source project which Google use for their Chrome browser. With additions of proprietary flash player, pdf, etc, like others have stated above. :)

---

### Post by forrestcupp on 2012-10-09
> **mamamia88 said:**
> no flash or pdf in chromium by default.  you can install both the pdf and flash though really easily at least in arch.   i actually find chromium faster.

Pdf was the major reason I switched to Chrome instead of Chromium. I don't know about Arch, but in Ubuntu, it was easier to install Chrome than it was to figure out how to get pdf's working in Chromium. I'm not an extreme FOSS freak, so I'd rather have a browser where everything I need just works, especially fundamental things like pdf and flash.

---

### Post by mamamia88 on 2012-10-09
> **forrestcupp said:**
> Pdf was the major reason I switched to Chrome instead of Chromium. I don't know about Arch, but in Ubuntu, it was easier to install Chrome than it was to figure out how to get pdf's working in Chromium. I'm not an extreme FOSS freak, so I'd rather have a browser where everything I need just works, especially fundamental things like pdf and flash.
me either i just wanted to install as few packages outside the official repos as possible.   to get pdf working in chrome i just had to install a package called chromium-stable-libpdf.  Not sure if that's available in ubunutu since i haven't tried.

---

### Post by forrestcupp on 2012-10-09
> **mamamia88 said:**
> me either i just wanted to install as few packages outside the official repos as possible.   to get pdf working in chrome i just had to install a package called chromium-stable-libpdf.  Not sure if that's available in ubunutu since i haven't tried.

I can't find anything like it in the repos. Maybe you have to have some PPA.

---

### Post by mamamia88 on 2012-10-09
> **forrestcupp said:**
> I can't find anything like it in the repos. Maybe you have to have some PPA.

pretty sure you have to download the google chrome deb and extract it's contents and then copy the .so file to the right directory in ubuntu.  that's what the pkgbuild does in the aur.

---

### Post by Cheesemill on 2012-10-09
You could probably extract the libpdf.so file from the Chrome .deb file as outlined in the Arch wiki, just follow the manual instructions from this page:

[https://wiki.archlinux.org/index.php/Chromium#Open_PDF_files_inside_Chromium](https://wiki.archlinux.org/index.php/Chromium#Open_PDF_files_inside_Chromium)


Edit: Sniped by mamamia88. BOOM!!

---

### Post by doorknob60 on 2012-10-09
I want to use the PDF plugin and the newer Flash, so I figure I might as well just use Chrome rather than get them working in Chromium (even though it's not hard, that's not the reason). No problems here :)

---

### Post by mamamia88 on 2012-10-09
> **doorknob60 said:**
> I want to use the PDF plugin and the newer Flash, so I figure I might as well just use Chrome rather than get them working in Chromium (even though it's not hard, that's not the reason). No problems here :)

no official chrome in arch but it's in the aur.   would take way too long to download and build with every release. building pepper flash and libpdf with yaourt though takes next to no time though.

---

### Post by DarkAmbient on 2012-10-09
Chromium is faster, and no pdf-viewing or flash-support by default. Probably already been mentioned. Personally I use neither.. but if I fly need to open some pdf in browser then there's plenty of sites that can render them for me.

---

### Post by forrestcupp on 2012-10-09
> **mamamia88 said:**
> pretty sure you have to download the google chrome deb and extract it's contents and then copy the .so file to the right directory in ubuntu.  that's what the pkgbuild does in the aur.

That's exactly what I found out when I was trying to get it working in Chromium. Then I just thought to myself, why not just install and use Chrome where everything just works, instead of installing Chrome, finding the right libs, transferring it to Chromium, and uninstalling Chrome? The fact that Chromium is FOSS is not a good reason because the pdf libs are proprietary.

---

### Post by doorknob60 on 2012-10-09
> **mamamia88 said:**
> no official chrome in arch but it's in the aur.   would take way too long to download and build with every release. building pepper flash and libpdf with yaourt though takes next to no time though.

It doesn't take long to download and build. I use yaourt to update, and all it needs to do is download the deb (or rpm, not sure which it uses, makes no difference) and extract it and install it. It doesn't need to do any compiling or anything. Remember, it's not open source, so it's a binary :P I know libpdf and pepper flash are in AUR, but wouldn't yaourt want to download Chrome twice, once for each of those packages to update them (plus the Chromium download when that updates)? I'll just stick to the Chrome AUR package, no reason to switch if you ask me.

---

### Post by mamamia88 on 2012-10-10
> **doorknob60 said:**
> It doesn't take long to download and build. I use yaourt to update, and all it needs to do is download the deb (or rpm, not sure which it uses, makes no difference) and extract it and install it. It doesn't need to do any compiling or anything. Remember, it's not open source, so it's a binary :P I know libpdf and pepper flash are in AUR, but wouldn't yaourt want to download Chrome twice, once for each of those packages to update them (plus the Chromium download when that updates)? I'll just stick to the Chrome AUR package, no reason to switch if you ask me.

it actually does download the chrome rpm for both.   i'll install chrome with yaourt and see if it's as fast.   if so i'll probably stick with that. edit yep pretty much exactly what i thought.  takes about just as much time to update pepper flash and libpdf to update via yaourt.  at least on my computer.  and it tells me i need to install openssl098 as well.  so i can either use chromium from the repos and 2 different packages from the aur or i could use two packages from the aur.  wonder why chrome isn't just moved to official repos for people who would prefer to use it

---

### Post by AgenT on 2012-10-10
Does anyone know why Chromium is no longer being updated in Ubuntu? 12.10 has the exact same version as 12.04, which is of course outdated (released July 28th). All PPAs have extremely outdated packages from like a year ago. What's going on?

---

### Post by vasa1 on 2012-10-10
> **AgenT said:**
> Does anyone know why Chromium is no longer being updated in Ubuntu? 12.10 has the exact same version as 12.04, which is of course outdated (released July 28th). All PPAs have extremely outdated packages from like a year ago. What's going on?
Nothing new here. I'm in a bit of a hurry but there are several threads in the forum asking the same question.
Essentially, it's my understanding that it's a matter of having **[SIZE="3"]volunteers[/SIZE]** with the ability to build Chromium from code since having Chromium in the repos is a community effort.

---

### Post by TenPlus1 on 2012-10-10
if you would like version 23 of Chromium then check out this link:

[http://www.webupd8.org/2012/09/new-chromium-stable-and-development.html](http://www.webupd8.org/2012/09/new-chromium-stable-and-development.html)

---

### Post by litiform on 2012-10-12
> **cbanakis said:**
> Just wondering if anyone knows what the difference is between Google Chrome, and Chromium.

As far as I can tell, the only difference is the colors of the logo, and the name.

Did Google actually do anything?

Or did they just slap their name on it?

Not that I think its a bad thing.

Just curious.

they the same except for some proprietary 3rd party stuff that Google Chrome added (flash, mp3 codecs etc, PDF)

---

