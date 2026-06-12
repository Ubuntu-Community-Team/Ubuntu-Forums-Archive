---
title: "Doesn't work past reboot"
date: 2007-04-30
forum: Ubuntuzilla
---

### Post by pacanukeha on 2007-04-30
Hi,
My install always succeeds, but after a reboot I can no longer retrieve email. An uninstall and a reboot and a reinstall solves the problem.  Quit/restart within the same session as the initial install works.

A successful install for me requires a copy of tb1.5 or nothing at boot time.

(Successfull install -> quit -> reload ) will succeed
(Successfull install -> reboot -> fail -> uninstall -> use tb1.5 -> reinstall ) will fail
(Successfull install -> reboot -> fail -> uninstall -> reboot -> reinstall ) will succeed

It doesn't seem to send the username/password to my POP3/S server.  I initially had a master password and it would never pop-up the request to enter it.

This makes me a sad panda.

Using feisty, up-to-date, with some 3rd party repositories (Automatix2, Medibuntu, Canonical Archive Commercial)

Any ideas?  Should I post it to the mozillazine forums or bugzilla?

---

### Post by nanotube on 2007-04-30
> **pacanukeha said:**
> Hi,
My install always succeeds, but after a reboot I can no longer retrieve email. An uninstall and a reboot and a reinstall solves the problem.  Quit/restart within the same session as the initial install works.

A successful install for me requires a copy of tb1.5 or nothing at boot time.

(Successfull install -> quit -> reload ) will succeed
(Successfull install -> reboot -> fail -> uninstall -> use tb1.5 -> reinstall ) will fail
(Successfull install -> reboot -> fail -> uninstall -> reboot -> reinstall ) will succeed

It doesn't seem to send the username/password to my POP3/S server.  I initially had a master password and it would never pop-up the request to enter it.

This makes me a sad panda.

Using feisty, up-to-date, with some 3rd party repositories (Automatix2, Medibuntu, Canonical Archive Commercial)

Any ideas?  Should I post it to the mozillazine forums or bugzilla?

heh wow, what a strange thing. 
i would suggest you try to rename your profile (~/.thunderbird) out of the way, let the new thunderbird create a fresh profile, recreate your email accounts, and then see if that solves the "reboot and fail" problem. if so, that's great, because we track the problem down to something in your profile. (then you could try moving the email archives from your old profile into the new one, and see if everything is still ok). 

if not, then... well, let's talk about it when we get there. :)

---

### Post by pacanukeha on 2007-04-30
Erm, okay, I'll try that.  My default profile is mounted on a r/w NTFS partition (so I can dual-boot).    I wonder if TB2 is using different system file routines.

---

### Post by pacanukeha on 2007-04-30
Right.  That seems to work, for a minimal set of work.  I created another profile under TB1.5, installed TB2, rebooted, and it was able to d/l messages.  So the issue is either in the NTFS bit or something to do with 2 gigs of mail & RSS entries.

Any suggestions as to where to next?

---

### Post by nanotube on 2007-04-30
> **pacanukeha said:**
> Right.  That seems to work, for a minimal set of work.  I created another profile under TB1.5, installed TB2, rebooted, and it was able to d/l messages.  So the issue is either in the NTFS bit or something to do with 2 gigs of mail & RSS entries.

Any suggestions as to where to next?

well, start moving your mail/rss archives in one by one, until you hit which one of them was giving you problems...

---

### Post by pacanukeha on 2007-04-30
It is definitely the extensions.  I renamed my extensions folder and it works now.
Next step, rename the ext folders one by one.  Yikes - there are 47 of them!

---

### Post by nanotube on 2007-04-30
> **pacanukeha said:**
> It is definitely the extensions.  I renamed my extensions folder and it works now.
Next step, rename the ext folders one by one.  Yikes - there are 47 of them!

haha, 47 extensions in t-bird? it's a wonder it runs at all! heh.

seriously though, what extensions do you have on there? maybe there are some good ones i don't know about?

all i've got is webmail+hotmail, so i don't have to use their crappy web interface for a hotmail account that i don't really use, but wanna check just in case. :)

---

### Post by pacanukeha on 2007-05-01
Sure - of course, not all of them are active since they are not 2.0 compatible.  I trimmed a few just now.  Some may no longer be relevant in the 2.0 world, but since the authors have taen the time to make them compatible that is unlikely -

