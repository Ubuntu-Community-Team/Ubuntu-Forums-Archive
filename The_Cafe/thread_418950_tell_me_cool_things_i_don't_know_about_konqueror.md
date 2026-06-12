---
title: "tell me cool things i don't know about konqueror"
date: 2007-04-22
forum: The Cafe
---

### Post by fuscia on 2007-04-22
i'm going through another phase of kde nuthuggery and have been stumbling across stuff in konqueror i hadn't known before. i'm sure there's a bunch of stuff i don't even know to look for, so hit me with glory.

---

### Post by Bloodfen Razormaw on 2007-04-22
My favorite hidden trick: You can create completely customized sidebars.  I use one which combines bookmarks, browser history, root and home folder tree sidebars into one.  Since I didn't need multiple sidebar tabs anymore, you can also hide that sidebar tab bar.

---

### Post by picpak on 2007-04-22
The best trick: stick a CD in, type audiocd:/ in the address bar, and hit enter. From here you have OGGs, MP3s, WAVs, FLACs, Full Album, etc. of the CD you put in!

---

### Post by jariku on 2007-04-22
When I used KDE, I liked the fish://-ioslave that you can use for file transfer over SSH. It doesn't require an sftp server, so it's more likely to work. :)

---

### Post by KiwiNZ on 2007-04-22
> **fuscia said:**
> i'm going through another phase of kde nuthuggery and have been stumbling across stuff in konqueror i hadn't known before. i'm sure there's a bunch of stuff i don't even know to look for, so hit me with glory.
 
May help to list what features and benefits you know about and then folks can fill in the blanks.

---

### Post by fuscia on 2007-04-22
> **KiwiNZ said:**
> May help to list what features and benefits you know about and then folks can fill in the blanks.

there's nothing in particular. it's just an overall astonishment at how many things i stumble upon.

---

### Post by %hMa@?b&lt;C on 2007-04-22
bluetooth:\ 
gets your bluetooth devices! (excellent for wiimote!)

---

### Post by me1on on 2007-04-23
Here are a couple things that I like about Konqueror:

Mouse gestures similar to the ones in Opera. Just go to System Settings (in KDE obviously)-> Accessibility-> Input Actions-> Click Konqueror Gestures-> Uncheck the "Disable" checkbox. You can also make new gestures.

Search-as-you type. Just type the "/" key then whatever you need to find on the page.

Built-in Konsole. You can assign a keyboard shortcut to open up a built-in Konsole (default is F8 in Kubuntu). If you are using Konqueror as a file manager, it automatically cd's to the current directory.

Bookmarklets. In Konqueror, you might have noticed "bookmarklets" (Javascript bookmarks; For example, I have an "add to del.icio.us" bookmarklet in Konqueror) don't work. They actually do, but they are called "minitools" in Konqueror. Just go to Tools-> Minitools-> Edit Minitools and add your bookmarklets.

Selection Filter. If you go Edit-> Selection-> Select in file browsing mode, you can select all files that match a regular expression. For example, M*.ogg selects all ogg files whose filename starts with the letter "M."

Ad Blocking. You probably already knew this one. Just go to Tools-> Configure Konqueror-> AdBlocK-> Enable.

That's all I can think of off the top of my head.

---

### Post by Bloodfen Razormaw on 2007-04-23
> Selection Filter. If you go Edit-> Selection-> Select in file browsing mode, you can select all files that match a regular expression. For example, M*.ogg selects all ogg files whose filename starts with the letter "M."
In addition, you can get a display filter by entering the expression in the location bar, e.g. ~/Audio/M*.ogg will display the Audio directory but with only matching files.  Also, you can use Ctrl+F to get an embedded search dialog, no need for opening a separate search window.  It's an embedded kfind with all the same functionality, and combines with Konqueror's ability to browse in tar/zip/gzip/etc. archives like they were folders to get results in them.

---

### Post by igknighted on 2007-04-23
In desktopBSD there is a mouse-gestures feature for konqueror already there.  I haven't seen it on any linux yet, but I only found it on DesktopBSD last week so I've only tried on Kubuntu and Fedora7.

