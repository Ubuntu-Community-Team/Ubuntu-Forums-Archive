---
title: "Security Help?"
date: 2011-01-13
forum: Security
---

### Post by harecanada on 2011-01-13
I have a problem but don't know where to go for help.
I do business on-line and work with a company that is based in Briton. I'm in Canada. Recently I have had a problem crop up that seems Spyware related. Whenever I click on this company's URL I'm redirected to a Russian site that is totally non-related. Even if the owner of that company sends me an e-mail with a link in it, it goes to that Russian URL. I asked the company if they were having any type of problem and they checked and said they were not and that I should check for spyware or malware. I use Firefox. I'm using Maverick. And I have a pretty good system. Can anyone give me a hand with this?

---

### Post by oldos2er on 2011-01-13
Post the URL.

---

### Post by harecanada on 2011-01-13
infoproductkiller.com

I tried it on my wife's Windows laptop and it worked fine.

---

### Post by sj1410 on 2011-01-14
check you DNS settings, and check if theres any proxy settings in your browser.

---

### Post by harecanada on 2011-01-14
sj1410  all it says is "Use system proxy settings" I don't know what this means and I don't know how to check DNS settings
Thanks for the response.
What is strange is it only happens with links from this company: infoproductkiller.com

---

### Post by ianblaire on 2011-01-14
You are not infected by spyware, yet. This site infoproductkiller.com redirects visitors based on browser settings, disabled javascript I suppose, didn't test it in detail. With default settings in Chromium I could get in no problem, custom Firefox installation was redirected several times (which looks a bit suspicious) over loads of mostly russian servers to juw.ru  However I do wonder what kind of company this is you are dealing with, that site looks a lot like scam.

---

### Post by Rubi1200 on 2011-01-14
I would clear the cache of all cookies, browser history etc. and then install NoScript:
[https://addons.mozilla.org/en-US/firefox/addon/noscript/](https://addons.mozilla.org/en-US/firefox/addon/noscript/)

---

### Post by harecanada on 2011-01-15
OK. I've tried all the suggestions here and still can't get to this site. I can get to it on my wife's windows laptop using Internet Explorer and Firefox. Not on Firefox on my machine. Has to be some sort of settings problem. Anyone else have any ideas?

---

### Post by nitrogensixteen on 2011-01-15
some ideas:
1) The site is a fraud
2) The site is a fraud and is unknowingly infected with malicious scripting
3) The site is a fraud and is complicit with cybercriminals in loading malicious scripting

---

### Post by harecanada on 2011-01-15
The site is not a fraud. I've been using it for 4 or 5 months. It works on other browsers. I just want to know why this redirect keeps happening. I've tried all the help I've been offered here and haven't solved it. I went on Firefox help and troubleshooting site and did a lot of the suggestions there to no avail. When I use Chromium web browser the redirect does not happen. I'm frustrated and want to get this fixed but I'm also curious as to how this can happen to a single site. I'm on the computer a lot and a lot of sites but this is the only one that gets a redirect.

---

