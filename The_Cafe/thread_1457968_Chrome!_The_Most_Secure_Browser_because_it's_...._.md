---
title: "Chrome! The Most Secure Browser because it's .... ohwait."
date: 2010-04-19
forum: The Cafe
---

### Post by Tristam Green on 2010-04-19
Security!  Only as good as the observance of the people it supposedly protects.

[http://www.theregister.co.uk/2010/04/19/google_chrome_trojan/](http://www.theregister.co.uk/2010/04/19/google_chrome_trojan/)

> Miscreants have created a Trojan that poses as a Google Chrome extension.

Spammed messages attempt to dupe prospective marks into trying an add-on that "helps you better organise your documents received in your email".

Interested parties are pointed towards a counterfeit Google Chrome Extensions page, which offers a malware executable.

More observant punters will notice that the download is offered in an .exe file and not a .crx Google Chrome extension. Such markers are easily missed, however.

---

### Post by Sand &amp; Mercury on 2010-04-19
As much as the word 'foolproof' gets bandied about, especially when it comes to things like security, nothing could ever be so. The fool is truly a force to be reckoned with.

---

### Post by asddf on 2010-04-19
Erm......it says people click a link to a fake chrome website, that asks them to download a .exe

That's not really anything to do with Chromes security at all.

Since it's just a webpage that people go to and asks them to download an .exe that would be the same on anyone with any web browser, with any operating system would still be asked to download the .exe.(although it wouldn't execute on Linux)

---

### Post by madnessjack on 2010-04-19
This is social engineering

Nothing to do with Chrome's security 

FUD

---

### Post by dannyboy79 on 2010-04-19
please change title of thread, this is very misleading.  is this really Google Chrome's fault? Does this trojan show up on any website that is browsed using Chrome? Does it show up because a person is using Chrome?

---

### Post by lovinglinux on 2010-04-19
> **Tristam Green said:**
> Security!  Only as good as the observance of the people it supposedly protects.

