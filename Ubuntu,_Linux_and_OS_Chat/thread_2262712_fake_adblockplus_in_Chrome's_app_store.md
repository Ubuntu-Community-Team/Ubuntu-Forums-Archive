---
title: "fake adblockplus in Chrome's app store"
date: 2015-01-26
forum: Ubuntu, Linux and OS Chat
---

### Post by monkeybrain20122 on 2015-01-26
Just found a fake ABP in Chrome's app store, it is said to be from masterdcc2000 instead of adblockplus.org. It installs as a 'webapp' that shows up in the dash instead of the Chrome menu bar, if you click it opens to some website in Chrome. Probably a malware, I have since deleted my Chrome profile and made a new one. Be careful when you install ABP next time.

---

### Post by kerry_s on 2015-01-27
your better off using a hosts block file these days. those adblock apps are all cutting side deals to allow what they consider acceptable ad's.

---

### Post by coldraven on 2015-01-27
I use ABP and Ghostery. It's currently blocking 1987 trackers etc.!

---

### Post by lisa6 on 2015-01-28
> **monkeybrain20122 said:**
> Just found a fake ABP in Chrome's app store, it is said to be from masterdcc2000 instead of adblockplus.org. It installs as a 'webapp' that shows up in the dash instead of the Chrome menu bar, if you click it opens to some website in Chrome. Probably a malware, I have since deleted my Chrome profile and made a new one. Be careful when you install ABP next time.

I downloaded this app today on my laptop. Google Chrome kept crashing, so I restarted my laptop. When its restarted it lets me enter my password, but then I get a blank screen. Nothing! No Windows! I'm typing this from my desktop. How do I fix it?

---

### Post by SeijiSensei on 2015-01-29
> **kerry_s said:**
> your better off using a hosts block file these days. those adblock apps are all cutting side deals to allow what they consider acceptable ad's.
You can choose to block "acceptable" ads in the configuration screen for ABP.  I have them blocked both in Firefox and on my Android phone, where ABP works as a proxy.

Trying to implement an effective blocking scheme in /etc/hosts given the large and ever-growing list of sites that distribute advertising would be a nightmare to manage.

---

### Post by Tar_Ni on 2015-01-29
> **SeijiSensei said:**
> You can choose to block "acceptable" ads in the configuration screen for ABP.  I have them blocked both in Firefox and on my Android phone, where ABP works as a proxy.

With Adblock Edge you don't have this 'sponsored ads whitelist' at all. A great addon for Firefox users. :)

As for the fake ABP extension, are Google not reviewing the extensions people add in their Chrome Store? It should be deleted by now..

> **lisa6 said:**
> I downloaded this app today on my laptop. Google Chrome kept crashing, so I restarted my laptop. When its restarted it lets me enter my password, but then I get a blank screen. Nothing! No Windows! I'm typing this from my desktop. How do I fix it?

Most likely you'll have to reimage your Windows install or make a clean reinstallation.. Your computer must be badly infected. Don't you have DVDs to reset your laptop to the factory state?

If not, then this might be an opportunity for you to try out Linux Ubuntu..

---

### Post by monkeybrain20122 on 2015-01-30
> **Tar_Ni said:**
> With Adblock Edge you don't have this 'sponsored ads whitelist' at all. A great addon for Firefox users. :)

As for the fake ABP extension, are Google not reviewing the extensions people add in their Chrome Store? It should be deleted by now..

.

Google's review appears to be very lax. I have searched this and apparently the problem has come and gone for a while (I don't use Chrome a lot so haven't noticed this before) Whenever it is banned it comes back with a different id (it wasn't 'masterdcc2000' before if you do a search).  BTW ABE is not availiable on Chrome because the developer detests google. :)

---

### Post by monkeybrain20122 on 2015-01-30
> **lisa6 said:**
> I downloaded this app today on my laptop. Google Chrome kept crashing, so I restarted my laptop. When its restarted it lets me enter my password, but then I get a blank screen. Nothing! No Windows! I'm typing this from my desktop. How do I fix it?

Sounds kind of drastic. What OS do you use? Are you sure it is due to the fake ABP and not a coincidental failure somewhere else? I haven't experienced any problem actually except the ABP 'webapp' showing up in the dash (on Fedora 21, gnome shell). Removed chrome's profile and started a new one it went away. I think it is either an adware or a malware that probably targets Windows.

---

### Post by vasa1 on 2015-01-30
> **SeijiSensei said:**
> You can choose to block "acceptable" ads in the configuration screen for ABP.  I have them blocked both in Firefox and on my Android phone, where ABP works as a proxy.

Trying to implement an effective blocking scheme in /etc/hosts given the large and ever-growing list of sites that distribute advertising would be a nightmare to manage.I too prefer AdBlock Plus (the original) over /etc/hosts because the latter doesn't allow regex. Also, the advanced filter screen in the Firefox version of ABP is really powerful. 

I consider ABE as something opportunistic, somewhat like Mint (at the time its only real USP was that it included restricted extras), SRWare Iron, etc.

I use Chrome for very, very specific sites and don't use any extensions at all for that browser.

---

### Post by vasa1 on 2015-01-30
> **kerry_s said:**
> your better off using a hosts block file these days. those adblock apps are all cutting side deals to allow what they consider acceptable ad's.ABP has an option to see both the blockable and blocked items on a page. I use that option ever so often to detect new stuff I would like to block. BTW, I have my own custom list and don't use any of the off-the-shelf lists which have blocks, and exceptions, I don't want.

---

### Post by Tar_Ni on 2015-01-30
> **vasa1 said:**
> I consider ABE as something opportunistic, somewhat like Mint (at the time its only real USP was that it included restricted extras), SRWare Iron, etc.

I am not sure why the Linux Mint project should be considered 'opportunistic' only because it uses Ubuntu as a basis. It has grown and matured to a different OS altogether with it's very own DE (Cinnamon.) If it must truly be so, than I suppose the folks at Debian must be saying the same of Ubuntu.

A great thing with the open source is that developpers can use a source code and make their own products from it. A dev disagreed with the direction ABP was going, allowing 'sponsored ads' to go through by default, which a lot of users are actually not even aware of. So he forked the 2.1.2 version without the 'sponsored ads withelist' and used it as a basis. He made the addon available to all on the Firefox extension site and provides updates regularly. Is that 'opportunistic'? Well, in my opinion he corrected a mistake and we can now use an alternative.

I recommend ABE over ABP because I don't need to say to someone ''Install X and then you should disable this X feature''. There's no need for that with ABE, once installed, the easyList will block every ads. Besides, ALL the blocking filters (like easyPrivacy, Malware Domain, Fanboy's Lists ect.) are available in two clicks in ''filter preferences'', not so in ABP.

---

