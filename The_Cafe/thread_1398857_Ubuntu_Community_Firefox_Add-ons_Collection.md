---
title: "Ubuntu Community Firefox Add-ons Collection"
date: 2010-02-05
forum: The Cafe
---

### Post by lovinglinux on 2010-02-05
The collection has been deleted.

> **Note:** Canonical denied my request to name the collection "Ubuntu Community". I don't know how to rename it to something else meaningful and in tune with the idea of the project, without violating Ubuntu's trademarks, so I decided to drop the project entirely and focus on [my own Add-on Collections](http://lovinglinux.megabyet.net/?p=36). I'm really sorry.


---

### Post by Psumi on 2010-02-05
If you have NoScript, you don't need adblock or flashblock, as NoScript usually takes care of that. For image-only ads that are not script based, just edit your hosts file.

---

### Post by lovinglinux on 2010-02-05
> **Psumi said:**
> If you have NoScript, you don't need adblock or flashblock, as NoScript usually takes care of that. For image-only ads that are not script based, just edit your hosts file.

Yes, but installing NoScript and Flashblock allows greater flexibility over which content should be allowed or not. For instance, you might want to block only flash content from a site that you fully allow on NoScript, to increase performance. That being said, using both might result in conflicts as I have already experienced, resulting in unblocked flash content.

Why should I edit the hosts file when I can simply use Adblock Plus and update the blacklist automatically? After all, there is no problem to have both Adblock and NoScript installed.

---

### Post by Psumi on 2010-02-05
> **lovinglinux said:**
> Why should I edit the hosts file when I can simply use Adblock Plus and update the blacklist automatically? After all, there is no problem to have both Adblock and NoScript installed.

The hosts file makes it so that the domains/IPs never resolve, so your browser doesn't load the domains in the first place.

---

### Post by lovinglinux on 2010-02-05
> **Psumi said:**
> The hosts file makes it so that the domains/IPs never resolve, so your browser doesn't load the domains in the first place.

That's a good reason, but not enough to make me edit the hosts files manually. Linux has made me a lazy guy :)

---

### Post by k3lt01 on 2010-02-05
I use a hosts file in preference to adblock as I like the advantage of not having to many add-ons on FireFox. The host file is already there so to my way of thinking I may as well use it instead of adding another item to do the same thing and possible not as well.

I do like noscript but I have found some people, my father for instance, have difficulty with it so the host file again is an advantage because it simply and quietly blocks any incoming traffic from the offending site.

---

### Post by Psumi on 2010-02-05
> **lovinglinux said:**
> Linux has made me a lazy guy :)

How is that even possible? That's Windows' job.

---

### Post by lovinglinux on 2010-02-05
> **Psumi said:**
> How is that even possible? That's Windows' job.

Because I can easily automate almost anything with bash scripts, use tab completion, aliases, installation of applications with one line command, re-installation of all previously installed packages with one line command, separate home partitions to keep everything in p&#314;ace when installing from fresh, no need to defrag disks every couple of days, no need to clean up the registry all the time, no need to scan for viruses, no need to boot after installing applications and system updates...well, the list goes on.

---

### Post by lovinglinux on 2010-02-05
Would be nice if those that are voting No could explain why they don't think this collection is a good idea.

---

### Post by Psumi on 2010-02-05
> **lovinglinux said:**
> Would be nice if those that are voting No could explain why they don't think this collection is a good idea.

it makes the mozilla/firefox users on windows think that the entire ubuntu community loves all those add-ons.

The only add on I care about in firefox is greasemonkey.

---

### Post by lovinglinux on 2010-02-05
> **Psumi said:**
> it makes the mozilla/firefox users on windows think that the entire ubuntu community loves all those add-ons.

The only add on I care about in firefox is greasemonkey.

Thanks for your explanation.

