---
title: "Chrome vs. Firefox question"
date: 2016-02-09
forum: Ubuntu, Linux and OS Chat
---

### Post by ra7411 on 2016-02-09
I've been using only Chrome in recent years. 
Does Firefox have any advantages over Chrome that I might not be aware of?

Thanks

---

### Post by howefield on 2016-02-09
Not really a support thread, moved to the "*Ubuntu, Linux and OS Chat*" forum.

---

### Post by pfeiffep on 2016-02-09
> **ra7411 said:**
> I've been using only Chrome in recent years. 
Does Firefox have any advantages over Chrome that I might not be aware of?

ThanksThere is a difference in the method used to check for invalid certificates. I switched a year ago from Chrome to FiireFox ... [my previous post]("http://ubuntuforums.org/showthread.php?t=2267329").

> Google has shunned the traditional methods of revocation: whilst Chrome  does check the status of EV certificates, revocation checking is not  enabled by  default for any other type of certificate. Instead, Chrome uses its  [own updating mechanism]("https://www.imperialviolet.org/2012/02/05/crlsets.html") to maintain an aggregated list of revoked certificates gathered by crawling CRLs. This is a [subset of all revocations]("http://news.netcraft.com/archives/2014/04/18/chrome-users-oblivious-to-heartbleed-revocation-tsunami.html") and is intended to cover only the most important. 
[Full text from quote]("http://news.netcraft.com/archives/2014/04/24/certificate-revocation-why-browsers-remain-affected-by-heartbleed.html")

---

### Post by coldraven on 2016-02-09
I use Firefox for most of my browsing, I like to use several add-ons for my privacy and security. I can set FF to delete all cookies etc. on exit. I only use Chrome for the occasional site that wants a more recent version of Flash. AFAIK in Chrome I have to manually delete cookies and history which means that Google is tracking me more often.

---

### Post by vasa1 on 2016-02-09
> **howefield said:**
> Not really a support thread, moved to the "*Ubuntu, Linux and OS Chat*" forum.And it's quite "Recurring" as well.

---

### Post by maglin2 on 2016-02-09
> **ra7411 said:**
> I've been using only Chrome in recent years. 
Does Firefox have any advantages over Chrome that I might not be aware of?