---

### Post by GeneralZod on 2007-04-23
You can re-arrange tabs my *middle-click* dragging.  Took me ages to realise that :)

Not Konqueror-specific, but the full set of protocols/ kio_slaves supported by your KDE install can be obtained via kinfocenter -> Protocols.

---

### Post by floke on 2007-04-23
It came first in my highly scientific browser speed test :( 

(actually :(  since I use Firefox)

[http://ubuntuforums.org/showthread.php?t=340042](http://ubuntuforums.org/showthread.php?t=340042)

---

### Post by dspari1 on 2007-04-23
Pros:
1. It passes the Acid2 test
2. Best Linux flash compatibility
3. You can spoof the browser's id to various browsers
4. KMplayer plugin can switch between Xine and Mplayer engines for compatibility
5. Loads fast since it's already loaded with the OS

Cons: 
1. No official Googlebar; I'm using the 3rd party "Google Suggest Bar" that I had to compile from source
2. Konqueror will many times try to open binary files with kate instead of giving you the option of downloading. (Workaround: right click -> save as)

Enclosed: Acid2 test results

---

### Post by awakatanka on 2007-04-23
> **dspari1 said:**
> 
2. Konqueror will many times try to open binary files with kate instead of giving you the option of downloading. (Workaround: right click -> save as)

Enclosed: Acid2 test resultsIts a Kubuntu config error. I don't have this problem on other kde centric distro's. 



Is there a plugin that save my bookmarks to a website so i can load them on any linux install i use? Like [https://addons.mozilla.org/en-US/firefox/addon/2410](https://addons.mozilla.org/en-US/firefox/addon/2410) ??

Btw here some good info and tips [http://en.opensuse.org/Konqueror_Tips_and_Tricks](http://en.opensuse.org/Konqueror_Tips_and_Tricks)

ctrl mousewheel to make letters bigger and smaller

---

### Post by dspari1 on 2007-04-23
> **awakatanka said:**
> Its a Kubuntu config error. I don't have this problem on other kde centric distro's. 



Is there a plugin that save my bookmarks to a website so i can load them on any linux install i use? Like [https://addons.mozilla.org/en-US/firefox/addon/2410](https://addons.mozilla.org/en-US/firefox/addon/2410) ??

Btw here some good info and tips [http://en.opensuse.org/Konqueror_Tips_and_Tricks](http://en.opensuse.org/Konqueror_Tips_and_Tricks)

do you know a fix?

---

### Post by Bloodfen Razormaw on 2007-04-23
> In desktopBSD there is a mouse-gestures feature for konqueror already there. I haven't seen it on any linux yet, but I only found it on DesktopBSD last week so I've only tried on Kubuntu and Fedora7.
That's in every distro.  Someone brought it up earlier in this thread: KDE provides mouse gestures for ALL applications; it's not just a Konqueror-specific feature.  DesktopBSD probably tweaks KDE by default to have them on, but upstream KDE turns gestures off by default.  You can enable them in the Control Center->Regional and Accessibility->Input Actions.  Make sure you have a non-zero timeout for mouse gestures too.

---

### Post by fuscia on 2007-04-23
you guys probably already know about this page - [http://wiki.kde.org/tiki-index.php?page=Hidden%20configuration](http://wiki.kde.org/tiki-index.php?page=Hidden%20configuration)

so far, i've only done the middle-click to close tabs thing. works great.

---

### Post by TheRingmaster on 2007-04-23
if you type /. in the address bar, it will automagically go to slashdot.

EDIT: no wait. that is for opera not konqueror sorry

---

### Post by Trail on 2008-02-07
> **GeneralZod said:**
> You can re-arrange tabs my *middle-click* dragging.  Took me ages to realise that :)

Not Konqueror-specific, but the full set of protocols/ kio_slaves supported by your KDE install can be obtained via kinfocenter -> Protocols.

omg, thank you!

---

