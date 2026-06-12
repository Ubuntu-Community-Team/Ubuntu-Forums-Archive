---
title: "How to decide if a particular script is safe or not?"
date: 2012-11-21
forum: Security
---

### Post by arroy_0209 on 2012-11-21
Default noscript configuration is somewhat restrictive as far as scripts are concerned and this causes loss of functionality of certain webpages. This is why very often we see noscript asking for permission to temporarily allow some scripts on some webpages. Now how do I decide which script is safe and which one is not? e.g., mathjax.org is necessary to view mathematical formula on some webpages and this sounds like safe but is there any objective criteria or way to test a script before allowing it even temporarily?

---

### Post by cwsnyder on 2012-11-21
You don't have to install NoScript.  You can browse unprotected by any security plug-ins.

The criteria I use, and I DO use NoScript on Firefox, is if it is just casual browsing, I don't allow scripts.  If I think I need to see something on a particular site, I enable javacript for those elements temporarily.  If it is a site which I trust, I will enable that javascript required to navigate the site and see elements which I want, while still blocking advertising javascript.  I also use BetterPrivacy to clean up after Flash Cookies.

I am more likely to use Chromium or Chrome with their sandboxing if I am casually browsing, don't care about advertising, and want to see what the full site looks like.

---

### Post by Hungry Man on 2012-11-21
Unfortunately, no, there really isn't. NoScript provides no detection, and there's really no way for a human user to decide whether a script is safe based purely on the URL of origin.

---

### Post by CharlesA on 2012-11-21
> **Hungry Man said:**
> Unfortunately, no, there really isn't. NoScript provides no detection, and there's really no way for a human user to decide whether a script is safe based purely on the URL of origin.
Indeed. You would have to look at the source to tell what said script does.

---

### Post by Hungry Man on 2012-11-21
I meant it doesn't provide **detection** not **protection**, sorry, edited my post.

As CharlesA says you either need to look at the source or have some AV do it for you.

---

### Post by gnusci on 2012-11-21
I use NoScript, and I give only access to the website I trust. You can use Google-fu to do your research about a website reputation!

---

### Post by Ms. Daisy on 2012-11-21
> **CharlesA said:**
> Indeed. You would have to look at the source to tell what said script does.
And there's no guarantee that a given script would be the same forever.

---

### Post by CharlesA on 2012-11-22
> **Ms. Daisy said:**
> And there's no guarantee that a given script would be the same forever.

Pretty much. I've seen some fishy scripts before - ads hidden via javascript and other such junk, but you can only trust a script as much as you trust the web site it is on.

---

### Post by arroy_0209 on 2012-11-22
Thanks for all the inputs.
Since uncertainty about scripts will probably continue, will it be safer, as indicated, to use chrome/chromium with sandboxing rather than firefox with noscript?

---

### Post by OpSecShellshock on 2012-11-22
There's really no one thing that will always work. Opening a site in Firefox with NoScript first is a good place to start. See if it gets you what you're after. If it looks like you're going to have to allow scripts in order for the site to function properly, then maybe switch to Chromium and just copy the URL.

It gets a bit more complicated considering how a lot of sites have code from several third-party domains on their pages, though. In Firefox with NoScript you have more control over that, because you can allow scripts on the main site but continue blocking them on all the other domains with code being used on the page. Then you can rescind the temporary permissions as soon as you're done with the site. Actually, if you go in the menu under View-->Toolbars-->Customize and you already have NoScript as an extension in Firefox, you can add a "Revoke Temporary Permissions" button to the toolbar.

---

### Post by tubbygweilo on 2012-11-22
arroy_0209, why not browse using both firefox & chromium loaded with extensions that work best with you and the browser? May be a bit slower switching between browsers but then each has strengths that may well meet your needs on different sites. Only you can tell which tools feel best in your hands.

---

### Post by Hungry Man on 2012-11-22
NoScript isn't a sandbox, and works in a way that's entirely different from a sandbox - therefor switching from one method of protection to another isn't the best way to handle things without first knowing the threat you need to protect against.

Whereas a sandbox reduces system attack surface and limits an attackers ability to interact with the running system, NoScript is targeted at preventing web-based attacks, such as XSS, CSRF, ClickJacking, and SVG Keylogging.

So if your goal is to access a website securely, in such a way that an attacker will not be able to compromise that particular website in your specific web session (ie: XSS/CSRF/SCG Keylogging) than NoScript is what you'll want to use (with careful whitelisting).

If your goal is to access a website that you don't trust, or that is potentially malicious, a sandbox is your best bet as it'll do the most to prevent the exploit from working properly despite the website specific rights.

---

### Post by CharlesA on 2012-11-22
> **Hungry Man said:**
> 
If your goal is to access a website that you don't trust, or that is potentially malicious, a sandbox is your best bet as it'll do the most to prevent the exploit from working properly despite the website specific rights.

I would rather visit a site like that from a locked down VM, then restore the snapshot after done. But then you need to ask yourself why you'd want to visit such a site in the first place.

---

### Post by Hungry Man on 2012-11-22
Well, the way I would say it is this:

For banking or dealing with "sensitive" websites, use NoScript.

For every day browsing, where you may run into an exploit page, use Chrome.

Few people intentionally look at exploit pages, but millions do it accidentally while simply browsing the web. 2011 Sophos Report stated that 90% of websites spreading malware were at one point legitimate pages that had just been hacked.

---

### Post by CharlesA on 2012-11-22
> **Hungry Man said:**
> 
Few people intentionally look at exploit pages, but millions do it accidentally while simply browsing the web. 2011 Sophos Report stated that 90% of websites spreading malware were at one point legitimate pages that had just been hacked.

Good point.

I've been sticking with just NoScript, and I've been ok so far.. but then I don't really "surf" the interwebz much any more.

---

### Post by OpSecShellshock on 2012-11-22
When a legitimate site has been compromised, the exploits/malware are still hosted on another site (from what I've seen, actually several others. It's annoying). The compromised site usually just has scripts or iframes added to it that load the objects from the sites that actually host the malware. In that situation, even if the script on the compromised site is allowed, NoScript can still prevent the objects on the third-party sites from loading. The sticky post on NoScript at the top of the Security Discussions section of this forum has a good guide for setting it up. Then it's just a matter of never, ever selecting "temporarily allow all" when using a site.

It's still not possible to fully predict, of course. A malicious payload itself certainly could be directly hosted at the domain (or a subdomain) of a compromised site. The Chromium sandbox would help more in that situation, if it were necessary to allow scripts and ads.

---

### Post by Hungry Man on 2012-11-22
That's true. Most of what I've seen is an iframe directing to another site.

The thing I have issue with is what this topic is about. There's no way for the user to know, off the bat, which scripts to allow. And once they allow that iFrame they lose significant protection. That's where a sandbox protects you.

---

### Post by OpSecShellshock on 2012-11-23
Right, it tends to drop off precipitously as the first couple domains get allowed. It's interesting that Mozilla is now saying that Firefox 17 has iframe sandboxing. Can't wait to see how real-world injection scenarios play out against that.

---

### Post by CharlesA on 2012-11-23
> **OpSecShellshock said:**
> Right, it tends to drop off precipitously as the first couple domains get allowed. It's interesting that Mozilla is now saying that Firefox 17 has iframe sandboxing. Can't wait to see how real-world injection scenarios play out against that.
I'm just waiting to see how fast that "sandbox" is broken.

---