Thanks
They recommend here that you use both, but for different purposes:
[https://github.com/lfit/itpol/blob/master/linux-workstation-security.md](https://github.com/lfit/itpol/blob/master/linux-workstation-security.md)

---

### Post by QDR06VV9 on 2016-02-09
Well I still use chromium with [COLOR=#303942][FONT=DejaVu Sans][KB SSL Enforcer]("https://chrome.google.com/webstore/detail/kb-ssl-enforcer/flcpelgcagfhfoegekianiofphddckof?hl=en-US") [SIZE=2]not a complete solution..but is there really one solution?
[/SIZE][/FONT][/COLOR]> Automatic security, browse encrypted.This extension enforces encryption for websites that support it as much as currently possible in Chrome. This gives you added security and privacy for your browsing automatically and transparently. This is particularly important on insecure networks, such as public wifi in e.g. coffee shops and hotels.


It is not completely secure against the infamous Firesheep, but it does minimize the risk greatly. See the section on complete enforcement for technical details and more on when this will be possible.


Features:
- Automatically detects if a site supports SSL (TLS) and enforces all subsequent requests to be over SSL
- As soon as a domain is set to be enforce, the browser will not send any unencrypted requests for that domain (unless the site deliberately enforces not using encryption, see the section on complete enforcement)
- Flexible options for overriding the auto-detection
- Caches which sites support SSL (respects incognito mode)
- Open source (GPLv2 or later)


Changelog:
[https://github.com/kbitdk/kbsslenforcer/blob/master/Changelog.md](https://github.com/kbitdk/kbsslenforcer/blob/master/Changelog.md)


Issue tracker:
[https://github.com/kbitdk/kbsslenforcer/issues](https://github.com/kbitdk/kbsslenforcer/issues)


Complete enforcement:
Due to Chrome limitations KB SSL Enforcer detects SSL on the very first visit to a page and is unable to block the unencrypted request from going through while this is happening. It will let that page load and if it is detected to support SSL, all subsequent requests to that domain will be enforced automatically to use SSL before the unencrypted request is sent from the browser.


The unencrypted request only goes through on the very first page visit where it's detecting SSL support. The setting will be saved and survives reboots and all. The only way to stop enforcing SSL is to manually set it to ignore SSL on that domain or if the extension detects that the site is trying to enforce an unencrypted connection and therefore backs off by not enforcing it from then on.


This first insecure request could send a cookie in the clear, which would give anyone with tools like Firesheep an opportunity to use your account on that site. But this only happens if they catch it during that first request and if it includes sensitive information, such as your logged in session. All subsequent requests, even after restarting the browser and rebooting the computer, will enforce encryption.


Permissions:
The manifest file states the permissions requested:
[https://github.com/kbitdk/kbsslenforcer/blob/master/chrome%20extension/manifest.json](https://github.com/kbitdk/kbsslenforcer/blob/master/chrome%20extension/manifest.json)
 * *://*/
  * This is for accessing pages on all domains and both with and without SSL
 * tabs
  * This is for accessing information on whether a tab is in incognito, so it can be respected
 * webRequest
  * This is for intercepting the unencrypted requests and detecting whether the site doesn't support encryption by redirecting encrypted requests to the unencrypted site
 * webRequestBlocking
  * This is for blocking the unencrypted requests while determining whether it needs to be redirected


The project is open source and any scrutiny of the code or the extension's behavior is encouraged. If you have any comments, please open an issue on the issue tracker:
[https://github.com/kbitdk/kbsslenforcer/issues](https://github.com/kbitdk/kbsslenforcer/issues)


Feedback:
Any questions or feedback are welcome in the issue tracker linked above, which has features to manage and notify people of any issues, so they can be fixed and we can all have a better extension. Please keep the user reviews section of this page to just reviews. Thanks.


Developed by KB IT:

[https://kbit.dk](https://kbit.dk)[COLOR=#303942][FONT=DejaVu Sans][SIZE=2]
Firefox lost me when they started including things like Hello World and Pocketreader.
I am not saying they are not useful but should be left to the user to decide..
Just my humble 2 cents worth.
Kind Regards [/SIZE][/FONT][/COLOR]

---

### Post by monkeybrain20122 on 2016-02-09
Well depending on what you mean by "advantage". I use a few addons for Firefox which are not possible in Chrome, I can also keep about 300 tabs open in FF and still brazing fast, Chrome would have choked with < 30. But that may not be your use case. 

I also don't log into google services from Chrome.

---

### Post by kurt18947 on 2016-02-09
I find Firefox's add-on ecosystem far more useful than Chromium. I don't notice a significant difference in page rendering speed and find that freshplayer works pretty reliably if I want the latest flash. Web sites like ESPN & NFL.com are **annoying** without noscript & bluhell firewall. I also use imagezoom and page zoom button frequently.

---

### Post by corbin.loftis on 2016-02-12
I have extensions that I use regularly on Firefox which are unavailable on Chrome, but I will pull up Chrome to watch the occasional video if Firefox is maxed out.

---

### Post by gordintoronto on 2016-02-12
I live in Chrome, but if I want to download a youtube video, I use Firefox along with Download Helper.

---

### Post by sabina2 on 2016-02-15
Beyond NoScript that provides unique security improvements, I also found interesting to hide my OS datas when I surf the Internet. When Javascript is on, you can not totally spoof your user-agent datas with Chrome or Chromium. You can only change the strict user-agent string but a website is still able to know what is your real browser and OS through Javascript. With Firefox, you are able to make your Ubuntu totally looks like a Windows, when javascript on, which can avoid a few more security issues related to Linux or Ubuntu targeted exploits. Moreover, you can add canvasblocker to Firefox, which forbids canvas fingerprint, the latter being particularly efficient to uncover your real browser and OS, even with full user-agent spoofing.

---

### Post by yoshii on 2016-02-15
I read an article on an internet security website that described the differences between Firefoxes blacklisting of attack sites vs other browsers and apparently Chrome implements it in a way which is incomplete and therefore more dangerous.  Also I like using several privacy and security addons so Firefox is for me.  I like the control that it allows for customization.  I also like being able to install addons for downloading videos and stuff like that.

---

### Post by mikodo on 2016-02-15
> **sabina2 said:**
>  - Snippet -  Moreover, you can add canvasblocker to Firefox, which forbids canvas fingerprint, the latter being particularly efficient to uncover your real browser and OS, even with full user-agent spoofing.
Real Nice.

---

### Post by monkeybrain20122 on 2016-02-16
> **sabina2 said:**
> Beyond NoScript that provides unique security improvements...

Noscript is overkill IMO, most sites won't work properly with NoScript so you have to click allow anyway. Also it messes up your profile even if removed. If I am that paranoid I will simply avoid certain sites or not going online. :) A better solution is [YesScript ]("https://addons.mozilla.org/en-US/firefox/addon/yesscript/")which allows you to disable scripts on demand rather than blocking all by default.

---

### Post by sabina2 on 2016-02-16
Yes, I also think that NoScript is overkill. It's a pain to find a good set up for oneself.

---

### Post by vasa1 on 2016-02-16
Some people claim that NoScript is the main reason they use Firefox. I use Firefox with *[uBlock origin]("https://github.com/gorhill/uBlock/wiki")*. It meets my modest needs.

---

### Post by help_me2 on 2016-02-16
> **gordintoronto said:**
> I live in Chrome, but if I want to download a youtube video, I use Firefox along with Download Helper.
I'm the same way. I also like how chrome syncs with the chrome browser on my phone.

---

### Post by sabina2 on 2016-02-16
> **vasa1 said:**
> Some people claim that NoScript is the main reason they use Firefox. I use Firefox with *[uBlock origin]("https://github.com/gorhill/uBlock/wiki")*. It meets my modest needs.

I would personnally say NoScript + full user-agent spoofing ability + private session. Otherwise, I would use Chromium with pepper flash.

---

### Post by mikodo on 2016-02-16
I don't use Chrome. So, I can't comment on what it has and doesn't have for features, privacy settings and security.

I have been using Firefox for seven years now. I liked it initially because it was open source. 

I lean towards security and privacy. As I said above, I find things in FF that I hear is not in other browsers. In FF, I go to the Privacy & Security & Advanced sections and set my own preferences which, are pretty much like what Private Viewing is set at only, with a few tweaks that I prefer. I maintain 5 different FF profiles, each for its' own use. Besides the default one, I have ones like for Banking, Professional Associations and others, that only have the encrypted HTTPS links booked-marked and, I only go to each respective website per profile and only that website to keep things separate.  I do not have flash installed.

Then, I use these extensions, (add-ons). NoScript took a little getting used to. I have been using it for 7 years, and no longer see its' use a hindrance to me. Two add-ons I just added yesterday.  So here they are, as listed in FF. It would take too long to explain why I use each. 

[BetterPrivacy]("https://addons.mozilla.org/en-US/firefox/addon/betterprivacy/"), [CanvasBlocker]("https://github.com/kkapsner/CanvasBlocker"), [Classic Theme Restorer]("https://addons.mozilla.org/en-US/firefox/addon/classicthemerestorer/"), [HTML5 Everywhere!]("https://github.com/lejenome/html5-video-everywhere"),[ [s]HTTPS by default[/s]]("https://github.com/Rob--W/https-by-default"), [HTTPS-Everywhere]("https://www.eff.org/https-everywhere"),[ NoFlash]("https://github.com/hfiguiere/no-flash"), [NoScript]("https://noscript.net/"), [Privacy Badger]("https://www.eff.org/privacybadger"), [s][Random Agent Spoofer]("https://github.com/dillbyrne/random-agent-spoofer")[/s], [uBlock Origin]("https://github.com/gorhill/uBlock"), [WOT]("https://www.mywot.com/"). All the add-ons installed are from Firefox's add-on page. Possibly, there is some redundancy here. In uBlock Origin, I make sure to include the 4 sites that include Host File Lists also. See Post #26 why I deleted Random Agent Spoofer from my list of FF Add-ons.

Addendum: I just read through the explanations for HTTPS-Everywhere and HTTPS by default again. I like HTTPS-Everywhere better (by the [Electronic Frontier Foundation)]("https://www.eff.org/") as, it automajically requests the HTTPS connection to the sites that offer it, where HTTPS by default, seems to need user intervention still. I have deleted the latter from my FF Browser.

I also like FF for being able to shut off many of the usually newer features I don't use that, often eat up resources. My FF remains responsive and quick on this old computer. Last night though, I added CanvasBlocker, and Random Agent Spoofer. Now while browsing with my VPN ([PIA]("https://www.privateinternetaccess.com/")) on, and have been into my encrypted Email site, [Protonmail]("https://protonmail.com/"), and leave the site, and immediately open another FF browsing instance, I get a message the last page has not been closed yet and would I like to close it. Click close and I am good. Now, if I have a Web-page open such as Ubuntu Forums already, which I usually do when I am on the computer this doesn't happen. I am not sure yet what is happening since last night. This behaviour only seems to be with my Email Provider. Possibly it has to do with the Encryption of the Web-site. I'll have to try a few things to see what might be causing it. But, it is not a deal breaker for me as, I love the privacy and security aspects of those two new add-ons.

I am sure people are going to scoff at my long list of add-ons and some of the ways I connect to the internet with FF. I am only listing all this information, to illustrate why I like Firefox. To show what I know it is capable of.

---

### Post by vasa1 on 2016-02-16
> **mikodo said:**
> ...

I am sure people are going to scoff at my long list of add-ons and some of the ways I connect to the internet with FF but, I am only listing all this information, to illustrate why I like Firefox. To show what I know it is capable of.

BTW, just in case you don't know, there's a forum dedicated to security here:  [http://www.wilderssecurity.com/forums/all-things-unix.99/](http://www.wilderssecurity.com/forums/all-things-unix.99/). My signature there, at least at one time, was the possibly politically incorrect "One can never be too thin or too secure", IIRC.

Edited link to point to Linux/UNIX subforum

---

### Post by mikodo on 2016-02-16
> **vasa1 said:**
> BTW, just in case you don't know, there's a forum dedicated to security here:  [http://www.wilderssecurity.com](http://www.wilderssecurity.com). My signature there, at least at one time, was the possibly politically incorrect "One can never be too thin or too secure", IIRC.
@vasa1 Thank you. [s]I have seen the forum before but, had forgotten about it.[/s]

No actually, I think I must have only read someone talking about it. I just spent 10 minutes looking in it and it looks* very* interesting and informative. I would have returned to it, had I actually looked into it before.

---

### Post by night_sky2 on 2016-02-17
I use Firefox as my default browser for two reasons primarily: Customization and it's wonderful addons.

I like the fact that I can really trim down the browser and remove all the features that I don't like. Chromium doesn't give you access under-the-hood.

[B]BluHell Firewall:

[/B]Extremely lightweight adblocker/anti-tracker that has virtually no impact on system ressources (the addon weight a tiny 56.1 Kb)

[https://addons.mozilla.org/en-us/firefox/addon/bluhell-firewall/](https://addons.mozilla.org/en-us/firefox/addon/bluhell-firewall/)

**FlashDisable**:

Toolbar button that lets you disable and re-enable Flash with just one click. Very convenient if you don't like Flash but still need it or don't trust Adobe.

[https://addons.mozilla.org/en-us/firefox/addon/flashdisable/?src=search](https://addons.mozilla.org/en-us/firefox/addon/flashdisable/?src=search)

---

### Post by monkeybrain20122 on 2016-02-17
> **night_sky2 said:**
> 

**FlashDisable**:

Toolbar button that lets you disable and re-enable Flash with just one click. Very convenient if you don't like Flash but still need it or don't trust Adobe.

[https://addons.mozilla.org/en-us/firefox/addon/flashdisable/?src=search](https://addons.mozilla.org/en-us/firefox/addon/flashdisable/?src=search)

What is the difference if you just set flash to "ask to enable" in tools > addons > plugins?

---

### Post by monkeybrain20122 on 2016-02-17
Here is my list of FF addons: Adblock Plus, Adblock Plus Pop-up Addon, DownThemAll! DownThemAll! AntiContainer, Google Translator For Firefox, Google Image Search, [mpv-youtube-dl-binding]("https://addons.mozilla.org/de/firefox/addon/watch-with-mpv/"), [Open Tabs Next to Current]("https://addons.mozilla.org/en-US/firefox/addon/open-tabs-next-to-current/"), user agent overrider, [yesScript]("https://addons.mozilla.org/en-US/firefox/addon/yesscript/")

I disable flash by default. Between mpv-youtube-dl-binding and html5 I rarely need flash.

---

### Post by sabina2 on 2016-02-17
I tried random agent spoofer but I decided to uninstall it. Even if it allows to increase anonymity against commercial trackers, it can not protect against the theorical global attacker and, more important for me, it can not hide, unless we are not talking about the same add-on and at least, for Firefox user-agents, that an user-agent spoofer is running. Actually, it does not provide the firefox BuildID corresponding to the user-agent it is supposed to spoof. It provides the same BuildID as the Tor Bundle Browser Firefox : 0. It means that an attack targeting the Tor Firefox BuildID could target an usual Firefox browser using this add-on. 

I thought to try tweaking this add-on on this point, but it appears to be too much work, when manual spoofing already meets my needs. 

I also tried to use as less add-on as possible to reduce the attack surface and to do not slow too much my browser. However, I am not sure what are the real benefits of Ghostery when we are already using NoScript and an AD blocker ?

---

### Post by night_sky2 on 2016-02-17
> **monkeybrain20122 said:**
> What is the difference if you just set flash to "ask to enable" in tools > addons > plugins?

The difference is that the plugin is _completely_ disabled. It's pretty much like not having it installed on your system. **FlashDisable** adds a toolbar button that acts like a 'on/off switch' when you need or don't need to enable flash on a particular website. The addon even let's you set a page to refresh when enabling flash or to disable the plugin upon exiting the browser. It's very convenient.

---

### Post by mikodo on 2016-02-17
> **sabina2 said:**
>  - Snippet - I tried random agent spoofer but I decided to uninstall it. Even if it allows to increase anonymity against commercial trackers, it can not protect against the theorical global attacker and, more important for me, it can not hide, unless we are not talking about the same add-on and at least, for Firefox user-agents, that an user-agent spoofer is running. Actually, it does not provide the firefox BuildID corresponding to the user-agent it is supposed to spoof. It provides the same BuildID as the Tor Bundle Browser Firefox : 0. It means that an attack targeting the Tor Firefox BuildID could target an usual Firefox browser using this add-on.   **I thought to try tweaking this add-on on this point, but it appears to be too much work, when manual spoofing already meets my needs**.    Thank you, for posting. 
 
Is this how I might manually spoof the user-agent string?  

See this for explanation about MS Internet Explorer user-agent strings: [https://msdn.microsoft.com/en-us/library/ms537503%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/ms537503%28v=vs.85%29.aspx)  

Change to Internet Explorer 11: Mozilla/5.0 (Windows NT 6.3; Trident/7.0; ry:11:0)  like Gecko  

Change FF user-agent strings:  [http://www.howtogeek.com/113439/how-to-change-your-browsers-user-agent-without-installing-any-extensions/](http://www.howtogeek.com/113439/how-to-change-your-browsers-user-agent-without-installing-any-extensions/)


Thanks.

---

### Post by sabina2 on 2016-02-18
> **mikodo said:**
> Is this how I might manually spoof the user-agent string?


Not really. You can check all leaked data here :

[https://www.browserleaks.com/](https://www.browserleaks.com/)

[http://ip-check.info/?lang=en](http://ip-check.info/?lang=en)

You will see that changing only the user-agent string can not hide your real OS and browser when javascript is enable. For Firefox, you have to over-ride the following strings : useragent, oscpu, platform, appname, appversion and BuildID. Otherwise, a website can determine 1- what is your real OS and browser, 2- that you are trying to hide these info. You also have to disable all plugins. Flash can leak your OS data and even your kernel version. If you only select "ask to activate" plugins or if you are using NoScript to disable it, one can still know what is your flash version (11.2, on Linux). On browserleaks.com, you can check that even with this, canvas fingerprinting is still able to recognize your OS (Linux, Ubuntu).

---

### Post by mikodo on 2016-02-18
@ Sabina2. Thanks, for that.

---

### Post by SagaciousKJB on 2016-02-18
Personally I prefer Chrome but only because FireFox has become extremely unstable in every incarnation I've used it in for the last three years. It has better support for extensions though, and plus if you're concerned about privacy the things like the Tor browser are based off FF.

Chrome, I would say a distinct advantage it has, is it will play Netflix and Amazon video by default whereas you need to do something special to get it to work in FireFox.

---