When I created the collection I also sent a PM to a moderator so they can analyze if the idea is  inappropriate in some way. If they decide that it is, then would be fairly easy to change the name of the collection, to something like Ubuntu Users or UbuFox Shared Collection, or whatever. Nevertheless, I don't believe a collection like that would imply everyone loves all extension inside it, after all we don't love all applications in the Ubuntu repository either. I see it as a way of easily sharing good add-ons between Ubuntu users. 

BTW, greasemonkey is my recommended collection. I will add it to the shared collection too.

---

### Post by scouser73 on 2010-02-05
Nice way of collaborating with Ubuntus' Firefox users.

---

### Post by lovinglinux on 2010-02-05
> **scouser73 said:**
> Nice way of collaborating with Ubuntus' Firefox users.

Thanks. Unfortunately, I thought the idea would be better received by the community members.

---

### Post by lovinglinux on 2010-02-05
Just for the record, I have written to Canonical's Trademark team if I can use the name Ubuntu Community on the collection. I will post their decision as soon as they reply.

---

### Post by wojox on 2010-02-06
Awesome idea lovin. I'll check it out sometime today and contribute to it. Yeah I was wondering do you use the the " prefs.js " or " user.js " files ?

I've been dabbling with those and was going to make one to go along with the Optimization page. Thanks for the link you updated about disabling IPv6 pointing to my site. I returned the favour: [http://wojox.homelinux.net/?p=33](http://wojox.homelinux.net/?p=33)

---

### Post by lovinglinux on 2010-02-06
> **wojox said:**
> Awesome idea lovin. I'll check it out sometime today and contribute to it. Yeah I was wondering do you use the the " prefs.js " or " user.js " files ?

Thanks. Any contribution will be very appreciated.

I use prefs.js. I don't see a reason to use user.js, which would be useful if you need to reuse some settings across profiles and want to make them permanent. Most of the time I don't need to re-configure my settings, since I backup my profiles regularly, but I also document any changes I do, so if I need to create a new profile, I simply spend some time changing the settings manually.

