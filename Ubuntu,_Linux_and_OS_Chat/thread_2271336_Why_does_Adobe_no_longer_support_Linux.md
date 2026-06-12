---
title: "Why does Adobe no longer support Linux?"
date: 2015-03-29
forum: Ubuntu, Linux and OS Chat
---

### Post by Alduins_Khajiit on 2015-03-29
Had to install adobe flash in order for a website's photo uploader to work. and on Adobe's website, it says the last supported Flash for any type of Linux machine is Flash 11! we're at 16 now on Windows!

Even on the lastest Linux Ubuntu build, we Linux users have to use an ***Old*** Flash 11!

why is that?

---

### Post by Bucky Ball on 2015-03-29
*Thread moved to **Ubuntu, Linux and OS Chat**.*

Not a support request. You might be better to email Adobe directly regarding this. I'd be curious to know.

If you want the latest Flash, install Chromium with Pepperflash or install Chrome. The latest flash only works with either of those, though, and is not system wide.

---

### Post by craig10x on 2015-03-29
Google Chrome, as Bucky Ball mentioned, will get you the latest versions of flash on linux (they have an agreement with Chrome for that) the advantage of downloading Chrome from their website (instead of getting from the software center and adding pepperflash separately) is that Chrome already has it built in...and Chrome updates more frequently then Chromium does (Chrome also adds a ppa updater in your software sources so that you get the newest version as soon as it arrives)...

It would be interesting to hear why adobe no longer supports flash for linux (other then the Chrome agreement) so you might want to inquire and let us know...

---

### Post by Tar_Ni on 2015-03-29
Hi Alduins_Kahjiit,

Adobe still supports the Flash plugin 11.2  for Linux with security updates until 2017. But they are not longer  developping any new versions for Linux desktop Oses and Android. However, Google ships it's one flash plugin known as ''pepperflash''' which is embedded in the Chrome browser and also available for Chromium

 It's important to mention that the plugin 11.2 still works for the vast majority of websites.  I use it everyday and I don't have any issue. You can safely download it in the Ubuntu Software Center.

> **craig10x said:**
> It would be interesting to hear why adobe no longer supports flash for linux (other then the Chrome agreement) so you might want to inquire and let us know...

Adobe has never been a great supporter of the Linux platform. Most of their products are not even available for Linux.

Honestly, I think this is actually a good thing that the flash plugin is no longer developped for Linux and Android. It means that the web will have to move towards HTML5 as a standard sooner than later. This is a process that will still take some time but hey, the major streaming website like Youtube, Dailymotion and Vimeo no longer require Adobe at all. They are showing the way.

---

### Post by SeijiSensei on 2015-03-29
The Linux market is too small for Adobe to care. Flash only has a few more years of life anyway.

---

### Post by craig10x on 2015-03-29
I must say, html5 works very well on youtube which is what they use for the videos on there now...would sure like to see more sites have it...it's a great replacement for flash...

---

### Post by monkeybrain20122 on 2015-03-29
HTML5 has come a long way, but there are still some short comings on Youtube (not other sites such as Vimeo) Only Chrome has resolution >= 1080p if using html5 on Youtube, FF goes only to 720p max (with flash it can go above) A bug was filed on Mozilla a while back, not sure what its status is. At the moment the only option I know to watch 1080p or above on Youtube without flash and not using Chrome/Chromium(?) would be to use mpv with youtube-dl option set to bestvideo + bestaudio. 

Also HTML5 doesn't work on Youtube's 3d channel unless you have a recent Nvidia card (granted that not too many people would use this feature), but it works in flash even with my crappy intel card.

---

### Post by kurt18947 on 2015-03-30
I too haven't found many if any sites that complain about 11.2.xxxx flash. Perhaps some gaming sites are fussy. There is something under development that enables "pepper-flash" in Firefox. 

