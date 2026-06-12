---
title: "Critical Firefox security update: Firefox/3.5.3"
date: 2009-09-09
forum: The Cafe
---

### Post by HappinessNow on 2009-09-09
> **Security Advisories for Firefox 3.5**

   Impact key:
   
[LIST]
[*][COLOR=Red]Critical:     Vulnerability can be used to run attacker code and install     software, requiring no user interaction beyond normal browsing.[/COLOR]
[*]High:     Vulnerability can be used to gather sensitive data     from sites in other windows or inject data or code into     those sites, requiring no more than normal browsing actions.
[*]Moderate:     Vulnerabilities that would otherwise be High or Critical     except they only work in uncommon non-default configurations or     require the user to perform complicated and/or unlikely steps.
[*]Low:     Minor security vulnerabilities such as Denial of Service     attacks, minor data leaks, or spoofs. (Undetectable spoofs of     SSL indicia would have "High" impact because those are generally     used to steal sensitive data intended for other sites.)
[/LIST]
[http://www.mozilla.org/security/known-vulnerabilities/firefox35.html#firefox3.5.3](http://www.mozilla.org/security/known-vulnerabilities/firefox35.html#firefox3.5.3)

Fortunately we're using Ubuntu, but you may want to check any Firefox on Windows.

---

### Post by MasterNetra on 2009-09-09
Apparently Firefox 3.5.3 was released today! Earlier this morning I finally put on Firefox 3.5.2 via ubuntuzilla then took it off to check out shierko or whatever it was from repo, played with it a little and shrugged, was gonna reinstate ubuntuzilla version but had to head off to school, came back home, ate then went to reinstate it and behold 3.5.3 was available. lol my timing. :lolflag:

---

### Post by coldReactive on 2009-09-09
yay for vulnerability fixes!

---

### Post by merlin666 on 2009-09-14
> **coldReactive said:**
> yay for vulnerability fixes!

I still have not received an update notification for canonical Firefox 3.5.2! Is it not available yet for those repos or could there be something missing?

---

### Post by Tibuda on 2009-09-14
> **merlin666 said:**
> I still have not received an update notification for canonical Firefox 3.5.2! Is it not available yet for those repos or could there be something missing?

You won't receive such notification. If you want FF3.5+, you have to install the [firefox-3.5]("apt:firefox-3.5") package. It is branded as Shiretoko instead of Firefox.

---

### Post by FuturePilot on 2009-09-14
> **danielrmt said:**
> You won't receive such notification. If you want FF3.5+, you have to install the [firefox-3.5]("apt:firefox-3.5") package. It is branded as Shiretoko instead of Firefox.

I think that's what he/she is talking about. It's still at version 3.5.2 on Jaunty.

---

### Post by NormanFLinux on 2009-09-14
Download and install Ubuntuzilla. Then your Firefox and Thunderbird will be kept up to date.

---

### Post by Tibuda on 2009-09-14
> **FuturePilot said:**
> I think that's what he/she is talking about. It's still at version 3.5.2 on Jaunty.

That's probably right. I thought he/she wished to update from 3.0 to 3.5.2.

---

### Post by merlin666 on 2009-09-14
> **danielrmt said:**
> That's probably right. I thought he/she wished to update from 3.0 to 3.5.2.

Yes I am at 3.5.2 from canonical repo, downgraded from 3.5.4pre mozilla daily builds but got annoyed with daily updates. 

How often does ubuntuzilla update?

---

### Post by Tibuda on 2009-09-14
> **merlin666 said:**
> Yes I am at 3.5.2 from canonical repo, downgraded from 3.5.4pre mozilla daily builds but got annoyed with daily updates. 

How often does ubuntuzilla update?

You should try the [Mozilla Security PPA]("https://edge.launchpad.net/~ubuntu-mozilla-security/+archive/ppa") instead of the Daily PPA. Ubuntuzilla uses the tar.gz download avialble at Mozilla website, I guess.

---

### Post by coldReactive on 2009-09-14
> **merlin666 said:**
> Yes I am at 3.5.2 from canonical repo, downgraded from 3.5.4pre mozilla daily builds but got annoyed with daily updates. 

How often does ubuntuzilla update?

Ubuntuzilla updates per Mozilla update.

---

### Post by tcoffeep on 2009-09-14
I use Firefox 3.0.14 :)

It just got updated too

---

### Post by coldReactive on 2009-09-14
btw, if you use ubuntuzilla, your flash will be left behind. You will have to reinstall flash, MANUALLY (not terminal, etc. as Ubuntu will complain that flashplugin-nonfree is already installed.)

> 1) Downloading the 32 bit version of flash from [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/) &#8211;the tar.gz version. 64bit version of flash did not work for me even though I run Ubuntu 64bit.

2) Extract &#8220;install_flash_player_10_linux.tar.gz&#8221; to desktop and copy the &#8220;libflashplayer.so&#8221; file to &#8216;/opt/firefox/plugins&#8217; you can use the command:
sudo cp libflashplayer.so /opt/firefox/plugins

3) Restart Firefox. You can visit the page &#8220;about : plugins&#8221; to confirm installation. Hope this helps.

Keep in mind that Firefox may show flash objects blank after a while, sadly.

---

### Post by nanotube on 2009-09-14
> **coldReactive said:**
> btw, if you use ubuntuzilla, your flash will be left behind. You will have to reinstall flash, MANUALLY (not terminal, etc. as Ubuntu will complain that flashplugin-nonfree is already installed.)


to clarify: that only applies for 64bit ubuntu, because mozilla doesn't release 64bit builds... so you end up with a 32bit browser, and then have to manually stick in a 32bit flash too.

---

### Post by merlin666 on 2009-09-14
> **nanotube said:**
> to clarify: that only applies for 64bit ubuntu, because mozilla doesn't release 64bit builds... so you end up with a 32bit browser, and then have to manually stick in a 32bit flash too.

Yikes, I have been avoiding that for years and finally got flash and java going not too long ago. Right now I have:

Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.1.2) Gecko/20090803 Ubuntu/9.04 (jaunty) Firefox/3.5

And this works fine, I think I may just wait until they load an update into the repo.

---

### Post by change_mode on 2009-09-19
It's been over a week and there's still no update to 3.5.3 in the official Jaunty repos. Firefox 3.0 was updated right away and 3.5.3 is in Karmic, so where exactly is the problem?

(No, I don't want to add an extra repository for every application I run)

---

### Post by Namtabmai on 2009-09-19
It's in Jaunty's proposed ( pre-release updates ) repository. As for why it hasn't been moved into updates one yet is anyones guess.

---

### Post by Chame_Wizard on 2009-09-19
I have
> Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.1.4pre) Gecko/20090918 Ubuntu/8.10 (intrepid) Shiretoko/3.5.4pre


(this are on my temporary PCs{desktop at my inter-ship place and server at home})
:guitar:

---

### Post by speedwell68 on 2009-09-19
THe easiest way of keeping FF3.5.x uptp date is just install the standard version from Mozillas website and let it sort itself out.

---

### Post by coldReactive on 2009-09-19
> **speedwell68 said:**
> THe easiest way of keeping FF3.5.x uptp date is just install the standard version from Mozillas website and let it sort itself out.

IE: Ubuntuzilla, as otherwise you'd have to compile, because the download for linux on the mozilla website is tar.bz2

---

### Post by NormanFLinux on 2009-09-19
Ubuntu releases only critical security and system updates between new versions. They don't update individual applications in a given version. So if a new application version comes out during Karmic Koala, the old version will remain by default.

---