> From:  [http://kb.mozillazine.org/User.js_file](http://kb.mozillazine.org/User.js_file)

A user.js file is an alternative method of modifying preferences, recommended for advanced users only. Unless you need a user.js file for a specific purpose you should use about:config instead. The user.js file does not exist by default.

Important: Once an entry for a preference setting exists in the user.js file, any change you make to that setting in the options and preference dialogs or via about:config will be lost when you restart your Mozilla application because the user.js entry will override it.

A user.js file can make certain preference settings more or less "permanent" in a specific profile, since you'll have to first delete or edit the user.js file to remove the entries before the preferences can be changed in the application. This has the advantage of locking in certain preference settings. A user.js file is also a way of documenting preference customizations and it makes it easier to transfer customized settings to another profile.

When you launch your Mozilla application, valid preferences you've added to the user.js file are automatically copied to the prefs.js file (located in the same profile folder) where all user-set preferences are stored. For this reason, you should make a backup copy of the prefs.js file before you create or edit the user.js file.  

> **wojox said:**
> I've been dabbling with those and was going to make one to go along with the Optimization page. Thanks for the link you updated about disabling IPv6 pointing to my site. I returned the favour: [http://wojox.homelinux.net/?p=33](http://wojox.homelinux.net/?p=33)

Thanks a lot for the link.

---

### Post by ankspo71 on 2010-02-08
Hi,
I think it's a great idea, but I don't think I will be able to help maintain the list though... (health issues). Here are some of my current must haves that haven't been mentioned yet, though.

'Shareaholic' would be a big hit with the socializers and bookmarkers.

'Status Buttons' Allows toolbar buttons to be moved to the status bar to make more room for the address bar and search bar. Nicer for people with poor screen resolutions. This works well with the addon called 'autohidestatusbar' too.

'Redirect Cleaner' gets rid of those pesky redirect urls.

'Zindus' (for thunderbird) for syncing address books with Gmail and Zimbra. 

Btw, nice list. I'll have to check out a few of those addons later.

---

### Post by lovinglinux on 2010-02-08
> **ankspo71 said:**
> Hi,
I think it's a great idea, but I don't think I will be able to help maintain the list though... (health issues). Here are some of my current must haves that haven't been mentioned yet, though.

Thanks a lot for your suggestions. I have changed the way people will be able to publish, by adding the option to just post them here and I take care of the rest. I guess this will be easier for those who doesn't have the time or are concerned about sending me their e-mail addresses.

> **ankspo71 said:**
> 'Shareaholic' would be a big hit with the socializers and bookmarkers.

Since Ubuntu is all about sharing, I think that extension deserves it's place. ;)

> **ankspo71 said:**
> 'Status Buttons' Allows toolbar buttons to be moved to the status bar to make more room for the address bar and search bar. Nicer for people with poor screen resolutions. This works well with the addon called 'autohidestatusbar' too.

'Redirect Cleaner' gets rid of those pesky redirect urls.

Thanks. I will test them and add to the collection as soon as I can.

> **ankspo71 said:**
> 
'Zindus' (for thunderbird) for syncing address books with Gmail and Zimbra.

I'm currently not dealing with Thunderbird extensions, but I'm considering this possibility. Thanks for the suggestions anyway.

> **ankspo71 said:**
> Btw, nice list. I'll have to check out a few of those addons later.

Thanks. I hope you like them.

---

### Post by lovinglinux on 2010-02-08
> **ankspo71 said:**
> 'Status Buttons' Allows toolbar buttons to be moved to the status bar to make more room for the address bar and search bar. Nicer for people with poor screen resolutions. This works well with the addon called 'autohidestatusbar' too.

Unfortunately, that extension hasn't been updated since June 5, 2008 and it has a major incompatibility with Organize Status Bar extension, preventing the user from customizing the tool bars (this is what happened here). The bug has been patched by a third-party and submitted to the author, but it hasn't been updated yet on Mozilla Add-ons site. So I'm not going to include it. Instead, I have already included the Organize Status Bar extension, which is really nice.

Nevertheless, you can get the patched version from [here](http://yellow5.us/firefox/osb/) (see note on that page).

---

### Post by lovinglinux on 2010-02-08
Just added gPDF, which scan webpages for pdf links and set them to open with Google PDF viewer. Works like a charm.

---

### Post by arnab_das on 2010-02-08
great great concept. awesome initiative. i hope canonical approves it (without adding a yahoo add-on to that list :P ) great work!

btw, a request. can there be such a list for chromium/google chrome? recently the no of extension for chrome has skyrocketed, and also an increasing no of users are moving towards chrome. so, if u can, maybe u could compile a list of that as well.

---

### Post by lovinglinux on 2010-02-08
> **arnab_das said:**
> great great concept. awesome initiative. i hope canonical approves it (without adding a yahoo add-on to that list :P ) great work!

btw, a request. can there be such a list for chromium/google chrome? recently the no of extension for chrome has skyrocketed, and also an increasing no of users are moving towards chrome. so, if u can, maybe u could compile a list of that as well.

Thanks for your comments.

Unfortunately, I don't have the energy to search, test and publish extensions for both browsers, since I'm also publishing extension reviews and tips on my blog, along with my own personal extension collections (much bigger than this one). Not to mention the development of my own Firefox extensions, which requires a lot of work. So prefer to do it for the browser I like and support. Additionally, as far as I know, only Mozilla offers tools for easily creating collections and adding/removing/downloading new extensions to/from them. So doing that for Chrome/Chromium would require manually editing the list of extensions, which is something I was trying to avoid when I created my collections at Mozilla Add-ons site.

---

### Post by lovinglinux on 2010-02-09
The collection has been deleted.

> **Note:** Canonical denied my request to name the collection "Ubuntu Community". I don't know how to rename it to something else meaningful and in tune with the idea of the project, without violating Ubuntu's trademarks, so I decided to drop the project entirely and focus on [my own Add-on Collections](http://lovinglinux.megabyet.net/?p=36). I'm really sorry.


---

