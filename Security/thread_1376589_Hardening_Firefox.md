---
title: "Hardening Firefox"
date: 2010-01-09
forum: Security
---

### Post by ooVoh9em on 2010-01-09
[COLOR=DarkRed]**_Table of Contents:_**[/COLOR]

   [COLOR=Green]1. Cookie Filtering
[COLOR=RoyalBlue]        - Firefox Configuration 
    - Cookie Monster [/COLOR][/COLOR][COLOR=Green][COLOR=RoyalBlue]([https://addons.mozilla.org/en-US/firefox/addon/4703/](https://addons.mozilla.org/en-US/firefox/addon/4703/))[/COLOR][/COLOR]
[COLOR=Green][COLOR=RoyalBlue]     - Better Privacy ([https://addons.mozilla.org/en-US/firefox/addon/6623/](https://addons.mozilla.org/en-US/firefox/addon/6623/))[/COLOR]
   2. Active Content Filtering
[COLOR=RoyalBlue]    - NoScript ([https://addons.mozilla.org/en-US/firefox/addon/722/](https://addons.mozilla.org/en-US/firefox/addon/722/))
    - RequestPolicy ([https://addons.mozilla.org/en-US/firefox/addon/9727/](https://addons.mozilla.org/en-US/firefox/addon/9727/))
- Ghostery ([https://addons.mozilla.org/en-US/firefox/addon/9609/](https://addons.mozilla.org/en-US/firefox/addon/9609/))[/COLOR][/COLOR]
[COLOR=Green]    3. Privacy Enchanced Proxy
[COLOR=RoyalBlue]    - Privoxy ([http://www.privoxy.org/](http://www.privoxy.org/))
    - Basic Configuration[/COLOR]
    4. Ad Blocking
[COLOR=RoyalBlue]- AdBlock Plus ([https://addons.mozilla.org/en-US/firefox/addon/1865/](https://addons.mozilla.org/en-US/firefox/addon/1865/))
[/COLOR][/COLOR][COLOR=Green][COLOR=RoyalBlue]- Optimize Google ([/COLOR][/COLOR]https://addons.mozilla.org/en-US/firefox/addon/52498/)
[COLOR=Green][COLOR=RoyalBlue]- Hosts File ([http://www.mvps.org/winhelp2002/hosts.htm](http://www.mvps.org/winhelp2002/hosts.htm))[/COLOR][/COLOR]
[COLOR=Green]    5. Phising Protection
[COLOR=RoyalBlue]    - Web of Trust ([https://addons.mozilla.org/en-US/firefox/addon/3456/](https://addons.mozilla.org/en-US/firefox/addon/3456/))[/COLOR]
   6. App Armor[/COLOR][COLOR=RoyalBlue]
[/COLOR][COLOR=Green]7. Facebook Related[/COLOR]
 [COLOR=RoyalBlue]- Facebook Beacon Blocker ([https://addons.mozilla.org/en-US/firefox/addon/10497/](https://addons.mozilla.org/en-US/firefox/addon/10497/))[/COLOR]
 

[COLOR=DarkRed]**Cookie Filtering**[/COLOR]

A cookie is a small piece of text that is created on a user's computer by a web browser. A cookie consists of varying name-value pairs that contain information such as, but not limited to: User preferences, server-based sessions, and so on. Most cookies are harmless and are used to enrich the overall experience of your web surfing. However, some types of cookies can be a privacy risk since they can be used to track what web sites that you visit and allow for annoying targeted advertisements that are often intrusive. Regular cookies are harmless, but tracking cookies, third-party cookies, super cookies, and flash cookies all have the potential to leak information about your browsing habits that may not wish to share with just anyone. 
[B]
Configuring Firefox:[/B]

We will start by rejecting all cookies by default. This will allow you to decide which sites you trust enough to place cookies on your computer. These changes to Firefox will ensure that cookies from all web sites will be disallowed until you explicitly allow an individual site access to store cookies on your computer.

Load Firefox and navigate to *Edit* -> *Preferences* and click on the *Privacy* tab. Now uncheck the option "Accept cookies from sites". When you have finished your options should look like:

[IMG]http://i45.tinypic.com/307qfix.png[/IMG]

[COLOR=DimGray]*Tip: Please note that I have selected to automatically start Firefox in private browsing mode. You do not need to have this option selected. It is simply how my browser is configured.*
*Tip: If you do not see options to modify cookie settings as described above then use the drop-down menu and change the value from _Firefox will: Remember history_ to _Firefox will: Use custom settings for history_*[/COLOR] [COLOR=DimGray]
[/COLOR] 
You can now install an addon called [COLOR=Red]**Cookie Monster**[/COLOR] ([https://addons.mozilla.org/en-US/firefox/addon/4703](https://addons.mozilla.org/en-US/firefox/addon/4703)) which will let you allow cookies and session cookies for web sites that you trust and need them to function properly. Once installed it will add a small icon to the bottom right of the browser. Click on this icon to see a list of options. From here you may temporarily allow cookies form a site, always allow cookies from a specific site, etc. 

There is also the threat of flash cookies, click-pings, and third-parties using data located within the DOMStorage file (super cookies) to track you across the Internet. Disallowing cookies in the manner above will not prevent these types of cookies from being installed on your computer alone. An addon called [COLOR=Red]**Better Privacy**[/COLOR] ([https://addons.mozilla.org/en-US/firefox/addon/6623](https://addons.mozilla.org/en-US/firefox/addon/6623)) can defend against these techniques without you having to manually remove files from your computer. It allows you to remove flash cookies at specific intervals, whenever you close Firefox, and much more. You can configure this addon by going to *Tools* and then selecting *Better Privacy*.

Some sites may not function correctly until you allow cookies. This is completely up to the user of which sites he/she trusts enough to accept cookies from. 

[COLOR=DarkRed]**Active Content Filtering:**[/COLOR]

[COLOR=Red]**NoScript**[/COLOR] ([https://addons.mozilla.org/en-US/firefox/addon/722](https://addons.mozilla.org/en-US/firefox/addon/722)) plays an important role in hardening your browser. It will allow you to filter active content such as; Java, JavaScript, Flash, and defend you against XSS attacks without losing functionality thanks to the way they filter content based on a default deny policy with a small whitelist of trusted sites to allow execution of active content from.

NoScript will also defend against common web bugs, which are often embedded into a site or email to check if the user visited a specific page or viewed a particular electronic mail. This is possible due to the web bug being downloaded off a third-party server, thus notifying the server that you had to visit a page or open an email to initiate said download.

Once installed you will see a large new panel at the bottom of your browser when you navigate to a web site. You may also notice a lot of the functionality of the site is missing. To correct this you simply click on the *Options...* button and allow sites that you trust. Once added, the page will reload and the site will load normally from now on.

You may also choose allow one script on a specific page to load and nothing else, on a temporary basis. If you see a place on the site that is replaced by the NoScript icon, you may click on it to execute the content. This is great when you want to watch a video from a web site that might want you to also hear annoying flash-based ads while the video plays.

[COLOR=Red]**Request Policy**[/COLOR] ([https://addons.mozilla.org/en-US/firefox/addon/9727/](https://addons.mozilla.org/en-US/firefox/addon/9727/)) will enable you to control how cross-site requests are handled by websites. Cross-site requests are requests that your browser is told to make by a website you are visiting to a completely different website. It works by disallowing all cross-site requests by default. The user can then create a whitelist of trusted websites that may deploy cross-site requests for legitimate reasons. 

[COLOR=Red]**Ghostery**[/COLOR] ([https://addons.mozilla.org/en-US/firefox/addon/9609/](https://addons.mozilla.org/en-US/firefox/addon/9609/)) will block over 200 web bugs and tracking services. You can use Ghostery to see a list of known web bugs/tracking services, and choose which ones to block. 

[COLOR=DarkRed]**Privacy Enhanced Proxy:**[/COLOR]

[COLOR=Red]**Privoxy**[/COLOR] ([http://www.privoxy.org/](http://www.privoxy.org/)) is a privacy enchanced proxy that will transparently filter out junk while you surf the web. By default it will filter out advertisements, web bugs, script abuse, html tag abuse, and much more! It is a wonderful way to ensure anything missed by your other layers of security will filtered through this proxy. 

**Installing Privoxy**:

To install Privoxy simply issue this command inside of the terminal:
```
sudo apt-get install privoxy
```By default Privoxy is set to only listen on the localhost, so you do not have to worry about remote computers connecting to your proxy and using it to surf the web. It will only be available to your computer unless you configure it differently. You may verify the default functionality by checking the configuration  file and ensuring the *listen-address* variable is set to *localhost:8118*

Open the configuration file in GEdit:
```
sudo gedit /etc/privoxy/config
```Ensure the listen-address is set accordingly:
```
listen-address  localhost:8118
```[COLOR=DimGray]*Tip: listen-address  127.0.0.1:8118 is also acceptable*
[/COLOR] 
**Basic Configuration:**

Now direct all HTTP traffic through your local proxy by going to *Edit* -> *Preferences* -> *Advanced* and click on the *Settings* button. Now check the *Manual proxy configuration* option. Set the HTTP Proxy to 127.0.0.1 and Port to 8118. You may also do this for SSL traffic if you wish. Once finished, your configuration should look like:

[IMG]http://i47.tinypic.com/wu2ezl.jpg[/IMG]

If you would like to configure Privoxy and use many of its great features then I would suggest checking out the online manual ([http://www.privoxy.org/user-manual/index.html](http://www.privoxy.org/user-manual/index.html)).

[COLOR=DarkRed]**Ad Blocking**[/COLOR]

**[COLOR=Red]AdBlock Plus[/COLOR]** ([https://addons.mozilla.org/en-US/firefox/addon/1865](https://addons.mozilla.org/en-US/firefox/addon/1865)) uses an extentsive database of known advertisements and prevents them from loading. This will also help your favorite sites load faster, because you no longer have to wait on the ad servers before the page loads!

**[COLOR=Red]Optimize Google[/COLOR]**  ([https://addons.mozilla.org/en-US/firefox/addon/52498/](https://addons.mozilla.org/en-US/firefox/addon/52498/)) can be used to  enable or disable various site options for Google. This includes being  able to disable advertisements, prevent spam, and just allows for a more  complete Google experience in general.

Another method for blocking known malicious sites and annoying ads is by  using a hosts file ([http://www.mvps.org/winhelp2002/hosts.htm](http://www.mvps.org/winhelp2002/hosts.htm)). This  will redirect all known bad sites to localhost or 0.0.0.0 and prevent  them from loading. If you would like more information regarding the  installation of a hosts file then please review: [http://ubuntuforums.org/showthread.php?t=241460#2](http://ubuntuforums.org/showthread.php?t=241460#2)

[COLOR=DarkRed]**Phishing Protection**[/COLOR]

[COLOR=Red]**Web of Trust **[/COLOR]([https://addons.mozilla.org/en-US/firefox/addon/3456](https://addons.mozilla.org/en-US/firefox/addon/3456)) warns you about risky sites that cheat customers, deliver malware or send spam. Millions of members of the WOT community rate sites based on their experience, giving you an extra layer of protection when browsing or searching the Web.

WOT will go a long way to help you identify web sites that have been known to be malicious in one way or another. It will simply add an icon next to your address bar that will indicate the web sites integrity by chaning colors. Green means it is trusted, orange means it is questionable and red means it is dangerous. 

[COLOR=DarkRed]**App Armor**[/COLOR]

In Ubuntu 9.10 and above, you can utilize an App Armor profile for Firefox to increase your security. You may enable this feature by opening a terminal an executing the following command:

```
sudo aa-enforce /etc/apparmor.d/usr.bin.firefox-3.5 
```

[COLOR=DarkRed][B]Facebook Related
[/B][/COLOR] [B][COLOR=Red]
Facebook Beacon Blocker[/COLOR][/B] ([https://addons.mozilla.org/en-US/firefox/addon/10497](https://addons.mozilla.org/en-US/firefox/addon/10497)) will disable the infamous web bug that the company deploys to track user statistics and usage across the Internet. Many of us who value our privacy will find this addon very useful.

---

### Post by marco123 on 2010-01-09
Thank you very much for the tutorial.  It adds nicely to the one in my sig by bodhi.zazen

Do you mind if I add it to my sig also?

Marco.

---

### Post by ooVoh9em on 2010-01-09
Feel free to add it to your signature. I do not mind at all.

---

### Post by marco123 on 2010-01-09
Thank you.

---

### Post by Sir Jasper on 2010-01-09
Hi,

As regards Phishing I use WoT (Web of Trust) as recommended above. I also use OpenDNS. Additionally, my understanding is that IE8 and some versions of Firefox have settings to protect against Phishing. 

My regards

---

### Post by coldraven on 2010-01-10
What version of Firefox are you referring to? I just installed Ubuntu 9.10 and it has FireFox version 3.5.7 In the past I have disabled third party cookies but in this version it seems impossible. See the attached screenshot. Have I missed something?

---

### Post by ooVoh9em on 2010-01-10
> **coldraven said:**
> What version of Firefox are you referring to? I just installed Ubuntu 9.10 and it has FireFox version 3.5.7 In the past I have disabled third party cookies but in this version it seems impossible. See the attached screenshot. Have I missed something?

Where it says: *Firefox will: Remember history* you want to change that to *Firefox will: Use custom settings for history*. You will then be able to modify cookie settings.

> **Sir Jasper said:**
> Hi,

As regards Phishing I use WoT (Web of Trust) as recommended above. I also use OpenDNS. Additionally, my understanding is that IE8 and some versions of Firefox have settings to protect against Phishing. 

My regards

I forgot to mention OpenDNS. I will make sure to add it to the guide very soon. Thank you for reminding me.

---

### Post by Sir Jasper on 2010-01-10
Hi again,

After checking back on what I read some months ago: Firefox 3.5 (and above) > Tools > Options > Security > Block reported web forgeries; is (presumably) an anti-phishing option?

As regards OpenDNS I used browser level protection but there is an alternative option to set it at router level. Also, there are numerous protection options (some of which gave[me]strange results) so I only use the anti-phishing option (which, from memory, does not even need free registration).

My regards

---

### Post by rookcifer on 2010-01-10
You forgot AppArmor.  It's probably the best hardening tool of all for Firefox (and for any network facing app).

---

### Post by dogdo on 2010-01-10
> **rookcifer said:**
> You forgot AppArmor.  It's probably the best hardening tool of all for Firefox (and for any network facing app).

Not to detract from the momentum of this thread but how much protection does the default apparmor profile for firefox 3.5.5 provide?

---

### Post by running_rabbit07 on 2010-01-10
> **dogdo said:**
> Not to detract from the momentum of this thread but how much protection does the default apparmor profile for firefox 3.5.5 provide?

I can't answer for how well AppArmor works, but if you are interested, Bodhi has his profiles listed on [this link]("http://bodhizazen.net/aa-profiles/bodhizazen/") and his profile only has a few additions over the default AA profile. Of course I am speaking of Karmic's default. The above link has profiles for all four supported releases.

---

### Post by bodhi.zazen on 2010-01-11
Nice tutorial. 

I would add a few comments / suggestions :

1. I have been running Privoxy for several weeks now and, IMO, Adblock Plus does not add much, and removing adblock plus will make firefox a bit faster.

I advise one or the other.

IMHO, Adblock plus is best on a single user system or desktop.

IMHO, Privoxy is best on a multiuser system or on a LAN, where one can use privoxy as a single site to configure adblock.

Alternates to privoxy include squid.


2. Your tutorial is "incomplets" without mention of apparmor. As of Ubunt u9.10 there is a profile for apparmor and IMO it should be used.

I have posted my personal Firefox apparmor profiles here (organized by version of Ubuntu)

[http://bodhizazen.net/aa-profiles/bodhizazen/](http://bodhizazen.net/aa-profiles/bodhizazen/)

See the apparmor thread at the top of the Security section if you do not know how to enable apparmor.

[[all variants] Introduction to AppArmor - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1008906") 


3. Your comments on privacy are incomplete. In terms of privacy, make sure you disable cookies **and** history (under privacy).

In about:config turn your cache off

#Turn your cache off for off line use
browser.cache.offline.capacity  0
browser.cache.offline.enable  false

Last, you may wish to mount /tmp files in ram (this topic is typically covered in netbook discussions)

4. Last brief comment, you might want to look at the firefox add on "customize Google", lots of privacy issues with Google.

[http://www.customizegoogle.com/](http://www.customizegoogle.com/)

For more specific instructions see :

[http://blog.bodhizazen.net/linux/netbook-optimization/](http://blog.bodhizazen.net/linux/netbook-optimization/)

---

### Post by ooVoh9em on 2010-01-12
> **bodhi.zazen said:**
> Nice tutorial. 

I would add a few comments / suggestions :

1. I have been running Privoxy for several weeks now and, IMO, Adblock Plus does not add much, and removing adblock plus will make firefox a bit faster.

I advise one or the other.

IMHO, Adblock plus is best on a single user system or desktop.

IMHO, Privoxy is best on a multiuser system or on a LAN, where one can use privoxy as a single site to configure adblock.

Alternates to privoxy include squid.


2. Your tutorial is "incomplets" without mention of apparmor. As of Ubunt u9.10 there is a profile for apparmor and IMO it should be used.

I have posted my personal Firefox apparmor profiles here (organized by version of Ubuntu)

[http://bodhizazen.net/aa-profiles/bodhizazen/](http://bodhizazen.net/aa-profiles/bodhizazen/)

See the apparmor thread at the top of the Security section if you do not know how to enable apparmor.

[[all variants] Introduction to AppArmor - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1008906") 


3. Your comments on privacy are incomplete. In terms of privacy, make sure you disable cookies **and** history (under privacy).

In about:config turn your cache off

#Turn your cache off for off line use
browser.cache.offline.capacity  0
browser.cache.offline.enable  false

Last, you may wish to mount /tmp files in ram (this topic is typically covered in netbook discussions)

4. Last brief comment, you might want to look at the firefox add on "customize Google", lots of privacy issues with Google.

[http://www.customizegoogle.com/](http://www.customizegoogle.com/)

For more specific instructions see :

[http://blog.bodhizazen.net/linux/netbook-optimization/](http://blog.bodhizazen.net/linux/netbook-optimization/)

1.) I would generally agree with this statement. However, I do find Privoxy to be a superior solution to AdBlock, regardless of the setting. Privoxy defends against not only advertisements but also web bugs, script abuse, browser leakage, and a lot more. It also has fairly good options you may customize for filtering, etc.

2.) I agree. A lot of things did manage to slip my mind while making the tutorial. I will eventually add all suggestions people have given me when I do update it. AppArmor is a wonderful tool that should be utilized.

3) A big reason why I didn't include the suggestions you listed in the privacy/cookie section was because I didn't think most people would want to do it. The tutorial is aimed at the non technical crowd, just to help them quickly better secure their browser. I find that the target audience would probably find disabling their history and such to be bothersome. However, for completeness I will add your suggestions.

4.) Thanks for the information regarding CustomizeGoogle. I had never heard of that before. I will look into it.

Thanks to everyone for the feedback. Expect to see your suggestions added to the tutorial before too long. It will most likely happen this weekend, if not before.

---

### Post by bodhi.zazen on 2010-01-12
I understand, just take care when you talk about "privacy" because you will find privacy gets technical and is in general related to but separate from security.

---

### Post by Soul-Sing on 2010-01-12
relatively new is [COLOR="Magenta"]optimizegoogle[/COLOR] [https://addons.mozilla.org/en-US/firefox/addon/52498](https://addons.mozilla.org/en-US/firefox/addon/52498)
there are rumors that customizegoogle doesn't work that well anymore. (After the latest adjustments on their searchengine)

---

### Post by jbird80 on 2010-01-12
I personally like untangle to secure my network. its free contentment is more than enough to secure a home network. It might be a little advanced for beginners but it's secure.

---

### Post by bodhi.zazen on 2010-01-12
> **leoquant said:**
> relatively new is [COLOR=Magenta]optimizegoogle[/COLOR] [https://addons.mozilla.org/en-US/firefox/addon/52498](https://addons.mozilla.org/en-US/firefox/addon/52498)
there are rumors that customizegoogle doesn't work that well anymore. (After the latest adjustments on their searchengine)

/me enjoys a shiny new "optimize google"

---

### Post by jedispork on 2010-03-13
How important is it to use noscript? How is a regular guy suppose to know which scripts are ok to run? I may start using it myself but you would get nothing but complaints if you were trying to help a common pc user by installing it. 

I've been using adblock plus for a while and think its great. I'm also looking into using privoxy or a hosts file. I would like to know if there is a benefit to using a hosts file along with privoxy or adblock? I do enjoy learning about passive solutions because it keeps people from pestering me about their computer.

Thanks for the  Optimize Google suggestion.

---

### Post by bodhi.zazen on 2010-03-13
> **jedispork said:**
> How important is it to use noscript? How is a regular guy suppose to know which scripts are ok to run? I may start using it myself but you would get nothing but complaints if you were trying to help a common pc user by installing it.

Only you can answer that. How important is security to you ?

Security is a balance between ease of use and security. Many do not use NoScript, many would not browse without it.

Personally, I find it takes a few minutes to set up, and the vast majority of users concerned with security find it easy enough to learn.

> I've been using adblock plus for a while and think its great. I'm also looking into using privoxy or a hosts file. I would like to know if there is a benefit to using a hosts file along with privoxy or adblock? I do enjoy learning about passive solutions because it keeps people from pestering me about their computer.

If you are using only firefox, and only want ad blocking, adblock is all you need.

If you are using multiple browsers on a single computer, go for a hosts file. You do not need both.

If you want additional privacy features, have multiple users, or multiple systems, use privoxy and / or squid (in the case of multiple systems and multiple browsers it makes more sense IMO to use a single central proxy server).

> Thanks for the  Optimize Google suggestion.

You are most welcome.

---

### Post by jedispork on 2010-03-15
Is using the built in password storage for firefox  a bad idea? I've always relied on cookies to store my login info for forums and such.  

I also had another no script question. Wouldn't most of the attacks involving java script only execute on a windows machine? So what we would be trying to prevent is a 0 day hack? I came across some other info that said if you white list a site that is compromised a hacker can upload new code and bypass no script. 

I am enjoying no script and wot. I typed a wrong url that took me to a shady site and a warning from wot came up. Very cool. I would like to put this on friends and family's windows computers that they keep breaking. The non stop warnings from the anti-virus program doesn't seem to get the message across to them.

thanks again

---

### Post by Ijan on 2010-03-15
> **jedispork said:**
> Is using the built in password storage for firefox  a bad idea? I've always relied on cookies to store my login info for forums and such.

It's a trade-off between security and convenience. When you use the Firefoxes built in password manager the file name of the file your (encrypted) passwords are stored in and it's path are standard so malware authors probably know what to test their keylogged passwords against.

Cookies are prone to XSS-Attacks.

An external password manager with a non-standard filename, -extension and path is not as safe as not storing your password database on your computer at all and not having a master password but it's a little safer - simply because malware mostly targets the common.

---

### Post by jedispork on 2010-03-15
thanks again for the info. 

I wanted to mention that there is a sub for adblock plus called malware domains. Nice thing is that it auto updates unlike a hosts file. I stopped using it for a while as it slowed down the start of firefox. I'm not seeing the issue now maybe because I have a ssd.

---

### Post by ooVoh9em on 2010-06-21
I recently added more content and fixed the formatting to be more readable. I will eventually update this again with more information. Any suggestions?

---