[http://www.webupd8.org/2015/01/fresh-player-plugin-sees-new-release.html](http://www.webupd8.org/2015/01/fresh-player-plugin-sees-new-release.html)

I do have a chromium install with pepper-flash installed. If a site misbehaves using Firefox, I try the same URL in chromium to see if flash 11.2.x is the problem. I don't recall one instance where Firefox didn't work but chromium using the newer flash version did. I think anyone who is clueful about Adobe, flash and security would like to see Flash disappear. For that to happen though, it seems like a LOT of web sites are going to have to be edited to replace their flash components. And for THAT to happen, web devs are going to have to learn alternatives.

---

### Post by Tar_Ni on 2015-04-02
> **kurt18947 said:**
> I too haven't found many if any sites that complain about 11.2.xxxx flash. Perhaps some gaming sites are fussy. There is something under development that enables "pepper-flash" in Firefox. 

[http://www.webupd8.org/2015/01/fresh-player-plugin-sees-new-release.html](http://www.webupd8.org/2015/01/fresh-player-plugin-sees-new-release.html)

I've finally decided to install the Fresh Player Plugin to enable pepperflash in Firefox and one thing I need to say: Wow!
This is amazing. All I did is installing the pepperflash-nonfree package in the Ubuntu Software Center and entered the command lines as prescribed in you link, to add the ppa and install the Fresh Player Plugin and it works perfectly.. and magically. I've now flash player 17 on my Firefox install! I've tried one site which no longer supports Flash 11.2 and hop you go, it played all the videos flawlessly.

One does not even to install Chrome or Chromium at all. Just the pepperflash-nonfree package.

These guys at webup8 deserve a lot of credits. I think they have come up with the best solution pending the death of adobe flash player. I am now free of the old flash plugin, which is all I asked.

I was hesitant at first, I didn't want to run into something buggy and unstable but version 0.2.3 works very well, I didn't encounter any problem so far. So I would say it's a solid beta. I strongly recommend people to make the switch now as it is safe and the most annoying bugs have been ironed out.

---

### Post by monkeybrain20122 on 2015-04-02
> **Tar_Ni said:**
> 
These guys at webup8 deserve a lot of credits. I think they have come up with the best solution pending the death of adobe flash player. I am now free of the old flash plugin, which is all I asked.
.

  I think a lot of credits should go to the developer too. :) [https://github.com/i-rinat/freshplayerplugin](https://github.com/i-rinat/freshplayerplugin) I have been using it on Fedora since F 20.


> One does not even to install Chrome or Chromium at all. Just the pepperflash-nonfree package. 

You can actually use any pepperflash source. e.g I have tried pepper flash extracted from a Chrome OS image following instructions from github (apparently it would work on DRM protected content too while the usual pepper flash on Linux Chrome wouldn't) But the problem is that only pepper flash from Chrome gets updated reliably along with Chrome(not sure about the pepper-flash non free package) It is important if you worry about security.

---

### Post by craig10x on 2015-04-03
Exactly...which is why i always say install Google Chrome not Chromium so you constantly get the LATEST UPDATED pepper flash...and know you will maintain your security...

---

### Post by SeijiSensei on 2015-04-03
I tried out the Freshplayer + pepperflash-nonfree solution.  It works quite well for unencumbered videos, but it won't play DRM-encumbered videos from Amazon Instant.  I can watch those in Firefox with **pipelight** which provides an interface to Microsoft Silverlight.  That works with Netflix as well.

---

### Post by Tar_Ni on 2015-04-03
> **monkeybrain20122 said:**
> You can actually use any pepperflash source. e.g I have tried pepper flash extracted from a Chrome OS image following instructions from github (apparently it would work on DRM protected content too while the usual pepper flash on Linux Chrome wouldn't) But the problem is that only pepper flash from Chrome gets updated reliably along with Chrome(not sure about the pepper-flash non free package) It is important if you worry about security.

That is an important thing people should know about: the pepperflash-nonfree package **is not updated automatically**.

What I do is that once every two weeks, I check for flash updates myself:

[FONT=Open Sans]sudo update-pepperflashplugin-nonfree  --status

And if there is a new flash version available:

[/FONT][FONT=Open Sans]sudo update-pepperflashplugin-nonfree  --install[/FONT]

As far as I am concerned, that's a very small inconvenient compared with the fact that I can now use my favorite browser (Firefox) with the latest flash version on Linux. :)

---

### Post by Tar_Ni on 2015-04-03
> **SeijiSensei said:**
> I tried out the Freshplayer + pepperflash-nonfree solution.  It works quite well for unencumbered videos, but it won't play DRM-encumbered videos from Amazon Instant.  I can watch those in Firefox with **pipelight** which provides an interface to Microsoft Silverlight.  That works with Netflix as well.

But isn't Mozilla actually working on it's own built-in DRM support? They were very reluctant at first to implement this closed-source feature, but had to concede this one or otherwise the Firefox browser would be shut out of most paid streaming services.

See: [URL="https://blog.mozilla.org/blog/2014/05/14/drm-and-the-challenge-of-serving-users/"]https://blog.mozilla.org/blog/2014/05/14/drm-and-the-challenge-of-serving-users/

[/URL]Now I am not exactly sure how that pertains to Pepperflash on Linux and  the Fresh Player Plugin, will that work when Mozilla release it's DRM  support?

---

### Post by monkeybrain20122 on 2015-04-03
> **SeijiSensei said:**
> I tried out the Freshplayer + pepperflash-nonfree solution.  It works quite well for unencumbered videos, but it won't play DRM-encumbered videos from Amazon Instant.  I can watch those in Firefox with **pipelight** which provides an interface to Microsoft Silverlight.  That works with Netflix as well.

According to this thread you can play DRM protected contents if you get pepper flash from a Chrome OS image instead of Chrome on Linux. [https://github.com/i-rinat/freshplayerplugin/issues/125](https://github.com/i-rinat/freshplayerplugin/issues/125) It is easy to switch between different copies of pepper flash by editing the line "Path to the Pepper Flash plugin" in the file .freshwrapper.conf (so you can use pepper flash in Chrome on non DRM videos because it is up to date)

Pipelight flash doesn't work as well as system flash and freshwrapper when all three work (start somewhat slower and buttons don't always work) An advantage of pipelight flash is that you can easily switch between system flash and pipelight flash with pipelight-plugin --enable/--disable flash. I think on Debian systems it may be able to implement something to switch between freshwrapper and system flash with update-alternatives..

---

### Post by monkeybrain20122 on 2015-04-03
> **Tar_Ni said:**
> But isn't Mozilla actually working on it's own built-in Adobe DRM support? They were very reluctant at first to implement this closed-source feature, but had to concede this one or otherwise the Firefox browser would be shut out of most paid streaming services.

See: [https://blog.mozilla.org/blog/2014/05/14/drm-and-the-challenge-of-serving-users/](https://blog.mozilla.org/blog/2014/05/14/drm-and-the-challenge-of-serving-users/)

Now I am not exactly sure how that pertains to Pepperflash on Linux and the Fresh Player Plugin, will that work when Mozilla release it's DRM support?

Mozilla's drm support will be for HTML5 streaming such as Netflix (This currently works only on Chrome. On FF you still need pipelight + silverlight) It has nothing to do with DRM streaming with flash. This is controversial because HTML5 is supposed to make the internet more open but the big media providers manage to subvert it by forcing DRM features on it. Mozilla is forced to play along or risks being shut out.

On Windows and Mac the flash plugins on FF (NAAPI) always works with DRM contents and I don't think it needs any support on Mozilla's part, flash is crippled like that only on Linux(same with pepper flash)  Hal used to work with system flash,--not for pepperflash,-- for such contents, not sure if that still works. Hal can be installed from ppa.

---

### Post by Tar_Ni on 2015-04-03
> **monkeybrain20122 said:**
> On Windows and Mac the flash plugins on FF (NAAPI) always works with DRM contents and I don't think it needs any support on Mozilla's part, flash is crippled like that only on Linux(same with pepper flash). Hal used to work with system flash,--not for pepperflash,-- for such contents, not sure if that still works. Hal can be installed from ppa.

Thanks. I am not exactly a user of these paid streaming services, hence my ignorance.

Hopefully they can all move to HTML5 players ASAP, that will save some troubles.

---

### Post by monkeybrain20122 on 2015-04-03
> **Tar_Ni said:**
> Thanks. I am not exactly a user of these paid streaming services, hence my ignorance.

Hopefully they can all move to HTML5 players ASAP, that will save some troubles.

Neither do I so I couldn't test whether freshplayer using pepper flash extracted from Chrome OS actually works on paid streaming sites. But I know these things because I was setting up Ubuntu for friends and I wanted to make sure their needs were met.

Paid HTML5 streaming will still be DRMed, but at least it will be cross platform and uniform so we don't need several versions of the same thing to work around platform discrimination.

---

### Post by SeijiSensei on 2015-04-04
> **monkeybrain20122 said:**
> Pipelight flash doesn't work as well as system flash and freshwrapper
I was talking about using pipelight as an interface to Microsoft Silverlight not as a method to use the Flash player for Windows.

Amazon Instant recently joined Netflix by choosing Silverlight as its preferred DRM streaming method, which is actually a better solution for Linux users.  To watch Amazon's DRM-encumbered Flash streams requires installing the [now-deprecated HAL interface]("http://www.amazon.com/forum/amazon%20video%20on%20demand/ref=cm_cd_t_rvt_np?_encoding=UTF8&cdForum=Fx3EQAX98ED5WQ3&cdPage=9&cdThread=Tx167YET6CH0PQI") on Linux.

---

### Post by monkeybrain20122 on 2015-04-04
> **SeijiSensei said:**
> I was talking about using pipelight as an interface to Microsoft Silverlight not as a method to use the Flash player for Windows.

Amazon Instant recently joined Netflix by choosing Silverlight as its preferred DRM streaming method, which is actually a better solution for Linux users.  To watch Amazon's DRM-encumbered Flash streams requires installing the [now-deprecated HAL interface]("http://www.amazon.com/forum/amazon%20video%20on%20demand/ref=cm_cd_t_rvt_np?_encoding=UTF8&cdForum=Fx3EQAX98ED5WQ3&cdPage=9&cdThread=Tx167YET6CH0PQI") on Linux.

I think Netflix is moving away from silverlight to HTML5 + DRM like you see in Chrome.

---

