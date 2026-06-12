---
title: "Websites are monitoring our activities!!!"
date: 2010-08-20
forum: The Cafe
---

### Post by JohnElway on 2010-08-20
Sorry for the dramatic title but I thought this was something people should see. I just read this article about websites monitoring user activity:

[http://online.wsj.com/article/SB10001424052748703940904575395073512989404.html](http://online.wsj.com/article/SB10001424052748703940904575395073512989404.html)

The article mentions three methods for tracking activity: cookies, beacons (or web bugs), and Flash cookies. Here's how I have tried to disable each of these (I'm not entirely sure how effective these methods are):

NOTE: This only works for Firefox.
 
Cookies: In Firefox, go to Edit>Preferences and in the Privacy section uncheck 'Accept cookies from sites'. There are many other options available, i.e. blocking only third party cookies or deleting cookies when you close your browser.

Beacons: For this, you need the NoScript add-on. I've been using this add-on since my computer got raped by Java viruses back when I was using Windows and I can tell you that it's the best add-on I've ever used for Firefox. It not only makes web browsing more secure, it also makes it faster due to its blockage of client side scripting.
To block beacons, click the NoScript logo (bottom right) and select Options. Select the advanced tab, then the Untrusted tab and check Forbid "Web Bugs". Unfortunately, this will not block beacons from trusted sites. If anyone knows how to block ALL beacons please let me know.

Flash cookies: You need to adjust you Flash Player Settings here: [http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager03.html](http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager03.html). In the Global Storage Settings tab, reduce the disk space amount to 0 so that the Flash Player won't be able to save any information on your machine.

IMPORTANT NOTE: Disabling these things may block functionality that you still want. My plan is to block everything initially and make adjustments when necessary.

Also, I occasionally use Chromium so does anyone know how to do the above in that browser? And does anyone know any better ways of doing the above in Firefox?

---

### Post by Artemis Fowl on 2010-08-20
I've known about this for a long time due to the fact I was intrigued by viruses as a windows user and spent a large portion of my computer time reading about them and anything related to them, including this fact.
Thanks for telling me how to not accept cookies, I was unaware of how to do that in firefox.

---

### Post by Spice Weasel on 2010-08-20
This is no new news, see Google.

---

### Post by mendhak on 2010-08-20
You can use ScriptBlock to block Flash and JS. 
There's also Ghostery you can look at.

---

### Post by lovinglinux on 2010-08-20
> **mendhak said:**
> You can use ScriptBlock to block Flash and JS.

What is that?

> **mendhak said:**
> There's also Ghostery you can look at.

There is also [Better Privacy]("https://addons.mozilla.org/en-US/firefox/addon/6623/"), but I'm not using it anymore since Ghostery seems to have this functionality now.

Also check the Privacy & Security section of AMO:

