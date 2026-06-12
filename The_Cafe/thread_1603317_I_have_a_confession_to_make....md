---
title: "I have a confession to make..."
date: 2010-10-22
forum: The Cafe
---

### Post by lovinglinux on 2010-10-22
I have been playing with Opera 11 alpha since the day of this post and I'm really enjoying it :confused:

The main reason for trying it again is that Opera now supports extensions, although they are not like XUL extensions of Firefox, but widgets based on the W3C specifications like Chrome and Mozilla's Jetpacks. So, they probably won't replace some functionalities I get with Firefox's XUL extensions.

Nevertheless, I must admit that I have, for the first time, configured Opera to my linking and imported bookmarks, feeds, mails, search engines and other stuff. I never had interest on doing that before. 

So far I like these:

[LIST]
[*]built-in speed dial (easier to use, although not very configurable)
[*]built-in mail reader (there was a Simple Mail extension for Firefox, but is defunct since Firefox Beta 1 was released)
[*]built-in rss reader (the one I like for Firefox is not compatible with Firefox 4 and I really want the feeds on the sidebar)
[*]built-in irc client (I used ChatZilla in Firefox, but it didn't open as a new tab, only new window)
[*]built-in support for stylish scripts (easier to manage in my opinion)
[*]per site preferences (really nice)
[*]skin installer and skins availability
[*]the ability to add web pages as sidebar panels (Firefox also opens sites in the sidebar, but from bookmarks)
[*]the ability to set toolbars and tabs positions to top,bottom,left or right (in Firefox I use Tree Style Tabs extension, but I can't move toolbars)
[*]built-in functionality to add new search engines (Add to Search Bar extension in Firefox)
[*]the search highlight feature (awesome)
[*]the notes system, which allows to copy from selected test on a page and paste to a form (simpler than Firefox extensions I used)
[*]the interface is gorgeous
[/LIST]

Things I don't like so far:

[LIST]
[*]too many menu options and no way to edit them
[*]no support for OPML import [[[COLOR="Red"]solved[/COLOR]]("http://ubuntuforums.org/showpost.php?p=10012666&postcount=18")]
[*]cannot middle-click on a link in the bookmarks bar to open it on a new tab [[[COLOR="#ff0000"]solved[/COLOR]]("http://ubuntuforums.org/showpost.php?p=10011840&postcount=2")]
[*]cannot open search results in a new tab [[[COLOR="#ff0000"]solved[/COLOR]]("http://ubuntuforums.org/showpost.php?p=10011840&postcount=2")]
[*]searches are tied to pages in display
[*]some sites I need are rendered completely wrong [[[COLOR="#ff0000"]solved[/COLOR]]("http://ubuntuforums.org/showpost.php?p=10012115&postcount=9")]
[*]cannot move extensions icons to a better position or different toolbars [[[COLOR="Red"]solved[/COLOR]]("http://ubuntuforums.org/showpost.php?p=10012589&postcount=16")]
[*]some pages take a lot of time to load [[[COLOR="Red"]solved[/COLOR]]("http://ubuntuforums.org/showpost.php?p=10012629&postcount=17")]
[*]cannot view saved passwords [[[COLOR="#ff0000"]solved[/COLOR]]("http://ubuntuforums.org/showpost.php?p=10012421&postcount=13")]
[*]smooth scrolling is not so smooth (fixed on latest alpha)
[*]torrent download doesn't seem to work [[[COLOR="Red"]solved[/COLOR]]("http://ubuntuforums.org/showpost.php?p=10012745&postcount=22")]
[*]I can't drag links from Opera to Firefox or other browser
[*]no way to sync bookmarks with Firefox
[*]is not open source
[*]cannot make screenshots of entire pages
[/LIST]

Perhaps some Opera users are willing to help me to solve those problems...I know, I probably don't deserve it :)

**EDIT:** after solving most of the problems with the help provided below and after exploring the browser features, I must admit this is an awesome browser. I guess my fanboyism and laziness were preventing me from exploring it appropriately and giving the credit it definitely deserves. I'm currently running Opera and Firefox simultaneously, using Opera as primary browser and Firefox only for development. I'm also starting to port some of the extensions I develop to Opera.

---

### Post by Canis familiaris on 2010-10-22
> **lovinglinux said:**
> 
[*]cannot open search results in a new tab

Shift + Enter
> 
[*]searches are tied to pages in display

I prefer that way to be honest.
> 
[*]some sites I need are rendered completely wrong

Those Web Site should check their compatibility with Opera. :| Opera IS a standards compliant browser
> 
[*]some pages take a lot of time to load (I'm not interested in turbo mode)

You'll be interested on a dial up and EDGE connection. :p

> 
[*]torrent download doesn't seem to work

That is weird. The in built Torrent client of Opera works for me.

> 
[*]no way to sync bookmarks with Firefox

For syncing bookmarks use Opera Link. It's Opera only though. However you can import your links from Firefox, I think.

I am mostly a Chromium user, but just few words. :)

---

### Post by lovinglinux on 2010-10-22
> **Canis familiaris said:**
> Shift + Enter

Thanks, that helps a lot. 

> **Canis familiaris said:**
> Those Web Site should check their compatibility with Opera. :| Opera IS a standards compliant browser

Not an options :) Perhaps is my Opera settings. Can anyone see this right:

[http://terratv.terra.com.br](http://terratv.terra.com.br)

This is how it's rendered here:

Firefox/Opera

[IMG]http://goo.gl/H9Xg[/IMG]  [IMG]http://goo.gl/mwhZ[/IMG]

> **Canis familiaris said:**
> You'll be interested on a dial up and EDGE connection. :p

My connection is fine. 

> **Canis familiaris said:**
> For syncing bookmarks use Opera Link. It's Opera only though. However you can import your links from Firefox, I think.

Thanks, but that wouldn't solve the problem of using both browsers. I guess I will have to wait for an Xmarks extension, if they really don't close for good.

---

### Post by Canis familiaris on 2010-10-22
Hmm weird. Looks fine to me in Opera.
[[IMG]http://jpeghoster.com/images/03569049975593057817_thumb.jpg[/IMG]](http://jpeghoster.com/viewer.php?file=03569049975593057817.png)

I think you have Opera Turbo Enabled. Disable it.

---

### Post by lovinglinux on 2010-10-22
> **Canis familiaris said:**
> Hmm weird. Looks fine to me in Opera.
[[IMG]http://jpeghoster.com/images/03569049975593057817_thumb.jpg[/IMG]](http://jpeghoster.com/viewer.php?file=03569049975593057817.png)

I think you have Opera Turbo Enabled. Disable it.

Is not enabled. I have disabled both Opera Turbo and Unite service.

---

### Post by Canis familiaris on 2010-10-22
Try a fresh copy of settings, mv ~/.opera ~/.opera.bak and re-run Opera. It's definitely something to do with your settings.

---

### Post by lovinglinux on 2010-10-22
> **Canis familiaris said:**
> Try a fresh copy of settings, mv ~/.opera ~/.opera.bak and re-run Opera. It's definitely something to do with your settings.

Yep, that was my next step and it worked, but I want to keep my profile.

Edit: the problem is in operaprefs.ini

---

### Post by Canis familiaris on 2010-10-22
Judging by those arrows instead of expected flash video in your screenshot, I can only think of Opera Turbo.
By Default Opera Turbo is Automatic mode, which means it is disabled but gets enabled during traffic. Do double check if Opera Turbo is set to Off and not Automatic.
Apart from that I have no idea.

And, oh just noticed this:
> cannot right-click on a link in the bookmarks bar to open it on a new tab
You mean the Bookmarks bar you enabled right? You can middle-click to open them in a new tab.

---

### Post by lovinglinux on 2010-10-22
> **Canis familiaris said:**
> Judging by those arrows instead of expected flash video in your screenshot, I can only think of Opera Turbo.
By Default Opera Turbo is Automatic mode, which means it is disabled but gets enabled during traffic. Do double check if Opera Turbo is set to Off and not Automatic.
Apart from that I have no idea.

I have triple checked it. It wasn't enable. Nevertheless, the problem seems to be solved with a clean *operaprefs.ini* file. I'm configuring it all over again, but testing to see which settings are affecting that page.

I also had to download flash square preview 2, because the stable version was crashing the browser 100% after watching the video for a few seconds.

> **Canis familiaris said:**
> And, oh just noticed this:

You mean the Bookmarks bar you enabled right? You can middle-click to open them in a new tab.

Yes, is the bookmark bar I have enabled and that you can drag bookmarks and bookmarks folders without changing the original order in the bookmarks sidebar.

I meant middle-click (already corrected in my first post), but still doesn't work. I can middle-click in the sidebar bookmarks and speed dial. Address bar, search bar and bookmarks bar only work with Shift+left-click.

---

### Post by froghopper on 2010-10-22
Page looks fine to me in 10.70 but you seem to have fixed that and torrenting works fine, just tried it

Opera RSS Feed List &#8644; OPML Converter
[http://nontroppo.org/tools/opml/]("http://nontroppo.org/tools/opml/")

Editing Opera Menus (hands dirty in test files stylee)
[http://my.opera.com/Tamil/blog/edit-menu-setup]("http://my.opera.com/Tamil/blog/edit-menu-setup")
and incidentally the goto site for opera knowledge

Perhaps Opera extensions will allow an integrated bookmark sync with firefox, but the opera unite was one thing that won me over to opera, it seemed to be far easier and neater than the various add-on attempts with firefox.

---

### Post by lovinglinux on 2010-10-22
> **froghopper said:**
> Opera RSS Feed List &#8644; OPML Converter
[http://nontroppo.org/tools/opml/]("http://nontroppo.org/tools/opml/")

Already tried that, but it doesn't seem to work. It seems to covert, but then what? Do I need to access my feeds from Opera site or am I missing something?

> **froghopper said:**
> Editing Opera Menus (hands dirty in test files stylee)
[http://my.opera.com/Tamil/blog/edit-menu-setup]("http://my.opera.com/Tamil/blog/edit-menu-setup")
and incidentally the goto site for opera knowledge

Thanks for that.

There is another problem, a serious one in fact. It seems there is no way to see the saved passwords using the built-in password manager. Nevertheless, the various Opera sites keep asking me to login on each of them, but the wand only detects My Opera site. So how am I supposed to copy a password from on site to another? I tried a bookmarklet, but it doesn't seem to work. 

This is a show stopper for me.

---

### Post by Quadunit404 on 2010-10-22
> **lovinglinux said:**
> [LIST]
[*]the built-in quick dial (easier to use, although not very configurable)


You mean the Speed Dial? You can configure it through ~/.opera/speeddial.ini. Just go down to the bottom and you'll see [Size], which lets you set your own custom Speed Dial size.

Opera is known for being highly configurable, even if some options are less obvious than others :wink:

---

### Post by lovinglinux on 2010-10-22
> **Quadunit404 said:**
> You mean the Speed Dial? You can configure it through ~/.opera/speeddial.ini. Just go down to the bottom and you'll see [Size], which lets you set your own custom Speed Dial size.

Opera is known for being highly configurable, even if some options are less obvious than others :wink:

Yes. The configuration options are not very rich like Speed Dial for Firefox, but that is not an important issue anyway.

BTW, I figured it out how to display the password, using [PowerButtons]("http://operawiki.info/PowerButtons"). I like it the idea of adding buttons for specific purposes. It doesn't matter if is a button, an extension or a widget, as long as it does the job without hassle.

---

### Post by mainerror on 2010-10-22
> **lovinglinux said:**
> 
[LIST]
[*][COLOR="Red"]cannot make screenshots of entire pages[/COLOR]
[/LIST]

Hold on. There is an extension fro doing this in FF or Chromium?! :o

If so please tell me its name.

---

### Post by lovinglinux on 2010-10-22
> **mainerror said:**
> Hold on. There is an extension fro doing this in FF or Chromium?! :o

If so please tell me its name.

Firefox 3.6 [https://addons.mozilla.org/en-US/firefox/addon/1146/](https://addons.mozilla.org/en-US/firefox/addon/1146/)
Firefox 4 [https://addons.mozilla.org/en-US/firefox/addon/9924/](https://addons.mozilla.org/en-US/firefox/addon/9924/)

There are others, but those are the ones I use.

---

### Post by lovinglinux on 2010-10-22
> **lovinglinux said:**
> 
[LIST]
[*]cannot move extensions icons to a better position or different toolbars
[/LIST]

Solved this one by adding a wrapper menu item before the extensions buttons, so now they are displayed in a new row. Awesome.

---

### Post by lovinglinux on 2010-10-22
> **lovinglinux said:**
> 
[LIST]
[*]some pages take a lot of time to load (I'm not interested in turbo mode)[/LIST]

For some reason I forgot to disable ipv6 in grub and since this is disabled in my Firefox config, I didn't noticed. Seems to be fixed for now.

---

### Post by lovinglinux on 2010-10-22
> **froghopper said:**
> Opera RSS Feed List &#8644; OPML Converter
[http://nontroppo.org/tools/opml/]("http://nontroppo.org/tools/opml/")

Thanks. I was in fact using another tool that wasn't working properly. Now I know what to do with the incoming.txt :)

---

### Post by sisco311 on 2010-10-22
> **lovinglinux said:**
> 
torrent download doesn't seem to work


Check the log file (~/.opera/bittorent.log). If you are behind a firewall, you have to set the listen port in [opera:config](opera:config).

---

### Post by mainerror on 2010-10-22
> **lovinglinux said:**
> Firefox 3.6 [https://addons.mozilla.org/en-US/firefox/addon/1146/](https://addons.mozilla.org/en-US/firefox/addon/1146/)
Firefox 4 [https://addons.mozilla.org/en-US/firefox/addon/9924/](https://addons.mozilla.org/en-US/firefox/addon/9924/)

There are others, but those are the ones I use.

Nice! Thanks.

If anyone is interested in a chromium extension for this then check this out.

[https://chrome.google.com/extensions/detail/alelhddbbhepgpmgidjdcjakblofbmce?hl=en](https://chrome.google.com/extensions/detail/alelhddbbhepgpmgidjdcjakblofbmce?hl=en)

---

### Post by lovinglinux on 2010-10-22
> **sisco311 said:**
> Check the log file (~/.opera/bittorent.log). If you are behind a firewall, you have to set the listen port in [opera:config](opera:config).


Thanks, but I have already done that. The torrent didn't start even with the firewall disabled. I suppose the same problem that was affecting the layout of some pages and installed extensions could be affecting torrent. I haven't tried again, but will do in a minute.

BTW, I couldn't find the [BitTorrent] section in the *operaprefs.ini*. I need to manipulate the port via config file, because I have a script that controls moblock, iptables and my other torrent clients.

---

### Post by lovinglinux on 2010-10-22
> **lovinglinux said:**
> Thanks, but I have already done that. The torrent didn't start even with the firewall disabled. I suppose the same problem that was affecting the layout of some pages and installed extensions could be affecting torrent. I haven't tried again, but will do in a minute.

BTW, I couldn't find the [BitTorrent] section in the *operaprefs.ini*. I need to manipulate the port via config file, because I have a script that controls moblock, iptables and my other torrent clients.

It's fixed. I guess the old *operaprefs.ini* was corrupted somehow, because I couldn't find which settings were causing all those troubles.

---

### Post by lovinglinux on 2010-10-22
> **lovinglinux said:**
> BTW, I couldn't find the [BitTorrent] section in the *operaprefs.ini*. I need to manipulate the port via config file, because I have a script that controls moblock, iptables and my other torrent clients.

Solved that too. The [BitTorrent] section is showing in the config now.

Do you know if the Opera torrent has UPnP support? I couldn't find anything about it and the port doesn't seem to be forwarded automatically.

---

