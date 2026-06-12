---
title: "Freaking Firefox 3.6.4pre!"
date: 2010-04-12
forum: The Cafe
---

### Post by madhi19 on 2010-04-12
Last update for Firefox Namaroka firefox 3.6.7pre this morning broke it any sugestion on how to reverse it one version and still keep my settings!

---

### Post by Excedio on 2010-04-12
> **madhi19 said:**
> Last update for Firefox Namaroka firefox 3.6.7pre this morning broke it any sugestion on how to reverse it one version and still keep my settings!
 
Let me guess... It freezes up on page load?

---

### Post by wojox on 2010-04-12
What are you running nightly builds or did you download the tar.bz2 for the site?

---

### Post by Excedio on 2010-04-12
Check this out...
 
[http://ubuntuforums.org/showthread.php?t=1451736](http://ubuntuforums.org/showthread.php?t=1451736)

---

### Post by lovinglinux on 2010-04-12
Your setting will not be lost, since they are stored under a Firefox profile in your home directory, under ~/.mozilla/firefox and are used by most Firefox versions.

About the problem, see quote below:

> **lovinglinux said:**
> **[SIZE="4"]Attention Firefox 3.6.4 [Namoroka] ubuntu-mozilla-daily users![/SIZE]**

It seems this is a bug affecting only Firefox 3.6.4 [Namoroka] installed using the *ubuntu-mozilla-daily* ppa. The browser crashes when viewing pages with flash content or content for other plugins.

This problem is due to a bad/old implementation of the new Lorentz technology that should prevent flash from crashing the browser. When opening a page with flash content using Namoroka 3.6.4, there is a new *firefox-bin* process loaded and the browser crashes. 

[Firefox 3.6.4 Lorentz from Mozilla](http://www.mozilla.com/en-US/firefox/lorentz/) doesn't behave like this and instead of loading a new *firefox-bin* process, it loads a *mozilla-runtime* process, which takes care of the flash content. It works like a charm and the browser doesn't crash or lock, even if you are viewing a messed up flash video.

So you have 3 options to fix your problem:

[LIST]
[*]disable *ubuntu-mozilla-daily* and reinstall Firefox to downgrade it to the default browser version
[*]temporarily turn off the flash process isolation following [these instructions](http://ubuntuforums.org/showpost.php?p=9104945&postcount=19)
[*]download [Firefox 3.6.4 Lorentz from Mozilla](http://www.mozilla.com/en-US/firefox/lorentz/) and follow [these instructions](http://lovinglinux.megabyet.net/?page_id=220##1---Manual-installation-of-fresh-final-releases-from-Mozilla-3) to install it.
[/LIST]

There are some considerations about using a ppa repository for Firefox that I would like to highlight:
[LIST]
[*]some ppa repositories like *ubuntu-mozilla-daily* update not only Firefox, but also other Mozilla applications, like Thunderbird.
[*]some ppa repositories like ubuntu-mozilla-daily install development versions of Firefox which does not have the official branding (logo and name). Although they use essentially the same source code, the browser could be called Shiretoko, Namoroka or something else.
[*] some repositories like *mozillateam/firefox-stable* doesn&#8217;t seem to be updated frequently, thus missing important security patches.
[*]some repositories like *ubuntu-mozilla-daily* upgrade Firefox with unstable releases, sometimes causing issues, like crashing the browser in specific conditions or preventing it from starting.
[/LIST]

Please Before adding a ppa repository for Firefox, please make sure you understand how the repository works, which version it will install and how often it will provide updates.[color="Sienna"][list]

[*]**Source:** [[color="DarkSlateGray"] Re: Firefox optimization and troubleshooting thread[/color]]("http://ubuntuforums.org/showpost.php?p=9112875")

[*]**Tags:** [[color="DarkSlateGray"]Firefox optimization and troubleshooting thread[/color]]("http://www.google.com/search?q=Firefox+optimization+and+troubleshooting+thread+site:ubuntuforums.org")

[*]**Powered by: **[[color="DarkSlateGray"]QuoteMarks[/color]]("http://lovinglinux.megabyet.net/?page_id=555")[/list][/color]

---

### Post by LinuXGo on 2010-04-13
Thanks LovingLinux, I have the same problem with the 3.6.4pre and I've installed swiftfox for alternative to firefox. Yesterday I can't seem to identify the problem because it can't play any flash content and it frustrates me, now that its resolved, I shall test it out to see: giving my result later. Thanks again for the post! :)

---

