---
title: "Firefox Noscript"
date: 2010-01-19
forum: Security
---

### Post by Silvertones on 2010-01-19
I want to make sure I have the philosophy of this add-on correct so as not to make things worse.
1. Without noscript no matter what web site I go to all script and objects are allowed to run.
2. With noscript if I go to a website that has been safe, such as this one, my bank etc, I would allow all script & objects to run.
3. If a good site that I have allowed all script to run gets hacked then the bad script would be allowed to run however I'm no worse off then if I wasn't running noscript.
4. If a good site that I have allowed all script to run should send up a noscript warning this is a good indication that they've been hacked.

---

### Post by balaknair on 2010-01-19
I'll try to answer your queries one by one

1) Without noscript no matter what web site I go to all script and objects are allowed to run.

True, unless you change the settings to disable Javascript, Java in Edit> Preferences> Content, where you can either enable/disable them for all sites(not on a site by site basis). With NoScript you can choose which sites are allowed and which are not.

2) With noscript if I go to a website that has been safe, such as this one, my bank etc, I would allow all script & objects to run.

I wouldn't advise that. Enable your bank's site to run scripts, but block other sites from running scripts on that page. Even 'safe' sites/pages have scripts from other sites running on them, usually as ads or flash videos, search tools etc. They're the really risky aspects, since the bank or your trusted site has no control over security of these other sites. So you'd be better off blocking third party scripts/objects except the ones necessary for full functionality of your site.
eg: On Ubuntuforums, you need to allow both ubuntuforums.org as well as yahooapis.com for the site to work, but you can block google-analytics.com scripts safely and the site will still work. You can even let the third party sites run withtemporary permissions.
This aspect of NoScript is especially useful to protect against Drive-By downloads using hacked Banner Ads on some 'safe' sites.

3) If a good site that I have allowed all script to run gets hacked then the bad script would be allowed to run however I'm no worse off then if I wasn't running noscript.

In most cases, yes.

4) If a good site that I have allowed all script to run should send up a noscript warning this is a good indication that they've been hacked.

Not necessarily, maybe they've just changed the way their web page works or moved it to a new domain, or new third party sites are now running scripts on that page. Keep in mind that the third parties may be bad guys who've hijacked an ad shown there.

---

### Post by tubbygweilo on 2010-01-19
Silvertones, to echo the advice from balaknair;

Only allow the minimum of scripts you need to perform your task.
Take your time to build your white list. 
I know this approach may at first seem slow and long winded but once you have a white list covering you daily surfing things will need hardly any intervention at all.

---

### Post by Silvertones on 2010-01-19
OK thanks. I'll CAREFULLY do that.

---

### Post by Silvertones on 2010-01-19
OK I'm getting a better feel for this. Correct me if I'm wrong.
When I go to a site I get the indication that noscript is blocking the site. If I click on the "S" it shows what's trying to run. For instances If I go to MajorGeeks.com, a very reputable site, what I see when I click the "S" is** Majorgeeks.com** and about 6 other entries. Because I trust MG it's OK to allow that one but do nothing with the others as they're third party. If the website doesn't work quite right then I need to decide which of the other 6 to allow and so on.
Is this sort of right? Minimize the amount of third party script that runs. For instance "Google Analytics" does nothing advantageous for me and is not needed. I have marked it as untrusted and this seems to be a global setting.

---

### Post by tubbygweilo on 2010-01-19
It is all trial and some error at first;) *Google Analytics* may not be required by a site but *Google Static* is if the site makes use of a Google map. So click wisely and be prepared to rethink your options every now and again especially when visiting new sites. I took me a few goes to realise than [http://www.guardian.co.uk/](http://www.guardian.co.uk/) made use of [http://www.brightcove.com](http://www.brightcove.com) when playing video content, you live and learn.

---

### Post by bodhi.zazen on 2010-01-19
Trial and error FTW !!!

After a while you will get the feel of it.

I temporarily allow most sites, and only white list trusted sites I visit with some frequency.

Most third party sites are not required, but some are.

---

### Post by Silvertones on 2010-01-19
I have only a small handfull of sites I go to regularly & most don't even have third party script. I'm also using the "Browser Defender" Firefox add on.

---

### Post by bodhi.zazen on 2010-01-19
> **Silvertones said:**
> I have only a small handfull of sites I go to regularly & most don't even have third party script. I'm also using the "Browser Defender" Firefox add on.

Although "Browser Defender" might sound nice, it is not really a security feature as it rates know web sites.

You can use several plugins to do this WOT is another.

NoScript blocks javascript and flash, both of which can be malicious.

Now I agree trusted sites tend not to have malicious scripts so "Browser Defender" helps, but only with potential known threats and only after the fact (someone has to report the site).

NoScript prevents the problem (in theory) in the first place.

---

### Post by dogdo on 2010-01-19
To use gmail i have to allow google-can google be trusted? i dont like having to use google search and letting google through noscript at the same time.

---

### Post by running_rabbit07 on 2010-01-19
Use Thunderbird for Gmail.

---

### Post by bodhi.zazen on 2010-01-19
> **dogdo said:**
> To use gmail i have to allow google-can google be trusted? i dont like having to use google search and letting google through noscript at the same time.

I think google can be trusted in terms of javascript.

Privacy is different, install and configure Optimize Google.

---

### Post by Silvertones on 2010-01-20
I've got the hang of Noscript now.
The way I use Browser Defender is if I do a search in Google I just stay away from the sites marked as bad.

---

