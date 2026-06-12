---
title: "privacy/cookie issues in firefox, ok to chat in this forum?"
date: 2012-02-11
forum: Security
---

### Post by goodbye-windows(tm) on 2012-02-11
Hi all,

I've been looking at user privacy with regard to browsers. It seems cookies are now un-deletable and ad agencies can now track anyone across the web and even write javascript to extract data from the hard drive (not just in the browser folder). The more stealth cookies are not written in plain text, so the user has no way to know their contents. Deleting cookies from the cookie folder is useless these days.

Linux provides no defense against privacy abuses related to the browser use.

Is it acceptable to discuss privacy issues due to the browser in this forum? If not, is there another ubuntu forum that is more appropriate for this type of discussions?

TY.

Art

---

### Post by winh8r on 2012-02-11
try installing the following firefox add-ons:

Ghostery
Adblock plus
 and if it really concerns you

no-script


they do a pretty good job.


 You can also go here [http://ip-check.info/?lang=en]("http://ip-check.info/?lang=en")

and see what info your browser is releasing and how to stop it.



Also avoid using google directly, use IXquick, startpage, or scroogle instead

---

### Post by tr333 on 2012-02-12
Also check out the BetterPrivacy addon at [https://addons.mozilla.org/en-US/firefox/addon/betterprivacy/](https://addons.mozilla.org/en-US/firefox/addon/betterprivacy/) and Https Everywhere at [https://www.eff.org/https-everywhere](https://www.eff.org/https-everywhere).

Another interesting site on browser privacy is [http://panopticlick.eff.org/](http://panopticlick.eff.org/).


As for search engines, I've heard good reports on [DuckDuckGo](http://en.wikipedia.org/wiki/DuckDuckGo) for privacy.

---

### Post by Ms. Daisy on 2012-02-12
[QUOTE=goodbye-windows(tm)]Linux provides no defense against privacy abuses related to the browser use.[/QUOTE] Hmm, maybe out-of-the-box that's kind of true, but you can certainly configure it to be more private.  

Check out [Better Privacy]("https://addons.mozilla.org/en-US/firefox/addon/betterprivacy/") (FF add-on). It claims to delete all super-cookies.  Have you followed the [NoScript configuration guide]("http://ubuntuforums.org/showthread.php?t=1912426")? If you're blocking scripts then you are automatically disabling the JavaScript-based cookies.

What about [Click Clean]("https://addons.mozilla.org/en-US/firefox/addon/clickclean/")? That wipes everything out after each session.  If you start a new browser session for every site you visit, there can't be anything left for anyone to track aside from what you're actively doing on that one website (and you can control that a bit by blocking unnecessary scripts).

---

### Post by Dangertux on 2012-02-12
> **goodbye-windows(tm) said:**
> Hi all,

I've been looking at user privacy with regard to browsers. It seems cookies are now un-deletable and ad agencies can now track anyone across the web and even write javascript to extract data from the hard drive (not just in the browser folder). The more stealth cookies are not written in plain text, so the user has no way to know their contents. Deleting cookies from the cookie folder is useless these days.

Linux provides no defense against privacy abuses related to the browser use.

Is it acceptable to discuss privacy issues due to the browser in this forum? If not, is there another ubuntu forum that is more appropriate for this type of discussions?

TY.

Art

I'm not sure I agree with the statement that linux provides no defense against these types of things, nor am I really sure that there is such a thing as an undetectable cookie.

There are methods for obfuscation of a cookie's content, however none are particularly hard to analyze. At least in terms of a traditional cookie. When you get into LSO's you're dealing with some other things, and obfuscation can be more complex. Though it is still limited to basic obfuscation techniques and 'armoring' the object.

As far as providing a defense, there are a number of addons available for firefox to "clean out" said cookies as others have already mentioned. However through enhancements in your browser security via mandatory access controls such as SELinux, or Apparmor you can completely remove a browsers ability to store cookies or LSOs. This control is outside of the realm of the browser and any code which may be executed in the browser, thus is inherently difficult to circumvent.  Though, for most average use cases this will break entirely too many sites to be considered an effective measure.

  I'm still curious how you deem that a cookie could be undetectable, and moreover how you feel there are no controls you can put in place to prevent the removal of "malicious cookies". Note the quotes, a cookie can not be malicious by nature, it is not executable and is only a data string.

Hope this helps.

---

### Post by hildenbrandsteven on 2012-02-13
Privacy on things look cookies is all browser dependent, no matter what OS you're on. Granted, Win7 has some built-in defense for it... But, any of these suggestions are good.. the firefox plugins are useful.

---

### Post by goodbye-windows(tm) on 2012-02-13
> **Dangertux said:**
> I'm not sure I agree with the statement that linux provides no defense against these types of things, nor am I really sure that there is such a thing as an undetectable cookie.

Unless you can discover where the cookies are stored, you can't delete all the copies-effectively making them undeletable. 

If active content is allowed to run in the browser, it can create cookie like objects anywhere on the hard drive. It can search directories and extract personal info, which is stored and made available via a cookie.

**So, how exactly do I delete all the hidden cookies on my system? **

**Before answering, read the following:**

[http://gracefool.com/how-you-have-no-real-privacy-on-the-internet](http://gracefool.com/how-you-have-no-real-privacy-on-the-internet)

[https://en.wikipedia.org/wiki/Evercookie](https://en.wikipedia.org/wiki/Evercookie)

[https://en.wikipedia.org/wiki/Zombie_cookie](https://en.wikipedia.org/wiki/Zombie_cookie)

Aren't zombie and evercookies effectively undeletable?

Regards,

Art

---

### Post by goodbye-windows(tm) on 2012-02-13
> **Dangertux said:**
> 
  I'm still curious how you deem that a cookie could be undetectable, and moreover how you feel there are no controls you can put in place to prevent the removal of "malicious cookies". Note the quotes, a cookie can not be malicious by nature, it is not executable and is only a data string.

Cookie is a broad term, it can effectively mean almost anything......

The only way to stop cookies in their tacks is to prevent all active content from all websites from running. But, active content does have some useful and legitimate purposes, so you can't surf well without active content being allowed to run.

Since you can't turn off javascript for all websites, then **cookies can be hidden anywhere and in almost any form-hence they become undeletable** because you can't find all the copies of the cookies.

Is this correct???

Regards,

Art

---

### Post by SeijiSensei on 2012-02-13
No, they have to be stored in directories that you, as an unprivileged user, can write to.  Out-of-the-box that list consists of your home directory and /tmp.  You'd have to run your browser with root privileges in order for it to write in other parts of the filesystem.

---

### Post by Ms. Daisy on 2012-02-13
[QUOTE=wikipedia on HTTP Cookies]A zombie cookie is any cookie that is automatically recreated after a  user has deleted it. This is accomplished by a **script** storing the  content of the cookie in some other locations, such as the local storage  available to Flash content, HTML5 storages and other client side  mechanisms, and then recreating the cookie from backup stores when the  cookie's absence is detected.[/QUOTE] 

An evercookie is javascript. So if they're both dependent on scripts, that means that if you block scripts (with NoScript) they can't run, right? Hopefully someone can confirm my logic leap.

As far as deleting them once you've allowed them to run, I have no idea.

---

### Post by CharlesA on 2012-02-13
NoScript blocks out flash too btw. Not sure if it blocks HTML5 video tho.

---

### Post by OpSecShellshock on 2012-02-13
> **CharlesA said:**
> NoScript blocks out flash too btw. Not sure if it blocks HTML5 video tho.

I don't believe it affects HTML5 objects. I recall browsing to a test page set up by the NoScript developer himself to demonstrate that the object would load even with NoScript active (all this object did was determine that NoScript was enabled and let you know). If I had a link I would provide it. Needless to say there are concerns in the infosec community about HTML5. Probably muddy the waters of this thread though.

---

### Post by CharlesA on 2012-02-13
> **OpSecShellshock said:**
> I don't believe it affects HTML5 objects. I recall browsing to a test page set up by the NoScript developer himself to demonstrate that the object would load even with NoScript active (all this object did was determine that NoScript was enabled and let you know). If I had a link I would provide it. Needless to say there are concerns in the infosec community about HTML5. Probably muddy the waters of this thread though.
Thanks. I googled it and found an entry about compatibility with html 5 but nothing about blocking it.

Thanks.

---

### Post by tr333 on 2012-02-13
You can use [FlashBlock](https://addons.mozilla.org/en-US/firefox/addon/flashblock/) to block Flash/Silverlight/etc. but I don't think it prevents the content download before blocking it.  Maybe that's irrelevant if the content doesn't get executed?

---

### Post by OpSecShellshock on 2012-02-14
There is an extension for Firefox called RequestPolicy that by default blocks all requests from one page to any other domain. In some ways it's even more of a pain to initially set up than NoScript can be for inexperienced users, which is why I only recommend it with caveats and only use it myself on a couple systems. Even if scripts are allowed on the third-party domain, the extension doesn't allow the request to be made. Since this also applies to sites that have CDNs, it has a side effect of making pages not load quite right, and look kind of ugly. If privacy is more of a concern than pretty, then it might be worth checking out.

---

