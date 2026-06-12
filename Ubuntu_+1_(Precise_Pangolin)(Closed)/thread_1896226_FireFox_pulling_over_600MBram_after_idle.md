---
title: "FireFox pulling over 600MBram after idle"
date: 2011-12-16
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ventrical on 2011-12-16
Anyone else seeing performance problems with ff?? I had my PC on for about 5 hours .. just sitting and all this activity was going on in the background. It's settled down after log-off log-on.

Thanks..

---

### Post by Sworddragon on 2011-12-16
Firefox with no Addons has no (critical) memory leaks and the memory usage is moderate. But there are some Addons which are leaking and can consume much memory. For exampel Firebug has a memory leak which can cause Firefox to use a few GB of memory after some days. You should check you Addons if they have such a problem.

---

### Post by paul_in_london on 2011-12-16
> **ventrical said:**
> Anyone else seeing performance problems with ff?? I had my PC on for about 5 hours .. just sitting and all this activity was going on in the background. It's settled down after log-off log-on.

Thanks..

I tend to have a lot of tabs open at any one time and one of the add-ons I use is Bar Tab:

[https://addons.mozilla.org/en-US/firefox/addon/bartab/](https://addons.mozilla.org/en-US/firefox/addon/bartab/)

Depending on what version of FF you're using (I'm using the nightly build) you may also need to install Nightly Tester Tools and Add-on Compatibility Reporter (or disable add-on compatibility checking via about:config), especially if you're using development versions of add-ons. HTH.

---

### Post by lovinglinux on 2011-12-16
> **Sworddragon said:**
> Firefox with no Addons has no (critical) memory leaks and the memory usage is moderate. But there are some Addons which are leaking and can consume much memory. For exampel Firebug has a memory leak which can cause Firefox to use a few GB of memory after some days. You should check you Addons if they have such a problem.

I agree. However, it could also be a problem specific to the page  left open, which seem to be executing some bad javascript or could be interacting badly with an extension. For instance, if you leave Gmail open, it will build up some memory, due to the constant reloading of data using Ajax.

