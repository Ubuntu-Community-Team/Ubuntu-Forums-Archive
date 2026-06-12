---
title: "Firefox add-ons disabled and fail to download"
date: 2019-05-05
forum: Ubuntu, Linux and OS Chat
---

### Post by harry332 on 2019-05-05
This bug appeared on late 3rd May.
For example Firefox informed that the add-on uBlock is not supported and thus disabled.
At the same time you could not download any add-ons.

Here is a link to Mozilla page dealing with this issue:

[https://blog.mozilla.org/addons/2019/05/04/update-regarding-add-ons-in-firefox/comment-page-1/](https://blog.mozilla.org/addons/2019/05/04/update-regarding-add-ons-in-firefox/comment-page-1/)

---

### Post by dino99 on 2019-05-05
Discussion and link:
[https://www.phoronix.com/forums/forum/phoronix/latest-phoronix-articles/1096631-mozilla-had-a-rough-night-with-add-ons-getting-disabled-due-to-an-expired-certificate/page4](https://www.phoronix.com/forums/forum/phoronix/latest-phoronix-articles/1096631-mozilla-had-a-rough-night-with-add-ons-getting-disabled-due-to-an-expired-certificate/page4)

---

### Post by ajgreeny on 2019-05-05
*Thread moved to **Ubuntu, Linux and OS Chat**.* which is more appropriate and a better fit.

This is nothing to do with the development version but is because the certification of the whole add-ons system has lapsed, temporarily as far as anyone can say, so wait a while and it should resolve itself.

The problem is happening on all OSs of all types, Windows, Linux, Mac (I presume?).

---

### Post by Buntu Bunny on 2019-05-05
I'm having the same problem with all of my Firefox addons. All have disappeared and can't be downloaded again. Dino99, thanks for the link.

---

### Post by #&amp;thj^% on 2019-05-05
From mozilla.
> We rolled out a hotfix that re-enables affected add-ons. The fix will be automatically applied in the background within the next few hours. For more details, please check out the update at [https://support.mozilla.org/en-US/kb/add-ons-failing-install-firefox](https://support.mozilla.org/en-US/kb/add-ons-failing-install-firefox) 
We are working on a general fix that doesn&#8217;t use the Studies system and will keep this blog post updated accordingly.

We will share a more substantial update in the coming days. 
[https://support.mozilla.org/en-US/kb/add-ons-disabled-or-fail-to-install-firefox?redirectlocale=en-US&redirectslug=add-ons-failing-install-firefox](https://support.mozilla.org/en-US/kb/add-ons-disabled-or-fail-to-install-firefox?redirectlocale=en-US&redirectslug=add-ons-failing-install-firefox)

---

### Post by ajgreeny on 2019-05-05
I have no wish to enable studies and I think the easier way to work around this, if you have not already removed your extensions, is to go to **about:config** in the addressbar, search for and double click the **xpinstall.signatures.required** line to toggle it to false.

If the add-ons are all extensions you've been using for some time we can presumably assume they are trustworthy and not harmful, so this change should not add any extra security risks.  I believe this does not allow you to add any new extensions so DO NOT REMOVE any you still want to use, simply remove the certification requirement temporarily.

Once this mess is sorted by mozilla you can double click the xpinstall line again in **about:config** to toggle it back to true.

---

### Post by harry332 on 2019-05-06
Here is an update from Mozilla:

A fix has been released in Firefox version 66.0.4.
An update will be rolled out automatically with the latest fixes or you can [download]("https://www.mozilla.org/firefox/new/") a new version.

---

### Post by Rubi1200 on 2019-05-06
Latest release of 66.0.4 seems to have fixed the issue but have not tested yet on all my installations, but so far so good.

---

### Post by harry332 on 2019-05-06
The new FF version 66.0.4 is now available from Ubuntu official repos.
[https://launchpad.net/ubuntu/+source/firefox/66.0.4+build3-0ubuntu1](https://launchpad.net/ubuntu/+source/firefox/66.0.4+build3-0ubuntu1)

---

### Post by kesetyan on 2019-05-06
> **harry332 said:**
> The new FF version 66.0.4 is now available from Ubuntu official repos.
[https://launchpad.net/ubuntu/+source/firefox/66.0.4+build3-0ubuntu1](https://launchpad.net/ubuntu/+source/firefox/66.0.4+build3-0ubuntu1)

Normally I don't need to manually update Firefox in my Lubuntu 18.04 system, which dual boots with Windows 7, as software updates automatically.  

I became aware of the Firefox Addons problem for the first time this morning (Monday 06 May 2019) in Windows 7 but the browser updated automatically the next time I opened it and the Addons issue was immediately resolved.  Unfortunately this simple resolution in Windows 7 has not been repeated in Lubuntu where Firefox 66.0.3 steadfastly fails to update via the Software Updater despite the availability of the updated version in the Ubuntu official repository.  At the moment I am disinclined to manually download and install it in case I cause more problems.  What I have done, though, is install the Vivaldi browser, copy my Firefox bookmarks into it and set up my required addons, all of which, fortunately, were also available for Vivaldi.

It may be that I remove Firefox if I am entirely happy with Vivaldi, I'll see what happens over the next 24 hours or so.

---

### Post by Daveski17 on 2019-05-06
I've run the updater on Ubuntu 16.04 LTS but there has been no updates for Firefox. Should I just wait for an update?

---

### Post by #&amp;thj^% on 2019-05-06
Same here on 19.04, just wait they will get it out.

---

### Post by Daveski17 on 2019-05-06
Yeah, probably best just to wait it out. Good job I have Chrome lol.

---

### Post by harry332 on 2019-05-07
The Firefox 66.04 can be updated from the main server of the development branch Eoan Ermine.

---

### Post by Daveski17 on 2019-05-07
Is Canonical actually going to address this issue at all? Even Mozilla have fixed the problem. Is there anything I should do, apart from download a default browser that isn't broken?

---

### Post by PaulW2U on 2019-05-07
> **Daveski17 said:**
> Is Canonical actually going to address this issue at all?
Firefox 66.0.4 was built yesterday. It's being tested and as per the post previous to yours is currently available in Ubuntu's development version, Eoan Ermine so its release can be considered to be in progress.

For what it's worth, Fedora users don't yet have Firefox 66.0.4 either - it's currently being tested.

Patience.

---

### Post by Daveski17 on 2019-05-07
> **PaulW2U said:**
> Firefox 66.0.4 was built yesterday. It's being tested and as per the post previous to yours is currently available in Ubuntu's development version, Eoan Ermine so its release can be considered to be in progress.

For what it's worth, Fedora users don't yet have Firefox 66.0.4 either - it's currently being tested.

Patience.
OK thanks. I figured it was something like that. I have a second browser anyway. I just wondered if I needed to do anything specific. I reckon I can wait lol.

---

### Post by VMC on 2019-05-07
> **harry332 said:**
> This bug appeared on late 3rd May.
For example Firefox informed that the add-on uBlock is not supported and thus disabled.
...

Looks like 66.0.4 works according to comments , but I'm using 66.0.3 and have ublock working ok here.

---

### Post by ajgreeny on 2019-05-07
As a test I have just upgraded all my FF installs to 66.0.4 by using the firefox ppa (probably just for this hiatus period) and that is working properly, just as it should, without enabling studies or setting the xpinstall.signatures.required to false in about:config.

I am sure mozilla and/or Canonical will get that version to us in normal repos very quickly, but I simply wanted to try the ppa version for my own information, not as a recommendation for other users to follow.

---

### Post by poorguy on 2019-05-07
> **PaulW2U said:**
> Patience.

What! No Way! I gotta have it now.  

Perhaps a patch for impatience is available. ;)

---

### Post by Daveski17 on 2019-05-07
> **poorguy said:**
> what! No way! I gotta have it now.  

rotfl!

---

### Post by Daveski17 on 2019-05-08
Hurrah! :guitar:\\:D/

[ATTACH=CONFIG]283221[/ATTACH]

---

### Post by poorguy on 2019-05-08
Yep I received my*** FireFox 66.0.4*** update and installed my only add on*** ublock origin*** and all is working well. ;)

---

### Post by kesetyan on 2019-05-08
My Firefox problem was resolved today as well - all my previous settings and bookmarks were preserved and my add-ons are back on and working correctly.

Thanks to those concerned for your efforts in resolving this issue.

Cheers.

---

### Post by poorguy on 2019-05-08
Firefox Devs are on the ball. 

[https://www.mozilla.org/en-US/firefox/66.0.5/releasenotes/](https://www.mozilla.org/en-US/firefox/66.0.5/releasenotes/)

---

### Post by Daveski17 on 2019-05-08
You just beat me to posting the same link!

---

### Post by kesetyan on 2019-05-13
This morning (Monday 13 May 2019) the Software Updater in my Lubuntu 64 bit system successfully updated Firefox to version 66.0.5 - things seem to have got back to normal after the recent add-ons problems.

---

