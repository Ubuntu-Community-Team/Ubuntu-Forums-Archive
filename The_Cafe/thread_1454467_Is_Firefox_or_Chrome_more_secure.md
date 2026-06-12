---
title: "Is Firefox or Chrome more secure?"
date: 2010-04-14
forum: The Cafe
---

### Post by Otis Spunkmiyer on 2010-04-14
I'd like to get some opinions concerning two different web browsers.
(and just the two, please)
**Firefox and Google Chrome.**
I'm using both on different operating systems Linux/Windows.
_What I'd like an opinion on is which one is most secure._

Please just opinions on security, not how quick one is over the other, or style/implementation.
Thank you in advance for any feed back.

---

### Post by new_tolinux on 2010-04-14
Not really security, but keep in mind that Google Chrome is from..... Google.
It is already the most common used search-engine, webmail-provider, etc.
It could be a security-risk in terms of privacy to also use Google Chrome.
But I have no proven evidence it is. I only know that that's a major reason to me to keep away from Chrome.

---

### Post by Crunchy the Headcrab on 2010-04-14
Chrome is the only browser that wasn't cracked at this years pwn2own. It wasn't cracked last year either.  Google does make good products, BUT they also watch everything you do.

---

### Post by aysiu on 2010-04-14
What does "most secure" mean exactly in this context?

With web browsers, there will *always* be new security holes that are discovered and/or exploited... and then patched. Firefox will have unpatched vulnerabilities that then get patched, and then Chrome will also have unpatched vulnerabilities that later get patched. Out of the box, neither is perpetually 100% secure.

Apart from software flaws, a lot of the security of the browser relies on the user: What sites do you visit? What links to you click on? Do you sometimes mistype URLs? Have you set certain file types to automatically execute after downloading?

How paranoid are you? The out of the box setups on both Chrome and Firefox try to balance convenience with security. You can always install extensions or add-ons to make the security a bit more hardened, at the cost of some convenience. Firefox has an add-on called NoScript that blocks pretty much everything interactive (Java, JavaScript, Flash) unless you specifically and intentionally whitelist a website. If Chrome doesn't already have an extension like that, it probably will soon.

In the end, though, there is no 100% security. There is no invincibility on the internet. Even a trusted site can be cracked into on the server end and compromise your security and/or privacy.

If you have common sense and use the most up-to-date version of Chrome or Firefox, you'll probably be just as safe with either browser.

---

### Post by H4F on 2010-04-14
> **new_tolinux said:**
> Not really security, but keep in mind that Google Chrome is from..... Google.
It is already the most common used search-engine, webmail-provider, etc.
It could be a security-risk in terms of privacy to also use Google Chrome.
But I have no proven evidence it is. I only know that that's a major reason to me to keep away from Chrome.

Same think here. I already use gmail and search. and thats alot

---

### Post by hackb0y294 on 2010-04-14
> **Crunchy the Headcrab said:**
> Chrome is the only browser that wasn't cracked at this years pwn2own. It wasn't cracked last year either.  Google does make good products, BUT they also watch everything you do.

I agree. I would say Firefox is more secure, in terms of the manufacturer monitoring you.

---

### Post by Otis Spunkmiyer on 2010-04-14
OK, let me ask this, and before I do, let me say Google watching me doesn't bother me.  But here's what might.
Could a hacker get into Google themselves and get the information Google is storing on everyone ?

---

### Post by new_tolinux on 2010-04-14
> **Otis Spunkmiyer said:**
> OK, let me ask this, and before I do, let me say Google watching me doesn't bother me.  But here's what might.
Could a hacker get into Google themselves and get the information Google is storing on everyone ?
Can someone break into your house?

Ofcourse they can.

_Anything_ connected to the internet _can_ be hacked.

---

### Post by Otis Spunkmiyer on 2010-04-14
Can anyone without a doubt say Firefox stores no information on people ? 
What is Google's purpose in collecting information ?

---