### Post by ianblaire on 2011-01-15
The site redirects based on user agent.
Install something like this
[http://chrispederick.com/work/user-agent-switcher/](http://chrispederick.com/work/user-agent-switcher/)
and set it to IE for example.

WARNING This is suspicious behaviour, do not trust this site, use precautions, it could be serving exploits. This "company" is either malicious or incompetent.

---

### Post by harecanada on 2011-01-15
Well THANK YOU ianblaire!!! That worked! It's been driving me crazy. I still don't know why it happened but thanks. Now can you briefly explain why User Agent Switcher handles it? I'm curious and love to learn.
Thanks so much.
harecanada

---

### Post by CharlesA on 2011-01-15
I would suggest contacting the company who manages the site and let them know that their site is redirecting based on what browser the user is using.

---

### Post by CharlesA on 2011-01-15
I would suggest contacting the company who manages the site and let them know that their site is redirecting based on what browser the user is using.

---

### Post by ianblaire on 2011-01-15
> **harecanada said:**
> Well THANK YOU ianblaire!!! That worked! It's been driving me crazy. I still don't know why it happened but thanks. Now can you briefly explain why User Agent Switcher handles it? I'm curious and love to learn.
Thanks so much.
harecanada

I'm not a web dev so I might be wrong but according to Netcraft the site is running Apache. Maybe they are using mod_rewrite: [http://httpd.apache.org/docs/current/misc/rewriteguide.html](http://httpd.apache.org/docs/current/misc/rewriteguide.html) On this site you can see how that when you use Firefox and select "your user agent" you get a 302 redirect, with others you get the actual site:
[http://web-sniffer.net/](http://web-sniffer.net/)
Note how their Firefox 3 UA doesn't get redirected.  

User agent redirects are common on malware sites to obfuscate and stay under the radar from malware researchers. For example google bot gets a clean site, patched users too but those with a vulnerable browser/plugins get served the exploit.

---

### Post by OpSecShellshock on 2011-01-15
Everything about this situation seems as though what's happening is that there is a script that initiates the redirections only for vulnerable browsers. So it'll be checking the browser itself as well as which version is in use. Most likely it culminates in exploit code for that version of the browser. In those situations what usually happens next is that a successful browser exploit will cause it to crash and/or run a further piece of code. This will usually be some kind of Windows executable. The only way to know for sure would be to access the site via Firefox on Windows, but that would be a risky move to be made only if you are prepared to reinstall the OS afterwards.

---

### Post by harecanada on 2011-01-15
Most of this stuff is way over my head. One thing I would like to know though, if I reboot my system then I get the redirect again. Then I have to use the User Agent to get to the desired site. Is this something I have to do each time I reboot? I just tried it on my wifes Windows system using Vista and Firefox and all was fine. Now this is sounding like it is isolated to my system. Is that possible? Is there something in my settings out of wack? I can't believe I am going to have to live with this. There has to be a solution to getting rid of this crap. What do you think?

---

### Post by ryanfx on 2011-01-17
> **harecanada said:**
> Most of this stuff is way over my head. One thing I would like to know though, if I reboot my system then I get the redirect again. Then I have to use the User Agent to get to the desired site. Is this something I have to do each time I reboot? I just tried it on my wifes Windows system using Vista and Firefox and all was fine. Now this is sounding like it is isolated to my system. Is that possible? Is there something in my settings out of wack? I can't believe I am going to have to live with this. There has to be a solution to getting rid of this crap. What do you think?

You are ignoring everyone's legitimate and fully deserved suggestions.

The fact that it is redirecting based on your UA string is extremely suspicious behavior, especially given its destination.  I would personally refuse to use that site.

---

### Post by harecanada on 2011-01-18
No ryanfx, that is totally incorrect. I've been trying everything I've been told on here and appreciate all of it. The help here is simply awesome. If you don't have something to contribute, then please don't comment. The site doesn't matter. I want to figure out how any site can get this kind of unsolvable(as yet) redirect attached to it and not be able to be fixed. I've been looking into it for weeks. So don't come here tearing me down. I like to learn and that's why I'm here asking.

---

### Post by tgm4883 on 2011-01-19
> **harecanada said:**
> No ryanfx, that is totally incorrect. I've been trying everything I've been told on here and appreciate all of it. The help here is simply awesome. If you don't have something to contribute, then please don't comment. The site doesn't matter. I want to figure out how any site can get this kind of unsolvable(as yet) redirect attached to it and not be able to be fixed. I've been looking into it for weeks. So don't come here tearing me down. I like to learn and that's why I'm here asking.

Ok, the user agent thing. What is happening is you go to the site and the site knows what browser and version you are using, and based on that it either redirects you to another site or allows you into the site. What the user agent switches does, is when you visit the site, instead of the site thinking you are using Firefox 3 on Ubuntu, it thinks you are using IE 8 on Windows (or whatever you selected in the switcher). Sites might do this for legitimate reasons such as compatibility, but in this instance you are being redirected to a completely unrelated site. This is extremely suspicious. What could have happened here is that the site was hacked and malicious code introduced to do this. 

What you need to do is contact the site owner with this information. You need to realize that using the user agent switcher is a **_WORKAROUND NOT A FIX_**. The fix needs to be at the site level. 

As noted by previous posts, I would also recommend going to this website until the website has been fixed.

---

### Post by harecanada on 2011-01-21
Thanks tgm4883. This definitely shines some light on what's happening. It gets me closer to solving it. From what your saying, you feel that the problem is on their end with their site. My only problem with that is it seems to be only my computer and only Firefox. If it has something to do with the IP address then it wouldn't work on my wife's system as we have the same IP address. It works fine at my work place too. To me this means that it has something to do with my computer and Firefox. It really bugs me that I can't solve it. By the way there is no worries about me going back to Windows. I love Linux too much. Been using Linux for about 4 to 5 years. I will continue to figure this out.
Thanks again. If I get it solved I will post it here and mark it solved.

---

### Post by HermanAB on 2011-01-21
So set your Firefox User Agent String to be exactly the same as your Wife's and the problem will go away.

---

### Post by tgm4883 on 2011-01-21
> **harecanada said:**
> Thanks tgm4883. This definitely shines some light on what's happening. It gets me closer to solving it. From what your saying, you feel that the problem is on their end with their site.

Yes, it's an issue with their site.

> **harecanada said:**
> 
My only problem with that is it seems to be only my computer and only Firefox.

Incorrect. I am saying it happens on all linux machine using the same version of firefox as you have.

> **harecanada said:**
> 
If it has something to do with the IP address then it wouldn't work on my wife's system as we have the same IP address. 

No, it doesn't have anything to do with your IP address. Your IP Address is specific to your Internet connection. Your user agent string is specific to the OS+Browser you are using. If you fire up Chromium it's possible that the issue will not be reproducible.

> **harecanada said:**
> 
It works fine at my work place too. 

Do you use the same version of Ubuntu and Firefox at work? If not, I wouldn't expect the issue to happen for you at work.

> **harecanada said:**
> 
To me this means that it has something to do with my computer and Firefox. 

Yes, only because you have the version of Ubuntu+Firefox in question. I would expect it to be reproducible on other systems that have the same version of Ubuntu+Firefox.

> **harecanada said:**
> 
It really bugs me that I can't solve it. By the way there is no worries about me going back to Windows. I love Linux too much. Been using Linux for about 4 to 5 years. I will continue to figure this out.
Thanks again. If I get it solved I will post it here and mark it solved.

As said before, others have been able to reproduce this issue. That should be proof to you that it isn't something specific to your machine. The information I've given you proves the same, that it isn't specific to your machine. It's an issue with the site and someone needs to tell them about this issue.

---