Anyway, it seems you are not alone: [http://support.mozilla.com/en-US/questions/869432](http://support.mozilla.com/en-US/questions/869432)

BTW, I have 62 add-ons installed and my memory consumption easily grows to 600Mb. Depends on what I am doing. I have been delaying troubleshooting the memory leak for some time now and just reload the browser with [Restartless Restart](https://addons.mozilla.org/en-US/firefox/addon/restartless-restart/) when Firefox starts to behave slow.

I would recommend trying [NoScript](https://addons.mozilla.org/en-US/firefox/addon/noscript/), [AdBlock Plus](https://addons.mozilla.org/en-US/firefox/addon/1865/), [Ghostery](https://addons.mozilla.org/en-US/firefox/addon/9609/) and [Flashblock](https://addons.mozilla.org/en-US/firefox/addon/433/) to reduce what can be loaded.

> **paul_in_london said:**
> I tend to have a lot of tabs open at any one time and one of the add-ons I use is Bar Tab:

[https://addons.mozilla.org/en-US/firefox/addon/bartab/](https://addons.mozilla.org/en-US/firefox/addon/bartab/)

Depending on what version of FF you're using (I'm using the nightly build) you may also need to install Nightly Tester Tools and Add-on Compatibility Reporter (or disable add-on compatibility checking via about:config), especially if you're using development versions of add-ons. HTH.

BarTab was an wonderful add-on, but is no longer maintained and has stopped working, even with compatibility check disabled. BTW, you don't need Nightly Tester Tools or Add-on Compatibility Reporter if you are using a nightly build, because since this week Firefox 10.0a2 and 11.0a1 are now considering add-ons [compatible by default](http://blog.mozilla.com/addons/2011/12/12/help-test-default-compatibility-for-add-ons-on-aurora/).

The author of BarTab moved to the development of BarTab Lite, which only prevents tabs from loading when you start Firefox. That functionality is now [built-in Firefox](http://www.tech-recipes.com/rx/19198/firefox-8-load-tabs-on-demand/), which renders the extension useless.

---

### Post by jbicha on 2011-12-17
How many tabs do you have open? If you're crazy enough to use hundreds of tabs (like I do too often), then Firefox will use GBs of RAM.

---

### Post by paul_in_london on 2011-12-17
> **lovinglinux said:**
> 
BarTab was an wonderful add-on, but is no longer maintained and has stopped working, even with compatibility check disabled. BTW, you don't need Nightly Tester Tools or Add-on Compatibility Reporter if you are using a nightly build, because since this week Firefox 10.0a2 and 11.0a1 are now considering add-ons [compatible by default](http://blog.mozilla.com/addons/2011/12/12/help-test-default-compatibility-for-add-ons-on-aurora/).

The author of BarTab moved to the development of BarTab Lite, which only prevents tabs from loading when you start Firefox. That functionality is now [built-in Firefox](http://www.tech-recipes.com/rx/19198/firefox-8-load-tabs-on-demand/), which renders the extension useless.

Thanks for pointing this out. I didn't know that Bar Tab isn't maintained anymore, but I was aware that FF is now able to load tabs on demand via the Preferences option "Don't load tabs ubtil selected". I'm just going to check whether I would lose the "Unload Other Tabs" functionality without Bar Tab enabled.

EDIT: Ok, I removed Nightly Tester Tools and Add-on Compatibility Reporter, disabled Bar Tab.

It wasn't obvious that the Preferences option "Don't load tabs ubtil selected" is actually functional in the current nightly build of FF. Haven't checked other builds. I've re-enabled Bar Tab anyway though for now so that once a given tab is loaded I can unload it (or unload all other tabs) with a right click.

---

### Post by irv on 2011-12-17
Facebook website runs a script which loads older post automatically. Sometimes the script stops running and you will get a message like the op posted. Just thought I would throw this remark out here seeing we are on this subject.

---

### Post by ventrical on 2011-12-17
> **jbicha said:**
> How many tabs do you have open? If you're crazy enough to use hundreds of tabs (like I do too often), then Firefox will use GBs of RAM.


  I only had 3 tabs open.

---

### Post by lovinglinux on 2011-12-17
> **paul_in_london said:**
> Thanks for pointing this out. I didn't know that Bar Tab isn't maintained anymore, but I was aware that FF is now able to load tabs on demand via the Preferences option "Don't load tabs ubtil selected". I'm just going to check whether I would lose the "Unload Other Tabs" functionality without Bar Tab enabled.

EDIT: Ok, I removed Nightly Tester Tools and Add-on Compatibility Reporter, disabled Bar Tab.

It wasn't obvious that the Preferences option "Don't load tabs ubtil selected" is actually functional in the current nightly build of FF. Haven't checked other builds. I've re-enabled Bar Tab anyway though for now so that once a given tab is loaded I can unload it (or unload all other tabs) with a right click.

Unfortunately, Firefox doesn't have the feature to unload tabs like BarTab. I don't know any other extension that can do that.

The reason why BarTab was disabled when you removed Nightly Tools and ACR is probably because BarTab is not even compatible with Firefox 4.0, only 4.0b6. Firefox is now considering add-ons compatible by default, but in that particular case, it suppose it won't work.

---

### Post by paul_in_london on 2011-12-17
> **lovinglinux said:**
> Unfortunately, Firefox doesn't have the feature to unload tabs like BarTab. I don't know any other extension that can do that.

The reason why BarTab was disabled when you removed Nightly Tools and ACR is probably because BarTab is not even compatible with Firefox 4.0, only 4.0b6. Firefox is now considering add-ons compatible by default, but in that particular case, it suppose it won't work.

Hi. No, what I meant was that Bar Tab still works for me in FF nightly with Nightly Tools and ACR disabled, but the "new" native FF Preferences option to load tabs only when selected didn't seem to have any effect when I disabled Bar Tab. That's one reason I re-enabled Bar Tab. The other reason was to allow me to unload some tabs (or all but the active tab) selectively.

---

### Post by lovinglinux on 2011-12-17
> **paul_in_london said:**
> Hi. No, what I meant was that Bar Tab still works for me in FF nightly with Nightly Tools and ACR disabled, but the "new" native FF Preferences option to load tabs only when selected didn't seem to have any effect when I disabled Bar Tab. That's one reason I re-enabled Bar Tab. The other reason was to allow me to unload some tabs (or all but the active tab) selectively.

The feature only works when you start Firefox.

---

### Post by paul_in_london on 2011-12-17
> **lovinglinux said:**
> The feature only works when you start Firefox.

Yes, I do realise that's how it's supposed to work. :)

---

### Post by lovinglinux on 2011-12-17
> **paul_in_london said:**
> Yes, I do realise that's how it's supposed to work. :)

Perhaps it is conlicting with an add-on,because it works like a charm. Anyways, it won't provide the functionality you are looking for.

---

### Post by paul_in_london on 2011-12-17
> **lovinglinux said:**
> Perhaps it is conlicting with an add-on,because it works like a charm. Anyways, it won't provide the functionality you are looking for.

Could be, yes. I have the dev version of Bar Tab installed (2.1b2), which is doing what I want. It would be nice to have all of that fuctionality available in FF natively though because obviously now that this add-on is no longer maintained it may not continue to work indefinitely.

---

### Post by lovinglinux on 2011-12-17
> **paul_in_london said:**
> Could be, yes. I have the dev version of Bar Tab installed (2.1b2), which is doing what I want. It would be nice to have all of that fuctionality available in FF natively though because obviously now that this add-on is no longer maintained it may not continue to work indefinitely.

Indeed. That's why I move on quickly to alternative add-ons when I see they are not being maintained in a decent frequency. Currently, all my 62 add-ons work with the latest Beta.

Sometimes, we don't have the luxury of finding alternatives. Unfortunately, this is the case with BarTab. It is a shame, because the ability to unload the tab is really useful.

---

### Post by lovinglinux on 2011-12-17
I just installed the beta version of BarTab and remembered why I wasn't using it. It doesn't load the tab anymore when you click on it. This is really annoying, because I need to right-click on the tab and reload. The default behavior of BarTab was to load the tab automatically when clicked, as is the behavior of Firefox built-in feature. When BarTab is enabled, the built-in feature doesn't work.

---

### Post by lovinglinux on 2011-12-17
> **lovinglinux said:**
> I just installed the beta version of BarTab and remembered why I wasn't using it. It doesn't load the tab anymore when you click on it. This is really annoying, because I need to right-click on the tab and reload. The default behavior of BarTab was to load the tab automatically when clicked, as is the behavior of Firefox built-in feature. When BarTab is enabled, the built-in feature doesn't work.

Solved that problem with [Reload Tab On Double-Click](https://addons.mozilla.org/en-US/firefox/addon/reload-tab-on-double-click/?src=search) :-)

---

### Post by lovinglinux on 2011-12-17
> **paul_in_london said:**
> EDIT: Ok, I removed Nightly Tester Tools and Add-on Compatibility Reporter, disabled Bar Tab.

I had to install Add-on Compatibility Reporter again, because even with add-ons being considered compatible by default in 10.0a2, you still can't install add-ons from AMO site if they are not compatible. ACR allows to install them.

---

### Post by ventrical on 2011-12-17
I just looked in add-ons and I am not sure if I have any!

 I'm usign this version of firefox:

---

### Post by paul_in_london on 2011-12-17
> **lovinglinux said:**
> I just installed the beta version of BarTab and remembered why I wasn't using it. It doesn't load the tab anymore when you click on it. This is really annoying, because I need to right-click on the tab and reload. The default behavior of BarTab was to load the tab automatically when clicked, as is the behavior of Firefox built-in feature. When BarTab is enabled, the built-in feature doesn't work.

If you right click on an unloaded/inactive tab you can reload it though (that works here anyway).

---

### Post by lovinglinux on 2011-12-17
> **paul_in_london said:**
> If you right click on an unloaded/inactive tab you can reload it though (that works here anyway).

That brings the tab context menu.

---

### Post by paul_in_london on 2011-12-17
> **lovinglinux said:**
> I had to install Add-on Compatibility Reporter again, because even with add-ons being considered compatible by default in 10.0a2, you still can't install add-ons from AMO site if they are not compatible. ACR allows to install them.

Maybe I'll end up having to the same if I find other add-ons that I want to install, but for now (thanks to your tip!) I'm no longer using ACR. :)

---

### Post by lovinglinux on 2011-12-17
> **ventrical said:**
> I just looked in add-ons and I am not sure if I have any!

 I'm usign this version of firefox:

If you are not sure, you probably don't have any. Just in case, type **about:addons** in the address bar, click the extensions tab and tell us what do you have.

---

### Post by lovinglinux on 2011-12-17
> **paul_in_london said:**
> Maybe I'll end up having to the same if I find other add-ons that I want to install, but for now (thanks to your tip!) I'm no longer using ACR. :)

I do a lot of add-on testing, so I will certainly need to keep it. Not a big deal. BTW, if you need it again in the future, you could also try [Disable Add-on Compatibility Checks](https://addons.mozilla.org/en-US/firefox/addon/checkcompatibility/) which is lighter and restartless.

---

### Post by paul_in_london on 2011-12-17
> **lovinglinux said:**
> That brings the tab context menu.

That's what I meant. I know it would be better if a single left click would do it though!

Btw, there does seem to be some discussion [here](https://bugzilla.mozilla.org/show_bug.cgi?id=675539) about making BT-type functionality available natively in FF.

---

### Post by paul_in_london on 2011-12-17
> **lovinglinux said:**
> I do a lot of add-on testing, so I will certainly need to keep it. Not a big deal. BTW, if you need it again in the future, you could also try [Disable Add-on Compatibility Checks](https://addons.mozilla.org/en-US/firefox/addon/checkcompatibility/) which is lighter and restartless.

Thanks - that's useful to know.

---

### Post by lovinglinux on 2011-12-17
> **paul_in_london said:**
> That's what I meant. I know it would be better if a single left click would do it though!

Btw, there does seem to be some discussion [here](https://bugzilla.mozilla.org/show_bug.cgi?id=675539) about making BT-type functionality available natively in FF.

And here we go, an alternative:

[https://addons.mozilla.org/en-US/firefox/addon/dormancy/](https://addons.mozilla.org/en-US/firefox/addon/dormancy/)

:popcorn:

---

### Post by paul_in_london on 2011-12-17
> **lovinglinux said:**
> And here we go, an alternative:

[https://addons.mozilla.org/en-US/firefox/addon/dormancy/](https://addons.mozilla.org/en-US/firefox/addon/dormancy/)

:popcorn:

Didn't know about that one. I'll try it out. I noticed this line on the Dormancy add-on page:

> This might land as a core feature in Firefox 9 ([https://bugzilla.mozilla.org/show_bug.cgi?id=675539](https://bugzilla.mozilla.org/show_bug.cgi?id=675539)).

---

### Post by lovinglinux on 2011-12-17
> **paul_in_london said:**
> Didn't know about that one. I'll try it out. I noticed this line on the Dormancy add-on page:

Yep, I found th link to this add-on in the bug page.

Found another one that can help with Memory issues:

[https://addons.mozilla.org/en-US/firefox/addon/memory-restart/](https://addons.mozilla.org/en-US/firefox/addon/memory-restart/)

---

### Post by paul_in_london on 2011-12-17
> **lovinglinux said:**
> Yep, I found th link to this add-on in the bug page.

Found another one that can help with Memory issues:

[https://addons.mozilla.org/en-US/firefox/addon/memory-restart/](https://addons.mozilla.org/en-US/firefox/addon/memory-restart/)

On the Dormancy page there is also this comment:

> Maybe Memory Fox Rated 3 out of 5 stars

by raywood on October 26, 2011 #

Just found Memory Fox addon. Seems to be well received. May be a better approach to the purpose of Dormancy.


Are you familiar with that add-on?

One thing about Dormancy compared with Bar Tab is that it's less obvious when tabs are unloaded (because they're not greyed out). What I prefer about BT is that tabs are unloaded at start-up and I can selectively unload active tabs. On the other hand, using Dormancy, just left-clicking on an unloaded tab is enough to reload it :)

EDIT: Looking at the mem usage reported by htop my initial impressions are that Dormancy is possibly less effective than BT, but I'll continue testing it...

---

### Post by ventrical on 2011-12-17
> **lovinglinux said:**
> If you are not sure, you probably don't have any. Just in case, type **about:addons** in the address bar, click the extensions tab and tell us what do you have.


Ahhh.. yes..  so these must be default because I never manually enabled them.

---

### Post by lovinglinux on 2011-12-17
> **ventrical said:**
> Ahhh.. yes..  so these must be default because I never manually enabled them.

Yes, the first one comes with Firefox Aurora and Nightly, the other two are installed by Ubuntu. So, you  probably don't have a add-on issue. Although Global Menu Integration can cause other problems, I never hard about it causing memory leaks.

Anyway, what page was open in the tab when you received the script alert?

---

### Post by lovinglinux on 2011-12-17
> **paul_in_london said:**
> Are you familiar with that add-on?

It is Windows only.

---

### Post by ventrical on 2011-12-17
> **lovinglinux said:**
> Yes, the first one comes with Firefox Aurora and Nightly, the other two are installed by Ubuntu. So, you  probably don't have a add-on issue. Although Global Menu Integration can cause other problems, I never hard about it causing memory leaks.

Anyway, what page was open in the tab when you received the script alert?

 ff just updated , restarted .. etc... so I haven't seen the problem reproduce itself just yet. Perhaps the update was a remedy/work-around. I'll keep an eye on it.

---

### Post by paul_in_london on 2011-12-17
> **lovinglinux said:**
> It is Windows only.

Yes, I remembered actually after I posted that!

---

### Post by lovinglinux on 2011-12-17
> **paul_in_london said:**
> Yes, I remembered actually after I posted that!

I think I used it, back in the old days of Windows.

---

### Post by paul_in_london on 2011-12-17
> **lovinglinux said:**
> I think I used it, back in the old days of Windows.

It'll be interesting to see whether FF incorporates (more of) the functionality of these kinds of add-ons anyway. The wealth of FF add-ons is partly why FF is my browser of choice. I do keep an eye on what's happening with opera-next and chromium. I find that chromium, for example, consumes a ridiculous amount of RAM with only a handful of tabs open, whereas I can have **lots** of active tabs in FF and not experience that.

---

### Post by lovinglinux on 2011-12-24
Found this while searching for an issue in Firefox 9:

[http://philikon.wordpress.com/2011/12/02/the-future-of-bartab/](http://philikon.wordpress.com/2011/12/02/the-future-of-bartab/)

---

### Post by paul_in_london on 2011-12-24
> **lovinglinux said:**
> Found this while searching for an issue in Firefox 9:

[http://philikon.wordpress.com/2011/12/02/the-future-of-bartab/](http://philikon.wordpress.com/2011/12/02/the-future-of-bartab/)

Thanks for the info. I ended up re-enabling BT a few days ago. It's good to know that, as well as introducing the FF Preferences option to load tabs only when selected, they're also working on [auto-unloading of inactive tabs](https://bugzilla.mozilla.org/show_bug.cgi?id=675539).

---

### Post by lovinglinux on 2011-12-24
> **paul_in_london said:**
> Thanks for the info. I ended up re-enabling BT a few days ago. It's good to know that, as well as introducing the FF Preferences option to load tabs only when selected, they're also working on [auto-unloading of inactive tabs](https://bugzilla.mozilla.org/show_bug.cgi?id=675539).

BTW, I have created a thread to discuss memory usage. See [http://ubuntuforums.org/showthread.php?t=1899304](http://ubuntuforums.org/showthread.php?t=1899304)

---

### Post by paul_in_london on 2011-12-24
> **lovinglinux said:**
> BTW, I have created a thread to discuss memory usage. See [http://ubuntuforums.org/showthread.php?t=1899304](http://ubuntuforums.org/showthread.php?t=1899304)

Thanks. That's another tab I should keep open! :lolflag:

---

### Post by lovinglinux on 2011-12-24
> **paul_in_london said:**
> Thanks. That's another tab I should keep open! :lolflag:

:lolflag:

---

