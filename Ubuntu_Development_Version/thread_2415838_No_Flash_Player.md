---
title: "No Flash Player?"
date: 2019-04-01
forum: Ubuntu Development Version
---

### Post by ping-wu on 2019-04-01
As entitled.  Running Google Chrome.  Adobe Flash Player grayed out.

---

### Post by Frogs Hair on 2019-04-01
Doesn't Chrome install it's own version of flash with the browser ? Where is it grayed out ?

---

### Post by ping-wu on 2019-04-01
This question was originally posted in a Chinese language based Ubuntu forum.

I followed all the right procedures to play flash in Chrome/19.04 but to no avail.

The same flash clip played OK in 18.04.2.

---

### Post by ping-wu on 2019-04-02
> **Frogs Hair said:**
> Doesn't Chrome install it's own version of flash with the browser ? Where is it grayed out ?

In Chrome, I was prompted to allow flash plugin (which is part of Chrome), but nothing happened.  Then I right-clicked the flash clip, all the "options" are grayed out.  Again, no problem in 18.04.2.

---

### Post by #&amp;thj^% on 2019-04-02
Unfortunately, there is no way to permanently enable the plugin in Chrome; it&#8217;s blocked by default. But you can make it work temporarily for whole websites and individual pieces of Flash content.

Select the padlock in the URL bar, (See Screenshot) Bear in mind that this will enable Flash across the entire website, not just for specific content. 