### Post by bash on 2010-04-14
It depends on what you understand under secure. Secure as in respect to your privacy? Then choice would be pretty simple. Don't use Chrome. It's has closed-source parts so no matter what is promised something *could* (to the tin foil hat degree) always be hidden. If you still really want something crome-ish, use the open-source Chromium builds ... or Firefox. Personally I find Firefox allows a far more fine grained control 
over what the browser records, allows, blocks and so on, than any other browser I have tried (Chrome(ium), Midori, Opera, IE, ...). And it has tons of privacy related add-ons  such as NoScript, AdBlock, Click2Flash, BetterPrivacy (although Chrome(ium) is catching up in this regard).

If you mean security from an exploitability stand-point I would say Chroe(ium) wins hands down. Chrome is the only browser besides IE on Windows to currently implement a proper sandboxing concept; isolating each webpage and with this greatly minimizing the harm (not the possibility) of exploits. So if this is the deciding factor than Chrome and Chromium would be your choice.

---

### Post by swoll1980 on 2010-04-14
> **Crunchy the Headcrab said:**
> Chrome is the only browser that wasn't cracked at this years pwn2own. It wasn't cracked last year either.  Google does make good products, BUT they also watch everything you do.

Not that chrome can't be cracked. The task was to open calc. Because of the sand-boxing in chrome, that particular task was much harder to achieve in chrome, therefor not attempted.

---

### Post by Otis Spunkmiyer on 2010-04-14
> **bash said:**
> (to the tin foil hat degree)


Classic !   =D>

---

### Post by new_tolinux on 2010-04-14
> **Otis Spunkmiyer said:**
> Can anyone without a doubt say Firefox stores no information on people ? 
What is Google's purpose in collecting information ?
They probably do store your IP-adress when you visit their sites.
They probably do store some other information you supply.

Correct me if I'm wrong, but as I remember Google even admitted storing information for business-purposes.

And for what is stored: your IP is probably worthless, it only tells your Internet Provider and your country, and with some Internet Providers it is also simple to find out in which place you live.
It's nice to statistics that (for example) today 1 billion visitors from New York used Firefox to visit [www.example.com]("http://www.example.com"), but there it ends.
To combine your personal details (for example from a gmail account) with your browsing behaviour...... sounds like "Big Brother is watching you".

Edit: the only thing I saw at my proxy-monitor is FF connecting to check for updates (Windows).

---

### Post by gradinaruvasile on 2010-04-14
Well Firefox was canned at This year's CanSecWest's Pwn2Own contest...
Chrome seems a bit tougher nut to crack according to the participants comments (also Google patched up Chrome a few days before the contest, some say there were some bugs known by the pwn2own contenders that got patched then - strange coincidence?).

