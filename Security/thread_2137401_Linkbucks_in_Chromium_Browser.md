---
title: "Linkbucks in Chromium Browser"
date: 2013-04-20
forum: Security
---

### Post by dnbremner on 2013-04-20
Does anyone know how to clear linkbucks ( ? virus ) from Chromium browser ( 25.0.1364.160-Oubunt0.12.04.1 ) which is driving me crazy? Any help greatly appreciated.

---

### Post by Hungry Man on 2013-04-21
What exactly is happening? Is it an extension? Plugin? Is your homepage changed?

I don't know what LinkBucks is - gonna need more info here.

---

### Post by dnbremner on 2013-04-22
My Homepage ( msn.co.uk) hasn't changed but when I attempt to open something on it a page entitled LinkBucks opens and takes me to a dodgy site(s).
It seems to be a Google redirect problem. I've tried uninstalling and reinstalling Chromium, installing Bleachbit and doing a complete clean to no avail. I have no extensions except Novell Moonlight (not enabled) and in the Privacy section of settings the only thing enabled is phishing and malware protection. I use Bing fo omnibox searches.  I'm really at the limit of my knowledge now so any help would be much appreciated.

I suppose I could revert to Firefox but I see from the web that most of the antigoogle redirect soft ware is designed for Firefox,so it would probably only be a matter of time before it was affected as well.

---

### Post by Hungry Man on 2013-04-22
Alright.

Go to chrome://extensions (in your URL bar) and double check that you don't have anything installed/ enabled that wasn't already enabled before all of this started.

Go to chrome://plugins (in your URL bar) and make sure nothing new is enabled, disable anything you don't need.

Check "On Startup" in your Chrome settings. It should say "Open a specific page or set of pages" "Set pages".

Clear out all of those pages - just delete them all.

Go to "Manage search engines". The format will be "Site name" "Site URL" "String"

Check that "String" section, and make sure you don't find "linkbucks" in there.

If you're willing you can just delete all of those search engines manually, and then add them back later.

Let me know what works/ doesn't work.

---

### Post by dnbremner on 2013-04-23
Thanks a lot for your reply. I've done all you asked but LinkBucks still comes up when I try to open e.g. subitem on MSN. However it doesn't happen everytime immediately . It shows up on the chrome task manager and under system processes under the same number.. I've also installed and run chkrootkit.
The only search engine left is Bing.

Any  other suggestions?

---

### Post by dnbremner on 2013-04-23
A little more info, Hungry Man,--I've noticed that LinkBucks doesn't come up immediately after I go online and to begin with, I can open subitems easily, then after a few minutes it reverts to as described before.  It's almost like it has to load after I go online. 
    Also, when LinkBucks opens it counts down 10 seconds after which one can cancel the ad and the original page requested will open. 
 
Hope this helps.

---

### Post by dnbremner on 2013-04-25
In the absence of any more advice and after experimenting , I've now found a suitable solution/workaround for this problem. I simply deleted my startup/homepage (msn.co.uk) and substituted it with the uk.news.yahoo.com and LinkBucks doesn't appear anymore. So the problem seems to have been specifically associated with and confined to msn.co.uk!  I'll mark this thread " solved " for the meantime.

---

