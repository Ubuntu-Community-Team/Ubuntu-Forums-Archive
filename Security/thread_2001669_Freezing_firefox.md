---
title: "Freezing firefox"
date: 2012-06-11
forum: Security
---

### Post by bjngchn on 2012-06-11
Installed kubuntu 12.04 from alternate cd (fully encrypted). Running firefox with js off. Also disabled all visible add-ons. No plugins, no flash. System should be secure and fast. Instead what happens: firefox freezes not only iself but the whole desktop for no reason quite often. When a big page is loaded it may freeze (even this should not happen), but  it happens at random times. Sometimes I get an error (after freezing)  which says something.js is not resposnding. Why is it even running: js is supposed to be off. Don't want to add any addons or plugins for extrasecurity. I just don't want any scripts.  (I don't click any ads, so noone can make click money from me anyway.)

---

### Post by bjngchn on 2012-06-13
Noone really knows anything about this? There are some programs running without user control, and I want to disable them permanently. Things that and with .js, .jsm, or any addons or default plugins. How can they be eliminated? Do I need to be a linux expert to get enough control on firefox? I also searched internet and it looks like these are common problems but people don't want to give any answer.

---

### Post by roelforg on 2012-06-13
Check your swap and your ram.
There might be a lack of size in either or bad ram.
My 256mb ram systems would go swapping so bad when using google images that i had to pull the ethernet cable to make it timeout and stop swapping.

---

### Post by bjngchn on 2012-06-13
Why do everything need to freeze only because one page is big, or I switch desktops. Only solution becomes: power off, and lose everything at once. If you need to be healty you need to know more than doctors. if you need to use computer you need to be as good as a hcker, or risk losing everything. Whenever I ask a critical question I don't get any answer (thanks for answer but this doen't help much). Main question: how to eliminate .jsm programs. Javascript is disabled, still some uknonw scripts running. Which firefox programs are really unnecessary and runs without user approval?

---

### Post by Ms. Daisy on 2012-06-13
How did you disable javascripts in your browser?

---

### Post by wacky_sung on 2012-06-14
> **Ms. Daisy said:**
> How did you disable javascripts in your browser?

about:plugins ->>> Firefox (make sure no java is down there)

[[img]http://s17.postimage.org/fg3toxk97/Screenshot_from_2012_06_14_23_58_46.jpg[/img]](http://postimage.org/image/fg3toxk97/)

---

### Post by Ms. Daisy on 2012-06-14
> **wacky_sung said:**
> about: plugins ->>> Firefox (make sure no java is down there)
Are we talking about [JavaScripts]("http://en.wikipedia.org/wiki/JavaScript") or [Java]("http://en.wikipedia.org/wiki/Java_%28programming_language%29")?  Similar names but very different things.

---

### Post by wacky_sung on 2012-06-15
> **Ms. Daisy said:**
> Are we talking about [JavaScripts]("http://en.wikipedia.org/wiki/JavaScript") or [Java]("http://en.wikipedia.org/wiki/Java_%28programming_language%29")?  Similar names but very different things.

Sound complex but in they are in common in term of programming.:popcorn:

---

### Post by Ms. Daisy on 2012-06-15
OK, I'll just make some presumptions to save a little time here.  I presume that you disabled java in the browser like wacky_sung showed. However, that does not block javascripts.  If you want to limit or stop javascripts, then you need to install an add-on like [NoScripts]("http://noscript.net/").  For a guide on how to configure NoScripts, please see the [No Scripts wiki]("https://wiki.ubuntu.com/BasicSecurity/NoScript").

---

### Post by wacky_sung on 2012-06-16
> **Ms. Daisy said:**
> OK, I'll just make some presumptions to save a little time here.  I presume that you disabled java in the browser like wacky_sung showed. However, that does not block javascripts.  If you want to limit or stop javascripts, then you need to install an add-on like [NoScripts]("http://noscript.net/").  For a guide on how to configure NoScripts, please see the [No Scripts wiki]("https://wiki.ubuntu.com/BasicSecurity/NoScript").

Actually you do not need Noscipt to do the disable of java script.

Uncheck the Javascript box from firefox will do.

[[img]http://s15.postimage.org/4y6djkvl3/Screenshot_from_2012_06_16_17_12_03.jpg[/img]](http://postimage.org/image/4y6djkvl3/)

---

### Post by bjngchn on 2012-06-18
No java, no js, no adons, no plugins. But there are stupid script errors like: resource://gre/modules/XPCOMUtils.jsm not responding. Question: Why is it even running and how to eliminate any such chrome or other stuff. Google seems to be living inside firefox in many ways. I prefer to eliminate any scripts that collects user info and sends to Google or any other place including Ubuntu.  Problem is similar to this: [http://www.computing.net/answers/windows-xp/i-keep-receiving-unresponsive-script-errors/199045.html](http://www.computing.net/answers/windows-xp/i-keep-receiving-unresponsive-script-errors/199045.html) but this happens with linux. There seem to be hidden addons or plugins or other programs which run without user approval.

---

### Post by Ms. Daisy on 2012-06-18
If you have used the method that Wacky_Sung showed to block scripts, then you have blocked ALL scripts.  That will break many many web pages.  IMO NoScripts is better because you can choose to allow some scripts so that you can actually get stuff accomplished on the web. But that's strictly personal preference.
 
Maybe the reason resource://gre/modules/XPCOMUtils.jsm isn't responding is because you disabled scripts?

---