If you don&#8217;t fancy enabling Flash across a whole website and instead just want to view certain Flash content like animations and games, you can just enable Flash Player for those particular pieces of content. Just select the grey box which reads Click to enable Adobe Flash Player. You&#8217;ll then be given a notification pop-up to confirm the action. Select Allow, and you&#8217;re good to go.
EDIT: You will have to refresh (Alt+F5) the page after making the change.  (chrome://settings/content/flash)
Can you post the site url with the non playing flash content?

---

### Post by ping-wu on 2019-04-03
> **1fallen said:**
> Unfortunately, there is no way to permanently enable the plugin in Chrome; it’s blocked by default. But you can make it work temporarily for whole websites and individual pieces of Flash content.

Select the padlock in the URL bar, (See Screenshot) Bear in mind that this will enable Flash across the entire website, not just for specific content. 

If you don’t fancy enabling Flash across a whole website and instead just want to view certain Flash content like animations and games, you can just enable Flash Player for those particular pieces of content. Just select the grey box which reads Click to enable Adobe Flash Player. You’ll then be given a notification pop-up to confirm the action. Select Allow, and you’re good to go.
EDIT: You will have to refresh (Alt+F5) the page after making the change.  (chrome://settings/content/flash)
Can you post the site url with the non playing flash content?

Believe me, I have tried everything.:P

Two example url's (both are in Chinese):

 [http://www.fecm.cn/index.html](http://www.fecm.cn/index.html)
 
[https://www.qq.com/](https://www.qq.com/)

qq.com is one of the most popular web sites in China.

---

### Post by Frogs Hair on 2019-04-03
I see the same with Opera which is Chromium based like Google Chrome. Run this Plug-in Fails.


Edit: With Firefox I see a enable DRM which allows me to play video, there is no Option in Chromium based Opera.

---

### Post by #&amp;thj^% on 2019-04-03
Stuff like this just blows me away, as to why it works for some and not others.
Both of those links works here in Chrome.

---

### Post by sunnyboy1 on 2019-04-04
I have exactly the same problem with the PPAPI Flashplayer plugin in chrome, chromium, vivaldi and opera. Grayed out and no function. NPAPI and Firefox works.

---

### Post by ping-wu on 2019-04-05
I tested the same flash clip/url on Fedora 30 beta/Firefox, had to install Adobe flash player plugin, was asked to give permission, but once given, Firefox crashed.

---

### Post by Frogs Hair on 2019-04-05
I tried Opera from Windows and Flash works though I get promoted to install the ten cent video player application for the NBA videos.Firefox has no such prompt and plays the videos. You can see this prompt in one of 1fallen's screenshots.

---

### Post by #&amp;thj^% on 2019-04-12
Try it now with firefox >> and I installed this time "flashplugin-installer"
```
apt policy flashplugin-installer
flashplugin-installer:
  Installed: 32.0.0.171ubuntu1
  Candidate: 32.0.0.171ubuntu1
  Version table:
 *** 32.0.0.171ubuntu1 500
        500 http://archive.ubuntu.com/ubuntu disco/multiverse amd64 Packages
        100 /var/lib/dpkg/status

```
Wish I could figure out what is different about my install and those here that are having problems playing the vids from those sites. :(
```
System:
  Host: me-ThinkPad-T430 Kernel: 5.1.0-050100rc2-lowlatency x86_64 bits: 64 
  Desktop: Gnome 3.32.0 Distro: Ubuntu 19.04 (Disco Dingo) 
Graphics:
  Device-1: Intel 3rd Gen Core processor Graphics driver: i915 v: kernel 
 ** Display: wayland server: X.Org 1.20.4 driver: modesetting **
  unloaded: fbdev,vesa resolution: 1600x900~60Hz, 1920x1080~60Hz 
  OpenGL: renderer: Mesa DRI Intel Ivybridge Mobile v: 4.2 Mesa 19.0.2 

```
EDIT: Brave Browser will not work though.

---

### Post by visylar on 2019-04-14
I got the same problem as you.  Installed PPAPI even though I think chrome doesn't depends on it.  Now Flash content works in Firefox but Chrome only shows a grey background with a darker grey plugin icon on its button right corner.

---

### Post by zuti on 2019-04-15
Same here. Two systems. Flash is enabled for site in Chrome, but the browser just blocks it every time. Made using Adobe Connect quite difficult.

---

### Post by sunnyboy1 on 2019-04-15
I have written down the error messages from chrome here

VM54:1 Uncaught TypeError: Cannot read property 'style' of null
    at showFallbackSkipBtn (<anonymous>:1:71)
showFallbackSkipBtn @ VM54:1
swfmousewheel.js?__cv=bc957abb90dc553f46a72256ebbd2b00:1 [Intervention] Unable to preventDefault inside passive event listener due to target being treated as passive. See [https://www.chromestatus.com/features/6662647093133312](https://www.chromestatus.com/features/6662647093133312)
d @ swfmousewheel.js?__cv=bc957abb90dc553f46a72256ebbd2b00:1
h @ swfmousewheel.js?__cv=bc957abb90dc553f46a72256ebbd2b00:1
swfmousewheel.js?__cv=bc957abb90dc553f46a72256ebbd2b00:1 Uncaught TypeError: Cannot read property 'externalMouseEvent' of null
    at HTMLDocument.h (swfmousewheel.js?__cv=bc957abb90dc553f46a72256ebbd2b00:1)
h @ swfmousewheel.js?__cv=bc957abb90dc553f46a72256ebbd2b00:1
swfmousewheel.js?__cv=bc957abb90dc553f46a72256ebbd2b00:1 [Intervention] Unable to preventDefault inside passive event listener due to target being treated as passive. See [https://www.chromestatus.com/features/6662647093133312](https://www.chromestatus.com/features/6662647093133312)

---

### Post by #&amp;thj^% on 2019-04-24
As of today 4-24-2019 it no longer works with>>Version 74.0.3729.108 (Official Build) beta (64-bit)
Seems it's just for those two sites, so far that I can find anyway.

---

### Post by sunnyboy1 on 2019-04-26
This has nothing to do with the version.
The PPAPI plugin did not work on Xubuntu 19.04 at all, neither with Chrome nor with chromium or vivaldi browser. It is a javascript error. At xubuntu 18.10 every browser works with the same settings.

---

### Post by alterra on 2019-04-30
hello,
i have the same issue with ubuntu 19.04, is there any information for a patch to solve this issue? 
bye

---

### Post by sunnyboy1 on 2019-05-01
[https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1825497](https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1825497)

---

### Post by slickymaster on 2019-05-02
19.04 is already released.

Thread closed.

---

