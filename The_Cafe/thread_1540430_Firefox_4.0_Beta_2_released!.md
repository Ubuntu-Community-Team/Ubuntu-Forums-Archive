---
title: "Firefox 4.0 Beta 2 released!"
date: 2010-07-27
forum: The Cafe
---

### Post by lovinglinux on 2010-07-27
Firefox 4.0 Beta 2 is available for [download]("http://www.mozilla.com/en-US/firefox/beta/"). 

If you want to test it without interfering with your current Firefox installation or user profile, you can do it easily with my extension [FoxTester]("http://foxtester-extension.blogspot.com/"). Make sure you get the latest 1.0.5 version from [here]("http://foxtester-extension.blogspot.com") or [here]("https://addons.mozilla.org/en-US/firefox/addon/141505/versions/"), since this version is already compatible with Firefox 4.0b3pre.

If you like to do install it manually, then see Method #1 of the [[COLOR="Sienna"]**Installing Other Versions**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/installing-other-versions.html) tutorial.

If you are planning to make it your default browser, then be aware that most extensions won't work yet and you should not override compatibility check, otherwise they [could cause all sorts of problems]("http://ubuntuforums.org/showthread.php?t=1531119"), due to the extensive changes in Firefox extension API.

Don't forget that this version has a Feedback extension, that allow you to report what you like and don't like about Firefox 4. You can also see what others users are saying about it, along with some statistics. See [http://ubuntuforums.org/showthread.php?t=1535483](http://ubuntuforums.org/showthread.php?t=1535483).

More info about this release at [http://blog.mozilla.com/blog/2010/07/27/new-update-to-firefox-4-beta-available-now-in-23-languages/](http://blog.mozilla.com/blog/2010/07/27/new-update-to-firefox-4-beta-available-now-in-23-languages/)

---

### Post by RiceMonster on 2010-07-27
Just downloaded on Windows 7. On the last beta I got a white window for about 15 seconds before it loaded. It seems to be fixed now. Overall though, I like the direction they're going with this version.

---

### Post by lovinglinux on 2010-07-27
Thanks moderator for fixing the poll question.

---

### Post by nrs on 2010-07-27
[https://wiki.mozilla.org/Firefox/4/Beta#Firefox_4_Beta_FAQ](https://wiki.mozilla.org/Firefox/4/Beta#Firefox_4_Beta_FAQ)

> **Q: Why does Firefox look different than it used to?** A: We updated the default look of Firefox to make it easier to focus on  Web content and easier to control the tools in your Web browser. Also,  we think it&#8217;s prettier looking. This change is on _***Windows and Mac only.***_ Detailed blog posts explain what we did to streamline the interface and  why Tabs are on Top in Firefox 4. I will be greatly displeased if this isn't changed in the future. Not really surprised though. Linux has always been the red-headed step child of Firefox.

I'm not even going to touch the Direct2D debacle.

---

### Post by RiceMonster on 2010-07-27
Isn't the new interface the big change for Firefox 4? So will there really be much of a change if the new interface doesn't show up on Linux?

---

### Post by lovinglinux on 2010-07-27
> **nrs said:**
> [https://wiki.mozilla.org/Firefox/4/Beta#Firefox_4_Beta_FAQ](https://wiki.mozilla.org/Firefox/4/Beta#Firefox_4_Beta_FAQ)

I will be greatly displeased if this isn't changed in the future. Not really surprised though. Linux has always been the red-headed step child of Firefox.

I'm not even going to touch the Direct2D debacle.

[http://www.mozilla.com/en-US/firefox/beta/features/](http://www.mozilla.com/en-US/firefox/beta/features/)

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=164721&stc=1&d=1280277191[/IMG]

> **RiceMonster said:**
> Isn't the new interface the big change for Firefox 4? So will there really be much of a change if the new interface doesn't show up on Linux?

The interface changes are not restricted to the theme. For instance the [Add-ons manager]("http://www.oxymoronical.com/blog/2010/07/Introducing-the-new-Add-ons-Manager") is completely new, there are [application tabs]("http://www.youtube.com/watch?v=55PnjIfC6cw") now, tabs can be placed on top/bottom of other toolbars and no longer appear after the sidebar, but over it.

There are other important changes not related to style, like the introduction of [WebM]("http://blog.pearce.org.nz/2010/07/webm-video-support-in-firefox-4-beta.html") support, performance improvements, a new [Web Developer Console]("http://daviddahl.blogspot.com/2010/07/web-developer-console-in-firefox-40.html"), Retained layers that allows to scroll complex pages faster and [other features]("http://www.mozilla.com/en-US/firefox/beta/features/").

---

### Post by Stancel on 2010-07-27
They didn't include the new default theme in the Linux version. 

I sent them a polite note about it using the Feedback tool.

---

### Post by nrs on 2010-07-27
> **lovinglinux said:**
> [..]("http://www.mozilla.com/en-US/firefox/beta/features/")
Nice. What about the performance disparity? Accelerated rendering?

---

### Post by Dustin2128 on 2010-07-27
mozilla should seriously shape up its treatment and support of the linux community, else I foresee many major distros swapping to chromium in the future. I barley use windows outside of school now, but I notice an extreme difference in speed on the two OSes, windows-firefox coming out far on top (assuming the windows machine isn't riddled with malware). In fact, if I recall correctly, there was a benchmark conducted a while back that showed the windows version of firefox in wine outperforming the linux native version on the same machine, quite disturbing. Chromium and opera, however, are consistently blazing fast on all platforms.

---

### Post by lovinglinux on 2010-07-27
> **nrs said:**
> Nice. What about the performance disparity? Accelerated rendering?

This is on 32bit. The 64bit version performs 10% better here.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=164738&stc=1&d=1280282552[/IMG]

---

### Post by 23meg on 2010-07-27
> **nrs said:**
> Accelerated rendering?

[http://weblogs.mozillazine.org/roc/archives/2010/07/retained_layers.html](http://weblogs.mozillazine.org/roc/archives/2010/07/retained_layers.html)

---

### Post by nrs on 2010-07-27
> **lovinglinux said:**
> This is on 32bit. The 64bit version performs 10% better here.

I mean the Windows, Mac, Linux performance disparity. The Windows version is miles ahead of either.

---

### Post by lovinglinux on 2010-07-27
> **nrs said:**
> I mean the Windows, Mac, Linux performance disparity. The Windows version is miles ahead of either.

Well, I have no idea. Honestly, I don't care that much, the same way I don't care about Chrome and Opera speeds. As long as Firefox works well for me and keep improving on every release, I'm fine with it :)

I'm not unhappy with 3.6.8, but 4.0b2 seems faster when rendering pages and chrome content. I have to consider that a clean profile is not the same as my regular profile, which usually has about 60-70 extensions enabled.

---

### Post by Old Marcus on 2010-07-28
I keep getting this error when trying to run Firefox Beta 2 downloaded from mozilla.

exec: 398: /home/bal/Programs/firefox/firefox-bin: not found

Yet I look in the folder and ta-daa! It's there. What's going on?

---

### Post by lovinglinux on 2010-07-28
> **Old Marcus said:**
> I keep getting this error when trying to run Firefox Beta 2 downloaded from mozilla.

exec: 398: /home/bal/Programs/firefox/firefox-bin: not found

Yet I look in the folder and ta-daa! It's there. What's going on?

How do you installed and how are you launching it?

---

### Post by Old Marcus on 2010-07-28
I extracted it from the tar.bz2 file and run the firefox executable from the terminal.

---

### Post by lovinglinux on 2010-07-28
> **Old Marcus said:**
> I extracted it from the tar.bz2 file and run the firefox executable from the terminal.

Have you checked the tar hash? See [CheckIt]("https://addons.mozilla.org/en-US/firefox/addon/127758/").

---

### Post by zekopeko on 2010-07-28
> **nrs said:**
> [https://wiki.mozilla.org/Firefox/4/Beta#Firefox_4_Beta_FAQ](https://wiki.mozilla.org/Firefox/4/Beta#Firefox_4_Beta_FAQ)

I will be greatly displeased if this isn't changed in the future. Not really surprised though. Linux has always been the red-headed step child of Firefox.

I'm not even going to touch the Direct2D debacle.

Linux market share of the Firefox pie is in single digits. It makes sense to put emphasis on the Windows version.

> **Stancel said:**
> They didn't include the new default theme in the Linux version. 

I sent them a polite note about it using the Feedback tool.

> **nrs said:**
> Nice. What about the performance disparity? Accelerated rendering?

> **Dustin2128 said:**
> mozilla should seriously shape up its treatment and support of the linux community, else I foresee many major distros swapping to chromium in the future. I barley use windows outside of school now, but I notice an extreme difference in speed on the two OSes, windows-firefox coming out far on top (assuming the windows machine isn't riddled with malware). In fact, if I recall correctly, there was a benchmark conducted a while back that showed the windows version of firefox in wine outperforming the linux native version on the same machine, quite disturbing. Chromium and opera, however, are consistently blazing fast on all platforms.

This is to all of you complaining about the lack of the new theme in FF. You can thank that one to technological limitations and fragmentation of the Linux platform.

[https://bugzilla.mozilla.org/show_bug.cgi?id=513159](https://bugzilla.mozilla.org/show_bug.cgi?id=513159)

I bet the same applies to the Direct2D thing.

---

### Post by gradinaruvasile on 2010-07-28
Hm. Then how Chrome/Chromium and Opera is so fast? On all platforms...

---

### Post by nilarimogard on 2010-07-28
> **Old Marcus said:**
> I keep getting this error when trying to run Firefox Beta 2 downloaded from mozilla.

exec: 398: /home/bal/Programs/firefox/firefox-bin: not found

Yet I look in the folder and ta-daa! It's there. What's going on?

Did you run the "firefox" executable or "firefox-bin"? You have to double click the "firefox" file and it should work.

---

### Post by nrs on 2010-07-28
> **zekopeko said:**
> L
This is to all of you complaining about the lack of the new theme in FF. You can thank that one to technological limitations and fragmentation of the Linux platform.

Oh, BS. Chrome has done it just fine since forever. It's not a hard thing to do. Especially in Qt. As far as Direct2D, they could've opted for OpenGL, a solution which would've worked on all their target platforms. Their rationale for choosing Direct2D was along the lines of OpenGL on Windows is poor / unsupported. Which is BS. Windows supports 1.4 at the minimum and both ATI and nVidia support the latest incarnation.

FFS, excluding all the professional apps that use it, iD uses OpenGL for all their games on Windows, and they aren't exactly known for their poor quality.

Blaming X, Linux, et. all for Firefox's poor performance is also a non-starter. When run using WINE, performance is near equivalent to Windows. WINE of course uses X, Linux, et all.

---

### Post by Pogeymanz on 2010-07-28
I love the direction Firefox is going. I started to lose faith around the time that Opera 10.60 came out, but Firefox 4 is fantastic.

There is a huge performance increase in addition to the UI redesign(long overdue, IMO).

In fact, I'm using the nightly build of Beta 3 right now and it's even faster than Beta 2! At this point, I don't care about benchmarks because my pages load just as fast in Firefox as Chromium or Opera (sometimes faster) and that is with all my favorite addons that make Firefox more customized to my web-surfing style than Opera or Chromium can be.

Not to mention, FOSS is awesome and Google sometimes worries me.

On a related note, what is the point of an app tab? Just so you don't accidentally close it and it doesn't take up a lot of space?

EDIT: I do agree with the sentiment that Mozilla needs to give us some more love. I don't mind that we get features and functions later than the other platforms (hey, supply and demand), but I do mind that our browser is ALWAYS SLOWER.

---

### Post by spoons on 2010-07-28
> **nrs said:**
> Oh, BS. Chrome has done it just fine since forever. It's not a hard thing to do. Especially in Qt. As far as Direct2D, they could've opted for OpenGL, a solution which would've worked on all their target platforms. Their rationale for choosing Direct2D was along the lines of OpenGL on Windows is poor / unsupported. Which is BS. Windows supports 1.4 at the minimum and both ATI and nVidia support the latest incarnation.

FFS, excluding all the professional apps that use it, iD uses OpenGL for all their games on Windows, and they aren't exactly known for their poor quality.

Blaming X, Linux, et. all for Firefox's poor performance is also a non-starter. When run using WINE, performance is near equivalent to Windows. WINE of course uses X, Linux, et all.

Most people don't use ATi or NVIDIA. They use Intel - who quite frankly suck at writing good OpenGL drivers. Direct2D is guaranteed to work on all of the remotely modern GPUs out there. I don't think OpenGL is very good at 2D stuff anyway. I seem to remember than OpenGL acceleration wasn't used for the OpenTTD game project because it's hacky and annoying to get it to work. (I am not sure if this is true)

---

### Post by lovinglinux on 2010-07-28
> **Pogeymanz said:**
> In fact, I'm using the nightly build of Beta 3 right now and it's even faster than Beta 2! At this point, I don't care about benchmarks because my pages load just as fast in Firefox as Chromium or Opera (sometimes faster) and that is with all my favorite addons that make Firefox more customized to my web-surfing style than Opera or Chromium can be.

+1  =D>

I'm using Beta 2 right now, because I have too many extensions and I don't want to force compatibility of those that I don't need, so I can easily track which extensions are fully functional and which are not. I still can't make 12 extensions to work that are important for me, but I think I won't go back to 3.6 now.

> **Pogeymanz said:**
> On a related note, what is the point of an app tab? Just so you don't accidentally close it and it doesn't take up a lot of space?

I think the idea is that they are automatically loaded when you start the browser, so are always available, without occupying much space. They are very buggy tho. They keep floating from their original position and sometimes overlap with the first tab, depending how you interact with it.

> **RiceMonster said:**
> Isn't the new interface the big change for Firefox 4? So will there really be much of a change if the new interface doesn't show up on Linux?

Except for the menu in the Windows version, I don't see a reason to get too much excited with the new UI in Linux. Unlike "the other browser" :), Firefox is extremely customizable. For instance, take a look at the attached screenshots, comparing my Firefox new look with a Windows version. 

Before anyone comment, I have huge toolbars, because one of the extensions I use to shrink and move the menu to another toolbar, so I can hide the one on the top, is not working yet. Additionally, the toolbar below the search bar has no icons, but I left it opened because I like some space between the toolbars and the content. I don't have any application tabs. Those on the left side of the tabs are extension icons and some default buttons.

The theme I'm using are in fact for the Windows version of Firefox 4 :) If you want to try it, the name of the theme is [QSQ]("https://addons.mozilla.org/en-US/firefox/addon/162069/"). Use it at your own risk. You will need to override the compatibility check to make it work. You can do that with [Add-on Compatibility Reporter]("https://addons.mozilla.org/en-US/firefox/addon/15003/"). Be careful tho, specially if you have many extensions, since overriding compatibility will also make all extensions active, which might even break Firefox completely. So if you override compatibility check, start Firefox in safe mode and disable all extensions. Then enable one by one carefully, always restarting after enabling each extension and checking if there are any errors on the "Error Console" (CTRL+Shift+J).

I t was about time to change my Firefox look. I was using Chromifox theme for too long.

---

### Post by nrs on 2010-07-28
> **spoons said:**
>  I don't think OpenGL is very good at 2D stuff anyway. I seem to remember than OpenGL acceleration wasn't used for the OpenTTD game project because it's hacky and annoying to get it to work. (I am not sure if this is true)
I don't think it is true. I use it extensively. 2D in OpenGL is as simple as calling glOrtho and glBlank2x instead of 3. 

I can't speak for the quality of Intel's OpenGL implementation in Windows, but it seems adequate in Linux and good enough for Apple to have used it as it's chipset for a time.

---

### Post by lovinglinux on 2010-07-28
Here is a new benchmark, comparing Firefox 4 Beta 2 with 3.6.8. The interesting detail is that 3.6.8 is using a clean profile, while 4.0 has 34 extensions installed, 1 theme designed for Windows and thousands of bookmarks.

[IMG]http://guide.ubuntuforums.org/attachment.php?attachmentid=164790&stc=1&d=1280330795[/IMG]

---

### Post by webtechquery on 2010-07-28
Hi..

A good and easy way to download Firefox 4 Beta 2 could be found in the following link:

[http://www.webtechquery.com/index.php/2010/07/firefox-4-beta-2-ubuntu-firefox-4-beta-2-linux/](http://www.webtechquery.com/index.php/2010/07/firefox-4-beta-2-ubuntu-firefox-4-beta-2-linux/)

Thanks

---

### Post by zekopeko on 2010-07-28
> **nrs said:**
> Oh, BS. Chrome has done it just fine since forever. It's not a hard thing to do. Especially in Qt. As far as Direct2D, they could've opted for OpenGL, a solution which would've worked on all their target platforms. Their rationale for choosing Direct2D was along the lines of OpenGL on Windows is poor / unsupported. Which is BS. Windows supports 1.4 at the minimum and both ATI and nVidia support the latest incarnation.

FFS, excluding all the professional apps that use it, iD uses OpenGL for all their games on Windows, and they aren't exactly known for their poor quality.

Blaming X, Linux, et. all for Firefox's poor performance is also a non-starter. When run using WINE, performance is near equivalent to Windows. WINE of course uses X, Linux, et all.

Did you even read the bug report I linked to?
Chrome does it but it doesn't still fit in nicely into the system theme and that includes window buttons. Also why do you mention Qt since Mozilla isn't targeting that platform on Linux? Funny thing is that for Firefox to implement the mockup it would need to use client-side-decorations which are opposed by KDE Kwin folk.

This comment pretty much sums it up: [https://bugzilla.mozilla.org/show_bug.cgi?id=513159#c14](https://bugzilla.mozilla.org/show_bug.cgi?id=513159#c14)

---

### Post by speedwell68 on 2010-07-28
I'll wait until the final is out.

---

### Post by Pogeymanz on 2010-07-28
> **speedwell68 said:**
> I'll wait until the final is out.

You're missing out!

Still, a few of my addons aren't working, but as long as the big ones (NoScript and Adblock) work, I'll be patient.

---

### Post by lovinglinux on 2010-07-28
Anyone  experiencing weird page rendering when scrolling? Sometimes when I scroll a page the content does not refresh properly, creating a series of ghost  images overlapped.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=164856&stc=1&d=1280364905[/IMG]

---

### Post by ElSlunko on 2010-07-28
I am. Have to highlight all to clear it up.

---

### Post by lovinglinux on 2010-07-28
> **ElSlunko said:**
> I am. Have to highlight all to clear it up.

I also noticed if you open the panel menu it clear it up too.

---

### Post by lovinglinux on 2010-07-28
I'm alos experiencing issues with overlays. For instance when I click an image preview on an extension page at Mozilla site, the lightbox should cover everything, but Firefox' logo and other stuff still remain.

---

### Post by Pogeymanz on 2010-07-28
> **lovinglinux said:**
> Anyone  experiencing weird page rendering when scrolling? Sometimes when I scroll a page the content does not refresh properly, creating a series of ghost  images overlapped.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=164856&stc=1&d=1280364905[/IMG]

I've got the same stuff. It's been in Beta 2 for a while.

---

### Post by Lucradia on 2010-07-28
> **Pogeymanz said:**
> I've got the same stuff. It's been in Beta 2 for a while.

Ive had the same stuff since 3.5 on all video cards.

---

### Post by lovinglinux on 2010-07-31
See the revolution of tab browsing coming with Firefox 4!

[http://ubuntuforums.org/showthread.php?t=1542777](http://ubuntuforums.org/showthread.php?t=1542777)

---

### Post by ArionKrause on 2010-09-18
> **Old Marcus said:**
> I keep getting this error when trying to run Firefox Beta 2 downloaded from mozilla.

exec: 398: /home/bal/Programs/firefox/firefox-bin: not found

Yet I look in the folder and ta-daa! It's there. What's going on?


I went through this exactly issue when trying to run Firefox 4.0b6 on Ubuntu 10.04 x64...

As it did work on another Ubuntu (32 bits) right out-of-the-box, I thought it could be something about x64 architeture, so I did a research and found this link: [https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit) which recommends to install **ia32-libs** package in order to execute x86 code.

It worked like a charm for me, so you might give it a try.


Step-by-step:
1. Open a terminal and run **sudo apt-get install ia32-libs** (41.4 MB total size).
2. Extract the contents of the last Firefox beta you've downloaded (**firefox-4.0b6.tar.bz2** is the last beta as today, and may be different at the time you're reading this) to a folder of you desire.
3. Run **firefox** from that folder (either by double-clicking on it or running from a terminal, i.e. **/home/you/firefox/firefox**).

---