[https://addons.mozilla.org/en-US/firefox/extensions/privacy-security/](https://addons.mozilla.org/en-US/firefox/extensions/privacy-security/)

BTW, there is also **[network.http.sendRefererHeader]("http://kb.mozillazine.org/Network.http.sendRefererHeader")** that sends information about which site you are when you click a link. I disable this, but some sites like launchpad doesn't work properly with this disabled.

---

### Post by Austin25 on 2010-08-20
Even this forum is using Google Analytics. :shock:

---

### Post by lisati on 2010-08-20
> **JohnElway said:**
> Sorry for the dramatic title but I thought this was something people should see. I just read this article about websites monitoring user activity:

[http://online.wsj.com/article/SB10001424052748703940904575395073512989404.html](http://online.wsj.com/article/SB10001424052748703940904575395073512989404.html)

The article mentions three methods for tracking activity: cookies, beacons (or web bugs), and Flash cookies. Here's how I have tried to disable each of these (I'm not entirely sure how effective these methods are):

Websites have had access to information about visitors for years. Part of this is for technical reasons: how can a server dish out web pages if it doesn't know where to send them?

Have a look here on my web site for an example of some of the information that can be inferred: [http://lisati.homelinux.com/whoami](http://lisati.homelinux.com/whoami)

If you're visiting websites run by reputable operators, you shouldn't have to worry. As others have mentioned, there are options available to help protect your privacy.

---

### Post by endotherm on 2010-08-20
> **mendhak said:**
> You can use ScriptBlock to block Flash and JS. 
There's also Ghostery you can look at.
beware. ghostery tracks your actions as part of it;s functions, so make sure you trust them.

---

### Post by DrMelon on 2010-08-20
I thought everyone and their grandmothers knew this. It's how "keep me logged in" things work on websites, with cookies.

---

### Post by -grubby on 2010-08-20
> **lisati said:**
> 
Have a look here on my web site for an example of some of the information that can be inferred: [http://lisati.homelinux.com/whoami](http://lisati.homelinux.com/whoami)

Your IP address (207.118.114.83) appears to be listed by the following service(s): 
zen.spamhaus.org
dnsbl.sorbs.net

:(

---

### Post by Spr0k3t on 2010-08-20
OMG!  The intarwebs are watching us!  This has been the case since 1994.  Nothing new.  You should see what the harvest logs look like from ARPAnet, quite humorous tbh.  I'm actually quite shocked WSJ even reported on it.

---

### Post by lisati on 2010-08-20
> **-grubby said:**
> Your IP address (207.118.114.83) appears to be listed by the following service(s): 
zen.spamhaus.org
dnsbl.sorbs.net

:(
Sorry about that: I've got some anti blog spam measures in place on my server. A visit to [http://blacklistalert.org](http://blacklistalert.org) or [http://debouncer.com](http://debouncer.com) might be able to help you figure out what's going on.

---

### Post by Zorgoth on 2010-08-20
I found an interesting article about how some developers at Microsoft were planning to not be evil for a change and put powerful privacy settings into IE8 that would be on by default, and some Microsoft advertising executives quashed it.  I don't really have a problem with what Google does on GMail, targeting ads based on what you're looking, but creating long-term profiles of me that apply on websites where I have never created an account strikes me as just plain creepy.

---

### Post by juancarlospaco on 2010-08-20
Internet _is_ a Public network and all non-encrypted data *can be/is* monitored by third party.

---

### Post by lisati on 2010-08-20
> **lisati said:**
> Sorry about that: I've got some anti blog spam measures in place on my server. A visit to [http://blacklistalert.org](http://blacklistalert.org) or [http://debouncer.com](http://debouncer.com) might be able to help you figure out what's going on.
NVM: I just had a look at the source for my [whoami]("http://lisati.homelinux.com/whoami") page: it's meant to show the DNSBL stuff; grubby's access to my page wasn't actually blocked! If it pops up something similar for you, check out the "Spam Blocklist Check" in my sig, it provides links where it can.
(/me wanders off, hanging head in shame!)


Edit: after another look at my system logs, I see Jaunty, Lucid, and even Windows! I see Chrome, Safari and a couple of different versions of Firefox (including v4)

---

### Post by MasterNetra on 2010-08-20
Of course cookies can track, they are meant to. It done to allow for a more personal experience with websites, don't block them though some sites need to use cookies for short term site related functions. If your worried about it, In Firefox go to Edit->Preferences->Privacy, select "Use custom..." in the "Firefox will:" drop down menu. Then go down to "Keep until:" and select "I close Firefox" from the drop down menu. And there you go every time you close Firefox out completely it will empty out all the cookies. Except the Flash Cookies, browsers period don't recognize them, you will have to add the "better privacy" addon for Firefox to clear those out at close. (And at that be sure to close the download list before the main windows as better privacy doesn't clear when the download list is the last to close for whatever reason.)

---

### Post by JohnElway on 2010-08-20
> **Spr0k3t said:**
> OMG!  The intarwebs are watching us!  This has been the case since 1994.  Nothing new.  You should see what the harvest logs look like from ARPAnet, quite humorous tbh.  I'm actually quite shocked WSJ even reported on it.

The point of the article isn't to just state that websites are monitoring our activity. I think just about everyone knows that is happening. 

What is unsettling is that after monitoring our activity, these sites compile our information into a profile and then sell it to advertisers for a profit. This is something that has become very prevalent only within the last few years. I realize what the original purpose of cookies was, but what they're doing now has absolutely nothing to do with enhancing the user experience. And what's worse is that, according to the article, many of these "reputable" sites don't even realize they're installing these tracking files (e.g. Dictionary.com). That functionality is somehow hidden in the free web software that these sites get from other companies.

It's one thing to track user activity. It's an entirely different thing to then sell that information for a profit, all without notifying the user. It strikes me as incredibly creepy and douchey at the same time.

---

