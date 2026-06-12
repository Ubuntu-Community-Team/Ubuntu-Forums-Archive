---
title: "firefox 3.6"
date: 2010-01-21
forum: Ubuntuzilla
---

### Post by ferric84 on 2010-01-21
Any word on when Firefox 3.6 will appear in Ubuntuzilla's repository?

---

### Post by nanotube on 2010-01-21
> **ferric84 said:**
> Any word on when Firefox 3.6 will appear in Ubuntuzilla's repository?

it was just released today. it will appear just as soon as i package it up and push it out to the repo, which will be within the next hour or so.

---

### Post by nanotube on 2010-01-21
it's up there now - just give it a few minutes to propagate through the sourceforge file release mirrors.

---

### Post by Objekt on 2010-01-21
Great!  Is there anything I need to do, or will I get prompted to upgrade Firefox to 3.6?

Thanks for Ubuntuzilla by the way; it's a big help.  Recently I built a machine for somebody & put Ubuntu on it.  Due to various problems with more recent releases of Ubuntu, I opted for the more stable (and longer-supported) but slightly old 8.04.3 LTS.  Ubuntuzilla helped me get the most current version of Firefox on that machine easily.

---

### Post by aysiu on 2010-01-21
It just showed up in the Update Manager for me. I didn't have to do anything special.

---

### Post by vrkalak on 2010-01-21
I had added the Mozilla/Firefox ppa repositories from _Launchpad.net_ to my */etc/apt/sources.list* a while back.  After updating, I can install any version of Firefox via Synaptic Manager.

I have been using Firefox 3.6 since it was in Beta 4
and Firefox 3.7 since it was in pre-Alpha 1.

I just updated to the Final Release of FireFox 3.6 today.

I have found the newer versions of Firefox to be faster than Chrome browser.
Only, problems are that many of the Mozilla add-ons, themes and extensions are not compatible with 3.6 or 3.7 yet.

---

### Post by nanotube on 2010-01-21
> **Objekt said:**
> Great!  Is there anything I need to do, or will I get prompted to upgrade Firefox to 3.6?

Thanks for Ubuntuzilla by the way; it's a big help.  Recently I built a machine for somebody & put Ubuntu on it.  Due to various problems with more recent releases of Ubuntu, I opted for the more stable (and longer-supported) but slightly old 8.04.3 LTS.  Ubuntuzilla helped me get the most current version of Firefox on that machine easily.

if you're using the ubuntuzilla repository (rather than the old installer script), then as aysiu said, it should happen automatically, as for any other package updates. 

if you want to get it 'right now' you can open synaptic and hit 'reload', then the update will appear immediately.

---

### Post by nanotube on 2010-01-21
> **vrkalak said:**
> I had added the Mozilla/Firefox ppa repositories from _Launchpad.net_ to my */etc/apt/sources.list* a while back.  After updating, I can install any version of Firefox via Synaptic Manager.

I have been using Firefox 3.6 since it was in Beta 4
and Firefox 3.7 since it was in pre-Alpha 1.

I just updated to the Final Release of FireFox 3.6 today.

the only problem with the nightlies is that they tend to be less stable than the official releases. 

> 
I have found the newer versions of Firefox to be faster than Chrome browser.
Only, problems are that many of the Mozilla add-ons, themes and extensions are not compatible with 3.6 or 3.7 yet.

the only addon that really matters (to me) (adblock plus) is, thankfully, compatible with ff3.6 ;)

---

### Post by Objekt on 2010-01-21
Unfortunately, things are not so simple for us 64-bit users.

---

### Post by nanotube on 2010-01-22
> **Objekt said:**
> Unfortunately, things are not so simple for us 64-bit users.

indeed, quite unfortunate. feel free to prod mozilla to produce 64bit release builds (though i'm sure they're already getting plenty of it).

in the meantime, if you're still using the ubuntuzilla script, then you have to use the old update instructions, which you can see on the ubuntuzilla website on the 'ubuntuzilla installed script' page:
[https://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Ubuntuzilla_Installer_Script](https://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Ubuntuzilla_Installer_Script)

or you could consider using the daily ppa, which provides 64bit builds (although it doesn't track releases, but rather the latest nightlies, so less stability).

---

### Post by ferric84 on 2010-01-22
One more... after upgrading, I went to Help -> About, which reports my version as 3.6, but my UA string is:

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.2) Gecko/20100115 Firefox/3.5.3

Shouldn't that read Firefox/3.6?  This might be a question for the Mozilla folks instead.  I'm on 9.04.

---

### Post by nanotube on 2010-01-22
> **ferric84 said:**
> One more... after upgrading, I went to Help -> About, which reports my version as 3.6, but my UA string is:

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.2) Gecko/20100115 Firefox/3.5.3

Shouldn't that read Firefox/3.6?  This might be a question for the Mozilla folks instead.  I'm on 9.04.

what leads you to believe that your useragent stayed at 3.5.3? what shows up if you go to whatsmyuseragent.com ? and are you sure you're not accidentally running an old repos version? (go to whatsmyuseragent, and while there, look at help->about for the version reported there)

---

### Post by Uncle Spellbinder on 2010-01-23
I have the Ubuntu supplied Firefox at the moment. Ubuntuzilla repo added. Also installed SeaMonket 2.0.

Question I have is, If, using Synaptic, I install firefox-mozilla-build, will this be an additional Firefox on my system alongside the Ubuntu supplied version? If so, will there be profile issues? Plugin issues?

---

### Post by kansasnoob on 2010-01-23
> **Uncle Spellbinder said:**
> I have the Ubuntu supplied Firefox at the moment. Ubuntuzilla repo added. Also installed SeaMonket 2.0.

Question I have is, If, using Synaptic, I install firefox-mozilla-build, will this be an additional Firefox on my system alongside the Ubuntu supplied version? If so, will there be profile issues? Plugin issues?

You will notice when you go to Applications > Internet that you'll have menu items for both Firefox Web Browser and Mozilla Build of Firefox but either launcher will actually launch the latest Mozilla Build of Firefox. The same is true for Seamonkey and Thunderbird.

If you'd like to clean that up you can go to System > Preferences > Main Menu and click on Internet in the left column and then remove the "tick" next to the menu entry you wish not to display.

During testing we decided to leave it this way because not everyone has the official Ubuntu build of the packages already installed.

I've had no issues whatsoever with plug-ins and the Mozilla builds of both Seamonkey and Firefox picked up my existing profiles seamlessly.

---

### Post by Uncle Spellbinder on 2010-01-23
Thanks, kansasnoob.

---

### Post by nanotube on 2010-01-23
and just to add something to that, as far as your question about profiles goes:

it's not adviseable to switch back and forth between different versions of firefox using the same profile. so, e.g., once you start using a profile with ff3.6, don't go back to ff3.5 using that profile.

---

