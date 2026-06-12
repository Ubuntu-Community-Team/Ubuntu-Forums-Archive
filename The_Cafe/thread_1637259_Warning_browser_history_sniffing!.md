---
title: "Warning: browser history sniffing!"
date: 2010-12-04
forum: The Cafe
---

### Post by lovinglinux on 2010-12-04
Several sites are exploiting a well known browser vulnerability, which allows the to sniff what other sites you have visited, by checking the color of the hyperlinks rendered by your browser.

[http://blogs.forbes.com/kashmirhill/2010/11/30/history-sniffing-how-youporn-checks-what-other-porn-sites-youve-visited-and-ad-networks-test-the-quality-of-their-data/](http://blogs.forbes.com/kashmirhill/2010/11/30/history-sniffing-how-youporn-checks-what-other-porn-sites-youve-visited-and-ad-networks-test-the-quality-of-their-data/)

Don't believe it? Test it [here]("http://startpanic.com/").

I have tested a few browser versions. Chrome 7.0.517.44 and Firefox 4.0b8pre are immune. Firefox 3.6.12 and Opera 11.0 beta are not. In Opera however, you can set [opera:config#VisitedLink|VisitedLinksState]("opera:config#Visited%20Links%20State"), to 0 or 1 to fix the problem. First disables the link state and the second limit it to the same domain.

In Firefox 3.6.12 I suppose you can avoid the issue with NoScript.

---

### Post by Spice Weasel on 2010-12-04
Turn off saving history until this is fixed, and just use bookmarks if you want to remember a page you visited. That's the only way around it. ;)

I'm surprised this vulnerability hasn't been exploited before.

---

### Post by Oxwivi on 2010-12-04
I don't use history or bookmarks. :D

---

### Post by jshepherd on 2010-12-04
Just tested mine - only history found was the link to the test.
I'm using Chromium.

---

### Post by koenn on 2010-12-04
strange that they're so concerned about privacy, and then have this too:
> Moreover, you can send your friend a special link via Startpanic.com mailing system. When your friend clicks it, you will receive the list of websites he has visited recently.

---

### Post by wilee-nilee on 2010-12-04
It don't got nothing on me, noscript, ghostery better privacy no history saved FF 3.6.12 other addons as well but youpron isn't a place I go. I also use bleachbit daily, all I'm trying to hide is any CC used on amazon for books.

---

### Post by The Real Dave on 2010-12-04
Firefox 4 Beta 7 seems fine.

I hadn't thought someone could exploit that. Still, anyone using a low power/old machine like me should notice the sudden spike in CPU usage.

---

### Post by sydbat on 2010-12-04
> **wilee-nilee said:**
> It don't got nothing on me, noscript, ghostery better privacy no history saved FF 3.6.12 other addons as well but youpron isn't a place I go. I also use bleachbit daily, all I'm trying to hide is any CC used on amazon for books.Nothing from me either. Similar set up. Of course if one was using IE...

---

### Post by CharlesA on 2010-12-04
The script caused my browser to stop responding, at which point, I selected "stop script"

O_o

---

### Post by chriswyatt on 2010-12-04
I'm using Firefox Beta 7 and it found nothing, zilch. :)

---

### Post by ssam on 2010-12-04
noscript stops it on firefox 3

---

### Post by MacUntu on 2010-12-04
Why would I want to make it harder for porn sites to recommend similar porn sites? :confused:

*justkidding*

---

### Post by wilee-nilee on 2010-12-04
> **MacUntu said:**
> Why would I want to make it harder for porn sites to recommend similar porn sites? :confused:

*justkidding*
:-\":-\":-\"

---

### Post by alexan on 2010-12-04
SRWare Iron (chromium build 7.0.520.0): [COLOR="DarkGreen"]**nothing found**[/COLOR]

Opera 11.00 (beta): [COLOR="Red"]**4 link found**[/COLOR]

results:
**sudo apt-get autoremove opera -y**

---

### Post by Frogs Hair on 2010-12-04
Strange , it only detects if I allow scripts for that page . A test or a new way fish ?

---

### Post by BigCityCat on 2010-12-04
The tab says warning browser history sniffing in firefox 4 beta.

---

### Post by Dustin2128 on 2010-12-04
hooray for me running ffox 4.0b8pre.

---

### Post by handy on 2010-12-04
Nothing found with Firefox 3.6.12, using NoScript, BeefTaco, BetterPrivacy & Greasemonkey with the *googlePrivacy* script (which is apparently a safer & more functional tool than GoogleSharing, you can view the script too).

I know, NoScript is all that is applicable for this test. :)

---

### Post by gradinaruvasile on 2010-12-04
> **lovinglinux said:**
> Several sites are exploiting a well known browser vulnerability, which allows the to sniff what other sites you have visited, by checking the color of the hyperlinks rendered by your browser.

[http://blogs.forbes.com/kashmirhill/2010/11/30/history-sniffing-how-youporn-checks-what-other-porn-sites-youve-visited-and-ad-networks-test-the-quality-of-their-data/](http://blogs.forbes.com/kashmirhill/2010/11/30/history-sniffing-how-youporn-checks-what-other-porn-sites-youve-visited-and-ad-networks-test-the-quality-of-their-data/)

Don't believe it? Test it [here]("http://startpanic.com/").

I have tested a few browser versions. Chrome 7.0.517.44 and Firefox 4.0b8pre are immune. Firefox 3.6.12 and Opera 11.0 beta are not. In Opera however, you can set [opera:config#VisitedLink|VisitedLinksState]("opera:config#Visited%20Links%20State"), to 0 or 1 to fix the problem. First disables the link state and the second limit it to the same domain.

In Firefox 3.6.12 I suppose you can avoid the issue with NoScript.

I use Opera 11 beta. How is this suppposed to work? I click on the check button and there is no history displayed (with the default settings).

---

### Post by lovinglinux on 2010-12-04
> **gradinaruvasile said:**
> I use Opera 11 beta. How is this suppposed to work? I click on the check button and there is no history displayed (with the default settings).

As far as I understand, it needs to actively check if you have visited a particular link. So perhaps the test didn't check for any sites you have on your history.

---

### Post by heldal on 2010-12-07
> **wilee-nilee said:**
> It don't got nothing on me, noscript, ghostery better privacy no history saved FF 3.6.12 other addons as well but youpron isn't a place I go. I also use bleachbit daily, all I'm trying to hide is any CC used on amazon for books.

Noscript is nice, but beware wrt Ghostery. It has been aquired by a commercial enterprise (Better Advertising) and reports its activities (blocked elements) to them. I.e parts of your browsing activities is logged by B.A.

---

### Post by Evil-Ernie on 2010-12-07
Mine smells like ripe cheese...

---

### Post by handy on 2010-12-07
> **heldal said:**
> Noscript is nice, but beware wrt Ghostery. It has been aquired by a commercial enterprise (Better Advertising) and reports its activities (blocked elements) to them. I.e parts of your browsing activities is logged by B.A.

That caused me to dump Ghostery.

I use Greasemonkey which allows me to use the googlePrivacy script. This script does more than Ghostery & it is available for inspection when you install it, so I know a lot of eyes that are far more knowledgeable than I am have perused the script.

---

### Post by kaldor on 2010-12-07
All clear on Iceweasel Beta 7.

Same with Google Chrome 9.0.570.1 dev.

What's all the fuss about?

---

### Post by 0per4t0r on 2010-12-07
Doesn't really concern me, as i have a strange habit to press ctrl+shift+del every few seconds..

---

### Post by Quadunit404 on 2010-12-07
> **heldal said:**
> Noscript is nice, but beware wrt Ghostery. It has been aquired by a commercial enterprise (Better Advertising) and reports its activities (blocked elements) to them. I.e parts of your browsing activities is logged by B.A.

Ghostery doesn't track blocked elements and report them to Better Advertising unless you opt in to GhostNet or whatever it's called. It's disabled by default.

---

### Post by MasterNetra on 2010-12-07
My history isn'remembered so it found nothing from me on firefox. ;)

---

### Post by handy on 2010-12-07
> **MasterNetra said:**
> My history isn'remembered so it found nothing from me on firefox. ;)

Both Firefox & I share the same situation re. memory, though in Firefox I set it that way. As far as my own memory is concerned, I guess I just have to blame it on the cumulative effects of age & injury...

---

### Post by cgroza on 2010-12-07
> **CharlesA said:**
> The script caused my browser to stop responding, at which point, I selected "stop script"

O_o
The script made my broser crawl. Switching tabs took forever. It found the only 12 sites I visit every day but not facebook.

---