[http://www.downloadsquad.com/2010/03/25/pwn2own-2010-google-chrome-is-the-last-man-standing/](http://www.downloadsquad.com/2010/03/25/pwn2own-2010-google-chrome-is-the-last-man-standing/)

---

### Post by aysiu on 2010-04-14
> **Otis Spunkmiyer said:**
> 
What is Google's purpose in collecting information ? All answered here:
[http://www.google.com/privacy_faq.html](http://www.google.com/privacy_faq.html)

---

### Post by Otis Spunkmiyer on 2010-04-14
Thank you.
Very informative, and no apologies from them I note.
So, they say they 'try' to strike the right balance.  But I do understand the business they are in and why such information is needed.  If they stoped collecting eventually we'd all have to go back to thinking in stead of Go-ogling.

---

### Post by Otis Spunkmiyer on 2010-04-14
So here's the brain storm.

We know to stay off porn sites.    Don't open any dubious files, or unsolicited Emails.  (although the reports out now say even Emails you think you know are subject for tighter scrutiny)

Other then that, if your doing monetary transactions, conveying sensitive information, or poking your boss's wife, then stay away from Google Chrome.

---

### Post by aysiu on 2010-04-14
> **Otis Spunkmiyer said:**
> 
Other then that, if your doing monetary transactions, conveying sensitive information, or poking your boss's wife, then stay away from Google Chrome. I don't see why you should stay away from Chrome. It isn't really in Google's best financial interests to snoop into your passwords or infidelities. They want to know search trends.

I have a better idea. If you want privacy, don't use a computer. Don't have a bank. Don't use money or pay taxes. Don't have a library account or a discount card at a grocery store. In fact, don't shop. Just live in a remote area in which you have a self-sustaining farm and house you built yourself with your own bare hands.

If the government and corporations (which increasingly work together) want to know your sensitive information, they'll find it.

More details here:
[Privacy on the internet doesn&#8217;t exist](http://www.psychocats.net/ubuntucat/privacy-on-the-internet-doesnt-exist/)

---

### Post by ali_etoom on 2010-04-14
i guess google chrome is secure enough because google uses great algorithms to secure gmail and firefox is great browser.

---

### Post by MasterNetra on 2010-04-14
> **aysiu said:**
> What does "most secure" mean exactly in this context?

With web browsers, there will *always* be new security holes that are discovered and/or exploited... and then patched. Firefox will have unpatched vulnerabilities that then get patched, and then Chrome will also have unpatched vulnerabilities that later get patched. Out of the box, neither is perpetually 100% secure.

Apart from software flaws, a lot of the security of the browser relies on the user: What sites do you visit? What links to you click on? Do you sometimes mistype URLs? Have you set certain file types to automatically execute after downloading?

How paranoid are you? The out of the box setups on both Chrome and Firefox try to balance convenience with security. You can always install extensions or add-ons to make the security a bit more hardened, at the cost of some convenience. Firefox has an add-on called NoScript that blocks pretty much everything interactive (Java, JavaScript, Flash) unless you specifically and intentionally whitelist a website. If Chrome doesn't already have an extension like that, it probably will soon.

In the end, though, there is no 100% security. There is no invincibility on the internet. Even a trusted site can be cracked into on the server end and compromise your security and/or privacy.

If you have common sense and use the most up-to-date version of Chrome or Firefox, you'll probably be just as safe with either browser.

Don't forget the better privacy addon, it clears flash cookies. Clearing cache from the browser the normal way doesn't clear out the flash cookies.

---

### Post by drreed on 2010-04-14
> **new_tolinux said:**
> Not really security, but keep in mind that Google Chrome is from..... Google.
It is already the most common used search-engine, webmail-provider, etc.
It could be a security-risk in terms of privacy to also use Google Chrome.
But I have no proven evidence it is. I only know that that's a major reason to me to keep away from Chrome.


Why support a company that is archiving your and your kids emails? Why do they need a copy of the emails my son sends to his girlfriend? Or his mom? They are EVIL. They have a plan you can be sure, or they wouldn't be doing it. They own it because your using a free service. Big mistake. 10 or 20 years from now it's going to come back to haunt all of us.:confused:

---

### Post by adeypoop on 2010-04-14
> **new_tolinux said:**
> Not really security, but keep in mind that Google Chrome is from..... Google.
It is already the most common used search-engine, webmail-provider, etc.
It could be a security-risk in terms of privacy to also use Google Chrome.
But I have no proven evidence it is. I only know that that's a major reason to me to keep away from Chrome.

I agree, sometimes worries me how much google already know and some of the direction they are heading in with disregard for people's privacy. They seem to be becoming too big and potentially scary. The end benefit is we get better adverts from them, gee great. Imagine if they start  misusing the power they are accumulating though.
 
In terms of bugs in the code which malicious coders can exploit I'd say they are probably on a par.

---

### Post by drreed on 2010-04-14
> **Otis Spunkmiyer said:**
> OK, let me ask this, and before I do, let me say Google watching me doesn't bother me.  But here's what might.
Could a hacker get into Google themselves and get the information Google is storing on everyone ?

of course they can, they probably have, and they definitely will. What about "big brother"? You can get a judge to issue a subpoena for almost anything. If you are ever accused of something they will get those records, and then use anything they find in the data to make you look like a bad guy to the jury. Ever send a rant to someone? How about a newspaper or e-zine you didn't agree with? How about a email to a girl friend or wife? Man . . .the idea is creeepy. Their probably kicking back right now reading through them and getting a laugh. 

How about a disgruntled employee? How do you know that person won't gradually post a few million emails somewhere on a server? Remember what happened to the "climate change" scammers? Imagine if that were google.

I'd think they were a GREAT company if they'd get rid of those archives, and start letting users really delete their mail. Until then . . .

---

### Post by Otis Spunkmiyer on 2010-04-14
> **drreed said:**
> Big mistake. 10 or 20 years from now it's going to come back to haunt all of us.:confused:

And everyone was so worried it was the government creating 'The New World Order'
When all along it's been 'Corporate America' and it's 'Global Allies'.

You just love how Google threatens to pull out of China but thens decides to route through other Asia country's.  Yeah, we call that 'China Big Brother' making it 'lucrative' to stay.
(so they can continue to monitor their citizens)

The more and more I think about the whole scheme of things, the more it smells.  And now that Firefox has HTML I don't even miss my Gmail account.  But it does display web pages for me anyway, just my opinion, allot richer, more depth and so on.  But they remind me of Nike and their slave labor for a $150 dollor pair of gym shoes.  Gee whiz..

---

### Post by lovinglinux on 2010-04-15
> **Otis Spunkmiyer said:**
> Can anyone without a doubt say Firefox stores no information on people ? 
What is Google's purpose in collecting information ?

[This report](http://blog.mozilla.com/metrics/2010/03/31/mozillas-q1-2010-analyst-report-state-of-the-internet/) should give you an idea of what Mozilla collects from Firefox users.

Additionally, it also collects information about installed add-ons. For instance, any add-on developer has access to some information about their add-on users, like add-on version, locale, OS, Firefox version, download source and others . Nevertheless, this information is non-identifiable and only available if the user choose to automatically check for add-ons updates.

> **gradinaruvasile said:**
> Well Firefox was canned at This year's CanSecWest's Pwn2Own contest...
Chrome seems a bit tougher nut to crack according to the participants comments (also Google patched up Chrome a few days before the contest, some say there were some bugs known by the pwn2own contenders that got patched then - strange coincidence?).

[http://www.downloadsquad.com/2010/03/25/pwn2own-2010-google-chrome-is-the-last-man-standing/](http://www.downloadsquad.com/2010/03/25/pwn2own-2010-google-chrome-is-the-last-man-standing/)

What about Firefox 32bit on Linux? The article only mention Firefox on Windows 7 x64. 

> **Otis Spunkmiyer said:**
> I'd like to get some opinions concerning two different web browsers.
(and just the two, please)
**Firefox and Google Chrome.**
I'm using both on different operating systems Linux/Windows.
_What I'd like an opinion on is which one is most secure._

Please just opinions on security, not how quick one is over the other, or style/implementation.
Thank you in advance for any feed back.

You also need to consider add-ons. Since both browsers offer third-party extensions, there are important additional security and privacy issues.

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

---

### Post by cong06 on 2010-04-15
> **aysiu said:**
> I don't see why you should stay away from Chrome. It isn't really in Google's best financial interests to snoop into your passwords or infidelities. They want to know search trends.

I have a better idea. If you want privacy, don't use a computer. Don't have a bank. Don't use money or pay taxes. Don't have a library account or a discount card at a grocery store. In fact, don't shop. Just live in a remote area in which you have a self-sustaining farm and house you built yourself with your own bare hands.

If the government and corporations (which increasingly work together) want to know your sensitive information, they'll find it.

More details here:
[Privacy on the internet doesn’t exist](http://www.psychocats.net/ubuntucat/privacy-on-the-internet-doesnt-exist/)

I think that the "tin hats" (for lack of a better description) need to re-read this.

Honestly, what makes you think you're so special that a goverment corporation woudl *care* about your e-mail to your girlfriend that you deleted, or even what porno sites you went to?
Maybe if you're a government spy you shouldn't be using gmail to forward information about United States Military secrets to the Russian government, and it's probably a bad idea to plan the bombing of a major government building over Google wave.
But really, what are you worried about Google "finding out"? (I really am curious)

Now, just as a precaution I probably wouldn't send my credit card details over e-mail... not that I think it's going to be stolen by google (I think it won't be stolen), but I just don't want to take that risk.

---

### Post by User Name 6 on 2010-04-15
Surely more commonly used browsers are going to be more often targeted with programs that exploit their particular weaknesses. No one's going to take much trouble to attack a browser with a tiny share of the user market? Hence the browser with the most users IE is probably somewhat less secure than those that are less often used like Chrome or Ninja or Pirateshark**&#8482;**: Quantumcrikey! Pro-gravity V2.3736251e or whatever they are calling themselves these days.

---

### Post by tica vun on 2010-04-15
Firefox doesn't tell Google corp. about your browsing habits.

---

### Post by gradinaruvasile on 2010-04-15
> **lovinglinux said:**
> 

What about Firefox 32bit on Linux? The article only mention Firefox on Windows 7 x64. 



AFAIK on 64-bit the ASLR protection is supposed to be better than in 32-bit... Anyway, i just read this sonewhere, i know the implementation (or the lack of it, i recall that DEP wasnt activated on Firefox) is the key, not the theory.

Comparing by these standards, all lesser-used browsers - Opera, Konqueror, you name it are better security-wise than Firefox. The Pwn2Own contest is not a security level measuring and comparison tool (granted the Safari-owning trend raises questions... Internet Explorer is no surprise, its routine).
They just prove something that everyone somewhat informed about informatics know: there is not 100% safe program/OS. I think thats PR why they eat IE+Safari for breakfast...

IRL a knowleadgeable user will hardly fall for social engineering whatever the browser/OS.
And the ones who dont know/care - they will be vulnerable anyway even the browser/OS asks them "Do you want to run this program etc..." because they have the yes-i agree-next-next-finish routine learned... The OS makers cannot protect the users if they just want ease of use regardless of the risks (and that makes up the bulk of computer users).

---

### Post by gnomeuser on 2010-04-15
Chrome is provably the most secure browser, however it also depends on the system it runs on. E.g. it can sandbox each tab in it's own process with the underlying system supports it. Additionally it will use preventive measures such as randomization  if it is easily supported on the platform in a generic fashion.

If you want to check the record, e.g. read about CanWests pwn2own contest. The only surviving browser in those the last few times has been Chrome and it is down to it's design. It simply has additional layers of separation which will have to be broken.

This also gives nice stability and recovery, if a tab crashes for some reason just reload it.

The Chromium project (From which Chrome is built) entirely open source, if you get Chromium from the Ubuntu repos (it's in Lucid at least) then you get a Chromium built from the official sources using our default compiler. 

The Google distribution of Chromium, Google Chrome does have some things you cannot opted out of such as the RLZ reply it sends to Google when something interesting happens such as a search is performed in the omnibox, a page crashes and other error conditions. This is however not part of Chromium and you can opt out of any other service that requires sending data to google (such as the integration with suggestions) in both Chrome and Chromium.

Chrome is more secure by miles than any of the major browsers.

The one but is that sandboxing on Linux currently as I understand isn't working since we can't agree on a way to do it. The in-kernel solution one might adopt is SELinux but only Fedora has adopted this, everyone else seems to be on minor frameworks or use the out of kernel AppArmor. Most still have not deployed anything though. They need to pick the right way or invent an acceptable common way to do it. This is being worked on as part of the ChromiumOS project amongst other places.

---

### Post by tica vun on 2010-04-15
> **gnomeuser said:**
> Chrome is provably the most secure browser

Chrome reports your browsing habits to Google. How this can be considered "secure" by anyone is beyond me.

---

### Post by aysiu on 2010-04-15
> **tica vun said:**
> Chrome reports your browsing habits to Google. How this can be considered "secure" by anyone is beyond me.
Then I suggest you read exactly what they collect:
[http://www.google.com/chrome/intl/en/privacy.html](http://www.google.com/chrome/intl/en/privacy.html)

Most of it seems harmless to *me*. A lot of it *you* can opt out of, though.

---

### Post by scouser73 on 2010-04-15
Firefox and Chrome are secure (in my opinion), there will always be security issues with any browser no matter how much a user thinks otherwise.

> **tica vun said:**
> Chrome reports your browsing habits to Google. How this can be considered "secure" by anyone is beyond me.

Yes Google collect data entered into the Omnibox, and I wouldn't be surprised if Microsoft did the same with Internet explorer, it seems that searching via an Internet Browser, rather than a Search Engine is inextricably linked.  You should look at what each companies privacy policy outlines for the data that's collected.

---

### Post by drreed on 2010-04-15
Microsoft doesn't need to read browser caches. They have spyware in windows capable of reporting everything you do. It's called Genuine Advantage

It gives them a genuine advantage over other spies (like google) Google may be able to see a lot that you do online M$ can see everything you do on that computer, including what you do on Intranets.

Rather than post a flickr link that may well be gone tomorrow, do a search for images using the keywords "google 2084"

And by all means, use google to do it. It's funny and appropriate.

---

### Post by cong06 on 2010-04-16
> **drreed said:**
> Microsoft doesn't need to read browser caches. They have spyware in windows capable of reporting everything you do. It's called Genuine Advantage

It gives them a genuine advantage over other spies (like google) Google may be able to see a lot that you do online M$ can see everything you do on that computer, including what you do on Intranets.

This made me laugh

---

### Post by lovinglinux on 2010-04-16
> **drreed said:**
> Rather than post a flickr link that may well be gone tomorrow, do a search for images using the keywords "google 2084"

And by all means, use google to do it. It's funny and appropriate.

:lolflag:

Really funny. I'm still rofl...

---

### Post by keiichidono on 2010-04-16
The day Google uses the data they collect on/from me for purposes I am opposed to is the day I stop using their services. Until that day I will continue to use Google services and the tinfoil hat crowd aren't going to convince me otherwise. Form your own opinions OP.

---

### Post by qwertyjjj on 2011-07-16
> **keiichidono said:**
> The day Google uses the data they collect on/from me for purposes I am opposed to is the day I stop using their services. Until that day I will continue to use Google services and the tinfoil hat crowd aren't going to convince me otherwise. Form your own opinions OP.

Lol. Don't you think by that day it will already be too late?

---

### Post by Dangertux on 2011-07-16
Skynet err...Google has become self-aware, it's already too late. J/K :-P

On topic though -- I think both browsers have had their fair share of Security advisories over the past few months. Both seem to be reasonably secure (for now) , so long as Adobe can get and keep their act together (in regards to the numerous flash vulnerabilities) . Arguably it would be a matter of choice at this stage of the game.

---

### Post by wizard10000 on 2011-07-16
NIST's National Vulnerability Database says:

[http://web.nvd.nist.gov/view/vuln/search](http://web.nvd.nist.gov/view/vuln/search)

**Vulnerabilities in the last three months -**

Chrome:  70

Opera:  66

Chromium:  58

Firefox:  46

Internet Explorer:  23

Konqueror:  1

Safari:  0

Epiphany:  0

**Vulnerabilities in the last three years - **

Opera:  439

Chrome:  396

Firefox:  378

Chromium:  317

Internet Explorer:  267

Safari:  243

Konqueror:  7

Epiphany:  2

---

### Post by Dangertux on 2011-07-16
Good to know. 

Although severity and what platform would have been very useful as well. 

For instance not all firefox vulnerabilities effect all platforms etc... But judging from that data it appears to be close to a toss up. Granted these types of statistics only cover exploits that have been reported. Not necessarily something a researcher may be sitting on. 

Personally I use Firefox but that is my personal preference.

---

### Post by wizard10000 on 2011-07-16
> **Dangertux said:**
> Good to know. 

Although severity and what platform would have been very useful as well...

Agreed, but that would have been a fair bit of work  ;)

If anybody does want to pick things apart NVD's got a pretty good search engine.

---

### Post by smellyman on 2011-07-16
> **keiichidono said:**
> The day Google uses the data they collect on/from me for purposes I am opposed to is the day I stop using their services. Until that day I will continue to use Google services and the tinfoil hat crowd aren't going to convince me otherwise. Form your own opinions OP.

The day cigarettes do something bad to me is the day I quit.....

---