Enabled Extensions: [23]
- Adblock Plus 0.7.2.4: [http://adblockplus.org/](http://adblockplus.org/)
- Buttons! 0.5.3.1: [http://www.chuonthis.com/extensions/](http://www.chuonthis.com/extensions/)
- Canadian English Dictionary 1.1.0: [http://www2.cs.uregina.ca/~schmpaul/firefox/](http://www2.cs.uregina.ca/~schmpaul/firefox/)
- Correct Identity 1.3.1: [http://www.google.com/search?q=Thunderbird%20Correct%20Identity](http://www.google.com/search?q=Thunderbird%20Correct%20Identity)
- Display mail route 0.2.2: [http://www.cweiske.de/misc_extensions.htm#mailroute](http://www.cweiske.de/misc_extensions.htm#mailroute)
- Empty Trash 1.3.11: [http://www.tom-cat.com/mozilla/](http://www.tom-cat.com/mozilla/)
- Enigmail 0.95.0: [http://enigmail.mozdev.org/](http://enigmail.mozdev.org/)
- header scroll extension 0.3.2: [http://www.cweiske.de/misc_extensions.htm#headerScroll](http://www.cweiske.de/misc_extensions.htm#headerScroll)
- Lightning 0.3.1: [http://www.mozilla.org/projects/calendar/releases/lightning0.3.1.html](http://www.mozilla.org/projects/calendar/releases/lightning0.3.1.html)
- Mail Redirect 0.7.4: [http://mailredirect.mozdev.org](http://mailredirect.mozdev.org)
- Mailbox Alert 0.12: [http://jelte.nlnetlabs.nl](http://jelte.nlnetlabs.nl)
- MR Tech Local Install 5.3.2.3: [http://www.mrtech.com/extensions/local_install/](http://www.mrtech.com/extensions/local_install/)
- No New Window on Double Click 0.2.3: [http://www.chuonthis.com/extensions/](http://www.chuonthis.com/extensions/)
- Provider for Google Calendar 0.1.1: [http://mozilla.kewis.ch/](http://mozilla.kewis.ch/)
- Remember Mismatched Domains 1.3.4: [http://www.andrewlucking.com](http://www.andrewlucking.com)
- SearchWith 0.3: [http://searchwith.mozdev.org](http://searchwith.mozdev.org)
- Sender Verification Extension 0.8.2.1: [http://razor.occams.info/code/spf](http://razor.occams.info/code/spf)
- Show Address 0.0.4: [http://www.moritz-abraham.de/](http://www.moritz-abraham.de/)
- Signature Switch 1.4.3: [http://mozext.achimonline.de](http://mozext.achimonline.de)
- Talkback 2.0.0.0: [http://talkback.mozilla.org/](http://talkback.mozilla.org/)
- View Headers Toggle Button 2.0.1: [http://joshandmerci.com/proj_thunder.php](http://joshandmerci.com/proj_thunder.php)
- ViewSourceWith 0.0.9: [http://dafizilla.sourceforge.net/viewsourcewith](http://dafizilla.sourceforge.net/viewsourcewith)
- Virtual Identity 0.4.0: [http://absorb.it/hacked/thunderbird/v_identity.html](http://absorb.it/hacked/thunderbird/v_identity.html)

Disabled Extensions: [4]
- Advanced Remove Duplicates 0.5: [http://www.moritz-abraham.de](http://www.moritz-abraham.de)
- Lightning Multiweek View 0.0.2: [http://jminta.googlepages.com/cal-extras](http://jminta.googlepages.com/cal-extras)
- MboxImport 0.5.3: [https://nic-nac-project.de/~kaosmos/index-en.html](https://nic-nac-project.de/~kaosmos/index-en.html)
- Unselect Message 1.3: [http://www.google.com/search?q=Thunderbird%20Unselect%20Message](http://www.google.com/search?q=Thunderbird%20Unselect%20Message)

Total Extensions: 27

Installed Themes: [2]
- Crossover X 2.3: [http://www.google.com/search?q=Thunderbird%20Crossover%20X](http://www.google.com/search?q=Thunderbird%20Crossover%20X)
- Thunderbird (default): [http://www.mozilla.org/](http://www.mozilla.org/)

---

### Post by nanotube on 2007-05-01
thanks for the list. it will take me a while to go through that. 

btw, i forgot that i also have enigmail. so make that 3 extensions for me, currently. :)

---

### Post by pacanukeha on 2007-05-01
I think if I listed my FF extensions you would have a heart attack so I will keep that quiet :)

---

### Post by nanotube on 2007-05-01
btw, from the "all headers button" extension website, i saw this:
> IMPORTANT NOTE for users upgrading from versions prior to the 1.5.0 release: due to a flaw in the Thunderbird installer please uninstall the old version of the extension and restart Thunderbird before installing the new version.

so maybe that's the one causing the trouble?

edit: so, i went through your list, and i found one that i think is really cool: virtual identity. it always bugged me that i have to create a whole account to have an alternate 'from' address. nice. :)

---

### Post by nanotube on 2007-05-01
> **pacanukeha said:**
> I think if I listed my FF extensions you would have a heart attack so I will keep that quiet :)

actually, i'd appreciate a list of those as well. :) i've only got 9 (and happy with them), but if i see something cool, i might add to my meager collection. :)

---

### Post by pacanukeha on 2007-05-01
I'm a web developer, so many of them are geared around that kind of thing, but here you go:

Generated: Tue May 01 2007 09:11:13 GMT-0400 (EDT)
User Agent: Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.3) Gecko/20061201 Firefox/2.0.0.3 (Ubuntu-feisty)
Build ID: 2007040314

Enabled Extensions: [47]
- About This Site Bookmarks 1.5: [http://ginatrapani.org/workshop/firefox/aboutsite/](http://ginatrapani.org/workshop/firefox/aboutsite/)
- Adblock Plus 0.7.5: [http://adblockplus.org/](http://adblockplus.org/)
- Add N Edit Cookies 0.2.1.2: [http://addneditcookies.mozdev.org/](http://addneditcookies.mozdev.org/)
- All-in-One Gestures 0.18.0: [http://perso.wanadoo.fr/marc.boullet/ext/extensions-en.html](http://perso.wanadoo.fr/marc.boullet/ext/extensions-en.html)
- All-in-One Sidebar 0.7.1: [http://firefox.exxile.net/aios/](http://firefox.exxile.net/aios/)
- Beagle Indexer 0.6: [http://beagle-project.org](http://beagle-project.org)
- BugMeNot 1.3: [http://roachfiend.com](http://roachfiend.com)
- Canadian English Dictionary 1.1.0: [http://www2.cs.uregina.ca/~schmpaul/firefox/](http://www2.cs.uregina.ca/~schmpaul/firefox/)
- Clear Cache Button 0.5: [http://clearcachebutton.mozdev.org](http://clearcachebutton.mozdev.org)
- Console² 0.3.7: [http://console2.mozdev.org/index.html](http://console2.mozdev.org/index.html)
- Context Search 0.4.1: [http://www.cusser.net](http://www.cusser.net)
- Deepest Sender 0.8.0: [http://deepestsender.mozdev.org/](http://deepestsender.mozdev.org/)
- del.icio.us Complete 1.3: [http://delicious.mozdev.org/](http://delicious.mozdev.org/)
- DiggiDig 0.43: [http://www.google.com/search?q=Firefox%20DiggiDig](http://www.google.com/search?q=Firefox%20DiggiDig)
- Fasterfox 2.0.0: [http://fasterfox.mozdev.org/](http://fasterfox.mozdev.org/)
- Firebug 1.05: [http://www.getfirebug.com/](http://www.getfirebug.com/)
- Firefly 0.2.2: [http://firefly.mozdev.org/](http://firefly.mozdev.org/)
- Hyperwords(tm) 2.3.1: [http://www.hyperwords.net](http://www.hyperwords.net)
- IE View Lite 1.3: [http://www.graysonmixon.com/extension/](http://www.graysonmixon.com/extension/)
- InspectThis 0.2.9: [http://firefox.mackay-it.com/extensions/inspectthis/](http://firefox.mackay-it.com/extensions/inspectthis/)
- JavaScript Debugger 0.9.87: [http://www.hacksrus.com/~ginda/venkman/](http://www.hacksrus.com/~ginda/venkman/)
- JSView 1.2.9: [http://forum.softwareblaze.com](http://forum.softwareblaze.com)
- Link Alert 0.7.2: [http://conlan89.googlepages.com/](http://conlan89.googlepages.com/)
- Live HTTP Headers 0.13.1: [http://livehttpheaders.mozdev.org/](http://livehttpheaders.mozdev.org/)
- Map+ 1.1.0: [http://www.usaflightinsurance.com](http://www.usaflightinsurance.com)
- MeasureIt 0.3.6: [http://www.kevinfreitas.net/pro/extensions/](http://www.kevinfreitas.net/pro/extensions/)
- MR Tech Local Install 5.3.2.3: [http://www.mrtech.com/extensions/local_install/](http://www.mrtech.com/extensions/local_install/)
- NoScript 1.1.4.8.070423: [http://noscript.net](http://noscript.net)
- Nuke Anything 0.2: [http://ted.mielczarek.org/code/mozilla/](http://ted.mielczarek.org/code/mozilla/)
- OperaView 0.6: [http://operaview.mozdev.org/](http://operaview.mozdev.org/)
- PDF Download 0.8: [http://www.pdfdownload.org](http://www.pdfdownload.org)
- Permit Cookies 0.6.2: [http://mfe.gorgias.de/](http://mfe.gorgias.de/)
- Popup ALT Attribute 1.3.2005092701: [http://piro.sakura.ne.jp/xul/_popupalt.html.en](http://piro.sakura.ne.jp/xul/_popupalt.html.en)
- Professor X 0.4.1: [http://www.designmeme.com/professorx/](http://www.designmeme.com/professorx/)
- Remember Mismatched Domains 1.3.4: [http://www.andrewlucking.com](http://www.andrewlucking.com)
- Resurrect Pages 1.0.7: [http://trac.arantius.com/wiki/Extensions/Resurrect](http://trac.arantius.com/wiki/Extensions/Resurrect)
- SafeCache 0.9: [http://www.safecache.com/](http://www.safecache.com/)
- ScrapBook 1.2.0.8: [http://amb.vis.ne.jp/mozilla/scrapbook/](http://amb.vis.ne.jp/mozilla/scrapbook/)
- Screen grab! 0.93: [http://andy.5263.org/screengrab/](http://andy.5263.org/screengrab/)
- Searchbar Autosizer 1.3.6: [http://searchbarautosizer.mozdev.org/](http://searchbarautosizer.mozdev.org/)
- SearchWP 1.0: [http://legege.com/mozilla/](http://legege.com/mozilla/)
- Tab Mix Plus 0.3.5.2: [http://tmp.garyr.net](http://tmp.garyr.net)
- Tamper Data 9.8.1: [http://tamperdata.mozdev.org](http://tamperdata.mozdev.org)
- URL Link 2.00.3: [http://www.fnxweb.com/software-mozilla](http://www.fnxweb.com/software-mozilla)
- View formatted source 0.9.5.0: [http://www.google.com/search?q=Firefox%20View%20formatted%20source](http://www.google.com/search?q=Firefox%20View%20formatted%20source)
- Web Developer 1.1.3: [http://chrispederick.com/work/webdeveloper/](http://chrispederick.com/work/webdeveloper/)
- X-Ray 0.8.1: [http://www.designmeme.com/xray/](http://www.designmeme.com/xray/)

Disabled Extensions: [14]
- : [http://www.google.com/search?q=Firefox%20](http://www.google.com/search?q=Firefox%20)
- Aging Tabs 0.5.1: [http://en.design-noir.de/mozilla/aging-tabs/](http://en.design-noir.de/mozilla/aging-tabs/)
- ColorZilla 1.0: [http://www.iosart.com/firefox/colorzilla/](http://www.iosart.com/firefox/colorzilla/)
- FxIF 0.2.2: [http://ted.mielczarek.org/code/mozilla/fxif/](http://ted.mielczarek.org/code/mozilla/fxif/)
- GiftTagging 1.2: [http://www.gifttagging.com](http://www.gifttagging.com)
- Glassier 0.1.3: [http://www.google.com/search?q=Firefox%20Glassier](http://www.google.com/search?q=Firefox%20Glassier)
- How'd I Get Here 0.1.2: [http://www.squarefree.com/extensions/high/](http://www.squarefree.com/extensions/high/)
- Html Validator 0.8.3.9: [http://users.skynet.be/mgueury/mozilla/](http://users.skynet.be/mgueury/mozilla/)
- Image Zoom 0.3: [http://imagezoom.yellowgorilla.net/](http://imagezoom.yellowgorilla.net/)
- Java Console 6.0: [http://www.google.com/search?q=Firefox%20Java%20Console](http://www.google.com/search?q=Firefox%20Java%20Console)
- Jump Link 1.3.2: [http://jumplink.mozdev.org/](http://jumplink.mozdev.org/)
- Mars 2.0.8: [http://www.spuler.us](http://www.spuler.us)
- Rain 2.0.8: [http://www.spuler.us](http://www.spuler.us)
- savegenpage 2006.03.20: [https://addons.mozilla.org/extensions/authorprofiles.php?id=383](https://addons.mozilla.org/extensions/authorprofiles.php?id=383)

Total Extensions: 61

Installed Themes: [10]
- Aluminium Kai 2 1.9: [http://franklion.blog.co.uk/](http://franklion.blog.co.uk/)
- Blue Ice 1.2.4: [http://www.firefoxreloaded.com](http://www.firefoxreloaded.com)
- BlueQute 2.0.3: [http://my.fit.edu/~hmiglani/resources/bluequte/](http://my.fit.edu/~hmiglani/resources/bluequte/)
- Cavendish 0.8: [http://ihoss.not-a-blog.com/](http://ihoss.not-a-blog.com/)
- Firefox (default): [http://www.mozilla.org/](http://www.mozilla.org/)
- Fusion Alternative 1.0.20070323: [http://f22.aaa.livedoor.jp/%7Eptdb/firefox/fusion.html](http://f22.aaa.livedoor.jp/%7Eptdb/firefox/fusion.html)
- My_buuf 1.0: [http://redmutt.com](http://redmutt.com)
- Orbit Yellow 2006 0.3: [http://www.google.com/search?q=Firefox%20Orbit%20Yellow%202006](http://www.google.com/search?q=Firefox%20Orbit%20Yellow%202006)
- Qute 3.2.2: [http://quadrone.org/](http://quadrone.org/)
- Smoke 2.0.8: [http://www.spuler.us](http://www.spuler.us)

Installed Plugins: (9)
- Adobe Reader 7.0
- Helix DNA Plugin: RealPlayer G2 Plug-In Compatible
- Java(TM) Plug-in 1.6.0-b105
- mplayerplug-in 3.31
- QuickTime Plug-in 6.0 / 7
- RealPlayer 9
- Shockwave Flash
- VLC Multimedia Plugin
- Windows Media Player Plugin

---

### Post by pacanukeha on 2007-05-01
I shall look into the "all headers" issue, although it does work.

I think the problem might be Extensions.rdf.  I tried a quick dos2unix on that and I am OK.  I will continue to try and create a list of necessary&sufficient conditions.

Cheers.

---

### Post by nanotube on 2007-05-01
thanks for the list, and good luck. :)

---

### Post by pacanukeha on 2007-05-01
It was the ShowAddress 0.0.4 Extension.  Debug accomplished.  <insert rolling of tb dev eyes here as the issue was with an extension and not tb> :)

---

### Post by nanotube on 2007-05-01
> **pacanukeha said:**
> It was the ShowAddress 0.0.4 Extension.  Debug accomplished.  <insert rolling of tb dev eyes here as the issue was with an extension and not tb> :)

hehe, well, anything that's got a version number of 0.0.4 doesn't usually inspire much confidence in terms of stability. :)
glad you figured it out! :)

btw, how do you generate those lists of installed extensions? i found [extension list dumper extension]("https://addons.mozilla.org/en-US/firefox/addon/3746"), but you don't even have it in your list, so i'm curious :)

---

### Post by pacanukeha on 2007-05-01
MR Tech Local Install provides the lists.

Also, I spoke too soon.  Although ShowAddress generates errors, it isn't the cause.  Hrmph.  In any case, I can avoid the issue by  renaming my extensions dir, starting tbird, closing, renaming it back and then starting.  I shall continue to poke.

---

### Post by pacanukeha on 2007-05-13
I can't seem to narrow it down to any specific extension.
If I delete extensions.cache, extensions.ini, and extensions.rdf from my profile directory before starting everything seems to work.  This is also true of the deb version available from other threads in the other forums.

For now I will simply make a replacement start script and lve with the extra 5 seconds on load.

---

### Post by nanotube on 2007-05-13
hmm, well, thanks for sharing. 
it seems strange that it's not any particular extension that causes it...

did you run your tests by removing extensions one by one to see which one fixes it, or did you do it by starting from 0 extensions, and then adding one by one? if you did the former, it could be that 2 extensions are causing problems, so one-by-one removal may not catch...

---

### Post by pacanukeha on 2007-05-18
Hah.  I found it.
Remember Mismatched Domains.
[http://www.andrewlucking.com/archives/2007/02/rmd-hacks/](http://www.andrewlucking.com/archives/2007/02/rmd-hacks/)

In the immortal words of Voltaire - "Booyah!"

---

### Post by nanotube on 2007-05-18
> **pacanukeha said:**
> Hah.  I found it.
Remember Mismatched Domains.
[http://www.andrewlucking.com/archives/2007/02/rmd-hacks/](http://www.andrewlucking.com/archives/2007/02/rmd-hacks/)

In the immortal words of Voltaire - "Booyah!"

nice! :)

---