[http://www.theregister.co.uk/2010/04/19/google_chrome_trojan/](http://www.theregister.co.uk/2010/04/19/google_chrome_trojan/)

The problem you have reported is a social engineering and phishing attack, not a browser issue. There is no indication that the browser itself was involved the installation of the trojan or that the browser security has been compromised, although it should at least detect that the site didn't belong to Google. 

Coincidentally, I have posted my concerns about Chrome extensions on another thread a couple of days ago (they have been merged). This is real potential problem for Chrome users (see quote below).

> **lovinglinux said:**
> You also need to consider add-ons. Since both browsers offer third-party extensions, there are important additional security and privacy issues.

I never uploaded any extension to Google Chrome Gallery, but from what I have read, Google pretty much use the "my *** is covered by terms of service" approach. Here are some links with interesting info:

[LIST]
[*][Google Chrome Gallery Terms of Service](https://chrome.google.com/extensions/intl/en/gallery_tos.html)
[*][Google Chrome Gallery Developer Agreement](https://chrome.google.com/extensions/intl/en/dev_tos_text.html)
[*][Extensions: Information for developers](http://www.google.com/support/chrome/bin/answer.py?hl=en&answer=113909)
[/LIST]

One particular info about chrome extensions got my attention:

> What is the approval process for extensions?

Most extensions won't go through an approval process before being listed in the gallery. The exception to this rule are extensions which utilize the NPAPI interface, or extensions which access file:// URLs. Such extensions will be queued for review before they can be listed in the gallery. 

[NPAPI](http://en.wikipedia.org/wiki/NPAPI) is Netscape Plugin Application Programming Interface, which basically means **plugins**. Most extensions won't fit into this category.

If you don't dig into Google's terms of service and faqs, you will never know that Chrome extensions are not reviewed. There is no indication on any extension page if it has been reviewed or not. Nevertheless, when you try to install an extension, it does prompt you for confirmation with some important details about privacy.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=153320&stc=1&d=1271318558[/IMG]

I don't make Chrome extensions, so I'm not familiar with their security. I have read somewhere that is hard to port some popular Firefox extensions to Chrome, due to the limitations of what the extension can do in Chrome. I'm not sure if this is true. Anyway, that doesn't mean Firefox extensions are insecure by nature. For example I develop an extension that adds a button to Ubuntu forums quote forms, so you can save a forum post as quote, to paste it later wherever you want. To do that I had to do some complicated safe maneuvers, because Firefox doesn't allow unprivileged content (web pages) to access the extension functions directly. 

Anyway, Mozilla takes different approached when dealing with third-party extensions. You can host extensions on Mozilla site or only publish the information with a link to your web site. The second type cannot be installed automatically from Mozilla site and there is a big yellow warning surrounding the extension link.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=152988&d=1271027640[/IMG]

Hosted extensions are only reviewed if the developer submit them for public status. Meanwhile, the receive the status of experimental and the user needs to click a checkbox with a warning before downloading. This type of extension is not updated automatically by Firefox add-on manager.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=152987&d=1271027640[/IMG]

The policy on Firefox experimental extensions will change soon. Basically they will not be listed on Mozilla Add-ons site, thus will be only accessible through direct link. Developers will have a period of 90 days after adding their extensions to the site, to submit them for editor review. After this period, the extension will be removed from the site.

Hosted+public extensions need to be manually reviewed by an editor. The process is rigorous and when an editor denies it, you receive a report with information why it hasn't been approved. Additionally, every extension is automatically scanned for malware and possible insecure javascript code or blacklisted file types. If an extension is flagged, then it must be reviewed by a coordinator. Even new versions of extension that have already been approved need to be manually reviewed before receiving public status.

There are also additional rules in regard to privacy. Extensions that save user personal information, must comply with the Private Browsing Mode, thus not saving any information while this mode is activated, otherwise they are not approved.

I'm not sure if this info will be useful to you, but I like talk about this subject and I thought would be interesting to post some info. I'm not a security expert and I'm barely an amateur extension developer, but I never had a problem with Firefox and use it since version 0.9. I'm not a prude paranoid web surfer and admit I click things and access sites I shouldn't (security wise), but NoScript, AdBlockPlus, Better Privacy and Ghostery seems to do a good job keeping my dirty habits under control.

[color="Sienna"][list]

[*]**Source:** [[color="DarkSlateGray"] Re: Is Firefox or Chrome more secure?[/color]]("http://ubuntuforums.org/showpost.php?p=9125173")

[*]**Tags:** [[color="DarkSlateGray"]Is Firefox or Chrome more secure[/color]]("http://www.google.com/search?q=Is+Firefox+or+Chrome+more+secure+site:ubuntuforums.org")

[*]**Powered by: **[[color="DarkSlateGray"]QuoteMarks[/color]]("http://lovinglinux.megabyet.net/?page_id=555")[/list][/color]

---

### Post by Tristam Green on 2010-04-19
Requesting title change to ** Chrome users are smrt. They are less apt to get malware because they use FOSS. owait  ** in that case.

And yes, this does have something to do with Chrome's security.  It's not a browser exploit, but it's an exploit of the users who are using what is loudly touted as one of the most secure browsers on the market.

Just because *you* are smart enough to recognize a fake browser plugin, does not mean that the average joe who you have "converted" to Chrome from any other browser is also.


FUD....honestly...

---

### Post by asddf on 2010-04-19
But in any way this has nothing to do with chromes security, someones just put a virus on a webpage, if anything this should be aimed at "Windows really crappy allows virus to mess up computer" since it's Windows fault, not chromes.

---

### Post by mickie.kext on 2010-04-19
> **Tristam Green said:**
> Requesting title change to ** Chrome users are smrt. They are less apt to get malware because they use FOSS. owait  ** in that case.

And yes, this does have something to do with Chrome's security.  It's not a browser exploit, but it's an exploit of the users who are using what is loudly touted as one of the most secure browsers on the market.

Just because *you* are smart enough to recognize a fake browser plugin, does not mean that the average joe who you have "converted" to Chrome from any other browser is also.


FUD....honestly...

You are still completely wrong, in more ways than one. Since others already proved you wrong about security, I will tell you that you got the wrong guy. Chrome is not FLOSS. It is proprietary browser. If you want to bash FLOSS for being FLOSS, you should be bashing Mozilla.

---

### Post by gnomeuser on 2010-04-19
Chrome still warn you when downloading .crx files as I understand and they actively warn people against websites known to carry malware using an autoupdated malware website list.

Extensions also can't autoinstall, you have to actively press okay to comfirm the access requests the extension make.

Chrome on Mac and Windows autoupdates, on Linux you get updates as part of your system updates and the entire repo is open, releases frequent. Correctness, Regression and performance testing is done down to every commit to ensure the code is in as optimal a state as possible.

Every tab is run in it's own sandboxed separate process, plugins are restricted (and a standard for this is actively being worked on by at least Adobe and Google). 

It is hard to do much more outside of plugging the holes as they are discovered and introduce the problem into our regression tests and continue to improve on it.

Chrome is incredibly secure by default.

---

### Post by swoll1980 on 2010-04-19
This whole thread makes zero sense to me.

---

### Post by Tibuda on 2010-04-19
> **mickie.kext said:**
> You are still completely wrong, in more ways than one. Since others already proved you wrong about security, I will tell you that you got the wrong guy. Chrome is not FLOSS. It is proprietary browser. If you want to bash FLOSS for being FLOSS, you should be bashing Mozilla.

you can install chrome extensions in the foss chromium.

---

### Post by mickie.kext on 2010-04-19
> **danielrmt said:**
> you can install chrome extensions in the foss chromium.

So?

---

### Post by Tibuda on 2010-04-19
> **mickie.kext said:**
> So?

yeah, so?

---

### Post by madnessjack on 2010-04-19
> **Tristam Green said:**
> 
Just because *you* are smart enough to recognize a fake browser plugin, does not mean that the average joe who you have "converted" to Chrome from any other browser is also.
Wrong- I'm actually pretty stupid.

I hit a fake Paypal email the other day. Chrome lit up red big-time! Thus, even I didn't continue to submit my financial details to a spam-bot.

Also, this wasn't a pluggin- it was an .exe file.

So, still FUD

---

### Post by gnomeuser on 2010-04-19
> **madnessjack said:**
> Wrong- I'm actually pretty stupid.

I hit a fake Paypal email the other day. Chrome lit up red big-time! Thus, even I didn't continue to submit my financial details to a spam-bot.

Also, this wasn't a pluggin- it was an .exe file.

So, still FUD

And every person not protected is one more person to partake in a botnet, have identity and/or credit information stolen, privacy exposed or being made into a silent spam/childporn distribution center. There are many good reasons to do these things. 

Google gains from people gaining more trust in the Internet as a platform which will bring them more users and more money as a result. 

We gain from reducing all these nasty problems and making the Internet a nicer place, and we increase the capacity of the pipes by removing the what 60% of it that comes from spam and other malicious activity. Faster, more stable Internet, I'm in.

So why is Chromium the only web browser to currently do all this, and doing it openly. I imagine there is so much to gain if we could make integrating similar levels of commit testing into Launchpad Ubuntu would improve leaps and bounds as projects learn how to work with these capabilities.

For now, despite this little extension problem, Chrome remains the single most secure major browser on the market right now. Saying otherwise requires a great deal of proof and justification.

---

### Post by V for Vincent on 2010-04-19
You know, the title still isn't relevant. This has nothing to do with closed/open source. Yes, chrome is (relatively) secure if you use common sense. If someone steals your password because you wrote it down, that doesn't make your OS insecure, either.

---

### Post by RiceMonster on 2010-04-19
> **danielrmt said:**
> yeah, so?

no, so?

---

### Post by Penguin Guy on 2010-04-19
> More observant punters will notice that the download is offered in an **.exe file** and not a .crx Google Chrome extension. Such markers are easily missed, however.
Therefore, it will not harm Linux.

---

### Post by phrostbyte on 2010-04-19
> **swoll1980 said:**
> This whole thread makes zero sense to me.

Failed attempt at trolling I think.

---

### Post by swoll1980 on 2010-04-19
> **phrostbyte said:**
> Failed attempt at trolling I think.

It would be like blaming Good Year for my flat tire, because someone through nails in the road, and I ran them over.

---

### Post by lisati on 2010-04-19
Closed at request of OP

---

